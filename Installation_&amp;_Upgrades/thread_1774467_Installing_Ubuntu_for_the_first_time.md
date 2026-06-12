---
title: "Installing Ubuntu for the first time"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by Glenstr on 2011-06-03
My hardware is just over a year old, Dell i7 920 64 bit with 12Gb ram, and I partitioned off 500GB right away with the thought of putting a linux distro on it to dual boot with the Windows 7 OS.  I haven't had a linux distro on any of my home PC's since Suse (7 or 8?) quite a few years ago, and after some reading up on them I have decided to go with Ubuntu Studio, since I am doing a lot of video editing these days. 

Right now I am looking at my options for installing, I am assuming that if I install it by booting from the dvd, it should install itself on the partition I have reserved for it and it will set up dual boot using it's own interface ok? IIRC this is the way my last linux install went, and it worked pretty good, I think it installed GRUB. 

Is this a correct assumption? Or should I be doing it differently? 

I was also wondering if it was possible to set it up on its own physical partition, but also have the option to boot it in a virtual machine from windows 7 (or vice versa) - is this also doable? Or do I have to do the entire install from within a virtual environment?

What I would like to have is to be able to jump from one OS desktop to another as seamlessly as possible, but if that is not possible then I will settle for the old dual boot option. 

thanks!

---

### Post by Quackers on 2011-06-03
Is your partition for Linux formatted?
Which version of Ubuntu do you intend to install?
If you install Ubuntu on its own partition you will need to reboot to run Windows.

---

### Post by Joe of loath on 2011-06-03
Technically it is possible to run your Windows install in a VM in Ubuntu. However, you'll have to find some way of disabling the WGA tool, as it will detect the change in hardware, assume you've cloned the hard drive into another PC (You know, that well known piracy technique), and give you three days to renew the license. If you do that, when you boot back, it'll do the same thing all over again...

---

### Post by Glenstr on 2011-06-03
> **Quackers said:**
> Is your partition for Linux formatted?
Which version of Ubuntu do you intend to install?
If you install Ubuntu on its own partition you will need to reboot to run Windows.

I am installing Ubuntu Studio 11

Partition is not formatted yet, I was going to let the Ubuntu install format it, I realize I will have to reboot it to run windows, I guess what I was wondering was is it possible to run an OS that resides physically on a disk as a VM from another OS?

I am still trying to decide whether to do the physical install of ubuntu or install it as a VM from within windows 7 using a vm platform like virtual box.

---

### Post by Quackers on 2011-06-03
Yes, you can run Ubuntu in a VM from within Windows - or vice-versa.
It is certainly an option to let the installer format the partition(s) although some prefer to create the partition(s) first then choose the manual option in the installer to give the proper mount points.

---

### Post by oldfred on 2011-06-03
Not sure what version of Ubuntu studio is based on but 10.10 has poor instructions that make it very easy to overwrite entire drive. Fixed in 11.04. But I like better control over partition sizes and at least a separte /home and/or a shared NTFS partition if dual booting with windows. So I recommend manual partitioning.

Some examples of installs and issues with 10.10:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration

---

### Post by Glenstr on 2011-06-03
> **Quackers said:**
> Yes, you can run Ubuntu in a VM from within Windows - or vice-versa.
It is certainly an option to let the installer format the partition(s) although some prefer to create the partition(s) first then choose the manual option in the installer to give the proper mount points.

I have admit I'm not totally up to speed on how the various VM's work, and I'm still wondering whether either of the OS's this way is a viable option or if I should just go with a dual boot setup and be done with it. 

On the shared NTFS partition, I just put in a 2nd 2 TB drive that I plan on using for data only, so this can be the data repository for the linux OS as well.

---

### Post by Joe of loath on 2011-06-03
VMs are alright for testing, but IMHO a pain to do any real work in, besides occasionally firing up IE or something. You won't get any video acceleration, and the overheads will slow the VM and the host system.

I'd say only use a VM if you NEED both OSs on at once.

---

### Post by Glenstr on 2011-06-03
> **Joe of loath said:**
> VMs are alright for testing, but IMHO a pain to do any real work in, besides occasionally firing up IE or something. You won't get any video acceleration, and the overheads will slow the VM and the host system.

I'd say only use a VM if you NEED both OSs on at once.


Good point - In reading through this thread again, I don't think I have been very clear. What I really want, is a dual boot setup so that I can use either OS  "standalone" on the PC, but I'd also like to have the ability to jump into the other OS from time to time, mostly for minor things as you point out, and can I use/access the existing physical installs through VM's, or do they need to be installed on their own VM's from the host OS.

(not sure if that's any clearer or not..:confused:)

---

### Post by Joe of loath on 2011-06-03
VMs in windows won't be able to boot your Ubuntu partition, as Windows can't read Linux disks. Ubuntu will be able to boot your Windows one in a VM, but only if you much about with WGA. Make sure you do that /before/ you key your license number in, or it might be rendered useless ;)

A Linux machine will be able to run other Linux partitions in VMs fine, but that's not what you're asking for :p

---

