---
title: "upgrade to 11.04 from 10.10 using livecd didn't use existing /home partition"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by ZX3Junglist on 2011-05-28
I couldn't find a thread for this using the search, so here goes.

I used a 11.04 livecd to upgrade my existing 10.10 install. There was a large separate partition dedicated to /home, which when I upgraded, wasn't used. The upgrade prompted me to create a user, and then proceeded to create an all-new home folder off of /. When I boot, I can mount my old /home partition and see all of my files. I previously had two users, both named differently than the new user I created during upgrade. How would I go about restoring my old home partition? Note that I don't particularly care about the new user. The old ones would be fine. 

I've considered creating the two users again, removing the new home, and then changing my fstab, but I'm afraid I'll break something. Thanks!

here's my /etc/fstab:
# / was on /dev/sda5 during installation
UUID=72ed483d-20c7-4fd4-9c94-353a539a2ac3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6f1592d4-f43d-4f5e-9de9-24309b65f0d5 none            swap    sw              0       0

here's my blkid where sda7 is my old home:
/dev/sda1: UUID="2214A6FB14A6D159" TYPE="ntfs" 
/dev/sda5: UUID="72ed483d-20c7-4fd4-9c94-353a539a2ac3" TYPE="ext4" 
/dev/sda6: UUID="6f1592d4-f43d-4f5e-9de9-24309b65f0d5" TYPE="swap" 
/dev/sda7: UUID="dfe6bb56-b978-44da-8039-7c43260deb93" TYPE="ext4"

---

### Post by mikewhatever on 2011-05-29
Just a guess, but it looks like you've not upgraded, but rather installed 11.04 over 10.10. Creating a new user strongly suggests that it was, in fact, a clean install.

---

### Post by ZX3Junglist on 2011-06-02
Ok, that could certainly be the case. Given that, any thoughts on how I could revert to using the partition I was previously using for home, preferably keeping my files?

Thanks
-ZX

---

### Post by oldfred on 2011-06-03
It is just like moving to a new /home except you have already done the first few steps of creating partition & copying files. 

These three are all essentially the same except using different commands to copy. You primarily have to edit your fstab with the new /home.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This is who you are:
echo $USER
echo $HOME

Because you have changed userIDs you may have other issues. Not sure if this is all of them or not.
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 600 $HOME/.ICEauthority

Natty .ICE issues work around
[http://ubuntuforums.org/showthread.php?t=1738580](http://ubuntuforums.org/showthread.php?t=1738580)
[http://ubuntuforums.org/showthread.php?t=1746144](http://ubuntuforums.org/showthread.php?t=1746144)

---

