---
title: "[SOLVED] Setting folder sharing"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sand &amp; Mercury on 2008-09-28
Has this been moved or removed, or am I just blind or something? For the life of me I can't find any option in Nautilus to set sharing options for folders anymore. I noticed there's no longer an emblem to select to signify sharing... hm.

---

### Post by plun on 2008-09-28
As I understands it the only way is a right click on a folder.

[[img]http://ubuntu-pics.de/thumb/3748/shares_J6fJFE.jpg[/img]](http://ubuntu-pics.de/bild/3748/shares_J6fJFE.jpg)


But... this was also discussed during Hardys development and where do you set a Windows Workgroup.?

**shares-admin** is still "hidden"...

About shares-admin
[http://ubuntu-tutorials.com/2008/07/12/share-folders-with-shares-admin/](http://ubuntu-tutorials.com/2008/07/12/share-folders-with-shares-admin/)


"Messing" with samba.conf is nothing for "Newbies".

I wrote a question within a bug but no answer...

---

### Post by jerrylamos on 2008-09-28
Linux/Unix strikes again!  I contend a million monkeys in a million years would never have figured out how to do Alt-F2 and shares-admin.

To this user (I've been on PC's since 1982 and on main frame computers since 1959) Linix/Unix is very frequently totally un-intuitive.  This is another example.

Just where in Ubuntu is this documented for the "ordinary desktop user" with a home network, like mine between me and my wife, or that matter between my PC's?  In the "old days" I could find sharing folders easily on a pop-up menu.  Why did "they" decide to remove this item I use on all my PC's?

What I've been doing is manually editing /etc/samba/smb.conf which is not something I'm comfortable with.

Jerry

---

### Post by Sand &amp; Mercury on 2008-09-28
Really strange... thanks for the help, that was what I was looking for. The strange thing is that I'd had folders set up for sharing through just opening up a folder's properties in Hardy. Where'd that option go? Or maybe it wasn't there at all and I inexplicably managed it some other way... up till this point I never knew shares-admin existed.

---

### Post by Gina on 2008-09-28
I too seem to have problems at times setting up sharing.  I use the right-click menu on a folder but for some reason it doesn't always work.  I really don't know why we can't simply have the main menu option back?  As a supposedly fairly knowledgeable Ubuntu user I often get asked how to set up file and folder sharing.  I agree with the above post - this is something that should be easy for new users of Ubuntu.  Many things are easier in Ubuntu than in Windows - this should be too.

---

### Post by plun on 2008-09-28
Well... I believe we have a major bug with this.

shares-admin can be a function which Gnome forgot about in ver 2.24 !!?

This is the bug I added a comment to

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480)

If you then right-click a share you cannot see this within shares-admin.

If shares-admin is a "bug" there is no GUI for adding a Windows Domain or Workgroup !!


As "jerrylamos" pointed out its smb.conf which controls this.

Wiki
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)


"Bug hunt"...:)

---

### Post by Gina on 2008-09-28
That wiki is way out of date :(

I still haven't figured out a reliable way of setting up sharing.  I play about setting domain name in Network dialog General tab then edit Hosts to remove it so that Terminal works.  There should be a proper  way of setting the Workgroup etc.  

Oh, and I wondered where the NFS sharing option had gone.  Seems samba is now the official method in Ubuntu.

---

### Post by plun on 2008-09-28
This one is newer...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

With Hardy and earlier shares-admin prompted a user if
he/she wants to install SMB and NFS.

Now its nothing.

shares-admin writes to smb.conf, Nautilus seems also OK.

```
gksudo gedit /etc/samba/smb.conf
```

samba restart
```
sudo /etc/init.d/samba restart
```


Tested with a Windows box and I can see Ubuntu boxes but I cannot connect to a share.

From the Ubuntu box smb:/// is empty.... :confused:

---

### Post by plun on 2008-09-28
Just some more clues...

The wiki points to this blog
[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

All bugs, **sorted newest first**

Samba:
[https://launchpad.net/ubuntu/+source/samba/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+source/samba/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Gnome-system-tools
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Not so easy....:)

---

### Post by Gina on 2008-09-28
It's a mess, isn't it?!

Thanks for the link :)

---

### Post by plun on 2008-09-28
No this is a challenge...:D     (within a mess)

Found this also where Steve Langasek writes "wisdom"..

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/235560](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/235560)


I have never changed anything within smb.conf so perhaps we need
more users whick likes challenges...

---

### Post by Gina on 2008-09-28
Oh yes :)  It's a challenge :lolflag:

And, yes, I agree, we need more users who like a challenge :)

---

### Post by plun on 2008-09-28
> **Gina said:**
> Oh yes :)  It's a challenge :lolflag:

And, yes, I agree, we need more users who like a challenge :)

Well, I gave up this one for a while..

```
plun@plun:~$ smbclient --list=192.168.0.101
timeout connecting to 192.168.0.101:445
timeout connecting to 192.168.0.101:139
Connection to 192.168.0.101 failed (Error NT_STATUS_ACCESS_DENIED)

```


Never seen that message before...XP SP3 changed :confused:

---

### Post by plun on 2008-09-29
Networking nightmare....:D

Got it to partially work after re-running the Networking guide in XP, this laptop was upgraded to SP3 earlier this summer...  (also enabled PnP support)

```
plun@plun:~$ smbclient --list=192.168.0.101
Enter plun's password: 
Domain=[Acer] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	Delade dokum    Disk      
	IPC$            IPC       Fjärr-IPC
	print$          Disk      Skrivardrivrutiner
	Mina dokument   Disk      
	Skrivare        Printer   Microsoft Office Document Image Writer
	ACERDATA (D)    Disk      
session request to 192.168.0.101 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[Acer] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master

```


- Nautilus Ok


- Impossible to connect from the XP client, the Ubuntu box seems to advertise wrong networkname/PC....   \\Plun\\temp  should be plun

**But where do I change this...**.:confused:


---------------------------------------------
NFS

Known issue from 8.04

>     *

NFS mount support

    *

      To mount NFS filesystems, you must now install the **nfs-common** package.



Choosing NFS sharing with Nautilus.....:confused::confused:


-----------------------------------------------------------

If anyone can file a Master bug about this it would be great....

- Nautilus

- shares-admin  > gnome-system-tools

- NFS

- Samba   > ***Winbind needed*** ?

- Network names


Just basic "mainstream" functionality...  there are tons with small bugs within Launchpad.

---

