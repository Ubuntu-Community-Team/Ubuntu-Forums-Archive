---
title: "Kernel : which one's best ??"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by troutrou on 2004-11-15
When I installed Ubuntu, it gave me the option to chose between for Kernel images:

1) Linux-image-386
2) linux-image-2.6.8.1-3-386
3) linux-image-2.6-386
4) linux-386

A friend of mine told me he obtained significant speed improvement of his desktop, when re-compiling his kernel (another distro), to suit his machine.

So I would rather have kernel optimised for my processor !
Is the Ubuntu Kernel optimised for a particular processor, or is it a low performance one, compataible with old processors ?

All four kernels listed by Ubuntu show "386" in their name, does that mean they are compatible with this processor ? Does Ubuntu provide Kernels optimized for more modern processors ?

I have an AMD Athlon XP 1700+, what kernel should I use ?

Please help, I hate to think my Ubuntu could be faster and is not simply because it's compatible with ancient processors like the 386 ! :o(


Regards,

Vince

---

### Post by ubuntu-geek on 2004-11-15
Take a look at this number 8, that should help guide you in the right direction.

[http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

---

### Post by TravisNewman on 2004-11-15
[QUOTE=ubuntu-geek]Take a look at this number 8, that should help guide you in the right direction.

[http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)[/QUOTE]
 I think ubuntu-geek means number 9.

---

### Post by troutrou on 2004-11-15
Thanks boys,

It says there are two kernels for AMD processors, which one is best for my "old" Athlno XP 1700+ ??

1. sudo apt-get install linux-686 for newer Intel/AthlonXP
2. sudo apt-get install linux-k7 for any AMD Processors

ANd once I have downloaded it, how to install it ? How to tell Ubuntu to start the machine with new kernel, and omit the stock one ?

Questions, questions... ;o)

Vince

---

### Post by TravisNewman on 2004-11-15
[QUOTE=troutrou]Thanks boys,

It says there are two kernels for AMD processors, which one is best for my "old" Athlno XP 1700+ ??

1. sudo apt-get install linux-686 for newer Intel/AthlonXP
2. sudo apt-get install linux-k7 for any AMD Processors

ANd once I have downloaded it, how to install it ? How to tell Ubuntu to start the machine with new kernel, and omit the stock one ?

Questions, questions... ;o)

Vince[/QUOTE]
 Hmm... according to synaptic, the 686 is for the pentium series, and the k7 is for all the athlons. But ubuntu-geek may know something I don't.

apt-get will install the kernel and update your grub config so that you don't have to do anything, it'll boot into your new kernel next time you reboot.

---

### Post by troutrou on 2004-11-15
Okay, sounds like I have nothing particular to do get it working then, great :o)

If I am allowed one last question... why does it say in the HOWTO, to use teh "apt-get install" command in a terminal, I tohught Synaptic was a graphical user interface for the apt system ? Can't I use just Synpatic to downloas/install the K7 kernel ?

How do I know when I can use Synpatic, and when I must use apt-get "by hand" on the command line ? ... :-/

Vince

---

### Post by TravisNewman on 2004-11-15
You can pretty much always use Synaptic in the place of apt-get. Synaptic is the front-end to apt-get, and it makes installing software easier, but using apt-get is a bit faster when you get the hang of it, so a lot of people prefer it over synaptic.

---

### Post by jdong on 2004-11-15
[QUOTE=panickedthumb]Hmm... according to synaptic, the 686 is for the pentium series, and the k7 is for all the athlons. But ubuntu-geek may know something I don't.

apt-get will install the kernel and update your grub config so that you don't have to do anything, it'll boot into your new kernel next time you reboot.[/QUOTE]

i686 is Pentium Pro and up, and the entire AMD line.

Note that k7 actually denotes Athlon XP's and Durons with similar cores, and higher... Though people have used it successfully on Athlon's. If you have issues with 3d or anything kernel-related, this would be the first thing to suspect ;-)

---

### Post by troutrou on 2004-11-15
[QUOTE=jdong]i686 is Pentium Pro and up, and the entire AMD line.

Note that k7 actually denotes Athlon XP's and Durons with similar cores, and higher... Though people have used it successfully on Athlon's. If you have issues with 3d or anything kernel-related, this would be the first thing to suspect ;-)[/QUOTE]


Just finished to download the 18MB of the K7 kernel (don't have broadband so took a while... ) ! Really dead easy, nothing to do. I just restarted the machine, and GRUB now gives me the choice between the Ubuntu 386 kernel and the K7 kernel it just installed, couldn't be easier :-)

Well, I am aware of "Placebo effet", however I do find it a bit quicker ! 
I used my usual test : starting OpenOffice ! Normally takes several minutes ;o) so every improvement is easiliy noticeable. When I switched from Mandrake 9.2 to 10.1C, it was faster, then when I installed Ubuntu 386 it was again faster, and now, with the K7 Kernel it's again a little bit faster ! :o)
Maybe I should try the 686 kernel as you suggest ? :-)
I guess I have nothing to lose, as it only adds an extra entry in GRUB and I am always free to chose whatever Kernel I prefer at boot time ! :o)

I loooove Linux :o)

Thanks for your help on this one boys, now on to start a new thread about my internal IDE ZIP drive that Ubuntu doesn't want to see/detect/mount whatever ! :o(((

Vince

---

