---
title: "Reinstall over the top?"
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by Gibbz on 2004-11-29
is it possible ot reinstall ubuntu over the top of itself without it removing the installed packages/programs that ive added after?

Will it restore the files ive edited(ie fstab etc) ?

---

### Post by Magneto on 2004-11-29
[QUOTE=Gibbz]is it possible ot reinstall ubuntu over the top of itself without it removing the installed packages/programs that ive added after?

Will it restore the files ive edited(ie fstab etc) ?[/QUOTE]
 why not just backup your /home/user  and /etc and whatever other little things and do a clean install?

---

### Post by adbak on 2004-11-29
It doesn't seem likely that you'll be able to do so.

Next time you reinstall, make about a 10gb partition, a 1gb partition, and use the rest for another partition (feel free to make these partitions bigger or smaller).

Mount the 10gb partition as "/".  This will include all of the /usr, /etc, and so on -- everything except /home.
Mount the partition that contains the rest of the disk as "/home" so that whenever you reinstall Ubuntu or another distro (if you so happen to fall to the dark side) then your personal files won't change.
Lastly, mount the 1gb partition as swap.

If you do this, then you won't need to reinstall all your personal files, mp3s, etc (assuming they're on /home) after you reinstall a distro of choice.

---

### Post by Gibbz on 2004-11-30
Yeah i keep my personal files safe on another partition already.
Just i want to reinstall ubunu, but not have to download all my packages etc again as in Australia we have a cap on our internet.  :( 

So i will over write it without deleting my extra packages?

Ill backup the files ive changed then :)

Thanks

---

### Post by Magneto on 2004-11-30
just copy /var/cache/apt/ somewhere - reinstall and copy it back

---

