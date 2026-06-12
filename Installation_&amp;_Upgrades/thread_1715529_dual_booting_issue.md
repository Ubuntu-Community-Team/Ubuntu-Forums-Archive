---
title: "dual booting issue"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2011-03-27
i  dual boot windows and ubuntu on my laptop, i am using wubi... so if i want to uninstall ubuntu i can easily do that.

if i do not use wubi and install ubuntu on my laptop, dual boot with windows; i have unallocated free space on my hard disk; and then if i want to remove ubuntu, then what should i do??

i once tried to do this, i opened the disk management in windows and deleted the ubuntu partition and then when i tried to boot there was some grub error.. infact i tried the same thing with open suse, i got the same error.. so i had to format the entire laptop and install windows again..

plz provide some solution urgently..

---

### Post by spiky001 on 2011-03-27
You have to repair the MBR [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by ubun2warrior on 2011-03-27
will the above method work with windows vista and 7 also..

if i do not have the windows install disc or repair disc, then how will i perform the above method..

---

### Post by Quackers on 2011-03-27
You make a repair disc :-)
In Windows Vista or 7 > Start > Control Panel > Backup & Restore Centre, then in the left pane of that window click on "make a recovery cd", put a blank cd in the drive and off you go :-)

---

### Post by Rubi1200 on 2011-03-27
This is a more comprehensive guide to restoring bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

>  if i do not have the windows install disc or repair disc, then how will i perform the above method..     By installing a basic Windows-like bootloader called lilo. This can be done from a LiveCD:

Go to System > Administration > Synaptic and under Software Sources or Repositories place a check mark next to universe enabled.

Then, go to Applications > Accessories > Terminal and run these commands:

```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```This assumes that sda is the Windows drive. If not, change this to reflect the actual drive e.g. sdb, sdc, etc. 

Ignore any warnings and continue with the installation to the MBR. The  main point is to get lilo installed and allow the user to boot Windows.

EDIT: and there is Quackers' way :-)

---

### Post by ubun2warrior on 2011-03-29
> **Rubi1200 said:**
> This is a more comprehensive guide to restoring bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

By installing a basic Windows-like bootloader called lilo. This can be done from a LiveCD:

Go to System > Administration > Synaptic and under Software Sources or Repositories place a check mark next to universe enabled.

Then, go to Applications > Accessories > Terminal and run these commands:

```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```This assumes that sda is the Windows drive. If not, change this to reflect the actual drive e.g. sdb, sdc, etc. 

Ignore any warnings and continue with the installation to the MBR. The  main point is to get lilo installed and allow the user to boot Windows.

EDIT: and there is Quackers' way :-)

hi

thanks for replying..

suppose i did not perform any of the above mentioned stuff and then someone deletes the ubuntu partition and then error occurs, then what do i do??

can i also repair grub using ubuntu live cd or any other linux live disc (lilo is one good option as u sugggest... )

regards

---

### Post by Sean Moran on 2011-03-29
> **ubun2warrior said:**
> hi

thanks for replying..

suppose i did not perform any of the above mentioned stuff and then someone deletes the ubuntu partition and then error occurs, then what do i do??

can i also repair grub using ubuntu live cd or any other linux live disc (lilo is one good option as u sugggest... )

regards
If someone somehow sneaks up while you're out and deletes the Ubuntu partition, then the Live CD can fix the MBR in around ten minutes.  Just boot off the live-CD, and install it.  It'll find anything else of value in the way of operating systems, (and more) and set a nice fresh MBR with a nice new GRUB.  Viola!

---

