---
title: "Unable to dual boot between Ubuntu and Windows 7"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by Swoorup on 2012-09-23
Sorry, I have double posted the same topic, But it was in the wrong section. 

> 
I downloaded a copy of Ubuntu 64-bit OS iso images and booted up in the  thumb drive. I then created a live USB using Unetbootin. I then booted  the live USB up in non EFI mode and installed Ubuntu in a separate  partition so that I could have 2 Operating System on my computer. 

But I could not get the dual boot option. And then again after following  up some forum posts from this website, I tried using boot-repair and it  installed GRUB 2.

Here's what the instruction said after the boot-repair completed its task.
[quote]
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1221979/](http://paste.ubuntu.com/1221979/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the  disk. Your BIOS may not detect them. You may want to retry after  creating a /boot partition (EXT4, >200MB, start of the disk). This  can be performed via tools such as gParted. Then select this partition  via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
I then rebooted the system and I could get an option booting up  Ubuntu and Windows 7 alongside with it, but the problem is that when  choosing Ubuntu it does not seem to do anything. The screen just goes  blank. 

The grub configuration file is attached within this post if it helps.

Please help. I am new to linux but I am eager to learn it.
[/quote]

---

