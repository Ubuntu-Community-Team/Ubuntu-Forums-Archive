---
title: "Problem creating a link to fat partition"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by John Read on 2007-11-11
Hi,

I have a fat32 partition on my hard disk that holds data files I share between Windows and Ubuntu 7.10

I added the following line to the fstab file to make the fat partition accessible to Ubuntu...

    /dev/sda6  /media/windows  vfat  iocharset=utf8,umask=000  0  0

When I try to create a link on my Linux desktop to data files on this fat partition I get the
error message...

   Error "operation not permitted" while creating a link to "/media/windows/somefile"

Can anyone suggest what I'm doing wrong?

Thanks in anticipation. John R.

---

### Post by ofb on 2007-11-12
Maybe you have to be root while you make that link, because /media is in root's domain? Though I'm not sure why that would matter because you've got permissions wide open with that umask, but try mounting it under your home, like /home/[YourUserName]/windows, instead of /media/windows.

---

### Post by John Read on 2007-11-12
Thanks for the suggestions. Tried creating the link as root but same error message.

No big drama as sooner or later I'll make my machine Ubuntu only and say goodbye to dual booting with Windows Vista.

Regards, John R.

---

### Post by ofb on 2007-11-12
How odd. I have no problem making a desktop link to files or folders on FAT32 using Konqueror. Here's the relevant fstab,

```
/dev/hdd1 /home/o/files/Thorax vfat umask=0000 0 0
```

---

### Post by erfahren on 2007-11-12
no problem creating launcher link to a file on my FAT32 partition here either. I have the same line in my fstab as well.

does this happen with any file on that partition? "ofb" mentioned that the permissions with that umask were wide open, but I had a problem deleting files in a folder I had in there awhile back (the folder was a backup of "My Documents" actually). I know it had something to do with the permissions of the directory, probably ownership. Not knowing a whole lot about that I booted into Windows and set the directory to "share"  through it's properties. That fixed it.

Maybe the permissions Windows sets interferes somehow? In any event, check the containing folder's properties through Windows.

---

### Post by erfahren on 2007-11-12
p.s. John... you're a couple of Ubuntu versions behind in your profile. :-P

---

### Post by ofb on 2007-11-13
IIRC, FAT32 doesn't support Unix permissions, so whatever is declared in the fstab is what's applied. Ownership is root, even if a file is created by a regular user.

The only permission error I've ever run into is badly worded dialogs that actually meant I couldn't copy to FAT32 because the filenames had illegal characters.

None of which helps here. Perhaps when John checks back in, he can tell us how he was creating the desktop shortcuts. Possibly there's some arcane glitch within nautilus or gnome.

AHA! See post #8.
[http://ubuntuforums.org/showthread.php?t=40922](http://ubuntuforums.org/showthread.php?t=40922)

---

### Post by erfahren on 2007-11-13
> **ofb said:**
> 
AHA! See post #8.
[http://ubuntuforums.org/showthread.php?t=40922](http://ubuntuforums.org/showthread.php?t=40922)
That is a good trick. I always have created launchers on the panel to files (like to file:///media/D/somefile for example), not links. I guess that's why I didn't have a problem.

Good to know!

---

### Post by John Read on 2007-11-14
Thanks very much for the plethora of suggestions.

Found that the suggestion of clicking and dragging with the *middle* mouse button worked a treat. I'd been trying to right-click and choose create link.

Thanks again. John R.

BTW, have updated my details.

---

### Post by ofb on 2007-11-14
Glad that worked. Here's how to mark your thread as Solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

