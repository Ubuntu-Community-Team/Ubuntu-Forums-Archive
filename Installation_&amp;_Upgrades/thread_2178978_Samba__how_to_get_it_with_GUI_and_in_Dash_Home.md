---
title: "Samba : how to get it with GUI and in Dash Home?"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by ButchMel on 2013-10-06
I'm completing 12.04.3 server installation with graphic interface, and installed the samba packages under terminal.

How can I get the ''visual'' version of it (and I guess, access it from Dash Home view)?

Just jumping from 10.04 here... fresh install though.

Tks,
B.

---

### Post by TheFu on 2013-10-06
I don't understand.  There isn't a GUI with "12.04.3 Server".  
What did you do?

If you wan to maintain samba shares, edit files under /etc/samba/

I suspect Nautilus might have an interface that appears to manage samba shares, but last time I checked, it was per-user and used gvfs, not CIFS.  If you read in the forums, you'll find where people tried to use Nautilus shares and ran into issues.  On a server, it is best to edit the config files in /etc/samba then manage the daemons with start/stop/status/restart like all other server daemons.  IMHO.

---

### Post by ButchMel on 2013-10-06
I just installed the gui on top of server:

sudo apt-get install ubuntu-desktop

The thing is now i can get samba in the Dash Home box, but i cannot enter it : when prompted to enter a password (admin) it does not recognize it... I only have one password in this freshly installed system, no other user or password than the one i have created at installation and now use to enter the system...

By the way i get exactely same issue with NTFS configuration tool.

---

### Post by TheFu on 2013-10-06
So, you expect a desktop GUI to control server components?  I see.
Do you think that is air you are breathing? [*in my best Mobius voice*]

I live in the Ubuntu Server world. No GUI. Lots of reasons this is better for my needs, but I understand the desire to learn with a GUI if there is just 1 box to manage.  With that, I'll drop off, since I cannot be helpful.

---

### Post by ButchMel on 2013-10-06
Well... Sorry if I am not 'man enough' for the real thing :))...

Yes indeed, I have only one box to manage.  Thing is: I have done this with guidance in the past using terminal.  Unfortunately, can't find the steps to do it again (it was about 2 years ago, with 10.04 server).  Yep I had the graphic stuff, but I did that partly with Morbius help and guidance.  If I could just find back all this ( I had printed the things, but moved since and don't find this 5-6 pages which was extremely useful.

Thanks anyway :)
B

---

### Post by Elfy on 2013-10-06
> don't find this 5-6 pages which was extremely useful

perhaps this one [http://ubuntuforums.org/showthread.php?t=1945342](http://ubuntuforums.org/showthread.php?t=1945342)

you can find your posts/threads here - [http://ubuntuforums.org/member.php?u=1582730](http://ubuntuforums.org/member.php?u=1582730) from the latest posts/threads items

---

### Post by Morbius1 on 2013-10-06
I know this has become expected of me but I'm confused by this whole thread.

It sounds like you want a GUI to control Samba. If that is the case and you already have the Ubuntu desktop of your server then you have 2 options depending on how complex the shares you are trying to create are:

** You can use Nautilus itself by right clicking a folder you own and selecting "Sharing Options" - that will install the samba server package automatically if you already haven't installed it.

** You can also install the more traditional samba gui:
```
sudo apt-get install system-config-samba
```

But I detect a sub-plot here about root / sudo and being able to invoke either one of these:
> when prompted to enter a password (admin) it does not recognize it... I  only have one password in this freshly installed system, no other user  or password than the one i have created at installation and now use to  enter the system...

By the way i get exactely same issue with NTFS configuration tool.         
That is another problem entirely and I have little experience with that issue.

[COLOR=#0000cd]* Side note: I wouldn't use ntfs-conf on a drunken bet but that's just me.*[/COLOR]

---

### Post by ButchMel on 2013-10-06
Wow ! :) 
Elfi, many thanks! This is the thread i was looking for !

Thanks also for pointing out how to look for this - i had been unsuccesful trying with just a basic "search".

Sincerely,

ButchMel

---

### Post by ButchMel on 2013-10-07
Ok, trying the basic stuff in terminal:

gksu gedit /etc/samba/smb.conf    and here again, can't get in: my admin password is not recognized in terminal mode either.

testparm -s gives me this (i should see 5 drives, but don't see these. However, on desktop, I can enter any of these, so yes: yjese are mounted):

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


The command: net usershare info --long  give no result.

robert@CrabConnect:~$ net usershare info --long
robert@CrabConnect:~$ 

I'm almost getting to the point of reinstalling everything from scratch,...

---

### Post by ButchMel on 2013-10-07
Should add that on a Mac OS X machine, I can see the Ubuntu machine. looks like i can access the network printer, but see no drives yet.

---

### Post by ButchMel on 2013-10-07
Morbius1, thanks for jumping in.  Looks like I aready have installed this. But (pls see below - messages) - I can't see my drives.  And the issue is really that I can't edit the smb.conf neither in graphic or terminal.  I'm going through the thread pointed out by Elfy above (yours/mine).  Which I would have expected to debug me, but the issue seems to be that unrecognized password.

---

### Post by ButchMel on 2013-10-09
Ok solved the access problem to edit the smb.conf - thanks to steeldriver - gksu mode was set to 'su' instead of 'sudo'.

However, now that I have edited with the basic setting, I am facing a new issue when I try to access from a Mac running OS X 10.8.5:

When trying to access with a user name, I am prompted with:

'There was a problem connecting to the server “crabconnect”.The version of the server you are trying to connect to is not supported. Please contact your system administrator to resolve the problem.'' 

Then, if I try to connect as a Guest:

'There was a problem connecting to the server “crabconnect”.Check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator.''

Have no clue what to do, what to try, which commands...

Thanks ahead,

B.

---

### Post by Morbius1 on 2013-10-10
If you are trying to access a Linux Samba server from OSX please post the output of the following commands from the Linux machine:
```
testparm -s
```
```
net usershare info --long
```

---

