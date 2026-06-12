---
title: "Triple Boot"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by markr on 2006-05-17
Hi,

I already have Kubuntu and WinXP on my laptop, but want to have a play with Gnome (Dapper) as well.  kubuntu is my workhorse, so I don't want to risk breaking it, I've decided that I need a third partition for Gnome (and also I can continue to upgrade to upgrade to new releases without risk of breaking my stable system.

What I'm not sure about is how Grub will handle two installations on Linux managing the grub menu

For the sake of this example,  Part1 = WinXP, Part2 = Existing Breezy, Part3 = Intended new Dapper system.

So currently, I have Part1 and Part2 listed in my grub list held in /boot of Part2.

I'm assuming that when I install Part3,  my grub menu will by amended to show Dapper at boot, but the grub menu will now be managed from /boot on Part3.

If a kernel update happens on Part2, I'm assuming it will update the grub menu in /boot on Part2 and thus have no effect on the boot options at all because it is currently managed by Part3.

How do people that triple boot manage this?

Does this make sense, or I'm I babbling?

Thanks

Mark.

---

### Post by Sutekh on 2006-05-17
[quote=markr]

So currently, I have Part1 and Part2 listed in my grub list held in /boot of Part2.

I'm assuming that when I install Part3,  my grub menu will by amended to show Dapper at boot, but the grub menu will now be managed from /boot on Part3.[/quote] Correct, if the installation is smart it will also list the current Breezy and Windows partitions on the (GRUB menu on Part3)

This scenario is true when the new installation on Part3 puts GRUB on the MBR. 

As another option you could put the GRUB from the new installation, on Part3 itself instead.  This leaves the old GRUB (Part2) on the MBR.  You will need to add a menu entry for the new installation on Part3.

This is how I run my system.  The original GRUB is on the MBR, subsequent installations out their GRUB on their own partition not the MBR.

[quote=markr]
If a kernel update happens on Part2, I'm assuming it will update the grub menu in /boot on Part2 and thus have no effect on the boot options at all because it is currently managed by Part3.
[/quote] Correct, the GRUB update that is part of a kernel update only changes those kernels that were updated.  So updating kernels on Part2, changes the GRUB menu on Part2, updating the kernels on Part3, changes the GRUB menu on Part3. 

[quote=markr]
How do people that triple boot manage this?

Does this make sense, or I'm I babbling?

Thanks

Mark.[/quote] You are making perfect sense.   

I have to remember to edit the GRUB menu that I boot from (I am currently booting seven different OS) when a kernel update is applied.  

Hope I made sense to you!


If someone knows a better way I'd love to hear it.

---

### Post by groggyboy on 2006-05-17
You could, if you wanted, let Part3 take over the grub responsibilities, provided that it is the active boot partition.

The downside is that everytime Part2 has a kernel upgrade, you'd have to manually update the grub menu to reflect this.

The other option is to assign /boot to its own partition (which is shared by every linux installation - kinda like a seperate /home partition).  The idea is that every linux installation you have installs its linux-image in the same place.  Then, every time Part2 or Part3 gets a kernel upgrade, you can run "sudo update-grub" from either partition, and grub is automatically updated!  Of course, for this to work, every linux flavour on your box has to have a uniquely named kernel-image.

I haven't tried out the seperate /boot partition myself, but from what I've read about it, I think it is certainly the way to go if you are going to run multiple linux flavours.  One of these days, I'll get around to setting it up!

Hope this sheds some light!
Cheers,
groggyboy

---

