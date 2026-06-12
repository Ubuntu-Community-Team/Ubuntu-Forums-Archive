---
title: "Need to clone ubuntu 6.06 from sata drive to IDE drive"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by spyshagg on 2007-06-18
hi

like the topic says, i am in the need to clone my current ubuntu 6.06  sata disc to a pata disc

the way i see it, the SO knows the current installation in on sda.  After i clone it to a pata disc, it will be hda.  How will linux deal with it?   

do i need to change fstab from sda to hda before i clone?
thanks

---

### Post by spyshagg on 2007-06-19
cold weather outside, ehm?

oh yeah, about the topic, anyone can help?

thanks

---

### Post by Rui Pais on 2007-06-19
hi,
The only thing you need to do is change yours /etc/fstab and menu.lst of grub of the cloned one to the UUIDs of the clones.

As long as you are using UUIDs for partitions you don't need to care if its detected as /dev/sda or /dev/hda. The kernel will load the modules at boot as needed (smart creature).

---

### Post by spyshagg on 2007-06-19
ola rui :)

obrigado pela ajuda!

tenho então que fazer algo deste genero? ou é automático? 

[http://www.novell.com/documentation/sles10/stor_evms/index.html?page=/documentation/sles10/stor_evms/data/uuidbootx86.html](http://www.novell.com/documentation/sles10/stor_evms/index.html?page=/documentation/sles10/stor_evms/data/uuidbootx86.html)
> 3.3 Using UUIDs in the Boot Loader and /etc/fstab File (x86)

After the install, you can optionally use the following procedure to configure the UUID for the system device in the boot loader and /etc/fstab files for your x86 system.

   1.

      Install the SUSE® Linux Enterprise Server for x86 with no SAN devices connected.
   2.

      After the install, boot the system.
   3.

      Open a terminal console as the root user or equivalent.
   4.

      Navigate to the /dev/disk/by-uuid directory to find the UUID for the device where you installed /boot, /root, and swap.
         1.

            At the terminal console prompt, enter

            cd /dev/disk/by-uuid

         2.

            List all partitions by entering

            ll

         3.

            Find the UUID, such as

            e014e482-1c2d-4d09-84ec-61b3aefde77a —> /dev/sda1

   5.

      Edit /boot/grub/menu.1st file, using the Boot Loader option in YaST2 or using a text editor.

      For example, change

      kernel /boot/vmlinuz root=/dev/sda1

      to

      kernel /boot/vmlinuz root=/dev/disk/by-uuid/e014e482-1c2d-4d09-84ec-61b3aefde77a


depois disto, pelos vistos basta fazer o clone de todo o disco sata para o disco pata e o linux monta tudo devidamente. 

qualquer clarificação extra que possas dar era bem vinda :) 
thanks

---

### Post by Rui Pais on 2007-06-19
Olá, então és português? :)

Lets keep it in English so others can use it if they search for something like that.

There are software to do OS cloning for backups/replications... but i never use it, and can't be of much help there. 

I prefer doing by hand.

1st, don't do it from a live OS (its asking for trouble). 
Boot from a liveCD, mount both partitions, the one to be cloned and the one that will have the clone.
And copy with cp -a:
```
sudo cp -a /mnt/original/* /mnt/clone/
```

For backups is all what is needed. :) 

If you are duplicating the OS for using the copy,
then edit: /mnt/clone/etc/fstab
and change the UUID of the / (root) line for the clone partition one.

You can get the UUID of a partition with:
```
sudo vol_id -u /dev/*XXXN* 
```
or of all parftitons with:
```
blkid
```

Finally the boot is the delicate thing. 
If you will boot computer with both HDs connected, you need to add a grub entry for the clone. Since you will have always only one grub/boot you need to change the menu.lst of the original one. Replicate the entry and change UUID and (hdX,X) according with partitions.

If you will disconnect or even move the clone for another box. You need to reinstall grub booter on the MBR of the HD that contains the clone and make the changes on cloned /boot/grub/menu.lst. If you don't know how to reinstall grub on MBR, [here is an now-to]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8"). And [here a thread with simple tips]("http://ubuntuforums.org/showthread.php?t=224351") for do it. :)


Post any doubts or parts unclear, ok?

---

### Post by spyshagg on 2007-06-19
thanks

i was thinking about doing it all offline. 

i would boot the server with both harddrives connected, but i would never get to enter Operative system.

 I will  use my homemade boot cd (with clone tools, partition tools, diagnostic tools etc etc) to clone the SATA disc directly to the PATA disc.  you see?  without going the route you mentioned. 
If this was windows OS, the new drive would still be C:, so problem solved. But in linux i dont know the behaviour because SDx is diferent from HDx

what you said still applies if i do this? 
thanks for the touble of helping me :)

edit: the sata drive would be removed after the clone was done.

---

### Post by Rui Pais on 2007-06-19
De nada, é com gosto (o tal que evita cansar quando se corre) :lol:

As i said i don't know clone software... i suppose they will make you life easier, yes.

Just do it then, and after the cloning mount it and check the UUID in the same manner i posted. 
Cloning tools should be smart enough to copy MBR so thats a little less work. 
The UUIDs may be problematic. They are new around, but updated tools should deal with them normally.
Just check to see if they change anything to /dev/xxx and if not, if they are correct.

Anyway, the worst that can happen is clone not booting :)
and you can post any errors here and we check what had gone wrong.

boa sorte, 
diz como correu.

---

### Post by spyshagg on 2007-06-19
will do!  as soon as the 2x 1TByte hitachi harddrives arrive later this week, i will try and see if the direct clone image will boot.  I guess i'm back to trial and error :D 

thanks rui

---

### Post by Rui Pais on 2007-06-19
> **spyshagg said:**
> will do!  as soon as the 2x 1TByte hitachi harddrives arrive later this week, i will try and see if the direct clone image will boot.  I guess i'm back to trial and error :D 

he he, thats the good part of Linux. After finish cloning you can immediately mount it and check what was done, check errors, etc. 
You can even chroot to the clone and run it, before reboot :D

---

