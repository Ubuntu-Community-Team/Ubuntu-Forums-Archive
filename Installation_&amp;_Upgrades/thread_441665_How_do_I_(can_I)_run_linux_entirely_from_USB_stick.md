---
title: "How do I (can I?) run linux entirely from USB stick?"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by trapix22 on 2007-05-12
I am looking to run linux (probably xubuntu) from my laptop with no hard drive at all. I want it to do EVERYTHING... Boot from it, install new software to it, save my files to it, etc... so when I'm gone, my entire system goes with me. My questions are...

1) Booting:
       a) My BIOS (Phoenix Award) doesn't support boot from USB. Can I change/upgrade BIOS?

       b) If "no"... Could I get a basic linux OS on floppy and boot to it in text mode, then from                    
          text mode load (i.e. xubuntu) from USB?

2) Security:
       -I'd like to encrypt (i.e. dm-crypt) the entire USB so if I lose it (or gets stolen), no one
        can get to my data

I know this is quite a project but I've spent hours searching and found pieces of what I want to do but can't quite put it all together.

I've had my clients' VERY private info stolen and misused and I am determined to NEVER let that happen again. I think this might be the way to go. I'm open to any suggestions. Thank you for the help.

---

### Post by Martje_001 on 2007-05-13
Yes, you can update your BIOS, check your motherboard manual.
If you want to encrypt it: use Debian + LVM encryption. I don't know if it is possible with Ubuntu.

---

### Post by trapix22 on 2007-05-13
Thank you for the reply.
My motherboard came with only install CD, I installed it a couple of years ago under (gag) Windows and I can't find anything on that CD.

How do I find out (Ubuntu Edgy) what type of motherboard I have?

---

### Post by Martje_001 on 2007-05-13
Maby in the device database somewere in 'system'...

---

### Post by rillip on 2007-05-13
I poked around on this, and couldn't find it in my system info section.  It may be burried somewhere, but I don't know where.  I could never find this information in Windows either, so you may need a third party utility for this.  Not sure what that would be on Linux; on Windows, Everest Home Edition is a free software that lets you find this information out.  It's a pay for utility now, but if you search for pervious versions, it was free.  

As for updating the bios, you typically download the update and  flash utility that you put on some removable media that you can boot from.  I can't say whether or not your bios will support boot from usb after update, if there's even an update available.    It just depends on the manufacturer.

If you know the model of laptop, you can probably Google the bios update or motherboard typel I've never heard of one model of laptop using more than one type of motherboard, since they're rather specific to the abilities of the case.

I don't know enough about encryption to help with that, but I hope you are prepared for a very, very long boot if it is possible.  If you are encrypting the entire stick, it would have to decrypt the section the OS is on to run it.  And I'm not sure how you'd accomplish that; you'd have to have some sortr of bootable decryption program, decrypt the / partition, launch the OS, decypt any files you want...

I'm not saying what you propose isn't possible, but it doesn't seem like neccisarily the best solution.  I would probably just write a /home parittion to a USB stick, encrypt it, then use a live CD and mount your home partition from the USB stick.

---

### Post by trapix22 on 2007-05-14
Thank you for input.. everyone... Thanks rillip, your proposal in last paragraph sure sounds less complicated. I guess, I tought the more complicated the better...

Let me cut to the chase...What I'm paranoid about... Data stollen and misused (I got sued, cost a ton, blah, blah) was on a Windows system. I researched Win security and found that Win litters the entire hard drive with temp files, backup files, registry backup, etc... and I suspect THAT is how my data was back-doored.

My worry about putting /home dir on USB and encrypting it is that I don't know how and where ELSE linux litters the hard drive or if in fact it does. If I know that no traces of data/passwrds/history etc... will EVER end up on hard drive... then your way sounds like the way to go. I'll wait for your reply before I go asking more advie :). Thanks

---

### Post by rillip on 2007-05-14
> **trapix22 said:**
> Thank you for input.. everyone... Thanks rillip, your proposal in last paragraph sure sounds less complicated. I guess, I tought the more complicated the better...

Let me cut to the chase...What I'm paranoid about... Data stollen and misused (I got sued, cost a ton, blah, blah) was on a Windows system. I researched Win security and found that Win litters the entire hard drive with temp files, backup files, registry backup, etc... and I suspect THAT is how my data was back-doored.

My worry about putting /home dir on USB and encrypting it is that I don't know how and where ELSE linux litters the hard drive or if in fact it does. If I know that no traces of data/passwrds/history etc... will EVER end up on hard drive... then your way sounds like the way to go. I'll wait for your reply before I go asking more advie :). Thanks

If you're running from the Live CD, it can't write temporary files of any sort anywhere.  Anything that is written would be on the USB stick.

However, it will load these things into main memory. This is wipped every time you reboot (and more often then that), but it does cause a performance hit, in that it has to keep everything it does in memory, making it slower. You also have to read from the CD instead of the HDD, which is also slower.  So I wouldn't do this for really intensive usage, but if you just want to be able to take your data anywhere and have it be safe, this seems like a good way to go.

---

### Post by 454redhawk on 2007-05-14
once you get the BIOS worked out.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


> **trapix22 said:**
> I am looking to run linux (probably xubuntu) from my laptop with no hard drive at all. I want it to do EVERYTHING... Boot from it, install new software to it, save my files to it, etc... so when I'm gone, my entire system goes with me. My questions are...

1) Booting:
       a) My BIOS (Phoenix Award) doesn't support boot from USB. Can I change/upgrade BIOS?

       b) If "no"... Could I get a basic linux OS on floppy and boot to it in text mode, then from                    
          text mode load (i.e. xubuntu) from USB?

2) Security:
       -I'd like to encrypt (i.e. dm-crypt) the entire USB so if I lose it (or gets stolen), no one
        can get to my data

I know this is quite a project but I've spent hours searching and found pieces of what I want to do but can't quite put it all together.

I've had my clients' VERY private info stolen and misused and I am determined to NEVER let that happen again. I think this might be the way to go. I'm open to any suggestions. Thank you for the help.

---

### Post by trapix22 on 2007-05-15
OK... rellip... here I go... btw, thank you so much for the help. I slmost understand it all :). Here's my plan with some questions.

1) Clean install Ubuntu on new hard drive
2) Move the /home directory to USB (and encrypt).(That way my data goes with me with nothing on harddrive other then system files)

Questions:
a. How do I move /home to USB so system knows that from now on /home is on USB and not on harddrive?
b. What happens on boot? If USB is not in... Linux asks for /home dir or it just boots without it? in which case...
c. How do I tell it where /home is (command)?
d. Is there /home on harddrive still but nothing is stored there or there just isn't one?

Please stay with me here, I almost got it. This can be your good deed for a month :)

---

### Post by rillip on 2007-05-19
> **trapix22 said:**
> OK... rellip... here I go... btw, thank you so much for the help. I slmost understand it all :). Here's my plan with some questions.

1) Clean install Ubuntu on new hard drive
2) Move the /home directory to USB (and encrypt).(That way my data goes with me with nothing on harddrive other then system files)

Questions:
a. How do I move /home to USB so system knows that from now on /home is on USB and not on harddrive?
b. What happens on boot? If USB is not in... Linux asks for /home dir or it just boots without it? in which case...
c. How do I tell it where /home is (command)?
d. Is there /home on harddrive still but nothing is stored there or there just isn't one?

Please stay with me here, I almost got it. This can be your good deed for a month :)

A. I'm not really sure.  It's probably a mount command... haven't actually remounted my home directory before
B. ... I'm not really sure.  I've never booted without my home directory before.  But the live install doesn't have your home directory, so I tend to think it'll just use the default one and have no issues.
C.  See A.
D.  See B.  Specifcally, on the liveCD there's a home directory with the default settings for things like menus, background, etc. but since it can't write to the CD, there's no point in really worying about its contents.

---

### Post by bluknight on 2007-05-19
Hi, This is my first post to share how I installed 6.10 entirely onto an ext USB HD with great success - and packages fully updated by synaptic. (I can also update to Feisty 7.04 but that broke my install). Here's how:

1. Boot up the LiveCD and check that you have internet connected wired or otherwise
2. Click installer and select manual partitioning of usb devices detected.
3. Make sure you have the empty partition ready (if not you have to use qparted, format and reboot all over - without rebooting the installer will fail to mount it when copying files - bug??)
4. Identify carefully what the target partition is named - for me it is /dev/sdb2 - you'll have to make sure of this when partitioning or getting info from qparted.
5. Proceed with "next" to obtain a summary list of /dev and point points. Heres where you define your /home partition (choose do not format) and the root mount point at the target partition. Also make sure you have a swap partition selected, if no go back and qpart
6. Select advanced to locate your grub bootloader medium. I put it in a fresh floppy (fd0) to save my WinXP:( in case the install fails. Then proceed to copy files.
7. (Here's the tricky part - grub often chose the wrong (hdx,y)) - when install completes while still in LiveCD mount the floppy to examine the /boot/grub/menu.lst file as well as the installed partition /boot/grub/menu.lst - make sure that the kernel line selects the correct root as (hd0,something) where "something" is the target partition - for my /dev/sdb2 it is (hd0,1) - you have to figure this out for your system as it may be qparted differently from me. I had to edit menu.lst from (hd2,1) to (hd0,1) for my setup to boot correctly. Good luck

(PS: Above doesnt work for Feisty because of the device change from /hdx to all /sdx labels - current distro version doesnt install properly for me :confused: )

EDIT: I solved this by using the Edgy kernel in Feisty
[http://ubuntuforums.org/showthread.php?t=450246](http://ubuntuforums.org/showthread.php?t=450246)

---

### Post by gsl on 2007-05-21
I have been successful in making the upgrade to 7.04.

Because the upgrade process rewrote /boot/grub/menu.lst, I edited the (hd3) back to (hd0) at the grub display -- that's how it gets rearranged on my box. I then made the corrections permanent by editing the file, after booting up. Incidentally, I wrote my grub MBR to hd3 , and not hd0.

In my case, I set my home partition to be on my sata hard drive. 

Does anyone have any ideas about which (if any) files get rewritten frequently on the (main) root partition?

There is an improvement in responsiveness; and I guess this is mostly because of the much reduced seek time on my 4gb stick. Booting up is still just over 60 seconds, and I guess this is a saving of about 15 seconds.

gsl

---

### Post by gsl on 2007-05-21
To start answering my own question, /tmp and /var seem to be the candidates for mounting to a hard drive. But are there any other files which get written and rewritten frequently?

gsl

---

### Post by kevpatts on 2007-05-22
surely [www.pendrivelinux.com](www.pendrivelinux.com) is the place to look, no? installation is a 15 minute job.

---

### Post by trapix22 on 2007-05-23
Thank you sooooooooo much for the help, everyone... 

ONLY THING MISSING NOW IS...

1) I want to have /home encrypted on the USB so if I lose (get stolen) the USB no one can get to my data. I found info on just plain encrypting it on its' own as a "backup" system but not if it's /home dir, tied to the boot process. Or is that all there is to it... Encrypt separately, boot PC with no /home mounted then de-crypt USB - /home and mount it to PC - /home

2) This is all on laptop (testing there so I don't screw up my PC yet .. and /home is mounted thru a USB 1.1 port so its' slow and if I encrypt, it will crawl (I think). I have PCMCIA card with USB 2.0 on it and now it only mounts the USB with /home if it's plugged directly into the 1.1 port. Is it possible to include recognizing the PCMCIA card earlier in the boot process, so when it comes to mounting /home, it will mount thru the 2.0 port on the PCMCIA card and may be even ask for de-crypt /home password? (getting fancy now :)

Thank you... Linux community ROCKS!

---

### Post by gsl on 2007-05-23
Thinking out of the box, here, I guess only some stuff is supersensitive for you. So maybe you could have this stuff in one folder, or even just one file. 

Encrypting and de-encrypting this stuff, could be sort of achieved by archiving it and renaming the filename suffix. E.g .tar could be changed to .jpg, or whatever. So to re-access it, you would change back the suffix and de-archive it. This method would be very hard to suss out, if anyone came across your stick.

There maybe more refinements to this off-the cuff method, so lets see what folks say.
-------------------------------------------------------

As regards to my issues, thanks to kevpatts. The thing is that my objectives perhaps differ in that I am using my 3gb as replacement hardrive in what is otherwise a conventional installation. Flash memory is not so very durable when it comes to lots of rewrites, so /home, /var  /tmp and the swap partition seem to me to be the candidates for mounting on the harddrive.

The advantage for me is faster bootup and faster application start up times. Pendrivelinux seems to be more about the more traditional uses of flash, and I guess I can do as I say, for the moment, and then look for the log files that contain rewrite info and tune up, according to that.

gsl

---

### Post by gsl on 2007-05-24
An enhancement I can think of is to write a script which, upon being started:

1)Unpacks and properly renames the required folder (If appropriate, a password can be required)

2) Leaves the shell open, waiting for the combined pack-again and exit command.

This script would sit in /usr/bin and it should be quite practical to mangle everything up so that a user who isn't in the know cannot crack it. I guess you would need a secure backup somewhere safe, because packing and unpacking can fail.

But, again, we will see if folk are interested in this idea and can think of enhancements.

gsl

---

### Post by oOsupremeOo on 2007-05-24
Greetings All, this is my first post so be gentle. I finally made the jump from Windoze to Ubuntu, and I gotta tell ya I'm totally satisfied!!! 
As far as USB Ubuntu here is the link to the tutorial :

 [http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/#more-200](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/#more-200)

The total install took about 45 minutes.

Good Luck!!!!

:D

---

### Post by trapix22 on 2007-05-24
Thanks ..Supreme.. That worked beautifully. Exactly what I wanted. Thank you everyone else who tried to help me along the way.

---

### Post by rggavubt on 2007-06-01
> **trapix22 said:**
> I am looking to run linux (probably xubuntu) from my laptop with no hard drive at all. I want it to do EVERYTHING... Boot from it, install new software to it, save my files to it, etc... so when I'm gone, my entire system goes with me. My questions are...

1) Booting:
       a) My BIOS (Phoenix Award) doesn't support boot from USB. Can I change/upgrade BIOS?

       b) If "no"... Could I get a basic linux OS on floppy and boot to it in text mode, then from                    
          text mode load (i.e. xubuntu) from USB?

2) Security:
       -I'd like to encrypt (i.e. dm-crypt) the entire USB so if I lose it (or gets stolen), no one
        can get to my data

I know this is quite a project but I've spent hours searching and found pieces of what I want to do but can't quite put it all together.

I've had my clients' VERY private info stolen and misused and I am determined to NEVER let that happen again. I think this might be the way to go. I'm open to any suggestions. Thank you for the help.

In reference to question #1 above...I have a Dell laptop with the same bios.  I found out(with laptop off) that if you plug in your USB stick and then turn on the laptop and got to setup(F2 on mine) you can then go to the boot menu and you will see the usb stick listed under the harddrives after you hit enter in the harddrive section...move USB up above the harddrive and save and exit.  It will now boot from the USB.  Only problem is that you have to do this each time you want to boot from the USB.

---

