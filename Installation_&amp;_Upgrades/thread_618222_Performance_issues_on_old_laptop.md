---
title: "Performance issues on old laptop"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by vandergus on 2007-11-20
I  just installed Xubuntu (7.10) on an old laptop to try to squeeze some more life out of it but the performance is excruciatingly slow. 

Specs

600 MHz processor
196 MB SDRAM
6 GB HDD

To start, the installation took several hours to copy the files from CD to HDD. Once installed, it takes minutes just to open a simple file browser window. 

When I opened System Monitor to try to identify the problem it showed my CPU was consistently at 60% usage, even when idle. Under the processes tab, it showed that the System monitor itself was using all of that CPU. My RAM sat around 50% to 60% with about 3 windows open so I don't think that's the problem. Could this be caused by an old HDD that's about to go? I've considered replacing it with a CF card (using the Addonics adapter) but would like to know if it will fix the problem first.

Any feedback is welcome. Thanks.

---

### Post by Daveski on 2007-11-20
I have Xubuntu on a PII 233 with 256Mb RAM and although it is not fast, it is certainly usable. I strongly recommend getting more memory, or trying to trim what is being used on that machine.

Things to try:

System -> Administration -> Services.

Remove things here you KNOW you will not require, eg, BlueTooth, or CUPS if you are not likely to be printing.

Edit your /etc/fstab file to include *noatime* for your drives - this stops Linux from tracking the last accessed time on files on this volume. This will speed up disk access:

```
/dev/hda1   /    ext3    defaults,errors=remount-ro,noatime 0    1
```

Anyone got other simple tips?

---

### Post by vandergus on 2007-11-20
My memory is maxed out on the laptop but I'll try the other tips you mentioned.

---

### Post by Daveski on 2007-11-20
Well if you suspect the drive (what file system is it by the way?) then here is a simple command to check read speeds:

```
sudo hdparm -T -t /dev/hda1
```

---

### Post by vandergus on 2007-11-20
results from hdparm

Timing cached reads: 16.10 MB/sec
Timinf buffered disk reads: 5.00 MB/sec

Seems slow, but not the type of slow enough to cause the types of problems I'm seeing.

I went to shut down some services but there was nothing listed in the services window when I opened it up.

I made the changes to fstab but didn't notice a change in speed.

Thanks for the suggestions.

---

### Post by mellowd on 2007-11-20
Although it would run I would run something a bit lighter on it. Maybe xubuntu or fluxbuntu?

---

### Post by vandergus on 2007-11-21
I'm currently running xubuntu. Not familiar with fluxbuntuu though. Runs a different windows manager, I presume. Or does it do a little more to lighten the load on the computer.

---

### Post by Sef on 2007-11-21
> I'm currently running xubuntu. Not familiar with fluxbuntuu though. Runs a different windows manager, I presume. Or does it do a little more to lighten the load on the computer.

With 196 mb ram, your computer should run ok.  Fluxbox is a really lightweight desktop manager.  It should run faster, but you should read up on it before installing.

---

### Post by vandergus on 2007-11-21
> **Sef said:**
> With 196 mb ram, your computer should run ok.  

That's what I thought when I installed xubuntu. I had read in some other threads that people were able to get xubuntu running on laptops with similar specs at reasonable speeds. I'm not sure why mine won't cooperate. Is there anything that would cause such huge lag in application launching? Is there anything that could be hogging my processor without my knowing it? I already tried looking at the system monitor but the only process it showed using any processor was the system monitor itself (~50%!). :confused:

---

### Post by vandergus on 2007-11-22
After some  more digging on the forums I found that others have seen similar issues with 7.10 on laptops. The general thought is that 7.10 just doesn't detect the hardware properly on some systems. I'll try installing Xubuntu 7.04 and see if that fixes things. I also wanted to try to install fluxbuntu 7.04 but could only find 7.10 around the internet. Anyone know where I could get a copy of 7.04. I realize I could just load the Fluxbox WM but there website said there was a little more optimization involved in the distro than just the windows manager. 

I'll let you know what I find.

---

### Post by Daveski on 2007-11-22
Ah ha, yes my Compaq Armada (specs in my first post) is indeed running Xubuntu 7.04 and as I said is not speedy but certainly usable. Please do post back your findings.

---

### Post by kerry_s on 2007-11-22
try straight debian xfce4, debian works better on the older stuff->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

the best thing to do would be a custom install using a debian base install and only installing what you need.
i use the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

for example:
uncheck everything in the package section for a base install
log in as root
apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
login as your regular user
open synaptic and keep adding what ever else you want

for example:
pcmanfm= filemanager
leafpad= editor
iceweasel= aka:firefox web browser
pidgin= instant messenger

you might want to go even lighter, that's up to you, it's really easy to build it to your needs.

---

### Post by vandergus on 2007-11-24
I installed Xubuntu 7.04 and all of the issues went away. The boot times are really fast and application launch times are normal but not speedy. One thing that might have contributed t o the slow down...

I ran hdparm again to check the hard drive speed and it had greatly increased. The Timing cached reads went from 16 MB/sec to 120 MB/sec. I think this is because ubuntu wasn't properly recognizing the hard drive earlier. In 7.10, the main hard drive was listed in the fstab as "sda1" and the swap was "sda5". I think this means that it was recognizing it as a SCSI drive (confirmation please). In 7.04, it is listed as "hda1" as it should be for an IDE drive. No idea what the fix is for something like this but I'm fine just staying with 7.04 for now. I may try out some other distros (if I can find them in 7.04) to find out which runs best on my computer though.

Thanks for the help all.

---

### Post by Daveski on 2007-11-24
That is interesting indeed. I will try out the Gutsy LiveCD on my Armada and see if I have a similar problem with the drive speeds.

<edit>
Compaq Armada E500:

7.04 (Live)  -  device is /dev/hda2 with an average speed of 100 / 12.6 Mb/s
7.10 (Live)  -  device is /dev/sda2 with an average speed of 100 / 12.8 Mb/s

So the drive speed is the same on this machine, but does indeed show as sda with Gutsy. The only difference I experienced was that the initial audio was choppy on Gusty during login.

</edit>

---

### Post by Pumalite on 2007-11-24
Xubuntu 7.04 is overall lighter than Xubuntu 7.10

---

### Post by vandergus on 2007-11-26
Just for the record, I've been using a Toshiba Satellite 2250XCDS for all of these installs.

---

### Post by vandergus on 2007-11-28
I've installed Enlightenment (e17) in Xubuntu and I quite like it. It's a bit faster than Xfce and much more configurable allowing me to make the most of my measly 800X600 screen. I must say that the largest restriction of the old hardware isn't the memory or the processor but the screen resolution. A lot of websites won't fit on a 800X600 screen so there can be a lot of scrolling.

Anyway... My next question was how much advatage there is in doing a clean install of Geubuntu (enlightenment+ubuntu distro) as opposed to keeping Xubuntu with e17 installed as the window manager. Would there be a big difference in speed? Would I lose some of the administative GUI's (it's nice not to have to do everything in the command line)?

---

