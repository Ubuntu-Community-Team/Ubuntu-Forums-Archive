---
title: "Samba/CIFS no longer working after 8.04 upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by copperhead on 2008-04-28
I'm putting this in the upgrade section, since it was working before I upgrade, and now it's no longer working.

I don't like upgrading, so I backed up all my home directories, and some important configuration files like my /etc/fstab, and rebuilt my workstation from scratch.  My workstation had a samba mount to a samba share on a SUSE server named "gandalf".  Here's my setup. (Please don't comment on my lack of security. :))

On gandalf, I have a directory /raid/share that is exported via samba.  All the files in the directory are owned by nobody:nobody, and my guest account on my samba share is nobody.  My windows box can mount the shares and read and write just fine to the samba share.  As I said, up until this upgrade, my Ubuntu box could mount it read/write just fine as well.

In my /etc/fstab on my Ubuntu workstation, I had the following line...
```
//gandalf/share /mnt/gandalf    smbfs  rw,username=Copperhead,password=,uid=65534,gid=65533,dmask=777,fmask=777 0 0
```

Now, I was getting these new errors:
```
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.

```

Odd... apparently, I'm using CIFS instead of SMB.  Not a problem, though.  I changed the line to the following:
```
//gandalf/share /mnt/gandalf    smbfs  rw,username=Copperhead,password=,uid=65534,gid=65533,dir_mode=0777,file_mode=0777 0 0
```

Now I do a "touch /mnt/gandalf/temp" (it doesn't exist) and get the following results:
```
-rw-r--r--  1 nobody nobody         0 2008-04-28 22:32 temp
```

If I do a the touch command again, I get the following:
```
touch: cannot touch `temp': Permission denied
```

I tried messing around with a bunch of different things, but to no avail.  One thing interesting is that I have a share on a windows box, that I also used to be able to mount read/write with no problems.  I now get the same error as above when I mount it.

Something changed in the way my CIFS/SMB client works since the upgrade, and I'd like help in getting this resolved.  Thanks!

**EDIT:** I wanted to add that when I try to delete the temp file I create using the touch command above, I get the following prompt, but I can delete the file:
```
rm: remove write-protected regular empty file `/mnt/gandalf/temp'?
```

---

### Post by MetalMusicAddict on 2008-04-28
I was in the same boat as you. I only got around it by going to NFS. (doesn't really help you here)

So I actually had a fstab line very similar to you and even made the same changes. I didn't have the gid/uid entries though. I could get the drives mounted though. Just the permissions were all weird. ie: I would copy a group of 10 files, 2 would fail with permission errors. I tried those 2 again and it worked. Was weird.

My fstab before the change:
```
[SIZE="1"]//192.168.1.100/Storage	    /media/Storage        smbfs   username=user,password=pass,dmask=777,fmask=777 0 0[/SIZE]
```

After:
```
[SIZE="1"]//192.168.1.100/Storage	    /media/Storage        cifs   username=user,password=pass,dir_mode=0777,file_mode=0777 0 0[/SIZE]
```

Now that worked for me, but was weird.

---

### Post by jelvis on 2008-05-01
I had a similar problem (mounting the filesystem om my D-Link 323 NAS) and below follows how I worked around it. My only concern was to get it up and working, I have no idea about any potential side effects or security issues. 

Changed from smbfs to cifs.
Changed dmask to dir_mode.
Changed fmask to file_mode.

Complained that I couldn't use octal notation for the numbers.
Changed from 777 to 0777 for both dir_mode and file_mode.

Still had permission problems.

Added the noperm option and it all worked again.

You can read more about the noperm option here.
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by tom-ubuntu on 2008-05-02
Having exactly the same problem since the 8.04 upgrade (well, upgrade and new fresh installation).

This noperm option can not be the final solution, right?

---

### Post by jaishup on 2008-05-03
how do i solve this problem? i am facing the same problem.. :( that means we can;t use the cifs command? any other alternatives?

---

### Post by ubundom on 2008-11-04
Hi folks, I found an answer that worked for me in:

[http://ubuntuforums.org/archive/index.php/t-778746.html](http://ubuntuforums.org/archive/index.php/t-778746.html)

whereby I have mounted the samba share which is served from an NSLU2 that is running Linux 2.6.18-6-ixp4xx #1 Tue Feb 12 00:57:53 UTC 2008 armv5tel with a couple of Western Digital 500GB disks attached.

I used ```
sudo mount -t cifs //nslu2ipaddress/sharename ~/my_local_mountpoint -o username=my_samba_username,password=my_samba_password,uid=my_linux_username,group=users
```

Thanks for your help Edk for finding: [http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&p=58707](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&p=58707)

---

### Post by YorYor on 2008-11-08
For those who are getting a ```
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
``` error,

do this

```
sudo bash -c "echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled"
```

ref: [http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/](http://www.linuxquestions.org/questions/linux-networking-3/mount.cifs-mount-error-20-not-a-directory-443693/)

---

