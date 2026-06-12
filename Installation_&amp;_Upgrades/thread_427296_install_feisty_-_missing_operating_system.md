---
title: "install feisty - missing operating system ??"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by treeby on 2007-04-29
hi i just installed Feisty onto my 500gig sata drive (have a duo core processor and msi mother board)
then when i went to restart it said "Missing operating system"
the grub menu didn't even start up.

i had installed vista on the drive previously and after trying to get it to dual boot with feisty i just
gave up and wiped the drive with gparted and then just did an automatic install on biggest
blank space with the ubuntu installer...everything went fine..it made the ex3 partition, installed
the files but then when i went to reboot...nothing. do i need to defrag the drive from partitioning
it around so much? is there any way to do that from the liveCD? this is really frusterating..i've been
trying to get ubuntu to work for three days now. i've wasted so much time i feel like i'm about to
give up.

thank you so so so so much if you can help me

---

### Post by Vinze on 2007-04-29
I just happened to have the same problem, I needed a LiveCD to fix this.

In your LiveCD, first install lilo (using Synaptic or from the terminal with "sudo apt-get install lilo"), then from the terminal run the command "sudo lilo -M /dev/hda". That is assuming your hard drive is hda, which it probably is if it is the only one. If it is the second one then it'll probably be hdb, etc.

I've also read some times that it is sda or sdb or whatever. 

Hope that helped.

---

