---
title: "moving encrypted /home"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2010-05-28
I am having a problem trying to move my newly installed /home directory from the / partition to a new partition. I inadvertently forgot to do that on install of Lucid Lynx. Because I selected to encrypt the /home directory the old way of moving home doesn't want to work because of not being able to read the data on the directory.

So does anyone know how to do this without breaking the whole system.

---

### Post by jaezcurra on 2010-05-28
Some problem here.  I would like to find a solution too.

---

### Post by tropdoug on 2010-05-30
Bump bump

---

### Post by tropdoug on 2010-06-03
is ANYONE HOME??? surely in the wide world of linux, someone must know how to move the encrypted /home dir to a new partition....... please

BUMP!

---

### Post by tropdoug on 2010-06-04
Well for the first time ever in the ubuntu world (2.5yrs) I am dismayed to find no one interested in trying to help.

---

### Post by alterpinguin on 2010-06-04
> **tropdoug said:**
> Well for the first time ever in the ubuntu world (2.5yrs) I am dismayed to find no one interested in trying to help.

lol ---
first, i only used the "encrypted home" for some testings
and i guess you are speaking about the "encrypted filesystem part" of
home/username that is stored somewhere in /var (if i remember this right).
This is different from the "normal" way to use an encrypted partition.
The encryption is based on single files, not of the whole /home/username-directory.
I hope you understand the difference.
You might want to go for an encrypted partition, which is mounted under /home
or for one user under
/home/username
A transition to this is done the same way like every transition to put parts of the root-filesystem to different partitions (harddisks...).
Like putting /var to an extra partition
or /boot to a special small one
or ..  (what you are thinking about) put /home to another one.
-
one way:
1. create the new partition with encryption and formated filesystem
2. mount it for example under /mnt
3. copy (you may use rsync) all your files to this new place
4. disable the "filesystem-encryption" for your user (search for doing this encryption after install and undoing it..  there should be entries)
and this could be the first step to be done, then you deal with a normal /home-directory setup.
5. setup the new partition to be mounted at the new place in fstab, and 
(if i remember right) the encrypted entry in crypttab.
....

---

### Post by tropdoug on 2010-06-04
Thanks for that, I shall go away and try to work through it.

---

### Post by alterpinguin on 2010-06-05
> **tropdoug said:**
> Thanks for that, I shall go away and try to work through it.

one larger text about ecryptfs in linux-magazine:
> [http://www.linux-mag.com/cache/7568/1.html](http://www.linux-mag.com/cache/7568/1.html)
and
you should check the sourceforge-site of ecryptfs
there are a lot more faq, answer+questions
dealing about moving around files from the ecryptfs.

Instead of the "Private" directory in home, one
could setup another and store files encrypted there
and the because the encryption is done on file-basis
it is possible to move those files around. There is
even the option not to encrypt the filenames, only the content.
But the backdraw is the additional disk-space used for the
encrypted files.
Update: they moved to launchpad, new link
> [https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)
and checkout the nice interview from Dustin Kirkland,
link is on this site too
> [https://launchpad.net/ecryptfs/+announcement/5017](https://launchpad.net/ecryptfs/+announcement/5017)

---

### Post by tropdoug on 2010-06-08
Thanks for the help, unfortunately nothing seemed to work, and in desperation I re installed and this time made sure I formatted my partitions correctly and did NOT encrypt my /home directory. So all is well in that direction at least

I shall continue to read about the encryption stuff until I understand it.

---

