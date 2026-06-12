---
title: "grub-install won't work"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by ShaneOMyNameO on 2007-11-28
Hey everyone,

I decided a few days ago to start using Linux. I downloaded the newest version of Ubuntu for a 64 bit processor.

However, having spent a lot of money on Vista, I wasn't about to get rid of it, so I decided on a dual-boot configuration.

So, I did all of the necessary defragmenting, and set up a 15 gb partition for Linux to install on. I booted from the Live CD and began the installation.

At about 96% the installation failed, telling me that grub-install failed, and that "This is a fatal error."

So I tried again, this time turning off boot-loader installation. It installed without a hitch.

Restarted the computer, and Vista loaded without a hitch. I looked up grub on google, and went back to the live cd. In the terminal I wrote

sudo -i
grub-install '(hd0)'

I was told :

"Could not find device /boot: Not found or not a block device."

I also tried grub-install /dev/sda, to no avail.


Why is grub refusing to install?

I really want to try Linux, but now I'm considering just sticking with Vista, which, despite its shortcomings, I was at least able to install without any issues.

I basically have an Ubuntu installation sitting on my second partition, with no way to get to it. :(

Thanks for your help.

---

### Post by Sef on 2007-11-28
-) How did you partition it? 

a) Did you use Vista to shrink its partition?

b) Did you defrag the hard drive before installing Ubuntu?

---

### Post by ShaneOMyNameO on 2007-11-28
I used diskpart.exe in the Vista command prompt to shrink my Vista partition. I let the Ubuntu installer format to ext3.

Yes, the computer was defragged (more than once).


Thanks for the quick reply!

---

### Post by ShaneOMyNameO on 2007-11-29
Great news!!!!

You asked if I created the partition in Vista.

I took the hint and destroyed the partition, and left the space unallocated.

I booted up the Live CD again and allowed the installer to work its magic on the space.

It ran smoothly and I now can dual boot Vista and Ubuntu :):)



Thanks for your help, Sef! And, uhh.... ROCK ON!!! :guitar:

---

