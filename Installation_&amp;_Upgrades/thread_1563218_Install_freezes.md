---
title: "Install freezes"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by curambar on 2010-08-28
Well, it's a weird problem.
I had an old desktop pc, and I downloaded and burned both Karmic and Lucid desktop and alternate ISOs. I installed the karmic alternate in that PC, and things went smoothly.

Now a friend of mine gave me his old Packard Bell Easynote R laptop. It has a centrino 1.6GHz mother, 1GB RAM and a 60GB disk. The GPU (Geforce Go 6200) overheats a lot, but I have lurked around and found out this is a common issue.
Well, so I installed Win XP, and recently I wanted to install xubuntu here as well.
Thing is, the desktop install freezes. It does nothing, I can't even use the Live CD.
The alternate install goes well until the proper install, and then starts complaining about missing files in the CD.

Two things: The CD is perfect, I just tried it on my other desptop PC and it goes well.
The laptop cd tray is well too, I install things all the time, and I tried to install a game after this happened, to try and see if it was this, but it appears to work just fine.

I don't know what could be causing this. And I don't know enough to change things at the install prompt (noacpi, thing like that, I don't know what they mean).

Has anyone experienced something like this? If so, is there a solution? I believe this laptop cannot boot from flash drive, in the  boot menu I only have HD, CD-DVD, Floppy and LAN.

Another thing: If is a CD issue, is there a way to install this from LAN? (that is, using my other working PC to do this?)

Well, I tried to put in here as much info as I can remember :p.
Thanks in advance.

---

### Post by curambar on 2010-08-28
Update:
I made an ISO from the Xubuntu 9.10 Desktop, and checked the MD5 sum, and it's correct. So I can disregard a bad ISO.

---

### Post by curambar on 2010-08-29
and yet another update:
I found a workaround to boot from a flash drive (PLoP Boot Manager, basically a bootable cd that access the flash drive), and it won't install whatsoever. HD led is idle, pendrive led also idle, so nothing is happening.

So far, i have this:
*) It's not the ISO, I've checked the md5 for all of them and they are all fine.
*) It's not the cd unit, the pendrive install also failed.

Could this be related to the Nvidia card?

Please, someone?

---

### Post by mörgæs on 2010-08-29
Can you boot a 8.04 live CD? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by curambar on 2010-08-29
lemme download it and I'll try. I have a slow connection, so it will be a few hours :P

---

### Post by curambar on 2010-08-29
Well, it was a failure as well.
I tired to use 8.04 Live CD, and when the progress bar filled up, I was presented with 20 minutes of solid color full screens, flickering through a lot of different colors.
So, I'm guessing is the video card.

Is there some way to deactivate it at the install?

---

### Post by mörgæs on 2010-08-30
Since your machine has only one video card, it can not be deactivated. 

Maybe you should try to feed it some other Linux distro like Puppy, Knoppix or Slitaz.

---

