---
title: "WARNING: external USB hard drives"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by somevietnameseguy on 2007-11-10
From my particularly terrible experience today, I should warn people about taking extra care in this matter. If you have an XP (or vista) OS installed on your internal hard drive and are about to try and install Ubuntu on an external USB hard drive, then be warned that the boot up program GRUB could screw things up for you.

Probably not relevant, but here is my system info:

Windows XP Pro
Intel 3.0ghz
2MB DDR2 RAM
Geforce 6600
40GB Internal
30GB USB HD

I started by creating an ISO image of Ubuntu 7.10 on a CD on windows and then rebooted with the aim of installing it onto my USB HD. All went fine (after making a second CD at 1x write speed). 

However, even though I had used detailed instructions (the large thread in this forum about this topic) I realised that the GRUB boot up program had installed onto my Windows hard drive, when I was trying to take all measures for this not to happen (obviously not very well). It turns out in the installer, the option to install GRUB is in the last step, but you have to press the 'Advanced' button and select a hard drive. The setting there is (hd0) which i'm assuming is the internal HD.

So I decided to try and install it again, but selecting (hd1) instead. Grave error. The install failed and now I neither had a bootable Windows or a bootable Ubuntu. Upon restart, GRUB kept on coming up with either 'Error 15' or 'Error 21'. Luckily I could use the CD (just about) to use Ubuntu and search the internet for answers. No luck really. I dont have an XP CD on me to reset the MBR (boot record thing which is changed by GRUB). Perhaps i'm not knowledgable enough with computers to do the other options available.

I tried reinstalling several times, but each time the CD was deemed corrupt. Then the installer was failing to create a partition. I even downloaded Ubuntu 6.whatever (the long term support one) to see if that would install on the USB HD. No luck again. Eventually, on the umpteenth attempt at installing Ubuntu 7.10, it finally worked (a good 14 hours later). I now have Windows back, but having to go through the GRUB menu every time I boot up. Plus no linux. So basically i've gone half a step backwards from where i was this morning. I'm reluctan right this minute to turn off my computer in the fear that GRUB will stop working (solution anyone???)

This is not me posting hate up about Linux, no way! I am very very much looking forward to using it one day. However, right now i'm slightly annoyed at how difficult it was. If anyone can give me consolation, please do. I'm really quite annoyed right now. Elated at having at least a working OS back (even if it's Windows) but annoyed that my entire saturday was utterly wasted, especially after hearing how easy Linux is to install so many times on the internet. Perhaps trying to use a USB HD was a mistake.

So please back up your internal hard drive before doing anything like this (as in a complete image of the hard drive that can be booted from). I made the mistake of not doing this...or backing any data up in fact. Just wanted to warn people about this. :)

---

### Post by Ocxic on 2007-11-10
for one, you'll need to use either grub or the windows boot loader,, you can't have both,, yes grub prolly installed on your internal hd,, wich is what you would want it to do,, grub will load the windows boot loader when you want to start windows,, I belive your mistake here would be trying to re-install ubuntu a second time ,, it prolly fouled everything up with you boot loader.. if you got your windows mbr back,, and windows working again I would suggest trying again with the alternat install cd 
and remember you want grub on your internal hd cause it'll be your internal hd that your computer will look for the boot loader,, anyhting on the usb drive it won't see unless you select to boot from it in your bios,, or you can go thru all the uh-bub to use the windows boot loader

---

### Post by Pumalite on 2007-11-10
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://partedmagic.com/](http://partedmagic.com/)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by xyphur on 2007-11-10
Hiren's Boot CD has a plethora of partition/drive tools that will facilitate repairing your windows MBR. You can locate an ISO of this disc using your good friend Google, and some creative inclusion of the word 'torrent'. I believe the latest version is 9.3.

Once you've fixed your internal drive's MBR, I would suggest unplugging that internal drive and then installing Ubuntu to your USB drive. Eliminate possibilities for failure when you can. Of course, you'd only want to do this if your BIOS is capable of booting from USB devices. If it can, it would be the easiest route. By setting the boot order to USB before the internal drive, when there's no USB drives that are bootable connected, windows would boot normally using it's native bootloader. If there is a USB device that's bootable connected, it'll boot from that (using GRUB located on the USB drive) and Ubuntu will load.

Failing all of that, like someone above mentioned, you absolutely have to have GRUB on your internal drive to get both Ubuntu & Windows booted.

---

### Post by Herman on 2007-11-10
> Perhaps trying to use a USB HD was a mistake.I am sure you will find Ubuntu will be much simpler to install in an internal hard drive when you get up the courage to try it properly some day. It takes most people between fifteen minutes and half an hour or so.

Although it is possible to install it in a USB drive and USB drives are all very nice and portable and all, Ubuntu was not really designed for that kind of use. It can be done, but it's more for experts than ordinary users, and even then only certain computers can boot a USB drive.  Two out of my four computers cannot boot a USB drive at all, one can chainload a USB drive from GRUB in the MBR of the internal hard disk, and one can boot a USB from the BIOS.
So you can give yourself a pat on the back and be proud of yourself that you got this far in only one weekend! Well done! :)

There are other Linux distros that are designed to be used with USB drives. 
A really good one is Knoppix. With a Knoppix CD or DVD, you can make an encrypted persistent /home in your USB disk, and boot it from almost any computer in the world, because you only need to boot the CD or DVD, not the USB disk. And it won't touch your hard disk at all, (unless you need it to).
Here's my how-to on Knoppix, [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html")

Ubuntu or GRUB won't hurt your Windows either, you just think they did, because you probably aren't used to having your MBR changed and then having to change it again back to how it was before. Actually, the MBR is just another sector on the hard disk that can be written to and overwritten again as many times as we like, it will never wear out. It is made of the same material as the rest of the hard disk. It is just that we use different programs to write to it. When you get used to using those programs it's really not much to worry about at all.
The boot loader section of the MBR is especially simple to deal with, as long as you can get your hands on the software to do it, and the right instructions.
Here's a web page with a whole list of different software you can use for that, and  how to use it,  [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")  You should be able to find something there that will help you, if xyphur's help isn't already enough.

I agree with the idea of warning people the installing Ubuntu to a USB disk isn't for everyone. I think Ubuntu is better installed in an internal hard drive (and preferably after deleting Windows)! 

But you can dual boot until you learn how to do everything better in Ubuntu.  :)
It's not that I hate Windows or anything, it's just that I don't know how to use Windows without having to pay extortion money for 'protection' against all manner of malware, adware, script kiddies, etc, etc, (you name it)...

Try Ubuntu out in an internal hard drive and see how much better it is. :)
You will find out that if you use Ubuntu for collecting email and all your internet browsing your Windows will stay clean as long as you keep it off the internet.
Eventually you'll learn how to do all kinds of things you wouldn't be able to do with Windows, and some day you'll realize you haven't booted Windows for such a long time you'll be lucky if you remember your password.

Regards, Herman :)

---

### Post by somevietnameseguy on 2007-11-11
Thanks for the response everyone.

At the moment I can't run the Ubuntu installed on the USB HD because I don't think I've installed it properly to be able to boot from USB. Whatever the case, i'm wanting to go back to the original Windows MBR instead of going through GRUB every time (with the final aim of installing Ubuntu onto a new internal HD without touching this one).

Firstly, is GRUB going to stay stable? Every so often the GRUB loader comes up with 'Error 21'. Restarting usually fixes it, but i'm just worried that one day it might pack up and die. That's kind of why I want to restore the original Windows MBR.

I've heard a solution is to run 'fdisk /mbr' in the XP desktop, as I dont have an XP disc handy. Is this recommended? I hear it can muck up easily (eg destroy everything on the internal HD). There several other options ive seen available, but 'fdisk /mbr' seems the easiest...i'm just wondering whether it's really worth the risk or destroying everything just to shave off 20secs of boot time.

Thanks

---

### Post by Herman on 2007-11-11
Here is a link about GRUB error 21, [Grub error 21]("http://users.bigpond.net.au/hermanzone/p15.htm#21").

I imagine since you have the first part of GRUB installed to MBR inside your computer and the rest of GRUB in your USB disk, then it depends on whether your computer's BIOS can 'see' the USB disk properly or not.
If you tried to boot without the USB disk plugged in you would get GRUB error 21 for sure. It seems like if it's intermittent then you might have some kind of a buggy BIOS that detects the USB sometimes and not others.
It's not GRUB that's unstable, it's the way you have things set up right now.

The command 'fdisk /mbr' is the command you use with a Windows 98SE boot floppy disk. That will restore a Windows 98 bootloader code to MBR and it also works fine for Windows XP if you don't have a Windows XP install disk.
Here is a link about that,[ Windows 98 Floppy Disk Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method"). 

To use a Windows XP recovery console (from a Windows XP install CD),  to overwrite GRUB's IPL and put the Windows IPL in the MBR, you use the command 'FIXMBR'.
Here is a link about that, [Windows XP 'Recovery Console' method.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console")

I have never heard of anyone's data being destroyed by changing the bootloader code in the MBR.
If people have some small booting problem they can't solve and they can't get the proper help they might panic. It doesn't affect their data at all, just that they can't access their data in the normal way until they fix the problem. With some people, emotions take over and replace logic, so they think they have lost all their data, but it is all in their imagination.  Some people get so impatient they go and delete their own data themselves and re-install Windows. If they waited for help they would still have all their data.
You can rewrite your Windows bootloader's code back into your MBR quite safely. 
In the unlikely event that something does go wrong, we have software that can fix it.

Regards, Herman :)

EDIT: Another way to restore the Windows boot loader in MBR is to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), the last time I checked, Super Grub Disk could do that. Super Grub Disk is free and it's a very small download and it's extremely useful for coping with all kinds of booting problems.

---

### Post by somevietnameseguy on 2007-11-11
Thanks for your help mate. I think i'll wait until I find my XP disc and fix the mbr then. At the moment, you'll be pleased to hear I have installed Mandriva 2008 on a spare internal hard drive (which currently involves switching the cable to boot from) but its all up and running.

Thanks again

---

### Post by teabuntu on 2007-11-15

Hi,
I'm totally new with things Linux and Ubuntu.  I have the Gutsy Gibbon Live CD that I got from Shipit, and have been searching for the best way for me to install Ubuntu.  Like the original poster, I was thinking of installing ubuntu on a USB stick.  This might sound like a no brainer question, but does installing Ubuntu (whether on a seperate USB stick, or together on a singel disk with Windows) change the BIOS codes that is there on my computer right now?

Thanks for any help on this.

---

### Post by NotTheMessiah on 2007-11-15
No it doesn't change the bios until you change it(boot preferences)

---

### Post by teabuntu on 2007-11-15
Hi,
Thanks for the reply.  During Ubuntu installation of Gutsy, will I be asked about boot preferences and so forth?

---

### Post by NotTheMessiah on 2007-11-15
You'll be asked where do you want to install gutsy(and you can make partitions )
But make sure you back up everything before you install. First try the livecd , it will load gutsy in ram so you can play with it before you install, you'll see the desktop and an install icon on the desktop. So check the desktop out and back up of course and when you are ready click on the install

If you want to change boot preferences press the delete(button) on boot up, and you'll enter your bios where you can modify options

---

### Post by Herman on 2007-11-15
You will only need to go into your BIOS settings and change the boot preferences if your computer isn't set to boot from the CDROM drive before the hard drive. If it isn't, then your Ubuntu CD won't boot, your computer will jst boot up as usual and show the CD as  folder full of files probably.
In case you don't know how to do that, here's what it looks like in my computer, but yours will be a little different, [BIOS' 'boot order]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_boot_sequence_in_CMOS").
As long as you can get a LiveCD to boot, that's all most people need to do in their BIOS settings.

Here is a great website that has an lot of informatuion about installing Ubuntu from the 'Desktop' (Live) CD and getting started with Ubuntu,  [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

Regards, Herman  :)

PS: ...and I agree with what NotTheMessiah said above, sorry for the simultaneous post.

---

### Post by teabuntu on 2007-11-15
Hi,
Thank you guys for the reply.  Just to be sure that I understood you correctly (since I'm totally new with things Linux and Ubuntu), installing Gutsy will NOT chnage the current BIOS codes on my computer?

---

### Post by teabuntu on 2007-11-16
bump

---

### Post by NotTheMessiah on 2007-11-16
I suggest that you read up on installing Ubuntu especially focus on GRUB loader which will be installed on your hard disk and it will be used for booting into your different partitions like - Gutsy partition,XP , Vista etc. Now, there are some hard disk issues with gutsy so you need to do some research on it so you'll know what to expect and do.If yyou install it properly gutsy will not delete any other partitions that you might have on the Hard disk even if you get GRUB boot errors - the partitions will be there.

---

### Post by teabuntu on 2007-11-16
Thanks for the advice.  Would you ahppen to know of any sites that you could recommend?

---

### Post by EspressoRulz on 2007-11-16
When I installed Ubuntu onto an external 2.5in HD I disconnected my internal (WinXP) hard drive from the laptop so the installer wouldn't see it at all.  Booted from CD and installed everything, including Grub, to the external drive.  After the install I reconnected the internal HD and set the bios to boot via CD/DVD first, USB second, and HD last.  When the USB HD is connected it boots up in Ubuntu AND has access to my XP files to boot!

---

