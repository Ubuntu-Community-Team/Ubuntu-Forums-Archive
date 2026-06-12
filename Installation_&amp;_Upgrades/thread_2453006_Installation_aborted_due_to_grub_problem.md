---
title: "Installation aborted due to grub problem"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by mbocciab on 2020-11-01
Hi everyone, 
I was trying to make a fresh install of 20.10 on my desktop PC but for three times it stuck during grub install. 
It's the first time I meet this kind of problems.
My system has a dual boot: one on 20.40 and the other user to be 19.10. I was trying to make this fresh install on previous 19.10 partition.
Now my system on startup on grub selection detects 20.10 (default) and 20.40 but it stucks when trying to start the 20.10. 
Selecting 20.40 all is ok.

Any solution?

---

### Post by VMC on 2020-11-01
Make, Model, and all that stuff will help us. Start with partition info:
```
lsblk -f
```

---

### Post by smojo on 2020-11-01
I have the exact same problem with Groovy on an Late 2015 iMac
I create 16 Gig swap, 512MB EFI, rest ext4 root.
When booting from LiveUSB I also have to set nomodeset or i'm greeted with a black screen.

My existing install which was 20.04 was upgraded to 20.10.
This seems to have broken my installation.

I can boot with the old 5.4 kernel, if i want to boot with the 5.8 kernel i have to add nomodeset which is a bad experience....

---

### Post by mbocciab on 2020-11-01
Thanks.
Here is the result of the command:
```
NAME FSTYPE LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0
     squash                                                  0   100% /snap/cano
loop1
     squash                                                  0   100% /snap/core
loop2
     squash                                                  0   100% /snap/core
loop3
     squash                                                  0   100% /snap/obs-
loop4
     squash                                                  0   100% /snap/obs-
loop5
     squash                                                  0   100% /snap/gnom
loop6
     squash                                                  0   100% /snap/core
loop7
     squash                                                  0   100% /snap/gtk-
loop8
     squash                                                  0   100% /snap/core
loop9
     squash                                                  0   100% /snap/pych
loop10
     squash                                                  0   100% /snap/spot
loop11
     squash                                                  0   100% /snap/nmap
loop12
     squash                                                  0   100% /snap/pych
loop13
     squash                                                  0   100% /snap/keep
loop14
     squash                                                  0   100% /snap/gnom
loop15
     squash                                                  0   100% /snap/snap
loop16
     squash                                                  0   100% /snap/spot
loop17
     squash                                                  0   100% /snap/gnom
loop18
     squash                                                  0   100% /snap/subl
loop19
     squash                                                  0   100% /snap/snap
loop20
     squash                                                  0   100% /snap/snap
loop21
     squash                                                  0   100% /snap/snap
loop22
     squash                                                  0   100% /snap/musi
loop23
     squash                                                  0   100% /snap/keep
sda                                                                   
&#9500;&#9472;sda1
&#9474;    ext4         4d2c5246-3759-4ada-b63c-bdf2c634cfc9   32,5G    66% /
&#9500;&#9472;sda2
&#9474;                                                                     
&#9500;&#9472;sda5
&#9474;    ext4         ea4f69f5-99af-4c6a-bab8-010eb6affa6d                
&#9492;&#9472;sda6
     swap         f53384ed-54ab-4e62-b424-32477a81630b                [SWAP]
sdb  ext4   Jupiter
                  e6f4f0f4-2160-47a2-ad84-cdf14f8d4682                
sdc  ext4   Rigel 4a2f4f0c-cb41-4bd6-9c05-74f756444df1                
sr0                                                                   

```

---

### Post by grahammechanical on 2020-11-01
@ mbocciab

I am confused. You get the Grub boot menu and it lists 20.10 as the default and also 20.04. This means that Grub has installed correctly. So, what is the problem? Ubuntu 20.04 loads correctly but Ubuntu 20.10 does not load correctly. You say it gets stuck.

You could try selecting Advanced Options for Ubuntu at the Grub menu and then select a Linux kernel with a Recovery Mode. At the recovery menu select resume. Ubuntu should load with a basic video driver. If you successfully get to a desktop it might indicate that you have a video driver issue.

Regards.

---

### Post by mbocciab on 2020-11-02
When booting with 20.10 option (both safe or normal mode) I have the messages:

```
timed out waiting for device /dev/disk/by-UUID/F366-AE33
dependency failed for filesystem
dependency failed for /boot/EFI
dependency failed for local filesystem

started emergency sheel
reached target emergency mode

```

---

### Post by yancek on 2020-11-02
The information you posted in post 6 indicates that the system is looking for a /boot/EFI partition with the UUID of F366-AE33.  The lsblk output in post 4 does not show an EFI partition.  That would indicate there was an EFI partition with that UUID at some point and it no longer exists so can't boot EFI.  Is your other OS installed in Legacy mode?

---

### Post by mbocciab on 2020-11-02
I installed OS always in the same mode. Booting from USB pen and installing. 
Do you mean that the system is searching for the USB pen drive?
A peculiar thing about 20.10 installation is a kind of grub when booting from installation pen. I selected ubuntu and made me install from live version.

---

### Post by Frogs Hair on 2020-11-02
I had the same problem, but in my case grub did install despite the message that it did not. There are more reports on this problem. 


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964)

---

### Post by mbocciab on 2020-11-02
I solved!
The problem seems to be in the fstab file. 
Looking into the file you'll find that is still present the line referring to the installation media!!!! #-o:mad:
So. Open the file using sudo command and modify it by commenting the line referring to UEFI stuff.
Restart your fresh system and it'll be fine.

---

