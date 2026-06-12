---
title: "Ubuntu v12 Installation on a external HDD issue"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by pyro117 on 2012-07-20
I am very new the ubuntu and followed a few articles about setting up  and installing ubuntu to an external HDD.  Here were the steps I  followed:
 
 1.  Created a 64-bit bootable DVD drive from the latest downlaoded version 12.04 (I think)
 2.  Booted the laptop with that DVD
 3.  Setup a /boot mount with 500mb on the external drive
 4.  Setup a 4GB swap disk
 5.  Setup a / mount with approximatly 75 GB (the rest of the external drive)
 6.  Made sure the boot was selecting the sdb drive
 7.  Allowed the installation to finish
 8.  Rebooted and selected the laptop boot menu, from here I told it to boot from the external HDD
 9.  I get a screen with several options.  I pick the top one (boot into ubuntu).
 10.  I get stuck no a purple screen and nothing.  My laptop has an intel graphics card.
 
 Any ideas on what to try next?
 
 I can't put anything ubuntu on the primary HDD because it is a work  laptop.  Also my graphics card is an intel based graphics card.

---

### Post by darkod on 2012-07-20
Looks like video driver issue, but I am not sure which one do you need to use for intel.

One way to try, is to try to boot the cd in live mode (Try Ubuntu). If it's a driver issue, it will get stuck too.

You can google around your intel graphics model and ubuntu 12.04.

---

### Post by sudodus on 2012-07-20
You can also try some boot option. See this link

[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Press **F6** and select one or several boot options at the screen described in the link. Start with ***nomodeset***

---

### Post by pyro117 on 2012-07-20
Sorry, but it was a black screen that it hung on.

I just let it sit and it finally came back with the following errors:

[INDENT]Gave up waiting for root device.
<common problems>
ALERT! /dev/disk/by-uuid/a1000b700-xxx-xxx  does not exist.  
Dropping to a shell!

BusyBos v1.18.5

(initramfs) ata_id[265]: HDIO_GET_IDENTITY failed for '/dev/sdb':  Invalid argument
[/INDENT]
not sure what I should do at this point.

---

### Post by pyro117 on 2012-07-20
I can also boot to the CD and "try Ubuntu" with no issues.  Its just the installation to the external HDD that is failing.

---

### Post by pyro117 on 2012-07-20
I have been searching for help and found the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/931929](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/931929)

Can someone explain it to me, please?  The steps that are necessary....

EDIT: tried dmraid -ay and I got "/bin/sh: dmraid: not found

This makes sense to me since it is a install to an external HDD and not a raid environment.

---

### Post by pyro117 on 2012-07-20
I know I am posting a lot but I am trying different things and posted what I am finding in hopes it can help.

I booted using the "recovery mode" and I get a slightly different error on boot:

(initramfs) [  34.007882] usb 1-1.1: reset high-speed USB device number 3 using echi_hcd


What is echi_hcd?  I tried to type the command to get help, but it says ehci_hcd is not found.

I hope this helps.

---

### Post by darkod on 2012-07-20
That's a USB port and the high-speed usb device mentioned might be your ext hdd.

One option is that the hdd is not detected (online) fast enough so that the boot can start/continue.

Try this, plug the ext hdd, and boot the computer. Immediately go into BIOS (not just the boot menu). Open the BIOS but don't make any changes, simply wait a little while the ext hdd comes online.
Exit the BIOS without making changes. Does it boot from the ext hdd or not?

In fact, in BIOS you can configure to try the USB-HDD before the internal HDD. That way if you have the ext connected, it will try to boot it. If not, it will try the internal.

For cases like there is also parameter root-delay=90 or similar, but not sure if it will help. When you see the grub boot menu with the ubuntu entry highlighted, hit 'e' for edit, go towards the end of the line starting with linux where it says 'quiet splash' and add root-delay=90.
Press Ctrl+X or F10 to boot. Did that work?

---

### Post by sudodus on 2012-07-20
> **pyro117 said:**
> Sorry, but it was a black screen that it hung on.

I just let it sit and it finally came back with the following errors:

[INDENT]Gave up waiting for root device.
<common problems>
ALERT! [COLOR="Red"]/dev/disk/by-uuid/a1000b700-xxx-xxx  does not exist[/COLOR].  
Dropping to a shell!

BusyBos v1.18.5

(initramfs) ata_id[265]: HDIO_GET_IDENTITY failed for '/dev/sdb':  Invalid argument
[/INDENT]
not sure what I should do at this point.

I think that it is a big problem, that the partition is not found (I guess it is the root partition). Can you check, that the partition UUID number is correct, and that the drive id number is correct. Maybe it helps to read the following link
[[COLOR="red"]_https://help.ubuntu.com/community/Grub2_[/COLOR]]("https://help.ubuntu.com/community/Grub2")

---

### Post by pyro117 on 2012-07-20
> **darkod said:**
> That's a USB port and the high-speed usb device mentioned might be your ext hdd.

One option is that the hdd is not detected (online) fast enough so that the boot can start/continue.

Try this, plug the ext hdd, and boot the computer. Immediately go into BIOS (not just the boot menu). Open the BIOS but don't make any changes, simply wait a little while the ext hdd comes online.
Exit the BIOS without making changes. Does it boot from the ext hdd or not?

In fact, in BIOS you can configure to try the USB-HDD before the internal HDD. That way if you have the ext connected, it will try to boot it. If not, it will try the internal.

For cases like there is also parameter root-delay=90 or similar, but not sure if it will help. When you see the grub boot menu with the ubuntu entry highlighted, hit 'e' for edit, go towards the end of the line starting with linux where it says 'quiet splash' and add root-delay=90.
Press Ctrl+X or F10 to boot. Did that work?

Adding a root-delay didn't help.  Thanks for the suggestion.

---

### Post by pyro117 on 2012-07-20
> **sudodus said:**
> I think that it is a big problem, that the partition is not found (I guess it is the root partition). Can you check, that the partition UUID number is correct, and that the drive id number is correct. Maybe it helps to read the following link
[[COLOR=red]_https://help.ubuntu.com/community/Grub2_[/COLOR]]("https://help.ubuntu.com/community/Grub2")


I read through the page and didn't see anything about the UUID number and how to validate it.  I did do some further research on the HDIO_GET_IDENTITY failed message and found this article:

[http://askubuntu.com/questions/150253/trying-to-install-ubuntu-via-usb-getting-error-hdio-get-identity-failed-for-dev]("http://www.officedepot.com/a/products/163375/StarTechcom-25in-Silver-USB-20-to/")

I typed exit like it says and it is just haning on the "ubuntu" with the 5 dots booting screen.

I am not sure if this is part of the problem or not, but the external HDD is fairly old (I believe 1.1 compliant only) and the laptop has USB 2.0 or 3.0 ports (can't remember).  I think ubuntu is having difficulties reading from the slower USB device.  

What would happen if I disabled the echi_hcd thing?  Not that I know how to do that mind you...

Thanks again for everyone's help!  I really want to start using ubuntu.  I have a copy running on a USB drive but it is really limited, but I love the desktop and how it works!

---

### Post by scradock on 2012-07-20
I had a similar problem, where one laptop allowed me to boot into the external USB HD and another laptop would not. I knew the install on the external HD was OK, because it worked with the first machine.

In my case I had a booting linux partition on the internal drive; the solution was to install PLOP, a boot manager, to switch from the sda drive to the sdb drive from the GRUB2 menu. Probably doesn't help you though, if you can't modify the sda drive. Probably you can make a "boot CD" with the boot files on it, plus PLOP, but I cannot give you full instructions.

Hope that helps you find a way forward!

---

### Post by pyro117 on 2012-07-20
> **scradock said:**
> I had a similar problem, where one laptop allowed me to boot into the external USB HD and another laptop would not. I knew the install on the external HD was OK, because it worked with the first machine.

In my case I had a booting linux partition on the internal drive; the solution was to install PLOP, a boot manager, to switch from the sda drive to the sdb drive from the GRUB2 menu. Probably doesn't help you though, if you can't modify the sda drive. Probably you can make a "boot CD" with the boot files on it, plus PLOP, but I cannot give you full instructions.

Hope that helps you find a way forward!

I have tried this on 3 different computers (Toshiba, Gateway, Dell).  My kids laptops and my work laptop.  They all behave the same.  This is the 64-bit version of 12.04. 

I wonder if I should just create a 32-bit version and see if that works.  To me it seems there is an issue with the USB handlers...

I base this off of 2 things and zero knowledge of Ubuntu (so take it with a grain of salt):

1.  This is an older enclosure requiring backwards compatibility
2.  I did get the installation to actually run, but it was not easy and even then it wouldn't recognize my laptop mouse and when I connected a usb mouse, it wouldn't recognize it either.  I had to reboot the laptop with the external mouse already connected.

The article I posted in my last reply was correct in getting it to work (I missed a step the first time I tried it):

One way to work temporarily is to remove "quiet splash" from the command  line in the grub menu and press f10 to begin booting.  When it fails  and prints (initramfs) enter exit and the boot will continue.

---

