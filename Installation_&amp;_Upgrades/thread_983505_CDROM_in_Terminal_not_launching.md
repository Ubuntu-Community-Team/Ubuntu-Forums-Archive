---
title: "CDROM in Terminal not launching"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by ronux on 2008-11-15
Hello All,

Installed on an old IBM Pentium III with Ram 500MB.
CDROM Acer CD ReWriter (I believe 8X).

Installed Xbuntu 8.10 via LiveCD - no problem.

CDROM seems not working after installation. Cannot playback any music. No icon on desktop or displayed in File System UI.

In Terminal tried this:

```
cat /etc/fstab

```

I get this for the CDROM info:
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

then did this to mount it
```
sudo mount /dev/scd0 /media/cdrom0

```

After password it hangs.
Nothing else.

I am baffled...

Moreover why is that I was able to use the CDROM for the installation but after the OS is installed it does not work?

Thanks for your feedback.

R -

---

### Post by argail1980 on 2008-11-15
hi,

I don't know if that causes your problem, but it should say "ro" instead of "rw" in the fstab entry for a cdrom

> /dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0


 btw, to mount the cdrom,

```
sudo mount /media/cdrom
```

should be sufficient.

---

### Post by ronux on 2008-11-15
Thanks argail1980 but both of your suggestions did not work :(

With your line
```
sudo mount /media/cdrom
```
in Terminal it does not hang (!) any longer but it states 
" No medium found "

...do not understand why...

R.

---

