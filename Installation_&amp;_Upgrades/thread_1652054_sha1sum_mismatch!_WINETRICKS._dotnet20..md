---
title: "sha1sum mismatch! WINETRICKS. dotnet20."
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by TheShadow124 on 2010-12-24
I've been having an issue with winetricks ever since 10.10 came out, it get a error while downloading a file called l_intl.nls, if I edit the winetricks script to ignore the error... im trying to install dotnet20, even with the modification, it crashes after barley starting the install.

Both cases:

No Script Mod:
```
usr@cmp1:~$ winetricks dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
------------------------------------------------------
sha1sum mismatch!  Rename /home/theshadow124/.cache/winetricks/dotnet20/l_intl.nls and try again.
------------------------------------------------------
theshadow124@captus-1-ProLiant-ML370-G4:~$ ^C
theshadow124@captus-1-ProLiant-ML370-G4:~$ ^C
theshadow124@captus-1-ProLiant-ML370-G4:~$ winetricks dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
------------------------------------------------------
sha1sum mismatch!  Rename /home/theshadow124/.cache/winetricks/dotnet20/l_intl.nls and try again.
------------------------------------------------------
usr@cmp1:~$ 
```

With mod: (have to kill with ctr-C because it locks up trying to run debugger)
```
usr@cmp1:~$ sh winetricks dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion SubVersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion VersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CSDVersion 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentBuildNumber 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentVersion 0 0 1
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ProductOptions ProductType 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\ServiceCurrent OS 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\Windows CSDVersion 0 0 1
The operation completed successfully
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/theshadow124/.cache/winetricks/dotnet20/l_intl.nls /home/theshadow124/.wine/dosdevices/c:/windows/system32
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Error: The system was unable to find the specified registry key or value
Executing wine /home/theshadow124/.cache/winetricks/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\theshadow124\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:imm:ImmDisableIME (-1): stub
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime 2.0 Error Reporting"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00001388,(nil),0x000b,0x000000ee,0x3009a1b4,0x5dc624): stub
err:eventlog:ReportEventW L"clr20r3"
err:eventlog:ReportEventW L"regsvcs.exe"
err:eventlog:ReportEventW L"2.0.50727.42"
err:eventlog:ReportEventW L"4333ae62"
err:eventlog:ReportEventW L"mscorlib"
err:eventlog:ReportEventW L"2.0.0.0"
err:eventlog:ReportEventW L"4333ab80"
err:eventlog:ReportEventW L"2a4a"
err:eventlog:ReportEventW L"0"
err:eventlog:ReportEventW L"system.nullreferenceexception"
err:eventlog:ReportEventW L"NIL"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
wine: Unhandled page fault on read access to 0x00000000 at address 0x2ed2c57 (thread 0036), starting debugger...
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 39 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 33 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 3d on event 0

usr@cmp1:~$ 

```

Im not sure where to go from here... I am not the most skilled Linux user, but I've done quite a bit of searching and I cant find any information about my particular problem. Its a fresh wine prefix.

Im running latest wine: 1.3.9
and winetricks: 20101222

I really hope someone has an idea, only reason I am posting is because its kinda urgent since I need it on my server and I have to have it back up by the 28th.

Thanks,
TheShadow

---

### Post by dankegel on 2010-12-27
The error message said

Rename /home/theshadow124/.cache/winetricks/dotnet20/l_intl.nls and try again.

Did you try doing that?

---

