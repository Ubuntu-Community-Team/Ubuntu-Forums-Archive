---
title: "Copying folders from cifs shares does not work in 8.04"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by jpatadia on 2008-04-30
I just installed 8.04 on my desktop. After doing that [and enabling samba] I decided to copy directories from my shared Network File Server. It's a DNS-323 unit, which I believe uses cifs as it's file system. 

The strange thing I noticed was that I can copy files over from my dns unit, but I get errors when I try to get folders.

The error I get in nautilus is "Permission Denied", and no reason why I can't copy folders, but can copy files. Even if the folder is completely empty, it still can't copy it over.

I tried the operation as root, and it still gave the exact same error.

This is pretty annoying since I don't want to re-create the entire hierarchy tree from my unit.

Thanks,
Jalpesh.

---

### Post by katgfan on 2008-05-09
I'm also having exactly the same problem. I tried to google for answers but no luck. My nfs server is maxtor shared storage plus. I dont have this problem with 7.10 i did have a problem after a fresh install of 8.04. Can anyone shed some light?

---

### Post by katgfan on 2008-05-09
Well i did a fresh clean install of Hardy. And for a the file server im using a Maxtor shared storage plus which is working perfectly in Gutsy.

[http://reviews.cnet.com/external-hard-drives/maxtor-shared-storage-plus/4505-3190_7-31272119.html](http://reviews.cnet.com/external-hard-drives/maxtor-shared-storage-plus/4505-3190_7-31272119.html)

---

### Post by joefidler on 2008-05-12
Just noticed the same issue. When we copy a file from a Hardy workstation to our a Windows NAS - we get empty files. 

I am using CIFS with the following fstab file entry:

//200.1.1.3/servername /mnt/mountname cifs noperm,user=joe,pass=password,auto,exec,dir_mode=0777,file_mode=0777 0 0

Note the noperm option- I saw this in another post on this forum - it works around the file permission error.

Joe.

---

### Post by GoodPanos on 2008-05-17
Same problem here.  Worked great in Gutsy.  What happened in Hardy Heron?  Now you have to mount the folder manually.
```
//192.168.1.1/share    /media/share smbfs  credentials=/root/.smbcredentials,uid=user,gid=users  0    0
```

Does any know if this is a bug or you have to browse network shares differently now?

---

### Post by Mike'sHardLinux on 2008-05-20
Wow! This is a serious problem. I cannot get work done this way.

If I use fstab or the command-line to mount an smb share, they seem to mount and I can browse through folders and see files, but I cannot open them.

If I use the Connect to Server from the Places menu in Gnome, I can access the files fine, but the problem there is that most Gnome programs (eg., gFTP, FileZilla) won't allow me to browse to a share that is "mounted" this way...or at least I can't figure out how to do it. They only want to browse to actual folders in the file-system.

If I have more time I will find out if this is a known bug that has already been filed.

---

### Post by GoodPanos on 2008-05-27
Bump!  We can't be the only ones with this problem.

---

### Post by miraceti52 on 2008-06-14
There is a detailed discussion of this problem at Bug #185729.  I too have this problem with a WD hdd in my NAS.

---

### Post by miraceti52 on 2008-06-14
OOPS  I forgot the url!

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729)

---

### Post by michaelzap on 2008-06-14
Odd. I have a couple of network drives (a Buffalo LinkStation and an HP MediaVault) and they work fine for me in Hardy (as well as Gutsy, XP, Vista, and Xandros). They worked for me when I updated to Hardy from Gutsy, as well as with a fresh Hardy install.

My fstab entries use the following format:

```
//192.168.0.120/sharename /mnt/mountname cifs credentials=/home/username/.smbpasswd,uid=1000 0 0
```

Maybe I'm not experiencing the problem because I'm using a local text file for my credentials?

I do need to use the ip address instead of the device name to mount these, however.

---

### Post by miraceti52 on 2008-06-14
I seem to have an issue with the cifs file system my NAS uses samba but whether I use cifs in fstab or in mount it rejects the fs type.
I'm lost on this one so I guess I'll wait until the bug gets sorted :)

Thanks for your input though it was certainly worth a try :)

 sudo mount -t cifs  //192.168.1.253/public /home/user/MNT
mount: wrong fs type, bad option, bad superblock on //192.168.1.253/public,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by GoodPanos on 2008-06-17
> Maybe I'm not experiencing the problem because I'm using a local text file for my credentials?
If you use fstab it works fine; see my previous post.

Try this, though.  Open Nautilus and in the address bar type:
```
smb://<hostname>/<shared folder>
```
Try to copy a folder from within your shared folder to your local drive or home folder.  You should get a Permission Denied error.

---

### Post by GoodPanos on 2008-06-17
Just to add a bit more.  I think the reason why we are having these issues now is because when you browse a network share it now mounts the folder.  If you notice on the desktop you will see the folder links.  It's sort of doing it like MAC OSX.

In Gutsy and earlier versions it did not do that.  You were just able to browse the shares within Nautilus.  You could create bookmarks but it would never mount the shared folders.

That's what I think is happening; correct me if I'm wrong.

In Fedora 9 it's even worse.  When you browse a network share the folder contents are blank.

So is it the new kernel or Samba? :-k

---

### Post by michaelzap on 2008-06-17
> **GoodPanos said:**
> If you use fstab it works fine; see my previous post.

Try this, though.  Open Nautilus and in the address bar type:
```
smb://<hostname>/<shared folder>
```
Try to copy a folder from within your shared folder to your local drive or home folder.  You should get a Permission Denied error.

This works fine for me with no error.

---

### Post by GoodPanos on 2008-06-17
Do you want to tell us your secret?  Did it work right out of the box?  Were you browsing a folder that you already have mounted in fstab?

---

### Post by michaelzap on 2008-06-17
> **GoodPanos said:**
> Do you want to tell us your secret?  Did it work right out of the box?  Were you browsing a folder that you already have mounted in fstab?

It is a share that's already mounted in fstab, yes, so maybe that's my secret (?).

---

### Post by GoodPanos on 2008-06-17
That explains that.

We're back to square one.

:-|

---

### Post by michaelzap on 2008-06-17
> **GoodPanos said:**
> That explains that.

We're back to square one.

:-|

Can you not mount your shares in fstab until the issue is resolved?

---

### Post by GoodPanos on 2008-06-17
Yes, I could and I have the ones I mostly use.  However, I use a laptop and I take it back and forth to work and home and there are 100s of shares.  So, I can't mount every one of them.

Before, with Gutsy I would just browse the share I wanted, copy the folder or files I needed, and I was done.  I can still copy files but not folders and just like jpatadia I don't want to re-create the entire hierarchy tree for every folder I copy.

---

### Post by GoodPanos on 2008-07-09
It's fixed :guitar:

The new version of Ubuntu 8.04.1 LTS has this issue fixed.  I tried the live CD and was able to copy folders from Windows shares without any access errors.

---

