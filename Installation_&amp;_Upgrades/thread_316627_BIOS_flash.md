---
title: "BIOS flash"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by DapperMe17 on 2006-12-11
Using Ubuntu Edgy.....

1) I have the BIOS update, an .exe file.
2) I have a floppy formatted with FreeDOS
3) I have the BIOS .exe file on that floppy
4) I am able to boot to the FreeDOS startup, as well as type in the .exe file name to execute
5) Here's my stump...when I enter the name of that .exe file, I get a FreeDOS message similar to "FreeDOS is not able to execute this type of file", or somthing very similar to that.


What could I be doing incorrectly?


Thanks for any help!

---

### Post by irw on 2006-12-11
You probably need Windows to run it ... ](*,)

---

### Post by ciscosurfer on 2006-12-11
> **DapperMe17 said:**
> Using Ubuntu Edgy.....

1) I have the BIOS update, an .exe file.
2) I have a floppy formatted with FreeDOS
3) I have the BIOS .exe file on that floppy
4) I am able to boot to the FreeDOS startup, as well as type in the .exe file name to execute
5) Here's my stump...when I enter the name of that .exe file, I get a FreeDOS message similar to "FreeDOS is not able to execute this type of file", or somthing very similar to that.


What could I be doing incorrectly?


Thanks for any help!Check my signature, the first Flash BIOS link.  I was going to write a HOWTO specific to Ubuntu, but found this link quite helpful.

> **irw said:**
> You probably need Windows to run it ... ](*,)Nah, there's a way ;-)

EDIT: I've decided to go ahead a begin a write up.  It will probably be ready in 10 minutes or so if you want to wait.  I'll post the link once it's completed! :-)

EDIT: The writeup is complete but has to be approved by an Admin before posting.  More than likely I will simply add a new Flash BIOS link to my signature (you'll know it's for Ubuntu by the title of the link)

---

### Post by DapperMe17 on 2006-12-11
Fantastic

---

### Post by DapperMe17 on 2006-12-11
Will you be posting it to this thread???

---

### Post by ciscosurfer on 2006-12-11
> **DapperMe17 said:**
> Using Ubuntu Edgy.....

1) I have the BIOS update, an .exe file.
2) I have a floppy formatted with FreeDOS
3) I have the BIOS .exe file on that floppy
4) I am able to boot to the FreeDOS startup, as well as type in the .exe file name to execute
5) Here's my stump...when I enter the name of that .exe file, I get a FreeDOS message similar to "FreeDOS is not able to execute this type of file", or somthing very similar to that.


What could I be doing incorrectly?


Thanks for any help!Where did you grab the flashing files for your BIOS and what company makes your BIOS?

---

### Post by DapperMe17 on 2006-12-11
The flash .exe is directly from HP. 

BIOS in Kestrel (HP proprietary, or made for HP).

---

### Post by ciscosurfer on 2006-12-11
> **DapperMe17 said:**
> Will you be posting it to this thread???No, the thread will be posted in the Howto, FAQs, tricks section, but I will link to it from here once it gets approved.  Hang tight. :KS (it could be a little while though, so hold off on flashing until my Howto gets posted)...In the meantime, what is your BIOS manufacturer and where did you download the flashing files?

EDIT: nevermind, just saw your response post.

---

### Post by ciscosurfer on 2006-12-11
Can you provide me with the link to the flashing files on the HP site?

---

### Post by DapperMe17 on 2006-12-11
Thanks partner...much appreciated is your time & help!

...I owe ya

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv494en&lc=en&cc=us&dlc=en&product=57628&os=54&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv494en&lc=en&cc=us&dlc=en&product=57628&os=54&lang=en)

---

### Post by ciscosurfer on 2006-12-11
> **DapperMe17 said:**
> Thanks partner...much appreciated is your time & help!

...I owe ya

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv494en&lc=en&cc=us&dlc=en&product=57628&os=54&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv494en&lc=en&cc=us&dlc=en&product=57628&os=54&lang=en)You  need to be absolutely positive that the flashing tool and new BIOS file listed on this link is made specifically for your BIOS...Does the information on the link you provided me match what you have in your computer...Are you sure your machine is an HP Pavilion 8670C Desktop PC (US/CAN) [I'm only asking b/c you will run into a world of hurt if you download and use the wrong flashing tool, etc.] So, before we begin, we just need to be absolutely sure about this :KS

---

### Post by ciscosurfer on 2006-12-11
It seems as though HP only provides an .exe file and so believe it or not, you will probably have to run it on a Windows partition (at least run it to extract certain files -- the .exe is probably meant specifically for M$ -- the reason I disputed the fact that you wouldn't have to run it on M$ is because most manufacturers will provide you with other files to accomodate users of non-microsoft computers.)  This is a pain, I know.  Coincidentally, I had to do the same thing b/c my BIOS manufacturer only had a self-executable for Windows.  That executable came with two files and those two files I copied over to my Ubuntu partition to work on them, place them onto a FreeDOS-enabled CD, and flash my BIOS that way.  

Usually, the .exe will deflate and come with a flashing utility and a BIOS (.bios) file, with instructions on how to procedd manually barring a failed install via the Windows GUI.

I'm really sorry that I couldn't be of more help.  Try to run it at least once on your Windows partition (providing of course you have one) and then back to me.  Otherwise, there are a few sites on the web that provides BIOS updates for various manufacturer and they may have a better idea of how to go about flashing your BIOS when you don't run Windows.  As a last-ditch manuever, I would contact HP and request a solution.

EDIT: In general, manufacturers need to work on providing better files and instructions for their non-Windows clients.

** EDIT: I realized I could do something different (which I should've thought about before ](*,)).  I'm making a new post below to show you what I did!**

---

### Post by ciscosurfer on 2006-12-11
Okay.  So I downloaded the .exe and realized I could use unzip to deflate (or inflate, depending on how you look at it) the .exe file -- this is what I came up with and I'm posting the output of my commands and Readme.txt file as well...hopefully it will help you out!  If you want to view this yourself, you'll need unzip and can grab it here: [unzip app]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fu%2Funzip%2Funzip_5.52-8ubuntu1_i386.deb&md5sum=fa2dc8ceab3e62da227023a177c91bcb&arch=i386&type=main")

If you want a much more robust set of archiving apps, then you can issue the following in a terminal (universe and multiverse may need to be enabled)```
sudo aptitude update && sudo aptitude install rar unace unrar p7zip arj unzoo lha libarchive1 libarchive-tar-perl libarchive-zip-perl dpkg-dev
```This link may also be of assisstance to you: [http://www.nenie.org/misc/flashbootcd.html](http://www.nenie.org/misc/flashbootcd.html)

[U][B]MY OUTPUT
[/B][/U]
**unzip ~/kest_116.exe **
Archive:  ~/kest_116.exe
  inflating: BIOS.rom                
  inflating: Readme.txt              
  inflating: Enquire.COM             
  inflating: PFLASH2.EXE             
  inflating: Autoexec.bat            
04:23 AM

**cat Readme.txt **
This update loads BIOS version: 1.16 04/17/00

Before proceeding with the BIOS Update, use the following steps
to create a system bootable disk:

(1). Open My Computer
(2). Locate the 3 1/2 Floppy (A:) drive.
(3). Using the "Right" mouse button, click once.
(4). Using the "Left" mouse button, select FORMAT.
(5). Select "Copy System Files Only" and press START.
(6). Run this patch program to unzip the update onto this floppy.

Description:
------------
This update creates a BIOS Flash Utility Floppy for the following
Pavilion Models:

8500(D7202E-ABA), 8500(D7202F-ABA), 8500(D7202G-ABA),
8500(D7202H-ABA), 8500(D7202J-ABA), 8500(D7202K-ABA),
8500(D7202Q-ABA), 8500(D7202S-ABA), 8500(D7202T-ABA),
8500(D7202U-ABA), 8500(D7203F-ABA), 8500(D7203G-ABA),
8562(D9962A-ABA), 8565C(D7429A-ABA), 8595C(D7491A-ABA),
8608(D9980A-ARS), 8608(D9980A-UUB), 8609(D9981A-AB2),
8609(D9981A-ARS), 8609(D9981A-UUB), 8614(D9982A-ARS),
8614(D9982A-UUB), 8616(D9984A-ARS), 8616(D9984A-UUB),
8617(P1311A-UUB), 8618(D9985A-AB2), 8618(D9985A-ARS),
8618(D9985A-UUB), 8619(P1303A-ARS), 8630(P1118A-ABE),
8640(P1120A-ABE), 8650(P1106A-ABF), 8650(P1237A-ABS),
8650(P1246A-ABN), 8655(P1107A-ABF), 8655(P1305A-ABS),
8655(P1306A-ABN), 8660(P1124A-ABE), 8665(P1125A-ABE),
8670(P1094A-ABU), 8670(P1110A-ABF), 8670(P1239A-ABS),
8670(P1248A-ABN), 8670C(D9290A-ABA),
8675(P1111A-ABF), 8676C(D9299A-ABA),
9600I(D7203H-ABA), 9600I(D7203J-ABA),
9600I(D7203K-ABA), 9600I(D7203L-ABA),
9600I(D7203M-ABA), 9600I(D7203N-ABA),
9600I(D7203P-ABA), 9600I(D7203Q-ABA),
9680C(D9291A-ABA), 9682C(P1285A-ABA),
9690C(D9292A-ABA), 9692C(P1286A-ABA)


Installation Method:
--------------------
1. Restart the computer with this floppy disk in the A: drive.
2. Press Y at the prompt to proceed with the installation.
3. When a message box appears indicating the Flash Memory has
   been successfully programmed, remove the disk from the A: drive
   and restart the computer.
4. During the boot process, the following message will be displayed:

     0251: System CMOS checksum bad - Default configuration used
     Press <F1> to Setup, <F2> to Resume

5. Press F1 to enter SETUP
6. Press F5 to reset BIOS defaults.
7. Press F10 to exit SETUP saving your changes.
8. Press ENTER to confirm the save.


Technical Release Notes:
------------------------

1.00: Initial Release

1.01 08/23/99
1. Fix for USB keyboard lockup when no PS2 keyboard installed and BIOS tries to
   boot from the floppy drive with non-bootable diskette.
2. Fix for hitting F8 failed to invoke Win98 boot menu.
3. Added TNT reset patch.
4. Added TV Output select item.
5. Fix for ZIP failures with no ZIP diskette inserted.
   ZIP drives will not be reported to the OS when it's not selected as a boot
   device.
6. Changed PIII 666MHz to PIII 667MHz.
7. Added microcode update support Cu-Mine cA-2 stepping.
   Revision = 01.

1.02 09/03/99
1. Fix for Win2K installation failure.
2. Fix for exclamation mark error in Device Manager when USB mouse installed
   without PS2 mouse attached.
3. Fix for PIII 667MHz error detected as 664Mhz.

1.03 09/07/99
1. Fix for system hang during recovery CD boot sometimes.
2. Fix for some mode 1 CD format boot failure.

1.04 09/27/99
1. Fix for Windows 2000/98 boot failure when installed memory size >= 256MB.
2. Fix for boot failure when HDD size > 32GB.
3. IRQ 5 reserved when Chameleon installed.
4. VIA recommended setting: Flush FIFO before generating IDE interrupt.
   Set 596.IDE.71.0 & 596.IDE.79.0 to 1.

1.05 10/19/99
1. Added support for boot from any IDE CD-ROM.
2. No extra dummy reset for onboard TNT if add-on card plugged.
3. Changed USB Legacy Support default to Auto.

1.06 10/25/99
1. Never allow INT 19 to be hooked.
2. IRQ 5 reserved when Aureal 8810 installed.

1.07 10/29/99
1. Always enable PCI to DRAM posted write feature.

1.08 11/08/99
1. Fix for some PC100 module boot failure when FSB running at 133MHz.

1.09 11/23/99
1. Reserved only IRQ 12 for PS2 mouse.
2. Incorporated new HP logo.

1.09a 11/24/99
1. Fix for HP logo background color incorrect.

1.10 12/06/99
1. In-Order-Queue set to 1-Level.
2. PCI Delayed Transaction disabled.
3. CPU microcode update:
   672: updated to revision 10
   673: updated to revision 0E
   681: updated to revision 0D

1.11 01/03/00
1. Fix for Network transmission failure with large files.
   Set PCI Master Bus Time-Out to 2x32 PCICLKs.

1.12 01/26/00
1. Fix for LS120 boot unsuccessful when primary channel was installed with
   HDD/LS120, and secondary channel was installed with a CD-RW.

1.13 02/01/00
1. Revised code for ATAPI drives reset.

1.14 02/02/00
1. Disabled Split REQ Change Channel bit.
   This resolves the DVD hang problem with the CD-E version of 82C693.
2. Revised USB Legacy support for 596B CE version.

1.16 04/17/00
1. Added microcode update block for Coppermine B-0 stepping.
   CPUID = 683h. Patch ID = 0Ch.
2. Changed Parallel Port Mode default to Normal.

---

### Post by ciscosurfer on 2006-12-11
Here's the link to my new HOWTO located in the howtos, faqs, tips category: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")[]("http://ubuntuforums.org/showthread.php?t=316639")
You can also find it in my signature below this post: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

[B]@DapperMe17,

* (Read all info I've provided before proceeding).*[/B]

You have two options: you can unzip the appropriate files I list below, then run the syntax I present just after this sentence, or you can unzip all of the files, reboot, and follow the instructions with the floppy placed in the drive.  The choice is up to you.
The specifc syntax that you can enter at the FreeDOS prompt once you get your files transfered over will be:
```
pflash2 /AUTO:BIOS.ROM /C /RESET
```Then hit CTRL-ALT-DEL to reboot and enjoy your new BIOS!

***_space_ = hit the spacebar***

I believe you can also copy over the Autoexec.bat file and it will run it for you.  In this case you should copy over all files you've unzipped (PFLASH.exe, BIOS.rom, Enquire.COM, Autoexec.bat)  The choice is yours!  You can check out the Readme.txt file that was unzipped for further information and remember to include spaces where neccesary when running the above bios flashing code

pflash2***_space_***/AUTO:BIOS.ROM***_space_***/C***_space_***/RESET 

(Read all info I've provided before proceeding).

---

### Post by DapperMe17 on 2006-12-12
Ciscosurfer...AAA+ effort! ...just back online now.

After reading all your information, Ii think the easiest way would be to....

1) unzip the .exe file to desktop, then copy to freeDOS floppy
2) Restart PC with floppy installed
3) Run Code at FreeDOS prompt...pflash2 /AUTO:BIOS.ROM /C /RESET

4) Then hit CTRL-ALT-DEL to reboot and enjoy your new BIOS!


Yes, the pc in question IS that model, and is still in stock configuration. I only have the Ubuntu partitions, no Winblows. 


I'm not having any unusual issues with the PC (as they say, don't fix which ain't broken:)). The reason why I'd like to flash is the mobo is not recognizing any wireless "g" standard pci cards. I do realize that this may have been a common issue with older HP machines, but have not been able to find any information in Google, or at the HP forum.

After looking through the BIOS update list, there are a couple of interesting updates, but nothing that looks like any major upgrades.


If I choose to go for it, I'll assume that the way I have indicated above will suffice...

Kudos!


PS...already have the program "unzip" from repository, but can't locate it???

---

### Post by ciscosurfer on 2006-12-12
You can probably copy all those files over to your floppy and then simply reboot with the floppy in the drive -- the Autoexec.bat file should take over at that point.

If you'd like more infomation, and a real HOWTO, then take a look at the new one I created here: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

Glad you liked the info -- and it was fun to research and write up!

If you ever need any extra help or come up with any questions that you'd like to ask, please feel free to PM me or shoot me an email.  If I'm online, then my instant messengers should be up as well.  Take care!

---

### Post by DapperMe17 on 2006-12-12
Typical noobie snag:-D ...already have the program "unzip" from repository, but can't find it...???

Thanks again for all you've researched. You really went out of your way, I appreciate it.

And, any "arch-rival" Windblows questions you "even care" to consider...please do the same, or just destroy that disk!!!

I really don't hate Win, just enjoying the new experience with this thing you  call Linux, for my lovely better-half's older, hand-me-down PC. No need to "punish" with 98 & time to update to something new & shiney:D, without the bloat.

---

### Post by ciscosurfer on 2006-12-12
You can download unzip from these locations:
  1.  For Dapper: [http://tinyurl.com/yko7gk]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fu%2Funzip%2Funzip_5.52-6ubuntu4_i386.deb&md5sum=c7f0fff7ec83ab3d8886334297b4f84a&arch=i386&type=main") 
  2.  For Edgy: [http://tinyurl.com/ygszts]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fu%2Funzip%2Funzip_5.52-8ubuntu1_i386.deb&md5sum=fa2dc8ceab3e62da227023a177c91bcb&arch=i386&type=main")

Once you've done that, if you're downloading via Firefox, the default location for downloaded files in the Desktop.  You need to change directories or simply go to your Desktop and (double) click on the unzip.deb file to install it.  Once installed, you can run the unzip *blahblah* command from the a terminal.

---

### Post by DapperMe17 on 2006-12-12
Ok, I just inflated the files...now, where would I find them?


UPDATE...justfound them in the home folder!

Will let you know how it goes.

---

### Post by DapperMe17 on 2006-12-12
Too bad...fried something.

Nah...just pulling your leg!!!

Cisco, your directions worked like a charm! 

I unzipped the .exe, transferred all to the FreeDOS formatted floppy, rebooted and followed the onscreen instructions after the BIOS was automatically flashed. 

All went perfect!



ps...forget Bamma for Prez, you better get your running shoes on my friend!

Thanks for helping a learning soul! It's a forum like this one that helps Ubuntu stand shoulders above all other OS's;) 


If you ever need a test "dummy", feel free to call on me.

---

### Post by ciscosurfer on 2006-12-12
For a brief moment, my heart and stomach completely sank. #-o

Of course, then I read the next line! \\:D/   

Congrats on the new BIOS!! =D> 

PS I don't know...I think BA has a better shot than HC...but we'll see! :-k

---

### Post by ciscosurfer on 2006-12-14
You can go on over to my [HOWTO]("http://ubuntuforums.org/showthread.php?t=318789") and vote in a poll now!  Yay!

---

