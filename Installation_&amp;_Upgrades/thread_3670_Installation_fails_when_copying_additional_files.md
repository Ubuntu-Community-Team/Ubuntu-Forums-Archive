---
title: "Installation fails when copying additional files"
date: 2004-11-08
forum: Installation &amp; Upgrades
---

### Post by danielo on 2004-11-08
Hi all,

When trying to install Ubuntu 4.10 I get an error, in "copying additional packages" step the installer says  that i don't have enough free space to write on /var but I have a 8.4 Gb hdd.

Please anyone can help me?

---

### Post by FLeiXiuS on 2004-11-08
[QUOTE=danielo]Hi all,

When trying to install Ubuntu 4.10 I get an error, in "copying additional packages" step the installer says  that i don't have enough free space to write on /var but I have a 8.4 Gb hdd.

Please anyone can help me?[/QUOTE]


Did you manually partition your drives during installation?

---

### Post by Yomanz on 2004-11-26
I seem to have the same prob.  Base installation packages all go well, but when the 'additional packages' are being installed > no more diskspace. I can't even install "Grub bootloader" because of the same error. Lilo on the otherhand does install ?

My Scsi Disk was partioned manually, because of dual boot. But I allowed the installer to automatically partition the free space. And during another attempt, I did the partioning myself. 

Both attempts had the same result: not enough diskspace ....

Any ideas what might be wrong?

Yoman

(using a Dell Precision 530, 2 U160 scsi disks connected to the onboard adaptec  controller)

---

### Post by p!=f on 2004-11-26
Post the output of df -h here please
```

 * 13:56:03 * pef @ agonicus *
[~] > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             228M  122M   94M  57% /
tmpfs                 380M   12K  380M   1% /dev/shm
shm                   380M   12K  380M   1% /dev/shm
/dev/hda7              67M   15M   49M  23% /boot
/dev/hda14            2,8G  2,1G  555M  80% /home
/dev/hda4              32G   19G   12G  62% /home/store
/dev/hdb2              32G  5,5G   25G  19% /home/store/audio
/dev/hdb3              38G   33G  3,2G  92% /home/store/video
/dev/hda11            3,3G   74M  3,0G   3% /opt
/dev/hdb1             5,1G  2,0G  2,9G  40% /opt/games
/dev/hda15            221M  4,4M  205M   3% /root
/dev/hda13            456M  8,1M  424M   2% /tmp
/dev/hda12            4,8G  2,7G  1,9G  59% /usr
/dev/hda9             1,8G  143M  1,6G   9% /var
/dev/hda10            228M   99M  118M  46% /var/log

```

---

### Post by wallijonn on 2004-11-26
is there a sym link between var under root on hda3 and /var on hda9&10?

---

### Post by p!=f on 2004-11-26
[QUOTE=wallijonn]is there a sym link between var under root on hda3 and /var on hda9&10?[/QUOTE]
No. Everything has its own partition so I can mount it with appropriate options.
ie. /var/log is mounted with nosuid,nodev,noexec.

---

### Post by quickball on 2005-01-17
[QUOTE=p!=f]Post the output of df -h here please
```

 * 13:56:03 * pef @ agonicus *
[~] > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             228M  122M   94M  57% /
tmpfs                 380M   12K  380M   1% /dev/shm
shm                   380M   12K  380M   1% /dev/shm
/dev/hda7              67M   15M   49M  23% /boot
/dev/hda14            2,8G  2,1G  555M  80% /home
/dev/hda4              32G   19G   12G  62% /home/store
/dev/hdb2              32G  5,5G   25G  19% /home/store/audio
/dev/hdb3              38G   33G  3,2G  92% /home/store/video
/dev/hda11            3,3G   74M  3,0G   3% /opt
/dev/hdb1             5,1G  2,0G  2,9G  40% /opt/games
/dev/hda15            221M  4,4M  205M   3% /root
/dev/hda13            456M  8,1M  424M   2% /tmp
/dev/hda12            4,8G  2,7G  1,9G  59% /usr
/dev/hda9             1,8G  143M  1,6G   9% /var
/dev/hda10            228M   99M  118M  46% /var/log

```[/QUOTE]




Were do i have to type written above?
I really am a Linux NooB. But a bigger windows hater

---

### Post by quickball on 2005-01-17
[QUOTE=p!=f]Post the output of df -h here please
```

 * 13:56:03 * pef @ agonicus *
[~] > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             228M  122M   94M  57% /
tmpfs                 380M   12K  380M   1% /dev/shm
shm                   380M   12K  380M   1% /dev/shm
/dev/hda7              67M   15M   49M  23% /boot
/dev/hda14            2,8G  2,1G  555M  80% /home
/dev/hda4              32G   19G   12G  62% /home/store
/dev/hdb2              32G  5,5G   25G  19% /home/store/audio
/dev/hdb3              38G   33G  3,2G  92% /home/store/video
/dev/hda11            3,3G   74M  3,0G   3% /opt
/dev/hdb1             5,1G  2,0G  2,9G  40% /opt/games
/dev/hda15            221M  4,4M  205M   3% /root
/dev/hda13            456M  8,1M  424M   2% /tmp
/dev/hda12            4,8G  2,7G  1,9G  59% /usr
/dev/hda9             1,8G  143M  1,6G   9% /var
/dev/hda10            228M   99M  118M  46% /var/log

```[/QUOTE]
 I need therefor a step by step plan... How noobish it may sound.
But I need that, to get rid of XP!
So i can install Ubuntu.. Only that / var is aching
8.4 gb hd ,2.2ghz 
so far. thanks

---

