---
title: "fm20 Install Failed with Winetricks"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by boaty on 2010-08-10
Hey everyone,

So a program I'm trying to run (INVedit, for the Minecraft Alpha) needs fm20 installed to work.  So going through the winetricks motions, I have it run, but the install program says "Microsoft ActiveX Control Pad Setup was not completed successfully."

However, this is the output from "sh winetricks fm20"
```

prerequisite wsh56 already installed, skipping
Executing /usr/bin/cabextract --directory=/home/zach/.wine/dosdevices/c:/winetrickstmp /home/zach/.winetrickscache/setuppad.exe
/home/zach/.winetrickscache/setuppad.exe: library not compiled to support large files.
Extracting cabinet: /home/zach/.winetrickscache/setuppad.exe
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/asycpict.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Index.htm
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Htmlref2.htm
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/vbsref.htm
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/acmsetup.hlp
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/fm20.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/fm20enu.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Hlp95en.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ISCtrls.ocx
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/license.txt
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Mfc40.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/msped_bb.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/mspedcah.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/mssetup.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Msvcrt40.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/P2D.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/PED.box
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ped.cnt
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/PEd.exe
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ped.hlp
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ped.inf
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ped.stf
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/Readme.txt
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/remove.exe
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/riched20.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/ScrWiz.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/setup.exe
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/setup.ini
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/setup.lst
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/setup.tdf
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/acmsetup.exe
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/commtb32.dll
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/MSNAudio.acm
  extracting /home/zach/.wine/dosdevices/c:/winetrickstmp/htmlr000.htm

All done, no errors.
If setup says 'Unable to start DDE ...', press Ignore
Executing wine /home/zach/.wine/dosdevices/c:/winetrickstmp/setup
fixme:shell:Dde_OnConnectConfirm stub
fixme:shell:Dde_OnRequest stub
fixme:shell:Dde_OnDisconnect stub
Install of fm20 done
winetricks done.

```

If it's important (maybe the issue isn't fm20), here is the output of when I try to run INVedit.
```

zach@Zach-Desktop:~/Games/Minecraft Alpha/INVedit$ wine INVedit.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x60e5dc,0x00000000), stub!

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.MimeIconEngine ---> System.DllNotFoundException: libgdk-x11-2.0.so.0
  at (wrapper managed-to-native) System.Windows.Forms.GnomeUtil:gdk_init_check (intptr,intptr)
  at System.Windows.Forms.GnomeUtil.Init () [0x00000] 
  at System.Windows.Forms.GnomeUtil.GetIcon (System.String icon, Int32 size) [0x00000] 
  at System.Windows.Forms.GnomeHandler.AddGnomeIcon (System.String internal_mime_type, System.String name) [0x00000] 
  at System.Windows.Forms.GnomeHandler.CreateUIIcons () [0x00000] 
  at System.Windows.Forms.GnomeHandler.Start () [0x00000] 
  at System.Windows.Forms.MimeIconEngine..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.WinFileSystem..ctor () [0x00000] 
  at System.Windows.Forms.MWFVFS..ctor () [0x00000] 
  at System.Windows.Forms.FileDialog..ctor () [0x00000] 
  at System.Windows.Forms.SaveFileDialog..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.SaveFileDialog:.ctor ()
  at INVedit.MainForm.InitializeComponent () [0x00000] 
  at INVedit.MainForm..ctor (System.String[] files) [0x00000] 
  at (wrapper remoting-invoke-with-check) INVedit.MainForm:.ctor (string[])
  at INVedit.Program.Main (System.String[] args) [0x00000] 

```

I also saw someone run this by using "mono INVedit.exe"
```

zach@Zach-Desktop:~/Games/Minecraft Alpha/INVedit$ mono INVedit.exe

** (INVedit.exe:23195): WARNING **: The following assembly referenced from /home/zach/Games/Minecraft Alpha/INVedit/INVedit.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/zach/Games/Minecraft Alpha/INVedit/).


** (INVedit.exe:23195): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (INVedit.exe:23195): WARNING **: Missing method EnableVisualStyles in assembly /home/zach/Games/Minecraft Alpha/INVedit/INVedit.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'

```

I have no idea what this output means, so I hope someone here can figure it out.

Thanks in advance.

Edit:

So I'm looking through these outputs again (it's much easier outside of the terminal), and both wine INVedit.exe and mono INVedit.exe mention System.Windows.Form.  To me, that makes it seem that it's a problem with fm20 since thats the form manager (I think that's the right acronym).  What do you think?

---

### Post by boaty on 2010-08-12
Bump.  This is still not working.  I really hope someone out there knows what's going on.  Google hasn't shown me anything to help so far.

TIA.

---

### Post by ajmilazzo on 2010-09-03
Hello, you will probably need the mono-winforms packages. You can install them by typing the following in to terminal:

> sudo apt-get mono-winform*

Then use Mono to run INVEdit:

> mono INVEdit.exe

---

