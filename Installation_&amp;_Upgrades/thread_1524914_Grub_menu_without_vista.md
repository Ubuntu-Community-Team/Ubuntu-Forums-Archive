---
title: "Grub menu without vista"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by reptil on 2010-07-05
Hi all,
 
I'm pretty sure about you see a post like this before, but I don't find the solution yet, So please reed it and give some help.

After upgrade to 10.4 I saw some strange in my grub menu, I see the ubuntu options, a couple of memtest* options and  a couple windows options and there is my problem (or I think is a problem)
The window's option are Windows recovery environment and Microsoft Windows XP Embedded

I'm sure that I got an other option to load windows vista, excuse my bad memory I not remember the name of that option.

So I run the  boot info script and this is the result...

thanks for your time

---

### Post by oldfred on 2010-07-06
We have seen several cases where the grub osprober reverses the recovery enviroment and the install titles. In you case it did not show the recovery in sda2 since it is missing some of the boot files. If you boot the one labeled recovery, does it not boot correctly? 

Also since your XP is in a logical partition, does grub boot it or do you still have to boot thru the windows boot. Its boot.ini says it thinks it is in partition 1 but it is in partition 8.

Windows normally combines all windows installs to the copy of windows with the boot flag (active Partition). Your boot flag is on a DOS partition sda1. Did your system boot thru that?

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by reptil on 2010-07-08
> **oldfred said:**
> If you boot the one labeled recovery, does it not boot correctly? 

It looks like boot correctly, but I miss some applications I need dis not  try to reinstall because I don't used any more

> **oldfred said:**
> 
Windows normally combines all windows installs to the copy of windows with the boot flag (active Partition). Your boot flag is on a DOS partition sda1. Did your system boot thru that?

not really, the last time that I try to load windows through the embedded xp I saw a pretty black screen and get back to the boot list. I did that after upgrade to lucid, I never try it again..

Thanks for the links

I will back If I cann't fix it

regards

---

