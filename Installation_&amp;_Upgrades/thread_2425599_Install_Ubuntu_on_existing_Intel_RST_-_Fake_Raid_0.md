---
title: "Install Ubuntu on existing Intel RST - Fake Raid 0"
date: 2019-08-27
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2019-08-27
Hello,

i am running the live usb but it cannot see the filesystem where i want to install ubuntu. lspci recognizes the RAID controller though:

```
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
```

but mdadm cannot recognize the array

```
ubuntu@ubuntu:~$ sudo mdadm --detail-platform
       Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels : raid0 raid10 raid5
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port1 : - non-disk device (MATSHITA BD-CMB UJ172 S) -
          Port0 : /dev/sda (WCC313X5)
```

The two 512gb nvme ssds are not listed. I want to run Ubuntu alongside Windows 10 on the fake RAID 0 (I need a big and fast cache). I do not want to downgrade to AHCI. How can i overtake the existing RAID? Should i use mdadm?

```
ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically
```

---

### Post by oldfred on 2019-08-27
Is it really RAID or just Intel RST?

       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

### Post by docdoc2 on 2019-08-27
It is Intel RST. I didnt know it had no effect on the read/write speeds. In the BIOS it is called RAID and when i disable it, i end up with two nvmes with 512gb each, but for the cache of my program one drive with 1tb would be better, and i read somewhere that Intel RST also works with Linux. Or is is discouraged to use it for dual boot?

---

### Post by oldfred on 2019-08-27
I have seen many disable it, but not those with RAID 0 unless they totally backup system and restore to just one drive. Half of data is on one drive and half on other. 
Often used for hard drives to speed things up, but only for systems that had daily backup or pulled all data from server. Not really recommended for standard desktops.

Do not know RAID, and if this applies or not:
       How to install Ubuntu  64-bit with a dual-boot RAID 1 partition on an UEFI/GPT system?
[http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi](http://askubuntu.com/questions/660023/how-to-install-ubuntu-14-04-64-bit-with-a-dual-boot-raid-1-partition-on-an-uefi)
Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by docdoc2 on 2019-09-08
I know about the dangers, but i want to do it nevertheless. Anyone an idea how ubuntu can initialiaze the existing RAID 0? i read that mdadm is better than dmraid, is that right? But as stated above, mdadm cannot see it.

---

### Post by docdoc2 on 2019-09-23
Has anyone an idea? Accordign to the Intel manual it should work with Linux[ https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/rst-linux-paper.pdf]("https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/rst-linux-paper.pdf")

and appaerently the two nvme drives are being recognized:

```
ubuntu@ubuntu:~$ dmesg | grep -i nvm
[   15.279502] ahci 0000:00:17.0: Found 2 remapped NVMe devices.

```



 [URL="https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/rst-linux-paper.pdf"]

[/URL]

---

