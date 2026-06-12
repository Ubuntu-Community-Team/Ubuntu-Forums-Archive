---
title: "Can't install Feisty from a bootable cd"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-05-01
This is what is happening: I was trying to install Feisty from a liveCD, the I tried with Edgy from a live CD or boot cd. However, when installing all the components from the cd to the hard drive I don't see any installation process from 20% or 30%. I also see vertical lines on the screen. If something like this has happened to you or have any advice, please let me know.

just in case, my bootable cds are in good condition.

---

### Post by Cyn on 2007-05-01
I have the same issue. When the installation hits 15%, the machine hangs. All I can do is re-boot.

I ended up installing dapper, and upgrading from there.

---

### Post by rcdeacon on 2007-05-01
I have tried three times to install Fiesty and I get nowhere. It won't even boot up. I thought I had a bad burn so I have burnt two additional cd's but no joy! I can boot many other distros fine live but NOT fiesty. Not sure what the problem is. BTW I have the same problem with Kubuntu.

---

### Post by ssands on 2007-05-01
Well, I'll throw my hat into the ring also. I have tried 3 times to install Feisty xubuntu and it has hung each time. I am trying to install dual boot with Win2K. I have a very clean Win2k install and a 3 GB partition for Fiesty. It hangs at "Installing file system 15%". Any ideas are much appreciated. This is my first foray into the Linux world and I'd really like to start exploring.

Stu

---

### Post by dannyboy79 on 2007-05-01
have you guys tried using boot options like irqpoll or noapic or nolapic? or have you tried using the alternate install cd as that one is text based and solves the lines on the screen as 1 of you stated you had. that's a graphics issue. especially if you have an ATI card. Anyway, try out the boot options and see if that does it. I am sure it will. Also, it's good to make sure you have nothing else attached to the computer, only keyboard, mouse, and monitor NO usb stuff or nothing else. Check out this thread for some more help. It's my personal experience with booting Edgy live cd (  [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688) ) READ THREAD #5 

and then also read the various solutions to getting Feisty to run here: [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by ssands on 2007-05-01
Thanks for the response. I'll check out the links you provided. The problem w/being an absolute beginner is that I have no idea how to use the boot options mentioned or what to expect from them. I will also remove the zip drive that is attached to the machine currently. 

Stu

---

### Post by chrisgreende on 2007-05-01
> **dannyboy79 said:**
> have you guys tried using boot options like irqpoll or noapic or nolapic? or have you tried using the alternate install cd as that one is text based and solves the lines on the screen as 1 of you stated you had. that's a graphics issue. especially if you have an ATI card. Anyway, try out the boot options and see if that does it. I am sure it will. Also, it's good to make sure you have nothing else attached to the computer, only keyboard, mouse, and monitor NO usb stuff or nothing else. Check out this thread for some more help. It's my personal experience with booting Edgy live cd (  [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688) ) READ THREAD #5 

and then also read the various solutions to getting Feisty to run here: [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

Hi Dannyboy

I have been experiencing the same problem.  

I am using an HP omnibook xe3 lapand have tried installing Ubuntu 6.06; 70.4 and now the alternate 6.06 installations.

After the splash screen is displayed laptop screen goes black with two white blocks and then dies.  This happens on both the 6.06 and 7.04 variants.  When I tried the alternative 6.06, the text screen loaded all of the drivers etc then the screen went black with the same two white blocks and although there appeared to be some drive activity the load process went no further.

Although I wanted to migrate to Ubuntu I am now reconsidering returning to Microsoft Windows (is that considered foul language on this forum)  XP of Vista, because when I try to load Windows XP I have no problems at all.


Chris

---

### Post by dannyboy79 on 2007-05-01
ok, well you didn't answer my questions, have you tried the boot options as I asked? this normally fixes various issues with black screens and blinking cursors. also, did you try the break=bottom trick where you correct the graphics driver that ubuntu installer choses, this is another very common issue. when say the text screen loaded all the drivers, what do you mean? what point in the alt install cd to you get to? also, why don't you remove quite and splash from the boot line so that you can see what part it's choking on.

---

### Post by chrisgreende on 2007-05-01
> **dannyboy79 said:**
> ok, well you didn't answer my questions, have you tried the boot options as I asked? this normally fixes various issues with black screens and blinking cursors. also, did you try the break=bottom trick where you correct the graphics driver that ubuntu installer choses, this is another very common issue. when say the text screen loaded all the drivers, what do you mean? what point in the alt install cd to you get to? also, why don't you remove quite and splash from the boot line so that you can see what part it's choking on.

Dannyboy,

Sorry I didnt answer your questions about trying the other boot options.  Yes I have, and I have also tried setting the screen option.

I did not know about the break =bottom trick what is it, and the splash screen seems to run through the loading of all the system drivers.  It then appears to start laoding the system and at that point hangs.  On the Alt disk no splash screen appears

As I am booting from a CD ROM I dont know how to the splash from the boot line to investigate it further.

Thanks again

Chris

---

### Post by Franscisco on 2007-05-02
I finally could install Feisty, but when the system loads I watch on the screen vertical lines blinking. Could this be my graphic card? anyone knows!

---

### Post by Topsiho on 2007-05-02
Please see the number of other threads on this forum which are all about this same problem.

Answering all threads about the same problem is a bit defeating.

The solution that made me happy was using the alternate CD, so avoiding the graphical installer of the Feisty Live CD, which must have some bug that was not there in the previous Ubuntu versions.

Topsiho

---

### Post by dannyboy79 on 2007-05-02
> **ssands said:**
> Thanks for the response. I'll check out the links you provided. The problem w/being an absolute beginner is that I have no idea how to use the boot options mentioned or what to expect from them. I will also remove the zip drive that is attached to the machine currently. 

Stu


well you need to read the screen at the point where it asks you what you want to do, so at the point where you have options like check cd for defects, run from first hard drive, run memtest, etc etc, you need to hit F6. then this will bring up a few lines of text. these are the boot lines, it's telling the cd where to find the kernel image and other stuff needed to boot. so you would then hit 'e' which will edit the line, this should bring up 1 line of text which will have 

quite splash

If I remember right. you want to remove those 2 options and add some options for example

irqpoll noapic nolapic

BUT make sure you don't change anything in front of these lines. then i think you hit 'b' which should boot the live cd using the boot options that you added. this is all from memory so if somethign isn't what I am saying that I apologize and come back for more help.

---

### Post by dannyboy79 on 2007-05-02
> **chrisgreende said:**
> Dannyboy,

Sorry I didnt answer your questions about trying the other boot options.  Yes I have, and I have also tried setting the screen option.

I did not know about the break =bottom trick what is it, and the splash screen seems to run through the loading of all the system drivers.  It then appears to start laoding the system and at that point hangs.  On the Alt disk no splash screen appears

As I am booting from a CD ROM I dont know how to the splash from the boot line to investigate it further.

Thanks again

Chris


well the link that I posted, just read thread #5 and it should refer you to how to do the break=bottom trick. if you can't find it within that thread I linked to it's pretty easy to explain. basically you add break=bottom to your boot line, then the installer will stop along the way, then you need to do this a the initramfs prompt:

chroot nano /etc/X11/xorg.conf

then find the line where it states driver and make it say, "vesa"

and then hit ctrl X (i think) nano will ask you at the bottom if you want to save, then hit "Y", then it'll ask if you want to save it as the same name, hit "Y". then you should be back at the command prompt, then hit

ctrl d

and the installer should continue to boot up.

also, if you don't want to see the boot splash and you want to see where it's hanging, just remove the words 

quite splash 

from the boot line.

---

### Post by dannyboy79 on 2007-05-02
> **Franscisco said:**
> I finally could install Feisty, but when the system loads I watch on the screen vertical lines blinking. Could this be my graphic card? anyone knows!

it most certainly is. once you get into feisty, go to the cli (command line interface) or terminal, and show me the output from 

lspci -v

---

### Post by ssican on 2007-05-02
When there is not BOOT(or Boot ERROR), try  these steps - 1) ON BIOS Setup (at BOOT Settings Configurations) make QUICK BOOT- DISABLED.
2) BURN CD on speed 4X or 3X - (600KB/s or less) with ANTIVIRUS and SCREENSAVER -  DISABLED.
3)Put the CD on CD-ROM/RW DRIVE an RESTART the computer
4) When Restarting the computer, IF there is ERROR (Not Boot), BURN again the iso image on a CD-R/RW of better Quality, but before check MD5SUM (MD5Hash) on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

EDIT: After Download of iso image, DEFRAGMENT YOUR HARD DISK DRIVE.

---

