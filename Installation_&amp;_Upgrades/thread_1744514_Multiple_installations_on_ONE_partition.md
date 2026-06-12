---
title: "Multiple installations on ONE partition"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by James Haigh on 2011-04-30
I've had enough of partitions. I have one for /home, 3 or 4 for various distros, and one for swap. It is rigid and difficult to adapt to varying disk usage. I'm currently finding it very difficult to upgrade all my machines to Natty. I want to avoid this problem in the future.

I would like to have an EXT4 partition like this:

```

/
    home/
        james/...
        ...
    Ubuntu_11.04/
        bin/...
        boot/...
        cdrom/...
        dev/...
        ...
    Ubuntu_10.04/...
    Arch_Linux/...
    lost+found/...

```

This cleans up the root directory, and makes it easy to see what distros are installed.

I want to be able to move existing installations into this system.

Thank you.
James.

---

### Post by dino99 on 2011-04-30
wow, ready to built your own custom distro ? with new homemade installer ? rebuiding all the conf files ?

Good Luck :)

---

### Post by srs5694 on 2011-04-30
There are at least three ways to do what you want, or something close to it:


[list]
[*]Use the chroot command to change from one distribution to another. This is the solution that's closest to what you describe, but AFAIK few distributions support directly installing in this way; thus, you might need to use some temporary medium (perhaps even a USB flash drive) to install your distribution, then copy everything over. [This page](http://www.togaware.com/linux/survivor/ChRoot_Multiple.html) describes the basics of this approach. Note that I've never attempted this in any serious way, so I can't be of further assistance on doing it.
[*]Use VirtualBox, VMWare, or some similar virtualization tool to run virtualized instances of all but one OS. This will require you to set up virtual disks, one for each OS, and you'll lose some performance in the virtualized OSes; but a lot of people know how to do it.
[*]Instead of using regular partitions, use a [Logical Volume Manager (LVM)](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) configuration. You can then multi-boot much as you would with partition-based installations, but logical volumes are much more flexible than are conventional partitions; they act more like files in a filesystem, so you don't need to worry about moving partitions around to consolidate your available space, for instance.
[/list]


Each approach has its advantages and disadvantages. An LVM gives each distribution full access to the hardware, including running its own native kernel, for instance; but you'll only be able to run one OS at a time. Using chroot enables you to run programs from multiple distributions simultaneously and provides seamless memory and disk management; but some features, such as the kernel, will be provided by just the one "master" distribution. Virtualization lets you run multiple distributions, including their own kernels and desktop environments, simultaneously; but it requires you to segment your memory and the virtualized OSes won't have full access to the hardware.

In determining which approach is best, I think you need to ask yourself why you want to run multiple distributions. IMHO, typical desktop users don't need multiple distributions, except perhaps for short-term evaluation purposes. If you need them to test software you're writing or for some other professional purpose, the details may help you decide which approach to take.

---

### Post by James Haigh on 2011-05-02
dino99: I'm well aware that this is a difficult challenge, but I'm going to give it a very good try.

srs5694: Thank you for your suggestions.

I think chroot is the closest to what I'm looking for. I am going to explore it. I think it'll at least give me some clues. The problem is, I don't want to /change/ root, I want root to /start/ in different location such as /Ubuntu_11.04/.

LVM may be more flexible, with the ability to fragment partitions to avoid moving them, but resizing logical partitions is just as risky if there is a power failure. I'd much prefer one partition only. I find partitions a big nuisance for many reasons.

Virtualisation is a solution to a different problem. I'm interested in exploring Xen, but that's a different topic.


I've been experimenting. I have an installation of Natty. I moved all of the directories except lost+found out of root into /Ubuntu_11.04/. I made a symlink to /Ubuntu_11.04/boot/.

I restarted the computer. Grub worked fine. I then experimented with different parameters. I could not make it boot.

I moved stuff back so it boots again.


One idea would be to make a hardlink to each directory in /Ubuntu_11.04/ (or other distro) in some on-the-fly manner on boot.


Alternatively, if 'root' was /Ubuntu_11.04/ in some chroot-like manner, how would the system access /home/ if it's in the partition's root?


This would be very useful to get working properly.

Apparently Mac works like this. It is possible to install multiple versions of Mac OS or Mac OS X on the same partition. I think each installation has a 'System folder'.

Thank you.
James.

---

