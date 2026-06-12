---
title: "Froze during install, now weirdness"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Goldspink on 2007-01-14
Hi, I've been installing Linux for the first time but had some problems. I'm installing alongside Windows XP.

While installing I happened to click one of the Applications menu on screen and I don't know what happened but Linux didn't like it and the installation froze at 49% with the Apps menu just stuck on screen. I left it to recover for as long as I could but nothing happened so I had to restart.

Then I got 'error loading operating system' at bootup so I booted from the Linux CD again and restarted setup. However, this time on the 'Prepare disk space' screen there was no option to resize the first disk and use free space, only the other three options, so I chose to manually edit partition table as I wanted to keep my Windows installation. I chose to install it on the EXT disk.

Now the grub menu appears and I can boot into Windows but its partition has shrunk to 12 Gb which was the size I wanted Ubuntu's disk to be. Furthermore, Ubuntu works but the hard disk on the Ubuntu desktop is actually my Windows disk -- when I open it there is my WINDOWS folder, Documents and Settings, IO.SYS, etc.

Can somebody help explain this please? When I set up the partition on the 1st attempt I dragged the slider till the number above it showed 12Gb, I assumed this was the size the Ubuntu partition would be. I don't know why my Windows drive shows up in Ubuntu. In that case, where is Ubuntu running from?

I hope someone can help me, let me know if you need me to describe anything else.

Thank you

---

### Post by Henry Rayker on 2007-01-14
The reason your windows hdd shows up on the desktop is because it mounted the windows partition. This will allow you to read files from your Windows install; If you wanted to transfer some documents from My Documents in the Windows install, for example, you could just drag them over with no problem.

As for why the Windows drive was resized, I'm not certain...I always resize the partitions on my own. My guess is that you misread a dialog; I assume the dialog was asking something to the effect of, "Your harddrive has no empty partitions. Resize one of the available partitions to  install." or something similar.

As for where Ubuntu is installed, it is installed on the harddrive you installed it on. A more appropriate question, I suppose, would be, "Where are the Ubuntu files stored?" If you are using GNOME (Ubuntu, not Kubuntu or Xubuntu etc), there should be a panel with an entry titled "Places". That should be the easiest way, I believe.

---

