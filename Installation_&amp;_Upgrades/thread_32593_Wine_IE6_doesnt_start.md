---
title: "Wine: IE6 doesnt start"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by moser on 2005-05-08
Hi Folx,

I searched a lot in this forum and didn't find a thread to my problem. 
I installed wine winetools and wine-utils without problems.

With winetools I made a fake windows, didn't install Arial.exe as this doesn't seem to work and installe IE6.

Winetools tells me everything were ok and added some scripts to my home-folder in bin/.

When I try to start IEXPLORE.EXE it asks me, wether I want to set Internet Explorer as my default browser - so it were installed, BUT... then another window opens "link to start menu", which has no content and is transparent (you cann look through to the window in the background). In the shell the winde-debugger starts. That's it, nothing happens from here on.

Here is the complete shell - output:

> most@josefk:~/.wine/drive_c/Programme/Internet Explorer $ wine IEXPLORE.EXE
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:ActivateActCtx stub!
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10032,0x00008003,0x00008000,0x0000c06e,0x00000001,0x7796ded4):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10032, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10032] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10036 wParam 00000001 lParam 00000000
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10050, wParam=0x00000000, size.cx=1024, size.cy=764 stub!
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:shell:NTSHChangeNotifyRegister (0x10050,0x00008003,0x0c02b7ff,0x0000c06e,0x00000001,0x7796df14):semi stub.
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:actctx:CreateActCtxW stub!
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:win:GetProcessWindowStation (void): stub
fixme:shell:SHELL32_DllInstall TRUE L"\0001": stub
wine: Unhandled exception (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00000000 ESP:7795df20 EBP:7795df3c EFLAGS:00210246(   - 00      -RIZP1)
 EAX:01001cc8 EBX:77b642a0 ECX:00021401 EDX:77eff17c
 ESI:00000000 EDI:00005000
Stack dump:
0x7795df20:  010062ec 01001cc8 00000000 01001dc8
0x7795df30:  7795f7f4 7795df44 76dcb440 7795f7f8
0x7795df40:  01002397 01001cc8 01001dc8 7795f7f4
0x7795df50:  76bd8110 77c5c400 77c5c400 7800dba8
0x7795df60:  78012820 7795e004 7ff988a3 7795df8c
0x7795df70:  7800dbb8 00000001 7ffcc407 77c5a49c
Backtrace:
=>1 0x00000000 (0x7795df3c)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file exe\grpconv.dbg ("C:\\windows")
  2 0x01002397 in grpconv (+0x2397) (0x7795f7f8)
  3 0x01002e45 in grpconv (+0x2e45) (0x7795fa50)
  4 0x01002f68 in grpconv (+0x2f68) (0x7795fb84)
  5 0x01007440 in grpconv (+0x7440) (0x7795feac)
  6 0x010076ee  ??  in grpconv (0x7795ff20)
  7 0x77b73de2 in kernel32 (+0x53de2) (0x7795fff4)
  8 0xb7fc9181  ??  in libwine.so.1 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Wine-dbg>

---

### Post by gunnyman on 2005-05-08
You probably need to install DCOM98 as well.

---

### Post by moser on 2005-05-08
[QUOTE=gunnyman]You probably need to install DCOM98 as well.[/QUOTE]

I forget to mention: I did that as well. I made a complete base-setup with winetools but the download of the arial.exe.

---

