---
title: "Hardisks seem as media rather than part of system"
date: 2022-01-10
forum: Installation &amp; Upgrades
---

### Post by ratty01 on 2022-01-10
Hi I have Ubuntu 20.04 installed on a SSD and 2 had drives for data. The idea I can reinstall Ubuntu any time I want and keep my data safe

The hard drives sit under media/username/storage/downloads

My Ubuntu (SSD) user folders sit under home/username/downloads etc

Is username a directory and if so how come there are two?

JDownloder cannot find the downloads folder on storage why not?

Thanks for any advice

---

### Post by yancek on 2022-01-10
The media directory shows non-system or removable media and the user name is the user logged in to access it.  If you had another user and logged in as that user to access media drives, the different user name would show there.  The username under /home is for personal data and configuration files for each specific user.

I don't know what JDownloader is, post a link or explain.

---

### Post by TheFu on 2022-01-10
Please don't confuse 
media/username/storage/downloads
with 
[COLOR="#FF0000"]/[/COLOR]media/username/storage/downloads

They are VERY DIFFERENT locations.  That leading / is critical.  The first example above is a "relative path".  The second example is an "absolute path". These are very different.

Not being able to save files outside of home using a browser usually means the browser is running in some sort of a constrained environment - perhaps it is a snap package?  
Or course, of you cannot create any files on the storage under /media/ not using a broswer, but using a normal terminal command like "touch {path/to/file} then that means there are ownership and/or permissions settings which don't allow it.  This is common for newly added storage.

---

### Post by ratty01 on 2022-01-10
Thanks for the replies 

In Files if I click on other locations I get Computer (SSD) this is where I've installed Ubuntu Storage (HD) Storage 2 (HD)

My root directory has a media folder 

 
To find my hard drives I have to go on media 

I did try some screen shots but it wouldn't post

JDownloader is a download manager and it was a snap install

Cheers

John

---

### Post by TheFu on 2022-01-10
snap packages have to be allowed access to save/access any storage that isn't in the user's HOME directory.
There is a command to request that access, but if the developer didn't allow it when they created the snap package forgetoutit. There isn't any workaround with snaps to allow access.  Find a different, non-Snap-tool. 

Some links about snaps:
[Https://snapcraft.io/docs/removable-media-interface](Https://snapcraft.io/docs/removable-media-interface)
[Https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](Https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)

$ snap connections <application-name> --all

For example, the freemind snap has these allowed connections:
```
$ snap connections freemind
Interface       Plug                     Slot             Notes
cups-control    freemind:cups-control    -                -
desktop         freemind:desktop         :desktop         -
desktop-legacy  freemind:desktop-legacy  :desktop-legacy  -
home            freemind:home            :home            -
network         freemind:network         :network         -
x11             freemind:x11             :x11             -
```
It cannot access for read or write anything in /media/

---

### Post by ratty01 on 2022-01-10
Thanks very much for solving that. I can work round it  and I know not to  spend any more time on it.

Have learnt some more though!

Cheers

John

---

### Post by TheFu on 2022-01-10
> **ratty01 said:**
> Thanks very much for solving that. I can work round it  and I know not to  spend any more time on it.

Just to be clear, by default, no snap package will allow access to /media/ storage, but many of them do have the option which can be requested.  Follow those links for the exact command. It is 1 command. I just don't remember it because I don't have any storage under /media/.

---

### Post by MAFoElffen on 2022-01-11
Two questions... 

Are you the only user on this computer?
Why are you mounting them there?

Logic says that you should mount drives where you can easily use them. right?

So, if you are the only user, and you are using Snaps, then the logical place would be to mount the drives into a folder within Your $HOME directory... If you are not the only user and you need to have others access the data on those drives, then the logical place would be to create a Shared folder for that, or to mount them in the Desktop's Public Folder... Or to another mounted drive, where the folder access and permissions are setup to share with others.

Just an observation.

I have used JDownloader in the past... Before it was a Snap App. Back then there was a config/preferences, where you could change where it downloaded to, where mine was on another drive, into a specific folder on that drive. The drive was mounted to the system as a separate drive (/dev/sdd), but again, that was before it was a Snap Application.

---

### Post by TheFu on 2022-01-11
The only issue I have with mounting extra storage under a HOME directory (3rd level), it that backup will try to traverse that storage and likely the amount of backup storage can't support both the / and the /home/joeuser/whatever storage totals.

But, if there are 3 disks in the system (or a remote backup server exists) with sufficient storage on the 3rd disk for everything on the first 2 disk, go for it.

Be certain that the jdownloader snap doesn't support the removable-media connection. If it doesn't, make a request of the package team, since it would be foolish for a downloader NOT to support that.

---

