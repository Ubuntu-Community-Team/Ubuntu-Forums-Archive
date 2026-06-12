---
title: "Dualboot troubles [Win7 + Ubuntu]"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by HappyJaZZ on 2011-03-11
Hey folks!

I have previously been running dualboot with Windows 7 and Ubuntu 10.10, which worked great.

However, with the recent release of Win7  Service Pack 1 I decided it was a good time to wipe the windows disk. After reinstallation of Win7, however, I no longer got the option to boot into Ubuntu, though the partition with all the Ubuntu files is still intact.

Any idea of how I can restore the option? Will it be enough to boot from the windows CD and do a /Fixboot or /Fixmbr or whatever the command is?

Many thanks in advance!

---

### Post by oldfred on 2011-03-11
Those are windows commands to repair windows boot. 

You need to reinstall grub or more likely grub2. You would only have grub legacy if you upgraded from old versions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub


If you need specific instructions for your configuration, post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

