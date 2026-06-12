---
title: "Problem Restoring Grub after windows install"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by nizdobs on 2015-07-30
I had a dual boot PC (Windows on the spinning disk and Lubuntu on the SSD). Windows got hosed so my corporate IT guy reinstalled windows on my hard drive. Now I need to restore the Grub menu so I can choose to boot to Lubuntu or to Windows. I followed the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and [here]("https://help.ubuntu.com/community/Boot-Repair") and I ran the Boot Repair utility successfully.

The boot repair utility created the output that can be seen [here]("http://paste.ubuntu.com/11969248/"). However, when I start up the computer I'm still not presented with my Grub menu.

Any help is very much appreciated.

Thank you,

- Niz

---

### Post by oldfred on 2015-07-30
Is your hard drive identical in size to your SSD?
It looks like you have only Windows installed on both drives, perhaps as RAID?

Post this from terminal in Ubuntu live installer.
       sudo lshw -C Disk -short

---

