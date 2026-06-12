---
title: "Dual Boot / RAID1 / Partitioning"
date: 2024-01-25
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2024-01-25
I am setting up a new machine where Ubuntu will be a webserver. Unfortunately, it has to have a Win10 install too. I am hoping for some advice about partitioning & setting up RAID1. The machine has a 1T drive where Win10 will install and two 0.5T drives that will form into a RAID1 array. I do NOT want the machine to boot from the RAID1 array. I would like as much of Ubuntu on the RAID array as possible. My plan is to use GPT partitioning make 3 partitions on the 1T drive:
[INDENT]One for Win10
One for Linux backup
One for SWAP[/INDENT]
I would like to have just one partition on the RAID1 array and mount it as "/" but not sure if this will cause the machine to boot from the RAID1 array. 

Is my understanding that boot information will remain on the 1T drive correct?
Will I need an alternative Ubuntu install iso to do this or will the normal GUI install iso let me set up RAID?
Thanks in advance for any replies.
Scott

---

### Post by TheFu on 2024-01-25
**Don't dual boot.**

Run a virtual machine for the OS that doesn't need too much GPU. That is probably Linux since a web server doesn't need any GPU at all.  There is no GUI for RAID on Ubuntu.

By doing using virtualization, you've completely removed the Linux RAID question and are left with MS-Windows RAID questions, which I suspect you can get help with elsewhere.  Also, you can run both OSes concurrently and keep your web server up, as long as the host OS is booted.

To the virtual machines, there wouldn't be any knowledge of the underlying physical storage. It wouldn't know that it is RAID1 or RAID50 or RAID60 or whatever RAID level you pick. It would only see the storage and access it through a virtual device.  Hopefully, you'd choose a "virtio" device for both storage controller and network controllers. These are the most efficient and extremely well supported by all Linux OSes.

The hypervisor you use is completely up to you and your skills. I understand that Windows has a few options, but haven't used MS-Windows as a VM host in over a decade.

Using a single partition for an entire OS is a bad idea, BTW.  Especially for Linux.  There are security implications that become important, especially for a web server that might be available over the internet.  Restrictive mount options are part of web-server security.

---

### Post by SBFree on 2024-01-25
Thanks, this gives me food for though.
Windows gets little use and from what you've suggested, I should make that run in a VM
I have read that using a mdadm created RAID drive as a boot device is a bad idea.
Where are suggestions for mount options that are good for web servers?
From you 'bold comment' about Dual Booting, what is it's downside?
Thanks again
s

---

### Post by TheFu on 2024-01-25
A web search found these links, to start:
[LIST]
[*][https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html](https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html)
[*][https://www.stellarinfo.com/article/risks-with-dual-booting-operating-systems.php](https://www.stellarinfo.com/article/risks-with-dual-booting-operating-systems.php)
[/LIST]

If booting is controlled by more than 1 OS, each OS will try to manage the boot files. This can turn out really badly, especially when one OS maker acts like they are the only OS in the world.  This can lead to 1 OS wiping the ability to boot from the other OS. Of course, which will happen when it is 100% convenient and you aren't in any hurry, since that's how computers always work. They never break with we really need them to work, not ever.

Disk layouts and mount options are different based on the system, what it does, what the admin understands, and what the attack vectors are.  Only you can decide if using non-default settings and partitions are worth the hassle.  I've posted my disk layouts in these forums multiple times.  I use LVM to help manage storage for greater uptime, greater flexibility and greater security.  If you don't know and aren't interested in LVM, then only you can decide if learning that is useful.  I cannot imagine running a physical server without LVM.  Inside a virtual machine, I use LVM about 50% of the time, just depends on what the machine is doing and how much total storage it will have.  For little VMs that do mostly processing, but don't have data, LVM isn't really needed.  OTOH, for servers with more than a few hundred GB of storage, I'm going to add LVM for the flexibility it provides.  Plus, my hypervisor understands LVM, so it makes storage tasks pretty easy for a VM if I've setup LVM on the host system. 

Here's a taste, grouped by VG, of a VM host system.  Think of each LV as a partition.
```

$ sudo lvs |sort -k2
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  plex_varlib       istar-8TB-B    -wi-a-----   90.00g                                                    
  jellyfin_varlib   istar-8TB-B    -wi-a-----   90.00g                                                    
  lv5_back          istar-8TB-B    -wi-ao----    3.43t                                                    
  lv4_back          istar-8TB-B    -wi-ao----    3.63t                                                    
  istar-back3-b     istar-8TB      -wi-ao----    3.62t                                                    
  istar-back3-a     istar-8TB      -wi-ao----   <3.65t                                                    
  lv-tv             istar-stuff    -wi-a----- <298.09g                                                    
  lv_media2_back    istar-vg2-back -wi-ao----   <3.64t                                                    
  lv_media2         istar-vg2      -wi-ao----   <3.62t                                                    
  lv_media3_back    istar-vg3-back -wi-ao----    3.63t                                                    
  lv_media          istar-vg       -wi-ao----   <3.54t                                                    
  ubuntu2204-srv    vg00           -wi-a-----   15.00g                                                    
  ubuntu22.04-srv-2 vg00           -wi-a-----   15.00g                                                    
  lv-tv             vg00           -wi-ao----  100.00g                                                    
  lv-xen41-1804     vg00           -wi-ao----   12.50g                                                    
  home              vg00           -wi-ao----   26.00g                                                    
  lv-blog44         vg00           -wi-ao----   30.20g                                                    
  root-00           vg00           -wi-ao----   35.00g                                                    
  lv-zcs45-1804     vg00           -wi-ao----   35.00g                                                    
  Mint21.1          vg00           -wi-ao----   40.00g                                                    
  swap              vg00           -wi-ao----    4.10g                                                    
  lxd               vg00           -wi-ao----   50.00g                                                    
  var               vg00           -wi-ao----   55.00g                                                    
  lv-vpn09-2004     vg00           -wi-ao----    7.50g                                                    
  jellyfin          WDBLK_8T       -wi-ao----   20.00g                                                    
  lv_d6             WDBLK_8T       -wi-ao----    3.60t                                                    
  lv_d7             WDBLK_8T       -wi-ao----    3.60t                      

```
vg00 is an SSD and where the OS being run sits.  Different virtual machine storage is in vg00 - 1 LV per VM.  Any LV over 50G is for data, most likely.  Much of that storage is for backups - about 50%.

I run a VPN server. It has 7.5G of storage, since it doesn't actually hold any data.  The LV, lv-vpn09-2004, is the entire storage allocated to it.  From inside that system, the storage looks like this:
```
$ lsblk 
NAME    SIZE TYPE FSTYPE MOUNTPOINT
vda     7.5G disk        
&#9500;&#9472;vda1    6G part ext4   /
&#9500;&#9472;vda2    1K part        
&#9492;&#9472;vda5 1021M part swap   [SWAP]
```

and
```

$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4  5.8G  4.2G  1.4G  76% /

```
No LVM being used. In early 2025, I'll move this VPN to 24.04 or Debian 12. We'll see. It has 20.04 currently.

Depending on risk factors, I'll choose a VM over a Linux Container. Just depends on what the system does, use will have access and how risky I deem it to be. It is a judgement call. My choices are based on 30 yrs experience as an admin.  300+ data points were considered in the decision and none of them were written down. Sorry.

---

### Post by SBFree on 2024-01-26
This post is very helpful and I appreciate your spending the time. I am in the stage of not knowing what I don't know. I am not sure I would have been able to start searching for securing mount points without your help. The only other 'server' I built is not more than 10 years old and a lot has changed. My past experience tells me that a bit of work and learning at the beginning will save me headaches in the future. Thanks again.
scott

---

### Post by TheFu on 2024-01-26
Controlling mount options to aid with security isn't really new. It has been done since before I started using UNIX 30+ yrs ago. It is a normal technique.
If you really want to learn to think different, "Real World Linux Security" is a book on the subject by Bob Toxen.  Just as relevant today as it was in 2002. Obviously, the detailed commands will have changed, but the ideas haven't.  Might be able to get it for $5 at a used bookstore.  Doesn't hurt to look if you are browsing.

---

### Post by MAFoElffen on 2024-01-28
> **SBFree said:**
> Thanks, this gives me food for though.
Windows gets little use and from what you've suggested, I should make that run in a VM
[COLOR=#ff0000]I have read that using a mdadm created RAID drive as a boot device is a bad idea.[/COLOR]
Where are suggestions for mount options that are good for web servers?
From you 'bold comment' about Dual Booting, what is it's downside?
Thanks again
s
Hmmm. I've been doing dual-boots for 19 years now... For Desktops. Servers are not something you dual-boot.

Since Windows 10 does not get much use, why not run Ubuntu Server as a KVM Host, then run Windows and your other Servers as VM Guests?

I don't know where you read that RAID, (whether mdadm, LVM2 RAID or ZFS RAIDZ) should not be as a boot device. That sounds like from someone that never worked in the commercial world. RAID has been an industry standard for much too long already. It is a thing for commercial pursuits. It is overkill for private use.

Going into the history of RAID, it came about for cost effectiveness, because you could combine many smaller disks together as a larger storage space a lot cheaper than buying larger disks. Then it was found that striping across those disks made things faster. Then mirroring and striping made things more secure because you had fault tolerance it a disk or an allowable number of disks failed. Not relying on that for anything beyond that, because backups are the way to restore lost files.

I have created bootable RAID Arrays and had no problems. More leaning towards the other side of that. But I started with hardware RAID. Then moved to mdadm. Then LVM2 RAID. Now ZFS RAID2 & DRAID. But I use them for the improve performance, ad I can lose 2-3 disks and go on with business, depending on the RAID type...

On the other-hand, I have also created systems that all raid was for Data, and the boot devices where just that. Just large enough to hold the bootable files and OS... and were considered as disposable, replaceable, plug & play pieces in the design. If it failed, pull out that drive and plug in another already setup for that, which mounted the data drives, and went on with business. Some of those systems actually boot from a RAM Disk or Flash Drive. It really didn't need more.

It depends on what you are doing, and the design of the system.

The important piece to take from that, is that RAID does not replace backups. That is not it's place or it's job. Do not assume that. You need a good backup and recovery plan that works.

As for mounts, that is subjective. I tend to design systems in a modular way, in a plan that looks towards, after time, things will change and evolve. Plan for ease of migrations to a newer release down the road. If you do that now, while putting it together, that will save you a lot of work when that day come around. I have many pieces that mount together as one system. Each piece is easily replaced.

Hint: Ask TheFu about how he sets up his KVM storage pools now, and how that has evolved over the years...

---

### Post by SBFree on 2024-01-28
Thanks again for the replies. I don't use RAID for backup. At a site called, The Center for Internet Security ([https://www.cisecurity.org/]("https://www.cisecurity.org/")), they suggest separate partitions for Ubuntu as follows:
/tmp
/var
/var/temp
/var/log
/var/log/audit
/home

Using LVM is a bigger jump for me at the moment so I would have to pick partition sizes if I don't. Any suggestions for how much space to allocate to /tmp & /var if I don't use LVM? I was going to use remaining space for /home as well as making a partition for backups.I am reading about LVM at 
[https://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html]("https://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html")
[https://linuxhandbook.com/lvm-guide/]("https://linuxhandbook.com/lvm-guide/")

Thanks again,
scott

---

### Post by MAFoElffen on 2024-01-28
> **SBFree said:**
> Thanks again for the replies. I don't use RAID for backup. At a site called, The Center for Internet Security ([https://www.cisecurity.org/](https://www.cisecurity.org/)), they suggest separate partitions for Ubuntu as follows:
/tmp
/var
/var/temp
/var/log
/var/log/audit
/home

Using LVM is a bigger jump for me at the moment so I would have to pick partition sizes if I don't. Any suggestions for how much space to allocate to /tmp & /var if I don't use LVM? I was going to use remaining space for /home as well as making a partition for backups.I am reading about LVM at 
[https://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](https://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
[https://linuxhandbook.com/lvm-guide/](https://linuxhandbook.com/lvm-guide/)

Thanks again,
scott
TheFu does similar using LVM VGs and LVs... As he can explain very well. He is very 'Security Aware'. Both he and I are fans of not allocating all we have at the start, so we can add space here and there as needed on-demand.

I have been around 'IT' for a very long time. (Longer than I like to admit) I think in broader terms. When someone says partitions or drives (Windows worlds), I think of the basic concept of using storage containers to separate things out. We are talking about the same things in concept, if you open up that understanding. When I taught Computer Science, that is how I taught that... To break it down into the concepts, and then how to apply those concepts into something workable. If you understand how something works, then you can make more things possible.

As starting out with concepts and best practices from long ago, and how that evolves over time and new technologies, I now use Volume Managers and what added value they provide in what I can do with them. TheFu and I have used LVM for about 24 years. I just recently, in the past 4 years, went back to using ZFS as my volume manager... But I have 19 years of experience with that.

I have recently created some hybrid LVM/ZFS systems, that I can use the pluses from each to leverage what I want to do. They are working out well, so far.

Using a Volume Manager makes things easier, manageable, and more flexible, while staying online, making those changes on a live filesystem. TheFu is still using LVM... But I think I have at least temped him enough into looking into it. (LOL) It has a steeper learning curve than LVM. Both add so much value in what they can add. Most only scratch the surface of what they can do.

That was the biggest drawback to mdadm RAID, and why I moved away from it. Changes had to be done offline.

---

### Post by TheFu on 2024-01-29
I will add this .... MAFoElffen is older than me. ;)  I spent about 5 yrs doing mainframe stuff before even starting with UNIX.  I did DOS, OS/2 and Windows programming professionally for about a decade with about 5 yrs of Unix programming overlap.

I use LVM on Linux.  In the early 2000s, I used ZFS on Solaris and my Linux desktop has ZFS on it, but not in any complex way.  See:
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    24G  8.4G   15G  37% /
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    15G  128K   15G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/var/games               zfs    15G  128K   15G   1% /var/games
rpool/USERDATA/root_5njgy6                       zfs    15G  384K   15G   1% /root
rpool/USERDATA/jp_5njgy6                         zfs    25G  9.7G   15G  40% /home/jp
rpool/ROOT/ubuntu_d0wbmk/var/log                 zfs    17G  1.5G   15G   9% /var/log
rpool/ROOT/ubuntu_d0wbmk/usr/local               zfs    15G  256K   15G   1% /usr/local
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    15G   27M   15G   1% /var/lib
rpool/ROOT/ubuntu_d0wbmk/var/snap                zfs    15G  128K   15G   1% /var/snap
rpool/ROOT/ubuntu_d0wbmk/var/spool               zfs    15G  4.7M   15G   1% /var/spool
rpool/ROOT/ubuntu_d0wbmk/var/www                 zfs    15G  128K   15G   1% /var/www
rpool/ROOT/ubuntu_d0wbmk/var/lib/AccountsService zfs    15G  128K   15G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d0wbmk/var/mail                zfs    15G  128K   15G   1% /var/mail
rpool/ROOT/ubuntu_d0wbmk/var/lib/NetworkManager  zfs    15G  256K   15G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0wbmk/var/lib/dpkg            zfs    15G   69M   15G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_d0wbmk/var/lib/apt             zfs    15G   94M   15G   1% /var/lib/apt
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  400M  1.4G  23% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi
```

My servers using LVM have much simpler layouts, which I've posted in these forums a few times, including some data in this thread.

And just to be clear, I haven't dual booted anything in about 13 yrs and I haven't dual booted a server in nearly 25 yrs.  Use virtualization. Avoid the stupid issues that dual booting causes.

---

