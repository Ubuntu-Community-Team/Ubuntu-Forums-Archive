---
title: "Lower case filenames"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-09-03
I'm really not sure what would be responsible for this, but I noticed that if I plugin my card reader and CF card, all the filenames are in lower case. If I plug it in on a Windows box, they are correctly in upper case.

Maybe a setting in the mounting command?

---

### Post by cariboo on 2009-09-03
That's because windows is seeing the file name incorrectly. In Linux BOB.JPG is not the same as bob.jpg or BOB.jpg.

I have a networked HD in an enclosure, I set the share name as public and Windows only see it as PUBLIC, and I can't change it and it 's driving me nuts. :)

---

### Post by froggyswamp on 2009-09-04
I have another interesting issue, if the "MP3" extension is in upper case then Exaile 0.3 can't play it. Converting to lower case solved the issue.

---

### Post by inportb on 2009-09-04
> **cariboo907 said:**
> That's because windows is seeing the file name incorrectly. In Linux BOB.JPG is not the same as bob.jpg or BOB.jpg.

I have a networked HD in an enclosure, I set the share name as public and Windows only see it as PUBLIC, and I can't change it and it 's driving me nuts. :)

Incidentally, if on Ubuntu I rename an NTFS file to all-uppercase, it immediately shows up on the same Ubuntu setup as all-lowercase. It has been this way for as long as I could remember and I think this might be the same issue. What gives?

---

### Post by MacUntu on 2009-09-04
But this worked before, right? I put in my camera's SD card yesterday and got filenames starting with "dsc..." when they [I'm close to 100% sure] always showed up as "DSC...".

---

### Post by MacUntu on 2009-09-04
To answer my question: Yes! 

At the top: Karmic Alpha 5
At the bottom: Jaunty Alpha 4

[IMG]http://img.xrmb2.net/images/277638.png[/IMG]

Care to open a bug report?

---

### Post by ssam on 2009-09-04
NTFS and FAT are case insensitive. the OS gets to interpret them however it wants. lowercase is easier on the eyes, but it might be best to match windows.

from wp [http://en.wikipedia.org/wiki/File_Allocation_Table#Directory_table](http://en.wikipedia.org/wiki/File_Allocation_Table#Directory_table)
looks like FAT stores all letters as upper case.

looks like NTFS can store upper and lower case letters, but that windows ignores the case. probably more subtle than this.

---

### Post by MacUntu on 2009-09-04
I don't know if that happens on NTFS too. My testing with a FAT formatted SD card showed, that it's only happening to filenames in FAT's 8.3 format (AFAIK that's a vfat mount option: shortname=lower).

If I choose to create a filename upper case (doesn't matter if the file is created with Windows or Linux) I expect Linux to show me the file upper case. :/

While this is not a bug per definition, I still opened a bug report: [https://bugs.launchpad.net/ubuntu/+bug/424246](https://bugs.launchpad.net/ubuntu/+bug/424246)

---

### Post by knarf on 2009-09-04
FAT is case-insensitive and non case-preserving. VFAT and NTFS are case-insensitive and case-preserving. Unix filesystems are case-sensitive and with that of course also case-preserving.

As case does matter in Unix it is important that non case-preserving filesystems are handled consistently. To assure this there are several mount options:

```

shortname=[lower|win95|winnt|mixed]

              Defines the behaviour for  creation  and  display  of  filenames
              which fit into 8.3 characters. If a long name for a file exists,
              it will always be preferred display. There are four modes: :

              lower  Force the short name to lower case upon display; store  a
                     long name when the short name is not all upper case. This
                     mode is the default.

              win95  Force the short name to upper case upon display; store  a
                     long name when the short name is not all upper case.

              winnt  Display  the  shortname as is; store a long name when the
                     short name is not all lower case or all upper case.

              mixed  Display the short name as is; store a long name when  the
                     short name is not all upper case.

```

([FONT="Courier New"]man mount[/FONT] for more of this)

You can change the default mount options used in several file systems in Gnome by editing the relevant keys ([FONT="Courier New"]/system/storage/default_options/<filesystem>[/FONT]) in [FONT="Courier New"]gconf-editor[/FONT].  The display of the *shortname* (filenames which fit within the PC/MS-DOS 8.3 convention) is handled by the above mentioned *shortname* option.

---

### Post by Enigmatic on 2009-09-04
> **MacUntu said:**
> To answer my question: Yes! 

At the top: Karmic Alpha 5
At the bottom: Jaunty Alpha 4

[IMG]http://img.xrmb2.net/images/277638.png[/IMG]

Care to open a bug report?

Yes, that is exactly what I'm referring to! I would like the behaviour of 9.04 back.

---

### Post by MacUntu on 2009-09-04
> **knarf said:**
> FAT is case-insensitive and non case-preserving.

Then why does a file "abc.TXT" on a FAT formatted SD-Card show up as "abc.TXT" on every Windows (case-preserved long name?) but as "abc.txt" on Ubuntu (which would indicate "abc.TXT" being a short name)?

---

### Post by knarf on 2009-09-04
You never know what case the filename on a FAT filesystem will have as there are many different conventions (all upper case, all lower case, mixed case, force to lower/upper on display, etc). The case in which the filename is displayed often does not match the case in which it is stored, so in that sense FAT is non case-preserving. It is possible to store mixed upper/lowercase names in the short filename but that is not what will be displayed on eg. Windows ME or earlier. As to what your camera/phone/mediaplayer/etc will do with those files is up to the device developer as case does not play any role in FAT filesystems given the above constraints.

---

### Post by knarf on 2009-09-04
> Yes, that is exactly what I'm referring to! I would like the behaviour of 9.04 back.

Edit the gconf key I mentioned above ([FONT="Courier New"]/system/storage/default_options/vfat[/FONT]), set *shortname* to something else than *lower* (one of *win95*, *winnt* or *mixed*) and you'll have what you want.

---

### Post by MacUntu on 2009-09-04
Well, then I'll marked my bug invalid as it's just a (IMO bad) default. I'll definitely change that back (to mixed like in Jaunty) but the gconf-key is only one part as this is default for any vfat mount. Have to check if there's a way to globally change mount defaults.

Seems this has to happen in-kernel here: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=fs/fat/inode.c;h=8970d8c49bb00eaa791a390f5dfd87b56a438294;hb=HEAD#l974](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=fs/fat/inode.c;h=8970d8c49bb00eaa791a390f5dfd87b56a438294;hb=HEAD#l974)

---

### Post by knarf on 2009-09-04
The kernel makes all above mentioned mount options (*lower*, *win95*, *winnt*, *mixed*) available. The [FONT="Courier New"]mount[/FONT] command chooses *lower* as default as can be read in the man page:

```

              lower  Force the short name to lower case upon display; store  a
                     long name when the short name is not all upper case. **This**
                     **mode is the default**.

```

---

### Post by MacUntu on 2009-09-04
Sure, but if you want to change the default behavior you have to edit it at above mentioned link (to "VFAT_SFN_DISPLAY_WINNT | VFAT_SFN_CREATE_WIN95" for shortname=mixed) - at least I haven't found another way. I've just compiled the kernel that way and it works like Jaunty did.

---

### Post by Enigmatic on 2009-09-05
I'm still seeing this. The setting by default was 'mixed', and changing it to 'winnt' didn't change anything. Still shows everything as lowercase.

---

### Post by mattduckman on 2009-09-06
> **Enigmatic said:**
> I'm still seeing this. The setting by default was 'mixed', and changing it to 'winnt' didn't change anything. Still shows everything as lowercase.

Yeah, I'm seeing this too. Using mount manually works though. That would mean that this is caused by a bug in whatever program mounts devices automatically (gnome-volume-manager?)

---

### Post by MacUntu on 2009-09-06
This key doesn't seem to get used at all. Let Gnome automount your device and then type 'mount' at a terminal:
```
/dev/sdb1 on /media/E8D1-6BB7 type vfat (rw,nosuid,nodev,
uhelper=devkit,uid=1000,gid=1000,**shortname=lower**,dmask=0077,utf8=1,flush)
```

---

### Post by Enigmatic on 2009-09-08
So, that would mean a bug report should be filed? I tried mounting it manually, but somehow I cannot mount it manually...unless it's been automounted it doesn't show up under fdisk -l and I can't address the device location (might be a problem specific to a card reader).

---

### Post by fhr on 2009-10-04
Hi all,

I've got exactly the same problem. I had a look at /system/storage/default_options/vfat in gconf-editor and /etc/gconf/schemas/gnome-mount.schemas, but in both cases there's already shortname=mixed. 

So, what file/key is used by Gnome for automounting ? Is there a package which could replace the current automounting (and which would follow the rules...) ?

NB: the problem occurs on a fresh install of Ubuntu 9.10 Beta, but not on a few months old daily-live Xubuntu...

---

### Post by MacUntu on 2009-10-04
Chris Coulson reopened my bug report:

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/424246](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/424246)

No idea if you can edit dk-disk's options.

---

### Post by fhr on 2009-10-04
Good news the bug report is reopened, because it seems there was a lot of incomprehension around our problem. Anyway, it seems that the bug is due to devicekit-disks, as stated here : [https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/428174](https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/428174)

---

### Post by fhr on 2009-10-09
Fix commited \o/

---

