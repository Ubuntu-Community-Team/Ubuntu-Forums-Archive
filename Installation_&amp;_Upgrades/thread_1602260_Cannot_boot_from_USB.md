---
title: "Cannot boot from USB"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by mster on 2010-10-21
I cannot get my laptop to boot up any system.  My CD drive doesn't work so I have for months been trying to boot from USB.

I thought maybe my hard drive was b*ggered so I bought a new one but have the same problems.

I am at the moment trying to boot into ubuntu 10.04 I just get the message "vesamenu.c32: not a COM32R image"

when I try to boot from the Hard Drive (ie no usb attached) it goes to the grub> prompt.

It also says


"GRUB version 0.93 (639k lower / 121664k upper memory)

[minimal BASH-like line editing is supported. For the first word TAB lists the possible completions of a device/filename.]

grub>"

Can anyone help please?

I'd really love to be able to use my laptop again..

Thank you!!

Marianne

---

### Post by viralmeme on 2010-10-21
> **mster said:**
> I cannot get my laptop to boot up any system.  My CD drive doesn't work so I have for months been trying to boot from USB

What did you use to create the USB distro? I downloaded the latest Lubuntu ISO and used the USB creator on a Ubuntu 9.10 installation to make a USB that boots. This might have something to do with it.

"[vesamenu.c32: not a COM32R image]("http://ubuntuforums.org/showthread.php?p=9955215")"

---

### Post by Rubi1200 on 2010-10-21
See here for some options to boot from the GRUB prompt which you are seeing:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Good luck!

---

### Post by mster on 2010-10-21
> **viralmeme said:**
> What did you use to create the USB distro? I downloaded the latest Lubuntu ISO and used the USB creator on a Ubuntu 9.10 installation to make a USB that boots. This might have something to do with it.

"[vesamenu.c32: not a COM32R image]("http://ubuntuforums.org/showthread.php?p=9955215")"

I used 10.10 to make a usb bootup for ubuntu 9.10 is that the problem?

I am currently downloading 10.10 and will try that.. :)

fingers crossed.

Any more suggestions before I try it? - I take it that creating a startup usb in system/startup disk creator is all I need to do and then just restart my laptop with the usb in? - it's set to boot from removable device already.

Thank you

Marianne

---

### Post by mster on 2010-10-21
I am also going to download the 10.10 alternate iso (the text based one) to see if that works if this fails.

Any more advice would be most grateful - I am a newbie at grub and Ubuntu as I have used the dreaded windows all my life.

For me Ubuntu is turning out to be a bit complex, which is a shame as I really like it and have it running fine on an old desktop pc that I turned to when my laptop died (the one I am using to post this message)

Really hope my laptop isn't a lost cause. :(

---

### Post by mster on 2010-10-22
Still need help!

The furthest I got was with lubuntu 10.10 by typing acpi=off when tabbing at the install menu I got a little text lubuntu 10.10 and the rolling dots underneath - it didn't progress though and the screen went black, no noise from pc - just stalled.

---

### Post by utilitytrack on 2010-10-22
Hello, if you have some Ubuntu installed, can you provide this:
```
$ dpkg -l syslinux\*
```

[B]EDIT:
[/B]See this: [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications")

Workaround: [http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/]("http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/")

---

### Post by mster on 2010-10-22
> **utilitytrack said:**
> Hello, if you have some Ubuntu installed, can you provide this:
```
$ dpkg -l syslinux\*
```



Hi I managed to get into drop to prompt with networking in recovery mode and typed in the above, this is the text:

> 
Desired=Unknown/Install/Remove/Purge/Hold
Status=Not/Int/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
/Err?=(none)/Reinst-required (status,Err: uppercase=bad)
/Name               Version           Description
ii syslinux         2:4.01+dfsg-3u    collection of boot loaders
ii syslinux-commo   2:4.01+dfsg-3u    collection of boot loaders (common files)




Does this help?!?!

---

### Post by mster on 2010-10-23
can anyone help?

---

### Post by utilitytrack on 2010-10-24
> **mster said:**
> can anyone help?

You should try to use other version of Ubuntu, or some other live distributions wich don't have such problems with Syslinux bootloader: Knoppix, Fedora LiveUSB, etc. For example, for to do this you can use unetbootin installer: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") (it available for Linux or DefaultOS)

---

### Post by mster on 2010-10-24
> **utilitytrack said:**
> You should try to use other version of Ubuntu, or some other live distributions wich don't have such problems with Syslinux bootloader: Knoppix, Fedora LiveUSB, etc. For example, for to do this you can use unetbootin installer: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") (it available for Linux or DefaultOS)

Thank you utilitytrack, I'll get on that right away :)

Have a great weekend.. :guitar:

---

### Post by arnavk007 on 2010-10-24
My suggestion is that u use Linux mint live USB or try fedora
both are gr8

---

### Post by mster on 2010-10-25
I have tried fedora 13, debian 5, ubuntu 10.10, lubuntu 10.10 ubuntu 10.10 alternative

no luck.

With lubuntu mini iso I managed to install all of the files over my ethernet connection but could not get the desktop up no matter what i tried.

then I tried updating my grub config to include acpi=off and i.915modeset=0 (as per nvidia graphics tutorial on wiki) but this did not have an impact either.

I officially give up. :(

---

### Post by Rubi1200 on 2010-10-25
Did you try any of the options from the thread I linked to in my previous post?

Please don't give up!

There are still some other distros you could try, including Puppy Linux, SliTaz, AntiX, and Damn Small Linux.

It would also be helpful if you could post the full specifications for the laptop.

---

### Post by mster on 2010-10-25
> **Rubi1200 said:**
> Did you try any of the options from the thread I linked to in my previous post?

Please don't give up!

There are still some other distros you could try, including Puppy Linux, SliTaz, AntiX, and Damn Small Linux.

It would also be helpful if you could post the full specifications for the laptop.

 Hi   I just managed to get knoppix to work!!  So I have installed it to my HARD DRIVE (I read that it's not recommended but I did it and it works..)  :popcorn: anyone? :)

---

### Post by utilitytrack on 2010-10-25
> **mster said:**
> I have tried fedora 13, debian 5, ubuntu 10.10, lubuntu 10.10 ubuntu 10.10 alternative... no luck.

It seems there is some hardware problem. What laptop do you use?

---

### Post by mster on 2010-10-25
> **utilitytrack said:**
> It seems there is some hardware problem. What laptop do you use?

I got it more than 8 years ago in January 2002!

It's a notebook I think.

EI Systems

Celeron2.4 Ghz processor
256 MB RAM (but I installed 1GB)
40 GB HDD
DVD Rom + CD Writer (Combo Drive)
5x USB ports.
TV Out
15" TFT

---

### Post by Rubi1200 on 2010-10-25
We still need to know what graphics card you have installed.

You said you installed Knoppix?

Go to the terminal and post the output of```
 lspci | grep VGA
```
Thanks.

---

### Post by mster on 2010-10-25
> **Rubi1200 said:**
> We still need to know what graphics card you have installed.

You said you installed Knoppix?

Go to the terminal and post the output of```
 lspci | grep VGA
```Thanks.

Sorry!

Here it is

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by Rubi1200 on 2010-10-25
Thanks for the information.

I know you have tried a number of things already, but humor me and try the following:

Get another Ubuntu CD or USB and boot the computer.

Then do the following:

Put the LiveCD or USB in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line (you may have to do this first before the step above)

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop of the LiveCD/USB.

Let us know if this works.

---

### Post by Hakunka-Matata on 2010-10-25
mster:  The most reliable application for me to build a good USB boot drive has been unetbootin.  

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

It was mentioned by utilitytrack in an earlier post, I mention it again to add credence.  It has worked for me where other schemes have not worked.  
Good Luck

---

### Post by mster on 2010-10-26
Sorry, didn't work.  Still got the Black Screen of Death..

I do get the feeling it's booting okay though but the graphics are just not showing on the screen.  I made sure the brightness was up as I read that it sometimes gets reset.

no worky.. :(

---

