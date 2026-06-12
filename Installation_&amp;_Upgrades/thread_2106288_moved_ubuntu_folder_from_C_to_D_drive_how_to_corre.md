---
title: "moved ubuntu folder from C: to D: drive how to correct UUID entries"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2013-01-18
I had previous Ubuntu 11.10 installation which was done using Wubi in D: drive of my computer the corresponding grub.cfg entries are

[http://paste.ubuntu.com/1546414/](http://paste.ubuntu.com/1546414/)


now I wanted to use new Ubuntu 12.04 so I deleted the previous installation from D: drive 
then installed Ubuntu 12.04 I accidentally instead of installing it in D: drive I installed in C: drive  and grub entries here are
[http://paste.ubuntu.com/1546422/](http://paste.ubuntu.com/1546422/)

I was not having space in C: drive so I moved the ubuntu folder from C: drive to D: drive but I surprisingly could not boot, 
realizing that grub.cfg needed to be updated I opened the old grub.cfg (this 11.10 was installed  in D: drive) 

and checked the UUIDs  which are (for previous 11.10 install in D: drive) 

```
search --no-floppy --fs-uuid --set=root 8E9E86339E86143D 

linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=8E9E86339E86143D loop=/ubuntu/disks/root.disk ro
```

in the new 12.04 grub.cfg (which was accidentally installed in C: drive )

has following  (for 12.04 in C: drive) 
```
search --no-floppy --fs-uuid --set=root E4ACAFF5ACAFC082
linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=E4ACAFF5ACAFC082 loop=/ubuntu/disks/root.disk ro
```

I have since moved the entire Folder C:\ubuntu to D: drive so it is now D:\ubuntu 

what I notice is the old UUID entries (from 11.10 ) are not the same as the  UUID entries in 12.04 is there a way to fix this ,installation was done in C:\ by Wubi but now I have moved the entire folder of ubuntu to D: drive 
the OS was windows 7 ,Ubuntu 11.10 and Ubuntu 12.04

---

### Post by dabl on 2013-01-18
I'm not a wubi user, so take this for whatever it's worth.

When logged into Linux, an excellent command to see your partitions and UUIDs goes like this

```
sudo blkid -c /dev/null -o list
```

Then you can copy any of the UUIDs that you need, and paste it wherever it is needed, whether /etc/fstab or /boot/grub/.

---

### Post by jamesbon on 2013-01-19
Well some one solved the problem here
[http://askubuntu.com/questions/244758/moved-ubuntu-folder-from-c-to-d-drive-how-to-correct-uuid-entries/244839#244839](http://askubuntu.com/questions/244758/moved-ubuntu-folder-from-c-to-d-drive-how-to-correct-uuid-entries/244839#244839)

---

### Post by dabl on 2013-01-19
Nice!  :)

---

