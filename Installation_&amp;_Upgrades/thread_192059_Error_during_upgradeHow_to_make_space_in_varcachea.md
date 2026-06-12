---
title: "Error during upgrade:How to make space in var/cache/apt/archives?"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by tomash_cz on 2006-06-08
Hello, I was trying to upgrade breezy to dapper today via update-manager but  later on it showed an error saying that not enough space in var/cache/apt/archives. i already did sudo apt-get clean, but it's still the same. following is the report after df command in terminal:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.1G  4.4G  690M  87% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda2              19G   12G  6.7G  65% /data
/dev/hda1             9.4G  8.9G  459M  96% /windows

apparently there is still 690M space, but i don't know how to make space in var/cache/apt/archives/. Could you please help me with this? Thank you very much!

Ps.: as a newbie please kindly explain the solution to me step by step

---

### Post by karthik085 on 2006-06-08
[QUOTE=tomash_cz]Hello, I was trying to upgrade breezy to dapper today via update-manager but  later on it showed an error saying that not enough space in var/cache/apt/archives. i already did sudo apt-get clean, but it's still the same. following is the report after df command in terminal:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.1G  4.4G  690M  87% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda2              19G   12G  6.7G  65% /data
/dev/hda1             9.4G  8.9G  459M  96% /windows

apparently there is still 690M space, but i don't know how to make space in var/cache/apt/archives/. Could you please help me with this? Thank you very much!

Ps.: as a newbie please kindly explain the solution to me step by step[/QUOTE]
Did you also try sudo apt-get autoclean...?

---

### Post by tomash_cz on 2006-06-08
i did sudo apt-get autoclean, but get following error again...

The upgrade aborts now. Please free at least 201M of disk space on /var/cache/apt/archives/. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by christhemonkey on 2006-06-08
Did you do apt-get clean?
Your apt-cache may just be full...

---

### Post by tomash_cz on 2006-06-08
yes, i did apt-get clean, also apt-get autoclean, but still it doesn't let me continue upgradeing and report an that error..

---

### Post by karthik085 on 2006-06-08
Try this link:
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/05/debian-linux-remove-unwanted-packages.php](http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/05/debian-linux-remove-unwanted-packages.php)

---

### Post by metoo on 2006-06-09
For the update the installer has to download all the packages first. Here apparently 690MB+210MB about 900MB, which you don't have on '/' (/dev/hda3) .
Make sure to have a bit extra space on the root drive over what apt is asking for, otherwise you can get problems. Happend to me and I could not login into KDE as a standard user.

So:
You can temporary or for the future use /dev/hda2 = /data for the archives directory:
- create a directory /data/archives
- delete /var/cache/apt/archives
- create a symbolic link from /var/cache/apt/archives pointing to /data/archives
   (I always use mc, midnight commander, for this, don't even know the command option. In mc: file-...)
Now you should have enough space as /dev/hda2 shows >6GB free.

After the hopefully successful update you can clear (sudo apt-get clean) the archive directory again, otherwise you will constantly loose the space of the installation packages, the 900MB.
Future updates should be much smaller.
You can revert the "achives" directory back to the root partition if you like:
- sudo apt-get clean
- delete /data/archives
- delete the symbolic link /var/cache/apt/archives
- create the directory /var/cache/apt/archives
From the next update on the new (old as today) directory will be used again.

---

