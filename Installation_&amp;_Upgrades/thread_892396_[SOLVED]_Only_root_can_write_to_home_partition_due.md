---
title: "[SOLVED] Only root can write to /home partition due to no space left on device"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by TC!! on 2008-08-17
I started with a 64 bit installation + decided to switch over to 32 bit (since it's supported by the XBMC team). I didn't want to lose my home folders so I created a new partition and installed 32 bit ubuntu there. I then moved all my original home folders to the base of the original partition and mounted it as home of the new installation.

My main user can login with no problems but I can't write onto this partition at all due to no space being available.

If I do this:
echo test > test

I get "-bash: echo: write error: No space left on device", but if I do it with sudo then it works fine.

df -h reports this:
Filesystem Size Used Avail Use% Mounted on
/dev/sda3 21G 2.6G 18G 14% /
varrun 251M 104K 251M 1% /var/run
varlock 251M 0 251M 0% /var/lock
udev 251M 64K 251M 1% /dev
devshm 251M 12K 251M 1% /dev/shm
lrm 251M 39M 213M 16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1 209G 202G 0 100% /home

That shows that there should be about 7G of space available, not 0.

I'm guessing that I have messed up how I mount my home directory, here is the line for it in my /etc/fstab:
/dev/sda1	/home	ext3	nodev,nosuid	0	2

Any help would be greatly appreciated.

---

### Post by TC!! on 2008-08-17
Just to add a bit more information, I used gparted and it shows that there is 3% space left on the partition, but I guess that runs as root, right?

Again, any help in fixing this would really be appreciated, I've already spent weeks trying to set up XBMC using ubuntu and now I'm going backwards.

---

### Post by kflorek on 2008-08-18
>I'm guessing that I have messed up how I mount my home directory, here is the line for it in my /etc/fstab:
>/dev/sda1 /home ext3 nodev,nosuid 0 2

OK, so how about

/dev/sda1 /home ext3 rw,nosuid,nodev 0 2

but I think these are all the defaults anyway so

/dev/sda1 /home ext3 defaults 0 2

would do the same thing.

>My main user can login with no problems but I can't write onto this partition at all due to no space being available.

If you create a new user, can he write into this partition or not?

 But, reading your original post, it sounds like you installed Ubuntu 32 and later added /home to your fstab, instead of letting the installer set up using /home, in which case there are possibly differences between what you have in /home and what Ubuntu 32 is looking for.

 You didn't bother to say whether the ID numbers are exactly the same, as I wondered before. I guess you thought that was too stupid to check out?  If you actually want help, you have to respond to it.

 What could possibly be so important in /home that you needed to preserve it as home? If it is 200G of data files, link to them. Dump the idea of a separate home  partition and put a link in the users home to the data files. At least you'll know you have a sane /home setup to start with. Then possibly you could copy the sane home to the different partition and have something working to compare with.

---

### Post by TC!! on 2008-08-18
Thanks for trying to help again.

I've tried creating a new user and he can't write either.
My main user is the same on both installations, so I guess they would have the same id? I now how to check the id of my current user (I looked in the passwd file), but how would I find out the user id of the user who owns those files?

I think I should have gotten around that problem by using sudo chown -R username:username /home/username

Thanks for the the idea of using links to get to the data. It is basically lots of video files which I want XBMC to be able to use. I had setup a user called XBMC so i could allow my old xbox running XBMC to access a share using that username. I always though of samba as being less secure so i wanted to do it as a separate user.

I'll try the defaults fstab idea and then try going back to the home on the disk just to confirm that the disk is writable when mounted normally.

---

### Post by TC!! on 2008-08-18
I tried rw,nosuid,nodev and it was the same.

I used the installer CD to go in and put the home folder back in the right place and removed the /home mount from /etc/fstab. I then booted back into the 32 bit installation + mounted the partition I use for home by using the Places menu on the desktop. When I tried to create a new folder it gave me the error message "No space left on device". I tried creating a folder through the terminal as well, it was mounted as /media/disk, but that didn't work either.  df -h showed me 0 space available again, even though only 202G of 209G was used. So it is exactly the same as before.

So it looks like it isn't down to me mounting it incorrectly but something at the file level.

One other thing, if I use sudo glkid I get this:
/dev/sda1: UUID="5b03d9d1-f2c6-42e1-8b2c-85f31cc2e408" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="f215799e-62af-48b4-bdab-5e97cf7782b9" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7509f65a-d529-4583-92b7-9f58be3188e5"

Is it right that sda1 says SEC_TYPE="ext2", that is the partition I'm having problems with.

---

### Post by TC!! on 2008-08-18
OK, I just got somewhere. I read about another guy having similar problems with an NTFS disk. In the end his problem was that files weren't being deleted so his disk really was full.

I just went in as root and deleted a large folder which i had already backed up to DVD and that free space is now showing up with df!!!!!
/dev/sda1             209G  198G  2.8G  99% /home

As you can see it is still only showing about 3G free when there should be about 11G.

When I tried deleting the original files to make space I did it using nautilus and I removed a 7G folder user rm -r from the command line.

Now that I have some space everything is working fine, but now how do I get back all my space?

I just tried deleting another large file ~2.5G via nautilus and then emptying deleted items and that shows up as extra space. I also tried deleting one using rm as my normal user and now that works fine as well!!

So it looks like when I created my new partition I used up all the free space from my original partition which meant it really was full. At that point for some reason deleting files didn't give the space back to the partition, but now it does. So at least I can carry on for now, but I would really like to know where my 7G has gone.

---

### Post by jtniehof on 2008-08-18
By default, 5% of the space on a filesystem is reserved for the root user. This is so that if the filesystem fills up, there's still a little space for root to come in and clean up the mess. You can change this percentage with the -m option of tune2fs; do not do this while the filesystem is mounted and read the manpage very carefully. This is a potentially dangerous operation.

---

### Post by TC!! on 2008-08-18
You beauty, that must be what's happening!!!! I managed to get into this situation by forcing the disk to fill up completely by using gparted to take away all the free space to make a new partition.

That's great, I can carry on with creating my XBMC!!

p.s. I'll post a link to this in my other thread 32 bit to 64 bit in case it helps someone else doing the same thing

---

