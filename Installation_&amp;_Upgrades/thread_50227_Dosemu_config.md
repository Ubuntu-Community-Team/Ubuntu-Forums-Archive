---
title: "Dosemu config"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by FoxTerrier on 2005-07-19
Hi,

I need to install a rpogram made in clipper for DOS. I've installed DOSEMU and copyed the information I need to the directory, so I can see it running DOS in DOSEMU ( it's set to the default mode)
I need to make an autoxec.bat and a config.sys like this:

Autoexec.bat
@ECHO OFF



PATH C:\DOS\COMMAND;C:\DOS

SET TEMP=C:\DOS

set rede=1

set clipper=f150

LH MODE COM1 9600,n,8,1

LH MODE COM2:9600,N,8,1

rem - By Windows Setup - C:\DOS\MOUSE.COM

lh mode con codepage prepare=((850) C:\W98\COMMAND\ega.cpi)

LH  mode con codepage select=850

LH  keyb po,,C:\DOS\COMMAND\keyboard.sys

MODE LPT1:,,P >nul

PATH=%PATH%;C:\HPLJUTIL



-----------------------------------------------------



Config.sys



DEVICE=C:\DOS\HIMEM.SYS

DEVICE=C:\DOS\EMM386.EXE NOEMS

BUFFERS=20,0

FILESHIGH=150

DOS=HIGH,UMB

LASTDRIVE=Z

FCBS=4,0

DEVICEHIGH =C:\DOS\SETVER.EXE

DEVICEHIGH =C:\DOS\COMMAND\DISPLAY.SYS CON=(EGA,,1)

COUNTRY=351,850,C:\DOS\COMMAND\COUNTRY.SYS

Can anyone help with this problem? I know I can't edit directly the DOSEMU autoexec and config files.


Thank's in advance
Pedro

---

