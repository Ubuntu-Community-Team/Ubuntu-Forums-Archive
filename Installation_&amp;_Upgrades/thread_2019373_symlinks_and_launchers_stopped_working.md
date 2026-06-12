---
title: "symlinks and launchers stopped working"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by tg3793 on 2012-07-07
Just upgraded _from Lucid Lynx to Maverick Meerkat_ and my **symlinks  and launchers stopped working**. So far (it's been just a couple of hours) I 'think' that the only symlinks and launchers effected are the ones that used to refer to my external HD, which is MOST (several hundred) of my symlinks and launchers.

This actually happened within the first third of the upgrade process so there must be a configuration file somewhere, fstab or smb.conf (though I'm pretty sure I'm barking up the wrong tree on the latter one) that was altered or replaced.

I notice in nautilus, that the path of my external drive (at the top) still says "Signature Mini" like it always has. However when I do a "CTRL+L" to copy or edit the path, it will then include "/media/sdb1/" in the path name. It hadn't done that previously so I know there is a clue to what has happened there.

I've done some googling and ubuntuforuming, and I'm looking over [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) even as I post this. 

Help point me in the right direction if you can think of one; thanks!

---

### Post by tg3793 on 2012-07-10
Never mind. [[COLOR="Blue"]Morbius[/COLOR]]("http://ubuntuforums.org/member.php?u=982144") reached from the past and into the future [[COLOR="blue"]from this thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10544164&postcount=18") to give me the answers that I needed. And as I read over that thread I could remember the whole issue all over again. Which brings to my mind; how did that fstab entry get back in there again?

In any case, after commenting out the fstab entry for sdb1 completely, I followed the instructions below and everything was back to normal.


> **Morbius1 said:**
> 
Step 1: If you have the external drive mounted - unmount it.

Step 2: Disconnect the exteranl drive from the machine.

Step 3: Make sure your fstab entry for the external drive has been removed.

Step 4: Run the following command:
```
sudo mount -a
```

Step 5: Connect the external drive to the machine



---

