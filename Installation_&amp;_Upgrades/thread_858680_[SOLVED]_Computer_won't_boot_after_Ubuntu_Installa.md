---
title: "[SOLVED] Computer won't boot after Ubuntu Installation"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by abrahmm on 2008-07-13
Hi,
A little background, I have been using this computer for some time with windows xp on it. I'm taking a linux programming class this next semester so I wanted to install linux on my computer without messing with my Windows.

Anyways, I bought a separate SATA hard drive and installed it on my computer. Windows booted up fine after it was installed. I put the Ubuntu live cd in, and installed Ubuntu onto the new hard drive.

Now when I start my computer, nothing happens. The BIOS will come up with system information, and then at the point where Windows used to start loading, the computer just sits there. I can load up the Ubuntu live cd with no problem. I tried "Load from first Hard disc" option and it just sat there, again nothing happened. I tried the Grub installation guide on this site by loading into Ubuntu from the "Try Ubuntu without changing anything" option, but after the grub re-installation nothing has changed. 

I'm really not sure what else to try and am looking for anything to help me out to avoid having to completely reformat with Windows XP.

Thanks in advance

---

### Post by randomnote1 on 2008-07-13
Boot up with your XP cd and repair the existing system.  You should be able to get Windows up and operational again.  From there it should be easier to diagnose why Ubuntu won't boot.

---

### Post by abrahmm on 2008-07-13
> **randomnote1 said:**
> Boot up with your XP cd and repair the existing system.  You should be able to get Windows up and operational again.  From there it should be easier to diagnose why Ubuntu won't boot.

I attempted to do this, but when I tried I was prompted to "Enter Administrator password". When I entered the only password I have ever used in Windows, it said it was wrong and I couldn't get pass that point.

---

### Post by oilchangeguy on 2008-07-13
> **abrahmm said:**
> I attempted to do this, but when I tried I was prompted to "Enter Administrator password". When I entered the only password I have ever used in Windows, it said it was wrong and I couldn't get pass that point.

just press enter, and it should go by the password prompt. then type fixmbr press enter. then type fixboot press enter. then type exit press enter.

---

### Post by abrahmm on 2008-07-13
> **oilchangeguy said:**
> just press enter, and it should go by the password prompt. then type fixmbr press enter. then type fixboot press enter. then type exit press enter.

Wow you are awesome! I did this thinking that this would just make windows boot automatically and bypass grub, but after doing these commands, Grub loaded up and I had the options to load up both Ubuntu and Windows XP! :) Thank you so much for the help!

Now I just have to figure out how to make Windows XP load when by default instead of Ubuntu, because at the moment if you don't touch anything in grub it automatically goes to Ubuntu.

Thanks a lot everyone, you guys are lifesavers, I was about to pull my hair out!

---

### Post by Rallg on 2008-07-13
Making Windows boot by default: In Ubuntu, you need to edit the file menu.lst located in /boot/grub. To do that, get a Terminal (Start Menu, Accesories, Terminal). Then:

gksudo gedit /boot/grub/menu.lst

(That's lst as in LST).

You will notice that your Windows system isn't the first choice. So, make it the first choice. You will also notice that your aren't given much time to choose. Lengthen that, if you wish.

Since you're taking a programming class, "proof left to student" :twisted:

---

### Post by abrahmm on 2008-07-14
Well Yesterday everything was working fine. When I would turn my computer on, Grub menu would pop up and I could choose whether to boot Windows xp or Ubuntu. Today I turned my computer on and got 

Grub Loading, please wait...
Grub Error 17

Thats it, won't load. Been googleing trying to find answers but they are hit and miss. Any help is appreciated. Thanks!

EDIT: Figured out the cause of the issue, this time I was starting my computer with my external hard drive plugged in, and Grub must have been picking this up and not liking it. Unplugged the HD and it booted up fine. /sigh

---

