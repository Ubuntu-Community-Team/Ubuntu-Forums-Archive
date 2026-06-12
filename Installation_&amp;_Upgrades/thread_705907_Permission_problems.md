---
title: "Permission problems"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2008-02-23
I did a new install of 7.10 on a big hard drive. Gave 30 gig for root partition, The system made a swap which left a 150 GB+ partition for other use. The system mounted it at /usr/local. However, when I try to use it, all I get is that I do not have permission. Not as a user using the GUI interface, the terminal, or the terminal with SUDO. And it appears that I can't get ROOT access. And none of them will allow me to change the permissions. I want to give read and write permission to all for that area. Yes, I know that is not a good idea.

Oh well, it is LINUX. Anyone have any ideas?

---

### Post by taurus on 2008-02-23
Are you the same user that you created when you installed Ubuntu?  Again, changing permissions or ownerships of /usr/local is a real bad idea.

Post the output of this command from a terminal here.

```
id
```

---

### Post by ubuntu1sttimer on 2008-02-24
The result of the ld command is:

dave@LINUX1:~$ id
uid=1000(dave) gid=1000(dave) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(dave)

ld is a new command for me. Hope it helps. I made the extra partition because they always say to make separate partitions for security.  

Have never seen a good piece on Ubuntu file structure and what goes where.

---

### Post by PmDematagoda on 2008-02-24
Can you take root priviledges using:-
```
sudo -s
```

---

