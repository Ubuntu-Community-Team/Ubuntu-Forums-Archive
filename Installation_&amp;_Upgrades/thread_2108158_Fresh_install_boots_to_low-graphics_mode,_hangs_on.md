---
title: "Fresh install boots to low-graphics mode, hangs on &quot;Stopping System V runlevel&quot;"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by qianian on 2013-01-23
I'm prepping a new Samsung 840 Series SSD to replace my current laptop hard drive. It's connected via USB adapter. 

I successfully partitioned and clean installed 12.04 from live disk with d/l updates and third-party software sources. At the end of install I got a warning that some software did not install completely, so I'd have to fix it. The problem is the new drive boots to low-graphics mode. It can't find screen, graphics card, or input device settings and I can't get a command prompt.

I've found solutions to install a new graphics driver, but I've never needed to do so for previous installs on this laptop. (Example: [http://ubuntuforums.org/showthread.php?t=1920814](http://ubuntuforums.org/showthread.php?t=1920814) )

How do I get a command prompt? Ctrl+Alt+Fn lets me log in, but blinks an output before returning me back to login screen. Any other option from safe mode hangs. Please help me get this new SSD set up.

---

### Post by qianian on 2013-01-26
Any ideas at all?

---

### Post by qianian on 2013-01-26
I reinstalled from live CD and found an error at the end that matches [Bug #1066347]("https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1066347") 

No solution yet. Any idea if this is the source of the problem?

---

### Post by qianian on 2013-01-31
Any ideas? A fresh install to a new SSD should not be this hard. 

Any chance the adapter is the problem, and I can resolve this by installing the drive directly?

---

### Post by Mark Phelps on 2013-01-31
IF your current laptop drive's install works OK, one alternative I did was to (1) shrink down the partition size on the HDD (to fit on the SSD), (2) connect the SSD and (3) use Clonezilla (booting from CD) to image the HDD install to the SSD.

When done, replace the HDD with the SSD and you should be ready to go.

---

### Post by qianian on 2013-02-01
Thanks, Mark, here's what I got. I used fsarchiver to save my original root partition to a separate hard drive, then extracted it to the target drive. From the BIOS menu I select the target drive, which is still connected via adapter. 

Here's where it goes wrong: the adapter indicator blinks as I'm prompted for which version to boot to (regular, recovery mode, etc) and blinks again after I hit enter, but my original drive then boots. I see my original home folder instead of an empty one and I can see the target drive as a mounted device. 

Why won't the target drive boot? Here are the commands I used from live disk:

$ fdisk -l
[partition IDs]
$ fsarchiver savefs /separatehd/bootfs.fsa /temp_mounted_targethd
$ umount temp_mounted_targethd
$ fsarchiver restfs /separatehd/bootfs.fsa id=0,dest=/dev/sdb1

Both fsarchiver commands returned large numbers successful and zeros error.

---

### Post by Mark Phelps on 2013-02-01
Sorry, don't use fsarchiver, only used Clonezilla.  So, I can't help you fix the current problem, sorry.

---

### Post by qianian on 2013-02-01
Okay, I tried Clonezilla but have the same results: booting with only the new SSD installed goes to an ubuntu error screen saying it can't find /home and asking if I want to skip or mount manually. If I attach my old hd that boots instead of the SSD.

---

### Post by qianian on 2013-02-01
Okay, I've fixd this problem by updating the /etc/fstab. The clone had kept the old UUIDs for /home and swap. 

Now I have a login problem: [http://ubuntuforums.org/showthread.php?p=12487439#post12487439](http://ubuntuforums.org/showthread.php?p=12487439#post12487439)

---

