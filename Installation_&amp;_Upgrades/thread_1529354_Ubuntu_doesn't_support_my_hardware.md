---
title: "Ubuntu doesn't support my hardware ?"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by TheNTW on 2010-07-12
Ok, 
so this was my problem for instlling: [http://ubuntuforums.org/showthread.php?t=1526522](http://ubuntuforums.org/showthread.php?t=1526522)
Now I downloaded ubuntu server edition, and typed sudo apt-get install kubuntu-desktop, so it did. Now I am starting my PC up, and I can't get past "waiting mouse" image and the background of the splash screen. 
What the hell is wrong ? I am on this error for a week or so already! 
**Help!**

---

### Post by oldfred on 2010-07-12
I have a 9600GT and this worked for me for both install and first boot.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by TheNTW on 2010-07-14
This didn't work, because I cannot boot even in a Live CD!

---

### Post by oldfred on 2010-07-14
the server install CD is not a liveCD, did you also download a liveCD? Whenever I am changing system I have several liveCDs that I know work, gparted, system rescue. I used to write them all to CDs just in case, but now just copy ISOs to a grub loopmountable bootable USB.

---

### Post by TheNTW on 2010-07-15
I downloaded Ubuntu x86, kUbuntu x86, kUbuntu x86_64 (twice) and burnt them. Also tried burning to flash drive and booting from it, failed as well.
That exactly is my trouble. Nothing works for me, no live CD's at all.
I tried nomodeset, noapic, nolapic, deleted quiet splash, different type of everything. Nothing works. I am desperate. I really want Ubuntu, since it is the only distro I actually do like. SuSE would be nice, but it's YaST is too weird, and suse is too buggy itself anyways. So yeah - help.

---

### Post by oldfred on 2010-07-15
From your server install can you get to a command line?

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

---

### Post by TheNTW on 2010-07-28
Is there no real solution for this ?

---

### Post by varunendra on 2010-07-29
Ok, just a shot in the darkness..
Have you tried removing the HDDs and booting into Live session with only CD drive connected? Maybe some kind of HDD error??

Also, if you have tried so many distros already, try two more- 1)DSL, 2)Slax.
Yes, they're not Ubuntu, just curious about how does it go with these? (just a matter of different modules/drivers with different kernels)

---

### Post by oldfred on 2010-07-29
You said you removed raid but did you remove the meta data from your drive?

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

sudo apt-get remove dmraid
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

---

### Post by varunendra on 2010-07-29
> **oldfred said:**
> You said you removed raid but did you remove the meta data from your drive?.........
Exactly, that's what I was trying to remember !! :D (so not entirely a shot in the dark :lol:)
It was your very own reply to Me_Rock in one of his threads ([see the post]("http://ubuntuforums.org/showpost.php?p=9189493&postcount=10")).

I still don't have much understanding of RAID metadata, but I remembered that solution of yours. Besides, I also have an impression- I don't know since when, maybe I read somewhere- that SUSE relatively has some good understanding with RAID setups, so it often overcomes such errors automatically.

Let's hope it works for TheNTW as well. [-o<

---

