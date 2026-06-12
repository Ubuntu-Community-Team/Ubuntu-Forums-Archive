---
title: "Good copy of 10.10 won't install to HDD, badblocks found NO bad sectors. What to do?"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by Slinkee2k on 2010-11-15
Hey all. I have a puzzler (to me, at least). I tried to install Ubuntu 10.10 from a known-to-be-good disc, to a certain hard drive, which I will call "Frank". Frank is an 80GB SATA HDD. So, I tried to install to Frank on two different computers, where Frank was the ONLY connected HDD. Same exact error both times: at the end of the install, after all other files are copied, it says **"could not install boot loader".**

So I tried to install to a different physical portion of Frank. No dice. Note: no matter to which section I try to install the boot loader, it won't do it. Same error.

So I ran badblocks, doing a FULL DESTRUCTIVE TEST of Frank (newbs like me, note that this will destroy all data on the drive). So, what happened? Nothing: It ran the test, and found NO BAD BLOCKS.

Here is the output:
```
ubuntu@ubuntu:~/Desktop$ sudo badblocks -wvsX /dev/sda -o results.txt
Checking for bad blocks in read-write mode
From block 0 to 78150743
Testing with pattern 0xaa: done                                
Reading and comparing: done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.
ubuntu@ubuntu:~/Desktop$
```

Does badblocks test the MBR section of the HDD? Is there really nothing wrong with Frank? Did I do something wrong?

What gives?? Why would Ubuntu fail to install to this drive, with two different motherboards? The Ubuntu 10.10 install disc verified itself was correct, and I successfully installed to another computer with it. What do I do now?
Thanks.

---

### Post by dazman19 on 2010-11-15
has "Frank" been part of a raid array in the past? EVEN IF HE HAS BEEN FORMATTED.  Because I had a couple of disks the other day before I loaded 10.10 and they were part of a raid array. I ended up having to use some disk manager i got off a fedora 14 cd to tidy up the old raid array. Disk druid didn't work, and I don't like using parted, it scares me.

---

### Post by Slinkee2k on 2010-11-16
Hmmmmmm. *ponders a moment*...

I am about 95% sure that this disk-- Err, I mean *Frank,* was *never *part of any RAID array. However, it is REALLY good to be aware of such a thing. Wow, so, are RAID config setting stored elsewhere the disk (like a Flash RAM chip)?

:( Sigh. I'll definitely check that out. Any other recommendations? I guess I could try a different SATA cable. -_-

---

### Post by dino99 on 2010-11-16
to remove (if it exist):

sudo dmraid -rE

then prepare installation:

boot on partedmagic ( [http://partedmagic.com/](http://partedmagic.com/) ) to create 3 partitions:

- / : which is "root", make it bootable, ext4, ~ 12 Gb (take note of its name, something like /dev/sd?, the installer in manual mode will ask about it )

- swap : ~ 2 Gb

- /home : ext3 or ext4, unlimited space to store your data and settings

then use the "alternate" iso to install it on / , and install grub2 on /dev/sd? ( ? is a letter )

then you can choose to boot on hdd into the bios.

---

### Post by Slinkee2k on 2010-11-16
Thank you, I will try what I can! I wonder why it would fail... I will post my findings!

I also found [this thread post]("http://ubuntuforums.org/showpost.php?p=9202074&postcount=5") that looked helpful.

Also, please note the following: the operating system actually installs, as far as I know. I think it is only the boot loader that fails to install.  I was able to manually install GRUB to ROOT, but I couldn't get vmlinuz kernel to boot!! (I have since formatted the drive).

---

