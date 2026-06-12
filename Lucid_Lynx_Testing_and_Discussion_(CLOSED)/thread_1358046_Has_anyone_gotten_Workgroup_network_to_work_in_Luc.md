---
title: "Has anyone gotten Workgroup network to work in Lucid"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2009-12-17
I have a 2 computer Windows network with Lucid, Karmic, Karmic, Vista and 7 installed
and a Windows workgroup network. I can see all drives, devices including printer on all
but Lucid install. When I open Network have Workgroup icon, then go's to password and
will not accept. I have read it is Nautilus and or Samba. I was wondering if anyone has a
working network with Lucid.

---

### Post by cariboo on 2009-12-18
See this bug #[lpbug]490201[/lpbug]

---

### Post by ubername on 2009-12-18
I was going to ask exactly the same question, possibly with a poll attached.  I think it is an attempt to find out how widespread this is and if anyone has any work-arounds. FWIW I am using pyneighborhood which allows me to go from the workgroupname to the list of machines, but I haven't managed to get to moumt the shares on the machines: that's probably because I haven't played enough.

(p.s. Garvinrick has actually contributed to the bug report (as have I)).

---

### Post by sparker256 on 2009-12-27
> **garvinrick4 said:**
> I have a 2 computer Windows network with Lucid, Karmic, Karmic, Vista and 7 installed
and a Windows workgroup network. I can see all drives, devices including printer on all
but Lucid install. When I open Network have Workgroup icon, then go's to password and
will not accept. I have read it is Nautilus and or Samba. I was wondering if anyone has a
working network with Lucid.

I run into this when trying to get my printer working which is on my Windows XP machine. I do not have any password for that machine so when I get the Authentication dialog box have no idea what it is looking for.

 I have a Karmic installation and is finds my printer with no problem so not sure if the problem is with Samba or Nautilus but there sure is a problem. 

In looking at the bugs not sure is have seen one to this point as the one listed is for Nautilus and not sure if that is the real reason. I am wondering if a new bug related to printing should be filed?

Bill

---

### Post by cariboo on 2009-12-27
I managed to setup a printer connected to a computer running XP by using the cups web interface@ [http://localhost:631](http://localhost:631)

---

### Post by terry_gardener on 2009-12-27
you could try the workaround on the following thread, post #29

[http://ubuntuforums.org/showthread.php?t=1353165&page=3]("http://ubuntuforums.org/showthread.php?t=1353165&page=3")

---

### Post by rtalcott on 2009-12-27
Works for me!
Thank You!
rt

---

### Post by ubername on 2009-12-29
Another step you could take prior to the workaround mentioned above from terry_gardner is to install pyneighborhood. I can use this to browse through my workgroup to the machine names, and then the shares on them, and even to find their IP addresses (sometimes - but I can go to my router config for that if pyneighborhood fails).

This will give the info required for his workaround.

In fact the only bit of pyneighborhood I can't get to work is to mount the shares, and I haven't played too much with that - it looks like some kind of permissions thing)

---

### Post by sparker256 on 2009-12-29
I have found that browsing is the problem on my machine. I went into my Karmic installation and copied my Device URI into my Lucid and now have my printer working. This is the line that I pasted.

MSHOME/BILLS/HPPhotos

It ends up as smb://MSHOME/BILLS/HPPhotos

We still need the bug fixed but now my Windows XP printer is working in Lucid.

Bill

---

### Post by garvinrick4 on 2010-01-30
Used this fix and now I have network access in Workgroup in Lucid.
 Given you already have a created a Samba user and password.

sudo gedit /etc/samba/smb.conf
 

Find this section in the file:
 ####### Authentication #######
 # &#8220;security = user&#8221; is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;  security = user
 

Uncomment the security line, and add another line to make it look like this:
 security = user
username map = /etc/samba/smbusers

---

