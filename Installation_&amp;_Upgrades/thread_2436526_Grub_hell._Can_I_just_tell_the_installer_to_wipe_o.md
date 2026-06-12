---
title: "Grub hell. Can I just tell the installer to wipe out grub and reinstall it entirely?"
date: 2020-02-07
forum: Installation &amp; Upgrades
---

### Post by david503 on 2020-02-07
Here's the story: 

I was having problems with python/django so out of frustration I decided to just reinstall ubuntu entirely.

My /home directory was on the same partition as /.  

So before the reinstall I used gparted and resized the partition and made room for 100g for the reinstall.

When I installed (18.04), In the installer I set the mount point for what *was* the old ubuntu as /home, and use the new empty partition as /

I installed, when I rebooted it threw errors and dropped to cli.  So I figured grub was trying to point at the /boot on the old install partition.  (why didn't the installer tell grub to point to the new / partition?  why would it tell grub to point to the /home/boot?)

So I figured,  I'll just hide every directory in what *was* the old install into a directory called (oldboot) so the installer can't even find a boot directory, and then I deleted the 100g partition and then I reinstalled 18.04 again.

Now what happens is I get the emergency mode cli.  (not the same prompt as before (and btw neither one is a grub prompt). This was was the "You are in emergency mode press Ctrl-D to login" prompt)

So what's happening? Is this grub's fault? Maybe  grub still hung up on something remnant? 

How do I tell the installer to just delete grub entirely and reinstall it, instead of editing the current one?

I don't understand what the installer and/or grub is doing to make it try to even look in the /home directory at all.  

How does this happen? This makes no sense.

thanks

Oh wait- can I delete the EFI parition? Or will that destroy the MBR or something?

---

### Post by oldfred on 2020-02-07
UEFI using ESP - efi system partition for UEFI boot is required.
Only if you have the old BIOS/MBR configuration, would you have a MBR used for booting. UEFI/gpt does have a protective MBR with one entry saying drive is gpt partitioned, just so old partition tools would not see a blank drive and try to redo it.

You cannot use a /home/$USER folder as the /home partition. Your folder is not at top level. You have to move /home to its own partition first.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by coley9225 on 2020-02-16
The only way I could get lubuntu 18.04 to install on my computer, was to start live usb, in terminal run ubiquity -b. That will install the operating system without the bootloader. BEFORE you restart your computer, use boot repair to set things so you can boot. In my case, after booting into lubuntu and getting error messages, I had to purge and reinstall grub. Now my lubuntu install runs great. Good luck.

---

### Post by vidtek on 2020-02-16
David-

Listen to oldfred, he is the guru.

Shrink your old home partition to it's very minimum, delete all the folders in the / root directory and just keep the /home folder.

Then create a separate new partition for your new /home folder as big as you can.

Do the boot thing as in this thread: [https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625]("https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625")

Then copy your stuff with rsync as oldfred says, delete your old /home and use gparted to gobble that old home partition into itself. 

Cheers Tony.

---

