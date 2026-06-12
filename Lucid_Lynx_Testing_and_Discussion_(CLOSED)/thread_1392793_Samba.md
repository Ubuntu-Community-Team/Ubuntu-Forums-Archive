---
title: "Samba?"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-01-28
When is samba going to be fixed? I am using nfs right now but would like to know when samba is going to be fixed so I can add a network printer.

---

### Post by llawwehttam on 2010-01-28
Fixed? Whats wrong with it? It works fine for me.

---

### Post by sparker256 on 2010-01-28
> **llawwehttam said:**
> Fixed? Whats wrong with it? It works fine for me.

I cannot browse to my network printer that is on my Windows XP machine without it asking for a password. When I use Ubuntu 9.10 it does not ask me for a password. I have filled this bug report at   [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607)

Bill

---

### Post by cariboo on 2010-01-28
There was a samba update today, but the bug has nothing to do with samba, as it works the way it should from the command line. It seems to be more of an authorization/policykit problem.

If it's just a network printer, you don't need samba to make it work. If the printer is connected to a windows computer you can set them both up using the the cups web interface. I have both here, and had zero problems setting them up.

---

### Post by emarkay on 2010-01-28
Then again there is this, FWIW, may still be an issue.  I have not bothered with this for a while...

[https://answers.launchpad.net/ubuntu/+source/samba/+question/87080](https://answers.launchpad.net/ubuntu/+source/samba/+question/87080)

---

### Post by tad1073 on 2010-01-28
It is not just a printer issue. I am asked for a password if I am accessing shares or printer but samba rejects my password and keeps asking for it.

---

### Post by garvinrick4 on 2010-01-28
> **tad1073 said:**
> It is not just a printer issue. I am asked for a password if I am accessing shares or printer but samba rejects my password and keeps asking for it.
I myself and quite a few others have had this problem from the get go with Lucid, day 1.
Karmic works great, Juanty works fine, Vista and Windows 7 but Lucid does ask for password
that is not accepted. I do not believe it has been assained yet and priority is low. I am sure by
the time release date is here it will be taken care of. But it would be nice to have access to  devices on other Machines sooner than later.

---

### Post by Roasted on 2010-01-29
I never had trouble with Samba. I use OSX, Ubuntu, Kubuntu, OpenSuSE, Vista, XP, 7, etc on my network with no issues with network shares, permissions, etc.

However, I've always added the user level of security to my smb conf file. Example:

[Jason]
	path = /home/jason
;	browseable = yes
	writeable = yes
	valid users = jason
	comment = Jason

[Tyler]
	path = /media/storage/tyler
	writeable = yes
;	browseable = yes
	valid users = jason, tyler
	comment = Tyler

The "valid users" section is what I'm referring to.

I just make sure all samba users are in 1 group, tie that group to the share with 770 permissions, and then each individual share within the parent samba folder had 770 permissions with the owner being tyler:tyler, or curt:curt, etc. Then they just have valid users tag, which seems to work well.

I've always used this method, so I can't say "this fixed my issue" because I never had an issue to begin with. I've been running with the same smb.conf since about 2006 when I first loaded 6.06 and added file server services to it.

---

### Post by garvinrick4 on 2010-01-29
> **Roasted said:**
> I never had trouble with Samba. I use OSX, Ubuntu, Kubuntu, OpenSuSE, Vista, XP, 7, etc on my network with no issues with network shares, permissions, etc.

However, I've always added the user level of security to my smb conf file. Example:

[Jason]
    path = /home/jason
;    browseable = yes
    writeable = yes
    valid users = jason
    comment = Jason

[Tyler]
    path = /media/storage/tyler
    writeable = yes
;    browseable = yes
    valid users = jason, tyler
    comment = Tyler

The "valid users" section is what I'm referring to.

I just make sure all samba users are in 1 group, tie that group to the share with 770 permissions, and then each individual share within the parent samba folder had 770 permissions with the owner being tyler:tyler, or curt:curt, etc. Then they just have valid users tag, which seems to work well.

I've always used this method, so I can't say "this fixed my issue" because I never had an issue to begin with. I've been running with the same smb.conf since about 2006 when I first loaded 6.06 and added file server services to it.
Try Lucid.

---

### Post by Roasted on 2010-01-29
> **garvinrick4 said:**
> Try Lucid.

Lucid isn't out yet. Why would I use Lucid on a production machine?

---

### Post by sparker256 on 2010-01-29
> **Roasted said:**
> Lucid isn't out yet. Why would I use Lucid on a production machine?

Because you are in a testing and developement forum:D

---

### Post by garvinrick4 on 2010-01-29
> **Roasted said:**
> Lucid isn't out yet. Why would I use Lucid on a production machine?
I believe we were discussing Testing and Development in Lucid.

---

### Post by Roasted on 2010-01-29
> **sparker256 said:**
> Because you are in a testing and developement forum:D

How in the hell did I end up here...

man, I suck. My apologies.

---

### Post by phillw on 2010-01-29
> **cariboo907 said:**
> There was a samba update today, 

There are some extra samba releases popping their heads into the release emails, must be samba day :D

[https://launchpad.net/ubuntu/lucid/+queue?queue_state=3&queue_text=samba&start=60](https://launchpad.net/ubuntu/lucid/+queue?queue_state=3&queue_text=samba&start=60)

Regards,

Phill.

---

### Post by cariboo on 2010-01-29
Just out of curiosity what version of Samba are you running on the systems you are trying to connect to? Or is it smbclient that is causing the problem. 

You don't need the Samba server to connect to Windows systems. I know this is a pretty basic question, but it would be nice to narrow it down to the correct package. So is it other OS's that every one is having problems connecting to, or is it Samba server?

---

### Post by sparker256 on 2010-01-29
> **tad1073 said:**
> When is samba going to be fixed? I am using nfs right now but would like to know when samba is going to be fixed so I can add a network printer.
On my system it was today:D. I can now browse to my windows XP printer.

Bill

---

### Post by garvinrick4 on 2010-01-29
> **cariboo907 said:**
> Just out of curiosity what version of Samba are you running on the systems you are trying to connect to? Or is it smbclient that is causing the problem. 

You don't need the Samba server to connect to Windows systems. I know this is a pretty basic question, but it would be nice to narrow it down to the correct package. So is it other OS's that every one is having problems connecting to, or is it Samba server?

For me it is a Windows Network to see all devices on a small home network. All other machines
or USB devices on those machines. Can access all partitions on its home computer through Places dropdown menu. When you try to access network in Places drop down menu you can see
windows network icon, click on this icon and you will be presented with Password, will not accept password. On all other installs Karmic twice and Vista and Windows 7 has no problem. One Vista/Ubuntu dual boot desktop with Router, USB printer and USB external. One Windows 7/Karmic/Lucid triple boot with Wifi.
My Lucid is actually an upgrade from Karmic and on upgrade network was incapable of accepting password. Since opening bell of Lucid. Samba installed is 2:3.4.0-3 samba and samba common.
and 1.2.63 system-config-samba. Will accept Samba/Windows Workgroup password for printing.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

---

### Post by tad1073 on 2010-01-30
> **cariboo907 said:**
> Just out of curiosity what version of Samba are you running on the systems you are trying to connect to? Or is it smbclient that is causing the problem. 

You don't need the Samba server to connect to Windows systems. I know this is a pretty basic question, but it would be nice to narrow it down to the correct package. So is it other OS's that every one is having problems connecting to, or is it Samba server?

I have an Ubuntu 9.10 file server sharing a ntfs drive, samba is version is:
```
:~$ samba --version
Version 4.0.0alpha9-GIT-27087e6
```
It works with 9.10 desktop, and xp, haven't tried W7 yet.

---

### Post by ubername on 2010-01-30
Thid thread looks like a duplicate of 

[http://ubuntuforums.org/showthread.php?t=1341141](http://ubuntuforums.org/showthread.php?t=1341141)

see also 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

---

### Post by garvinrick4 on 2010-01-30
> **tad1073 said:**
> It is not just a printer issue. I am asked for a password if I am accessing shares or printer but samba rejects my password and keeps asking for it.
Used this fix and now I have network access in Workgroup in Lucid.
 Given you already have a created a Samba user and password.

sudo gedit /etc/samba/smb.conf
 

Find this section in the file:
 ####### Authentication #######
 # “security = user” is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;  security = user
 

Uncomment the security line, and add another line to make it look like this:
 security = user
username map = /etc/samba/smbusers
 		                   		  		  		 		 			 				__________________

---

### Post by tad1073 on 2010-01-31
It is working now, I installed samba4 and that seemed to solve the problem.

---

### Post by cariboo on 2010-02-07
It also seems to be fixed in smbclient 2.3.4.5-dfsg-1ubuntu1 too.

---

### Post by ybytyruzu on 2010-02-21
I installed Kubuntu desktop, and under gnome I can browse windows network with dolphin.
Maybe is Nautilus problem.

---

### Post by ybytyruzu on 2010-02-24
Hi, here still unabled to browse networks with Nautilus. As i mentioned, with Dolphin under Ubuntu I can open all my networks location.

---

### Post by ybytyruzu on 2010-02-24
Hi, here still can't browse networks with Nautilus. As I mentioned, with Dolphin under Ubuntu I can open all my networks location.

---

### Post by ybytyruzu on 2010-02-24
Sorry for my dupe post....

---

