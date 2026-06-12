---
title: "fakeraid 0 dualboot installation woes..."
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by TheHammer101 on 2013-08-01
So I have a pretty decent computer with a Core i7 2700k, 8GB DDR3, and two 320GB HDD in a RAID 0 "fakeraid" set up. I was told from several locations across the web that installing Ubuntu in dual boot despite this would be a breeze, but getting grub to work would be a pain. Clearly incorrect.

I boot into x64 Ubuntu LiveCD, load the installation program, and see..... NOTHING! Just plain unformated raw disks in /dev...

```
ubuntu@ubuntu:~$ ls /dev
alarm            loop2               ram9      tty2   tty52      ttyS26
ashmem           loop3               random    tty20  tty53      ttyS27
autofs           loop4               rfkill    tty21  tty54      ttyS28
binder           loop5               rtc       tty22  tty55      ttyS29
block            loop6               rtc0      tty23  tty56      ttyS3
bsg              loop7               sda       tty24  tty57      ttyS30
btrfs-control    loop-control        sda1      tty25  tty58      ttyS31
bus              mapper              sda2      tty26  tty59      ttyS4
cdrom            mcelog              sda3      tty27  tty6       ttyS5
cdrw             mei                 sdb       tty28  tty60      ttyS6
char             mem                 sdc       tty29  tty61      ttyS7
console          net                 sdc1      tty3   tty62      ttyS8
core             network_latency     sg0       tty30  tty63      ttyS9
cpu              network_throughput  sg1       tty31  tty7       uinput
cpu_dma_latency  null                sg2       tty32  tty8       urandom
disk             oldmem              sg3       tty33  tty9       usb
dri              port                shm       tty34  ttyprintk  vcs
dvd              ppp                 snapshot  tty35  ttyS0      vcs1
dvdrw            psaux               snd       tty36  ttyS1      vcs2
ecryptfs         ptmx                sr0       tty37  ttyS10     vcs3
fb0              pts                 stderr    tty38  ttyS11     vcs4
fd               ram0                stdin     tty39  ttyS12     vcs5
full             ram1                stdout    tty4   ttyS13     vcs6
fuse             ram10               tty       tty40  ttyS14     vcs7
hidraw0          ram11               tty0      tty41  ttyS15     vcsa
hidraw1          ram12               tty1      tty42  ttyS16     vcsa1
hidraw2          ram13               tty10     tty43  ttyS17     vcsa2
hidraw3          ram14               tty11     tty44  ttyS18     vcsa3
hidraw4          ram15               tty12     tty45  ttyS19     vcsa4
hpet             ram2                tty13     tty46  ttyS2      vcsa5
input            ram3                tty14     tty47  ttyS20     vcsa6
kmsg             ram4                tty15     tty48  ttyS21     vcsa7
kvm              ram5                tty16     tty49  ttyS22     vga_arbiter
log              ram6                tty17     tty5   ttyS23     vhost-net
loop0            ram7                tty18     tty50  ttyS24     zero
loop1            ram8                tty19     tty51  ttyS25
ubuntu@ubuntu:~$ ls /dev/mapper
control
```

Alright, that's dumb, something must have gone wrong with dmraid since apparently that's what's in charge of fakeraid by default in Ubuntu...

```
ubuntu@ubuntu:~$ sudo dmraid -a yes
RAID set "isw_dfahbjjjad_Little Boy" was activated
RAID set "isw_dfahbjjjad_Little Boy1" was not activated
RAID set "isw_dfahbjjjad_Little Boy2" was not activated
RAID set "isw_dfahbjjjad_Little Boy3" was not activated
```

That... kinda worked, I guess? So, we check /dev, and /dev/mapper again, right?

```
ubuntu@ubuntu:~$ ls /dev
alarm            hidraw3             ram2      tty15  tty5       ttyS25
ashmem           hidraw4             ram3      tty16  tty50      ttyS26
autofs           hpet                ram4      tty17  tty51      ttyS27
binder           input               ram5      tty18  tty52      ttyS28
block            kmsg                ram6      tty19  tty53      ttyS29
Boy              kvm                 ram7      tty2   tty54      ttyS3
Boy1             log                 ram8      tty20  tty55      ttyS30
Boy1-part1       loop0               ram9      tty21  tty56      ttyS31
Boy2             loop1               random    tty22  tty57      ttyS4
Boy2-part2       loop2               rfkill    tty23  tty58      ttyS5
Boy3             loop3               rtc       tty24  tty59      ttyS6
Boy3-part3       loop4               rtc0      tty25  tty6       ttyS7
bsg              loop5               sda       tty26  tty60      ttyS8
btrfs-control    loop6               sda1      tty27  tty61      ttyS9
bus              loop7               sda2      tty28  tty62      uinput
cdrom            loop-control        sda3      tty29  tty63      urandom
cdrw             mapper              sdb       tty3   tty7       usb
char             mcelog              sdc       tty30  tty8       vcs
console          mei                 sdc1      tty31  tty9       vcs1
core             mem                 sg0       tty32  ttyprintk  vcs2
cpu              net                 sg1       tty33  ttyS0      vcs3
cpu_dma_latency  network_latency     sg2       tty34  ttyS1      vcs4
disk             network_throughput  sg3       tty35  ttyS10     vcs5
dm-0             null                shm       tty36  ttyS11     vcs6
dm-1             oldmem              snapshot  tty37  ttyS12     vcs7
dm-2             port                snd       tty38  ttyS13     vcsa
dm-3             ppp                 sr0       tty39  ttyS14     vcsa1
dri              psaux               stderr    tty4   ttyS15     vcsa2
dvd              ptmx                stdin     tty40  ttyS16     vcsa3
dvdrw            pts                 stdout    tty41  ttyS17     vcsa4
ecryptfs         ram0                tty       tty42  ttyS18     vcsa5
fb0              ram1                tty0      tty43  ttyS19     vcsa6
fd               ram10               tty1      tty44  ttyS2      vcsa7
full             ram11               tty10     tty45  ttyS20     vga_arbiter
fuse             ram12               tty11     tty46  ttyS21     vhost-net
hidraw0          ram13               tty12     tty47  ttyS22     zero
hidraw1          ram14               tty13     tty48  ttyS23
hidraw2          ram15               tty14     tty49  ttyS24
ubuntu@ubuntu:~$ ls /dev/mapper
control                isw_dfahbjjjad_Little Boy   isw_dfahbjjjad_Little Boy2
isw_dfahbjjjad_Little  isw_dfahbjjjad_Little Boy1  isw_dfahbjjjad_Little Boy3
```

OMG WHY DOES ANYTHING NEED TO BE NAMED SO CRAZY?! This isn't freaking raw drive names or anything... Seriously, was "isw_dfahbjjjad_Little Boy" neccesary... alright, learning experience, whatever... so I'll just try to have some patience... I set out to rename these devices since this is clearly going to wreak havoc if I try to install with the device names like this, which turns out was easy enough after some tough hour in Google land...

```
ubuntu@ubuntu:~$ sudo dmsetup rename "isw_dfahbjjjad_Little Boy" LittleBoy
The node /dev/mapper/isw_dfahbjjjad_Little Boy should have been renamed to /dev/mapper/LittleBoy by udev but old node is still present. Falling back to direct old node removal.
ubuntu@ubuntu:~$ sudo dmsetup rename "isw_dfahbjjjad_Little Boy1" LittleBoy1
The node /dev/mapper/isw_dfahbjjjad_Little Boy1 should have been renamed to /dev/mapper/LittleBoy1 by udev but old node is still present. Falling back to direct old node removal.
ubuntu@ubuntu:~$ sudo dmsetup rename "isw_dfahbjjjad_Little Boy2" LittleBoy2
The node /dev/mapper/isw_dfahbjjjad_Little Boy2 should have been renamed to /dev/mapper/LittleBoy2 by udev but old node is still present. Falling back to direct old node removal.
ubuntu@ubuntu:~$ sudo dmsetup rename "isw_dfahbjjjad_Little Boy3" LittleBoy3
The node /dev/mapper/isw_dfahbjjjad_Little Boy3 should have been renamed to /dev/mapper/LittleBoy3 by udev but old node is still present. Falling back to direct old node removal.
```

Awesome, looks like it cleaned it up.

```
ubuntu@ubuntu:~$ ls /dev/mapper
control  LittleBoy  LittleBoy1  LittleBoy2  LittleBoy3
ubuntu@ubuntu:~$ ls /dev
alarm            fuse                oldmem  sda2      tty19  tty44      ttyS10  ttyS8
ashmem           hidraw0             port    sda3      tty2   tty45      ttyS11  ttyS9
autofs           hidraw1             ppp     sdb       tty20  tty46      ttyS12  uinput
binder           hidraw2             psaux   sdc       tty21  tty47      ttyS13  urandom
block            hidraw3             ptmx    sdc1      tty22  tty48      ttyS14  usb
Boy              hidraw4             pts     sg0       tty23  tty49      ttyS15  vcs
bsg              hpet                ram0    sg1       tty24  tty5       ttyS16  vcs1
btrfs-control    input               ram1    sg2       tty25  tty50      ttyS17  vcs2
bus              kmsg                ram10   sg3       tty26  tty51      ttyS18  vcs3
cdrom            kvm                 ram11   shm       tty27  tty52      ttyS19  vcs4
cdrw             log                 ram12   snapshot  tty28  tty53      ttyS2   vcs5
char             loop0               ram13   snd       tty29  tty54      ttyS20  vcs6
console          loop1               ram14   sr0       tty3   tty55      ttyS21  vcs7
core             loop2               ram15   stderr    tty30  tty56      ttyS22  vcsa
cpu              loop3               ram2    stdin     tty31  tty57      ttyS23  vcsa1
cpu_dma_latency  loop4               ram3    stdout    tty32  tty58      ttyS24  vcsa2
disk             loop5               ram4    tty       tty33  tty59      ttyS25  vcsa3
dm-0             loop6               ram5    tty0      tty34  tty6       ttyS26  vcsa4
dm-1             loop7               ram6    tty1      tty35  tty60      ttyS27  vcsa5
dm-2             loop-control        ram7    tty10     tty36  tty61      ttyS28  vcsa6
dm-3             mapper              ram8    tty11     tty37  tty62      ttyS29  vcsa7
dri              mcelog              ram9    tty12     tty38  tty63      ttyS3   vga_arbiter
dvd              mei                 random  tty13     tty39  tty7       ttyS30  vhost-net
dvdrw            mem                 rfkill  tty14     tty4   tty8       ttyS31  zero
ecryptfs         net                 rtc     tty15     tty40  tty9       ttyS4
fb0              network_latency     rtc0    tty16     tty41  ttyprintk  ttyS5
fd               network_throughput  sda     tty17     tty42  ttyS0      ttyS6
full             null                sda1    tty18     tty43  ttyS1      ttyS7
```

Wow, that got cleaned up nicely.. So, now I still have the messiest list ever when I'm in the Installation program..

[IMG]http://denieru.no-ip.org/pics/lolfail.png[/IMG]

I go ahead and format the 2nd partition with ext4 as the root "/" and continue with the install without a swap to the most appropriate copy of /dev/mapper/LittleBoy2 that I can see, and get no errors.. what a pain in the butt.. I restart my computer, boot into windows, install EasyBCD, and tell it to find a Grub2 automatically. All seems well at this point, and so I restart once more. When I get back into the Windows 7 bootloader I have my Ubuntu option, and I try to boot that, but it just gives me some random code....

```
Try (hd0, 0): NTFS5: No ang0
Try (hd0, 1): EXT2:
```

What the heck do I do now? I am so lost.. do I need to rebuild Grub2? Do I need to reinstall? Why did my system fail so miserably to come up with a RAID array that even Windows XP can find without additional drivers?

---

### Post by oldfred on 2013-08-01
Does EasyBCD even work with fakeRAID?

Normally you just install grub to the root of the RAID or /dev/mapper/LittleBoy and it works. 

With Linux you soon learn not to use spaces. You have to escape them \040 or put every entry in "quotes". Just easier to use CamelCase, under_score, or justonename.

Are you sure you want RAID 0. Failure of any drive destroys entire system, so very good backups to another device is essential.
        
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
 "fakeRaid" with nVidia
sudo mount /dev/mapper/LittleBoy2 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/LittleBoy

      
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by TheHammer101 on 2013-08-02
> **oldfred said:**
> Does EasyBCD even work with fakeRAID?
It's a Windows program, which handles fakeRAID far better than Linux so far.. so, yes.
> Normally you just install grub to the root of the RAID or /dev/mapper/LittleBoy and it works. 
From everything I have heard that's exactly what you DON'T want to do  with a fakeRAID... it makes sense too since you can mess with the  metadata and lose your data pretty easily.
> With Linux you soon learn not to use spaces. You have to escape  them \040 or put every entry in "quotes". Just easier to use CamelCase,  under_score, or justonename.
Yeah, except I didn't really think "Hey, maybe I'll install Linux later  on so I should not make a more pleasant name for myself since Linux is a  pain in the butt." when I set up the RAID. Last time I checked humans  used computers, and spaces are incredibly common in human languages..  seems like someone needs to do a little better.. not to mention I've  seen RAID controllers that don't easily allow you to create a name of  your own, and those may have spaces, or Linux unfriendly characters in  them.
> Are you sure you want RAID 0. Failure of any drive destroys  entire system, so very good backups to another device is  essential.
        I have a Ubuntu server set up that holds all of my important  data on a ZFS array, so I am not worried. Cheap, speedy storage was my  intent. I'm going for a pair of RAIDed SSD drives later on.
> How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
 "fakeRaid" with nVidia
sudo mount /dev/mapper/LittleBoy2 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/LittleBoy

      
 Don't bother with RAID 0 unless you have a specific need for speed  without data redundancy, since if one drive goes out, you lose the whole  array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
The  Windows 7 bootloader is fine, as I just said I was able to boot into Windows 7 after the installation process. I have no desire to mess up my new install of Windows 7 by messing with that grub install.. you know, since Windows 7 actually works... It passes into grub, and  then grub fails.. I supposed I need to go into recovery console and  somehow force it to find the drive, but I have no idea where to begin on  that. Plus I've got no idea how to make those changes persistent..

---

### Post by oldfred on 2013-08-02
I think that may be an EasyBCD question. You can force grub2 to install to a PBR - partition boot sector. But it then uses blocklists or hard coded addresses to find the rest of grub in your install. An update to grub may change location on drive and then you have to reinstall grub to PBR with new addresses. So have Ubuntu live version available to fix it.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by TheHammer101 on 2013-08-02
> **oldfred said:**
> I think that may be an EasyBCD question. You can force grub2 to install to a PBR - partition boot sector. But it then uses blocklists or hard coded addresses to find the rest of grub in your install. An update to grub may change location on drive and then you have to reinstall grub to PBR with new addresses. So have Ubuntu live version available to fix it.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
  Ummmmm......
> Windows 7 actually works... It passes into grub, and  then grub fails..

---

