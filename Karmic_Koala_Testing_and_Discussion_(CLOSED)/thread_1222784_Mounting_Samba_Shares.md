---
title: "Mounting Samba Shares"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2009-07-25
Hi, 
    I just moved a machine over to karmic from jaunty. When using jaunty I had a script which ran when the wireless interface went up, which mounted some samba shares.

After moving to karmic the samba shares still mount but the uid is set to 1001 so I don't have any write permissions. 

I use the following line to mount the share

smbmount //MyServer/Monkey /media/Monkey -o username=username,password=password,rw,uid=username,auto 0 0

Might raise a bug about this as it worked in jaunty. 

George

---

### Post by ELDal on 2009-07-25
I have a problem that's somewhat related, i'm unable to copy any files from windows networks (tried several different networks and windows boxes to confirm it wasn't the router or windows box).

Error while copying "file".
There was an error copying the file into /home/"name"/Desktop
Invalid argument

---

### Post by scaine on 2009-07-25
[http://ubuntuforums.org/showthread.php?t=1218934](http://ubuntuforums.org/showthread.php?t=1218934)

My thread above is related to the exact same issue only using AutoFS (which you might want to consider instead of running scripts for interface up/down - does that handle suspend/resume elegantly?  Hidden credentials?).

Anyway, turns out that AutoFS, when used with samba shares is just calling smbclient, albeit in a complex fashion.  I've tried AutoFS 4 and 5, but since they both call the same smbclient command, it didn't make any difference.

So, the bug is with Karmic and smbclient.  If I have time later tonight, I'll raise a bug.  If not, it'll be Monday, as I'm out most of Sunday.

---

### Post by snkiz on 2009-07-25
thought smb was depreciated cifs instead?

---

### Post by scaine on 2009-07-25
Just went ahead and did a "ubuntu-bug smbclient" and rattled though a bug report :
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/404623](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/404623)

Yep, SMB is replaced by CIFS.  The various commands now generally support cifs (like smbclient) but for various reasons they never changed the names of the commands...

---

### Post by scaine on 2009-07-26
If anyone can help confirm this bug in smbclient, I'd appreciate it if you could comment on the bug report.

Thanks.

---

### Post by tekstr1der on 2009-07-26
> **ELDal said:**
> I have a problem that's somewhat related, i'm unable to copy any files from windows networks (tried several different networks and windows boxes to confirm it wasn't the router or windows box).

Error while copying "file".
There was an error copying the file into /home/"name"/Desktop
Invalid argument

This has been triaged: [https://bugs.launchpad.net/gvfs/+bug/393012](https://bugs.launchpad.net/gvfs/+bug/393012)

And sent upstream: [http://bugzilla.gnome.org/show_bug.cgi?id=588391](http://bugzilla.gnome.org/show_bug.cgi?id=588391)


Hope the fix comes down fairly quickly as I am unable to downgrade to libsmbclient 3.3.5.

EDIT: Sorry to mildly hijack the thread, just wanted to answer a previous post here.

---

### Post by michaelzap on 2009-07-26
You might try mounting your shares using GVFS instead:
[http://ubuntuforums.org/showthread.php?p=7563868](http://ubuntuforums.org/showthread.php?p=7563868)

Once you've saved the your login credentials into the keyring, you can use this syntax to mount a share in a bash script:
```
#!/bin/sh
gvfs-mount smb://server/share
```

---

### Post by scaine on 2009-07-27
> **tekstr1der said:**
> This has been triaged: [https://bugs.launchpad.net/gvfs/+bug/393012](https://bugs.launchpad.net/gvfs/+bug/393012)

And sent upstream: [http://bugzilla.gnome.org/show_bug.cgi?id=588391](http://bugzilla.gnome.org/show_bug.cgi?id=588391)


Hope the fix comes down fairly quickly as I am unable to downgrade to libsmbclient 3.3.5.

EDIT: Sorry to mildly hijack the thread, just wanted to answer a previous post here.

Not all all.  Those bugs are certainly related and I'll likely close my bug as a duplicate of this one.

[quote=michaelzap]
You might try mounting your shares using GVFS instead:
[http://ubuntuforums.org/showthread.php?p=7563868](http://ubuntuforums.org/showthread.php?p=7563868)[/quote]

That's not much use, because as per this report ([https://bugs.edge.launchpad.net/gvfs/+bug/388444](https://bugs.edge.launchpad.net/gvfs/+bug/388444)), which I tried to get added 100PaperCuts (and failed!), a gvfs mount point isn't actually mounted until you click on it.  This means that things that need to see that shortcut when they run will fail until you've done so.

But sure, it's a workaround for som people until this libsmbclient regression is solved.  In the meantime, sadly, until this is the case, I can't meaningfully use my two Karmic boxes for testing, since every byte of useful data I need to access is on my Ubuntu server running Samba (because my wife still uses microsoft).

---

### Post by taavikko on 2009-07-27
```
taavikko@hp-dv5:~$ ls -l .gvfs/
total 0
taavikko@hp-dv5:~$ gvfs-mount smb://192.168.0.103/DEVIL_VIDEOS/
taavikko@hp-dv5:~$ ls -l .gvfs/
total 0
drwx------ 1 taavikko taavikko 0 2009-07-26 10:32 devil_videos on 192.168.0.103
taavikko@hp-dv5:~$ ls -l .gvfs/devil_videos\ on\ 192.168.0.103/ |wc -l
220
taavikko@hp-dv5:~$ 

```

I had no problem mounting smb shares from my Desktop 9.10 (KDE)

EDIT// whups, the issue wasn't the connection, so wasted info on my part.

---

### Post by michaelzap on 2009-07-27
> **scaine said:**
> That's not much use, because as per this report ([https://bugs.edge.launchpad.net/gvfs/+bug/388444](https://bugs.edge.launchpad.net/gvfs/+bug/388444)), which I tried to get added 100PaperCuts (and failed!), a gvfs mount point isn't actually mounted until you click on it.  This means that things that need to see that shortcut when they run will fail until you've done so.

I think this "issue" just refers to these shares not auto-mounting on login. I just use a simple bash script to do this (which is in the forum post that I linked to). This mounts these shares on login much like fstab, and my symbolic links to them work exactly the same using either method.

I actually put my share mounting script in the main menu and I run it manually instead of automatically, since I only want to mount them when I'm home and my wireless is up.

---

### Post by scaine on 2009-10-11
> **michaelzap said:**
> I think this "issue" just refers to these shares not auto-mounting on login. I just use a simple bash script to do this (which is in the forum post that I linked to). This mounts these shares on login much like fstab, and my symbolic links to them work exactly the same using either method.

I actually put my share mounting script in the main menu and I run it manually instead of automatically, since I only want to mount them when I'm home and my wireless is up.

<not sure why I didn't see this reply for so long, but ah well>

That's the whole point of autofs (at least in my use case), since autofs will only try to mount the shares if you use them.  Obviously, if your wireless is down, you won't be using any network shares and so you won't have mounted anything.

In my case, I run my thunderbird mail files from a server.  With autofs, I just run thunderbird - it needs to see the server, so tries to navigate to the server directory.  Autofs sees the attempt and tries to mount the server.

In your case, you'd have to click on your "mount shares" link, THEN run thunderbird.  Autofs, well, automates your filesystems.

Anyway, just rebuilt my Karmic box from beta, fully updated it, then tried autofs again.  No dice.  Despite claiming that the smbclient regression is now fixed, autofs is still mounting all my drive shares as read-only.  Which sucks.

I'll update the bug report, but if ANYONE is using autofs to mount samba shares, please do a quick test and report back here (and on the bug report if possible).  This bug is ruining my otherwise amazing karmic experience.

---

