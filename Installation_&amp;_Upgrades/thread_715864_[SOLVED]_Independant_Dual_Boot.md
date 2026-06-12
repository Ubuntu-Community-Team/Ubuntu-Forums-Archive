---
title: "[SOLVED] Independant Dual Boot"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by scruffybeard on 2008-03-05
Hey there ladies and gents.

Here's what I'm trying to do. I'm trying to get my laptop to boot XP and Gutsy. While I am able to do a successful dual boot, I would like my XP partition to boot directly unless I insert my Super Grub Boot Disk.

I have been able to do this on my desktop by installing Grub onto a second hdd, but this is not a possibility on my laptop as it only has 1 hdd.

The options I have tried at installation are 1.) Installing grub to hd3 rather than hd0
                                                                    2.) Installing grub to hda3 rather than hd0
                                                                    3.) Simply not installing grub

Near as I can figure by my usage of Super Grub is that it scans for installed bootloaders, rather than being a bootloader in and of itself. This means that grub **HAS** to be installed somewhere, otherwise Super Grub gets confused and will not boot Linux.

Does anyone know where I could install grub so that it is not on the MBR, but is installed somewhere so that Super Grub can detect it?

This will be a new install of Ubuntu, so if there is a way to do it through the Ubuntu installer, that would be most awesome.

If I need to clarify things any, let me know. 

Thanks!

-Scruffy Beard

---

### Post by dstew on 2008-03-05
> Does anyone know where I could install grub so that it is not on the MBR, but is installed somewhere so that Super Grub can detect it?In your case you want to install the grub boot loader to the Ubuntu partition on your hard drive, rather than to the MBR of the hard drive.

If you have not installed yet, stop when you get to the grub install step and see if there is an Advanced button (I can't remember) Then, tell grub to install to the Ubuntu partition. You might need to know ahead of time the partition name. Since you only have one hard disk, it will probably be (hd0,1) or (hd0,2). I am pretty sure the Alternate Install CD lets you pick where to install grub. Bottom line is not to install to (hd0). That puts grub into the MBR.

Maybe safer is not to install grub at all during the installation. Then you can install grub from the grub command line on the supergrub disk at leisure, taking your time to make sure you have the correct partition. To install from the grub command line, get to the command line first (menu choice in supergrub). It should show the grub> prompt. Then, enter the command```
find /boot/grub/stage1
```That should give you the correct partition name in grub-language. Let's say it returns (hd0,1). Then, to set up grub in the partition, to boot later with the supegrub disk, enter these commands:```
root (hd0,1)
setup (hd0,1)
quit
```Then, try to boot (hd0,1) using the supergrub disk.

---

### Post by scruffybeard on 2008-03-05
Thank you so much. This is exactly what I was looking for.

I basically have been getting tired of booting my laptop at the airport, and having to explain what grub is, what Linux is, ect before I am allowed to board my flight.

I read something about this some time back about booting to an encrypted Debian system, but I'm not interested in the encryption as much as the hassle (and occasional missed flight:mad:).

Thanks again, as soon as I get a chance, I'll be testing this!

---

### Post by Kiri on 2008-03-05
Do airports in (I assume the US?) really make you boot up your laptop and show them what's on it before letting you board??

---

### Post by logos34 on 2008-03-05
> **scruffybeard said:**
> I basically have been getting tired of booting my laptop at the airport, and having to explain what grub is, what Linux is, ect before I am allowed to board my flight.

Huh?  Does TSA now do this?  Before or after the loyalty test?

---

### Post by scruffybeard on 2008-03-05
Ok, so here's the final results.

After doing an install from the alternative CD, I ended up in exactly the same place as before where I had a fully functional Gutsy/XP system, but even though I selected the Linux partition for the bootloader, it still went on the MBR.

Not a big deal though.

I used the SuperGrub disc to put the Winderz loader back on the MBR. This actually worked better than I thought, because now XP boots automatically with no hint of grub, but somehow, Supergrub still knows how to find real grub.

Just what I wanted.

As for the airport questions, I am always forced to put my backpack on the conveyor, then security opens it up, pulls out my machine, and tells me to turn it on and boot it up to prove that it is not some terrorist device.

Now, mind you I have lived in America my whole life. Born and raised in the midwest. I have no hint of any accent, and I look like your typical stoner college student. And somehow my laptop is some nefarious do-evil device?

Meanwhile, four other people have powered up their slabs, shown a Windows or OSX desktop, and been allowed to board, while I am still explaining to some overweight fool the ins and outs of alternative operating systems while he/she stares at me with a glazed over, dead look.

---

### Post by logos34 on 2008-03-05
> **scruffybeard said:**
> As for the airport questions, I am always forced to put my backpack on the conveyor, then security opens it up, pulls out my machine, and tells me to turn it on and boot it up to prove that it is not some terrorist device.

Now, mind you I have lived in America my whole life. Born and raised in the midwest. I have no hint of any accent, and I look like your typical stoner college student. And somehow my laptop is some nefarious do-evil device?

Meanwhile, four other people have powered up their slabs, shown a Windows or OSX desktop, and been allowed to board, while I am still explaining to some overweight fool the ins and outs of alternative operating systems while he/she stares at me with a glazed over, dead look.

I don't know whether to laugh or cry.

TSA is brain-dead...I mean, you could easily have a **fully functional** lappy with a pound of Semtex or C-4 explosives crammed inside its crevices--enough to blow the plane apart and still read your email beforehand!

Your taxpayer dollars at work!

To think what this country has come to. (And it's not just us--the UK is right behind us in the race to the full Surveillance State).

---

