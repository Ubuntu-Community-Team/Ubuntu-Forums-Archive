---
title: "Installing dapper on lacie mobile HDD"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by adamswe on 2006-08-13
Hi!

I was "given" a computer by my employee and have during the summer been using linux (suse) on the internal HDD (Dell latitude d520, dual core intel 1,66, 40 gb, intel gma950). But now work has started again and my HDD is to be eraised and windows 2000 for the network is to be put on it. Yes, I know I should start a discussion as to why we can't use linux, but that won't leed to anything soon, that is why I bought myself a LACIE mobile HDD, 40 GB. I am intending on installing Ubuntu on this. I have given it a shot but am having some problems:

I boot the live cd (this could be the first problem?) and the cd finds my lacie drive as a USB storage device. When I start my installation and get to the partitioner a fat32 partition is found (preformatted in fat32). Unfortunately it was impossible to erase this partition within the installer. A small lock symbol was seen against the drive. I exited the installer and in gparted replaced the disklabel thereby erasing the HDD. I then started the restall again and was able to create partitions (swap, / and /home). Asigning the mountpoints got a bit wierd as I still have my suse install on the internal HDD. The installer wanted to use the internal swap. After asigning the internal swap a mount point of it's own (/media/sda1) I was able to asign the swap I created on the external HDD.

So far so good, but when the install itself starts I get an error saying that the filesystem was unable to be created and I get back to the partitioning part of the install. Here I can now see my partitions have a lock against them as before (except for the swap).

Questions:

Is it possible to install onto external HDDs? I have seen the subject discussed, so it seems to have been done. My bios allows me to boot (as far as I know) from USB devices.

Why the locks?

Can I install to the HDD in a way alowing me to move the HDD to any computer? Sort of like a live CD but on a HDD? (Could be quite handy!) Pros and cons of this?

Am I doing anything wrong?

As I am supposed to give the computer back for reinstalling soon I would be very grateful for a quick reply!

Thanks for now

Adam in Shweden...

---

### Post by apurva on 2006-08-16
Hi

I have the exact same situation as Adam, I inted to run a secondary OS which is completely installed on my USB Dongle. From the reading that I have done all over, I am guessing that I can do it in 2 ways. 

1. install ubuntu on my USB Drive - Tried this and got the same problem that adam's facing (Also this way i think the os will be configured for the hardware I install it on, and I am guessing it wont work with other computers i.e. will not behave as a live CD)

2. Make the USB drive a live CD (using syslinux etc) and have my computer boot to it. - I would love to use ubuntu like this, but I am not sure if i can then save changes that I make (meaning files that i download or apps that i install or bookmarks that i add. 

I have seen puppy linux and a few other distros claim that they arer built for USB drives and they can do all of this but I would really like to use ubuntu as i like gnome over KDE.

ps. I am a total linux noob! so excuse anything stupid that i said!

---

### Post by keri_ubu on 2006-08-19
yes this is possible:

check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)
it gives a detailed tutorial for breezy, but this works also for dapper, see in same thread: 
[http://www.ubuntuforums.org/showpost.php?p=1093160&postcount=403](http://www.ubuntuforums.org/showpost.php?p=1093160&postcount=403)

note that you for Dapper you need to use the "alternate" installation CD instead of the live CD to do this

---

