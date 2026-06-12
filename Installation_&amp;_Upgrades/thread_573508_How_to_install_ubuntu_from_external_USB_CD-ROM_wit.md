---
title: "How to install ubuntu from external USB CD-ROM without BIOS &quot;boot&quot; support?"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by romkeris on 2007-10-11
I have only hard drive and floppy boot support. USB doesn't boot too.

Thanks.

---

### Post by Pumalite on 2007-10-11
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by romkeris on 2007-10-12
Thanks Pumalite.

But I want to know if there is another method. For example like: maybe there is a bootable floppy which software boots a USB CD-ROM. I know that is possible with internal CD-ROM's. I have tryed some software, but no luck with external.

Thanks

---

### Post by scapalexis888 on 2007-10-12
Net install is your best choice. Other methods are complicated and not worth your time

---

### Post by romkeris on 2007-10-12
Maybe somebody has already made a bootable floppy with such software and can upload it's image. So i will not have to seek for another computer everytime when I just want to try live-cd's or install.

thanks

---

### Post by romkeris on 2007-10-14
Any suggestions?

---

### Post by romkeris on 2007-10-14
Wakepup bootable floppy does half a thing. It's loads external DVD-ROM drivers and loads puppylinux livecd (tested). Maybe someone moore experienced, can change what it could load ubuntu instead of puppylinux.

---

### Post by romkeris on 2007-10-16
Here is autoexec.bat file.

rem Init
cls
set drv=

rem Using SHSUCDX.COM 3.03, a freeware replacement for MSCDEX.EXE
rem Assign 1st IDE-CD to drive X:, 2nd (if found) to drive Y: and USB-CD to drive Z:
driver\SHSUCDX /D:?IDE-CD,X,,2 /d:?USB-CD,Z,,1 /QQ

echo Checking any IDE drive for marker file IDEHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\idehd set drv=%%x:
if "%drv%"=="" goto try_usbhd
set media=idehd
goto optmenu

:try_usbhd
echo.
echo Checking any USB drive for marker file USBHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbhd set drv=%%x:
if "%drv%"=="" goto try_usbflash
set media=usbhd
goto optmenu

:try_usbflash
echo.
echo Checking any USB drive for marker file USBFLASH...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbflash set drv=%%x:
if "%drv%"=="" goto try_cd
set media=usbflash
goto optmenu

:try_cd
echo.
echo Checking IDE or USB CD-ROM drive for file INITRD.GZ...
for %%x in ( X Y Z ) do if exist %%x:\initrd.gz set drv=%%x:
if "%drv%"=="" goto failed
if "%drv%"=="X:" set media=idecd
if "%drv%"=="Y:" set media=idecd
if "%drv%"=="Z:" set media=usbcd

:optmenu
echo ...file found on %media%, drive %drv%
echo.
echo É&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;»
echo &#343; Select Puppy2 boot option &#343;
echo &#290;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;¹
echo &#343; &#343;
echo &#343; 1. acpi=on Default for newer PCs (made 2002 or later) &#343;
echo &#343; &#343;
echo &#343; 2. acpi=off For older PCs, or use if acpi=on causes problems &#343;
echo &#343; &#343;
echo &#343; 3. acpi=force Needed to force acpi=on on older PCs &#343;
echo &#343; &#343;
echo &#268;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;¼
echo.
choice /C:123 Please choose :
if "%errorlevel%"=="1" set acpi=acpi=on
if "%errorlevel%"=="2" set acpi=acpi=off
if "%errorlevel%"=="3" set acpi=acpi=force

set append=root=/dev/ram0 PMEDIA=%media% %acpi%
echo.
LINLD.COM image=%drv%\vmlinuz initrd=%drv%\initrd.gz "cl=%append%"
goto end

:failed
echo.
type FAILMSG.TXT

:end

---

### Post by mickeyWD on 2007-10-24
Hi romkeris,
I need the same tool
can I have the bootable floppy? thank you

---

### Post by mickeyWD on 2007-10-24
Hi romkeris,
I've found this:[http://paulsiu.wordpress.com/2007/09/29/booting-acronis-trueimage-from-usb-even-when-your-bios-does-not-support-usb-boot/#comment-2009](http://paulsiu.wordpress.com/2007/09/29/booting-acronis-trueimage-from-usb-even-when-your-bios-does-not-support-usb-boot/#comment-2009)

But trying it cdrom stop working and messages says that a pup_xxx.fsf file is needed.
Have you had a better luck?

Someone else can surely help us.
This is my autoexec.bat:```
@echo off
rem wakepup2 0.2 (C) 2006, Paul Akterstam ('pakt' on Puppy Linux Forum)
rem Boot diskette for Puppy 2.xx series. For Puppy 1.xx series, use wakepup
rem This version for IDE/USB drives (built-in or external CD-ROM, HD and flash)
rem Inspired by Barry Kauler's BOOT2PUP (http://www.puppyos.com)
rem Except for the drivers, uses only GPL'd software or freeware
rem Requires FreeDOS & FreeCOM

rem This program is distributed in the hope that it will be useful, but
rem WITHOUT ANY WARRANTY; without even the implied warranty of
rem MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
rem General Public License for more details.

rem The GNU General Public License is available from http://www.fsf.org/
rem or, write to the Free Software Foundation, Inc., 59 Temple Place,
rem Suite 330, Boston, MA 02111 USA

echo.
echo   ***  wakepup2 0.2 by pakt - Boot Puppy2 Linux from IDE/USB drives  ***
rem Pause here so USB driver messages can be read...
echo Pausing for driver messages. Press any key to continue or Ctrl-C to abort...
pause >NUL

rem Init
cls
set drv=

rem Using SHSUCDX.COM 3.03, a freeware replacement for MSCDEX.EXE
rem Assign 1st IDE-CD to drive X:, 2nd (if found) to drive Y: and USB-CD to drive Z:
driver\SHSUCDX /D:?IDE-CD,X,,2 /d:?USB-CD,Z,,1 /QQ

echo Checking any IDE drive for marker file IDEHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\idehd set drv=%%x:
if "%drv%"=="" goto try_usbhd
set media=idehd
goto optmenu

:try_usbhd
echo.
echo Checking any USB drive for marker file USBHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbhd set drv=%%x:
if "%drv%"=="" goto try_usbflash
set media=usbhd
goto optmenu

:try_usbflash
echo.
echo Checking any USB drive for marker file USBFLASH...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbflash set drv=%%x:
if "%drv%"=="" goto try_cd
set media=usbflash
goto optmenu

:try_cd
echo.
echo Checking IDE or USB CD-ROM drive for file INITRD.GZ...
for %%x in ( X Y Z ) do if exist %%x:\initrd.gz set drv=%%x:
if "%drv%"=="" goto failed
if "%drv%"=="X:" set media=idecd
if "%drv%"=="Y:" set media=idecd
if "%drv%"=="Z:" set media=usbcd

:optmenu
echo ...file found on %media%, drive %drv%
echo.
echo &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#891;
echo &#65533;                     Select Puppy2 boot option                     &#65533;
echo &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 
echo &#65533;                                                                   &#65533;
echo &#65533;  1. acpi=on      Default for newer PCs (made 2002 or later)       &#65533;
echo &#65533;                                                                   &#65533;
echo &#65533;  2. acpi=off     For older PCs, or use if acpi=on causes problems &#65533;
echo &#65533;                                                                   &#65533;
echo &#65533;  3. acpi=force   Needed to force acpi=on on older PCs             &#65533;
echo &#65533;                                                                   &#65533;
echo &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#892;
echo.
choice /C:123 Please choose :
if "%errorlevel%"=="1" set acpi=acpi=on
if "%errorlevel%"=="2" set acpi=acpi=off
if "%errorlevel%"=="3" set acpi=acpi=force

set append=root=/dev/ram0 ramdisk_size=8192 %acpi%
echo.
LINLD.COM image=%drv%\install\vmlinuz initrd=%drv%\install\initrd.gz "cl=%append%"
goto end

:failed
echo.
type FAILMSG.TXT

:end



```

---

### Post by romkeris on 2007-10-25
I havn't had time yet to try moore. But if i'll find  something i'll post it.
It's good to hear that I'm not alone searching for solution. :)

---

### Post by mickeyWD on 2007-10-25
No, you are not alone.
I think this is a good piece of software.
I've tried it with Puppy linux and
wonderful,
it works, Puppy live from external CD and no burned other CD or netwotk connection.
I hope someone else here can care about it.
Is a method to install Ubuntu as "installing from Knoppix" or "with SmartBootManager".
If there'll be a solution I think that many more people will use it!

For now maybe is good move adding Wakepup in thread title, after "?" :-D
Do you agree?

I'm looking for something else. Stay tuned.

---

### Post by romkeris on 2007-10-25
it's a pitty that popular linux distributions, who want to spread linux worldwide do not care to include such methot for booting from external drive as puppy does.
Many people  don't bother searhing for this solution, they install other network and forget it, but we don't :)).

---

### Post by mickeyWD on 2007-10-25
WOWOW !!!!!
romkeris,
I'll do it
Ubuntu alternate started with WAKEPUP 2.02 
Thank you
Thank you
=D>

---

### Post by romkeris on 2007-10-25
Try to change in autoexec.bat pieces to the folowing, then istalling from ubuntu CD. For me that almost worked, but stopped in the middle.

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
:try_cd
echo.
echo Checking IDE or USB CD-ROM drive for file INITRD.GZ...
for %%x in ( X Y Z ) do if exist %%x:[COLOR="Red"]\casper\[/COLOR]initrd.gz set drv=%%x:
if "%drv%"=="" goto failed
if "%drv%"=="X:" set media=idecd
if "%drv%"=="Y:" set media=idecd
if "%drv%"=="Z:" set media=usbcd

"""""""""""""""""""""""""


[COLOR="Red"]LINLD.COM image=%drv%\casper\vmlinuz initrd=%drv%\casper\initrd.gz "cl=%append%"[/COLOR]


""""""""""""""

---

### Post by romkeris on 2007-10-25
> **mickeyWD said:**
> WOWOW !!!!!
romkeris,
I'll do it
Ubuntu alternate started with WAKEPUP 2.02 
Thank you
Thank you
=D>

How did you reach it? Did you change something in wakepuppy?

---

### Post by romkeris on 2007-10-25
Here is floppy image for booting puppylinux.
[http://www.murga-linux.com/puppy/viewtopic.php?mode=attach&id=1685&sid=d1674630fffa32eb539a198f8bd6bab6](http://www.murga-linux.com/puppy/viewtopic.php?mode=attach&id=1685&sid=d1674630fffa32eb539a198f8bd6bab6)
you may use winimage to write it on flpooy
You have also to download puppylinux CD image, write it on CD, put it in your external cd-rom and boot from downloaded floppy image.

If somebody succesfully loaded ubuntu using wakepup as mickeyWD please, write that. It's good to hear :)

---

### Post by mickeyWD on 2007-10-26
> **romkeris said:**
> Try to change in autoexec.bat pieces to the folowing, then istalling from ubuntu CD. For me that almost worked, but stopped in the middle.

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
:try_cd
echo.
echo Checking IDE or USB CD-ROM drive for file INITRD.GZ...
for %%x in ( X Y Z ) do if exist %%x:[COLOR="Red"]\casper\[/COLOR]initrd.gz set drv=%%x:
if "%drv%"=="" goto failed
if "%drv%"=="X:" set media=idecd
if "%drv%"=="Y:" set media=idecd
if "%drv%"=="Z:" set media=usbcd

"""""""""""""""""""""""""


[COLOR="Red"]LINLD.COM image=%drv%\casper\vmlinuz initrd=%drv%\casper\initrd.gz "cl=%append%"[/COLOR]


""""""""""""""

When stopped?
Why casper? I've an /install dir on ubuntu alternate! :-D and finally I've Xubuntu running on that pc!

---

### Post by romkeris on 2007-10-26
> **mickeyWD said:**
> When stopped?
Why casper? I've an /install dir on ubuntu alternate! :-D and finally I've Xubuntu running on that pc!

i'm glad you do, with my help :)

On desktop ubuntu CD linux load files are in casper directory.

with desktop edition my boot stops at:

12.840000] SCSI device sdb: 2880 512-byte hdwr sectors (1 MB)
12.904000] sdb: Hrite Protect is off
12.904000] sdb: assuming drive cache: write through
12.904000] sdb: unknown partition table 
13.982000] sd 3:0:0:0: Attached scsi removable disk sdb t   
13.9920001 sd 3:0:0:0: Attached scsi generic sg2 type 0 
14.004000] srl: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
14.008000] sr 2:0:0:0: Attached scsi generic sg3 type 5


[COLOR="Blue"] ALREADY TESTED:

WAKEPUP2.02 BOOT FLOPPY LOADS UBUNTU ALTERNATE INSTALLATION USING EXTERNAL USB CD/DVD-RW/ROM!!!

ENJOY ANOTHER METHOD OF INSTALLING UBUNTU IN THIS SITUATION [/COLOR]


but yau have to modify autoexec.bat in floppy to the following (red words are new):



@echo off
rem wakepup2 0.2 (C) 2006, Paul Akterstam ('pakt' on Puppy Linux Forum)
rem Boot diskette for Puppy 2.xx series. For Puppy 1.xx series, use wakepup
rem This version for IDE/USB drives (built-in or external CD-ROM, HD and flash)
rem Inspired by Barry Kauler's BOOT2PUP ([http://www.puppyos.com](http://www.puppyos.com))
rem Except for the drivers, uses only GPL'd software or freeware
rem Requires FreeDOS & FreeCOM

rem This program is distributed in the hope that it will be useful, but
rem WITHOUT ANY WARRANTY; without even the implied warranty of
rem MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
rem General Public License for more details.

rem The GNU General Public License is available from [http://www.fsf.org/](http://www.fsf.org/)
rem or, write to the Free Software Foundation, Inc., 59 Temple Place,
rem Suite 330, Boston, MA 02111 USA

echo.
echo   ***  wakepup2 0.2 by pakt - Boot Puppy2 Linux from IDE/USB drives  ***
rem Pause here so USB driver messages can be read...
echo Pausing for driver messages. Press any key to continue or Ctrl-C to abort...
pause >NUL

rem Init
cls
set drv=

rem Using SHSUCDX.COM 3.03, a freeware replacement for MSCDEX.EXE
rem Assign 1st IDE-CD to drive X:, 2nd (if found) to drive Y: and USB-CD to drive Z:
driver\SHSUCDX /D:?IDE-CD,X,,2 /d:?USB-CD,Z,,1 /QQ

echo Checking any IDE drive for marker file IDEHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\idehd set drv=%%x:
if "%drv%"=="" goto try_usbhd
set media=idehd
goto optmenu

:try_usbhd
echo.
echo Checking any USB drive for marker file USBHD...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbhd set drv=%%x:
if "%drv%"=="" goto try_usbflash
set media=usbhd
goto optmenu

:try_usbflash
echo.
echo Checking any USB drive for marker file USBFLASH...
for %%x in ( C D E F G H I J K L M N O P Q R S T U V W ) do if exist %%x:\usbflash set drv=%%x:
if "%drv%"=="" goto try_cd
set media=usbflash
goto optmenu

:try_cd
echo.
echo Checking IDE or USB CD-ROM drive for file INITRD.GZ...
for %%x in ( X Y Z ) do if exist %%x:[COLOR="Red"]**\install**[/COLOR]\initrd.gz set drv=%%x:
if "%drv%"=="" goto failed
if "%drv%"=="X:" set media=idecd
if "%drv%"=="Y:" set media=idecd
if "%drv%"=="Z:" set media=usbcd

:optmenu
echo ...file found on %media%, drive %drv%
echo.
echo É&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;»
echo &#343;                     Select Puppy2 boot option                     &#343;
echo &#290;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;¹
echo &#343;                                                                   &#343;
echo &#343;  1. acpi=on      Default for newer PCs (made 2002 or later)       &#343;
echo &#343;                                                                   &#343;
echo &#343;  2. acpi=off     For older PCs, or use if acpi=on causes problems &#343;
echo &#343;                                                                   &#343;
echo &#343;  3. acpi=force   Needed to force acpi=on on older PCs             &#343;
echo &#343;                                                                   &#343;
echo &#268;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;&#310;¼
echo.
choice /C:123 Please choose :
if "%errorlevel%"=="1" set acpi=acpi=on
if "%errorlevel%"=="2" set acpi=acpi=off
if "%errorlevel%"=="3" set acpi=acpi=force

set append=root=/dev/ram0 PMEDIA=%media% %acpi%
echo.
**[COLOR="Red"]LINLD.COM image=%drv%\install\vmlinuz initrd=%drv%\install\initrd.gz "cl=%append%"[/COLOR]**
goto end

:failed
echo.
type FAILMSG.TXT

:end

---

