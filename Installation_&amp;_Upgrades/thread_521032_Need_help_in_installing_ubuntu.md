---
title: "Need help in installing ubuntu"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by ajyrds on 2007-08-08
Hi,
I am installing a linux OS for the first time ever and am facing a lot of problems while trying to do this.

I have a laptop with the following config:
Intel core2 duo CPU T7300 @ 2.00GHz
2GB RAM
383MB NVIDIA GeForce 8400M GS video card
80GB 5400RPM SATA Hard Drive
Windows Vista home premium

I deleted the recovery partition which comes with the laptop and resized the drive where Vista was installed. The computer now looks like this:
B: 10gb
C: 38.6gb (Vista is installed on this drive)
D: 25.6gb

1. First I copied the .iso from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Options I selected:
Ubuntu 7.04 - Supported to 2008
Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) 

Then i burned the image onto a cd rom and restarted the laptop after inserting the disc into the ROM.
I reach the menu bar which gives various options to install, start ubuntu in safe graphics mode, etc.
I selected the The progress bar comes up and after that it stops at the prompt and says 
"/bin/sh: can't access tty; job control turned off
(initramfs)"

No matter what option i choose (except the check memory option), I come back to the same screen

2. When this did not work i tried to install ubuntu using wubi. It went on fine and i restarted the system when it asked me to. When i booted to ubuntu, some text messages came up and then the progress bar came up and then it stopped at this:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem."
<Yes> <No>
I clicked Yes and then some more messages came up. When i said ok, it finally stopped at:
"X server is now disabled. Restart when it is configured correctly."

Now I don't know what to do next. My guess is that there is a problem with the hardware not being recognized but i'm not sure.

Please help!
Thanks,
Ajay

---

### Post by Pumalite on 2007-08-08
Start from the basics: do md5sum on iso, burn at 4x, check CD for corruption before install. In any case,  you'd be better off with the Alternate CD to avoid graphical interface problems. So, get a new iso and do what I indicated. To get the Alternate, mark the box below the green sign that says: 'Start Download'.

---

### Post by merlinus on 2007-08-08
You might try this when the error msg appears:

Ctrl-Alt-F1 to get to prompt

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

-merlin

---

### Post by Pumalite on 2007-08-08
I'm sleepy, I think Merlinus is right.

---

### Post by ajyrds on 2007-08-09
Hi Merlin,
Your solution worked! Thanks a ton!
Ajay

---

### Post by ajyrds on 2007-08-09
I had one more question - i am now able to login to ubuntu and need to connect to the internet. But i can only see the wired connection and the modem connections in the network connection window. How do i bring up the wireless option? Also, i'm not able to login to the root user. I only created one account - that was for me - and it says i do not have administrative priviledges. How do i get them?
~Ajay

---

### Post by merlinus on 2007-08-09
For root privileges, preface terminal commands with sudo (or gksudo for graphical apps such as nautilus and gedit).

-merlin

---

### Post by MrObvious on 2007-08-09
Ahh wireless, how fun to set up. It would help to know which chipset you're running for wi-fi. Can you get the card details? I can't remember which command to use as I doubt lspci will work. lsmod maybe?

---

### Post by ajyrds on 2007-08-09
Merlin, thanks for helping again. I will try sudo after getting back home from work (i was trying su and it did not work).
MrObvious, i'll try to get the card details. 
~Ajay

---

### Post by MrObvious on 2007-08-09
Yeah Ubuntu uses sudo not su. Can you tell me which laptop you bought? If you post a website that should be enough for me to google the wi-fi card and then get a chipset and post a few steps or give us an idea of how to set it up.

---

### Post by ajyrds on 2007-08-09
MrObvious - I have a HP dv6500t laptop with the following config:
Intel core2 duo CPU T7300 @ 2.00GHz
2GB RAM
383MB NVIDIA GeForce 8400M GS video card
80GB 5400RPM SATA Hard Drive
Windows Vista home premium

---

### Post by ajyrds on 2007-08-09
I am facing multiple problems - Gurus please help:
1. I don't know how to get my wireless internet working
2. The sound card does not seem to work - i can't hear any sounds
3. The dvd drive also doesn't seem to be recognized. The /etc/fstab file does not show any cd/dvd info.
Can somebody please halp me?

~Ajay

---

### Post by mooseboy on 2007-08-14
I have this laptop and a few things I can contribute to this conversation:

1. There are two kinds of wireless chips that can go in here. Both are Intel variety. One is the 3945 ABG which does up to 802.11g. The other is the 4965 AGN which does up to 802.11n. The first one is much easier to support on feisty. The second requires a kernel upgrade to 2.6.22. A search for "dv6500t" on the forums will bring up old threads that explain how to do these.

2. You likely have the same sound issue as the rest of us dv6500t owners. It will work if you do a decent amount of tweaking and patching of the latest alsa revisions (all done by hand). There's a guide floating around the forums to do this, but if you're not an experienced linux user this will prove very difficult. 

3. The cdrom issue can be fixed by running "modprobe generic_ide" at runtime. You can make this fix permanent by adding it to the end of /etc/rc.local

---

### Post by ajyrds on 2007-08-15
Thanks mooseboy for replying!
1. I have 4965 AGN 
2. I am an inexperienced linux user :(
3. I'll try this solution out

---

