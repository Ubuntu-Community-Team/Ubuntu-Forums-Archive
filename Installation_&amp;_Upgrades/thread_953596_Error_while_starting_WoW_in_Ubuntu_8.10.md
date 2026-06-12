---
title: "Error while starting WoW in Ubuntu 8.10"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by ons on 2008-10-20
After installing WoW: The Burning Crusade, and watching the WoW cinematic intro, I get this error:

```
==============================================================================
World of WarCraft (build 9056)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Oct 20, 2008  8:35:03.974 AM
User:     jake
Computer: jake-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:005CE838

The instruction at "0x005CE838" referenced memory at "0xFF7FE2B8".
The memory could not be "read".


WoWBuild: 9056
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET showToolsUI "1"
SET portal "eu"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=011AECB0  EBX=0AF652E8  ECX=3F7FFFFF  EDX=017FBB78  ESI=0AF652E8
EDI=0000000C  EBP=003AF8D0  ESP=003AF8C4  EIP=005CE838  FLG=00210246
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 18/18 threads...

--- Thread ID: 56 ---
00000008 79EC8534 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 79EC8634 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 79EC8664 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 79EC87B4 0001:0006B372 C:\windows\system32\KERNEL32.dll
7D6E5A2E 79EC87E4 0001:00034A2E C:\windows\system32\winex11.drv
7ED2550E 79EC8994 0001:0007450E C:\windows\system32\user32.dll
7ED2556F 79EC89B4 0001:0007456F C:\windows\system32\user32.dll
006D9357 79EC89E4 0001:002D8357 C:\Program Files\World of Warcraft\Wow.exe
006D7725 79EC89F8 0001:002D6725 C:\Program Files\World of Warcraft\Wow.exe
007E8CCF 79EC8A30 0001:003E7CCF C:\Program Files\World of Warcraft\Wow.exe
007E8D74 79EC8A48 0001:003E7D74 C:\Program Files\World of Warcraft\Wow.exe
7BC6C252 79EC8AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 79EC93D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 79EC94C8 0000:00000000 <unknown>

--- Thread ID: 55 ---
00000008 7A039758 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7A039858 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7A039888 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7A0399D8 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C56C 7A0399F8 0001:0006B56C C:\windows\system32\KERNEL32.dll
0086B695 7A039A14 0001:0046A695 C:\Program Files\World of Warcraft\Wow.exe
00835B62 7A039A24 0001:00434B62 C:\Program Files\World of Warcraft\Wow.exe
00839B14 7A039A38 0001:00438B14 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7A039A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7A039AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7A03A3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7A03A4C8 0000:00000000 <unknown>

--- Thread ID: 54 ---
00000008 7A1AA534 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7A1AA634 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7A1AA664 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7A1AA7B4 0001:0006B372 C:\windows\system32\KERNEL32.dll
7D6E5A2E 7A1AA7E4 0001:00034A2E C:\windows\system32\winex11.drv
7ED2550E 7A1AA994 0001:0007450E C:\windows\system32\user32.dll
7ED2556F 7A1AA9B4 0001:0007456F C:\windows\system32\user32.dll
006D9357 7A1AA9E4 0001:002D8357 C:\Program Files\World of Warcraft\Wow.exe
006D7725 7A1AA9F8 0001:002D6725 C:\Program Files\World of Warcraft\Wow.exe
007E8CCF 7A1AAA30 0001:003E7CCF C:\Program Files\World of Warcraft\Wow.exe
007E8D74 7A1AAA48 0001:003E7D74 C:\Program Files\World of Warcraft\Wow.exe
7BC6C252 7A1AAAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7A1AB3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7A1AB4C8 0000:00000000 <unknown>

--- Thread ID: 53 ---
00000008 7B51C758 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7B51C858 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7B51C888 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7B51C9D8 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C56C 7B51C9F8 0001:0006B56C C:\windows\system32\KERNEL32.dll
0086B695 7B51CA14 0001:0046A695 C:\Program Files\World of Warcraft\Wow.exe
00835B62 7B51CA24 0001:00434B62 C:\Program Files\World of Warcraft\Wow.exe
00839B14 7B51CA38 0001:00438B14 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7B51CA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7B51CAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7B51D3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7B51D4C8 0000:00000000 <unknown>

--- Thread ID: 51 ---
00000008 7B68D888 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7B68D988 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7B68D9B8 0001:00058ED2 C:\windows\system32\ntdll.dll
7BC69F2C 7B68D9D8 0001:00058F2C C:\windows\system32\ntdll.dll
7BC6EAC0 7B68DA38 0001:0005DAC0 C:\windows\system32\ntdll.dll
7BC6BBBE 7B68DA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7B68DAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7B68E3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7B68E4C8 0000:00000000 <unknown>

--- Thread ID: 50 ---
00000008 7B7FE534 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7B7FE634 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7B7FE664 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7B7FE7B4 0001:0006B372 C:\windows\system32\KERNEL32.dll
7D6E5A2E 7B7FE7E4 0001:00034A2E C:\windows\system32\winex11.drv
7ED2550E 7B7FE994 0001:0007450E C:\windows\system32\user32.dll
7ED2556F 7B7FE9B4 0001:0007456F C:\windows\system32\user32.dll
006D9357 7B7FE9E4 0001:002D8357 C:\Program Files\World of Warcraft\Wow.exe
006D7725 7B7FE9F8 0001:002D6725 C:\Program Files\World of Warcraft\Wow.exe
007E8CCF 7B7FEA30 0001:003E7CCF C:\Program Files\World of Warcraft\Wow.exe
007E8D74 7B7FEA48 0001:003E7D74 C:\Program Files\World of Warcraft\Wow.exe
7BC6C252 7B7FEAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7B7FF3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7B7FF4C8 0000:00000000 <unknown>

--- Thread ID: 49 ---
00000008 7BBFE518 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7BBFE618 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7BBFE648 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7BBFE798 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C4CA 7BBFE7B8 0001:0006B4CA C:\windows\system32\KERNEL32.dll
0042256B 7BBFEA10 0001:0002156B C:\Program Files\World of Warcraft\Wow.exe
00421E2E 7BBFEA1C 0001:00020E2E C:\Program Files\World of Warcraft\Wow.exe
006A1297 7BBFEA38 0001:002A0297 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7BBFEA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7BBFEAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7BBFF3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7BBFF4C8 0000:00000000 <unknown>

--- Thread ID: 48 ---
00000008 7BEFE748 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7BEFE848 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7BEFE878 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7BEFE9C8 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C56C 7BEFE9E8 0001:0006B56C C:\windows\system32\KERNEL32.dll
006A4FE0 7BEFE9F8 0001:002A3FE0 C:\Program Files\World of Warcraft\Wow.exe
00421CF5 7BEFEA10 0001:00020CF5 C:\Program Files\World of Warcraft\Wow.exe
00421E11 7BEFEA1C 0001:00020E11 C:\Program Files\World of Warcraft\Wow.exe
006A1297 7BEFEA38 0001:002A0297 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7BEFEA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7BEFEAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7BEFF3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7BEFF4C8 0000:00000000 <unknown>

--- Thread ID: 47 ---
00000000 7C3D69C8 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7C3D69F8 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7C3D6A18 0001:0006D605 C:\windows\system32\KERNEL32.dll
00835A1D 7C3D6A24 0001:00434A1D C:\Program Files\World of Warcraft\Wow.exe
00839B49 7C3D6A38 0001:00438B49 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7C3D6A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7C3D6AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7C3D73D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7C3D74C8 0000:00000000 <unknown>

--- Thread ID: 46 ---
00000000 7C5479C8 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7C5479F8 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7C547A18 0001:0006D605 C:\windows\system32\KERNEL32.dll
00835A1D 7C547A24 0001:00434A1D C:\Program Files\World of Warcraft\Wow.exe
00839B49 7C547A38 0001:00438B49 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7C547A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7C547AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7C5483D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7C5484C8 0000:00000000 <unknown>

--- Thread ID: 45 ---
00000000 7C6B89C8 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7C6B89F8 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7C6B8A18 0001:0006D605 C:\windows\system32\KERNEL32.dll
00835A1D 7C6B8A24 0001:00434A1D C:\Program Files\World of Warcraft\Wow.exe
00839B49 7C6B8A38 0001:00438B49 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7C6B8A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7C6B8AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7C6B93D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7C6B94C8 0000:00000000 <unknown>

--- Thread ID: 44 ---
00000000 7C8299C8 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7C8299F8 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7C829A18 0001:0006D605 C:\windows\system32\KERNEL32.dll
00835A1D 7C829A24 0001:00434A1D C:\Program Files\World of Warcraft\Wow.exe
00839B49 7C829A38 0001:00438B49 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7C829A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7C829AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7C82A3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7C82A4C8 0000:00000000 <unknown>

--- Thread ID: 43 ---
00000003 7C9CA9C8 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7EE10CF5 7C9CAA38 0001:0001FCF5 C:\windows\system32\winmm.dll
7BC6BBBE 7C9CAA48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7C9CAAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7C9CB3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7C9CB4C8 0000:00000000 <unknown>

--- Thread ID: 42 ---
00000008 7CBA5754 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7CBA5854 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7CBA5884 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7CBA59D4 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C56C 7CBA59F4 0001:0006B56C C:\windows\system32\KERNEL32.dll
006A4FE0 7CBA5A04 0001:002A3FE0 C:\Program Files\World of Warcraft\Wow.exe
0077F4D2 7CBA5A1C 0001:0037E4D2 C:\Program Files\World of Warcraft\Wow.exe
006A1297 7CBA5A38 0001:002A0297 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7CBA5A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7CBA5AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7CBA63D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7CBA64C8 0000:00000000 <unknown>

--- Thread ID: 41 ---
00000000 7CD165A0 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7CD165D0 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7CD165F0 0001:0006D605 C:\windows\system32\KERNEL32.dll
007C99ED 7CD165FC 0001:003C89ED C:\Program Files\World of Warcraft\Wow.exe
00455179 7CD16A1C 0001:00054179 C:\Program Files\World of Warcraft\Wow.exe
006A1297 7CD16A38 0001:002A0297 C:\Program Files\World of Warcraft\Wow.exe
7BC6BBBE 7CD16A48 0001:0005ABBE C:\windows\system32\ntdll.dll
7BC6C252 7CD16AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7CD173D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7CD174C8 0000:00000000 <unknown>

--- Thread ID: 40 ---
00000000 7CE87980 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7B88E5B4 7CE879B0 0001:0006D5B4 C:\windows\system32\KERNEL32.dll
7B88E605 7CE879D0 0001:0006D605 C:\windows\system32\KERNEL32.dll
006BCFC4 7CE879F8 0001:002BBFC4 C:\Program Files\World of Warcraft\Wow.exe
007E8CCF 7CE87A30 0001:003E7CCF C:\Program Files\World of Warcraft\Wow.exe
007E8D74 7CE87A48 0001:003E7D74 C:\Program Files\World of Warcraft\Wow.exe
7BC6C252 7CE87AE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7CE883D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7CE884C8 0000:00000000 <unknown>

--- Thread ID: 39 ---
00000008 7D0DC728 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7BC69BFB 7D0DC828 0001:00058BFB C:\windows\system32\ntdll.dll
7BC69ED2 7D0DC858 0001:00058ED2 C:\windows\system32\ntdll.dll
7B88C372 7D0DC9A8 0001:0006B372 C:\windows\system32\KERNEL32.dll
7B88C56C 7D0DC9C8 0001:0006B56C C:\windows\system32\KERNEL32.dll
006BB095 7D0DC9E4 0001:002BA095 C:\Program Files\World of Warcraft\Wow.exe
006D7725 7D0DC9F8 0001:002D6725 C:\Program Files\World of Warcraft\Wow.exe
007E8CCF 7D0DCA30 0001:003E7CCF C:\Program Files\World of Warcraft\Wow.exe
007E8D74 7D0DCA48 0001:003E7D74 C:\Program Files\World of Warcraft\Wow.exe
7BC6C252 7D0DCAE8 0001:0005B252 C:\windows\system32\ntdll.dll
7BC6C482 7D0DD3D8 0001:0005B482 C:\windows\system32\ntdll.dll
F7D804FB 7D0DD4C8 0000:00000000 <unknown>

--- Thread ID: 38 [Current Thread] ---
005CE838 003AF8D0 0001:001CD838 C:\Program Files\World of Warcraft\Wow.exe
005CBE3A 003AF8F0 0001:001CAE3A C:\Program Files\World of Warcraft\Wow.exe
00798FA7 003AF920 0001:00397FA7 C:\Program Files\World of Warcraft\Wow.exe
00785D28 003AF94C 0001:00384D28 C:\Program Files\World of Warcraft\Wow.exe
00787007 003AFA20 0001:00386007 C:\Program Files\World of Warcraft\Wow.exe
00787285 003AFAF8 0001:00386285 C:\Program Files\World of Warcraft\Wow.exe
008AEB6B 003AFBD0 0001:004ADB6B C:\Program Files\World of Warcraft\Wow.exe
0047B831 003AFBF8 0001:0007A831 C:\Program Files\World of Warcraft\Wow.exe
0042C262 003AFCB4 0001:0002B262 C:\Program Files\World of Warcraft\Wow.exe
004391E7 003AFCD0 0001:000381E7 C:\Program Files\World of Warcraft\Wow.exe
004396D9 003AFCEC 0001:000386D9 C:\Program Files\World of Warcraft\Wow.exe
00443EFC 003AFDB8 0001:00042EFC C:\Program Files\World of Warcraft\Wow.exe
00427BA9 003AFDE8 0001:00026BA9 C:\Program Files\World of Warcraft\Wow.exe
004264B9 003AFE54 0001:000254B9 C:\Program Files\World of Warcraft\Wow.exe
00426591 003AFE6C 0001:00025591 C:\Program Files\World of Warcraft\Wow.exe
00406B28 003AFF08 0001:00005B28 C:\Program Files\World of Warcraft\Wow.exe
7B877B27 003AFFE8 0001:00056B27 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 18/18 threads...

--- Thread ID: 56 ---
00000008 <unknown module> <unknown symbol>+0 (0x79EC8568,0x7C162338,0x79EC85FC,0x79EC85D8)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x79EC869C,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x79EC869C,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x79EC8818,0x00000000,0xFFFFFFFF)
7D6E5A2E winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x79EC8818,0xFFFFFFFF,0x00000000)
7ED2550E user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x79EC89DC,0xFFFFFFFF,0x00000000)
7ED2556F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x79EC89DC,0x00000000,0xFFFFFFFF)
006D9357 Wow.exe      <unknown symbol>+0 (0x01205DB0,0x007E8CF5,0x0AC78B50,0x79EC8A30)
006D7725 Wow.exe      <unknown symbol>+0 (0x0AC78AF0,0x1C907178,0x007E8CF5,0x0AC78B50)
007E8CCF Wow.exe      <unknown symbol>+0 (0x0AC78B50,0x7BC6BBBE,0x0AC78B50,0x007E8CF5)
007E8D74 Wow.exe      <unknown symbol>+0 (0x007E8CF5,0x0AC78B50,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x79EC8B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x79EC9490,0x79EC9490,0x79EC9490)
F7D804FB              start_thread+203 (0x79EC9B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 55 ---
00000008 <unknown module> <unknown symbol>+0 (0x7A03978C,0x7BC45EB7,0x7A039820,0x7A0397FC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7A0398C0,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7A0398C0,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7A039A00,0x00000000,0xFFFFFFFF)
7B88C56C KERNEL32.dll WaitForSingleObject+60 (0x000021F4,0xFFFFFFFF,0x00839ADB,0x0ADCBC9C)
0086B695 Wow.exe      <unknown symbol>+0 (0x0ADCBE30,0xFFFFFFFF,0x7A039A38,0x00839B14)
00835B62 Wow.exe      <unknown symbol>+0 (0x0ADCBE30,0x0ADCBC9C,0x00000037,0x7A039A48)
00839B14 Wow.exe      <unknown symbol>+0 (0x0ADCBC9C,0x00839ADB,0x7A039AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x0ADCBC9C,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7A039B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x7A03A490,0x7A03A490,0x7A03A490)
F7D804FB              start_thread+203 (0x7A03AB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 54 ---
00000008 <unknown module> <unknown symbol>+0 (0x7A1AA568,0x7C162338,0x7A1AA5FC,0x7A1AA5D8)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7A1AA69C,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7A1AA69C,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7A1AA818,0x00000000,0xFFFFFFFF)
7D6E5A2E winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7A1AA818,0xFFFFFFFF,0x00000000)
7ED2550E user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7A1AA9DC,0xFFFFFFFF,0x00000000)
7ED2556F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7A1AA9DC,0x00000000,0xFFFFFFFF)
006D9357 Wow.exe      <unknown symbol>+0 (0x01205D50,0x007E8CF5,0x0AC9A790,0x7A1AAA30)
006D7725 Wow.exe      <unknown symbol>+0 (0x0AC9A750,0x1F665178,0x007E8CF5,0x0AC9A790)
007E8CCF Wow.exe      <unknown symbol>+0 (0x0AC9A790,0x7BC6BBBE,0x0AC9A790,0x007E8CF5)
007E8D74 Wow.exe      <unknown symbol>+0 (0x007E8CF5,0x0AC9A790,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7A1AAB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x7A1AB490,0x7A1AB490,0x7A1AB490)
F7D804FB              start_thread+203 (0x7A1ABB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 53 ---
00000008 <unknown module> <unknown symbol>+0 (0x7B51C78C,0x00000000,0x7B51C820,0x7B51C7FC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7B51C8C0,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B51C8C0,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7B51CA00,0x00000000,0xFFFFFFFF)
7B88C56C KERNEL32.dll WaitForSingleObject+60 (0x000021C4,0xFFFFFFFF,0x00839ADB,0x0743DF5C)
0086B695 Wow.exe      <unknown symbol>+0 (0x07533C10,0xFFFFFFFF,0x7B51CA38,0x00839B14)
00835B62 Wow.exe      <unknown symbol>+0 (0x07533C10,0x0743DF5C,0x00000035,0x7B51CA48)
00839B14 Wow.exe      <unknown symbol>+0 (0x0743DF5C,0x00839ADB,0x7B51CAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x0743DF5C,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7B51CB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x7B51D490,0x7B51D490,0x7B51D490)
F7D804FB              start_thread+203 (0x7B51DB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 51 ---
00000008 <unknown module> <unknown symbol>+0 (0x7B68D8BC,0x028E5A38,0x7B68D950,0x7B68D92C)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7B68D9E0,0x00000004,0x7B68DA20)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B68D9E0,0x00000000,0x00000000)
7BC69F2C ntdll.dll    NtWaitForSingleObject+60 (0x000021C0,0x00000000,0x7B68DA20,0x7BC85AF6)
7BC6EAC0 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC6E990,0x7B68DAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x7BC6E990,0x00000000,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7B68DB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x7B68E490,0x7B68E490,0x7B68E490)
F7D804FB              start_thread+203 (0x7B68EB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 50 ---
00000008 <unknown module> <unknown symbol>+0 (0x7B7FE568,0x7C02DD60,0x7B7FE5FC,0x7B7FE5D8)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7B7FE69C,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7B7FE69C,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7B7FE818,0x00000000,0xFFFFFFFF)
7D6E5A2E winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7B7FE818,0xFFFFFFFF,0x00000000)
7ED2550E user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7B7FE9DC,0xFFFFFFFF,0x00000000)
7ED2556F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7B7FE9DC,0x00000000,0xFFFFFFFF)
006D9357 Wow.exe      <unknown symbol>+0 (0x01205D08,0x007E8CF5,0x072EB028,0x7B7FEA30)
006D7725 Wow.exe      <unknown symbol>+0 (0x072DFF48,0x1E031178,0x007E8CF5,0x072EB028)
007E8CCF Wow.exe      <unknown symbol>+0 (0x072EB028,0x7BC6BBBE,0x072EB028,0x007E8CF5)
007E8D74 Wow.exe      <unknown symbol>+0 (0x007E8CF5,0x072EB028,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7B7FEB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x7B7FF490,0x7B7FF490,0x7B7FF490)
F7D804FB              start_thread+203 (0x7B7FFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 49 ---
00000008 <unknown module> <unknown symbol>+0 (0x7BBFE54C,0x7BC3AA00,0x7BBFE5E0,0x7BBFE5BC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BBFE680,0x00000004,0x7BBFE780)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BBFE680,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7BBFE8DC,0x00000000,0x000001F4)
7B88C4CA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x7BBFE8DC,0x00000000,0x000001F4)
0042256B Wow.exe      <unknown symbol>+0 (0x00421E20,0x7BBFEA38,0x006A1297,0x0651E528)
00421E2E Wow.exe      <unknown symbol>+0 (0x0651E528,0x006A1240,0x064BB298,0x7BC88444)
006A1297 Wow.exe      <unknown symbol>+0 (0x0000219C,0x006A1240,0x7BBFEAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x006A1240,0x064BB298,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7BBFEB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x7BBFF490,0x7BBFF490,0x7BBFF490)
F7D804FB              start_thread+203 (0x7BBFFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 48 ---
00000008 <unknown module> <unknown symbol>+0 (0x7BEFE77C,0x7B84E8BC,0x7BEFE810,0x7BEFE7EC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BEFE8B0,0x00000004,0x7BEFE9B0)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BEFE8B0,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7BEFE9F0,0x00000000,0x000003E8)
7B88C56C KERNEL32.dll WaitForSingleObject+60 (0x0000210C,0x000003E8,0x7BEFEA10,0x00421CF5)
006A4FE0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000030,0x00421E00,0x0651E538)
00421CF5 Wow.exe      <unknown symbol>+0 (0x00000000,0x7BEFEA38,0x006A1297,0x0651E538)
00421E11 Wow.exe      <unknown symbol>+0 (0x0651E538,0x006A1240,0x064BB298,0x7BC88444)
006A1297 Wow.exe      <unknown symbol>+0 (0x00002198,0x006A1240,0x7BEFEAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x006A1240,0x064BB298,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7BEFEB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x7BEFF490,0x7BEFF490,0x7BEFF490)
F7D804FB              start_thread+203 (0x7BEFFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 47 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x3F733333,0x7C3D6A24)
7B88E605 KERNEL32.dll Sleep+37 (0x0000000A,0x7C3D6A38,0x00839B49,0x0000000A)
00835A1D Wow.exe      <unknown symbol>+0 (0x0000000A,0x057C44C0,0x0000002F,0x7C3D6A48)
00839B49 Wow.exe      <unknown symbol>+0 (0x057C44C0,0x00839ADB,0x7C3D6AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x057C44C0,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7C3D6B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x7C3D7490,0x7C3D7490,0x7C3D7490)
F7D804FB              start_thread+203 (0x7C3D7B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 46 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000000)
7B88E605 KERNEL32.dll Sleep+37 (0x0000000A,0x7C547A38,0x00839B49,0x0000000A)
00835A1D Wow.exe      <unknown symbol>+0 (0x0000000A,0x05437C18,0x0000002E,0x7C547A48)
00839B49 Wow.exe      <unknown symbol>+0 (0x05437C18,0x00839ADB,0x7C547AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x05437C18,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7C547B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x7C548490,0x7C548490,0x7C548490)
F7D804FB              start_thread+203 (0x7C548B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 45 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x3F733333,0x7C6B8A24)
7B88E605 KERNEL32.dll Sleep+37 (0x0000000A,0x7C6B8A38,0x00839B49,0x0000000A)
00835A1D Wow.exe      <unknown symbol>+0 (0x0000000A,0x05436978,0x0000002D,0x7C6B8A48)
00839B49 Wow.exe      <unknown symbol>+0 (0x05436978,0x00839ADB,0x7C6B8AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x05436978,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7C6B8B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x7C6B9490,0x7C6B9490,0x7C6B9490)
F7D804FB              start_thread+203 (0x7C6B9B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000000)
7B88E605 KERNEL32.dll Sleep+37 (0x0000000A,0x7C829A38,0x00839B49,0x0000000A)
00835A1D Wow.exe      <unknown symbol>+0 (0x0000000A,0x03EA9A88,0x0000002C,0x7C829A48)
00839B49 Wow.exe      <unknown symbol>+0 (0x03EA9A88,0x00839ADB,0x7C829AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x00839ADB,0x03EA9A88,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7C829B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x7C82A490,0x7C82A490,0x7C82A490)
F7D804FB              start_thread+203 (0x7C82AB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
00000002 <unknown module> <unknown symbol>+0 (0x7C9CAA10,0x00000001,0x00000002,0x00000000)
7EE10CF5 winmm.dll    <unknown symbol>+0 (0x00000000,0x7EE10AD0,0x7C9CAAE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x7EE10AD0,0x00000000,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7C9CAB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x7C9CB490,0x7C9CB490,0x7C9CB490)
F7D804FB              start_thread+203 (0x7C9CBB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
00000008 <unknown module> <unknown symbol>+0 (0x7CBA5788,0x7CBA578C,0x7CBA581C,0x7CBA57F8)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CBA58BC,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CBA58BC,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CBA59FC,0x00000000,0xFFFFFFFF)
7B88C56C KERNEL32.dll WaitForSingleObject+60 (0x00002080,0xFFFFFFFF,0x7CBA5A1C,0x0077F4D2)
006A4FE0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x012E6B30,0x0000002A,0x0077F470)
0077F4D2 Wow.exe      <unknown symbol>+0 (0x012E6B30,0x006A1240,0x024C0DE8,0x7BC88444)
006A1297 Wow.exe      <unknown symbol>+0 (0x000020D4,0x006A1240,0x7CBA5AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x006A1240,0x024C0DE8,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7CBA5B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x7CBA6490,0x7CBA6490,0x7CBA6490)
F7D804FB              start_thread+203 (0x7CBA6B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 41 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)
7B88E605 KERNEL32.dll Sleep+37 (0x00000001,0x7CD16A1C,0x00455179,0x00000001)
007C99ED Wow.exe      <unknown symbol>+0 (0x00000001,0x00454FA0,0x024C09F0,0x00000029)
00455179 Wow.exe      <unknown symbol>+0 (0x024C09F0,0x006A1240,0x024C0A10,0x7BC88444)
006A1297 Wow.exe      <unknown symbol>+0 (0x000020D0,0x006A1240,0x7CD16AE8,0x7BC6C252)
7BC6BBBE ntdll.dll    call_thread_entry_point+14 (0x006A1240,0x024C0A10,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7CD16B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x7CD17490,0x7CD17490,0x7CD17490)
F7D804FB              start_thread+203 (0x7CD17B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7B88E5B4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7CE879D0,0x7B855027)
7B88E605 KERNEL32.dll Sleep+37 (0x00000064,0x7B88E5E0,0x7BC88444,0x02511830)
006BCFC4 Wow.exe      <unknown symbol>+0 (0x02511830,0x19948178,0x007E8CF5,0x01E23090)
007E8CCF Wow.exe      <unknown symbol>+0 (0x01E23090,0x7BC6BBBE,0x01E23090,0x007E8CF5)
007E8D74 Wow.exe      <unknown symbol>+0 (0x007E8CF5,0x01E23090,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7CE87B1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x7CE88490,0x7CE88490,0x7CE88490)
F7D804FB              start_thread+203 (0x7CE88B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
00000008 <unknown module> <unknown symbol>+0 (0x7D0DC75C,0x7D0DC760,0x7D0DC7F0,0x7D0DC7CC)
7BC69BFB ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7D0DC890,0x00000004,0x00000000)
7BC69ED2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7D0DC890,0x00000000,0x00000000)
7B88C372 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7D0DC9D0,0x00000000,0xFFFFFFFF)
7B88C56C KERNEL32.dll WaitForSingleObject+60 (0x000020B0,0xFFFFFFFF,0x7BC88444,0x7B88E5E0)
006BB095 Wow.exe      <unknown symbol>+0 (0x017FB8C0,0x007E8CF5,0x017FB940,0x7D0DCA30)
006D7725 Wow.exe      <unknown symbol>+0 (0x017FB8E0,0x18713178,0x007E8CF5,0x017FB940)
007E8CCF Wow.exe      <unknown symbol>+0 (0x017FB940,0x7BC6BBBE,0x017FB940,0x017FB940)
007E8D74 Wow.exe      <unknown symbol>+0 (0x007E8CF5,0x017FB940,0x10012A03,0x00000000)
7BC6C252 ntdll.dll    <unknown symbol>+0 (0x7D0DCB1C,0x00000000,0x00000000,0x00000000)
7BC6C482 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7D0DD490,0x7D0DD490,0x7D0DD490)
F7D804FB              start_thread+203 (0x7D0DDB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 [Current Thread] ---
005CE838 Wow.exe      <unknown symbol>+0 (0x00000006,0x011AECB0,0x00000006,0x0000008F)
005CBE3A Wow.exe      <unknown symbol>+0 (0x0AF652E8,0x0000000C,0x0000008F,0x07FF1D48)
00798FA7 Wow.exe      <unknown symbol>+0 (0x00000000,0x003AFA40,0x0AF65DE0,0x00000000)
00785D28 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x074F3170,0x3F77FE41)
00787007 Wow.exe      <unknown symbol>+0 (0x00000001,0x0AF65EE8,0x0AF65DE0,0x0000002C)
00787285 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x07659F64,0x3F800000)
008AEB6B Wow.exe      <unknown symbol>+0 (0x3F800000,0x00000003,0xFF000000,0x07406654)
0047B831 Wow.exe      <unknown symbol>+0 (0x4405199A,0x00000001,0x074065D8,0x07406654)
0042C262 Wow.exe      <unknown symbol>+0 (0x07406654,0x073B0E30,0x00000006,0x073B0140)
004391E7 Wow.exe      <unknown symbol>+0 (0x01E269E8,0x072D29B0,0x072D2998,0x00000000)
004396D9 Wow.exe      <unknown symbol>+0 (0x00000000,0x072D29A0,0x072D29B0,0x3DAC0832)
00443EFC Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x017F63A0)
00427BA9 Wow.exe      <unknown symbol>+0 (0x017F63A0,0x00000011,0x00000000,0x00000A28)
004264B9 Wow.exe      <unknown symbol>+0 (0x00000000,0x00406AC0,0x00000001,0x00000001)
00426591 Wow.exe      <unknown symbol>+0 (0x0040AD89,0x00400000,0x00000000,0x00111DF4)
00406B28 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B877B27 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x0138E000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x79290000 - 0x792D6000  C:\windows\system32\dbghelp.dll
0x7B820000 - 0x7B92D000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA4000  C:\windows\system32\ntdll.dll
0x7C9F0000 - 0x7CA36000  C:\windows\system32\dsound.dll
0x7D440000 - 0x7D44C000  C:\windows\system32\psapi.dll
0x7D4C0000 - 0x7D4F0000  C:\windows\system32\uxtheme.dll
0x7D630000 - 0x7D637000  C:\windows\system32\msacm32.drv
0x7D640000 - 0x7D66D000  C:\windows\system32\winealsa.drv
0x7D6A0000 - 0x7D6A4000  C:\windows\system32\midimap.dll
0x7D6B0000 - 0x7D73D000  C:\windows\system32\winex11.drv
0x7D860000 - 0x7D8B7000  C:\windows\system32\rpcrt4.dll
0x7D8D0000 - 0x7D95B000  C:\windows\system32\ole32.dll
0x7D960000 - 0x7D981000  C:\windows\system32\msacm32.dll
0x7D9B0000 - 0x7D9C9000  C:\windows\system32\iphlpapi.dll
0x7D9D0000 - 0x7D9F5000  C:\windows\system32\ws2_32.dll
0x7DA00000 - 0x7DAB4000  C:\windows\system32\comctl32.dll
0x7DAC0000 - 0x7DBC7000  C:\windows\system32\shell32.dll
0x7DBD0000 - 0x7DC20000  C:\windows\system32\shlwapi.dll
0x7DC30000 - 0x7DC41000  C:\windows\system32\mpr.dll
0x7DC50000 - 0x7DC8F000  C:\windows\system32\wininet.dll
0x7DCA0000 - 0x7DCAF000  C:\windows\system32\imm32.dll
0x7DCB0000 - 0x7DCC8000  C:\windows\system32\version.dll
0x7DCE0000 - 0x7DDCB000  C:\windows\system32\wined3d.dll
0x7DDD0000 - 0x7DDFB000  C:\windows\system32\d3d9.dll
0x7EB40000 - 0x7EBA6000  C:\windows\system32\opengl32.dll
0x7EBB0000 - 0x7EBF8000  C:\windows\system32\advapi32.dll
0x7EC10000 - 0x7EC93000  C:\windows\system32\gdi32.dll
0x7ECB0000 - 0x7EDDA000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE6C000  C:\windows\system32\winmm.dll
0x7EEA0000 - 0x7EEA4000  C:\windows\system32\lz32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 005CE838)

005CE838: 39 B4 8A 44  27 00 00 75  2A C1 E1 04  8B BC 11 80  9..D'..u*.......


Stack: 1024 bytes starting at (ESP = 003AF8C4)

* = addr               **                                         *           
003AF8C0: 78 BB 7F 01  0C 00 00 00  E8 5D 96 00  E8 52 F6 0A  x........]...R..
003AF8D0: F0 F8 3A 00  3A BE 5C 00  06 00 00 00  B0 EC 1A 01  ..:.:.\.........
003AF8E0: 06 00 00 00  8F 00 00 00  40 FA 3A 00  10 21 4F 07  ........@.:..!O.
003AF8F0: 20 F9 3A 00  A7 8F 79 00  E8 52 F6 0A  0C 00 00 00   .:...y..R......
003AF900: 8F 00 00 00  48 1D FF 07  00 00 00 00  00 00 00 00  ....H...........
003AF910: 48 1D FF 07  40 FA 3A 00  4C F9 3A 00  AA 5B 78 00  H...@.:.L.:..[x.
003AF920: 4C F9 3A 00  28 5D 78 00  00 00 00 00  40 FA 3A 00  L.:.(]x.....@.:.
003AF930: E0 5D F6 0A  00 00 00 00  40 FA 3A 00  48 F9 3A 00  .]......@.:.H.:.
003AF940: 8E FC 77 00  48 1D FF 07  00 00 00 00  20 FA 3A 00  ..w.H....... .:.
003AF950: 07 70 78 00  01 00 00 00  00 00 00 00  70 31 4F 07  .px.........p1O.
003AF960: 41 FE 77 3F  00 00 00 80  00 00 00 00  00 00 00 80  A.w?............
003AF970: 00 00 00 80  AF FE 39 3F  00 00 00 80  00 00 00 00  ......9?........
003AF980: 00 00 00 00  00 00 00 80  00 00 00 00  00 00 80 3F  ...............?
003AF990: 00 00 00 80  00 00 00 00  0D FD 8F C0  FF FF 8F 40  ...............@
003AF9A0: 00 00 00 00  00 00 00 00  00 00 80 BF  00 00 00 00  ................
003AF9B0: 00 00 80 3F  2E BD 3B B4  00 00 00 00  00 00 00 00  ...?..;.........
003AF9C0: 2E BD 3B 34  00 00 80 3F  00 00 00 00  00 00 00 00  ..;4...?........
003AF9D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
003AF9E0: F6 21 84 3F  00 00 00 00  00 00 00 00  00 00 00 00  .!.?............
003AF9F0: 00 00 00 00  49 2D B0 3F  00 00 00 00  00 00 00 00  ....I-.?........
003AFA00: 00 00 00 00  00 00 00 00  9F 02 80 3F  00 00 80 3F  ...........?...?
003AFA10: 00 00 00 00  00 00 00 00  E2 92 63 BE  00 00 00 00  ..........c.....
003AFA20: F8 FA 3A 00  85 72 78 00  01 00 00 00  E8 5E F6 0A  ..:..rx......^..
003AFA30: E0 5D F6 0A  2C 00 00 00  B8 A0 27 0B  64 9F 65 07  .]..,.....'.d.e.
003AFA40: 41 FE 77 3F  00 00 00 80  00 00 00 00  00 00 00 80  A.w?............
003AFA50: 00 00 00 80  AF FE 39 3F  00 00 00 80  00 00 00 00  ......9?........
003AFA60: 00 00 00 00  00 00 00 80  00 00 00 00  00 00 80 3F  ...............?
003AFA70: 00 00 00 80  00 00 00 00  0D FD 8F C0  FF FF 8F 40  ...............@
003AFA80: 70 31 4F 07  30 6B 2E 01  30 00 72 07  01 00 00 00  p1O.0k..0.r.....
003AFA90: B0 63 F6 0A  00 00 00 00  00 00 00 00  FF FF FF FF  .c..............
003AFAA0: 68 3B 4F 07  00 00 00 00  10 21 4F 07  00 00 00 00  h;O......!O.....
003AFAB0: 64 3D 4F 07  00 00 00 00  00 00 00 00  00 00 00 00  d=O.............
003AFAC0: 00 00 00 00  FF FF FF FF  B0 F4 0C 08  00 00 00 00  ................
003AFAD0: F0 14 FF 07  00 00 00 00  0C AB 7A 07  00 00 00 00  ..........z.....
003AFAE0: 00 00 00 00  8F 00 00 00  B0 15 52 06  30 97 1B 07  ..........R.0...
003AFAF0: C0 3D 21 07  00 00 00 00  D0 FB 3A 00  6B EB 8A 00  .=!.......:.k...
003AFB00: 01 00 00 00  00 00 00 00  64 9F 65 07  00 00 80 3F  ........d.e....?
003AFB10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFB20: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
003AFB30: 00 00 00 00  00 00 80 3F  00 00 00 00  CD CC CC BE  .......?........
003AFB40: 99 99 99 BE  00 00 00 00  00 00 80 3F  00 00 20 40  ...........?.. @
003AFB50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFB60: 56 55 55 40  00 00 00 00  00 00 00 00  00 00 00 80  VUU@............
003AFB70: 00 00 00 80  6F 12 03 BB  00 00 00 00  CD CC CC B9  ....o...........
003AFB80: CC CC CC 39  00 00 00 80  00 00 80 3F  CC 8D 24 C1  ...9.......?..$.
003AFB90: 1D 7F 0F BD  58 41 1C 40  97 AE 5E 00  C0 BF 13 00  ....XA.@..^.....
003AFBA0: C0 DF 31 41  1D 7F 0F BD  58 41 1C 40  00 00 80 3F  ..1A....XA.@...?
003AFBB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
003AFBC0: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 80 3F  ...........?...?
003AFBD0: F8 FB 3A 00  31 B8 47 00  00 00 80 3F  03 00 00 00  ..:.1.G....?....
003AFBE0: 00 00 00 FF  54 66 40 07  10 C6 8F 07  00 00 00 00  ....Tf@.........
003AFBF0: 14 00 00 00  00 00 00 00  B4 FC 3A 00  62 C2 42 00  ..........:.b.B.
003AFC00: 9A 19 05 44  01 00 00 00  D8 65 40 07  54 66 40 07  ...D.....e@.Tf@.
003AFC10: 28 FC 3A 00  53 B0 42 00  00 00 00 00  10 13 53 07  (.:.S.B.......S.
003AFC20: 14 6C 69 07  01 00 00 00  40 FC 3A 00  B3 B2 42 00  .li.....@.:...B.
003AFC30: 10 13 53 07  CC 9A 62 07  14 6C 69 07  14 6C 69 07  ..S...b..li..li.
003AFC40: 78 FC 3A 00  6F B3 42 00  18 9E 58 07  02 00 00 00  x.:.o.B...X.....
003AFC50: 04 00 00 00  9C 9B 62 07  CC 9B 62 07  00 00 00 00  ......b...b.....
003AFC60: 00 00 00 00  06 00 00 00  78 BE 9B 00  B8 93 7F 01  ........x.......
003AFC70: 10 DD 5D 07  CC 9A 62 07  84 FC 3A 00  E5 B3 42 00  ..]...b...:...B.
003AFC80: CC 9A 62 07  9C FC 3A 00  B3 50 43 00  14 6C 69 07  ..b...:..PC..li.
003AFC90: 98 6B 69 07  74 6C 69 07  E8 BB 42 00  C0 FC 3A 00  .ki.tli...B...:.
003AFCA0: 55 8E 43 00  74 6C 69 07  66 8E 43 00  00 00 00 00  U.C.tli.f.C.....
003AFCB0: 06 00 00 00  D0 FC 3A 00  E7 91 43 00  54 66 40 07  ......:...C.Tf@.
003AFCC0: 30 0E 3B 07  06 00 00 00  40 01 3B 07  B8 E9 2C 07  0.;.....@.;...,.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3846

Percent memory used:    65
Total physical memory:  1035501568
Free Memory:            356282368
Page file:              4070588416
Total virtual memory:   2147352575

```

---

### Post by Shugs81 on 2008-11-11
i get a similar error.... any clues peeps?

---

