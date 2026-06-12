---
title: "fstab and automount only for my user"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by supersopa on 2015-02-01
hi guys!
I hope to have chosen the right forum where to write this post.

I share my laptop with ubuntu with my girlfriend, she uses the guest account and me a proper one. I would like that my two nfts partitions would auto mount and would be accessible at the boot boot time only for my user (uid 1000) and not for the guest account. I have tried several combination of options but I am still not able to sort my need out. The current options in the fstab are the followings:

uid=1000,rw,exec,noauto 0 0

but I would have the auto mount only for my user uid 1000

how could I make it?

many thanks!! :)

---

### Post by TheFu on 2015-02-01
Make certain that the mount point locations don't allow "other" any access.  This will need to be in the mount command for NTFS. Make certain the owner and group are for the userid you want.  uid= and gid= and file_mode and dir_mode are the options according to the mount.cifs manpage.

Just to clarify - are you mounting through the fstab or using automounter?

---

### Post by Morbius1 on 2015-02-01
> uid=1000,rw,exec,noauto 0 0
Not sure why you have it set to noauto but umask appears to be your answer.

umask represents the permissions you want to remove from the ways ntfs partitions mount by default. A "0" removes nothing and a "7" removes all permissions so a umask of 077 allows only the owner of the mounted partition ( uid=1000 ) to gain access to the partition:
> uid=1000,rw,exec,noauto,[COLOR=#0000cd]umask=077[/COLOR] 0 0
I'd really get rid of the noauto option if these are internal partitions if I were you:
> uid=1000,rw,exec,[COLOR=#0000cd]umask=077[/COLOR] 0 0

---

### Post by supersopa on 2015-02-01
thank you very much [**[COLOR=#000000]Morbius1[/COLOR]**]("http://ubuntuforums.org/member.php?u=982144")! :) it works :) yes that was the best solution I did not think about it ... it is my fault :)

---

