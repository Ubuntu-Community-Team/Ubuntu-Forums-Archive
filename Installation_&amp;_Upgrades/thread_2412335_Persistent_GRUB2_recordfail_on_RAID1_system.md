---
title: "Persistent GRUB2 recordfail on RAID1 system"
date: 2019-02-11
forum: Installation &amp; Upgrades
---

### Post by Leechpool on 2019-02-11
Hi,
I've installed Ubuntu 18.04 on RAID1.
```
myth@myth-system:~$ lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda       8:0    0  1.8T  0 disk  
&#9500;&#9472;sda1    8:1    0 65.2G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0 65.2G  0 raid1 /
&#9500;&#9472;sda2    8:2    0 18.6G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0 18.6G  0 raid1 [SWAP]
&#9492;&#9472;sda3    8:3    0  1.8T  0 part  
  &#9492;&#9472;md1   9:1    0  1.8T  0 raid1 /media/DATA
sdb       8:16   0  1.8T  0 disk  
&#9500;&#9472;sdb1    8:17   0 65.2G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0 65.2G  0 raid1 /
&#9500;&#9472;sdb2    8:18   0 18.6G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0 18.6G  0 raid1 [SWAP]
&#9492;&#9472;sdb3    8:19   0  1.8T  0 part  
  &#9492;&#9472;md1   9:1    0  1.8T  0 raid1 /media/DATA
sr0      11:0    1 1024M  0 rom   


```

To install GRUB, I used
```
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
sudo update-grub

```
I set the grub menu to always show but only for 3 seconds

This has worked fine for a few months but recently instead of 3 seconds it was counting down 30s before booting.
I did some googling and found that adding 

GRUB_RECORDFAIL_TIMEOUT=15

to /etc/default/grub and updating caused the timeout to reduce to 15s.
It does this every time I boot even though there are no problems I'm aware of booting.
It seems as though there is a persistant recordfail somewhere.

I found references to ```
sudo grub-editenv list
and
sudo grub-editenv - unset recordfail
``` but the first command didn't reveal any records. Then I learnt that /boot/grub/grubenv doesn't work with RAID partitions.

So I seem to have a persistent recordfail but I don't know how to remove it?

If someone understands the above and could offer some advice on how to fix the recordfail, I'd appreciate it. I already tried reinstalling GRUB using the three lines above but it didn't have any effect.
It's not a big issue as I can control the menu display time through GRUB_RECORDFAIL_TIMEOUT, but I'd like to fix it properly if I could.... or at least understand what's going on (this is the first time I've encountered GRUB recordfail).
thanks
:)

---

### Post by Leechpool on 2019-02-11
Writing the above out made me think. I do get an error during boot, although it always seems to carry on and boot ok...

```
myth@myth-system:~$ cat /var/log/syslog | grep apport
Feb 11 17:16:09 myth-system systemd[1]: apport-autoreport.service: Main process exited, code=exited, status=1/FAILURE
Feb 11 17:16:09 myth-system systemd[1]: apport-autoreport.service: Failed with result 'exit-code'.
Feb 11 17:16:12 myth-system apport[1878]:  * Starting automatic crash report generation: apport
Feb 11 17:16:12 myth-system apport[1878]:    ...done.
Feb 11 17:16:12 myth-system systemd[1]: apport-autoreport.service: Main process exited, code=exited, status=1/FAILURE
Feb 11 17:16:12 myth-system systemd[1]: apport-autoreport.service: Failed with result 'exit-code'.

```
Could this explain the recordfail?

thanks
:)

---

### Post by dmnur on 2019-02-11
See here: [https://ubuntuforums.org/showthread.php?t=2412153](https://ubuntuforums.org/showthread.php?t=2412153)

---

### Post by Leechpool on 2019-02-11
dmnur,
Thanks for the quick reply. Bug report seemed to match (I don't really understand the technicalities enough to be sure). Updated the system and it fixed the issue. :)
Really appreciate you pointing me to it.
Cheers

---

