---
title: "All Ubuntu builds fail on installation"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by XtrmJosh on 2013-07-07
I'm encountering an issue very similar to that described here:[URL="http://ubuntuforums.org/showthread.php?t=2128715"]

http://ubuntuforums.org/showthread.php?t=2128715[/URL]

The key difference being my computer is high-end and I can't comprehend the answers because I'm too new to GUI based Linux. I've worked with Ubuntu via Putty on Windows, and I got on just fine, but getting the GUI working is proving a nightmare.

Tried installing Xubuntu, as that was my preferred GUI, and it failed saying that the installation was corrupt. I tried 10~ times, checking (and twice re-downloading) the file. It runs just fine from the live USB, and appears to install fine, but after reboot it fails giving me that whole installation error. (Can't remember the exact words, can't screenshot it, it appears and quickly disappears, and I am no longer interested in the GUI, don't mind having general Ubuntu GUI).

I assume specs are important, so here goes:

AMD 8350 Black Edition, 8 core 4.2GHz CPU.
ASUS M5A92 R2.0 Motherboard.
2x 4GB Kingston 1330MHz RAM. 99U5471-012 ADDLF.
2x 2GB Hyundai Electronics 1330MHz RAM. HMT125U6BFR8C-H9.
1x WD 320GB HDD (onto which I'm trying to install Linux).
1x SG 500GB HDD (on which I'm keeping my Windows installation).
1x cheap DVDRW, I guess it's unimportant since I'm booting from USB.
AMD Radeon HD 6450 GPU, 2GB RAM.

So I moved on to the general Ubuntu GUI, which is working fine until the login screen, as soon as that is loaded the screen goes funny colours and decides it won't allow me to use my keyboard, mouse, nor see what's happening. I tried booting to terminal, and it didn't work. Gave the same style of issue (first picture is terminal, second obviously GUI). I wouldn't really know what to type when I got to that stage anyway, since I don't work with GUIs, only terminal.

Any help appreciated.

Pictures, in case they give any leads:

[IMG]http://i.imgur.com/Boh1U2q.jpg[/IMG]
[IMG]http://i.imgur.com/PSuiAbc.jpg[/IMG]

Kind regards,
Josh

---

### Post by grahammechanical on 2013-07-07
At the Grub boot menu you should select recovery mode. You do not tell us what version of Ubuntu you are using. I am not refering to the flavours such as Xubunt, but to the release dates such as 12.04, 12.10, 13.04

If you are using 13.04 go to Advanced Opetions and select Recovery Mode and then select resume. See how far that gets you. You need to install a different video driver.

Regards

---

### Post by XtrmJosh on 2013-07-07
> **grahammechanical said:**
> At the Grub boot menu you should select recovery mode. You do not tell us what version of Ubuntu you are using. I am not refering to the flavours such as Xubunt, but to the release dates such as 12.04, 12.10, 13.04

If you are using 13.04 go to Advanced Opetions and select Recovery Mode and then select resume. See how far that gets you. You need to install a different video driver.

Regards

I'm running 12.04 LTS. I assume by the Grub boot menu you mean the bit where it offers to install, try, or check an installation? If so, the check runs fine and the install option doesn't fix the issue. If not, how do I access this?

Regarding 13.04, when you say "go to advanced options", I see no buttons or dialogs at all bar the login screen for a portion of a second on bootup, meaning it would be very difficult if not impossible for me to use any GUI orientated settings.

Thank you for your time,
Josh

---

### Post by Penguenci on 2013-07-07
Have you ever had trouble with your video card? The pattern on your screen is a very common symptom of a GPU in lousy shape. Could also be just the graphics driver, or total incompatibility of your GPU with Ubuntu. If you have absolutely no problem using above-par graphics on Windows, chances are you need a special driver, or your GPU and Ubuntu don't like each other.

---

### Post by XtrmJosh on 2013-07-08
> **Penguenci said:**
> Have you ever had trouble with your video card? The pattern on your screen is a very common symptom of a GPU in lousy shape. Could also be just the graphics driver, or total incompatibility of your GPU with Ubuntu. If you have absolutely no problem using above-par graphics on Windows, chances are you need a special driver, or your GPU and Ubuntu don't like each other.

I've never noticed any issues with it. It's by no means a high spec graphics card, the card itself is the least powerful part of my machine, but it does everything I need it to (WoW, GTA, few other 3D games) and it doesn't scream about it. The GPU isn't anything unusual, it uses the bog standard drivers on windows (AMD catalyst installs them), not sure what the driver is actually called though. I'm gonna try the Grub boot menu today if I get the time, really disappointing though, everyone had told me Ubuntu was becoming the new Windows. I promise you, I've never had any problem like this (or the others I've experienced when previously installing Ubuntu) using Windows :(. Ah well, chin up!

I suspect if I try an Intel graphics card this may "fix" the issue, does anyone share this suspicion?

---

### Post by Penguenci on 2013-07-12
If at all possible, you should try installing with another video card, Intel or not, and see where that leads you. Just so you know, my experience with Ubuntu (or rather Linux in general) has been such that Nvidia is less less likely to cause trouble than other video cards, and low end cards cause less trouble than high end ones.

There is also a little command line entry you should run on the terminal after installing Catalyst, have you done that? Failure to do that usually gives you a blank screen on boot rather than that weird pattern, so your problem is probably not that. But it's something to be considered anyway.

---

