---
title: "request multiboot help with grub"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by tn_eagle on 2008-01-16
Hi. I'm new to Linux and Grub and this is my first post here. Recently my XP hard drive started going bad so I just replaced it with a larger drive, then installed XP Pro, then Mandriva and then Ubuntu 7.10. I can boot fine into any of the 3 operating systems. I like what I've seen so far in both of the Linux distros.

Here is my problem: Prior to installing the new hard drive, I had a dualboot setup with XP Pro on the master hard drive and Vista HP on the slave hard drive. This worked fine. I'm wondering if anyone can advise me on how to make Vista work with Grub hopefully without reinstalling Vista.

I can edit the menu.lst file for Grub and I added an entry for Vista, but everytime I try to boot into Vista, it instead boots into XP. To be able to edit menu.lst, I created a launcher with this command:
gksudo "gnome-open %u"
...and can drag 'n drop menu.lst on the launcher, enter password at the prompt, and then can edit and save the file. I found this tip here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
...and it works great.

Anyway, I'm not sure what to put in menu.lst for Vista. I tried this:

# This entry manually added for a non-linux OS
# on /dev/hda1
title Microsoft Vista Home Premium
root (hd1,0)
savedefault
makeactive
chainloader +1

...but that doesn't work. It was only a guess. Also, since in the previous dualboot setup, Vista would only boot when selected in the Windows bootloader menu and would not boot on its own (got the ntldr not found message), I suspect that I may need to add some boot files to the Vista hard drive.

If anyone can advise me on what to do to add Vista to Grub and make Vista boot, I would greatly appreciate it.

Thanks,
Richard

---

### Post by tn_eagle on 2008-01-19
Nevermind...I just got it working. I did a startup repair on the Vista hard drive while booted from the Vista DVD to change the hard drive to a bootable hard drive and now the addition I made to the Grub menu.lst file works fine for Vista. I can now boot into XP Pro, Vista HP, Mandriva or Ubuntu through the Grub bootloader.

Richard

---

