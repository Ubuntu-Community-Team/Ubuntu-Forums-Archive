---
title: "Blank screen after install with USB"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Werdine101 on 2012-03-25
Hi!
I hope anybody can help me with this.
I just installed Ubuntu via a USB stick, I can't use the optical drive,  and everything went well enough until I rebooted at the end of the  installation. I just get a blank screen. It starts out with a purpleish screen that then reverts to black, then nothing happens.
I did a fresh install with no other OS on the HD (the HD has been formatted) on an HP PC.
Any thoughts?
Thanx!
Carl

---

### Post by s0b3 on 2012-03-25
This happened to me too just now. After installing xubuntu 11.1 Alternate installer, via an 8gb flash drive, it just goes to a cursor upon finishing the installation. It only goes to GRUB when I put the usb stick back in. I opted to have full drive encryption with lvm install to a single partition on my 160gb hdd.

---

### Post by mörgæs on 2012-03-25
Both: Please give a complete hardware description, especially of the graphics card.

Werdine101: Which release are you trying to install?

---

### Post by s0b3 on 2012-03-25
How lazy of me, apologies.

Acer Aspire D150


[LIST]
[*] **Processor**  Intel Atom N270
[*] **Cache**  L2 cache - 512.0 KB
[*] **Front Side Bus**  533.0 MHz
[*] **Chipset**  Mobile Intel 945GSE Express
[*] **Graphics Processor**  Intel GMA 950
[*] **Memory Allocation Technology**  Dynamic Video Memory Technology 3.0
[/LIST]
Borrowed this text from [www.review.cnet.com]("http://www.review.cnet.com")


Ok so I decided to re-do the installation and I realize I installed both boot loaders Lilo and GRUB, no wonder it didn't boot. Noob mistake, sorry to waste your time [[COLOR=#d40000]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075"). Hopefully another noob may find it helpful.

---

### Post by s0b3 on 2012-03-25
Wait, it worked once and now it doesn't again, so now I have no idea what I did wrong... GRUB only shows up when I have the flash drive inserted, otherwise it just stays on a blank console to which you can type nothing.

---

### Post by mörgæs on 2012-03-26
You might need to set boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Werdine101 on 2012-03-26
Hi, thanks for the responses.

I tried to install the latest release on a HP ProBook 4530s.
I have a feeling it has something to do with the graphics card. I managed to install the 64 bit version as the 32 bit simply wouldn't load after installing, but even though the 64 bit version was installed and did boot, it kept giving problems. Also when I closed to lid to let the updates download and opened it later, the screen was all messed up and I had to reboot. Also rebooting was hit and miss, sometimes it would actually reboot, most of the time the screen went blank (no cursor).
Since I had not much time in setting the PC up I had to abandon this project. The PC was simply needed pronto so I had to install some bloatware.
So as far as I am concerned this thread is over, but maybe others with a similar problem would like to keep it open.
Thanks none the less!

Carl

---

### Post by mörgæs on 2012-03-26
> **Werdine101 said:**
> Also when I closed to lid to let the updates download and opened it later

In case someone else is reading the thread: While installing you should eliminate all sources of error, for example putting the computer to sleep-mode by closing the lid. The updates you are downloading could be related to a bug in the sleep/wake up proces!

It sounds like you were close to getting Buntu running. Write again if you want to give it a try later.

---

### Post by Werdine101 on 2012-03-27
Well I did manage to do the whole thing over again after the first update didn't work out, and didn't close the lid so I could monitor the process this time, but I simply still had troubles after that when rebooting. Sometimes it worked, sometimes it went right to a blank screen. 
In my case, I just had to stop experimenting as time ran out. 
I don't think if I will try it on my own PC any time soon as the software I need to use doesn't run on Ubuntu and I don't feel like experimenting with WINE as I haven't the time to tweak until things work, I need things to work out of the box really so I have to stick with Win7 for now. Maybe when I have another PC I can do some experimenting on before I need to use it I will try again.
So anybody else who has the same problems can use this thread but I have nothing new to report. I will check in now and again and if there is no activity I will close the thread.
Thanks for the help!

---

