---
title: "macromedia studio 8 on ubuntu"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by manuleka on 2007-07-03
just wondering if anyone tried macromedia studio 8 on ubuntu? i think i have the latest wine! i did a recent update and i saw the wine being updated...

is wine all required if installing windows application?

cheers

---

### Post by Juan_VCS on 2007-07-03
Yeah, wine is prolly all you need. If a direct install doesn't work and you have a Windows partition with Studio 8 installed, you could try [this](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)

---

### Post by manuleka on 2007-07-04
so i should try direct install first... cool i'l do that soon... and post after

---

### Post by ali4949 on 2007-07-07
Hey
I did a Dreamweaver 8 install on my feisty last night. Current wine version in the repo's is 0.9.40 which does not work. Use version 0.9.37.  After install I typed wine dreamweaver.exe and it gave me a could not find module error. So I browsed to the directory under wine where the dreaweaver.exe is installed and clicked it and it ran fine. You actually have to use the full path to the exe file, but it runs just fine.

---

### Post by edthehead101 on 2007-07-11
ok the other day i came back to ubuntu. vista lagged my laptop to death.. feisty here we go.. I just tried to install my copy of flash under feisty, it runs fine for around 3 minutes and the quits with no warnings. also it does not open .fla files. any ideas?

---

### Post by r@ndom@n on 2007-07-12
i need help installing macromedia studio 8 and adobe photoshop cs2 using wine.
it starts ok, but after a while i get "wizard was interupted" message, and the installation stops.
what can i do?

---

### Post by proxess on 2007-07-19
Well its not worth trying to install directly through wine.

First you should install in windows then copy paste it to your wine drive_c folder, OR use a partition accessible by both systems. What I do is use a 40gb partition in EXT2 and user drivers for it in Linux, and give wine the same drive letter.
In wineconf, put the OS as winXP (your OS has to be winXP as well i guess).
DON'T run the applications as sudo like its said in the tutorials mentioned above, its not necessary.
The flash 8 tutorial should work fine, i've made it work. Don't have screenshots tho.
For photoshop CS2, you also need to copy the uninstall registry key from windows. Just search for EPIC_SERIAL and you'll find it.
Then in linux, copy the C://Documents and Settings/<Username>/Application Data/Adobe folder into <wine drive_c>//windows/profiles/<Username>/Application Data/.

[Heres a screenshot of Photoshop CS2 on Feisty]("http://myte.zyns.com/Screenshot-12.png")

Tho for some reason it only worked once. I keep getting the admin error. Don't ask me, its just weird.

---

### Post by lyceum on 2007-07-24
Has anyone gotten Studio 8 to run on wine yet? I have Vista on my laptop, but I do not use it and I am selling it anyway to get a Dell Ubuntu laptop. I really need to get Studio 8 going on Feisty if it is possible. This is what I am getting:

david@lyceum:~$ wine "/media/cdrom1/install studio 8.exe"
wine: could not load L"D:\\install studio 8.exe": Module not found

Am I doing it wrong? I configured wine to add my DVD drives....

---

### Post by eldersoares on 2007-08-06
well, one more to the list
i've been trying all these options and tutorial and tips and blogs and websites... my wine says:
> libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err:shell:SHGetFileInfoW pidl is null!
fixme:wintab32:WTInfoW (0, 0, (nil)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x5b70020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1db690)->((nil),00000008)
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:ntdll:FILE_GetNtStatus Converting errno 19 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x78d0000 1000 000000000 failed
err:storage:BIGBLOCKFILE_UnmapPage unmapping inuse page (nil)
fixme:ntdll:FILE_GetNtStatus Converting errno 19 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x78d0000 1000 000000000 failed
wine: Unhandled page fault on write access to 0x00000000 at address 0xb7dcaea7 (thread 000e), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000f
        00000011    0
        00000010    0
0000000d (D) (null)
        00000017    1
        00000016    2
        00000015    1
        00000014    0
        00000013    0
        00000012   15
        0000000e    0


the funny is that it works in my elder amd k6-2, 64 ram w/ kurumin linux and an elder version of wine... but in my dell inspiron 6400 intel centrino duo 2x1,6ghz 1gbram it DOESNT! any suggestions, plzzzzzzzzzz????????????
thanks a lot! if i get free of this, i get free of WINDOWZ

---

### Post by maxrisc on 2007-08-16
Gutsy Kernel 2.6.22
Wine 0.9.42 out of the repos.
Dreamweaver Studio 8 - (Everything works.  Screen resizing is a little slow in Compiz/Fusion though)

Installed Dreamweaver 8 using Wine directly from Macromedia CD.  I didn't bother to upgrade to CS3 as I don't really use it for anything else than coding PHP/mySQL.  CS3 requires 512MB of RAM to run.  What a waste.

Using RapidSVN to open up files directly. :)

Anyway...enjoy!

---

### Post by lyceum on 2007-08-17
> **maxrisc said:**
> Gutsy Kernel 2.6.22
Wine 0.9.42 out of the repos.
Dreamweaver Studio 8 - (Everything works.  Screen resizing is a little slow in Compiz/Fusion though)

Installed Dreamweaver 8 using Wine directly from Macromedia CD.  I didn't bother to upgrade to CS3 as I don't really use it for anything else than coding PHP/mySQL.  CS3 requires 512MB of RAM to run.  What a waste.

Using RapidSVN to open up files directly. :)

Anyway...enjoy!

That is awesome! How stable is Gutsy? I normally wait for the month prior to release to upgrade. If if it stable enough though, I will go for it now.

---

### Post by alex30002 on 2007-10-03
i have Studio 8 running too with wine 0.9.41.

It runs well, except windows 98 interface

---

