---
title: "Newbie install/Update nightmare!"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by fuzzbuzz85 on 2008-09-04
Hi, I'm super new to Ubuntu and linux, and I'm having the following problems:

1 - Used to run a copy of Windows that I accidentally tried to update, and basically the OS stopped working, so I took the opportunity to switch to Linux (rescuing my files with Knoppix and putting them safely away on an external HD)

2 - I installed 7.10, although it didn't seem to install fully as I had lots of problem with getting the wireless going, and when 8.04 came out it wouldn't show the updates. So, since I hadn't replaced my files I just figured I'd do a fresh install. Then I got all the errno 5 messages which are mentioned on other messages, even though I've tried a variety of discs, mirrors, burned them at a low speed and so on. 

3 - SO, I try to install 7.10, which throws the errno5 problem even though I had previously installed from that disc. I try the text based installer for 8.04, which throws an error on the install part, and I even tried the mini-installer, to no avail.

4 - Next, I have gone back to Feisty Fawn, intending to update to Gutsy then to Heron. Fawn installed ok, but now with the 211 updates I'm getting the following problems:

-- each time I try to install the updates I get errors, which have so far been:
Occasion 1: 
E:/var/cache/apt/archives/openssl-blacklist_0.3.3+0.4-0ubuntu0.7.04.2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/openssl-blacklist/blacklist.RSA-2048')

Occasion 2:
E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu6_all.deb: corrupted filesystem tarfile - corrupted package archive

E: /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu6_i386.deb: corrupted filesystem tarfile - corrupted package archive

-- Each time I try again there are fewer packages to install, but it told me that I have a varying number of broken dependencies each time (!)

So here's my system specs which I got with sudo lshw, but tell me if you need to know anything else - I'm not sure what's useful!

-core
       description: Motherboard
       product: 8363/A-686A
       physical id: 0
       slot: BANK_3

*-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB

partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 147GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1474MB
                      capacity: 1474MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1474MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: FUJITSU MPE3204AT
                   vendor: Fujitsu
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: ED-03-04
                   serial: 05023683
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 18GB
                      capabilities: primary
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      size: 855MB
                      capacity: 855MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hdb5
                         capacity: 854MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4120B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: A102
                   serial: K3246394029
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc



So here are my questions:

Why does ubuntu loathe my computer?! 
Why am I having so many problems upgrading?
Is there something wrong with the way my disks are partitioned? This time I used the entire master disk (the 160G), but I've tried a gazillion different ways of partitioning both of them.
Help!

Thanks!

---

### Post by Peter09 on 2008-09-04
I suspect that you have a hardware error mixed up in there somewhere. Are all the errors being generated from reading the CD drive?

---

### Post by slaminsamin on 2008-09-04
Hi; first of all, congratulations on getting rid of windows; blame all your problems on some vestige of that.

Peter09 suggested you may have a hardware problem in there.  Were there any signs of hardware problems before?  Could your windows problem have been a hardware problem in disguise?  Not knowing your circumstances you may want to employ a cd startup disk and run some hardware diagnostic packages as a first step.  You can do this off the live cd.

If you eliminate hardware problems then you may be looking at some vestige of previous installs which may be stumping the installer.  Since you are able to "start over" (ie all files off on ext disk) why don't you try a disk reformat and clean install from the live cd.  Let the installer do the partioning.  If that works then problem solved.  You can always go back and re-partition or re-install with manual partitioning once you've eliminated vestige files or disk errors.

Out of curiosity, what do you gain from installing back releases of Ubuntu?  8.04 is LTS.  Why not start there?

LOLuck

---

### Post by Sef on 2008-09-04
When you run the Live CD, do you have any problems?

---

### Post by Partyboi2 on 2008-09-04
> Occasion 1: 
E:/var/cache/apt/archives/openssl-blacklist_0.3.3+0.4-0ubuntu0.7.04.2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/openssl-blacklist/blacklist.RSA-2048')

Occasion 2:
E: /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu6_all.deb: corrupted filesystem tarfile - corrupted package archive

E: /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu6_i386.deb: corrupted filesystem tarfile - corrupted package archive
Open a terminal (Applications>Accessories>Terminal)
and try
```
sudo apt-get clean
```
then
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by slaminsamin on 2008-09-05
null

---

### Post by fuzzbuzz85 on 2008-09-05
Hi guys,

first of all a massive thank you for your replies, they're really helpful and it's great to get some support! I am definitely glad to see the back of windows, even if this is taking ages to get going! Feisty is now letting me upgrade to Gutsy, so we'll see how it goes. I've never had any hardware problems before, and I definitely think the windows problem was due to an upgrade from the internet. I like the theory that these problems have been caused by so many attempted upgrades and installs, so if this step-wise upgrade to Hardy doesn't work I'll definitely try the format-and-start-over idea, after checking my hardware. So basically I'll have another bash and let you know how I get on! Thanks again!

PS: Got the back releases idea from another post from the errno5 thread. I started all this before Hardy was released, which is why I started with Gutsy, then went back to Feisty because that was the only one which would install without failing! Really hope the errno5 thing is sorted for the next release... and that I'll be on Hardy by then so I can just do a lovely update without a fresh install!

---

### Post by fuzzbuzz85 on 2008-09-06
Right, since I last messaged I tried the following:

Upgrading from Feisty to Gutsy this time didn't work, with a load of errors coming up when I tried the upgrade part.

In the live CD I tested the hardware, which appeared to be fine, and I also ran memtest86+, in which everything passed, so does that mean my RAM is ok?

Anyway, I deleted all the partitions on my hard drives using gparted, and then tried to install from the live CD (which is an official one I bought, so it really *should* be ok!), then I got errno5.... AGAIN!

So my question now is: What else can I attempt? I really want to get this sorted because it's been going on far too long and I've got to actually use my computer for my course!

(I've already attempted: live cd; upgrading from a previous distro; alternative install; mini install)

Cheers x

---

### Post by fuzzbuzz85 on 2008-09-06
I forgot to mention: I haven't had any problems with the live cd at all, and I've checked them all!

x

---

### Post by fuzzbuzz85 on 2008-09-24
Hey,

I finally solved this problem by

- wiping the hdd
- making the smaller hdd the master
- making sure all of the cables were properly plugged in
- trying again

... not sure which of those steps worked, but I'm finally off the live cd and have managed to install!

Woohoo! Thanks for your suggestions

x

---

### Post by Peter09 on 2008-09-24
Congratulations

Well done

---

