---
title: "Samba issue?  VM clients keep giving IO error"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by nosebreaker on 2011-04-04
I have a Ubuntu 10.04 desktop VM that is running torrent software, and it is saving the files to a samba share (which is actually the host it is running on).  I have also tested from another Ubuntu box on the network and it experiences the same problem.

The problem I am having is that any torrent client on a Ubuntu machine or VM can't save to the samba share, but a WinXP torrent client can download the same torrent and save to the share with no problem.

I created a public share, and the problem seems to be that I cannot edit files after I create them. It seems that samba is ignoring the create mask and creating files as rw-r--r-- instead of rw-rw-rw-

I even tried adding the "unix extensions = yes" option and that didn't seem to work either.
```

[global]

# map any unknown username to nobody so login succeeds, don't forget to run:
# smbpasswd -an nobody
# so that it will work!
guest account = nobody
map to guest = bad user

	security = share

[public]
	comment = Public Stuff
	path = /public
	public = yes
	writable = yes
	printable = no
	read only = no
	browsable = yes
	guest only = yes
	create mask = 0666
	directory mask = 0777
```

---

### Post by nosebreaker on 2011-04-04
I tried changing the mask to 664 and 775, and now when I edit files on the command line they are rw-rw-r-- which should work, but the torrent applications create files as rw-r--r-- still!  I tried unmounting/remounting the share and reloading the torrent app.

---

### Post by nosebreaker on 2011-04-05
Oh what the heck, Transmission works fine, and doesn't ignore the umask, so I'm just going to use that.

---

### Post by nosebreaker on 2011-04-06
Nevermind, Transmission only works for files that don't come in a subdirectory.  Argh forget it, I'll just use Windows.  Confirmed, Windows works fine.

---

### Post by nosebreaker on 2011-11-23
I finally got this to work.  The answer was in setting "force directory mode = 0777" as an option on the share.  I had read earlier that the keyword "mask" and "mode" mean the same thing for the file-level option, but apparently you MUST use the keyword mode for directory.  You also have to set the directory security modes, this is my config section:

```
[public]
        comment = Public Stuff
        path = /public
        writeable = yes
;	browseable = yes
        guest ok = yes
        printable = no
        force directory mode = 0777
        create mask = 0777
        force create mode = 0777
        security mask = 0000
        force security mode = 0777
        directory mask = 0777
        directory security mode = 0000
        force directory security mode = 0777
```

---

