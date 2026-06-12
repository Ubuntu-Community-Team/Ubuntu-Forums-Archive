---
title: "Add LVM to 23.04"
date: 2023-08-13
forum: Installation &amp; Upgrades
---

### Post by dhotrum52 on 2023-08-13
SOLVED
Everyone suggested I keep trying. I don't understand what I just did but I followed a YT video EXACTLY and it works.
I hd 60 GB of data stored on a HD but I could not get at it. Lost it all.

Hi Guys, I have Ubuntu 23.04 with cinnamon installed and I want to add more drives. My primary drive is an SSD 500GB I want to add 2 SATA 500GB and THEN add a LVM.2 I have looked for software to do this but haven't found any. I watched one of those guys from India do what I want to do on the command line but I don't want to ruin what I have. Is there software or shall I just do what this guy says?
Thank You
Dave

As a suggestion from THEFU I will wipe and reinstall 22.04. I will get back and tell how that went.
Thanks Everyone

---

### Post by TheFu on 2023-08-13
LVM is all command line.  Good news is that LVM is LVM is LVM, it isn't distro specific for data areas.  Find any tutorial you like.  Setup a virtual machine and try some things out where it doesn't matter.  With LVM, whether you are playing with 10MB sizes or 10TB sizes, doesn't really matter.  Creating a 4TB file system on a 4TB logical volume takes less than 20 seconds. I did this just a few weeks ago.

Why would you run 23.04 at all?  I'm confused.  Support for that release ends in January. Hardly worth the effort.  Best to wipe it and load 22.04.
Here's a diagram for your consideration.  Ignore the LUKS encryption part.

Here's an LVM setup for 3 disks in a system here:
```
$ sudo pvs
  PV             VG       Fmt  Attr PSize    PFree   
  /dev/nvme0n1p4 vg01     lvm2 a--  <930.78g <690.68g
  /dev/sda1      vg-hadar lvm2 a--  <465.76g   36.00m
  /dev/sdb1      vg-rom01 lvm2 a--    <7.28t   <1.88t

$ sudo vgs
  VG       #PV #LV #SN Attr   VSize    VFree   
  vg-hadar   1   1   0 wz--n- <465.76g   36.00m
  vg-rom01   1   5   0 wz--n-   <7.28t   <1.88t
  vg01       1   7   0 wz--n- <930.78g <690.68g

$ sudo lvs
  LV                VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-backups        vg-hadar -wi-ao---- 465.72g                                                    
  lv-rom-data-1tb   vg-rom01 -wi-ao---- 200.00g                                                    
  lv-rom-data-r2    vg-rom01 -wi-ao----   1.50t                                                    
  lv-rom-export     vg-rom01 -wi-ao---- 200.00g                                                    
  lv-rom-misc-2tb   vg-rom01 -wi-ao----  <1.51t                                                    
  lv-rom-raid       vg-rom01 -wi-ao----   2.00t                                                    
  home01            vg01     -wi-ao----  10.00g                                                    
  libvirt-01        vg01     -wi-ao---- 137.00g                                                    
  lxd-containers-01 vg01     -wi-a-----  30.00g                                                    
  root01            vg01     -wi-ao----  35.00g                                                    
  swap01            vg01     -wi-ao----   4.10g                                                    
  tmp01             vg01     -wi-ao----   4.00g                                                    
  var01             vg01     -wi-ao----  20.00g                   

$ lsblk
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
sda                              disk                    465.8G                            
&#9492;&#9472;sda1                           part  LVM2_member       465.8G                            
  &#9492;&#9472;vg--hadar-lv--backups        lvm   ext4              465.7G  455.8G     1% backups     /Backups
sdb                              disk                      7.3T                            
&#9492;&#9472;sdb1                           part  LVM2_member         7.3T                            
  &#9500;&#9472;vg--rom01-lv--rom--data--1tb lvm   ext4                200G   61.2G    64% rom-1tb     /d/rom/Data/1TB
  &#9500;&#9472;vg--rom01-lv--rom--export    lvm   ext4                200G   66.5G    61% rom-export  /d/rom/export
  &#9500;&#9472;vg--rom01-lv--rom--misc--2tb lvm   ext4                1.5T   21.4G    94% rom-2tb     /d/rom/misc/2TB
  &#9500;&#9472;vg--rom01-lv--rom--data--r2  lvm   ext4                1.5T      1T    25% rom-r2      /d/rom/Data/r2
  &#9492;&#9472;vg--rom01-lv--rom--raid      lvm   ext4                  2T  216.9G    84%             /d/rom/raid
nvme0n1                          disk                    931.5G                            
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                            
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M    343M    42%             /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                            
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G     26G    19%             /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G   15.5G    15%             /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.6G     2% tmp01       /tmp
  &#9500;&#9472;vg01-home01                  lvm   ext4                 10G    3.9G    55% home01      /home
  &#9500;&#9472;vg01-libvirt--01             lvm   ext4                137G    2.8G    98% libvirt--01 /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01     lvm                        30G                        
```    

The NVMe device has the OS on it.  Setting that up happened BEFORE installation.  All the others were added post-install.

vg-rom1 is there after a lightning strike broke a computer I'd been planning to retire. It also took out the UPS protecting it, the GPU, RAID card, and an external RAID array. The HDDs in the external array seem fine, but I've been using them in a read-only degraded mode until the new hot-swap caddy arrives that will fit into another system.  

Oddly, no other computers or equipment seems to have been harmed. Don't know how that happened.  I think the UPS internals had an arc that cause shorts in specific plugs.  Just enough to fry electronics, but not total break stuff.  

Anyway, if you have specific questions about LVM, there is a bunch of expertise in these forums.  Ask, AFTER you've worked through a tutorial and read 10 other threads about LVM already here.  My main warning is that you shouldn't allow LVs to span across different disks unless you have excellent backups.  I did long ago, before I had backup religion and lost 80% of my data when 1 of 3 HDDs failed. Don't do it.

---

### Post by Dennis N on 2023-08-13
> Is there software or shall I just do what this guy says?

There is software, but Ubuntu does not offer it. Fedora does. Even so, the terminal is what I use - it is arguably faster. If you gave a URL, we could comment on the advice of the man from India.

Since you are not installing an OS on an LVM logical volume, just making a LVM logical volume for data is a relatively simpler task. But you still need an understanding of LVM structures and commands for maintenance.

---

### Post by dhotrum52 on 2023-08-13
At your suggestion I have 22.04 coming. Here in Philippines it takes MANY hours. I will do a LVM during the install 
Here is the man in India:  [https://www.youtube.com/watch?v=PIF1Yf1ul_c](https://www.youtube.com/watch?v=PIF1Yf1ul_c)

---

### Post by dhotrum52 on 2023-08-13
[https://www.youtube.com/watch?v=PIF1Yf1ul_c](https://www.youtube.com/watch?v=PIF1Yf1ul_c)

Thefu said just wipe out and reinstall 22.04. SO...That is what I will do and add LVM during the install. 
Thanks for your input

---

### Post by mIk3_08 on 2023-08-13
Hi dhotrum52. you just say that you are from Philippines. Where exactly in the Philippines are you? I'm from Philippines too. How was the installation of your 22.04 LTS system? Regards and cheers

---

### Post by Dennis N on 2023-08-14
Comments on the linked video:

Besides using the terminal, the partition creation can be done with gparted. After creation, gparted can format the partition as LVM2, which makes the partition an LVM physical volume. Also, The partition for LVM doesn't have to use the entire disk.

After creating the LVM physical volume that you plan to use, you need to use the terminal for VG and LV creation.

Placing physical volumes on different physical disks into one volume group (he did this with **vgcreate mvg /dev/sdb1 /dev/sdc1** and later adding **sdd1** to it) can be one source of data loss since LVs can spread their data anywhere in the VG. Still, with very small disks it may be necessary and a useful way to get more space. Even Red Hat shows this being done in their LVM guide. Keeping good backups is important.

---

### Post by dhotrum52 on 2023-08-14
I have a Asus EX-H510M-V3 I don't know what is wrong with this MB but I fight it to make any changes. Asus didn't even recognize the USB with 22.04 on it. Even when I disconnected the first HD and the only boot option was the USB. Wouldn't work it said "Install a boot disk" . I used Ubuntu USB writer but the MB did not recognize it. I think I will give up and try to install the LVM with the 23.04 already on it. I just hope that guy from India is correct. He makes lots of videos on YT Linuxhelp. If it doesn't work I guess I will have to buy another MB.
I live in Banban, Lila, Bohol. We aren't supposed to chat here. Look up David Hotrum on FB

---

### Post by dhotrum52 on 2023-08-14
My MB wont let my delete and install a new OS. says. "Install a boot disk " when the USB is the only bootable device in it. I am very disgusted with this MB. It has fought me for every change.

---

### Post by dhotrum52 on 2023-08-14
I hope you got an answer. Where are the files on the 3rd drive?? I did not make it into an LVM partition. I left it as it was so I could transfer all my data back. HHEELLPP

---

### Post by TheFu on 2023-08-14
> **dhotrum52 said:**
> At your suggestion I have 22.04 coming. Here in Philippines it takes MANY hours. I will do a LVM during the install 
Here is the man in India:  [https://www.youtube.com/watch?v=PIF1Yf1ul_c](https://www.youtube.com/watch?v=PIF1Yf1ul_c)

ph.archive.ubuntu.com is supposes to be an ubuntu mirror there.  I didn't check it too close, but this says it has 22.04:
[http://ph.archive.ubuntu.com/ubuntu/dists/jammy/Release](http://ph.archive.ubuntu.com/ubuntu/dists/jammy/Release)

---

### Post by Dennis N on 2023-08-14
> I just hope that guy from India is correct.
He is correct. But there are variations in how to complete tasks, such as using gparted to initially create partitions and formatting them for LVM use. I would do that task with gparted. It's simpler. 

His disks were small, so LVM gives him the ability to expand available space for his LVs by adding a physical volume on another disk to the VG containing the LVs.  Easily increasing the size of LVs with a terminal command is the great advantage of using LVM.

---

### Post by TheFu on 2023-08-14
I use gparted to setup partitions BEFORE install, if I can.  For setting up my desired LVM layout on a fresh install, I have a script that I pull over at the beginning of the installer, but before the disk section.  That's how I setup the NVMe storage shown above.  Then, once I have the PV, VG, and LVs setup, I let the Ubuntu installer continue and connect the different LVs to the specific mount locations I want for them - /, /var, /home, /tmp, and any others as needed based on how the system will be used.  I always start with just enough for expected needs for the next few months. Adding more space to an LV is trivial - about 5 seconds.  In 25+ yrs as a system admin, I've never guessed correctly where space will be needed.  LVM means I don't need to be correct, since expanding as needed where needed, is easy.

I do have a rule with LVM.  I don't cross physical device boundaries within the same LV.  Basically, that means I have different VGs for each physical device.  I learned that lesson the hard way, after losing 80%+ of my data when 1 HDD failed in an LV that used 3 partitions on 3 disks.  In the old days, using LVM to span different disks was common because larger drives weren't cheap.  These days, we can have a 4TB HDD for $50, so there's really no good excuse to span drives.  Heck, I've seen enterprise DBs with 25K employees and 50M customers that used DBs of 2TB, so it really isn't needed.  BTW, you don't want to know how many millions of USD that storage cost at the time - it was more than $2M, though I don't recall exactly how much more. I don't think it was $5M.

---

### Post by MAFoElffen on 2023-08-14
> **Dennis N said:**
> There is software, but Ubuntu does not offer it. Fedora does. 
Well...

RedHat used to have LVM GUI, which was named 'system-config-lvm', which was abandoned years ago. That is how it ended up in Fedora, when it was around. I can remember trying it out o Ubuntu 14.04 LTS.

The good news is that it was replaced by 'blivet-gui'. The PPA is at OpenSUSE. That is installable to current releases of Debian and Ubuntu.

I still find it faster to just declare everything in a terminal... But I can see it useful for beginners. Attached screenshots. Shown is a VM with an LVM2 RAID1 root LV and LVM2 RAID5 data LV...

If someone wants to try it, I'll post instructions. It's not documented how to install it on Ubuntu 22.04, and there is a trick with a non-default icon theme, to get it installed and running.

---

### Post by mIk3_08 on 2023-08-15
> **dhotrum52 said:**
> I have a Asus EX-H510M-V3 I don't know what is wrong with this MB but I fight it to make any changes. Asus didn't even recognize the USB with 22.04 on it.
Make sure that the USB drive is formatted correctly. The USB drive should be formatted as FAT32 or NTFS.
Try using a different USB port. Sometimes, a USB port can be faulty and not recognize a bootable USB drive.
Try creating the bootable USB drive using a different tool. There are a number of different tools available, such as Rufus and Etcher.
Check the BIOS settings to make sure that the boot order is correct. The boot order should be set to boot from the USB drive first.
Update the BIOS. Sometimes, a BIOS update can fix issues with bootability.
If you've tried all of these things and you're still having trouble, you may need to contact Asus support for further assistance.

Here are some additional tips for creating a bootable Ubuntu 22.04 USB drive:

Use a high-quality USB drive. A cheap USB drive may not be able to hold the Ubuntu image properly.
Make sure the USB drive is at least 8GB in size. The Ubuntu image is about 4GB in size, but you'll need some extra space for the boot loader and other files.
Follow the instructions carefully when creating the bootable USB drive. If you make a mistake, the USB drive may not be bootable.
Regards and cheers

---

### Post by georgesgiralt on 2023-08-15
Hello, I'm late on this but it may serve others through search engines. 
You do not have to reinstall Oses to switch to LVM PROVIDED you ADD new disks to an existing installation.
I'll write a route for you, and you will have to check how to do each individual steps. 
1) install all new disks to make them accessible on your computer. 
2) boot your current OS. 
3) install all the LVM needed packages (there often is only a metapackage doing all the joob for you)
4) decide if you want to use mirroring (or RAID) on your new set of disks. If yes make one RAID array from you new hardware using mdam (software raid)
5) create as may Physical Volumes as you want (generally one on every physical disk or one on every RAID array created)
6) from these PV (physical volumes) create ONE volume group. I suggest naming it with the computer name, in case you will need to move the whole set of disks to another computer because of a hardware fault in the one you are using).
7) then slice this VG into as many logical volumes you need. I use Slash (/) Usr, Var, Root (for /root), Boot, VarLog, VarTmp, Tmp, Home and Swap. This make backups and mount options for security purposes far easier.
8) Format them using the appropriate filesystem for your OS and taste. Do not forget to add journalling (we are in the XXI century...).
9) Once all filesystems are created, mount them under /mnt  (VG/Slash is mount ed under /mnt, then you mount VG/Usr under /mnt/usr, then VG/tmp under /mnt/tmp, and so on)
10) dump each filesystem in you existing OS into the new set of filesystems under /mnt... It you have a set of different filesystems, this is easy, as /usr goes into /mnt/usr and so on, but if everything is on the same filesystem, you have to resort to tar cf and tar xf to do the job, crossing fingers everything goes fine. Using dump I do : dump 0uaf - / | (cd /mnt && restore -ruf -) Once completed, I dump /usr then /root, then.... 
11) under /mnt/etc/change fstab to use the new VG/LV. Make use of UUID in order to ensure you always use what you want where you want it. Ensure that you have /usr, /var, /var/tmp, /var/log, /tmp, /root, and swap mounted using the LVM version of your OS....
12) Once finished, in a shell, chroot to the new /mnt copy of you OS and do upgrade grub initramfs. If you plan to remove the disks you used previously, be sure to install Grub and the EFI boot part on one of the new disks, BEFORE removing them and attempting to boot.... 
14) reboot and pat you on the back, and enjoy your new LVM system.

I'm often asked why I do split /usr from / or /var from /var/log and /var/tmp. Well if you intent to use your system for a long time, you may find that the /usr (or the /) filesystems is too small. Having them on separate LV make increasing size a walk in the park.
Similarly, during the ages, my /home got very big.  But I do not need fast storage for this. So I kept a 2TB mechanical drive for /home while I use SSD and NVME for storage where speed is paramount. So my VG is made from various PV, one being my 2TB disk and the others being made from smaller SSD, either 3.5" or small NVME in M.2 size. I make the lv on the exact PV I choose depending if I need huge space or fast storage. Same goes for MD arrays. This provide versatility. I have a computer which is more than 25 years old. Everything has been changed except the box.  Raid and LVM helped switch from very small disks (60GB when I started) to 1To now. The process is as follow : remove one disk from the array. Install the bigger disk. Make the array "new again usng the tools for synchronising it. Switch the other(s) disk(s) using the same process. Once the array is up and running and in sync, extend it using the tools in the RAID software suite. Then make you VG aware that the underlying PV has expanded. And voila, you switched from a small size storage to a bigger size storage. Without reinstalling, without backups, without fear, and without disruption of service (except for the time to put the new disks inside the box). Pvmove, vgsplit and vgmerge are commands you should learn to use. This will help you use your /home in one computer to another one in case of hardware failure (this is why all my VG in all my computers have different  names to avoid conflict when you plug and extraneous disk in your machine to recover data or get access to important files)  ....
Hope this helps.
Have a nice and bright day.
Edit : typos. One should proof read before posting.
P.S. : as per you Mobo showing trouble, you should read the "BIOS" utility manual and check options from it. ASUS is known to have a lot of failsafe mechanism implemented to prevent user errors or failures. (I have one computer with an old ASUS MB which won't turn power back on if the power was lost because of a grid failure. This prevent disks or MB failure if the power goes out hen on then out then on in a very short period of time. This saved my computer a couple of time. And of course is documented in Asus manuals... 
As per you release of Ubuntu or any Linux, check if some universities in your country does not have a mirror for you to use and download. This make life easier, sometimes. If not ask them if they will do such mirroring. Do not forget to ask your ISP company for the same service, often they help....

---

### Post by Dennis N on 2023-08-15
> RedHat used to have LVM GUI, which was named 'system-config-lvm', which was abandoned years ago. That is how it ended up in Fedora, when it was around. I can remember trying it out o Ubuntu 14.04 LTS.
Blivet-gui is in the Fedora repository. That's the LVM management application I was referring to in post #3. I have it installed, but I feel the terminal is quicker to accomplish most tasks.

---

### Post by dhotrum52 on 2023-08-15
I fought this all day yesterday and the machine won. I lost. My SSD is formatted LVM and one sata is used for timeshift. I lost 60 GB of data

---

### Post by dhotrum52 on 2023-08-15
I have used ph.ubuntu before and it is a waste. I don't think anybody watches the office. I went back to the main Ubuntu site.

---

### Post by TheFu on 2023-08-15
> **dhotrum52 said:**
> I fought this all day yesterday and the machine won. I lost. My SSD is formatted LVM and one sata is used for timeshift. I lost 60 GB of data

Whenever learning something new like LVM, it is best to setup a play virtual machine, create a few tiny virtual HDDs and try things out first.  For LVM learning, it doesn't matter if the fake HDDs are 10MB or 10TB.  LVM works the same.

Never screw with data.  Always have backups that are 100% certain to be restored and disconnect those backup disks from the system you are screwing around on.

We've all thought we were smart enough not to lose data.  Yet, we've all lost data, so what does that really tell us?

---

### Post by MAFoElffen on 2023-08-15
Reminiscent of "The Clash" singing "I fought the law and the law won..."
"I fought the machine and the machine won..."

Been there. Always have good backups. I say that and myself have lost data trying to get good backups. LOL. Nothing is a guaranty, but we have good intentions and we try to do the right thing. The best of intentions.

---

### Post by dhotrum52 on 2023-08-16
Good afternoon. The USB I used were new. Made in Taiwan. I formatted fat before install but what made it work was a bios reinstall AGAIN . this is the 3rd time. I finally figured out that as soon as the MB recognises an OS it locks the MB to anything else. I tried to go back in with the same USB to undo the LVM format but the MB immediatly said it wanted a install key. The security switch in Bios is turned off. As well as TPM, this isn't my first rodeo installing OS's just my first installing LVM. TheFu said he uses a different VG for each drive and I thought so that is the same as having 3 different drives and just installing certain data on a particular drive. Right now my primary is LVM and the other 2 are fat but I removed one drive and the other sata is used by Timeshift. I lost 60 GB of data in that fiasco. OK later my friend Bohol, Lila, Banban

---

### Post by dhotrum52 on 2023-08-16
Now I am confused. WHY have 3 vg-groups, one on each HD? I thought the purpose of LVM ws to consolidate all HD's?

---

### Post by dhotrum52 on 2023-08-16
Hi Georgesgiralt, I just today 8/17 saw your comment. You mention "journaling" I have never nor do I even know what that is. Yes dumb. I don't think they had that in 1983 when I first started with an XT. Yeah I'm that old. To most of you all this is easy. I have tried to install a VM but my ASUS PC doesn't like it. Something about a kernal. I am extremely disappointed with this MB but it is what is carried here in my city. I do not trust the local repository. ph.ubuntu is a waste of time and space. MUCH slower that going to UB main. Plus they only have a few pkgs. 

I have dropped out completely unless someone can tell me the positives of having LVM. TheFu has 3 HD's and 3 VG-groups. I don't understand why so I asked him. I have 3 HD's but for now my SSD will carry the boot sector and the other that I left installed will carry Timeshift. SO......why add LVM?

---

### Post by Dennis N on 2023-08-17
> I have dropped out completely unless someone can tell me the positives of having LVM
You might want to do some reading. I suggest just google "advantages of using LVM" which will return many results for reading. 

I suppose two of the main advantages are the ability to utilize space on a disk that is not contiguous, and the ease of increasing space for your OS or storage when more is needed. 

As to using space on separate disks in the same Volume Group, Red Hat itself shows this in their LVM administrator's guide, so it is done in practice. The probability of one or both of two disks failing in a given time period will be greater than a single disk failing in that time period, so that's the negative for doing it. But your needs and situation might outweigh the added risk. And common sense tell us to always have good backups of important data in case something fails.  

I swear by LVM myself, and now don't install an OS in any other way unless the installer doesn't support LVM installs.

---

### Post by aljames2 on 2023-08-17
I use LVM as well, but not for grouping disks.  As stated already, back in the day when it was more common to have 100 GB or smaller hard drives, LVM provided methods to extend a volume group across multiple storage devices.  You can still do it today but less necessary given the cost & size of PVs today. 

LVs are much easier to manage and work with than static partitions.  It is very simple to expand an LV is the need for more storage is needed.  With static partitioning, you don’t know how much space you’re going to need in the future, so you end up creating these large partitions that waste of space that never ends up being used efficiently.

My favorite feature of LVM is snapshotting, which freezes your data at a single point in time.  Then from that snapshot you can pull your backups.  This means you can effectively back up your system files without taking the system off-line.

Plus, LVM Has been around for a long time and is very well documented and reliable.

+1 suggesting more reading.

---

### Post by dhotrum52 on 2023-08-17
I have read MANY articles and alll say the same. I tried to make a subdirectory on a different HD other than the boot and it fought me. I had to use sudo to make a sub. The only thing I can see now is just let the PC make sub's and just add files as I get them.

---

### Post by dhotrum52 on 2023-08-17
I found a video by Dorian on YT. I followed EXACTLY what he did. I know my drive size numbers are different but it is DONE At the very last he said" If your first drive fills up it will just spill over into the next drive. That is what I thought a raid did. But doesn't matter now. I hope all this helps. 
root@dave:/home/dave# lvresize -l +100%FREE -r /dev/vgubuntu/root 
  Size of logical volume vgubuntu/root unchanged from <904.43 GiB (231534 extents).
  Logical volume vgubuntu/root successfully resized.
resize2fs 1.46.5 (30-Dec-2021)
Filesystem at /dev/mapper/vgubuntu-root is mounted on /; on-line resizing required
old_desc_blocks = 56, new_desc_blocks = 114
The filesystem on /dev/mapper/vgubuntu-root is now 237090816 (4k) blocks long.

root@dave:/home/dave# df -h
Filesystem                 Size  Used Avail Use% Mounted on
tmpfs                      1.6G  2.1M  1.6G   1% /run
/dev/mapper/vgubuntu-root  890G   41G  809G   5% /
tmpfs                      7.8G     0  7.8G   0% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      7.8G     0  7.8G   0% /run/qemu
/dev/sda1                  511M  7.2M  504M   2% /boot/efi
tmpfs                      1.6G  128K  1.6G   1% /run/user/1000
root@dave:/home/dave# pvs
  PV         VG       Fmt  Attr PSize    PFree
  /dev/sda2  vgubuntu lvm2 a--  <446.63g    0 
  /dev/sdb1  vgubuntu lvm2 a--  <465.76g    0 
root@dave:/home/dave# 

All that is supposed to look better but I didn't find a way to make it look better. 
Dave

---

### Post by Dennis N on 2023-08-18
Looks good. I see what you did. Now, when the content of your root LV grows over ~446G, you won't have a space problem, where you would have had one without the LVM installation. 

To fix the appearance of the terminal output, edit the post, select "go advanced" at the bottom, then highlight (select) the terminal output and click on the button with # at the top of the edit window (which encloses the output in CODE tags) and save.

---

### Post by MAFoElffen on 2023-08-18
> **dhotrum52 said:**
> Now I am confused. WHY have 3 vg-groups, one on each HD? I thought the purpose of LVM ws to consolidate all HD's?

No. PV's can be assigned 'storage containers'. Think of storage containers as slices of a pie. They can be whole disks (not recommended) or partitions (recommended).

You can make those partitions and size, they define them as PV's and added and used when needed. When you add a PV to a VG, all the space inside of it is allocated to the VG.

When you define a VG, it is like this
```

vgcreate [-t type] /dev/PV_device_name_1 [/dev/PV_device_name_2...]

```
VG's, are made up of PV's. A PV can only be assigned to one VG (at a time), but a VG can be made up of many PV's. When you want to make a VG lager, you can add PV's to it. (Like adding another slice.)

LV's are created inside of a VG. There can be many LV's inside of a VG. When you create an LV, you say what size you want it to be. There can be unused space that is not used inside  of a VG. You can save that space for Snapshots, or assign some out later to LV's, as you need it.

That is how LVM2 is supposed to work. You can see where that gives you options and flexibility...

How that happens with the canned LVM2 default templates in the installer, it that One VG is create inside of one partition, LV's are create inside of that and 100% of that VG is allocated.

When I create LVM2 systems... I usually manually create my partitions on a GPT partitoned disk:
```

EFI
bios_boot
boot
swap
root
home
data

```
EFI, bios_boot (optional, based on if I want Legacy BIOS compatibility), and Boot are not PV's. All other's will, so a partition type LVM.

Then I add those others as LVM PV's using pvcreate. Then I create VG's that I assign PV's to. Then I create LV's.

Then I fire up an installer disk, use "Other", let the partitioner see the LVM structure... Set the "mounts" of the filesystem to the LVM structure I created, then continue the install.

Unfortunately, the partitioner in the 23.04 installer is NOT filesystem aware, so will not see LVM2 filesystem structures. So to do it that way, you would have to use an older installer and upgrade the release to 23.04... or use debootstrap to install the OS into the filesystem structure.

---

### Post by dhotrum52 on 2023-08-19
As a final note:
I tried to reduce LVM and ended up in a big mess. Reinstalled with 20.04 and now NO LVM.

---

### Post by aljames2 on 2023-08-20
I suspect you attempted to reduce an LV while it was mounted with the target file system in use.  I do not think we were privy to the specifics of what you were trying to do.  YT videos are not applicable to all situations & are often not in your best interest to follow without further research.

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/lv_reduce](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/lv_reduce)

---

### Post by MAFoElffen on 2023-08-20
Is now a fresh install. No reason not to try again... Or to re-install with the canned LVM install to modify from there... Right?

Or would you like me to create a recipe to follow, to get to where you want to be? I know you are trying. There is a path to get get there.

---

### Post by dhotrum52 on 2023-08-25
Not gonna try that again. Took me 2 days to straighten things out and I am retired.
Finished
Dave

---

