---
title: "Can't boot clean install - grub rescue prompt"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by Seltox on 2012-08-04
**SOLVED** - Shortly after posting this, I tried one last thing that had come to mind, and it seems to have done the trick.  Will add details to the end of this post incase anyone else has a similar problem.

-----

Hey,
I've been running Ubuntu 10.04 for a while on my laptop, and upgraded it to 12.04 today.  First thing that came to mind was "Hey, this would be amazing on my desktop!" - which runs W7.  My desktop has multiple hard drives, so I was able to easily dedicated an entire disk to Ubuntu, not having to worry about Windows at all.

The installation process went perfectly smooth.  I dedicated 600mb to the /boot partition, 20gb to /, >900gb to /home, and ~8gb to swap (running 16GB of memory in the desktop).

The issues came when I tried to boot.  When I try to boot from the disk Ubuntu was installed on, I am getting this error:

```

error: file not found.
grun rescue>

```

I know i've seen this before somewhere, I can't remember where thoguh..  Anyway, I have no idea what the commands are for this prompt, but I tried a few unix commands and 'ls' turned up this:

```

grub rescue> ls
(hd0) (hd0,7) (hd0,6) (hd0,5) (hd0,1) (hd1) (hd1,1)

```

I've got to assume that hd0 is the drive (I unplugged all other devices - 4 other disks, optical drive & HDD dock), and hd1 is the USB I installed from, with the numbers afterwards being a reference to the partition?  (I'm still very much new with linux.)

I've really got no idea why it isn't booting.. I'm installing on a drive i've had for quite a few years, so it's possible that I had a linux install on it previously?  I'm not sure though.

Any advice would be greatly appreciated.

- Seltox



-----

**SOLVED**

I started thinking about the possibility that I had installed linux/grub previously on this drive (given that it was a few years old)..  Then I remembered one extra option during the installation, when setting up partitions.  The one that was like "New partition table..." or something, and thought I should give it a go.  So booted up the install again, and chose that option on the hard drive.  Continued past the message telling me it would delete my partitions and stuff - re-partitioned everything (as described above) and installed.  This time it booted up straight away :)

Since I don't actually have a whole lot of knowledge in this area, I can only make presumptions about the exact cause of this, but perhaps someone else will know and could kindly explain it :)

- Seltox

---

