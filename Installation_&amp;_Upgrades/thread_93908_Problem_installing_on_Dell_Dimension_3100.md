---
title: "Problem installing on Dell Dimension 3100"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by dhpeterson on 2005-11-23
Hi.

Several users, myself included, have experienced that breezy and Hoary do not install on the Dell Dimension 3100.

The problem appears to be the with USB UHCI on this machine. However, Knoppix 2.6 correctly recognizes the chipset and boots successfully.

We have started to discuss this issue on another thread, see: [http://ubuntuforums.org/showthread.php?t=88358](http://ubuntuforums.org/showthread.php?t=88358)

I would like to know what Knoppix is doing in its USB kernel that breezy and hoary are not, as this seems to be the root of the problem.

I have two machines here and am happy to work on the development and testing of a solution. For a start, should I file a bug report? On which package?

--Dave

---

### Post by gix on 2005-11-23
I've got the same problem!
I've tried with the "noacpi acpi=off" parameters on boot but they don't work...
the system halt after the line:
Starting system log daemon: syslogd, klogd.

---

### Post by navneetbhojane on 2005-11-23
Hello,
      I have a system with intel915glvg motherboard & P4(2.66) processor/80 gb sata hdd. I have installed ubuntu linux 5.10 on this machine. Does ubuntu 5.10 supports my machine? because, while rebooting ,it is halt at "setting up network, start hotplug subsystem".     
    Please, Provide  me a solution..................

---

### Post by wakingeden on 2005-12-17
Ok im having the same problem with my Dell Dimension 3100/E310 and it looks as if the answer is not to be found here so if someone could please point me in the right direction it would be much appericated.

---

### Post by Darkhack on 2005-12-17
try some of these boot parameters.... (if all else fails try using them all at once)

linux noapic pci=routeirq pci=noacpi acpi=off irqpoll

---

### Post by LucidParody on 2006-01-07
any other ideas? i would really like to get ubuntu back.  i hate having to use windows....

---

### Post by gix on 2006-01-07
[QUOTE=LucidParody]any other ideas? i would really like to get ubuntu back.  i hate having to use windows....[/QUOTE]

I've successfully installed an OpenSUSE 10 with this hw ... 
doh

---

### Post by LucidParody on 2006-01-07
i guess if that's my only recourse.  i would much rather have ubuntu. :(

---

### Post by LucidParody on 2006-01-12
Hi.  So I can't stand suse.  I tried to use knoppix, but I get a "cannot unite real only media and initial ram disk" error when it tries to boot up the life CD.

maybe this is related to the ubuntu problem?

---

### Post by st3w13 on 2006-01-14
I also have the exact the same problem trying to install on my Dimension 3100. Has anyone found a solution? Thanks!

---

### Post by LucidParody on 2006-01-18
i haven't figured anything out.  i was able to install suse 10 but i couldn't get the resolution right ( 1680x1050 ), so it was practically useless.  even knoppix wouldn't boot! i'm gonna try DSL next.

---

### Post by whelanp on 2006-01-30
Anyone ever manage to get this working. I am getting the same issue on a dell 3100 here too.

Any work arounds I plugged out the keyboard and mouse and got further along the install but I can't get the keyboard to work when i plug in back in.

Paul

---

### Post by MaggotPie on 2006-01-30
Yea I can't install Ubuntu on my Dell E310, it stops installation right in the beggining after an scsi message....I have no idea what to do....:cry:

---

### Post by Gregoyle on 2006-02-04
I'm having the same problem on my Dimension e310.

The general consensus I've found in my research is that the ubuntu installer has a problem with the onboard USB controller.

This guy posted how he did it:

[http://www.stillhq.com/diary/toys/dell/e310/](http://www.stillhq.com/diary/toys/dell/e310/)

But it involves installing with netboot and disabling the onboard USB then installing a PCI USB controller.  That isn't really an acceptable option for me :-).

---

### Post by deadgoon on 2006-02-04
I don't have a solution to your problem, but I do have a link.

[http://linux.dell.com](http://linux.dell.com)

There are community driven forums there and some other information.  There's no official support from Dell, but considering their Windows based support, I doubt you're missing anything.  Maybe you can get some help there.

---

### Post by lila on 2006-02-05
Hello,
 my boyfriend is trying to install Ubuntu as we speak, on a Dell Dimension XPS T600.  He's not even getting to USB problems, it just fails to boot from CD (yes, we have changed the boot menu).  It thinks about it longer than usual while the DELL screen is up, before opening on Win98 like it did before.  You can then open the CD, but obviously, the files can't be read.  We even tried to do fdisk to wipe the lot, but it won't.  We just can't get rid of the DELL thing, and it won't get rid of Windows (actually, it just has he tells me - but it still won't boot on the CD).  
Any suggestions?
Is this Dell version known to be very Ubuntu-incompatible?
Help!:cry: 
Lila

---

### Post by obaudys on 2006-02-10
The Dimension 3100 is not Ubuntu-incompatible per se, its just that linux kernel 2.6.12 does not support the USB chipset, and the machine has no PS2 ports.  I have manage to install ubuntu on it by building my own kernel on the aforementioned machine, here is the wiki article describing how i did it: 
[https://wiki.ubuntu.com/InstallingBreezyOnaDellDimension3100](https://wiki.ubuntu.com/InstallingBreezyOnaDellDimension3100).

Hope this helps.  Interestingly, Knoppix 4.0.2  uses kernel 2.6.12 as well but seems to play nice with the USB controller. Unfortunately Knoppix does not detect the Dell USB Keyboard, so a different USB keyboard is mandatory, I am afraid

---

### Post by LucidParody on 2006-02-11
[QUOTE=Gregoyle]I'm having the same problem on my Dimension e310.

The general consensus I've found in my research is that the ubuntu installer has a problem with the onboard USB controller.

This guy posted how he did it:

[http://www.stillhq.com/diary/toys/dell/e310/](http://www.stillhq.com/diary/toys/dell/e310/)

But it involves installing with netboot and disabling the onboard USB then installing a PCI USB controller.  That isn't really an acceptable option for me :-).[/QUOTE]

Yeah, I don't even know *how* to do a net install. :(

Anyone know if this problem will be fixed in the next release of ubuntu?

---

### Post by warrataw on 2006-02-18
[QUOTE=LucidParody]Yeah, I don't even know *how* to do a net install. :(

Anyone know if this problem will be fixed in the next release of ubuntu?[/QUOTE]

Well, I just installed Dapper Flight 3 on my Dell Dimension 3100 without a hitch, so I suppose the answer must be a big YES! I assume the upgraded kernel has fixed things (says he who knows nothing about kernel development).

So, all of you who, like me, felt rather depressed after reading this thread - take heart! You can have Ubuntu on your Dimension 3100, and it's a beautiful thing indeed. :D

---

### Post by bbqbaker on 2006-02-18
hi, i also have problems installing ubuntu on my dell 3100 that i recently purchased through slickedals!

i am encountering this problem. how do i fix it? is there an updated version of ubuntu that i need to download?
thx!!!!!!!!

---

### Post by bbqbaker on 2006-02-18
thanks for the link. i think i may have to wait till the next ubuntu release because i will definitly mess things up.

[QUOTE=obaudys]The Dimension 3100 is not Ubuntu-incompatible per se, its just that linux kernel 2.6.12 does not support the USB chipset, and the machine has no PS2 ports.  I have manage to install ubuntu on it by building my own kernel on the aforementioned machine, here is the wiki article describing how i did it: 
[https://wiki.ubuntu.com/InstallingBreezyOnaDellDimension3100](https://wiki.ubuntu.com/InstallingBreezyOnaDellDimension3100).

Hope this helps.  Interestingly, Knoppix 4.0.2  uses kernel 2.6.12 as well but seems to play nice with the USB controller. Unfortunately Knoppix does not detect the Dell USB Keyboard, so a different USB keyboard is mandatory, I am afraid[/QUOTE]

---

### Post by warrataw on 2006-02-18
[QUOTE=bbqbaker]hi, i also have problems installing ubuntu on my dell 3100 that i recently purchased through slickedals!

i am encountering this problem. how do i fix it? is there an updated version of ubuntu that i need to download?
thx!!!!!!!![/QUOTE]

You can download Dapper from [http://cdimage.ubuntu.com/releases/dapper/flight-4/]("http://cdimage.ubuntu.com/releases/dapper/flight-4/"). Flight 4 must have just been released coz I don't think it was there last night! Anyway, Flight 3 worked perfectly for me, so I assume Flight 4 would also. I know it's still in development, but I haven't encountered any major problems so far, and if you can't wait until the official release in April then you might want to give it a go.

---

### Post by global_dev on 2006-02-19
i had the same issue on a hp slimline s7310n. (very small machine1 /3 size of midtower = proprietary hardware) and a sony ra820g ( sony hw = proprietary ). There is no support from either on hardware, i mean not even manuals...

regardless of the warnings not to use ubuntu dapper as a normal desktop, i was getting tired of searching for ways to get breezy to work. I was using dapper live to just get to the web to search how to install breezy. by the way gentoo universal 2005.1 had no problems detecting everything and compiling everything. want to learn about a linux variant very quickly, install gentoo 2x and you'll have touched almost every basic command in linux  (time-consuming) 

i then proceeded to successfully install the dapper release from jan 15 (no longer uses hotplug susbsytem from what i understand) and the updates though "killed" x-system. I read about some new releases that fixed the problem. you need to ***search for today's current release, i used 2-17***. They are on a different page then the official dapper release (jan 15) I can't say its stable, but i am having a much better time using this than sitting there trying to just get breezy to boot. 

just advice from a person just trying to get things to work...  i don't mind tinkering, but not right now.

[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

---

### Post by bbqbaker on 2006-02-19
awesome thanks. its now installed and now i am just installing all the packages.


[QUOTE=warrataw]You can download Dapper from [http://cdimage.ubuntu.com/releases/dapper/flight-4/]("http://cdimage.ubuntu.com/releases/dapper/flight-4/"). Flight 4 must have just been released coz I don't think it was there last night! Anyway, Flight 3 worked perfectly for me, so I assume Flight 4 would also. I know it's still in development, but I haven't encountered any major problems so far, and if you can't wait until the official release in April then you might want to give it a go.[/QUOTE]

---

### Post by LucidParody on 2006-02-20
yeah, i tried the live version of flight 4.  it works like a charm, though it doesnt recognize my 2005FPW monitor with 1680x1050 resolution.  i wish it would. :(

---

### Post by bbqbaker on 2006-02-21
since i will be doing alot of development work, i am sort of afraid of using flight4. do you guys/girls think that the next update to breezy will have the fix?

i think somehow all they would have to do is bypass those checks for dell's type of hardware.


[QUOTE=LucidParody]yeah, i tried the live version of flight 4.  it works like a charm, though it doesnt recognize my 2005FPW monitor with 1680x1050 resolution.  i wish it would. :([/QUOTE]

---

### Post by oraknabo on 2006-03-16
I recently bought 4 3100s and have spent 2 days trying to set them up. I did everything in the HOWTO obaudys posted from the Wiki. I had a few problems here and there, but I made it through everything and got the kernel upgraded to  2.6.15 but now I can't get GRUB to work. I know everything in Breezy is installed and ready to go but when I try to do 

update-grub gives me "Searching for GRUB installation directory ... found: /boot/grub ." and nothing else. grub-install /dev/sda says "/dev/sda: Not found or not a block device."

I've tried everything to get around this and nothing is working. I guees I'm going to cut my losses and attempt to install Dapper flight 5.

If anyone can help and keep me from having to start over with Dapper, I'd highly appreciate it.

---

### Post by obaudys on 2006-03-16
[QUOTE=oraknabo]I recently bought 4 3100s and have spent 2 days trying to set them up. I did everything in the HOWTO obaudys posted from the Wiki. I had a few problems here and there, but I made it through everything and got the kernel upgraded to  2.6.15 but now I can't get GRUB to work. I know everything in Breezy is installed and ready to go but when I try to do 

update-grub gives me "Searching for GRUB installation directory ... found: /boot/grub ." and nothing else. grub-install /dev/sda says "/dev/sda: Not found or not a block device."

I've tried everything to get around this and nothing is working. I guees I'm going to cut my losses and attempt to install Dapper flight 5.

If anyone can help and keep me from having to start over with Dapper, I'd highly appreciate it.[/QUOTE]
Hi oraknabo,

I think i know what the issue is.  I have come across this but my memory on the topic is shakey so this is only a suggestion:

 Running update-grub requires some devices in the /dev directory that normally are created by the "udev" daemon after we successfully boot. You will have to create them by hand in this case.  You can find where update-grub is failing by running "strace update-grub", and see which files it tries to access.  

You can then create device files with "mknod <filename> <type> <major-num> <minor num>"  When you know the filename (from the strace output above), use google to see what the type and the major and minor numbers should be.

I cant for the life of me remember exactly what i did when i encountered this, but "strace" is a handy tool and should help you out.  Also, if grub-install still cant find /dev/sda,  use "cat /proc/partitions" in a new knoppix terminal (ie not chrooted to your new partition) to see what your hard drive is at... it might be you have an IDE drive installed, perhaps?

---

### Post by oraknabo on 2006-03-23
I never got to try this but I really appreciate your reply. I had to switch to a different project and let my partner take over. Since she's less technical than I am, I just had her go with Dapper, which has been working just fine. 

The HD is the standard one in the 3100 and mounted just fine in Knoppix on sda, so I don't know what the deal is. I also wanted to mention that I had absolutely no problem with the Dell keyboard throughout the entire process.

---

