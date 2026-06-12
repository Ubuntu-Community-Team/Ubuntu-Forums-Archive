---
title: "Install Help"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Mike.42 on 2008-05-25
I am trying to in stall ubuntu on a sony vaio laptop. After I select either the 'Install Ubuntu' or 'run live' option from the Live CD, a progress bar pops up, and after a while it goes away, then the screen is black with a underscore flashing in upper left.
Thanks,
-Mike

---

### Post by zaivala on 2008-05-25
> **Mike.42 said:**
> I am trying to in stall ubuntu on a sony vaio laptop. After I select either the 'Install Ubuntu' or 'run live' option from the Live CD, a progress bar pops up, and after a while it goes away, then the screen is black with a underscore flashing in upper left.
Thanks,
-Mike

Are you running Windows now?  Are you looking to replace Windows with Ubuntu, or dual-boot?  How much free space do you have on your hard drive?

Hugs,
Moss

---

### Post by zaivala on 2008-05-25
Also, if you're still running Windows and don't mind a dual-boot, try running Wubi.exe on the disc instead of Install.  This will install Ubuntu in a folder on your Windows drive and won't require any messy partitioning.

Moss

---

### Post by Mike.42 on 2008-05-25
I am not interested in duel booting windows Me. I was just going to reformat the drive during the install.

---

### Post by zaivala on 2008-05-25
> **Mike.42 said:**
> I am not interested in duel booting windows Me. I was jut going to reformat the drive during the install.

I think you need to reformat the drive BEFORE the install... your problem could be that it is running out of room on your hard drive during install.

I am a fairly knowledgeable Windows person, but NOT the most knowledgeable in Linux, although I've played with it some over a lot of years.  Ubuntu 8.04 is by far the best I've used, and it still is not user-friendly in a Windoze sense, but we're getting there.

Look forward to more knowledgeable responses.

Hugs,
Moss

PS - I don't blame you for wanting to lose ME... giggle

---

### Post by Mike.42 on 2008-05-25
I am havening an insanely hard time formatting my drive before the install. I am trying to format the HDD by using knoppix live cd. Every time i try to use the fdisk command "fdisk /dev/hda1" i get 'unable to open /dev/hda1'
What is the best way for me to reformat this hdd?

---

### Post by zaivala on 2008-05-25
> **Mike.42 said:**
> I am havening an insanely hard time formatting my drive before the install. I am trying to format the HDD by using knoppix live cd. Every time i try to use the fdisk command "fdisk /dev/hda1" i get 'unable to open /dev/hda1'
What is the best way for me to reformat this hdd?

Personally, I would just use GPartEd.  Of course, it helps that a friend of mine burned GPartEd to a bootable CD...

Hugs,
Moss

---

### Post by Mike.42 on 2008-05-25
GParted comes with knoppix so running was no problem. However, the partition i want to format is read only/ locked How can i unlock it?

---

### Post by Mike.42 on 2008-05-25
The HDD is now clean. However, i still get the flashing underscore in the upper left corner. My question is this, is there a way for me to install ubuntu while running knoppix?

---

### Post by zaivala on 2008-05-25
> **Mike.42 said:**
> GParted comes with knoppix so running was no problem. However, the partition i want to format is read only/ locked How can i unlock it?

I hate to say this, but you'll need someone more knowledgeable than I to answer that.  Hope someone chimes in soon.

Hugs,
Moss

---

### Post by Mike.42 on 2008-05-25
> **zaivala said:**
> I hate to say this, but you'll need someone more knowledgeable than I to answer that
Thanks so much for your help anyway, never would have thought to use gparted!

---

### Post by seekers on 2008-05-25
I was wondering why you don't let Ubuntu 8.04 wipe the drive for you.  You don't get the live cd?

---

### Post by Mike.42 on 2008-05-25
The live CD wont load. After selecting either to install or run live, there is the logo and the orange bar, then after that the screen goes black with a underscore flashing in the upper left corner.

---

### Post by seekers on 2008-06-01
Its posssible that your cd is currupted.  You can also download the alernate cd.  Try a lower speed when you burn it.

---

