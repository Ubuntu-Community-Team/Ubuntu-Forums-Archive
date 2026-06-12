---
title: "Minimum requirement for &quot;/&quot; partition"
date: 2024-03-22
forum: Installation &amp; Upgrades
---

### Post by wjwh on 2024-03-22
I am trying to install Ubuntu in dual boot with Windows 10 ( a task which I have done successfully many times before). I prefer to have two partitions - "/" and "/home" - so that I can keep upgrading with a clean install each time. I know that this is not the current fashion, but I prefer it that way. On my previous device I dual booted Ubuntu 20.04 with Windows 10, which worked very successfully with a "/" partition size of 40 GB.  This time I am trying to install Ubuntu 22.04 in the same way.  When I get to "Something else" and try to set the partition size of the "/" partition to 40 GB, I am told that this is smaller than the minimum size required and that I must increase the size. I have done so but keep getting the same response. I have now tried to set the "/" partition size to 100 GB and am still met with the same response - this is smaller than the minimum size required! Surely this can't be right? I have plenty of space available (1 TB), but do I really need more than 100 GB to run Ubuntu 22.04?  Actually, I know that I don't, because I am running the same setup successfully on another machine with the "/" partition size only 45 GB.  So, can anyone tell me what is going wrong here and what I can do about it.  I do want to retain the two partition system, so please don't tell me just to install it all on the one partition.  Thank you all in anticipation.

---

### Post by MAFoElffen on 2024-03-22
Which ISO do you have downloaded? 22.04.4 right?

Honestly, I have never seen that error come up... I test the DEV Daily ISO, and for them install with 16GB the whole OS.

I would recommend 30GB to 40 GB. Even though is will install at 16GB, that I would say is the absolute minimum, and it would later run into space problems with updates, and if you installed any other applications.

40GB as "/", and an additional separate "/home" would be comfortable.

---

### Post by wjwh on 2024-03-23
Actually, the ISO is 22.04.3. I'll try downloading the latest one to see if that works any better. Thank you for the quick response. I'll report how I get on, but it won't be for several days as I will not be able to get back to it before then.

---

### Post by MAFoElffen on 2024-03-23
No problem. I'm patient. LOL

---

### Post by wjwh on 2024-03-24
Thank you, MAFoElffen.  I've now downloaded Ubuntu 22.04.4 and tried it.  Unfortunately the result was exactly the same. I could not proceed any further, even when trying a 100 GB partition for "/".  I am still being told that this is less than the minimum size required.  The only thing left that I can think of doing is to use gParted to create the partition sizes that I want and then try to install on those pre-prepared partitions.  It will probably be another couple of days before I find time to do this, but when I do I'll post the results.

---

### Post by MAFoElffen on 2024-03-24
Let's take a look at what it is talking about...

Boot from the installer LiveUSB and got to "Try". Start up a terminal session.

Post the results of this, within CODE Tags:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```

---

### Post by wjwh on 2024-03-24
Hello again, MAFoElffen ,

I have done as you suggested and here is the result that I get.  I hope you will excuse an old man (I am 87, going on 88) if I have got it wrong. I have no idea what code tags are or how to post the result within them so this is the best i can do.

```
ubuntu@ubuntu:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME   LABEL                      SIZE FSTYPE  MOUNTPOINT MODEL
sda                               1.8T                    CT2000BX500SSD1
&#9500;&#9472;sda1                            500M vfat               
&#9500;&#9472;sda2                             16M                    
&#9500;&#9472;sda3                          930.5G ntfs               
&#9500;&#9472;sda4                            522M ntfs               
&#9492;&#9472;sda5                          931.5G ext4               
sdb                                 0B                    USB SD Reader
sdc                                 0B                    USB CF Reader
sdd                                 0B                    USB SM Reader
sde                                 0B                    USB MS Reader
sdf    Ubuntu 22.04.4 LTS amd64   7.5G iso9660            USB DISK 3.0
&#9500;&#9472;sdf1 Ubuntu 22.04.4 LTS amd64   4.7G iso9660 /cdrom     
&#9500;&#9472;sdf2 ESP                        4.9M vfat               
&#9500;&#9472;sdf3                            300K                    
&#9492;&#9472;sdf4 writable                   2.8G ext4    /var/crash 
sr0                              1024M                    ATAPI iHAS324 Y
```

---

### Post by wjwh on 2024-03-24
I obviously did get it wrong. Sorry!

---

### Post by Rubi1200 on 2024-03-25
Hi wjwh :-)

Go back to your post #7

Click to edit with Go Advanced.

Highlight the output and then click on the # icon to wrap with code tags.

MAFoElffen will help you with the best way forward for your situation.

---

### Post by Rubi1200 on 2024-03-25
Hi wjwh :-)

Go back to your post #7

Click to edit

Highlight the output and then click on the # icon to wrap with code tags.

MAFoElffen will help you with the best way forward for your situation.

---

### Post by ubfan1 on 2024-03-25
I see no free space on your 1.8 TB disk.  Maybe the message is that there is not enough space to make any partition, be it 100GB or 40Gb.  Did you make the 931.5GB partition to install Ubuntu?  If nothing is on it, just assign that to / but consider deleting it (if empty) and remaking a 50GB / and the rest a /home partition. Either way.  If you just deleted it and left free space, the installer should find it.

---

### Post by wjwh on 2024-03-25
Thank you. I'll try to do that. The 931.5 GB partition has Ubuntu on it (everything on one partition).  I was trying reinstall it on two partitions. Previously, the installer has been able to create the appropriate partitions and reformat them itself, wiping out everything on them in the process, but if I have to do it first with gParted, so be it. I'll give it a go.

---

### Post by MAFoElffen on 2024-03-25
Just woke up. 5 am here. Getting ready for work... So will hurry a response.
```

ubuntu@ubuntu:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME   LABEL                      SIZE FSTYPE  MOUNTPOINT MODEL
sda                               1.8T                    CT2000BX500SSD1
&#9500;&#9472;sda1                            500M vfat               
&#9500;&#9472;sda2                             16M                    
&#9500;&#9472;sda3                          930.5G ntfs               
&#9500;&#9472;sda4                            522M ntfs               
&#9492;&#9472;sda5                          931.5G ext4               

```
I'm thinking from your posts, the 
/dev/sda1 is EFI
/dev/sda2 is ms reserved
/dev/sda3 is Windows
/dev/sda4 is ms reserved
/dev/sda5 is for Ubuntu

For /dev/sda5, you could either use TRY, and delete that partition... Then start the partitioner. Then the installer should offer to install it in the unreserved space on the disk, alongside of Windows...

Or use Other as an install option to start the manual partitioner, then select that partition, then select "Change" > Reformat > Use as Ext4 > mount as "/" > Finish/Install...

---

### Post by yancek on 2024-03-25
The output in post 7 shows sda1 as a 500MB vfat partition which is likely an EFI partition.  You can definitely learn this by running the command:  sudo parted -l  which will list partitions and devices.  sda5 is a nearly 1TB partition and since you want a separate /home partition, you need to resize/shrink that partition down to what you want for / then use the rest for /home or make whatever change you want.  You could do this using GParted on the Ubuntu install USB before beginning the installation if you want.  If you were trying to create a / partition without shrinking that partition (sda5) it would not work as there is no free/unallocated space on the drive.

---

### Post by wjwh on 2024-03-26
Many thanks to all of you who have helped me.  I have now managed to install 22.04 in the way that i wanted.  I used gParted to delete the sda5 partition and then proceeded with the installation.  All went exactly as it should. Thanks again.

---

### Post by MAFoElffen on 2024-03-26
You are welcome. Glad to be of assistance.

So this is a done deal now?

We are responsible for closing "our own threads" when through. As the OP, if you go to the upper right of the first page of the thread, Select the "Thread Tools" link and mark your thread as "Solved". That helps others find what helped you find your answer, to help them with their own similar problems.

---

