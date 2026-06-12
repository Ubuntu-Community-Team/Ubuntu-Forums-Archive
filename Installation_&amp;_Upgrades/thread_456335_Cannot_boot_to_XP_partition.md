---
title: "Cannot boot to XP partition"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by tbingel on 2007-05-27
Hi. I had win XP Pro on my system disc. I have installed Ubuntu 7.04 today. I had problem accesing Ubuntu after editing the screen resolution. I have sorted this out editing menu.lst file to point correct partititon. However, when I try to boot into XP I get an error message saying hit Ctrl+Alt+Del to reboot. How can I solve this?

---

### Post by merlinus on 2007-05-27
Are you still using grub as your boot manager?  Can you post /boot/grub/menu.lst?

This might help....

-merlin

---

### Post by tbingel on 2007-05-27
Here it is...

---

### Post by mousejunkie on 2007-05-27
I can't download the zip file but it sounds like your mbr is screwed. Meaning you will have to repair it to get Windows back. google for "Windows Recovery" and "fixmbr". You will need a bootable Windows CD.

Alternatively you could just delete the Windows partition and use the space for Ubuntu.

---

### Post by merlinus on 2007-05-27
From what I can see in your menu.lst, it looks like you have a number of partitions, and the numbering and defaults for both the linux lernels and windows seem screwed up.  

For example, here is the windows part:

title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

It looks like there are two maps, each the reverse of the other, so things are very confused in terms of booting.

I would do what mousejunkie says, and restore your mbr so you can boot into windows.

Then you can decide what to do about ubuntu.

Another suggestion:

in a terminal (you can get to this by booting from a live cd), enter:

sudo fdisk -l

(l is a lowercase L)

That will give information about your partitions and filesystems.

Good luck!

-merlin

---

### Post by tbingel on 2007-05-28
Thank you very much guys... I have re-installed Win Xp Pro onto an unpartititoned space and got accees to my old XP data. I will back them up on a large external HD and then go back to play with Ubuntu until I am confident with it...

---

