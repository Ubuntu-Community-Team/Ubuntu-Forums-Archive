---
title: "Installing MS Office Xp in WINE"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Trilby on 2010-04-08
I have a copy of *MS Office Standard for Students and Teachers* which I want to run in *Wine 1.0.1*. The install .exe on the CD-rom runs fine but when it comes to actually installing the programs, I get the message shown in attachment 1. Clicking on the "click here" link gives attachment 2.

Hope someone can help.

My computer:
Acer Aspire 7730
Ubuntu 9.10 64 Bit

---

### Post by phillw on 2010-04-08
Hi,

having had a quick look at winehq [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) it looks like it should run quite happily.

Most wine threads i come accross say to use the latest development version of wine, you can see from that link that they tested it with 1.1.32 and 1.1.40

Ubuntu forums have a wine area over at [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)  which is good place to head for information on using wine with Ubuntu and getting the development version.

Hope that helps.

However, I do wonder what you cannot do in OpenOffice that needs MS Office - but that is a completely different discussion :-)

Regards,

Phill.

---

### Post by Trilby on 2010-04-08
> **phillw said:**
> Hi,
However, I do wonder what you cannot do in OpenOffice that needs MS Office - but that is a completely different discussion :-)


Good question.
I prefer MS Office to Open, although the later has come a long way from where it was. I've was using Xp Office for several years and like it over any other package I've used, for example 2007 (which is frankly awful). Open's word processor is good for straight text typing but doesn't handle images very well and I dislike their spreadsheet application. I also have a copy of MS Office which I might as well use -- doing so will allow me to move to using Ubuntu for virtually everything except games.

That said, I welcome the day I can completely do without any MS products on my laptop.

---

### Post by Trilby on 2010-04-08
I installed the latest version of wine but the same thing happens as before.

---

### Post by Kellemora on 2010-04-08
Hi Trilby

I'm very surprised at your response regarding images in msWord!

Before I retired a couple of months ago, we published many of those Tri-Folds you pick up at tourist traps.

Slightly over two years ago, we switched our entire office over to Open Office BECAUSE Open Office Writer DID NOT mangle the images the way msWord did (scattering them all over the place at printing time).
AND Open Office is NOT printer dependent as msWord is.....
msWord uses your printer to obtain it's margins, switch printers and images fly all over the place.
We've NEVER had a problem using any printer, crash printer or offset mask with Open Office Writer!
After a short learning curve, switching our entire office from Mickey$oft to Ubuntu Hardy increased productivity exponentially.....
The ONLY things we used the WinDOZE for were our commercial grade 12x18 scanners and Accounting programs linked to the POS equipment.
And even a few of those manufacturers are FINALLY providing Linux drivers with their equipment now, unfortunately many are RedHat (CentOS) based, not Debian based for Ubuntu, but it's headway!

TTUL
Gary

---

### Post by Trilby on 2010-04-08
> **Kellemora said:**
> 
I'm very surprised at your response...


That's kinda beside the point, besides I did say:

> **Trilby said:**
> 
I welcome the day I can completely do without any MS products  on my laptop.


I'm glad you like Open Office so much. It just happens I want to install MS Office Xp on my computer. That doesn't mean I'll never use Open Office (which I do use occationally). I like to be versitile and might as well get my money's worth from MS.

Thanks

---

### Post by stilling on 2010-04-08
more easy than you think 
sudo wget [http://deb.playonlinux.com/playonlinux_squeeze.list](http://deb.playonlinux.com/playonlinux_squeeze.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

then open it and add microsoft office 2007 that is in his menu or games he automaticaly gets what he needs for your program of course you need the the office installer cd


hope that this helps others like it helped me

---

### Post by Trilby on 2010-04-08
@stilling

Will that work just as well with Office Xp?

---

### Post by stilling on 2010-04-08
so you need the microsoft office 2007 cd install playonlinux you will find that on your games tab start it then hit add search the game ... microsoft office select it and he will ask for your cd it installs like in windows and works the same

---

### Post by Trilby on 2010-04-08
> **stilling said:**
> so you need the microsoft office 2007 cd install playonlinux you will find that on your games tab start it then hit add search the game ... microsoft office select it and he will ask for your cd it installs like in windows and works the same

It's not the 2007 version, it's the Xp version. It doesn't appear on the list of programs on Play on Linux.

---

### Post by stilling on 2010-04-08
sorry did not looked well xp = 2003 if i remember well so for that
After wine has been installed
Put your MS office 2003 cd in your drive and in terminal type following:
cd /media/cdrom0
wine autorun.exe
And follow instructions as if you were installing it on windows.
Now on your desktop right click -->Create launcher for each below
Create launchers for each application:
in Command field type this
For excel
env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\EXCEL.EXE"
For Word
env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE"
For powerpoint
env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\POWERPNT.EXE"
For Access
env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\MSACCESS.EXE"
You are almost done.
Now if you are having problem running your macro then you need to install Dcom98.
Dcom98 contains three dlls from Windows 98: ole32, oleaut32, and rpcrt4. Use winetricks to install it:
In terminal type:
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks dcom98
The winetricks script will set to override globally, and if you have any other programs installed in that wineprefix it may affect them. If that happens, you can fix it through winecfg.
if you dont have autorun.exe on your cd or setup.exe that installs all the features install it one by one microsoft word , excel , powerpoint, access
that will be all i think

hope this helps you

---

### Post by Trilby on 2010-04-09
> **stilling said:**
> sorry did not looked well xp = 2003 if i remember well so for that
hope this helps you

Office Xp* is not 2003 -- It was released in 2001. There is no "autorun.exe". There is a "setup.exe" which I was runing before. With terminal, I get:

```

MY_COMPUTER'S_NAME:/media/cdrom0$ wine setup.exe
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:LookupAccountNameW (null) L"mark" (nil) 0x33f380 (nil) 0x33f384 0x33f378 - stub
fixme:advapi:LookupAccountNameW (null) L"mark" 0x138890 0x33f380 0x138de8 0x33f384 0x33f378 - stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
err:msi:ITERATE_Actions Execution halted, action L"CADpc" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
MY_COMPUTER'S_NAME:/media/cdrom0$ fixme:imm:ImmDisableIME (-1): stub

```EDIT: *Also, know as MS Office 10.0**.
EDIT 2: **Not to be confused with MS Office 2010 (ie MS Office 12)

---

