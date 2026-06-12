---
title: "Unable to Locate RSDP"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2006-06-04
I am trying to install and everything goes ok until its time to start. It doesn't start.

It goes to a screen that has the words:
[4294667.296000] ACPI: Unable to Locate RSDP
with "_" blinking at the bottom.

The hard drive used to be a windows me and it was wiped by a previous tried install of the previous ubuntu which wasn't successful either.

Is the hard drive the problem or is there something I can do to install it?

help please.

Ok I cooled and found stuff that said what to do I think. It said turn acpi=off. then boot. i did it and the os installed but then just as it started the screen went black n my monitor shutdown.

i turned off the pc and it never installed.

what can i do?

could my bios be too old?

I am a windows person so this is new to me.

---

### Post by Kapre on 2006-06-04
[QUOTE=maddbaron]I am trying to install and everything goes ok until its time to start. It doesn't start.

It goes to a screen that has the words:
[4294667.296000] ACPI: Unable to Locate RSDP
with "_" blinking at the bottom.

The hard drive used to be a windows me and it was wiped by a previous tried install of the previous ubuntu which wasn't successful either.

Is the hard drive the problem or is there something I can do to install it?

help please.

I am a windows person so this is new to me.[/QUOTE]

Since there is no data on your drive yet (except for unsuccesfull attemps of ubuntu), I would suggest to re-format the drive a do a scandisk(to check for errors/bad clusters) on it. This maybe is what's causing the problem. Also check the integrity of your CD (as it may also is what's causing this RSDP).

K

---

### Post by maddbaron on 2006-06-04
[QUOTE=Kapre]Since there is no data on your drive yet (except for unsuccesfull attemps of ubuntu), I would suggest to re-format the drive a do a scandisk(to check for errors/bad clusters) on it. This maybe is what's causing the problem. Also check the integrity of your CD (as it may also is what's causing this RSDP).

K[/QUOTE]


i ran a live cd on another pc and it worked but my other pc was slow and didnt run right. but it did boot.

how can i reformat?

---

### Post by maddbaron on 2006-06-05
start pc. insert cd. cd starts. then I click ubuntu screen comes on install or start unbuntu.

I click that and the install starts.

then it says loading linux kernel. and uncompressing kernel....ok.

I see a bunch of stuff about drivers and file systems and it says ok many times.

the x thing says ok then the configure power management says go then the screen goes to black screen with white text saying

uncompressing linux... Ok, booting the kernel.
[4294667.296000] ACPI: Unable to locate RSDP

with flashing text cursor under the text.

what do i type/do now?

I am running pent 3.

---

### Post by phend-one on 2006-06-06
After the menu comes up to Install, run liveCD, check CD integrity etc, hit F6.

A little text prompt will pop up with stuff already in it. Put:
```
irqpoll
```

right after it.

That worked for me, but I still see the ACPI / RSDP error you get during bootups etc. But ubuntu 6.06 runs fine.


**NOTE:** If the irqpoll didn't work, try:
```
noapic nolapic
```
after it.

---

### Post by takayuki on 2006-06-13
I've got the same error at the beginning of the install.  can't install the os...

[4294667.296000] ACPI: Unable to Locate RSDP

then it just hangs.

i'm trying to install dapper on a Compaq Presario 2298.

any solutions?

thanks,

takayuki

---

### Post by jasonyu on 2006-06-15
I have accounted this problem too, I am using a rather old pc, it has a 815 mainboard, and 512 sdRam. I am using a Ubuntu DVD 6.06 LTS.

I have tried many times to install Ubuntu 6.06 on it, and failed. I have installed it   as a server, booted into the X(this works fine.:?: ) and installed from the link on the desktop, installed in a text mode, but none suceeded. At the last moment my display just blanked out, and the harddisk led is long lighted. 

First I think it is the harddisk's problem, but it is good, because I have checked it in XP.  And I found that each time, when ubuntu tries to write the first few parts of the disk, like installing grub, the display blanks out. And I have tried out the parameters in Bios on ACPI and hard disk working mode, but none worked.

At last, I plugged the disk into another pc and completed the installation, which has a mainboard of 848p.  When I plugged the disk back into the old pc, it told me somthing like "cannot locate the RSDP"

and I have searched it by google, but found nothing good. is the hardware not supported? windows 2K and windows 2K3 works fine on the old pc.

---

### Post by jasonyu on 2006-06-19
Hello everyone, I have solved my problem. 

Can not locate RSDP, and "Wait for the root system"; 

When installation the root partitation is hda1, after the installation I put it to hdb1, and grub cound not find the root file system, I changed the parameter temporally "root=" from hda1 to hdb1, and it started successfully. 

The RSDP problem still displayed, but the box booted successfully.:D

---

### Post by Varjagy on 2006-06-30
Hello.

I new to Ubuntu in general. I et this error when I try to install 6.06, and I have no clue what to do. I have tried what I have read here, but it's not doing anything.

It's an old machine.

Any tips?

---

### Post by slikvic2002 on 2006-07-02
Same here I'm also pretty much new to Ubuntu and I'm also having this ACPI problem. My problem is with an old laptop:

Compaq Presario 1230
-32MB RAM
-Cyrix MediaGXm CPU
-233 MHz cpu speed
-3GB HD
-BIOS: PhoenixBios

I try to boot from the Ubuntu installation CD I get the same message as everybody else:

"ACPI: Unable to locate RSDP"

The "Unable to locate RSDP" screen disappears and the screen with the ubuntu logo comes up. The loading stops right when it tries to MOUNT ROOT FILE SYSTEM with the follwing message:

/bin/sh: can't access tty; job control turned off

I tried Kubuntu and Xubuntu and they all give me the same message. I also tried Xandros but it just freezes while it's trying to load the kernels. I tried practically everything. I looked on google, other forums and I have found no solution to this problem. This laptop had formerly Windows 98 installed. So I know the laptop works fine. I also know it's not the Ubuntu disc because I used that to install it on my Desktop. Oh well  I guess I'll just have to reinstall windows 98 or dump this shitty *** laptop.:mad: 

[IMG]http://illustrationsvb.com/ubuntu/1.JPG[/IMG]
[IMG]http://illustrationsvb.com/ubuntu/2.JPG[/IMG]
[IMG]http://illustrationsvb.com/ubuntu/3.JPG[/IMG]

---

### Post by AhrenBa on 2006-07-18
Gosh, I am having this exact same problem. I wish there was an answer. I have tried like 7 different distros and I either get the ACPI error, a buffer error, unable to mount cd, or it just plain freezes. 

I very much want to install Linux on my PC, but it is just not working. :(

---

### Post by monakhov on 2006-08-18
Same thing.
From this post (and a newer one) it seems that RSDP problem appears quite often.
Is it a well-known problem?
Could anyone give some real solution and/or explanation?
(except verifying installation CDs)
Or the only hope is ACPI-HOWTO?

---

### Post by Maxlent on 2006-09-02
Hi,

Iam trying to install Ubuntu on an old Digital laptop and run into the same problem.  Has anyone come across a fix for this issue?

Max

---

### Post by Cornald on 2006-09-03
Hi guys,

I´m quite new to this forum, but not go ubuntu (although I´m far away from what someone would call an expert :rolleyes: ).
Now to topic:

I have the same issue on an old box (PII 233 MHz, Intel 440i with 198 MB RAM).
I just installed 6.06.1 from the alternative CD and see the same message: *ACPI: Unable to locate RSDP*

But, my box starts quite fine. I think the boot-failure is a result of some acpi problem.
Like jasonyu said, grub or ubuntu seems to mix up partitions.
In my case everything ("/boot" and "/") are installed on on partition "/hda1"

Please try to open up grub during boot (usually using "ESC") and edit the line grub uses to start ubuntu.
You will find something similar to this:
```

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot
```

Edit the kernel line to :
```
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash acpi=off apm=on
```

If this does not work try:
```
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash noacpi acpi=off apm=on
```

This should switch ACPI off, which isn´t supported by "old" machines (usually 2000 and before).

If this should work, you can add this permanently by using:
```
vi sudo /boot/grub/menu.lst
```

instead of vi you can of corse also take 
```
gedit sudo /boot/grub/menu.lst
```

Regards

Cornald

---

### Post by bernardfrancois on 2006-09-05
I also had the *Unable to locate RSDP* error. Right after entering my user name and password, I only saw a brown screen and the cursor (it was stuck there).
What I did that solved is was installing ubuntu 5.10 and upgrading to 6.06. Now it seems to work fine.

It happened on an older computer with an intel mmx 400mhz processor. I don't know any other specifications of it.

---

### Post by altonbr on 2006-10-25
**@Cornald**

This works in most cases yes, but I had the same problem on an old Pentium II and this is how I fixed it:


When GRUB started to boot and said there was a 2 second window to hit 'esc', I did. I hit 'e' to edit the top kernel line and saw:
```
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hde1 ro quiet splash
```

I noticed something odd from my experience with Linux and partitioning. It says "/dev/hde1"... well that confused me because I only have one hard drive.. so I changed the line by changing the "hde1" to "hda1" and removed "quiet" for a more verbose output:
```
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro splash
```

Also, if you'd like to edit grub, make sure you enter in
```
 $  sudo cp /boot/grub/menu.lst.backup
 $  sudo vi /boot/grub/menu.lst
```

and then change that line appropriately. Hope this helps somewhat.

---

### Post by czer323 on 2006-12-03
Installing ubuntu on this computer was probably one of the hardest projects I've had to do so far.  First off, I couldn't get it to install 6.06.1 at all. I could get it halfway through the installer, and it'd freeze while trying to install the kernel.  6.10 however, was a different story.  After booting up with some options "noapci irqpoll pci=irqbios" then I could get to a language screen.  From there, I'd normally change to a shell(alt-f2) and modprobe ide-cd, ide-generic, ide-disk, and cs5520 just to be thorough.  Change back to Alt-F1 and continue installing.  

Afterwards though, i actually had an issue with it finding the IDE drives.  The kernel would hang approximately 70% of the time.  Unfortunately, no combination of append commands would change it.  I eventually found someone who had a very similiar situation and upgraded to 2.6.19 kernel to fix their issue.  I changed my apt sources list to use feisty, and then used synaptics to update just the kernel.  

I haven't tested it too much yet, but it seems to be loading every time, so far.

---

### Post by firstc624 on 2007-01-03
I to had this error and i was searching google and came across this post on a forum board

"
However the Windows problem persisted and the fixmbr command only succeeded in disabling the multi partition boot ability. After a long session of multiple image restores (new and old), partition deletions, disk formatting, chkdsk /f, and anything else I could think of, I finally took a look at the BIOS settings. There is a setting under Power Mangement called "ACPI BIOS mode" which was 'disabled'. After setting it to 'enable' (and restoring the latest image), XP booted just fine. Setting it back to 'disable' once again kills XP, but it boots again (without requiring image restoration) when set back to 'enable'. I probably disabled this some time ago for an OS/2 issue and it caused no problem with that OS."

I checked my BIOS and for some reason my ACPI was shut off as well turned it back on and rebooted.  seems to have gone away.  

I recomend checking your bios too.

Hope that helps

First_c

---

### Post by powercow on 2007-02-09
Wow I am going through this now.
I never sucessfuly got ubuntu or xubuntu or kubuntu or even dsl installed. I would get a wide variety o f percentages through the installation. My closest was 92% done. (most of the time the livecd would come up but not always) WHile i got the same message as all of you, my installations rarely stopped there.

I did however find something to work with this ancient laptop
fluxbuntu..
it is the only one i could actually install. and it works surprisingly well for this old laptop.. takes a bit too boot but definately brings new life to this old machine.

and if like me you will probably have to edit the /etc/X11/xorg.conf file so that your resolution is functional and not 640x480
Scool to monitor section i cahnged mine to 36-52 and 36-60 .. then ctrl-alt-backspace to restart fluxbox.

---

### Post by geotrouvetout on 2007-02-10
I resolved this problem going into the bios and unchecked all power management option.

---

### Post by bodyART on 2007-02-12
@firstc624:  Thanks for that tip!  Going into my bios, I found ACPI disabled.  I enabled it and the error vanished.  For reference, my system is rather old.  It's a dual celeron system(333mhz) on an old abit BP6 board, with 512mb memory, some old framebuffer video card, and two 40mb HDDs.  That fix made the ol' clunker useful. :P

-BA

---

### Post by MaXqUE on 2007-02-12
> **phend-one said:**
> 

That worked for me, but I still see the ACPI / RSDP error you get during bootups etc. But ubuntu 6.06 runs fine.
.

I wondered what RSDP was  so I looked it up. RSDP is "Root System Descriptor Pointer". This leads me to guess that the root partition hasn't been marked or at least hasn't been properly marked. When you partitioned the drive, did you mark one partition as root?

I get the say each time I boot, but only for about a second, then it grabs the root file system and the kernel and Ubuntu boots.

Just a guess on my part 

Cheers,
MaXqUE

---

### Post by teddyt on 2007-02-28
I had this exact problem and found that my PCI bus on the motherboard I was using did not support the dual GigE Intel NIC I was using. Once I removed the hardware conflict, everything installed as expected without errors. :)

Travis

---

### Post by scythedxheartx on 2007-04-03
Just to let all of you know, I am a high school student just learning about computer talk and everything...so stuff like ACPI i won't understand

I have an old Windows 95 and I started deleting programs awhile ago, and i rebooted it...and then it wouldn't work without an activation disk. Then yesterday i learned about Lindux from the computer teacher in my school. He said that Lindux would make it reboot again so it'd work under lindux. So i have tryed and it has worked until it starts installing. 

I go to the main page and choose the option "Start or Install Unbuntu"

After that it starts up but then it comes to a page with the "ACPI: Unable to Locate RSDP" thing...

any ideas??

---

### Post by Robynsveil on 2007-04-07
> **bodyART said:**
> @firstc624:  Thanks for that tip!  Going into my bios, I found ACPI disabled.  I enabled it and the error vanished.  For reference, my system is rather old.  It's a dual celeron system(333mhz) on an old abit BP6 board, with 512mb memory, some old framebuffer video card, and two 40mb HDDs.  That fix made the ol' clunker useful. :P

-BA
40 *mB* HDDs? Gee, that *is* old. :lolflag: Are they MFM drives? or RLL? Takes me back to the days of my old slant-front IBM with its 8088 processor, 640K RAM, and 10 megabyte (yes, megabyte!) hard drive. DOS was king.

I'm trying to resurrect a Tyan board sporting a blazingly fast 433mHz Celeron processor, a S3 video card and a 6 gig hard drive that spat the dummy trying to run Window 2000 Pro. Does have 786mb of RAM, so it shouldn't have any issues there. I was able to get Ubuntu server 6.10 to install like a champ, but after it rebooted also got the "*<some-huge-number>*ACPI: Unable to locate RSDP" message, :confused: :confused:  and although I went in and tried to make Grub tell me what it was doing, until I made the change in /boot/grub/menu.lst from this:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash

```

to this:

```
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro splash acpi=off apm=on

```

there was no joy. Now, the error is gone, but an uncertainty remains whether the problem has been fixed... I'll have a go at fiddling with the BIOS settings and let you know how I get on.

BTW, great group of people, you guys!

---

### Post by Robynsveil on 2007-04-07
> **scythedxheartx said:**
> Just to let all of you know, I am a high school student just learning about computer talk and everything...so stuff like ACPI i won't understand

I have an old Windows 95 and I started deleting programs awhile ago, and i rebooted it...and then it wouldn't work without an activation disk. Then yesterday i learned about Lindux from the computer teacher in my school. He said that Lindux would make it reboot again so it'd work under lindux. So i have tryed and it has worked until it starts installing. 

I go to the main page and choose the option "Start or Install Unbuntu"

After that it starts up but then it comes to a page with the "ACPI: Unable to Locate RSDP" thing...

any ideas??

First off, have a read of the above posts. You'll see that that the posters have already been over this ground. Like you, I had no idea what ACPI was, so I googled it and got:

>  ACPI is an open standard describing how computer components work together to manage system hardware. Unlike previous standards, ACPI activities are initiated at the operating system rather than firmware level. This enables more sophisticated and flexible approaches towards power management. For example, on a platform implementing ACPI, the OS can direct a cpu to turn itself off to conserve energy, and quickly return to a working state when needed.

The ACPI specification was released in 1996, the latest version is 2.0c and available at [COLOR="DarkOrchid"][http://www.acpi.info/]("http://www.acpi.info/")[/COLOR]. The latest version includes extensions for platforms with 64 and 36 bit addressing. Sections 2,3,8 and 9 are recommended for the first-time reader.

While ACPI can be used for more than power management, this has been the focus of the Linux/ACPI team to date. Also note that ACPI defines interfaces for both hardware and software, so most power management activities, such as the system sleep states, require ACPI support from the BIOS, motherboard, and operating system kernel.

There's even a link if you want to know more.

To start off with, you might want to get a "For Dummies" book on Linux - I assume that's what you meant by 'Lindux' - and get your head around some of the basics. Or at the very least, have a read of:

[COLOR="DarkOrchid"][http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")[/COLOR]

You might find Linux requires a bit more study than Windows to install and operate. Not overwhelming for a high-school student, but certainly a bit more work than just downloading an .exe and double-clicking it.

As to fixing the ACPI problem: jasonyu, Cornald, altonbr, firstc624, powercow, geotrouvetout, bodyART and MaXqUE all have excellent suggestions. Have a go and share how it went. Be sure to explain in detail what you did, what files you changed and what results you got from your changes. I've found this group quite helpful for solving problems, but they like details. :)

---

### Post by Pagla on 2007-04-08
One doesn't have to be a 15 year old to be new to *Lindux*... er... *Linux*! I am more than triple that age, spent 25 years in IT industry - but probably more a newbie to Linux than anybody else here. :lolflag:

I tried installing the Ubuntu flavor of Linux for the first time last night on my Pentium II 350 MHz faithful but ancient clunker with 196 MB RAM, got the *Unable to Locate RSDP* message, googled with it, arrived here, read every one of them, tried some unsuccessfully and was finally able to resolve (?) my problem with the help of robynsveil's suggestion.

I will try to explain what I did, as a newbie for a newbie with the same problem. I am not trying to preach whatever I did as the appropriate thing to do - these are just the steps I happened to follow and are very open to corrections and suggestions.

**Read all the steps first before you try this at your own risk!**

1.
Boot with the Live CD. Mine was Ubuntu 6.10 Edgy Eft.
2.
Select the *Run/Install* option from the menu.
3.
The ACPI error message *Unable...* will be displayed at this time. The screen will go blank thereafter.
4.
Do nothing. Sit tight for several minutes. I waited for 6-7 minutes before the opening screen was laboriously displayed. Your wait time might depend on your hardware config.
5.
Install it on your HDD (long process) and reboot. The error message should still be displayed. If so, follow the next steps after logging in.
6.
Go to System-->Administration-->Users and Groups
7.
Select the user "root".
8.
Click on "Properties".
9.
Change the existing default password to one of your liking.
10.
Close window.
11.
Now, go to System --> Administration --> Login Window.
12.
Click on the "Security" tab and check "Allow local system administrator login".
13.
Close window, log out of GNOME and on to GDM.
14.
Enter "root" as user and root's password that you chose.

**You are now logged in as root at your own risk - so be careful! This was only needed to edit the *menu.lst* file, which can only be edited by the user root. **

15.
Go to Places --> Computer. Double-click on *File System*.
16.
Proceed towards boot/grub.
17.
Double-click on *menu.lst*.
18.
Look for the line:
```
kernel    /boot/vmlinuz-2.6.17-10-generic root=/dev/hda<x> ro quiet splash
```
19.
Append "<space>acpi=off apm=on" to this line (as suggested by robynsveil)
20.
Save the file. Close the File browser and reboot.

The error message should have disappeared by now.

I have no idea about the origin of the error message or the reason of its disappearance after I followed the above steps - so I'll appreciate if anybody can enlighten me on this matter.

Thanks.

---

### Post by Robynsveil on 2007-04-08
> **Pagla said:**
> 19.
Append "<space>acpi=off apm=on" to this line (as suggested by robynsveil)
20.
Save the file. Close the File browser and reboot.

...

I have no idea about the origin of the error message or the reason of its disappearance after I followed the above steps - so I'll appreciate if anybody can enlighten me on this matter.
...
Thanks for giving me the credit for finding the answer to that one, but it actually belongs to Cornald: he made that suggestion on page two of this thread. BTW, once you've got the password set for root, you'll be able to access root (administrator) functions in the terminal, sorta like:

```
Robyn@Flight$ sudo gedit /boot/grub/menu.lst
password: ********

```

as opposed to leaving your GUI to perform admin tasks. Of course, some stuff you have to actually _*log in*_ as root, and can't do with 'sudo'. I've found that putting a link to Terminal in the taskbar has been handy - at this point there's not a session that I don't invoke Terminal at some point.

Since ACPI is a power-management standard that functions at the OS level, and - as Cornald said - the ACPI issue appears to affect only older machines, adding those parameters to that line in the grub menu.lst appears to tell the OS not to try to do any power-management stuff on that system.

---

### Post by undyboy91 on 2007-04-11
> **geotrouvetout said:**
> I resolved this problem going into the bios and unchecked all power management option.

THIS WORKED FOR ME! THANK YOU SO MUCH! :) :D

---

### Post by gba3 on 2007-05-04
well, at the moment I don't know if my error is the same...
i have
[            0.000000] ACPI: Unable to Locate RSDP

instead of
[4294667.296000] ACPI: Unable to Locate RSDP

and i had this message while trying to install Feisty on Celeron 400MHz (i440 chipset on HOT-661 motherboard by Shuttle)  296MB of Ram 20GB HDD...

i've read some commands to type in if F6 is hit in the installation CD menu... and then I got textual information of everything's going on. And here is the information:

[  62.756884] VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
[  62.756972] Please append a correct "root=" boot option
[  62.757042] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)
[  62.757130] <4>atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.
[  63.757075] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.
[  64.253658] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.

and the last message repeated all the time i guess for 5 or something minutes... only the numbers in [] were changing.

At the moment i've found bios upgrade for the motherboard and am installing Ubuntu 5.10 in hope to upgrade bios and do the above mentioned  line edit in kernel.

If somebody knows the faster or better solution, please, post it! Otherwise i hope this all will help somebody...

---

### Post by tk03759 on 2007-05-13
I'm trying to install Fiesty and I've tried just about everything here and I'm still having trouble.

At first, I get the "[ 0.000000] ACPI: Unable to Locate RSDP" error. I tried turning off Power Management in the bios with no luck, and there is no acpi option in the bios. I tried appending acpi=off and apm=on to the end, but instead of getting the "ACPI: Unable to..." error, the blinking "_" appeared without the error and the installation hung there. I've tried letting the error sit on the computer for long periods of time, but nothing happens and it just hangs.

If it helps any, I just tried again after removing "quiet" and "splash" from the end of the F6 Boot Options Command on the Ubuntu Boot Disk and these are the last few lines:

originally:

[393.596231] NET: Registered protocol family 16
[393.596231] EISA bus registered
[393.600566] PCI: PCI BIOS revision 2.10 entry at 0xfdba1, last bus=0
[393.600664] PCI: Using configuration type 1
[393.600745] Setting up standard PCI resources
\\\\\(blinking "_") appears and installation hangs\\\\\

and with acpi=off and apm=on appended:

[79.041593] NET: Registered protocol family 16
[79.042788] EISA bus registered
[79.045937] PCI: PCI BIOS revision 2.10 entry at 0xfdba1, last bus=0
[79.046034] PCI: Using configuration type 1
[79.046157] Setting up standard PCI resources
\\\\\(blinking "_") appears and installation hangs\\\\\


I don't know if any of that helps... any instructions would be greatly appreciated (especially working ones ^__^) .

------

Correction: with quiet and splash removed and acpi=off and apm=on appended, after about 15 minutes, the entire screen goes blank.

------

Edit:    I used a different CD Drive to perform the installation, and it got by. The system has been working fine. I'm reeeally confused on this one, but hey, it worked, so I'm happy.

---

### Post by Warpspeed on 2007-07-17
Anyone made any further progress with this ?

I am having these exact same problems on a Pentium three, 455mhz trying to load 7.04 Fiesty.  Changing the power settings in Bios seems to effect things slightly, but it still always hangs up.

I have four selectable choices choices in my Bios:

1/ ACPI
It comes up with an error message "0.000 ACPI: Bios age (1977) fails cutoff (2000), acpi=force is required to enable ACPI 

2/ APM
Error message is "unable to load RSDP" 

3/ Disabled
Error message is "unable to load RSDP" then after a very long wait, it says "Loading please wait" the screen goes blank for a long time then, Busy Box V1.1.3 (Debian 1:1.1.3.3 ubuntu 3) Built in shell (ash) Enter 'help' for a list of built in commands.  /bin/sh: can't access tty; job control turned off (initramfs)

4/ APM/ACPI
Same bios age fail error message as in first choice.

So what is this acpi=force, and how can I accomplish that ?

---

### Post by NautTboy on 2007-07-28
So is there a real solution to solve this problem "Unable to Locate RSDP"? I've read try this and that.  Like turn of the power management in the bios, it doesn't work.

Both Ubuntu and Server get this message.
Ubuntu hangs after getting message desktop/theme/background might not work properly.

U.Server same message, but installed. Try to apt-get desktop, didn't work. 

If someone got a solution, it would be great to share it as sticky.  Instead of reading thru 3-4 pages with nothing but people with same problem.  No solution.

I'm running on an old Emachine 400Mhz 128Mb 6Gb.

---

### Post by tjmoes on 2007-07-29
same old problem and read all the post and see no solutions that worked and more ideas would be helpful:mad::mad:

---

### Post by n8fau on 2007-09-08
Hello all:

I've read the posts regarding this issue....  No luck!!!

Hardware:
P200MMX /w 20GB HD
198Mb RAM

I get the RSDP error message...
Then it looks like it's doing the install,  it starts Linux but I have no keyboard or mouse.
It stops on the desktop....

If I reboot with a W98 boot disk the hard drive is still a windows drive (no Linux partitions). 

The drive is empty.... 1 dos partition....

Thanks again for any help on this matter.

---

### Post by xsystemx on 2007-09-11
Hi everyone

I was able to solve this issue by doing the following...

Insert installation CD, press F6 and add the following text at the beginning of the phrase/command...

acpi=off atapi=on "leave the rest of the text there and press enter"

---

### Post by xuejm1225 on 2007-10-02
I also have a very OLD machine Pentium II-MMX 233Mhz.

I sucessfully have Ubuntu server 7.04 installed and it did run several time with this error appeared. But this morning it got stuck there.:-(

Following suggestions in this thread, I appended acpi=off to booting parameters, but it seemed only the error message is suspended. The starting process got stucked.

Don'e really know the reason. Looking forward to any help!

CHeers,

---

### Post by idontlikealltheksinkde on 2007-10-24
I did have that problem. But, then, I found out in the 7.04 Live CD help menu to change my disk type to IDE. I did. I no longer had the ACPI error but when I started, theres a Kernel panic with something like VFS error not syncing (not sure on that...) After that, my keyboard blinks and  a ackbd.c Supuious some program might be trying to acsess the hardware directly" error. HELP!!! 

P.S: I tried noapic nolapic and acpi=off together and it said loading please wait... the GUI apears for boot up, then it hangs.](*,):(:confused:

---

### Post by janipewter on 2007-12-10
My server has an IDE and a SCSI hard disk in it. I got the RSDP error when I booted from the CD but I didn't touch anything and a few seconds later it let me install.

---

