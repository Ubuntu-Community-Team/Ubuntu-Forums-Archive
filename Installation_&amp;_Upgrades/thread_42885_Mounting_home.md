---
title: "Mounting /home"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by Kyral on 2005-06-19
This isn't a problem, YET. I have my /home mounted on a separate partition. Now, like most of us, I enjoy screwing around with my computer, often forcing me to reinstall. Now my question is, if/when I reinstall, and I tell the uninstaller to use /home as /home, will the current data on /home be overwrittin by the installer, or will the packages use the data already there? (ie, GAIM using the current .gaim instead of overwriting it)

Thanks :D

---

### Post by tread on 2005-06-19
When installing, just tell the installer to use the partition for /home without formatting. You get that option when you choose to manually partition at install time.

Tip: something I have learned from mistakes of my own .. also backup the /etc folder .. I often customize something and then end up losing that customization. Something like firewall rules, for example. It helps if I have a backup of that too :)

---

### Post by Kyral on 2005-06-19
Why do I think I am going to wind up mounting the full 4 HDs my case can support?

Imagine it

HD1 /
HD2 /home
HD3 /etc /usr
HD4 /media/anime <---MUST HAVE :D


Thanks BTW :D

---

### Post by afonic on 2005-06-19
[QUOTE=Kyral]Why do I think I am going to wind up mounting the full 4 HDs my case can support?

Imagine it

HD1 /
HD2 /home
HD3 /etc /usr
HD4 /media/anime <---MUST HAVE :D


Thanks BTW :D[/QUOTE]
 LOL!

I use the anime folder more often so my 80GB hard disk is mounted on /home/username/Desktop/Anime

:-)

Sure you can do that, no problem. However if one HDD brakes... You better keep the system files in one and /home and other user stuff in another.

---

### Post by Kyral on 2005-06-19
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G  2.3G   16G  14% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hda3             256G  3.0G  240G   2% /home
/dev                   19G  2.3G   16G  14% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hdc              589M  589M     0 100% /media/cdrom0
/dev/hdd              494M  494M     0 100% /media/cdrom1
**/dev/sda1             154G   81G   73G  53% /media/anime**
```

  O:)

---

