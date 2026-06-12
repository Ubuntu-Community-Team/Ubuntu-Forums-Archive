---
title: "Dualing with Vista"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Justin125 on 2008-03-14
I've been looking around for guides/how-to's on the partitioning part of dual-booting with Vista and I'm kinda confused if I should be doing the partition stuff in Vista or in Ubuntu's installer.

I've installed ubuntu (feisty, I think) before, but it was a test PC for it more than anything and it was XP, I used some auto thing for the partition part I think. I want to install it as a dual-boot on my primary PC with Vista this time, and therefore it's a bit more important to me that I don't mess up the partition part. Other then the partition stuff I'm fine.

---

### Post by Pumalite on 2008-03-14
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Justin125 on 2008-03-14
By looking at the bottom link, this is pretty n00b-y but: The amount I shrink in Vista is the amount of space I'm giving to Ubuntu?

---

### Post by froy02 on 2008-03-14
What you shrink is the amount for vista not the linux installation.   So if you 200gb and shrink it down to 150 gb, then your linux will have 50 gb.

---

### Post by Justin125 on 2008-03-14
Just making sure I get this:

I have a 200GB HDD and I shrink the Vista partition to 140GB; I install Ubuntu and manually do the partitions and make a SWAP partition of 2GB(i've heard SWAP should be 2 times my RAM; which is 1GB) and make it a primary. Next, I make a new ext3 partition off the free space and make it 58GB.

That would give me a 58GB Ubuntu installation, correct?

---

### Post by Pumalite on 2008-03-14
In Vista you MUST partition with Vista partitioner to allocate space for Ubuntu. You cannot partition with Ubuntu partitioner. And you can pretty much control exactly how much you want to give to Ubuntu.

---

### Post by Justin125 on 2008-03-14
The resizing to 140GB needs to be done in VISTA, but the SWAP and Ubuntu 58GB ext3 is to be done in the Ubuntu installer?

Or do I actually make the Ubuntu 58GB ext3 in vista?

---

### Post by Pumalite on 2008-03-14
After you partition in Vista, get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Grab that new space you have and make 3 new partitions:
10 GB for '/'
1 gb for /swap (in laptops /swap=RAM)
The rest for /home
Install Ubuntu, go Manual and use the partitions already prepared.

---

### Post by jflaker on 2008-03-14
I was a dual booter while contemplating going 100% linux.

During the install, you will be given the opportunity to choose to resize the current partition to accomodate Linux.  

Pay CLOSE attention to the prompts on the screen.....you will have the option of wiping the whole drive (DO NOT DO THAT!!!!!!!!) or resizing it.

Patients and it works flawlessly.

---

### Post by Justin125 on 2008-03-14
And now I'm not sure which method to do. I think I'm going to try the g-parted way, the 10GB for the '/' isn't like saying 'giving ubuntu 10GB', that's something else right?

jflaker, is that using the auto thing where you use a % drag bar?

---

### Post by Pumalite on 2008-03-15
Those 10 GB for '/' are for the filesystem; for 'root'

---

