---
title: "Screen Hangs at grub"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by festaman on 2005-09-09
When i turn on my computer it jsut says grub with a blinking cursor, i have resintalled and formatted 3 times.  The odd part is i put my hirens boot cd 7.3 in and when i hit start windows grub loads fine. if i restart with out hirens it doesn't work it just hangs and Says Grub_  any ideas?

---

### Post by mlomker on 2005-09-09
[QUOTE=festaman]When i turn on my computer it jsut says grub with a blinking cursor, i have resintalled and formatted 3 times.  The odd part is i put my hirens boot cd 7.3 in and when i hit start windows grub loads fine. if i restart with out hirens it doesn't work it just hangs and Says Grub_  any ideas?[/QUOTE]

Grub is a boot loader--formatting won't get rid of it, actually.

Boot up to a CD copy of linux and try this at a command prompt.  I'm assuming that your booting from your first hard disk and first partition.

grub
grub> root (hd0,0)
grub> setup (hd0)
grub> reboot

[A more detailed explanation.](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by festaman on 2005-09-11
That didn;t seem to work its driving me bonkers!

---

### Post by LoneWolf3574 on 2005-09-11
I'm having the same problem.  I'm running Ubuntu exclusively on one of my computers.  It installs just fine, but when I bootup the computer all I get is "GRUB Loading, please wait...".  I'm on my 3rd reinstall right now after doing a format and resetting the master boot record on the disk using a Win98SE floppy (fdisk /mbr).  Any help would be greatly appreciated.  Thanks in advance.

---

### Post by crysys on 2005-09-17
I'm in the same boat as the post starter.  My GRUB just hangs after the word GRUB.  I'm currently using a Live Mepis CD to seek an answer.

Here is how I found myself in this shameful state of affairs:

I had a typical Warty install I've been using since it's release.  I recently downloaded and burned the 5.10 Preview disk, then pointed synaptic to it just to see what happens.  I do not recommend this course of action.  It will not upgrade your Warty install to Breezy.  ](*,) 

Luckily I had 8GB free on the disk that never got turned into a Windows partition as planned.  So when my new franken-wart-badger would not reboot I popped that preview disk back in and commenced a fresh install in the free space.  Then I allowed GRUB to put itself in the MBR and finished up the install.  On reboot I was not greeted with a choice.  Instead a rather unhelpfull aforementioned four letter word was staring back at me with an emptyness in it's eyes.  (This is metaphor, words don't have eyes like potatos and some animals do.)  

I've wiped the Breezy install off the disk to try again.  I'm sure the warty install is still sunk but I need to retrieve my files from it before I can wipe that partition and start anew. I could perhaps make a new partition from the 8GB from my LiveCD and move everything there, then wipe the warty partition.  If I pull this off can I clear the MBR so that GRUB has a chance of working this time?

I'm hesitant to belive this would work if, as the original poster says, reformats and reinstalling has not repaired the MBR.  What do we do to force GRUB and the MBR to start over from scratch?

---

### Post by docmanny on 2005-09-17
Probably not the most efficient way, but I just had the same problem. Search under linuxquestions.org. I think the thread is called "grub hanging".

Long story short, I ended up reinstalling Yoper using Lilo as a bootloader. Put ubuntu in as a second OS. Lilo then gets redirected to grub to load Ubuntu.  A little roundabout but its working!!

---

