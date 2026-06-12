---
title: "Cannot upgrade system with unmerged /usr"
date: 2024-09-29
forum: Installation &amp; Upgrades
---

### Post by espierre on 2024-09-29
Hello,

  I have a MSI Z790 motherboard and a TX401 network card. Under windows no issue. Underl inux no NIC and wifi is 20MB.

  I've found out that new versions could fix that so I wanted to go from 22.04.5 LTS to a newer version through the do release upgrade.

  but:
```
Cannot upgrade system with unmerged /usr 

Please install the usrmerge package to fix this, and then try the 
upgrade again. 

```

and when reinstalling usermerge:
```
 Preparing to unpack .../usrmerge_25ubuntu2_all.deb ...
Unpacking usrmerge (25ubuntu2) over (25ubuntu2) ...
Setting up usrmerge (25ubuntu2) ...
Smartmatch is experimental at /usr/lib/usrmerge/convert-usrmerge line 172.

FATAL ERROR:
Both /lib/x86_64-linux-gnu/libselinux.so.1 and /usr/lib/x86_64-linux-gnu/libselinux.so.1 exist.

You can try correcting the errors reported and running again
/usr/lib/usrmerge/convert-usrmerge until it will complete without errors.
Do not install or update other Debian packages until the program
has been run successfully.

```

 /usr/lib/ is a symlink to /lib/

Spent the whole day trying to assess how ot do that, but I found no way on forums so far, and I am stuck with poor connectivity... help !
kernel 6.8.0-45-generic
arch x86_64

---

### Post by 1fallen on 2024-09-29
Read this over thoroughly: [https://ubuntuforums.org/showthread.php?t=2501198&p=14207414#top](https://ubuntuforums.org/showthread.php?t=2501198&p=14207414#top)

---

### Post by Tadaen_Sylvermane on 2024-09-29
Another suggestion for future issues of this type that may not be related to usrmerge. I have both on my Bookworm dev environment on my Chromebook. I ran the following and found the files identical.

```
for i in /lib/x86_64-linux-gnu/libselinux.so.1 /use/lib/x86_64-linux-gnu/libselinux.so.1 ; do
  sha1sum "$i"
done
```

Hashes matched. While I have no reason to go further I think it's a relatively safe bet that removing either file (by moving it to a backup filename, not just deleting it) then running the usrmerge should cause you zero problems. If problems arrive then you can always move that file back to its original name.

*EDIT* The safest one to move most likely is the one in /lib. Only because most things will work with /usr stuff before checking base directory stuff barring any full path specs for whatever is needed.

---

### Post by 1fallen on 2024-09-29
> **Tadaen_Sylvermane said:**
> Another suggestion for future issues of this type that may not be related to usrmerge. I have both on my Bookworm dev environment on my Chromebook. I ran the following and found the files identical.

```
for i in /lib/x86_64-linux-gnu/libselinux.so.1 /use/lib/x86_64-linux-gnu/libselinux.so.1 ; do
  sha1sum "$i"
done
```

Hashes matched. While I have no reason to go further I think it's a relatively safe bet that removing either file (by moving it to a backup filename, not just deleting it) then running the usrmerge should cause you zero problems. If problems arrive then you can always move that file back to its original name.

*EDIT* The safest one to move most likely is the one in /lib. Only because most things will work with /usr stuff before checking base directory stuff barring any full path specs for whatever is needed.

+1 And a Great Suggestion, it was unclear to me if the OP ever ran>>>"/usr/lib/usrmerge/convert-usrmerge", so this might just hit the spot. :)

---

### Post by ubfan1 on 2024-09-29
Careful, the /bin, /lib, and /sbin are just links these days to the /usr counterparts.  Some old code needs updating if it thinks there are duplicate files.

---

### Post by espierre on 2024-09-30
> **ubfan1 said:**
> Careful, the /bin, /lib, and /sbin are just links these days to the /usr counterparts.  Some old code needs updating if it thinks there are duplicate files.

exactly, both ways were tried and none worked (cp and mv are dynamically linked...)

I've known a time where / was statically linked against these issues, and they are fully back... 

The only option I have is to reinstall a distro, crossing finder it will work against my config (raid 1 btrfs full on nvme)

---

### Post by espierre on 2024-09-30
> **1fallen2 said:**
> Read this over thoroughly: [https://ubuntuforums.org/showthread.php?t=2501198&p=14207414#top](https://ubuntuforums.org/showthread.php?t=2501198&p=14207414#top)

went through this already... does not work for me as I said above, too low level libs are seen as duplicate though physically the same through a directory softlink

---

### Post by espierre on 2024-10-04
Hello,

  Reinstalled to 24.02 all is fine now. Still thinking or not going back to full btrfs raid 1.

  So bad this migration breaks all, last time I had that was mandrake before the fall...

---

