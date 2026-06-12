---
title: "Can anyone help me with an Arch Install?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Joe Ker1086 on 2009-11-27
Hello, I know this is not exactly the right forum but I am having a lot of trouble installing arch linux.....posted on that forum but no one seems to be able to help. This is my second install of Arch.....and it failed again. It said it could not locate the super block for /root. I used the by-label naming scheme and had a /boot, swap, /root and /home directory. /root and /home were both ext4, /boot was ext2. For some reason when checking file systems it could not locate the superblock on /dev/disk/by-label/root. When i tried to use the by-label to replace the superblock it could not be found so i had to use /dev/sda3 (which was /root) I tired several different superblocks (located with systemrescuecd-testdisk) with no success. obviously i am doing something wrong and i would really like to fix it....when i try to access /etc/fstab it says permission denied....i was going to try and rename them by uuid but if i cant get in here i dont know how i would. i already got the uuid for each partition its just a matter of assigning it in fstab now i think.......i really dont wanna give up on arch so please help me out.

---

### Post by robrink on 2009-11-27
Dude, I've read all your posts in the Arch forum (I'm a member there).You've been helped plenty in the Arch forums! You're just not grasping some fundemental concepts about partioning and installing.

---

### Post by snowpine on 2009-11-27
Ubuntu is an ethic or humanist philosophy focusing on people's allegiances and relations with each other. The word has its origin in the Bantu languages of southern Africa. Ubuntu is seen as a classical African concept. The Ubuntu operating system was named for this principle.

---

### Post by SuperSonic4 on 2009-11-27
> **snowpine said:**
> Ubuntu is an ethic or humanist philosophy focusing on people's allegiances and relations with each other. The word has its origin in the Bantu languages of southern Africa. Ubuntu is seen as a classical African concept. The Ubuntu operating system was named for this principle.

We don't like spam. kthx

I installed arch yesterday and oddly had the same problem - that fstab would not recognise UUIDs. Eventually I commented out those lines and changed them to /dev/sdxy

Best place for mounting woes is **[http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)**

---

