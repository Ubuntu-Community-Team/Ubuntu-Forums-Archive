---
title: "Packard Bell EasyNote TE69KB : White screen after installation Ubuntu 12.04"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by Snube on 2014-02-11
Hey,

so my problem is, I installed Ubuntu 12.04 on my laptop, and i got it installed ok. But after installation, every time i try to boot my ubuntu, it loads a while, then appears text "Checking battery state.......OK" and then it throws a white screen, and it won't go any further. I have kinda cheap laptop (Packard Bell EasyNote TE69KB series) with preinstalled Windows 8. Is there anything that can be done about this, or is Ubuntu unavailable for my laptop? My laptop has AMD Radeon HD 8240 graphics card, if that helps anything.

---

### Post by Portaro on 2014-02-11
Your problem probably is a graphical problem, I think that you need / try give a parameter to kernel boot to use a xorg primary config.

Try to boot in safe mode (press "e" at boot) to see if boot and if boot, you need give to us what is you Graphic card type , and then try to find what kernel parameter can be send to kernel boot with no parameters to graphic mode by default -
for example with ATI cards the parameter that I know is - radeon.modeset=0.

About this kernel parameter i recommend to you see this forum post ->
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Snube on 2014-02-12
So I tried to put "nomodeset" parameter, after booting in grub menu, and pressing "e" to get to edit parameters for this boot. If i put the nomodeset there, it gets me only purple screen, and it's stuck there for like forever.

Then i tried to enter recovery mode, and put the "nomodeset" in the /etc/default/grub file, but it won't let me, because it's somehow "write-protected".

What do? :)

PS. Sorry for bad articulation.

---

### Post by Bucky Ball on 2014-02-12
*Thread moved to **Installation and Upgrades**.*

Welcome. Choose the recovery kernel and add 'nomodeset' to the end of that (after 'quiet splash') and run recovery. That way you should be able to get some idea of what's causing the hold up.

As far as I know, though, nomodeset is for Nvidia cards and you're running AMD. :-k

How did you install Ubuntu? Does Windows 8 still boot? Windows 8 preinstalled is installed in EFI and you need to switch off fastboot, secureboot and faststart before you install Ubuntu.

---

### Post by Snube on 2014-02-12
Bucky Ball, I tried to add the 'nomodeset' after quiet splash to recovery kernel, but it won't let me edit the /etc/default/grub.cfg because it's write-protected. 

I installed ubuntu from USB-stick, and at first, i had trouble installing, but with 'nomodeset' it let me install it normally. And my Windows 8 works normally, and fastboot, secureboot etc are switched off, when I try to boot Ubuntu.

---

### Post by Bucky Ball on 2014-02-12
DON'T edit this: /etc/default/grub.cfg. 

You want /etc/default/grub, but I wouldn't bother with that for the moment. If you're getting to a menu list and booting Ubuntu, grub is probably working fine.

As I say, only put it in the file if you know it is going to work. Makes no difference whatsoever whether it is there or on the end of the kernel line. One's to test, the other's to make it permanent if it works. ;)

---

### Post by mastablasta on 2014-02-13
> **Bucky Ball said:**
> As far as I know, though, nomodeset is for Nvidia cards and you're running AMD. :-k



nope, my AMD radeon HD 3650 needs it.

> **Snube said:**
> Bucky Ball, I tried to add the 'nomodeset' after quiet splash to recovery kernel, but it won't let me edit the /etc/default/grub.cfg because it's write-protected. 

I installed ubuntu from USB-stick, and at first, i had trouble installing, but with 'nomodeset' it let me install it normally. And my Windows 8 works normally, and fastboot, secureboot etc are switched off, when I try to boot Ubuntu.

you need to get into recovery mode (basic VGA) and then install proprietary graphics drivers. just like in windows... :-)

also make sure you are using latest 12.04.4 though i would suggest you try 13.10 or maybe even 14.04 to get improved support fo rthat newish chip.

via graphical interface (GUI): [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)
if you really can't get basic VGA mode to get the GUI then via command line (CLI)...: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

this should solve your issue.

when you boot and use nomodeset it is a temporary measure active only for that boot so if oyu can get in normally with nomodeset then you can change it permanently by editing the mentioned file. 

to edit in terminal you need to use ```
sudo nano
``` before the file name. sudo give you temporary admin privilege, while nano is CLI editor.
to edit in GUI you need to run gedit as root or run it using ```
gksu gedit

```

don't bother with editing the file if using the temporary boot option doesn't work.

---

### Post by Snube on 2014-02-13
I will try 14.04 now, but i'm kinda close on giving up on this, can't really make anything work on this crap laptop .__.

Edit: So now i made an bootable USB stick with 14.04, and i made it to "Try without installing" the first time without any "nomodesets" etc, I feel i'm getting somewhere here!

Edit2: Got 14.04 installed without any problems, finally! Thank you all for helping! :)

---

### Post by Bucky Ball on 2014-02-13
Good luck with it. All future support requests should be posted in the [Ubuntu+1]("http://ubuntuforums.org/forumdisplay.php?f=427") section of the forum, nowhere else, until it is released in April. It is an area to discuss, report, and try and figure out any problems that arise, so you might get help, you might not. Update daily as fixes (and some breakages) are constant are constant at this point. Be aware that there may be times when the OS will become very unstable and possibly break. Just post because everyone will be going through the same and a fix will be forthcoming.

The course is set, a path is laid, so enjoy the OS, the forums and the learning curve. ;)

(The best news is that as 14.04 LTS is a long-term support release it will be supported for five years and develop into a rock solid release perfect for work, production, everyday environments where stability is required (exactly as 12.04 LTS is now).)

---

### Post by oscar17 on 2014-02-26
Can I get some help here. I ve got the same crappy PC, just in my case it was not uploaded with Win 8 but with some Linpus without GUI. I tried to install Ubuntu from live usb but only shows some dots loading with the ubuntu logo and then white screens appears. Thanks.

---

### Post by mörgæs on 2014-02-26
It's hard to help you if you don't provide enough information. First of all, which versions of Buntu have you tried?

---

### Post by IvoGuerreiro on 2014-02-26
I have a packard bell EasyNote with windows 7 with a  AMD Radeon HD 8240 graphics card, its a cheap Laptop :p.
And i installed Ubuntu 13.10 without problems](*,), it was very simple really:-\". 
But before attempting to install i read everything i could find, it took me about 2 weeks  :-k  :shock:. 


Just to give a good feedback between ubuntu and packhard bell laptops hardware.\\:D/

---

### Post by bc.haynes on 2014-02-26
**@ oscar17**; **Snube** (the OP -Original Poster) had the same problem (white screen), and I believe the comments in this thread helped him solve it.

---

