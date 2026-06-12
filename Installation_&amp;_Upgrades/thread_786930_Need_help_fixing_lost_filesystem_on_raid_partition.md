---
title: "Need help fixing lost filesystem on raid partitions"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by oceanmajk on 2008-05-08
I need some help recovering a broken filesystem on my raid partitions. I setup mythbuntu 7.10 a while back with the alternative disk in order to setup a software raid for my htpc. I have two 500gb drives, and set them up to have 4 partitions on each, 3 of which were in a raid 0 configuration, like so:

/dev/sda1	500MB 	boot
/dev/sda2	10GB 	/	raid
/dev/sda3	1GB 	swap	raid
/dev/sda4	455GB	/home	raid

/dev/sdb1	500MB 	boot
/dev/sdb2	10GB 	/	raid
/dev/sdb3	1GB 	swap	raid
/dev/sdb4	455GB	/home	raid

The large partition was my /home directory, which I stored all of my movies and tv shows.... almost 700GB worth. It was working ok, but I needed to make some updates, and ran the pending updates through synaptic manager. Once I rebooted, I was presented with a new mythbuntu login screen, which before it booted into ubuntu desktop and i had to start mythbuntu manually. The problem was, my main user for the machine was there, but trying to login said that the home directory for that user could not be found, and to use the root user's home directory as a fail safe, and it tried to login then kicked me back to the login screen. So basically after installing the updates there weren't any users available to login and I couldn't get into the machine. I tried fixing this in the terminal but couldn't figure out what went wrong. I then decided to just do a new install of the latest Mythbuntu 8.04, but did not want to reformat my partitions for obvious reasons. I ended up installing mythbuntu 8.04 on the 10GB partition that was setup for the filesystem, and it installed fine and booted up. But it seems during install it wiped out any information about my raid partitions, even though during the install I didn't have it touch them. 

The problem is, I can't mount my other raid partitions anymore. They were formatted ext3 but now aren't showing any filesystem when using GParted (see pictures). I've tried booting the live cd, making sure nothing is mounted and tried to run "sudo parted /dev/sda" but don't know the start and end of the partitions exactly, and don't know exactly if it's going to repair what I need repaired. I've also run "sudo testdisk" but it finds multiples of the same partitions and doesn't look correct. I tried "sudo gpart /dev/sda" but haven't repaired anything because I don't want to lose all of that data on the big partition. I'm trying to be very careful about what I do with these partitions because losing an archive of my movies will suck royally.

Can anyone please help explain something that I can do to repair the filesystem on these raid partitions and get them mounted again and accessible? Can I reinstall mythbuntu with the alternative disk and setup the raids again without formatting the drives? Can I run some utility to repair the filesystems on the raid partitions and setup mdadm again? Your help is greatly appreciated.

Here are the screenshots of GParted for my drive info. (sorry for the quality, only thing I could do)
[IMG]http://majk.net/mythbuntu1.jpg[/IMG]
[IMG]http://majk.net/mythbuntu2.jpg[/IMG]

---

### Post by lemming465 on 2008-05-10
I think there may be bugs in the Ubuntu 8.04 kernel 2.6.24 and mdadm 2.6.3 MD support; web searches on *linux 2.6.24 mdadm* turn up some nasty stuff.

Try an older version, e.g. a 7.10 live CD.  Wouldn't necessarily have to be a Mythbuntu CD.

---

