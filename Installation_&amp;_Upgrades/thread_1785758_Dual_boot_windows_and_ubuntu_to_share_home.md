---
title: "Dual boot windows and ubuntu to share /home"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by civillian on 2011-06-18
I'm just about to install ubuntu alongside a windows 7 install (which was preinstalled), and while this isnt unusual (I've dual booted for a while on older machines), as I've been using this laptop for all kinds of work & photo editing etc, whereas before I used windows for games etc and the odd photo and used ubuntu for my primary OS.

To get to the point, is it possible to install ubuntu after windows 7 (with a root partition, and a /home partition), and effectively 'share' the 'C:\Users\Civillian' folders (my documents, my music, etc) with the '/home/civillian' partition?

I thought about creating a mass of symlinks (an inelegant solution) but I'm not sure about any other options I might have!

thanks
Civ

---

### Post by ajgreeny on 2011-06-18
If you make a separate partition on disk (called civilian) with ntfs format, for all your data files (docs, videos, photos, music etc) you can mount it in ubuntu at boot with an edit of /etc/fstab, then either use it directly from ubuntu, or if you prefer, create links to the folders in it in your ubuntu /home folder/partition.

Windows will see the ntfs partition with no problem, and if you get the fstab line right so will ubuntu.

What you can not do is have a partition mounted as /home on ubuntu and also used by windows, as /home has to be a linux filesystem in order for it to work (ext2, ext3, ext4, etc etc) and windows can not see that filesystem.  YOu can not have an ntfs partition as your ubuntu /home partition as the linux permissions are not possible in ntfs.

---

### Post by oldfred on 2011-06-18
I have a ext3 /data partition and a NTFS /shared partition. Now most of my new data goes into the /data.

If you put just folders in the data partition you can issue one command to link all the folders. If the names already exsist in /home it does not work.

#Or link all folders with one command, run in /home and use your mount of data folder:
for i in `echo /mnt/data/*`;do ln -s $i; done

I used to do this for each folder, but I am up to 14 folders and had to find a better way:
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data, default is to put link into location run from so run from /home.
ln -s /mnt/data/Music

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by J V on 2011-06-18
I just use symlinks. Desktop > my desktop, documents > my documents etc... Doesn't have encryption but you plan on using windows anyway :P

---

### Post by civillian on 2011-06-20
To be honest the fstab and more complex options are probably overkill, I think that just mounting the C:\ parition, and creating symlinks to the NTFS folders that I need (documents, pictures, music) which might actually be simpler (given that my music is in C:\Users\civillian\My Music\ipod\ipod media\music - out of necessity, really)

Thanks for the help, guys, I needed a bit of a memory jog, to get out of the windows mindset!

cheers.

[solved]

---

### Post by derekcentrico on 2011-11-27
Would you mind detailing what all you were able to symlink?  Did you find a way to link the two desktops?

I like the idea of using the Windows 7 libraries locations to allow for another partition to store all data on.  However, this wouldn't work for the two desktops. 

I know this is a "solved" thread, but I didn't want to open a new one when you all are already providing useful data here.

---

