---
title: "In some cases fIle sharing is still too difficult!"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by | MM | on 2009-03-29
Sharing files/folders on NTFS partitions is still too difficult IMHO.

I had to edit my /etc/samba/smb.conf file to share folders on an NTFS partition.  Specifically, I had to add the following to my [global] section:
```
usershare allow guests = Yes
usershare owner only = False
```

Whats more frustrating is that the GUI for sharing folders, i.e. the Folder Sharing tab in Nautilus just gives a message exclaiming that it does not have the permissions to share the folder, which is all we and good.  

Thing is though, in this day in age with PolicyKit and the like you would have thought a nice little 'Unlock' + enter password prompt would be provided which does all the nitty-gritty stuff to get you sharing files ASAP.

---

### Post by Yashiro on 2009-03-29
I agree but no one has produced a sensible blueprint in all the years of waiting.
There are loads of half baked attempts at the problems but they're left in that state.

---

### Post by forcecore on 2009-03-29
sharing options should be usable by default not like now i must install something to get working.

---

### Post by | MM | on 2009-03-29
> **forcecore said:**
> sharing options should be usable by default not like now i must install something to get working.

I agree.  My thought is that if the installer is able to establish an internet connection, or connection to a ethernet/LAN then it should offer to set up file sharing, and install the required packages from the internet.  It could also ask the user which folders he or she would like to share.  That would be cool!

---

### Post by tom56 on 2009-03-29
Actually, file sharing is very easy now. What you are talking about isn't like that by design - it's a bug, so I suggest you file it on Launchpad. All I had to do to share a folder is right-click it, choose sharing options, and click yes when it offered to install samba.

To share with guests, you just need to tick the bottom box on the share options, like in this screenshot

EDIT: Didn't notice you meant sharing other partitions - yeah that could be easier. It's definitely an odd use case though, and still worth filing a bug.

---

