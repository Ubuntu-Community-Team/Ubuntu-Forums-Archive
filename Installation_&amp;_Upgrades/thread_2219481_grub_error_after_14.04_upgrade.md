---
title: "grub error after 14.04 upgrade"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by olly-xquest on 2014-04-24
I have a dual boot Ubuntu Studio 13.10 dvd-amd46 / Windows 8 installation and have just completed the recommended upgrade to 14.04 

On power-up the blue grub screen does not display and I get the following error message:

error: symbol 'grub-term-highlight-color' not found.
grub rescue>

I have tried the following boot repair procedure:

insert ubuntu 13.04 disk and select try unbuntu
open  2 instances of terminal
at command prompt of first terminal type:
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update 
sudo apt-get install -y boot-repair 
boot-repair

Select Recommended Repair
rename EFI files - yes

given lines pasted into command line of other terminal

completed without error

reference given: [http://paste.ubuntu.com/7320970/](http://paste.ubuntu.com/7320970/)

I have emailed the reference to [email]boot-repair@gmail.com[/email] and got a bounce back.


I still get the same error on startup - what action should I take?

---

### Post by oldfred on 2014-04-25
Undo the rename. That is for 'buggy' UEFI where vendor has modified UEFI to only boot Windows. I do not think Toshibas have that issue.

 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

      
 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

Boot-Repairs total purge & reinstall of grub may also work.

---

### Post by olly-xquest on 2014-04-27
Thanks for the useful links - I wil post a comment on bug #1289977.

---

