---
title: "Problems with 9.10 - 64bit - random program crashes"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by albtross on 2010-02-02
Hello ,

It's my first time dipping my toe into Ubuntu. (but not new to Linux).

Built a new system: 
Intel i7 920
Memory: DDR3 6GB
Nvidia GTX260
Gigabyte X58UD5
no other OS

Downloaded the default image of 9.10 64-bit and installed fine (2.6.31-14-generic) 

However I am just have stability issues all the time, I can't lock it down to a particular task or program which crashes the system or just crashes the programs.

have checked the memory and hard drives (all ok) (even temporarily install winxp 32bit to confirm it wasn't a hardware issue -).

I've tried to re-installing the same image 3 times just to confirm it wasn't a corrupt, but still have stability issues.

I was wondering if I could get some advice on what my next step  can be.

I tried (unsuccessfully) to install a new kernel, but on reboot into the new kernel it freeze after a while - (2.6.31-18 generic) 
I'm not sure i upgraded the correct way. (please advice?)
via: Synaptic
           Search for linux-generic
                    selected " linux-generic" which selected 2.6.31-18 generic


Another strange scenario, was I tried to install the 32-bit version, but I can't get past the partition manger, where it freezes or comes back to cluster value number is wrong (to to that effect). - just can't get that to install at all!! 

I would really appreciate any advice

desktop:~$ sudo update-grub2
[sudo] password for albtross: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-18-generic
Found initrd image: /boot/initrd.img-2.6.31-18-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
andrew@andrew-desktop:~$
grub-install (GNU GRUB 1.97~beta4)

cheers

---

### Post by albtross on 2010-02-04
Well I have been paying closer attention to the memory over the last few days.

ATM I noticed that when I had stability issues only 4 of the 6 GB was seen. looking on other forums seems to indicate BIOS.

[http://www.tomshardware.com/forum/256210-30-ex58-skill-ddr3-1600-issue#](http://www.tomshardware.com/forum/256210-30-ex58-skill-ddr3-1600-issue#)

I didn't adjusted the BIOS setting which lowers my memory (G.Skill 1600 CL 9-9-9-24) abilities to 7-7-7-20. 

I've updated the BIOS to the latest however it made no differences (still instability). So now i'm manually set the timings

Has anyone else experience this

---

### Post by albtross on 2010-02-18
ok, to close out this, just in case people have the same issues.

it took me a few days to pin point the fault (physically removing and waiting!!) but it was a single flacky memory stick (sometimes it was recognised and then not).

FYI: G-Skill DDR3 1600

Cheers

---

