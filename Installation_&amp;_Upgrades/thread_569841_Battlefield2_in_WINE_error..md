---
title: "Battlefield2 in WINE error."
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by Antexter on 2007-10-07
Trying to use wine under Kubuntu 7.04, to run BattleField2.
I really dont know much about linux so try and keep any replies basic.

> mike@mike-desktop:~$ wine "C:\\program files\\EA GAMES\\Battlefield 2\\bf2.exe"
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
err:module:import_dll Library d3dx9_25.dll (which is needed by L"C:\\program files\\EA GAMES\\Battlefield 2\\TextureAtlasBuilder.dll") not found
err:module:import_dll Library TextureAtlasBuilder.dll (which is needed by L"C:\\program files\\EA GAMES\\Battlefield 2\\RendDX9.dll") not found
err:module:import_dll Library d3dx9_25.dll (which is needed by L"C:\\program files\\EA GAMES\\Battlefield 2\\RendDX9.dll") not found
fixme:ntdll:NtSetSystemInformation (0x00000015,0x33ed10,0x00000024) stub
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x47a970
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x7e7855dc,0x54e9ca): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x175428,0x54e9ca): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x7e7855dc,0x54f1e2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x175428,0x54f1e2): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
mike@mike-desktop:~$   

So it just starts up I see the BF2 slash and then it just closes, how would i go about fixing this?

---

### Post by Tachyon1000 on 2007-10-07
I think you'd be best served by checking over at winehq.com to see how others have made BF2 run under Wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438)

---

