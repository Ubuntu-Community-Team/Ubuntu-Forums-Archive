---
title: "Advice for newbies like myself"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by johnson094 on 2010-08-29
Hi, I am a newbie and as of 3 days ago I had never laid eyes on Ubuntu. My son has been trying to get me to switch for some time now, so I have spent the last three days downloading, burning, backing up, formating, booting, uninstalling, reburning, downloading, reinstalling, booting and on and on and on. Finally I took a deep breath wrote down all the errors I had been getting and began to read these forums. Everyone seemed to say try this or try this or else they offered solutions that involved what appeared to require a masters degree in code writing. I kept at it..I tried those solutions which seemed to apply and kept a log of any errors at the point of the program failing. I then went back and searched and read.
 
Over the last days and nights I have tried to install 10.4 and 9.10 for 32 bit desktops. I payed close attention to forum posts that not only reflected my install problems but my hardware as well. I have a 7 year old HP Intel Pentium 386 with 1 gb ram, and dual HD (250/300 gb). That led me to download and try the versions for x86 desktops. I then got my install to progress to the point of partitioning. I thought maybe my computer wouldn't run the newer versions so I tried Version 8.10 and at this point found the x86 Alternative versions. This is when I finally saw a hint of impending success. I actually completed the live disk install and was ready to remove the CD and reboot. 
 
I then started getting an error "init rc-default main process (4119) killed by SEVG signal". Going back to the forums I came across this error and someone mentioned disabling graphics card and connecting to onboard video output. Simple fix and it worked! Rebooted and got to the Login page...entered name/password and "blank tan screen with functional mouse" would not respond to Contol/alt/delete had tocut power to reboot . Searched forum and finally Google using phrase "Ubuntu blank page after login" and found this solution: [http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/](http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/)
 
It was easy, even for me, and best of all it worked. I ended up sending my son a success email from inside Ubuntu. Right now I have upgraded all the files for 8.10 and now am installing 9.04 upgrade. 
 
Just wanted to share this with other newbies. Don't be like me and fail to do the prep work, and certainly be persistent about reading the information in these forums even though for newbies alot of it seems like "Greek". I still have a long way to go with updatng drivers, setting up hardware, and installing software. I didn't mention earlier that my installation was a dual boot with Windows Vista on the sideline.
 
Thanks to all of you who respond to the newbies.

---

### Post by davidmohammed on 2010-08-29
welcome and well done for persisting.

I'm intrigued - when you tried to plug in your 10.04 disk and used "try without installing" - what happened?

May be with help from the forums, we can shortcut your adventure from 8.04 - 8.10 - 9.04 - 9.10 - 10.04.....

it would be helpful if you could post your hardware details.  From a terminal session type

lspci
lsusb

post the contents displayed here in a reply.

---

### Post by johnson094 on 2010-08-29
The 10.04 version worked on my newer computer in Try it mode, would not even boot in i386 computer. That's after checking boot order in cmos etc. Same scenario as others who were trying to install to an older x86. That's why I knew it had to be something about the older computer. I have just finished upgrading 8.10, to 9.04. now have 9.10. Think I'll sit there until I get everything situated and running halfway right. Some issues with 9.10:
 
When I first rebooted the computer it progressed to just before the login screen showing a pale purple screen with Uguntu logo and status bar pulsing. I timed it, it spent 5 sec on that screen, then 5 sec gray screen, then 5 sec black screen then back to the logo screen. This kept up for probably 10-12 min until I had to actually kill the power to reboot. Upon reboot it did the same thing tnen after 5 minutes it finally presented the log on screen and I logged on for about 45 minutes...seemed ok. Restarted computer 10 minutes ago and it is just sitting there cycling thru those three screens trying to get to logon. Didn't have the problem when in 9.04.
 
The other thing I notice is my 5 in 1 card reader/USB is not recognized. I'll address that later.
 
Anyone have any ideas on the reboot problem?

---

### Post by johnson094 on 2010-08-29
What did you mean "post your hardware details. From a terminal session type"
 
Thanks

---

### Post by johnson094 on 2010-08-29
**[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2]This is the specs on my system:[/SIZE]**
**[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2]Operating System[/SIZE]**
 **[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2][/SIZE]** 
**[SIZE=2]System Model[/SIZE]**
[SIZE=2]Windows Vista Home Premium (build 6000)
Install Language: English (United States)
System Locale: English (United States)[/SIZE] [SIZE=2]HP Pavilion 061 PJ562AA-ABA a705w 0n41211RE101GIOVA00
System Serial Number: CNC44409NX NA440
Enclosure Type: Desktop[/SIZE]**[SIZE=2]Processor a[/SIZE]** **[SIZE=2]Main Circuit Board b[/SIZE]**[SIZE=2]2.93 gigahertz Intel Celeron
16 kilobyte primary memory cache
256 kilobyte secondary memory cache
Not hyper-threaded[/SIZE] [SIZE=2]Board: MICRO-STAR INTERNATIONAL CO., LTD Gamila/Giovani/Neon series 030
Serial Number: 4911201514
Bus Clock: 133 megahertz
BIOS: Phoenix Technologies, LTD 3.15 08/05/2004[/SIZE]**[SIZE=2]Drives[/SIZE]** **[SIZE=2]Memory Modules c,d[/SIZE]**[SIZE=2]76.26 Gigabytes Usable Hard Drive Capacity
58.40 Gigabytes Hard Drive Free Space

SONY DVD RW DRU-820A ATA Device [CD-ROM drive]
TSSTcorp CDW/DVD TS-H492A ATA Device [CD-ROM drive]

Generic USB CF Reader USB Device [Hard drive] -- drive 4
Generic USB MS Reader USB Device [Hard drive] -- drive 6
Generic USB SD Reader USB Device [Hard drive] -- drive 3
Generic USB SM Reader USB Device [Hard drive] -- drive 5
HP Photosmart D110 USB Device [Hard drive] -- drive 2
WDC WD2500JB-00REA0 [Hard drive] (250.06 GB) -- drive 0, s/n WD-WMANK5909508, rev 20.00K20, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
WDC WD3000JB-00KFA0 [Hard drive] (300.07 GB) -- drive 1, s/n WD-WMAMR1479445, rev 08.05J08, [SMART]("http://www.belarc.com/smart.html") Status: Healthy[/SIZE] [SIZE=2]1016 Megabytes Usable Installed Memory

Slot 'A0' has 512 MB
Slot 'A1' has 512 MB[/SIZE] **[SIZE=2]Local Drive Volumes[/SIZE]** [SIZE=2][SIZE=2]c: (NTFS on drive 0)[/SIZE][SIZE=2]70.51 GB[/SIZE][SIZE=2]57.48 GB free[/SIZE][SIZE=2]d: (FAT32 on drive 0)[/SIZE][SIZE=2]5.75 GB[/SIZE][SIZE=2]918 MB free[/SIZE][/SIZE] **[SIZE=2]Network Drives[/SIZE]** [SIZE=2]*None detected*[/SIZE]
 
Thanks for any suggestions ob 9.10 boot problem.

---

### Post by wjhildreth on 2010-08-29
He is asking you to do the folowing from your Ubuntu machine:

Click Applications from the top right of your screen, then click accessories, then from the menu that it supplies click Termial.  This gives you a screen that is similar to a Windows Dos prompt.

On this screen type the command:

lspci (then press enter)

copy the output of that command and paste it to a reply in the forum, then enter the command:

lsusb (then press enter)

copy the output of that command and paste it to a reply in the forum.

These command (lspci) and (lsusb) will show you what your computer things is plugged into a PCI or USB slot in your computer.  the (ls) portion on the front of the command means (list).

Hope that helps,

Joe

---

### Post by johnson094 on 2010-08-30
Thanks Joe
 
I'll post that later after work.
 
David

---

### Post by johnson094 on 2010-08-30
Now that I understand what lspci and lsusb are here is what you were asking for.

david@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0a.0 PCI bridge: PLX Technology, Inc. PEX 8111 PCI Express-to-PCI Bridge (rev 21)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
david@ubuntu:~$ 
david@ubuntu:~$ 
david@ubuntu:~$ 
david@ubuntu:~$ lsusb
david@ubuntu:~$ lsusb
david@ubuntu:~$ 

Apparently it is not recognizing USB ports.

BTW  I booted Ubuntu 9.10 choosing 1st kernel 2.6.31.22 genuine, then kernel 2.6.28.19 genuine, then retried kernel 2.6.31.22.  Each time it booted up to just before reaching the logon page and went into that cycling action I described in earlier post (purple screen with logo, grey screen, black screen, back to purple screen) and continued for 15 min + until I powered down and rebooted.  Finally I rebooted the default kernel 2.6.31.22 genuine waited about 5 minutes then left for work leaving it in the cycle mode.  When I arrived home, there was my login page and I logged in without a problem.

I there a way to print my CMOS settings so you guys can see what I have?

My hopes are to get this bootup problem solved then take everything out and load Ubuntu 10.4 on an external USB or external hard drive.  I want windows and only windows on C Drive and leave D drive for backup and storage.

Again, thanks for helping the new guys.

David

---

### Post by davidmohammed on 2010-08-31
OK,
  you have two sorts of graphics, ATI and onboard intel 845 graphics.  One idea could be that karmic is getting confused on what driver it needs to load.

My suggestion is to concentrate getting a stable desktop before trying to have two graphics/two displays.  Physically, pull out the ATI card and plug into the onboard graphics.

Reboot.  Does that work?

If it doesnt, then boot with "i915.modeset=0" as your grub option - 

When booting, press Escape (or shift) to display Grub.  Press e to edit.  Find the line with quiet splash.  Just before, add nomodeset

i.e. the line should look like ... i915.modeset=0 quiet splash --
 
Does that work?
If it doesnt then try with the following boot options
i915.modeset=1
nomodeset
i915.modeset=0 xforcevesa
i915.modeset=1 xforcevesa
nomodeset xforcevesa

If you use the 10.04 Live CD - you can try without installing if you use the boot option "i915.modeset=1".  During booting into the live CD press any key to reveal I think 5/6 options.  Press tab (I think) to edit and reveal the boot string.  Add the boot option as described above before quiet splash.

---

### Post by johnson094 on 2010-08-31
I do have the 2 graphics and and in CMOS I deselected ATI and selected onboard, then moved my cable to the onboard connector.  I will try your suggestions and get back to you.  Can I load the 10.4 live disc in the "try it" mode with the 9.10 still on board?
 
Thanks again for your response.  It's off to work right now, will advise in about 9 hrs.
 
David

---

### Post by davidmohammed on 2010-08-31
> **johnson094 said:**
> Can I load the 10.4 live disc in the "try it" mode with the 9.10 still on board?

Yes you can - this is a good way to see if stuff works without affecting the installation of any O/S on the hard-drive.

---

### Post by johnson094 on 2010-08-31
David,
 
I followed your directions as follows:
 
1- Removed ATI graphics IDE card and rebooted. No change...still cycles as per earlier post.
 
2- Rebooted tried to use "esc" did not halt boot as described, then realized that the esc was to bring me to the list of kernel choices in order to edit the grub option for whichever kernel I chose.
I am running Ubuntu 9.10 but I may have failed to advise you that I initially installed 8.10, then withing the program I used upgrade to install 9.04, and then repeated this to upgrade to 9.10. Since I am running dual boot systems (Ubuntu and Vista) when I reboot I automatically come to the kernel page.
 
My default kernel is 26.31-22-generic root
 
With this hightlighted, I then press "e" to edit the grub options and the screen reads:
 
uuid ec19aaf5-d067-4081-8826-483fe3d64050
kernel /boot/vmlinuz-2.6.31-22-generic root-VVID=ec19aaf5-d067-4081-->
initrd /boot/initrd.img-2.6.31-22-generic
quiet
 
This was not what I expected...I did not see "quiet splash"
 
Looking at the lines above I decided to try to imitate them so I typed this on the line that said just "quiet"   "quiet /boot/ nomoset splash quiet"
 
I rebooted and it did the same cycling thing BUT this time it created the same situation you had described in your directions. It bypassed my list of kernels.   I rebooted and pressed "esc" and there was my list of kernels . I selected default, pressed "e" and there was the old grub options with just the word splash.  
 
Thought I'd better get your comments on this before I played any further.
 
Awaiting a reply
 
David

---

### Post by Rasa1111 on 2010-08-31
David, 

 I am rather noobish myself,
been using Ubuntu for 8-9 months or so. 
I can't really help with the issues your having, 
but i must say.. You seem to be doing very good for a noob. :)

Ive run into only minor problems that were short lived,

for example, 
When I first installed ubuntu, it was 9.10~
amd it worked great, and I loved it!
 But, it would sometimes just freeze up and not move, so i had to learn the "magic keys" to safely reboot it. lol

 I never got that worked out, 
but when I installed 10.04, the freezing stopped..
 only now.. it would sometimes "go funky" on me, and start flashing odd screens at me.  lol

 I think that was a small issue with my intel graphics card, 
but after a month or so, it stopped completely, 
and now everything runs perfect. 
(ok, except stellarium). lol

I have installed Ubuntu on many computers since my first install,
and surprisingly, have not had any real issues.

 I also got my dad using ubuntu, a few months back, 
he used windows forever, and it was all he knew, 
but after I showed him Ubuntu, and started talking it up,
he got the itch and wanted to take the plunge. lol

 He made me proud, and did as I did,; 
he said "completely remove windows". lol
So I did, and he has been using only ubuntu (at home)
and he loves it.
No real issues there either. 
He still needs to use windoze on the court computers,
but has even been talking to the 'higher ups'.. about trying to break away from windows there to. . lol

I think once you get this lil issue sorted, you will be more than happy. :)

 But yeah, You seem to be doing quite well so far..
issues and all. :) 
Cheers dude. lol  <3

---

### Post by johnson094 on 2010-08-31
Thanks Rasa1111, appreciate the encouragement. I can say I have been inside Ubuntu 9.10 a few times since I installed and have been pleasantly surprised. I just want to get this boot up thing solved. The boot up will eventually bring me to the login page then it's "in like Flint", but this boot up sometimes takes hours. I just walk away let it churn, come back several hours later and there the login page is. Crazy huh!
 
Believe me..I'm not going to let it beat me. The worst I may have to do is format and reinstall everything. Already done that several times to the point my ketcode entry limit has been exceeded. Next time I format my drives I'm gonna leave Vista on the computer and install Ubuntu onto an external HD or 8gb thumb drive.
 
Thanks again for dropping by

---

### Post by Rasa1111 on 2010-08-31
No problem mate. 
if all users were like you.. 

well...
it would be good. lol  :P

Yeah that has to be kinda irritating. 
and so unlike what I experience with Ubuntu everyday. 
My PC is at least 7 years old, (dell dimension 2350) lol
and my boot up/ shut down times are amazing. 

It takes about 5 seconds, maybe 6, to shut down, from the second i click "shut down".
and when I turn it on, 
I am on my desktop in no more than 10 -15 seconds. 
really amazing. 

 Question~
Since you have a windows machine,
have you tried wubi?
(installing ubuntu inside of windows)? 

 Just inserting the Ubuntu disc into the booted up windows system,
and going from there? 

 anyway, this is surely the place to get the help needed. 
and it's always good to keep an eye on these threads and read as much of them as one can, it may (and probably will) help in the future. 
So i like to follow them. lol

since I can't help much with this boot up thing,
I will do my part and BUMP this thread whenever I feel it needs a bump. lol

it'll get worked out, i know it. :D
 Peace, and thanks. <3

---

### Post by johnson094 on 2010-08-31
I put in the 10.4 Live CD and booted .  Followed instructions for installation tute I found and I have it up and running .  I'm going to leave it up and running in case there are any tests you need me to run from inside.  Gotta hit the sack now...11 pm here and clock chimes at 6 am....I hate work, it interferes with my computing.  But then again it pays for my computing.  I will check forums for replys in am before I'm off to the hospital.
 
Later

---

### Post by Rasa1111 on 2010-08-31
one good thing to do,
just to prevent any unneeded issues.. such as freezing or crawling,
would be to go into System>Preferences>Appearance>Visual Effects> and choose NONE> if not already chosen. 

That will make it run much nicer. 

 Congrats on getting it going! :D

---

### Post by johnson094 on 2010-09-01
Grats alittle premature...I failed to clarify I have the "Try Mode" running. Been reading and I'm going to make some changes using the Live Disk and then try to to clean install of 10.4.  What the heck been there done that, and getting pretty good at it.
 
Later

---

### Post by davidmohammed on 2010-09-01
> **johnson094 said:**
> 
 
My default kernel is 26.31-22-generic root
 
With this hightlighted, I then press "e" to edit the grub options and the screen reads:
 
uuid ec19aaf5-d067-4081-8826-483fe3d64050
kernel /boot/vmlinuz-2.6.31-22-generic root-VVID=ec19aaf5-d067-4081-->
initrd /boot/initrd.img-2.6.31-22-generic
quiet
 
This was not what I expected...I did not see "quiet splash"
 
Looking at the lines above I decided to try to imitate them so I typed this on the line that said just "quiet"   "quiet /boot/ nomoset splash quiet"
 
I rebooted and it did the same cycling thing BUT this time it created the same situation you had described in your directions. It bypassed my list of kernels.   I rebooted and pressed "esc" and there was my list of kernels . I selected default, pressed "e" and there was the old grub options with just the word splash.  
 
Thought I'd better get your comments on this before I played any further.
 
Awaiting a reply
 
David

suggest have a read of [this]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") - it will describe how to edit your grub and where to add the boot parameters.

---

### Post by johnson094 on 2010-09-02
I read through the material and tried those commands, must be still a little confused because couldn't get the terminal to accept the commands as I wrote them. Let me do a little more research and reading and continue to work on this. If you don't mind I'll continue to monitor this thread and post as I learn more.
 
As I stated earlier, I did get the 10.04.1 Live CD to load. In fact it loads great. Been reading a lot about USB flash drives installation so I have been trying to install 10.04.1 to a flash drive. I am opening a new thread about a problem I ran into.
 
Thanks for all your advice and help.

---

### Post by johnson094 on 2010-09-15
Well after a week of reading, reading, reading...I finally have Ubuntu 10.04.1 up and working. ;)
 
 I tried all kinds of suggestions and ended up with a bit of a mess a couple of times...even lost access to my C drive yesterday.  Discovered how to restore Windows MBR and got that back to working.  I then formatted my D drive.  Next I scanned my complete computer with all devices connected for driver updates, downloaded about 3 and installed Ubuntu to the formatted D drive (selected use the entire hard drive).  When finished I crossed my fingers and rebooted .... It booted without a hitch.   Right now I am downloading all the suggested upgrades and hope to continue following the guidelines in the Ubuntu Pocket Guide for setting up my desktop, software and other peripherals.
 
Thanks to all who gave me assistance and encouragement!!! You know who you are.
 
I may be crying again tomorrow, but for right now I'm proud as a Peacock.
 
David   ):P

---

### Post by Rasa1111 on 2010-09-16
well done mate! :D
congrats! <3

---

### Post by johnson094 on 2010-09-16
Thanks guy,
 
24 hours and still going...can't believe it!   Thanks again for the encouragement.
 
David

---

