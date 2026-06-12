---
title: "No video after boot menu"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by ajfunk on 2007-07-19
hey guys im having trouble installing ubuntu ff 32bit on one of my desktops. heres the system specs:

athlon 64 4000+
2gb pc3200 ddr ram
HDD #1: 80GB IDE
HDD #2: 320GB IDE
Graphics: 2x NVIDIA GeForce 7600 GT 256mb PCI-e in SLI mode

The livecd boot menu appears, then once I click install/try out ubuntu, it begins to load everything then after that screen disappears it stays black. I've let it sit for a good hour and a half and the black screen does not dissipate. Any suggestions?

---

### Post by ddrichardson on 2007-07-19
Can you use <CTRL><ALT><F2> and get another TTY?

I've had this before with some nVidia graphics cards that start the X-Server but give a black screen.

---

### Post by ajfunk on 2007-07-20
i can get text up on screen, but im used to it just booting to the disc the way it does on my laptop. when i installed ubuntu on my laptop, all i had to do was pop in the disc and click the installer icon on the desktop. this rig on the other hand is not giving me that privilage. Is something not loading correctly?

---

### Post by ddrichardson on 2007-07-20
Yes the X-Org isn't loading the server in the correct mode. I dare say its to do with the SLI configuration (but don't quote me on that).

Some rooting around with the xorg.conf followed by a <CTRL><ALT><BACKSPACE> to restart the x server should prove it.

You could use a svga mode to install then configure the nVidia binary drivers afterwards.

---

### Post by ajfunk on 2007-07-20
hmm i think im gonna start by disabling sli, then investigate xorg.conf if no avail. standby.

---

### Post by ajfunk on 2007-07-20
bummer! it was the sli setup! im dual-booting with xp on this machine. if the ubuntu install goes well, will i be able to turn sli back on and still be able to get ubuntu to boot properly?

---

### Post by ddrichardson on 2007-07-20
Apparently the new nVidia drivers (restricted) support SLI.

---

### Post by ajfunk on 2007-07-20
any chance you can tell me how to install them? ^_^

---

### Post by ddrichardson on 2007-07-20
There's a thread on this already:

[http://ubuntuforums.org/showthread.php?t=96199]("http://ubuntuforums.org/showthread.php?t=96199")

A huge article on it [here]("http://www.phoronix.com/scan.php?page=article&item=326&num=1").

Be aware however that only the closed source nVidia binary driver supports this. Make sure to backup your current working /etc/X11/xorg.conf first so you can revert to a working system from a virtual terminal if it all goes wrong.

From what I've seen [here,]("http://www.linuxquestions.org/questions/showthread.php?t=499317") apparently its quite straight forward (famous last words).

The driver is at [nVidia's site]("http://www.nvidia.com/object/unix.html"). You need to chmod +x before running the script as its not executable by default. You will also need the linux-source package for it to compile.

Best of luck.

---

### Post by ajfunk on 2007-07-20
got the nvidia drivers installed after much frustration; couldnt get sli to kick in though. now im suspecting the hdd that feisty is on is now going bad; rebooted once and its clicking periodicly =/

running DFT to determine. thanks for the help =)

---

### Post by ddrichardson on 2007-07-21
Yeah intermittant clicking is often a giveaway of a drive or controller failure. Some DFT's are better than others - Seagate's is excellent - right down to firmware problems.

You're right though, the nVidia installer is quite unhelpful and can be downright frustrating. Plus it frequently breaks when updates are applied. Still at least they support Linux which is to be commended really.

---

