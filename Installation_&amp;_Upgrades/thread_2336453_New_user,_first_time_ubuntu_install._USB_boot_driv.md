---
title: "New user, first time ubuntu install. USB boot drive will not work."
date: 2016-09-08
forum: Installation &amp; Upgrades
---

### Post by no-win10 on 2016-09-08
So I downloaded the latest version of Ubuntu from the Ubuntu website. I then follow their instructions and used Rufus to create a bootable USB drive. The USB drive is a brand new 16gb Sandisk.
When I start my PC I press f10 to bring up boot menu and choose to boot from the USB drive, then a purple screen comes up with what looks like a picture of a keyboard set = to a little stick figure in a circle at the bottom center of the screen.
Then the screen goes black and there is a curser and I can type stuff but nothing else happens. Its just sits there.

Any help would be appreciated. Thank you in advance.

This is the first time I have ever tried to use anything other than windows, but recently Microsoft's antics with Win10 have pushed me to make the switch.

---

### Post by nothingspecial on 2016-09-08
You are supposed to see the purple screen with the little stick figure.

So you either have a bad Ubuntu ISO (unlikely), a bad usb stick (also unlikely), a bad live usb installer image (probably) or some hardware or secure boot EFI stuff that the installer doesn't like (possibly).

So, post your system specs make, model, graphics card etc and while you wait for another reply, try formatting the usb stick and making the live usb installer again.

---

### Post by cybrsaylr on 2016-09-08
I had the same problem and solved it here: [https://ubuntuforums.org/showthread.php?t=2336409](https://ubuntuforums.org/showthread.php?t=2336409)


Been using Linux for several years and was able to solve it with the directions given in that thread.

If you are brand new to Ubuntu it may be easier to create a bootable DVD from the ISO you downloaded.

---

### Post by #&amp;thj^% on 2016-09-08
> **nothingspecial said:**
> You are supposed to see the purple screen with the little stick figure.

So you either have a bad Ubuntu ISO (unlikely), a bad usb stick (also unlikely), a bad live usb installer image (probably) or some hardware or secure boot EFI stuff that the installer doesn't like (possibly).

So, post your system specs make, model, graphics card etc and while you wait for another reply, try formatting the usb stick and making the live usb installer again.

Sorry Off Topic But just had to say Hi to nothingspecial && Long time no see.

---

### Post by no-win10 on 2016-09-08
System specs: Intel core i5 3570k socket 1155 (no oc)
                     Intel DZ77RE-75K I do believe I have the latest bios installed 
                     16 gig of kingston hyper x DDR3 1600
                     Nvidia gtx 770
                     Windows 7 home premium service pack 1 64 bit

---

### Post by oldfred on 2016-09-08
Your system is UEFI, so you can boot in either UEFI or BIOS. If you have Windows installed you want to be sure to install Ubuntu in same boot mode. Windows 7 default install is BIOS, but it can be copied to flash drive and installed in UEFI boot mode. So depends on how you installed.

But with nVidia you have to add nomodeset whichever way you boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With UEFI or after install you have grub menu. If BIOS you use anykey and f6.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by no-win10 on 2016-09-08
Ok, you just said alot but I think I understand. There are two environments you can boot into UEFI and or BIOS and with WIN installed on the same machine I must boot Ubuntu to the same environment.
I'll read the page you linked me too and see if I can work it out.

One question though. If I had a fresh clean HD without any previous OS on it would I be able to install Ubuntu on it from the USB drive I made? Would it be easier?
Basically I just wanted to boot Ubuntu on my current system with windows 7 on it just to click around and see if I like it. But I am sick of windows and I want some thing new and I want to learn more any way so I will probably just stick with Ubuntu.

---

### Post by RobGoss on 2016-09-08
> **no-win10 said:**
> Ok, you just said alot but I think I understand. There are two environments you can boot into UEFI and or BIOS and with WIN installed on the same machine I must boot Ubuntu to the same environment.
I'll read the page you linked me too and see if I can work it out.

One question though. If I had a fresh clean HD without any previous OS on it would I be able to install Ubuntu on it from the USB drive I made? Would it be easier?
Basically I just wanted to boot Ubuntu on my current system with windows 7 on it just to click around and see if I like it. But I am sick of windows and I want some thing new and I want to learn more any way so I will probably just stick with Ubuntu.


Yes it would be a simple process to install Ubuntu on a clean hard drive with no other operating system on it, you would not really have to worry about partitioning and things like that. You can burn the ISO file of Ubuntu on to the **USB** stick and after booting in to the live session run the installer and choose to use the** entire disk** and follow the instructions

---

### Post by sudodus on 2016-09-08
Maybe this link and links from it helps you try Ubuntu:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by no-win10 on 2016-12-31
So I read the UEFI wiki and decided to just try a fresh install with a brand new hard drive. I bought a 2t sea gate firecuda and I still run nito the same issue. I can get to the screen where it asks me if I wish to try Ubuntu, install Ubuntu etc but when I select install Ubuntu the system just hangs on a black screen with a blinking curser.

So I am not sure what to try now.

Any advice would be greatly appreciated.

Thank you,

---

### Post by ScientificProp on 2016-12-31
I'm not an Ubuntu expert by any means, but I've been using it awhile. Have you selected to just try it instead of going right to an install. If you select to "try Ubuntu" that lets you verify that the system is working with your hardware. Before I install to a hard drive, I just installed 16.04 to a new SSD, I always select try the OS and then select install. If you want to try out the linux and see how it works, I'd try that first.
The problem you described reminds me of the 1st Ubuntu installation I did several years ago, It ended up being a problem with the graphics video driver. See one of the earlier responsed that mentioned "nomodeset".

---

### Post by gordintoronto on 2017-01-01
+1 for nomodeset.

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by no-win10 on 2017-01-02
So I tried the nomodeset thing but still same problem. It just go's to a black screen with a blinking cursor and hangs there.
I have tried with the UEFI on and also set to legacy boot in my bios still no go.

If I select boot from UEFI USB boot loader option instead of just booting from the USB drive it go's to a black and whiter screen with all the install and boot options but still same result.
I have a brand new hard drive that has never seen an OS before the UEFI shouldn't even be a problem at this point. 

I hate windows even more now.

---

### Post by oldfred on 2017-01-02
How you add nomodeset differs between BIOS (purple screen) and UEFI (black screen with grub menu).

In UEFI are you editing grub linux line to add nomodeset. Best to replace quiet splash with nomodeset so then you can see boot process in case additional boot parameter required to resolve another issue.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by ScientificProp on 2017-01-04
Have you tried any other Linux distributions? A couple years ago I was able to boot up Mint when I had troubles with Ubuntu. I believe someone else suggested you try booting up from a DVD instead of the USB Flash; have you tried that? Good Luck. You're reminding me of my first Ubuntu install, since then I haven't had any trouble loading the OS. Since then, I added an NVidia graphics card, a basic one ($60).

---

