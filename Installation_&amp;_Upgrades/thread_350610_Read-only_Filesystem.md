---
title: "Read-only Filesystem"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by jrice.blue on 2007-01-31
Greetings.

...Just installed Ubuntu this past weekend; it's good to be back under Linux.  I plan to use Ubuntu for art, music, and coding.  (I'm a little worried about the lack of "polish" to Linux's music apps, but hoping to help the community grow.)

I had quite a tricky install process, relatively speaking... though I was still up and running in less than 24 hours of deciding to "go for it"... which is a lot more than I can say about FreeBSD, which was an installation nightmare for me a few years ago.  ;)

ANYWAY, the question:

My FAT32/WinXP filesystem ended up being read-only from within Ubuntu.  I *really* need to have this drive with write-access.

I've done a little digging--enough to get me to post this.  ;)  I can't quite figure out where to change the filesystem itself (sudo chmodding doesn't work).  I assume this is actually a fairly simple change somewhere... just don't know where.  :\

Thoughts?

Thanks much; I appreciate it.

---

### Post by meng on 2007-01-31
Are you sure it's FAT32 and not NTFS? I thought Win XP preferred NTFS. NTFS is not read-write by default, but you can search the forums for setting up ntfs-3g which will allow read-write access. It is still considered experimental, so don't come crying to me if it all goes to heck ...

---

### Post by EricJosepi on 2007-01-31
I'm pretty sure that your WinXP file system is NTFS in which case you will need some help to get into it.  I suggest following the instructions here: [http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g?topic=298906](http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g?topic=298906) as they seem to be fairly coherent.  

Just a note though, they are directed towards accessing an external HDD but I'm sure they can be modified for your situation.

Cheers,
Eric

---

### Post by jrice.blue on 2007-02-01
Thanks for your suggestions.

Here's what I've tried so far (and hasn't worked).  I've got to stop for tonight, but will give another whack tomorrow.

[LIST]
[*]sudo synaptic
[*]Sections > Utilities > pmount (check it)
[*]Apply
[/LIST]
If you don't have pmount available, do this:
[LIST]
[*]Settings > Repositories
[*]Third Party > Add > "deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main main-all"
[*]Reload, then check the pmount box as above.
[/LIST]

Once you have pmount:
[LIST]
[*]sudo umount [your device's mount point, ex: /media/sda1]
[*]Sections > Utilities > pmount
[*]sudo vi /etc/fstab  (Or use whatever editor you prefer to vi)
[*]Change the line for your mount pint from 'ntfs' to 'fuse'.
[*]sudo mount [mount point]
[/LIST]

...At this point, I get the message:
> mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B4A0C66CA0C634A0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

As I said... gotta quit for tonight, but will take up the problem tomorrow.

Thanks again.  Hopefully I can get this to work.  :\

---

### Post by meng on 2007-02-01
Hang on, are you using Edgy or Dapper? Those instructions are for Edgy.
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)
has instructions for both Edgy and Dapper.

Good luck and back up your data!

---

### Post by jrice.blue on 2007-02-01
I'm using Edgy.

My previous post is a dead-end: pmount only works on removable devices.  (Not sure why, didn't dig.)  It complains: "Error: device /dev/sda1 is not removable".

Perhaps I'll give the ntfs-3g a whack.  Hmmmn.

Thanks again.

---

### Post by cenithx on 2007-02-17
Sorry to thread hijack but didn't deem this worthy of it's own thread since it's related.. 

I have an external USB hdd (IDE), followed EricJosepi's link.. it lets me write new files to the HDD now but I can't copy/paste folders/files or create new folders on the HDD. Seems to only let me "save as.." to the drive.. 

I'm trying to backup a whole  bunch of digital photos in various folders from Ubuntu to put onto my work laptop (has Vista Home Premium).. 

How can I copy files onto an NTFS-formatted external HDD?

---

