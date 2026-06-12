---
title: "Bios fail to send me to GRUB after upgrade to 8.10"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Gasten on 2008-11-13
Hi!
I recently upgraded from 8.04 to 8.10. The upgrade seemed to go fine, except that when I first rebooted, x seemed to have problems starting - it froze, among other things.

when doing a hard rebot, I discovered that grub would not boot. BIOS seemed to hang - I can't even get into the boot menu! I do not have a liveCD available at the moment, but I'm doing everything I can to get one - though, since it seems to be something with BIOS, I don't really think it'd help.

Any thoughts, ideas?
Thanks!

---

### Post by Otustelija on 2008-11-13
I don't see how upgrading would mess up with your BIOS. Most likely a problem with grub that should go away after a grub reinstall (from a live cd). Do you get any error messages?

However, you don't happen to have several hard drives, do you? In that case you could also see if the boot order in your BIOS is correct.

---

### Post by caljohnsmith on 2008-11-13
Do you get any Grub errors on start up at all? What exactly happens when you reboot or turn on the computer? Once you get your Live CD, how about opening a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
```
And for whichever is your Ubuntu partition, how about doing:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with your Ubuntu partition.

---

### Post by Gasten on 2008-11-13
Well, I get the dell-logo which should dissapear, but the system just freezes at that screen and refuses key-input. I'll try to be faster hitting the setup-key right when it boots (hopefully before it freezes).

I got two harddrives, and a couple of partitions on each. I dualboot(ed) ubuntu and Vista.

Gonna give you more info tonight. Thanks.

---

### Post by Gasten on 2008-11-16
Ok, I got myself a livecd, and it didn't work. BIOS still stops responding after boot. I can hear ´both the harddrive and the CD-Reader spin, but nothing happens. I have disconnected the computer from the power socket, and open it up and tried to remove the harddrives etc. still nothing. The homebrewers on handheld systems call this state "bricked". My computer is as useful as a brick.

I'm trying to get hold of some backup solution (other computer, or something) so I can save my data and check if the drives is corrupt or what the heck it is.

What do you think I should do? I have never experienced this kind of low-level problems before. I cant update/reinstall my bios because I cant even get into windows.

Please help me.

---

