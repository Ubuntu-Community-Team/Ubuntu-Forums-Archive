---
title: "permissions are denied on the Storage disc and going into FStab I do not even see the"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2012-05-04
I just installed Ubuntu 12.04 64 bit with a great deal of help from forum members. I installed a secondary hard drive for storage and want to set up symlinks in my Home folder on an SSD to direct to Music, Documents, video etc. However permissions are denied on the Storage disc and going into FStab I do not even see the drive listed. Here is my blkid output. I woould appreciate any help to get the drive listed in Fstab, automounting and giving perissions in my user account. 

```
david@david-desktop:~$ sudo blkid
[sudo] password for david: 
/dev/sda1: LABEL="EFI" UUID="04BC-5187" TYPE="vfat" 
/dev/sda3: LABEL="ROOT" UUID="fb91ba53-76d5-41af-aa6f-24035b6de7a4" TYPE="ext4" 
/dev/sda4: LABEL="HOME" UUID="89427c18-2e81-494e-baef-933d3216d968" TYPE="ext4" 
/dev/sda5: UUID="f531caff-a236-4f4c-a401-3b7fbc067c30" TYPE="swap" 
/dev/sdb1: LABEL="STORAGE" UUID="b3aaffec-03c9-40dd-b836-35d9346019cb" TYPE="ext4" 
david@david-desktop:~$ sudo umount /media/STORAGE
david@david-desktop:~$ sudo mkdir /media/STORAGE
david@david-desktop:~$ 

```

---

### Post by Morbius1 on 2012-05-04
fstab will only show the instructions on how you want to mount it if you put it there.

Open Nautilus and mount your "storage" disk. Then find out what the permissions are.

---

### Post by SuperFreak on 2012-05-04
I believe ROOT priviliges are needed. How would I change that to user.  See screenshot

---

### Post by Morbius1 on 2012-05-04
Take possession of the mounted partition:
```
sudo chown your-user-name /mountpoint
```For example, if your login name was morbius the command would be:
```
sudo chown morbius /media/STORAGE_
```

---

### Post by SuperFreak on 2012-05-04
I am afraid it didn't seem to work. I tried with and without the underscore after STORAGE


Must have made a mistake with syntax. Works now. Thanks

---

### Post by Morbius1 on 2012-05-04
What is the output of the following command:
```
ls -al /media
```

---

### Post by Morbius1 on 2012-05-04
You aren't done yet I'm afraid. In order to do this:
> I installed a secondary hard drive for storage and want to set up  symlinks in my Home folder on an SSD to direct to Music, Documents,  video etcYou will need to have the partition mount automatically when you boot. To do that:

**[1] Unmount the partition you just mounted in Nautilus:**
```
sudo umount /media/STORAGE_
```**[2] Edit fstab as root:**
```
gksu gedit /etc/fstab
```**[3] Add the following line to the end of fstab:**
```
UUID=b3aaffec-03c9-40dd-b836-35d9346019cb /media/STORAGE ext4 defaults,noatime 0 2
```**[4] Then save the file and run the following command that will test for errors in your edit and if there are none mount the partition:**
```
sudo mount -a
```

**[COLOR=Blue]EDIT[/COLOR]:** Please note that when you unmount /media/STORAGE_ that folder will automatically be removed. Since you already created a mountpoint at /media/STORAGE we used that as the permanent home of the mounted partition. Since you changed ownership of the mounted partition it's all set and you don't have to do a chmod again ( permissions stay with the partition not with the mountpoint ).

---

### Post by SuperFreak on 2012-05-04
I appreciate your help but I am finding that the symlinks do not work that I placed in the HOME folder. I placed Symlink for example for Music left link in Home and put original Music folder in STORAGE

---

### Post by Morbius1 on 2012-05-04
I have to leave for the airport in a few minutes so .....

Run the following command to show how the symlink is set up:
```
ls -dl /home/david/Music
```Based on your description it should come back with something like this:
> lrwxrwxrwx 1 david david 10 May  4 15:03 [COLOR=DarkGreen]/home/david/Music[/COLOR] -> [COLOR=Blue]/media/STORAGE/Music[/COLOR]

---

### Post by SuperFreak on 2012-05-04
```
david@david-desktop:~$ ls -dl /home/david/Music
ls: cannot access /home/david/Music: No such file or directory
david@david-desktop:~$ 

```

 Ithink I have this all wrong. I am trying to limit writes on my SSD and keep large volumes (ie music) on my storage drive and have it linked through the Home directory which is on the SSD. If I reboot the links stop working. To create a link I am right clicking on a folder and choosing "Make Link" and then moving the original folder to STORAGE

---

### Post by oldfred on 2012-05-04
I use command line to make links.

#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

If you have mounted it in fstab as /media/STORAGE
ln -s /media/STORAGE/Music


this takes every folder & I only have folders in my /mnt/data
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Everytime I read Morbius1 posts I find I am doing something wrong on permissions & ownership. I learned some more in this thread. :)

---

### Post by Morbius1 on 2012-05-05
> To create a link I am right clicking on a folder and choosing "Make Link" and then moving the original folder to STORAGEThis is one of a couple or reasons why I really dislike using symlinks. You are doing the reverse of what I think you want to do. 

First, move the Music folder to /media/STORAGE  ( and it sounds like you already did that ). Then make a link of /media/Storage/Music and move the Link to your home directory.

A symlink references an absolute path so the way you have it now the symlink is referencing a folder at /home/david/Music that is no longer there.

---

### Post by SuperFreak on 2012-05-06
Thanks to both of you.I will try your suggestion Morbius

---

