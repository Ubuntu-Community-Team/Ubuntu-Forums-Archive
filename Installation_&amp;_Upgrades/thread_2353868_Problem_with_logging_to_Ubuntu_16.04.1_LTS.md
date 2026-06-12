---
title: "Problem with logging to Ubuntu 16.04.1 LTS"
date: 2017-02-25
forum: Installation &amp; Upgrades
---

### Post by ModyKing on 2017-02-25
After a regular update using Software Updater, Ubuntu froze and stopped responding to any input from keyboard. I tried to do a fresh restart, but now I cannot go beyond the blinking cursor and black screen that does not respond to any input from keyboard.

After login using Live CD, you can see the output from "boot-repair" in [http://paste2.org/GcpgcVkJ](http://paste2.org/GcpgcVkJ) and the output from "dmesg" in [http://paste2.org/JBMjM82x](http://paste2.org/JBMjM82x)

---

### Post by RobGoss on 2017-02-25
Have you tried booting to an earlier **kernel **might be worth a try

I'm not sure what may have caused your lock out

---

### Post by ModyKing on 2017-02-25
> **RobGoss said:**
> Have you tried booting to an earlier **kernel **might be worth a try 
Yes, but it didn't work out. I couldn't load the Grub at all and it doesn't respond to any input from keyboard. I can only see a blinking cursor in a black screen like this 

[IMG]https://i.stack.imgur.com/VBCJO.jpg[/IMG] 

> **RobGoss said:**
>  I'm not sure what may have caused your lock out 
I think that it is a problem with the hard disk; the partition **/dev/sda1** that Ubuntu installed on it appears to be not mounted. 
Here are the output from

[B]sudo blkid
[/B]```
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="96E9-5126" TYPE="vfat" PARTUUID="0002f0af-01"
/dev/loop0: TYPE="squashfs"
/dev/sda1: PARTUUID="c8019649-01"
/dev/sda5: PARTUUID="c8019649-05"
```

[B]sudo blkid -c /dev/null -o list
[/B]```
/dev/loop0 squashfs         /rofs          
/dev/sda1                   (not mounted)  
/dev/sda5                   (not mounted)  
/dev/sdb1  vfat    UBUNTU 16_0 /cdrom      96E9-5126
```

---

### Post by RobGoss on 2017-02-25
I was thinking maybe you can use **Nomodest**  to gain access to the system once in, you can probably use Ubuntu's **Disk utility** to fix the partitions that are not mounting correctly  [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

Maybe someone else can share some insight on this also

---

### Post by cariboo on 2017-02-25
I'd suggest you start in recovery mode, and select root prompt from the menu, if it asks you to mount your partitions in rw mode say no. then at the prompt type the following command:

```
 fsck /dev/sdaX
```

for dev/sdaX use the partition your install is located.

---

### Post by deadflowr on 2017-02-25
The problem is a bad superblock.
essentially the same as this:
[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/]("https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")
failing repairing the superblock is using [testdisk]("https://help.ubuntu.com/community/DataRecovery#Testdisk")/ [photorec]("https://help.ubuntu.com/community/DataRecovery#Photorec") to recover the files and do a clean setup (reformatting the hard drive, et al)

---

