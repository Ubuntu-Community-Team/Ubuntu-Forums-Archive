---
title: "ubuntu 22.04 zfs Unable to create io-slave. Unknown protocol 'admin'."
date: 2023-12-13
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-12-13
I wanted to open a pdf attachment to an email filed in Thunderbird. instead there was an error message: I have tried both document reader and Okular. 

>  Unable to create io-slave. Unknown protocol 'admin'.

I opened the user settings and groups. There is no admin group, Is that to be expected? 

The nearest in name is Adm Group iD 4 I am a member. 

The nearest in function is Root it has a group ID of 0  and only me as an unticked group member.

A general search did not come up with an answer.  that seemed appropriate.

---

### Post by #&amp;thj^% on 2023-12-13
Is the PDF of a personal content?
If not can you attach it here.
EDIT: Also is the document viewer a flatpak?
EDIT: I see this:
```
org.kde.okular permissions:
    ipc                    network                cups       fallback-x11
    pulseaudio             wayland                x11        dri
    file access [1]        dbus access [2]

    [1] host, xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar, org.kde.KGlobalSettings, org.kde.kconfig.notify


```
On flatpak version.

---

### Post by Robbyx on 2023-12-13
It seems all my pdf files have the same problem. As an example, I tried to attach a pdf, but the manage attachment procedure did not work. I dragged it into the manager but nothing appeared as attached. Instead a message came up saying that no apps installed to open the file. 

The one I was going to add was from 2007. Some problem with recent ones as well. 

Robin

---

### Post by #&amp;thj^% on 2023-12-13
> **Robbyx said:**
> It seems all my pdf files have the same problem. As an example, I tried to attach a pdf, but the manage attachment procedure did not work. I dragged it into the manager but nothing appeared as attached. Instead a message came up saying that no apps installed to open the file. 

The one I was going to add was from 2007. Some problem with recent ones as well. 

Robin
Robin can you tell me if Okular is a flatpak. :D
Please show me this:
```
flatpak list
```

---

### Post by Robbyx on 2023-12-13
```
robins@robins-MS-7C96:~$ flatpak list
Name                Application ID           Version  Branch      Installation
Czkawka             …m.github.qarmin.czkawka 6.1.0    stable      system
Freedesktop Platfo… org.freedesktop.Platform 22.08.19 22.08       system
Mesa                …top.Platform.GL.default 23.1.9   22.08       system
Mesa (Extra)        …top.Platform.GL.default 23.1.9   22.08-extra system
Mesa                …top.Platform.GL.default 23.3.0   23.08       system
Mesa (Extra)        …top.Platform.GL.default 23.3.0   23.08-extra system
openh264            …sktop.Platform.openh264 2.1.0    2.2.0       system
GNOME Application … org.gnome.Platform                45          system
Yaru Gtk Theme      org.gtk.Gtk3theme.Yaru            3.22        system
Firefox             org.mozilla.firefox      120.0.1  stable      system
robins@robins-MS-7C96:~$ 

```

---

### Post by MAFoElffen on 2023-12-13
LOL... You two are funny.

Open FireFox. Right-Click on an open area of the top-bar. Check the Menu Bar CheckBox. Files > Open > Navigate to the PDF file and view if.

Most modern Web Browsers can view PDF Files these days.

---

### Post by #&amp;thj^% on 2023-12-13
I don't see where "thunderbird" was replaced by flatpak when you ran "unsnap"
Please show:
```
apt policy thunderbird okular
thunderbird:
  Installed: 1:115.5.2+build2-0ubuntu0.24.04.1~mt1
  Candidate: 1:115.5.2+build2-0ubuntu0.24.04.1~mt1
  Version table:
     1:115.5.2+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
 *** 1:115.5.2+build2-0ubuntu0.24.04.1~mt1 1001
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
okular:
  Installed: 4:23.08.3-0ubuntu1
  Candidate: 4:23.08.3-0ubuntu1
  Version table:
 *** 4:23.08.3-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status


```

---

### Post by #&amp;thj^% on 2023-12-13
> **MAFoElffen said:**
> LOL... You two are funny.

Open FireFox. Right-Click on an open area of the top-bar. Check the Menu Bar CheckBox. Files > Open > Navigate to the PDF file and view if.

Most modern Web Browsers can view PDF Files these days.

Ha Ha funny my behind...:P

---

### Post by Robbyx on 2023-12-13
```
 apt policy thunderbird okular
thunderbird:
  Installed: 1:115.5.0+build1-0ubuntu0.22.04.1
  Candidate: 1:115.5.0+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:115.5.0+build1-0ubuntu0.22.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
okular:
  Installed: 4:21.12.3-0ubuntu1
  Candidate: 4:21.12.3-0ubuntu1
  Version table:
 *** 4:21.12.3-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Robbyx on 2023-12-13
I tried opening the pdf file that I had wanted to view when I started this thread. It does not open with FF, which does not give an error message.

---

### Post by #&amp;thj^% on 2023-12-13
Please run:
```
okular
```
Leave the terminal running and try navigating to any PDF
Then copy the ouput back here, this is very strange Robin.

---

### Post by Robbyx on 2023-12-13
I am beginning to understand that the problem seems to arise from a particular HD.  I am going to check out my fstab. I will report back.

---

### Post by #&amp;thj^% on 2023-12-13
Ok ;)

---

### Post by MAFoElffen on 2023-12-13
Okular usually just works with most everything(???)

Others I have used: Master PDF Editor, and Scribus.

---

### Post by Robbyx on 2023-12-14
Is it possible that the failure to read some pdfs is because they are on partitions not specified in the fstab?  Was I wrong to have  left mounting  to the autoloader as when access was needed in a computer session.


My fstab is very basic. In my previous ubuntu systems the fstab mounted all the drives (I can post a copy of the fstab I used in July  for btrfs, which of course is not used for zfs) 

```
blkid -o list
device                                           fs_type         label            mount point                                          UUID
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/nvme0n1p3                                   zfs_member      bpool            (not mounted)                                        6678077119306010565
/dev/nvme0n1p1                                   vfat                             /boot/efi                                            13DA-E5AF
/dev/nvme0n1p4                                   zfs_member      rpool            (not mounted)                                        3637953239827115220
/dev/sdb7                                        swap                             (not mounted)                                        6bbc8a5a-b488-49b6-904a-952e05463815
/dev/sdb5                                        ext4            mydocs           /media/robins/mydocs                                 8d99bfc8-90ab-4488-b7da-87e7676aff19
/dev/sdb6                                        ext4            Data inc AV      /media/robins/Data inc AV                            1a2e8d10-7b93-4de1-b551-31db6a621276
/dev/sdc2                                        ext4                             /media/robins/bacac64a-73be-47fe-87a8-ea25ffbc2c01   bacac64a-73be-47fe-87a8-ea25ffbc2c01
/dev/sdc1                                        ext4                             /media/robins/32677e49-0894-4d3f-8cc4-7e27b74ac6f0   32677e49-0894-4d3f-8cc4-7e27b74ac6f0
/dev/mapper/keystore-rpool                       ext4            keystore-rpool   /run/keystore/rpool                                  006bfba2-2dbd-497a-aaa3-493d0b8f9b8f
/dev/mapper/cryptoswap                           swap            cryptoswap       [SWAP]                                               e49de4e5-7b82-40ea-bd4e-567ee5e77c7f
/dev/zd0                                         crypto_LUKS                      (not mounted)                                        91fa11a4-1d1e-40b1-86e8-afcc955a5be9
/dev/nvme0n1p2                                                                    (not mounted)                                        
/dev/sdd1                                                                         /media/robins/E0D0-35DF                              

```


This is the current fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=13DA-E5AF  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub	/boot/grub	none	defaults,bind	0	0
/dev/mapper/cryptoswap	none	swap	sw	0	0
```


Robin

---

### Post by #&amp;thj^% on 2023-12-14
I see nothing wrong, mine
```
device         fs_type label    mount point        UUID
----------------------------------------------------------------------------------------
/dev/nvme0n1p3 zfs_member bpool (not mounted)      3916227051976673936
/dev/nvme0n1p1 vfat             /boot/efi          26DD-9533
/dev/nvme0n1p4 zfs_member rpool (not mounted)      7080549889544376032
/dev/nvme0n1p2 crypto_LUKS      (not mounted)      20d5997f-a580-485b-858c-9d59167eb991
/dev/sdb2      zfs_member tank  (not mounted)      10926758658995060061
/dev/sdb1      vfat             (not mounted)      0335-2115
/dev/sdc1      ntfs    My Passport (not mounted)   3ACA0092CA004D17
/dev/sda2      ext2             (not mounted)      fba8487f-546c-4087-801a-edebc75d86a6
/dev/sda3      zfs_member dozer (not mounted)      12537660240534768289
/dev/sda1      vfat             (not mounted)      421D-2868
/dev/mapper/keystore-rpool
               ext4    keystore-rpool /run/keystore/rpool 31766af0-18c5-4154-8dd9-fd0d0610d7d6
/dev/mapper/cryptoswap
                                [SWAP]             
/dev/zd0                        (not mounted)      

```
fstab
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=26DD-9533  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub	/boot/grub	none	defaults,bind	0	0
/dev/mapper/cryptoswap	none	swap	sw	0	0

```
> Was I wrong to have left mounting to the autoloader as when access was needed in a computer session.

Not in my view, I do the same as you, plus 2 more created pools for my backs-ups, and playing around.
If the PDF's are on the unmounted drive, when you open said PDF it would or should then mount the Drive.

---

### Post by #&amp;thj^% on 2023-12-14
Robin will you try this>>>*if only* the PDF is on the Drive in question, the one you suspect as a problem.
copy that PDF to your /home directory, then try to open it with a reader.

---

### Post by Robbyx on 2023-12-14
I copied the file into ~/documents. It opened in Okular. I checked again with the original, on a drive known as data_sdde. There the original file would not open for the errors mention at the start of this topic.

The parent folder is admin:///home/robins/data_sdde/HEALTH/. How can I check where that folder is stored? I want to check if it is showing in the blkid -o at #15

Robin

---

### Post by #&amp;thj^% on 2023-12-14
What is /data_sdde/ formatted as? It shouldn't matter though I'm just curious.

---

### Post by Robbyx on 2023-12-14
The parent folder is admin:///home/robins/data_sdde/HEALTH/. How can I check where that folder is stored? I want to check if it is showing in the blkid -o at #15

I can not tell what format is used but as  it is  in Computer I assume it is  zfs


Robin

---

### Post by #&amp;thj^% on 2023-12-14
Bingo that's the problem or the reason why>>>"admin:///home/robins/data_sdde/" and yes you are right it would be a zfs system.
Did you do that intentionally? As "admin"

---

### Post by Robbyx on 2023-12-14
> Did you do that intentionally? As "admin" 

I do not recall doing it intentionally. I suspect it is the result of copying it off a drive that was the primary admin drive prior to installing zfs. I had an sdde drive that became corrupted. I am guessing the copy came from there. 

How do change it now?

Robin

---

### Post by #&amp;thj^% on 2023-12-14
See if Gnome Disks will allow you to change it.
If not wait, I'll be back it's supper time and I'm a hungry boy. lol

---

### Post by MAFoElffen on 2023-12-14
> **1fallen said:**
> Bingo that's the problem or the reason why>>>"admin:///home/robins/data_sdde/" and yes you are right it would be a zfs system.
Did you do that intentionally? As "admin"
Dang. I completely overlooked that aspect... I don't know why.

Sort of like if a user does
```

gedit admin:///etc/default/grub 

```
Would open gedit with file /etc/default/grub as a GUI (using my user environment) with admin privileges on the file. Not  normal everyday way to do that. Though it does work...

---

