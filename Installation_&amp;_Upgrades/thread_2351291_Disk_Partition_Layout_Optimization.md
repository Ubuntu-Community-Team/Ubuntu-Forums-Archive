---
title: "Disk Partition Layout Optimization"
date: 2017-02-01
forum: Installation &amp; Upgrades
---

### Post by attilatello on 2017-02-01
Hello all! This is my first post, please excuse if not doing it right.

I'm a returning Linux user from long time ago (Linux from Scratch) and I'm running *Ubuntu 16.04 LTS* as main and single OS on a 8Gb RAM (7,6 GiB) laptop machine.
Everything works great, but I'm a kind of update and semi-optimization freak... however, don't have the time to completely optimize it as I wish.

That said, my question is: I have this **120GB SSD** layout:

$ df -h

[TABLE="width: 500"]
[TR]
[TD]**Filesystem**[/TD]
[TD]**Size**[/TD]
[TD]**Used**[/TD]
[TD]**Avail**[/TD]
[TD]**Use% **[/TD]
[TD]**Mounted on**[/TD]
[/TR]
[TR]
[TD]udev[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: center"]0%[/TD]
[TD]/dev[/TD]
[/TR]
[TR]
[TD]tmpfs[/TD]
[TD="align: right"]778M[/TD]
[TD="align: right"]9,5M[/TD]
[TD="align: right"]769M[/TD]
[TD="align: center"]2%[/TD]
[TD]/run[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD="align: right"]106G[/TD]
[TD="align: right"]73G[/TD]
[TD="align: right"]29G[/TD]
[TD="align: center"]72%[/TD]
[TD]/[/TD]
[/TR]
[TR]
[TD]tmpfs[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: right"]38M[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: center"]1%[/TD]
[TD]/dev/shm[/TD]
[/TR]
[TR]
[TD]tmpfs[/TD]
[TD="align: right"]5,0M[/TD]
[TD="align: right"]4,0K[/TD]
[TD="align: right"]5,0M[/TD]
[TD="align: center"]1%[/TD]
[TD]/run/lock[/TD]
[/TR]
[TR]
[TD]tmpfs[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: right"]0[/TD]
[TD="align: right"]3,8G[/TD]
[TD="align: center"]0%[/TD]
[TD]/sys/fs/cgroup[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD="align: right"]511M[/TD]
[TD="align: right"]3,6M[/TD]
[TD="align: right"]508M[/TD]
[TD="align: center"]1%[/TD]
[TD]/boot/efi[/TD]
[/TR]
[TR]
[TD]tmpfs[/TD]
[TD="align: right"]778M[/TD]
[TD="align: right"]96K[/TD]
[TD="align: right"]778M[/TD]
[TD="align: center"]1%[/TD]
[TD]/run/user/1000[/TD]
[/TR]
[/TABLE]


...and I wish to create new partitions to hold the **/home** and, eventually, other *Ubuntu* versions for evaluation purposes. Also, I wonder if would benefit shrinking some of these partitions. Perhaps would be important to say I update minor versions of kernel frequently (looking at **/boot/efi** partition for some reason).

Any ideas or suggestions on how to achieve it?

Thanks!!

---

### Post by ajgreeny on 2017-02-01
This is obviously a UEFI system so the number of partitions you can create is unlimited in practical terms.
However with an SSD of 120GB only you will be a bit limited in space available; your current root partition of 106GB has only 29GB available and free.

What spec machine do you have as I presume you must have quite a large swap partition using space on the disk, or do you have another disk in the machine, and could that be used for the data files that are currently in your home folder?

With 8GB RAM you can probably manage with only 2 - 4 GB swap unless you need to hibernate when you must have as much swap as RAM.
Either way you will not have much avaiolable space to allow you to make partitions for root of other OS versions, as you really need about 20GB for each root partition to be sure there is sufficient space to run well and currently you have space available for only one further root partition.

Don't forget that if you separate out /home as a partition that will need to have at least 10% free space to allow it to work properly, as will the root partitions.  You probably have approx 63GB of files in your home folder, assuming root generally uses about 10 GB or maybe more depending on how you use the OS.

To sum up:-
[LIST]
[*]You could separate home as a partition, but you would need to be careful not to shrink root too far.
[*]I would leave the EFI partition alone as it uses only a small amount of space.
[*]I suggest that a separate physical disk for the data files currently in home might be a good idea.
[*]Any partition edits must be carried out using a live system as you can not work on any mounted partitions; gparted is the easiest application to use in a live system to do this.
[/LIST]

---

### Post by oldfred on 2017-02-01
I prefer to use 25GB for / (root) and have a separate /mnt/data partition for all my data.
And then I can have as many / as I can fit, but mount same data in all of them. I usually do not want same /home as I do not want same configuration, as I may want to test different settings and do not want to mess up my main working LTS install.

I normally now use just desktops, and have SSD for booting & HDD for data (and even more / if desired, but at least one / on every drive.

I normally suggest 300 to 500MB for the ESP - efi system partition. But that is more for future and if you want to experiment with alternative boot managers or UEFI direct boot.
Windows uses 100MB for ESP and even with Ubuntu's /EFI/ubuntu folder added is it not near full. I use 100MB if installing to a small drive like my 32 or 64GB flash drives.

---

### Post by attilatello on 2017-02-01
Thanks both for the replies! Actually, the HD size isn't much of an issue to me because I use this laptop mainly for some development with NetBeans and leisure time surfing the net - no games or large programs.

 There isn't much free available space because, at this moment, I have some virtual machines on it (which can be moved to an external drive soon) - so feel free to assume I can manage to free up about 60GB extra space. I've read somewhere that each install should have *at least* about 20GB, but I'm not so sure about it - EDIT: Just read again [COLOR=#C61919]**ajgreeny**[/COLOR] post, so it is confirmed :-D -  also read that swaps on SSD disks for computers with enough RAM wouldn't be as much needed, actually, some say it should be used less possible to extend HD life. 
I like the idea of creating a /data partition to share between installations and not messing the main installation, so probably not a good idea to share the /home as I thought! 
Also, thanks for the GParted tip, I was wondering if UDisks could do the task without a live CD!

---

### Post by ubfan1 on 2017-02-01
Since you want to evaluate other Ubuntu releases, here's a thought:  Increase the EFI partition to 10-11G (FAT) and add directories like A, B, C, etc. to hold 2-4G casper-rw files.  You can then download the new ISO, and specify a path to the casper-rw file to boot it with persistence.  Adding the "toram" to the boot makes a very quick ram-based system with persistence.

---

### Post by attilatello on 2017-02-01
Thanks, [[COLOR=#000000]ubfan1[/COLOR]]("https://ubuntuforums.org/member.php?u=1256996")! I'll educate myself a little more to better understand your suggestion... I'm not completely new to Linux, but I haven't use it for a long time - there are lots of stuff to remember and new things to learn :-)

---

### Post by ubfan1 on 2017-02-01
Below is an example ISO boot to add to /etc/grub.d/40_custom.  I have one FAT formatted partition, which gets found automatically. It has a directory /X containing my casper-rw file (initially an empty etx2 file).  The ISOs are on a big data partition (sda12) with a link, bootit.iso, pointing to the one I am testing.  Change the sda12 to be the partition you use (it doesn't matter where is it mounted -- mine is mounted at /usr/local/vm, so the bootit.iso link is at /usr/local/vm/bootit.iso, pointing to some ISO in a directory.  Once set up, you just have to change the link (and reset the casper-rw file) to boot another ISO, the grub file does not need to be changed.
Put in /etc/grub.d/40_custom and run sudo update-grub to get it into the grub menu:

menuentry "Some Ubuntu ISO" {
        # bootit.iso is a link to an ISO in a directory on an ext4 partition.
        # A link lets you change the ISO without needing to change this file.
        # The path is relative to the partition, not wherever it may later be mounted.
        set isofile="/bootit.iso"
        # Change the disk and partition to identify where the ISO is located.
        set diskpart="(hd0,12)"
        # On a FAT32 partition, you may have a persistent file for some system changes -- uncomment if wanted.
        # Disk identifiers seem to be ignored to identify the FAT32 partition with the persistence file.
        # Use a unique path for the persistence file. Sadly, seems you cannot use an ext4
        # filesystem for the persistent file.  Keyword order of "persistent persistent-path" is critical.
        set persist="persistent persistent-path=/X"
        loopback loop ${diskpart}$isofile
        #  persistent casper-rw file must be on a FAT partition to be seen.
        # and as of 3/23/2015, using both persistent and toram still cannot shutdown cleanly.
        # leaving casper-rw unclean, but working.
        linux (loop)/casper/vmlinuz.efi boot=casper $persist iso-scan/filename=$isofile toram noprompt noeject
        initrd (loop)/casper/initrd.lz
}

---

### Post by oldfred on 2017-02-02
I have used the ESP for an ISO, but normally use a separate partition on drives where I have lots of space.
Getting path correct is one of the bigger issues of getting grub to loopmount an ISO. And if using multiple drives, you are using device in these examples and I find flash drive often added to middle or beginning of device order, so sometimes I have to manually edit the hdX as I boot to have correct drive.
And my sdb HDD was hd2 as DVD was hd1. I then changed SATA port order to resolve that.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by attilatello on 2017-02-03
Again, thanks all for the replies!

For testing purposes, I guess ISO might be a good option (maybe for another thread, but wouldn't it be slower and restrict my hardware options?)... however, to be honest, I guess I didn't tell exactly what I had in mind when I started this thread, perhaps I didn't know at the time, but now I think I got it! I'm planning on install the non-LTS version on this machine and use it until end of life, but to be safe, I'll also want to keep the LTS as main installation. I don't think I'll need to test too many different distros - just a little curiosity about Kali, but indeed I wish to keep using Linux for longer period this time - and Ubuntu is my choice - therefore, perhaps would be nice to use another partition to make clean installations, if needed, and keep the disk in a good maintenance structure (that's why I'm worried with my small SSD disk optimization).

Hope I didn't waste your time, surely gave me some new knowledge and I'm grateful for that! Not sure if I should set it as solved, I'll come back later to do it if needed. Thanks!

---

