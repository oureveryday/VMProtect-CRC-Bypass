LONG WINAPI VMPCRCExceptionHandler(EXCEPTION_POINTERS* ExceptionInfo)
{

    if (std::find(hooked_addrs.begin(), hooked_addrs.end(), ExceptionInfo->ExceptionRecord->ExceptionAddress) != hooked_addrs.end())
    {
        ExceptionInfo->ContextRecord->Rip += 0x2;
        return EXCEPTION_CONTINUE_EXECUTION;
    }
    return EXCEPTION_CONTINUE_SEARCH;
}
