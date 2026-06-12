---
title: "Installing Ubuntu in a fixed partition"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Drcyclops on 2010-01-11
[FONT=Calibri][SIZE=3]Please could someone advise me how to install ubuntu 9.10 into a predefined (fixed) partition on my Windows 7 based computer?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I have Windows 7 installed on my computer on the first physical drive which is partitioned as C, D and E. [/SIZE][/FONT][FONT=Calibri][SIZE=3]sda3 is Windows drive D and is the partition where I wish to install ubuntu 9.10 [/SIZE][/FONT][SIZE=3][FONT=Calibri]and sda5 is Windows drive E for the data.[/FONT][/SIZE]

---

### Post by J V on 2010-01-11
edit your post to remove [SIZE=5]RANDOM SHOUTING[/SIZE] and someone might answer, thanks...

---

### Post by Elfy on 2010-01-11
If you get a no root defined message it is beacuse you haven't done so - when you are in the manual partition window - select the partition which you wish to install to and click the Edit button - in the new window you can selct a mountpoint - which needs to be /
> 
Reading some of the forums there is something about home, usr and swap partitions I would not personally bother with /usr - I sometimes have a seperate /home though.

> ...
there is a problem with the Grub supplied with ubuntu 9.10I had a problem when it was in alpha but not since - as you are doing a clean install it is likely that it will be ok.

> Am I right in thinking that there is no physical sda4? Please could you tell me why this is so?I would guess that you haven't made a new primary partition, sda5 is normally an extended partition.

Might be worth running this in a terminal on the livecd (terminal is in apps > accessories) 

```
sudo fdisk -l
```

That will give us more information about the partitions on your machine.

---

### Post by Drcyclops on 2010-01-24
Many thanks for your help forestpiskie. I have now a PC working as a dual boot machine for Windows 7 and Ubuntu 9.10! At first I did not split the partition as I forgot the swap volume. Anyway, on the second attempt everything loaded up okay and the system worked fine.
 
I still have a problem in trying to set the grub default to 4 so that Windows 7 is main operating system. Not sure what to do about this at the moment.

---

### Post by darkod on 2010-01-24
> **Drcyclops said:**
> Many thanks for your help forestpiskie. I have now a PC working as a dual boot machine for Windows 7 and Ubuntu 9.10! At first I did not split the partition as I forgot the swap volume. Anyway, on the second attempt everything loaded up okay and the system worked fine.
 
I still have a problem in trying to set the grub default to 4 so that Windows 7 is main operating system. Not sure what to do about this at the moment.

Write down the exact title of the windows entry from the grub menu, like "Windows 7 Loader on (/dev/sda1)".
Boot ubuntu and in terminal open:
sudo gedit /etc/default/grub

In the line GRUB_DEFAULT= put the full name of the windows enty. This will make it default even after it's not number 4 like after kernel updates for example.
Or you could just change it to GRUB_DEFAULT=3 if the win7 entry is 4th in grub menu (it's always the position minus one). But you would have to change this if win7 is not 4th any more later.

Save and close the file after the change and run:
sudo update-grub

for new grub.cfg to be created.

---

