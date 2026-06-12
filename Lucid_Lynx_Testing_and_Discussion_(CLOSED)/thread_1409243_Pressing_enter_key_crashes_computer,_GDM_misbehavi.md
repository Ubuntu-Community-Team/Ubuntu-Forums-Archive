---
title: "Pressing enter key crashes computer, GDM misbehaving"
date: 2010-02-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2010-02-17
This only happens on one of my two computers. If I press the enter key on my keyboard, the OS crashes. Second, for some reason at random times, gdm decides to make me logout. Also two packages that are related to each other are crashing. I don't recall what I did that made them crash but I can't mount my windows partitions.

*Edit*

I can use the enter key now. Weird.

---

### Post by cecilpierce on 2010-02-17
> **Jordanwb said:**
> This only happens on one of my two computers. If I press the enter key on my keyboard, the OS crashes. Second, for some reason at random times, gdm decides to make me logout. Also two packages that are related to each other are crashing. I don't recall what I did that made them crash but I can't mount my windows partitions.

*Edit*

I can use the enter key now. Weird.

My enter key locks up to, what fixed it? If I hit enter to go to the next line it will lock up, and I just noticed my scroll lock is going on and off...hmmmmm!

---

### Post by Jordanwb on 2010-02-17
> **cecilpierce said:**
> My enter key locks up to, what fixed it?

Dunno. I had opened a terminal to edit fstab via "sudo nano -w /etc/fstab", typed my password, hit enter and xorg crashed. I think it is xorg that's crashing because I can use System Rescue to force an emergency reboot. Also sound still works when Ubuntu has crashed.

Also apport won't work. I try to report a bug with mtpfs and apport crashes. The crash reporter crashed.

I had locked my screen while I was AFK, GDM forced a logout.

Regarding the unmountable drives, I got a message about two obsoleted packages. However GDM forced a logout, so I couldn't see what the packages were that were obsoleted.

---

### Post by philinux on 2010-02-17
> **Jordanwb said:**
> Dunno. I had opened a terminal to edit fstab via "sudo nano -w /etc/fstab", typed my password, hit enter and xorg crashed. I think it is xorg that's crashing because I can use System Rescue to force an emergency reboot. Also sound still works when Ubuntu has crashed.

Also apport won't work. I try to report a bug with mtpfs and apport crashes. The crash reporter crashed.

I had locked my screen while I was AFK, GDM forced a logout.

Regarding the unmountable drives, I got a message about two obsoleted packages. However GDM forced a logout, so I couldn't see what the packages were that were obsoleted.

Testing environment. ;) Hope you reported the bugs.

I would suggest a download of the daily build and a reinstall at this point.

---

### Post by zika on 2010-02-17
Try removing (purge) plymouth and using non-KMS, i.e. nomodeset in kernel line in GRUB.

---

### Post by Jordanwb on 2010-02-17
*Starts Synaptic*, *begins to enter password*, forced logout. Damnit. Now my KVM switch is acti *forced logout*. Damnit. I think my keyboard is malfunctioning.

---

### Post by donniezazen on 2010-02-17
> **Jordanwb said:**
> This only happens on one of my two computers. If I press the enter key on my keyboard, the OS crashes. Second, for some reason at random times, gdm decides to make me logout. Also two packages that are related to each other are crashing. I don't recall what I did that made them crash but I can't mount my windows partitions.

*Edit*

I can use the enter key now. Weird.

sudo apt-get purge plymouth 

Use this command in recovery mode as you are not able to press enter key and your synaptic is crashing.

---

### Post by Jordanwb on 2010-02-19
I bought a new keyboard yesterday and Ubuntu is running fine. MY KVM switch is being too intelligent for its own good however.

---

