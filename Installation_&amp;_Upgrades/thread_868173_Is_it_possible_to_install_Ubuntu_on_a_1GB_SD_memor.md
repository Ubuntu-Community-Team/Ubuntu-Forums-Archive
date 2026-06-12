---
title: "Is it possible to install Ubuntu on a 1GB SD memory card?"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Virtua-Touch on 2008-07-23
I just want to know because my mother hasn't bought my 2GB Flash Drive and all I have is my Camera's 1GB SD memory card. (I an use it as a mass storage device which made me think)

---

### Post by tamoneya on 2008-07-23
1 GB is a little small for ubuntu.  That will be fine for something like Damn small linux or Puppy linux though.  It may even be worth giving fluxbuntu or xubuntu a try.  They are lighter weight versions of ubuntu.

---

### Post by snowpine on 2008-07-23
> **tamoneya said:**
> 1 GB is a little small for ubuntu.  That will be fine for something like Damn small linux or Puppy linux though.  It may even be worth giving fluxbuntu or xubuntu a try.  They are lighter weight versions of ubuntu.

Base install of Xubuntu is about 1.5 gigs and Fluxbuntu is about 2. It may be possible to slim them down I suppose...

---

### Post by sisco311 on 2008-07-23
i'm running ubuntu on my 1gb mp3 player=hard disk:guitar:

ubuntu command line system + xorg + openbox + seamonkey(mozilla-mplayer, flash) 
+ xfe(file manager) ...
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


(4 weeks without a hard disk/bad sectors)

---

### Post by Virtua-Touch on 2008-07-23
How would I go about installing it onto my 1GB SD memory card? I don't really understand that.

---

### Post by tamoneya on 2008-07-23
> **sisco311 said:**
> i'm running ubuntu on my 1gb mp3 player=hard disk:guitar:

ubuntu command line system + xorg + openbox + seamonkey(mozilla-mplayer, flash) 
+ xfe(file manager) ...
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


(4 weeks without a hard disk/bad sectors)

that article refers to systems with small amounts of RAM not small amounts of harddisk.  It still may help make the install slimmer but by then it is a lot closer in terms of applications installed to fluxbuntu and xubuntu.  Wouldnt it be easier to start with those and strip them down?

---

### Post by sisco311 on 2008-07-23
> **tamoneya said:**
> that article refers to systems with small amounts of RAM not small amounts of harddisk.  It still may help make the install slimmer but by then it is a lot closer in terms of applications installed to fluxbuntu and xubuntu.  Wouldnt it be easier to start with those and strip them down?
installing xubuntu or fluxbuntu exceeds 1gb
ubuntu command line system ~ 440mb
xorg ~ 180mb
seamonkey ~ 160mb
mplayer + mozilla-mplayer ~ 40mb
flashplugin-nonfree (tricky) ~ 8mb
xfe(file manager), xfce4-terminal, xfce4-panel, pdf2txt, hsetroot (wallpaper), ivman(automounting)



 > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             912M  846M   18M  98% /
varrun                502M   68K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   40K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   43M  460M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/scd0             4.2G  4.2G     0 100% /media/cdrom0


---

