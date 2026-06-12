---
title: "Broken 32bit wine games and broken steam native Glxchoosevisual failed"
date: 2018-09-23
forum: MINT
---

### Post by dj--alex on 2018-09-23
I tries everything what i can found with one WEEK and i giveup
I think is 32bit support games broken in driver ot etc.

I select hardware forum, i thinking it's driver problem.

Please help with 
:: 0009:err:wgl:init_opengl Failed to load libGL:
0009:err:wgl:init_opengl OpenGL support is disabled.
or
\Games\\Steam-win32\\SteamApps\\common\\Unreal Tournament 3\\Binaries\\UT3.exe", 0x231eba8)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

Driver is not damaged !!!!
Normal DX10-DX11 games working in wine-dxvk. At lease No man's sky and Final Fantasy XV.
Normal Native games is working.  (Unigine Valley) 

Steam -Native gets  Glxchoosevisual failed(swrast error of course) 
I know how to fix run steam by command
sudo mv /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/mesa/libGL.so.1.ba
if fix errors with STEAM native only. Wine still unfixed.
But after any update NVIDIA driver errors resurrected and i need to do it again
3 updates - 3 additional commands.

My mesa files
[https://pp.userapi.com/c851032/v851032768/c490/lQFu9U3h1CM.jpg](https://pp.userapi.com/c851032/v851032768/c490/lQFu9U3h1CM.jpg)
Nvidia files
[https://pp.userapi.com/c851032/v851032768/c4ab/33NMQ4APtR4.jpg](https://pp.userapi.com/c851032/v851032768/c4ab/33NMQ4APtR4.jpg)
 

Spaceengine - is free application. 

Ryzen 1500, Mint linux 18.3 x64 Kernel 18.3 Nvidia 410 Driver (probowales 396 tez) 
CLEAN wine staging 3.16 PREFIX. + or - DXVK - no alteres error.
Arch Linux user tells install "nvidia-utils" for 32bit apps run 
nvidia-utils/lib32-nvidia-utils 
I don't know how to correctly this named in Linux Mint
Where is  lib32-nvidia-utils in Linux Mint? how to remove cursed swrast? 

I have 2 HDD with 2 install of Linux Mint 18.3 updated.
PC1 is named PCN, PC2 is named PC2.
It's one computer with one working hardware just 2 HDD to load.

I don't interest in installs Mint 19 or Ubuntu 18.04
Im create ISO image with Mint 18.3 with ALL needed for me programs& home using.
and configured DXVK for all my applications and games.

I can share ISO image if anybody can helps. and if it allowed on forum.

Im just want to found solution fix 32bit problems. 
All of other things works brilliant.

Bug [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101)
WORKAROUND: reinstall libc6-i386 by running 'sudo apt-get install --reinstall libc6-i386'.
sudo apt-get install --reinstall libc6-i386 (NOT TESTED)

PCZ:NO WORK.
```
E: Internal Error, No file name for libc6-i386:amd64
NO WORK ON PC2 
user@PC2 ~ $ steam
Running Steam on linuxmint 18.3 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Installing breakpad exception handler for appid(steam)/version(1536436120)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```



or maybe today is this bug
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852873](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852873)
A workaround for this bug:
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current wine Spaceengine.exe CHECK AGAIN
maybe fix name? 
LD_LIBRARY_PATH=/usr/lib32/nvidia-410 wine Spaceengine.exe 
not helped.
libGL error: failed to load driver: swrast
I hate swrast.
PC2 HAVE A SAME ERROR:
user@PC2 /media/user/D/Games/SpaceEngine098/system $ LD_LIBRARY_PATH=/usr/lib32/nvidia-current wine Spaceengine.exe 
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

```


I get this error in Steam Native, All Wine 32bit old games.
New games 64bit wine - DX10-11 works like Final Fantasy XV. 
I installed Nvidia-410, libcuda-410 and nvidia-settings.

u```
ser@PCN ~ $ glxinfo | grep 'direct rendering\| string'
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 1060 3GB/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 410.48
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL version string: 4.6.0 NVIDIA 410.48
OpenGL shading language version string: 4.60 NVIDIA
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 410.48
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
user@PCN ~ $ 
```

```
user@PCN ~ $ uname -a
Linux PCN 4.18.3-041803-generic #201808180530 SMP Sat Aug 18 09:32:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
user@PCN ~ $ lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia
user@PCN ~ $ 

```

```
user@PCN /media/user/D/Games/Steam-win32/SteamApps/common/Unreal Tournament 3/Binaries $ wine UT3.exe
0171:err:winediag:wined3d_dll_init Setting multithreaded command stream to 0.
0171:fixme:gameux:GameExplorerImpl_VerifyAccess (0x14d930, L"Z:\\media\\user\\D\\Games\\Steam-win32\\SteamApps\\common\\Unreal Tournament 3\\Binaries\\UT3.exe", 0x231eba8)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
0171:err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
0171:fixme:dbghelp:validate_addr64 Unsupported address fffffffff7b90000
0171:fixme:dbghelp:validate_addr64 Unsupported address fffffffff7b80000
0171:fixme:faultrep:ReportFault 0x231eb94 0x0 stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x13119d7 (thread 0171), starting debugger...
user@PCN /media/user/D/Games/Steam-win32/SteamApps/common/Unreal Tournament 3/Binaries $ 
```

======================
[https://forum.winehq.org/viewtopic.php?p=66845](https://forum.winehq.org/viewtopic.php?p=66845)
NOT HELPED
I figured out the issue - somehow Wine's trying to load the wrong libGL.so. I went in and changed the links like so.


```
sudo rm /usr/lib/x86_64-linux-gnu/libGL.so
sudo ln -s /usr/lib/nvidia-current-updates/libGL.so /usr/lib/x86_64-linux-gnu/libGL.so

PCN /media/user/D/Games/SpaceEngine098/system $ wine SpaceEngine.exe 000b:fixme:winediag:start_process Wine Staging 3.16 is a testing version containing experimental patches.
000b:fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
0009:fixme:ver:GetCurrentPackageId (0x32fcb4 (nil)): stub
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
0009:err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032fb94 EBP:0032fc60 EFLAGS:0
```


sudo apt-get upgrade not helped

I tries another method

user@PCN /media/user/D/Games/SpaceEngine098/system $ LD_LIBRARY_PATH=/usr/lib32/nvidia-current wine SpaceEngine.exe 


```
user@PCN /media/user/D/Games/SpaceEngine098/system $ LD_LIBRARY_PATH=/usr/lib32/nvidia-current wine SpaceEngine.exe 
000b:fixme:winediag:start_process Wine Staging 3.16 is a testing version containing experimental patches.
000b:fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
0009:fixme:ver:GetCurrentPackageId (0x32fcb4 (nil)): stub
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  253
  Current serial number in output stream:  257
user@PCN /media/user/D/Games/SpaceEngine098/system $ 
```

```
user@PCN /media/user/D/Games/SpaceEngine098/system $ wine SpaceEngine.exe 
002b:fixme:ver:GetCurrentPackageId (0x32fcb4 (nil)): stub
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  253
  Current serial number in output stream:  257
user@PCN /media/user/D/Games/SpaceEngine098/system $ 

```
PC2 Same error

========
[https://www.linux.org.ru/forum/games/14487728](https://www.linux.org.ru/forum/games/14487728)  tells
sudo apt-get install -t libgl1-nvidia-glx

not helped of course
```
user@PCN ~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083; $ sudo apt-get install -t libgl1-nvidia-glx
[sudo] &#1087;&#1072;&#1088;&#1086;&#1083;&#1100; &#1076;&#1083;&#1103; user: 
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
E: &#1047;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; «libgl1-nvidia-glx» &#1085;&#1077;&#1076;&#1086;&#1087;&#1091;&#1089;&#1090;&#1080;&#1084;&#1086; &#1076;&#1083;&#1103; APT::Default-Release, &#1090;&#1072;&#1082; &#1082;&#1072;&#1082; &#1074;&#1099;&#1087;&#1091;&#1089;&#1082; &#1085;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;&#1085; &#1074; &#1080;&#1089;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082;&#1072;&#1093;

```
PC2 same error.
no file(s) error

searching continues
 libGL error: No matching fbConfigs or visuals found libGL error: failed to load driver: swrast

```
user@PCN ~ $ steam
Running Steam on linuxmint 18.3 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Installing breakpad exception handler for appid(steam)/version(1536436120)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```

---

### Post by jeremy31 on 2018-09-23
Moved To Mint

---

### Post by dj--alex on 2018-09-23
Someone tells remove bbswitch-dkms
This not helped

I create video with bug
[https://youtu.be/hHnAjbqKrIA](https://youtu.be/hHnAjbqKrIA)

---

### Post by dj--alex on 2018-09-25
Relly anybody don't know how help to fix it?
Problem is NOT WINE BUG. This is a driver bug i think. 

If all community don't know how to fix problem maybe real ISO can helps. 
ISO image of my PC - This is image with error unfortunately non english. I used it on my PC 
and i done it for me with Systemback. I use utility 5 years without problems. Problem with 32bit part of drivers from Nvidia , i don't know how to install it.
[URL="https://cloud.mail.ru/public/4EBz/NfGLujChY"]https://cloud.mail.ru/public/4EBz/NfGLujChY
I check all old images system and all of it from 2 May contains this error.[/URL]
You can load and in Live without install  try to run any application and you can get this error.
Problem detected in all ISO images from 5 months, i don't want install Ubuntu 18 or Mint 19 or etc. they have problem with install Systemback (casper 1.340) and wine staging repositories problem ( doesn't support bionic)
I just want use image to End of support Ubuntu 16.04 \ Mint 18.3 (2022 Year) 
Rollback to 5 months is impossible, to much work and preinstalls done. 

If you don't like steam (it just simpliest to test) - download free Spaceengine . [http://spaceengine.org/download/spaceengine](http://spaceengine.org/download/spaceengine)
wine preinstalled.  and i full remove wine, error with SWRAST still exists.

If founds a solution for this problem i remove file from link

---

### Post by dj--alex on 2018-09-25
I found a temporatily solution
I delete with Synaptic these packets: libglapi-mesa:i386 libglu-mesa:i386  
And...
All Win32 apps like "total commander" "Spaceengine" , Panolapse without reboot start works!
And Steam Native start works but with EVERY START  tries reinstall libglapi-mesa:i386 (i just press CTRL-C to skip) 
All games and Steam Native or etc 32bit apps works

But i think it's no good solution
Steam must don't require download mesa.
And if i want to remove Nvidia driver  - how works system without it? 
Mesa without this files can run Radeon\ Intel  or it just works in 640x480 mode. I need test it.

Maybe exist another method to fix "SWRAST" problem ?

---

### Post by dj--alex on 2018-09-30
I get same error with Mint 19 x64 Mate

Get fresh system like 18 mint
don't use Oibaf. skip.
I install Nvidia 396 from PPA ( i cannot found Nvidia 410 with Vulkan 1.1.83 for Mint 19)
Install Wine 3.16 with PPA , Install DXVK 0.80
Nothing more.

Get fresh steam from official site

user@M19:~$ steam
Setting up Steam content in /home/user/.local/share/Steam
Package libgl1-mesa-dri:i386 needs to be installed
Package libgl1-mesa-glx:i386 needs to be installed
Running Steam on linuxmint 19 64-bit
STEAM_RUNTIME is enabled automatically
Pins potentially out-of-date, rebuilding...

i press CTRL-C instead of entering password. 
I create backup and test it.

I test if allowed install it i get Glxvisuals failed  and SWRAST problem.
[spoiler]
user@M19:~$ steam
Package libgl1-mesa-dri:i386 needs to be installed
Package libgl1-mesa-glx:i386 needs to be installed
Running Steam on linuxmint 19 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Installing breakpad exception handler for appid(steam)/version(1536436120)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Installing breakpad exception handler for appid(steam)/version(1536436120)
Installing breakpad exception handler for appid(steam)/version(1536436120)
Gtk-Message: 15:52:48.145: Failed to load module "gail"
Gtk-Message: 15:52:48.146: Failed to load module "atk-bridge"
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

[/spoiler]

---

### Post by dj--alex on 2018-10-08
system with Mint 19
i install nvidia-utils 396


[https://pp.userapi.com/c830709/v830709191/1ab991/GGnGTMC57-c.jpg](https://pp.userapi.com/c830709/v830709191/1ab991/GGnGTMC57-c.jpg)

screenshot
I today done third reinstall Linux Mint 19 X64

I install only Nvidia-396 driver
Download steam-latest.deb and run install
Wine is NOT installed and PPA is not addded,   dpkg not added architecture i386

after install i get error message

Steam needs to install these additional packages:
libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] &#1087;&#1072;&#1088;&#1086;&#1083;&#1100; &#1076;&#1083;&#1103; user:

steam window console
I allow steam install this libraries.
(steam can correct fix this problem?)
reboot
and run steam and get

GLXCHOOSEVISUAL FAILED
libGL error: failed to load driver: swrast
[2018-10-08 20:32:29] Startup - updater built Sep 8 2018 19:20:58
glXChooseVisual failed
glXChooseVisual failedMain.cpp (326) : Assertion Failed: Fatal Error: glXChooseVisual failed
Main.cpp (326) : Assertion Failed: Fatal Error: glXChooseVisual failed

now reinstall Linux mint 19 x64 4-times...

why this error appears?
from 2010 to may 2018 i NEVER see this stupid cursed error

---

### Post by dj--alex on 2018-10-08
system with Mint 19
i install nvidia-utils 396


[https://pp.userapi.com/c830709/v830709191/1ab991/GGnGTMC57-c.jpg](https://pp.userapi.com/c830709/v830709191/1ab991/GGnGTMC57-c.jpg)

screenshot
I today done third reinstall Linux Mint 19 X64

I install only Nvidia-396 driver
Download steam-latest.deb and run install
Wine is NOT installed and PPA is not addded,   dpkg not added architecture i386

after install i get error message

Steam needs to install these additional packages:
libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] &#1087;&#1072;&#1088;&#1086;&#1083;&#1100; &#1076;&#1083;&#1103; user:

steam window console
I allow steam install this libraries.
(steam can correct fix this problem?)
reboot
and run steam and get
```

GLXCHOOSEVISUAL FAILED
libGL error: failed to load driver: swrast
[2018-10-08 20:32:29] Startup - updater built Sep 8 2018 19:20:58
glXChooseVisual failed
glXChooseVisual failedMain.cpp (326) : Assertion Failed: Fatal Error: glXChooseVisual failed
Main.cpp (326) : Assertion Failed: Fatal Error: glXChooseVisual failed
```

now reinstall Linux mint 19 x64 4-times...

why this error appears?
from 2010 to may 2018 i NEVER see this stupid cursed error

after all i install Steam-windows (steam native not works)
and install Unreal Tournament 3 and get error

```
01cd:fixme:gameux:GameExplorerImpl_VerifyAccess (0x2f737c8, L"Z:\\media\\user\\D\\Games\\Steam-win32\\steamapps\\common\\Unreal Tournament 3\\Binaries\\UT3.exe", 0x231eba8)
01cd:err:wgl:init_opengl Failed to load libGL: libGL.so.1: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1088;&#1072;&#1079;&#1076;&#1077;&#1083;&#1103;&#1077;&#1084;&#1099;&#1081; &#1086;&#1073;&#1098;&#1077;&#1082;&#1090;&#1085;&#1099;&#1081; &#1092;&#1072;&#1081;&#1083;: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
01cd:err:wgl:init_opengl OpenGL support is disabled.

```

---

### Post by dj--alex on 2018-10-09
With Linux MInt 19 is more serious error cannot be fixed
all tricks from Mint 18 cannot be used. 
Maybe i do something wrong? 



Video install process Linux Mint 19 x64 Mate DE
[https://www.youtube.com/watch?v=gmCqiHLQubw](https://www.youtube.com/watch?v=gmCqiHLQubw)
Instal on fresh system nvidia and steam , reboot, trying run steam, show work Unigine x64 game engine, trying run Panolapse and UT3.exe (32 bit applications)
[https://www.youtube.com/watch?v=p0mi7hqE0O4](https://www.youtube.com/watch?v=p0mi7hqE0O4)
MX Linux 17.1 september x64 with Mate DE
Instal on fresh system nvidia and steam , reboot, trying run steam, show work Unigine x64 game engine, trying run Panolapse and UT3.exe (32 bit applications)
[https://www.youtube.com/watch?v=Wt_nqWgGcTY](https://www.youtube.com/watch?v=Wt_nqWgGcTY)

gksu bug (another problem)
[https://www.youtube.com/watch?v=aZR_061stE0](https://www.youtube.com/watch?v=aZR_061stE0)

I write all here
[https://devtalk.nvidia.com/default/topic/1042427/linux/gtx-1080-steam-broke-driver-libgl-error-failed-to-load-driver-swrast/?offset=6#5288585](https://devtalk.nvidia.com/default/topic/1042427/linux/gtx-1080-steam-broke-driver-libgl-error-failed-to-load-driver-swrast/?offset=6#5288585)

Problem similar like in 18.3 but it in fresh install and it cannot be fixed by me.
I waste 20 days

---

