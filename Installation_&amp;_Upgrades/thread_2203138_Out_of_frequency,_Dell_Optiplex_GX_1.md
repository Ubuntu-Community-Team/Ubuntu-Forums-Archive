---
title: "Out of frequency, Dell Optiplex GX 1"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by louiuiui on 2014-02-01
Hi all,

I've been trying to get Lubuntu 13.10 to work for a few days now. I completely installed Lubuntu from a CD onto my hard drive, rebooted and then my monitor went blank "out of frequency". I managed to navigate/see the recovery options by pressing **down** and **Enter** but not sure what to do from there?

At one point the Lubuntu blue screen loaded with 4 white dots under it but it just stayed like that?

I'm using an old Dell GX1 PC. 

Thanks for any help

---

### Post by Erik1984 on 2014-02-02
Maybe you could try to change the resolution of the boot loader screen (instructions there): [http://askubuntu.com/a/153046/212082](http://askubuntu.com/a/153046/212082)

---

### Post by sudodus on 2014-02-03
You can also try some boot option, start with ***nomodeset***, but try also some other options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

-o-

But I found these specs via the internet:

> Dell Optiplex GX1. 
Computer Specs:
350 MHZ Pentium II Processor
64 MB RAM
6 GB Hard drive


If they are correct for your computer, you cannot expect to run Lubuntu. Maybe you can enjoy trying DSL, Tiny Core or Puppy Linux. See this link[URL="http://ubuntuforums.org/showthread.php?t=2130640"]

Old hardware brought back to life[/URL]

---

### Post by louiuiui on 2014-02-03
> **sudodus said:**
> 

But I found these specs via the internet:



If they are correct for your computer, you cannot expect to run Lubuntu. Maybe you can enjoy trying DSL, Tiny Core or Puppy Linux. See this link[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
[/URL]
My comp has Pentium 3 and was running **Windows XP** fine so assumed Lubuntu would be even smoother.

---

### Post by sudodus on 2014-02-03
I see, obviously there are early and late GX1, and yours is more powerful with a P3 CPU. As you saw in the link (in post #2), you need 512 MB RAM to get reasonable performance, but it is *possible* to run Lubuntu with 256 MB too.

Anyway, try according to *Euroman*'s link and try ***boot options***.

If you still have problems, I recommend a system based on Ubuntu 12.04 LTS instead of 13.10. But don't use standard Ubuntu with Unity. It needs too much horsepower and memory. The graphics drivers of version 12.04 LTS might cooperate better with your old graphics card.

If you want some more (or other) bells and whistles compared to Lubuntu,  you can try Xubuntu or some other flavour, re-spin or distro based on  the Ubuntu engine but a different desktop environment (different look,  different set of programs).

Lubuntu has the ultra-light desktop environment LXDE. The only current version is 13.10.
Xubuntu has the light desktop environment XFCE, and there is a long time  support version until April 2015, Xubuntu 12.04 LTS, not only 13.10.
LXLE has the ultra-light desktop environment LXDE. The current version is 12.04 LTS with support until April 2017.
Bento and Bodhi are other re-spins slightly farther away but still based on Ubuntu 12.04 LTS with support until April 2017.
Precise Gnome Classic Tweaks is 'Ubuntu tweaked', so that it is using a basic gnome desktop instead of Unity.

I can recommend all these for old computers, and it is a matter of taste, which one of them you prefer.

---

### Post by louiuiui on 2014-02-03
OK I start the computer, then it says **out of range**, I then wait a moment and press DOWN followed by ENTER, this brings up the **recovery options**, from there I'm lost as I can't see anywhere to put the NOMODESET command? On the recovery menu I've tried E - F6 - F2 - but no other menus appear.

---

### Post by sudodus on 2014-02-03
When you have installed the system, boot, and when you are at the grub menu, press 'e' to be able to edit the boot options.

If there is no grub menu, press the left ***shift key*** (shift from lower case to upper case) at once when you boot or reboot.


You enter the options at the end of the line starting with linux. Usually there are some boot options, for example quiet splash. Add ***nomodeset*** (as an own word separated with space from those boot options before it. After editing you press ***ctrl + x*** to start linux using the boot option.

---

### Post by mörgæs on 2014-02-03
Sorry to be blunt, but I would send it to recycling. 
Just for fun I once installed [Lubuntu on a GX 150]("http://ubuntuforums.org/showthread.php?t=361236&page=83&p=12292664&viewfull=1#post12292664"). It needed Vesa drivers, and it's likely that the GX1 needs that too.

---

### Post by louiuiui on 2014-02-03
> **sudodus said:**
> When you have installed the system, boot, and when you are at the grub menu, press 'e' to be able to edit the boot options.

If there is no grub menu, press the left ***shift key*** (shift from lower case to upper case) at once when you boot or reboot.

OK bare in mind I'm doing this with a blank screen - I turn the computer on and the Dell Bios/logo shows for a few seconds before a blank screen stating "out of range". At what point would I need to press **E** or **Shift - E**?

---

### Post by tgalati4 on 2014-02-03
I have a GX1 with 768MB (maximum supported).  I'm currently running Mint4 which is quite old but I plan to upgrade to something newer.  The graphics are on the weak side, so keep the resolution low (like 800x600) at first.  Try Linux Mint Mate 14 32-bit and see if that loads.

---

### Post by sudodus on 2014-02-04
Maybe you can enjoy trying DSL, Tiny Core or Puppy Linux. See this link[URL="http://ubuntuforums.org/showthread.php?t=2130640"]

Old hardware brought back to life[/URL]

I think Lubuntu (the current version) will be very hard if not impossible to run in this computer. Try some linux distros that is based on older kernels. DSL, Damn Small Linux, is a good candidate, with much better chances to succeed.

---

### Post by louiuiui on 2014-02-04
> **sudodus said:**
> 
I think Lubuntu (the current version) will be very hard if not impossible to run in this computer.

Thanks for your help mate, it runs full Windows XP, Photoshop, and MS Office easily. Surely lightweight-Lubuntu should be a breeze :confused:

**How/when  can I get to a grub menu** without seeing the screen?

---

### Post by sudodus on 2014-02-04
The problem is not only the 'weight', but also compatibility with old hardware. Along the road to new versions of Ubuntu, some hardware is left behind, so the drivers in the current Lubuntu version are not the best for really old hardware.

If you want a linux distro with more muscles than DSL, and still is very good at recognizing old hardware, try ***Knoppix***.

You might also have better results with a flavour, re-spin or distro based on Ubuntu 12.04 LTS (compared to the current Lubuntu version (13.10). See this link

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552)

---

### Post by sudodus on 2014-02-04
> **louiuiui said:**
> Thanks for your help mate, it runs full Windows XP, Photoshop, and MS Office easily. Surely lightweight-Lubuntu should be a breeze :confused:

**How/when  can I get to a grub menu** without seeing the screen?

Press the left SHIFT key right after boot or reboot.

---

