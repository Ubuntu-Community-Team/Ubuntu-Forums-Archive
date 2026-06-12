---
title: "Wanting to change my LVM setup without reinstalling, if possible"
date: 2022-12-10
forum: Installation &amp; Upgrades
---

### Post by stoogiebuncho on 2022-12-10
Last time I installed Kubuntu, I went through it a little fast and selected the option to use encrypted LVM on the whole disk.

Time has passed, it's time to upgrade once again, and I'd like to do things differently this time.  Specifically:

- Since LVM used my whole partition, I don't have any room to create snapshots, which is one of the main reasons I selected LVM in the first place.  So I need to shrink my encrypted root LVM partition to make room for snapshots.
- I want to have /home on a separate partition

Can I accomplish this without nuking the whole thing and starting over?  My understanding is that the root partition needs to be unmounted in order to shrink it, and I'm not sure how it would work to shrink an unmounted encrypted partition.

How do you prefer to prep your partitions prior to installation?  Any tips or best practices?

---

### Post by TheFu on 2022-12-10
> **stoogiebuncho said:**
> 
Time has passed, it's time to upgrade once again, and I'd like to do things differently this time.  Specifically:


Not unusual. But ... 

> **stoogiebuncho said:**
> - Since LVM used my whole partition, I don't have any room to create snapshots, which is one of the main reasons I selected LVM in the first place.  So I need to shrink my encrypted root LVM partition to make room for snapshots.
Actually, this isn't true.  You don't need to touch the encrypted container, the PV, nor the VG at all.  What you need to sufficient free space in the VG.  Now, if you were lazy post-install and didn't immediately reduce the root LV size to 35G, set the swap LV to be 4.1G (desktops), add a var and home LV sized to fit the needs for the next 3 months, well, that's a problem.  Further, if this is on SSD storage, it is a good idea to drastically increase the SSD lifespan to never allocate to LVs more than 80% of the total storage on an SSD.  Because all the storage is virtual and only the SSD really knows how load leveling is performed, it is just the LVs (including LV-snapshots) that matter.  Assigning the full partition to the LUKS container, and that to the PV and VG, is fine, provided you don't tell it to pre-encrypt the entire storage, but have it encrypt as it goes along.

> **stoogiebuncho said:**
> 
- I want to have /home on a separate partition
Why?  Forget partitions.  Think LVs.

> **stoogiebuncho said:**
> Can I accomplish this without nuking the whole thing and starting over?  My understanding is that the root partition needs to be unmounted in order to shrink it, and I'm not sure how it would work to shrink an unmounted encrypted partition.

If you think "LVs" and not attempt to change partitions, you don't need to start over.
If you want to reduce the LVs, VG, PV, LUKs container, then force the existing partition holding all those to be smaller .... it is possible, but a bunch of accounting is needed to know exactly how much space is used between the different types of objects.  Mess up and there aren't any warnings. You'll just lose data, corrupt data or overwrite the newly created partition that is supposed to be outside the LUKs container.  Good luck with that.

> **stoogiebuncho said:**
> How do you prefer to prep your partitions prior to installation?  Any tips or best practices?
For laptops, I go with full drive encryption and immediately post-install reduce the sizes of the installer-created LVs, add the LVs I want.  I've posted my layout here a number of times.

For non-encrypted systems, I have a template with a little script that I pull over via ssh during the installation process, before getting to the "Do Something Else" option.  Did one of those in late-August. Here's that layout:
```
NAME                         SIZE TYPE FSTYPE     LABEL      MOUNTPOINT
nvme0n1                    465.8G disk                       
&#9500;&#9472;nvme0n1p1                   50M part vfat       EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                  600M part ext4                  /boot
&#9492;&#9472;nvme0n1p3                  465G part LVM2_membe            
  &#9500;&#9472;vg00-swap                4.1G lvm  swap                  [SWAP]
  &#9500;&#9472;vg00-root--00             35G lvm  ext4                  /
  &#9500;&#9472;vg00-var                  35G lvm  ext4                  /var
  &#9500;&#9472;vg00-home                 26G lvm  ext4       home       /home
  &#9500;&#9472;vg00-ubuntu2204--srv      15G lvm                        
  &#9500;&#9472;vg00-xubuntu22.04         40G lvm                        
  &#9500;&#9472;vg00-test                 10G lvm                        
  &#9500;&#9472;vg00-ubuntu22.04--srv--2
  &#9474;                           15G lvm                        
  &#9492;&#9472;vg00-xubuntu22.10         20G lvm                        

```
I'm showing some virtual machine storage that is provided directly to the VMs. The host doesn't access it and never mounts it.
Some other commands:
```
$ sudo pvs
  PV             VG             Fmt  Attr PSize    PFree   
  /dev/nvme0n1p3 vg00           lvm2 a--  <464.98g <264.88g

$ sudo vgs
  VG             #PV #LV #SN Attr   VSize    VFree   
  vg00             1   9   0 wz--n- <464.98g <264.88g

$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home              vg00           -wi-ao----   26.00g                                                    
  root-00           vg00           -wi-ao----   35.00g                                                    
  swap              vg00           -wi-ao----    4.10g                                                    
  test              vg00           -wi-a-----   10.00g                                                    
  ubuntu22.04-srv-2 vg00           -wi-a-----   15.00g                                                    
  ubuntu2204-srv    vg00           -wi-a-----   15.00g                                                    
  var               vg00           -wi-ao----   35.00g                                                    
  xubuntu22.04      vg00           -wi-a-----   40.00g                                                    
  xubuntu22.10      vg00           -wi-a-----   20.00g         
```

As you can see, I'm definitely not using the entire SSD. Over 260GB is free.

I almost forgot:
```
$ dft    # this is an alias that shows only real storage.
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   11G   22G  33% /
/dev/nvme0n1p2                              ext4  574M  272M  260M  52% /boot
/dev/nvme0n1p1                              vfat   50M  5.2M   45M  11% /boot/efi
/dev/mapper/vg00-home                       ext4   26G  9.9G   15G  41% /home
/dev/mapper/vg00-var                        ext4   35G   26G  6.6G  80% /var
```

/var is much larger than I'd normally want/need (4G should be plenty normally), but this is a VM host and sometimes I'll want a file-based VM.  My hypervisor places those in /var/lib/libvirt/images/ . Before this fresh install, I mounted extra storage directly to /var/lib/libvirt/.  

The trick to using LVM, or any volume manager, is NOT to allocate to file systems all the available storage.  Having some free storage means there's room for snapshots (use for backups) and for extending existing LVs in about 5 seconds - no downtime - system keeps running. LVM is about flexibility to handle things we don't predict will happen.  In 25+ yrs of being an admin, I've never, ever, guessed correctly where storage will be needed.  Not once.  So, LVM lets me appear like a genus.  Shhhhh.  Don't tell anyone that I'm really any idiot who learned from prior mistakes.  Lots of mistakes, not all mine, fortunately, but a bunch were.  Most definitely.

Anyway, hope this is helpful.  We all make slightly different choices based on what we've seen, been told, and the defaults for Ubuntu disk layouts are pretty bad for everyone except noobs.  If you are using encryption and LVM, you aren't a noob.

BTW, if you use encryption, please, please, please, ensure you have excellent backups that you 100% know can be restored.  Any failure on encrypted storage can be either a slight inconvenience or total data lose.  It is your choice.

---

### Post by stoogiebuncho on 2022-12-17
Thanks, this is helpful - though in some ways it was mostly helpful by highlighting the sheer amount of things I didn't understand yet!

Nevertheless, it helped me set a path and follow through.

I managed to resize my existing LV without losing data.  KDE Partition Manager was a big help here, as I was still a little gun shy about some of the command-line stuff because I wasn't *positive* I understood what everything was doing.  I set up LVs for / and /home, and was able to move my data to the /home LV so I could install the latest LTS without writing over my personal data.  Now the LVs are more reasonably sized and I have room for snapshots.  Still lots to learn here, but feel like I've got a good start.

Thanks again!

---

