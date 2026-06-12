---
title: "Network Help Needed."
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by Scribe_05 on 2005-11-17
I have only just installed Ubuntu, my first try at Linux.

I had 3 PC's which worked well on a Home Network under XP Pro and added a 4th on which I installed Ubuntu.

I use the same Username and Password on all machines, and on the XP machines, each shares the 'My Documents' Folder and some other Special Folders for specific types of Files.

When I log on to the Network Servers however from Ubuntu, and select one of the other PC's, the only Shared Folders shown are the 'Special' ones. 

I certainly would appreciate if someone could tell me what I have done wrong, and how to correct this.

Also, when I try to access the Ubuntu machine from one of the others in Windows Explorer, I get a Pop-Up Window with the heading 'Connect to localhost.localdomain', and the message, 'Connecting to ???' with Blank Fields for a User Name and Password.

No matter what I enter however, I cannot connect, so I must have missed something else, and therefore would also appreciate if someone could tell me what should be entered in these fields.

---

### Post by tonysathre on 2005-11-17
look at these posts:
[http://ubuntuforums.org/showthread.php?t=12306&highlight=shares](http://ubuntuforums.org/showthread.php?t=12306&highlight=shares)
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
[http://ubuntuforums.org/showthread.php?t=91486&highlight=shares](http://ubuntuforums.org/showthread.php?t=91486&highlight=shares)

---

### Post by Scribe_05 on 2005-11-18
Thank you for the reply but I still can't connect so I will try again.

I have a Network of 4 PC's, and the WorkGroup name is 'Disney'

PC # 1 is called 'Mickey' - Password 'Mouse' - O/S Windows XP Pro
PC # 2 is called 'Donald' - Password 'Duck' - O/S Windows XP Pro
PC # 3 is called 'Peter' - Password 'Pan' - O/S Windows XP Pro
PC # 4 is called 'Batman' - Password 'Robin' - O/S Ubuntu v 5.1

All 4 show up in 'My Network Places' on the Windows Machines, and I have no problem connecting between #'s 1,2 or 3, but when I try to access # 4 from one of the others in Windows Explorer, I get a Pop-Up Window with the heading 'Connect to localhost.localdomain', and the message, 'Connecting to Batman', with Blank Fields for a User Name and Password.

If it is assumed that the Network is setup correctly, my question again therefore is, "What should I enter in these 2 fields?"

---

### Post by tonysathre on 2005-11-21
have u tried entering your username and password for your linux box, or the domain admin username and password, or root and root password

---

### Post by Scribe_05 on 2005-12-23
I have been away for a while so must apologize for the delay, but to get back to my problem

You name it, I've tried it.

I have no problem at all with the XP PC's but I cannot get these and the Ubuntu PC to talk.

---

### Post by afhp on 2005-12-23
Just wondering, have you installed the samba *server* on the Ubuntu box ?

What is the contents of your /etc/samba/smb.conf ?

---

### Post by Scribe_05 on 2005-12-23
I tried editing (viewing) smb.conf and got the message:

(gedit:8410): Gtk-WARNING **: cannot open display:

Sorry to be such a bore but, how do I "Put Right" what I "Put Wrong"? :confused:

---

### Post by Zimmer on 2005-12-23
[QUOTE=Scribe_05]I tried editing (viewing) smb.conf and got the message:

(gedit:8410): Gtk-WARNING **: cannot open display:

Sorry to be such a bore but, how do I "Put Right" what I "Put Wrong"? :confused:[/QUOTE]
(gedit:8410): Gtk-WARNING **: cannot open display:
sounds a bit ominous...as though you may have made some changes to the computer's networking /DNS/hostname configuration that may confuse it?
Especially when you said earlier
<You name it, I've tried it.>

On a more positive note here are some tips for file sharing using Samba:
For Samba you will need to create a Samba user ..
and a Samba share (ie the folder on the Ubuntu box you want Windows to see)

Have you done this? 

have a look here on how to set up Samba Users and Shares..
scroll down to the Samba Server section.
[http://ubuntuguide.org/](http://ubuntuguide.org/)
and see if the instructions there clarify things for you...
..if in doubt, ask again...

note:
If when trying to browse the share from Windows you are asked for a user and password it will be for the Samba User and Samba password you have set up.
Regards

Zimmer

---

### Post by Scribe_05 on 2005-12-23
Many Thanks for your time.

I think I will try re-installing again from the beginning, which I did not want to do because the system freezes as soon as the Screensaver kicks in, and it took me many, many tries to disable this because as soon as I accessed it a timer started and about 2 seconds later everything would freeze, so I would have to re-boot and try again.

When I am up and running again I will see if I have better luck with the File Sharing but I suspect this will be it for me because it just is not worth the hassle.

---

### Post by Scribe_05 on 2005-12-24
Well, I downloaded a new copy of the 'iso' and re-installed the program and, without any 'fiddling', except of course to make sure Samba was installed, and when I try to view/edit smb.conf, I get the - "Gtk-WARNING **: cannot open display:" message.

When I installed Samba though I did get some error messages which had to do with Passwords which I ignored because I did not think they should have anything to do with the display.

---

### Post by Zimmer on 2005-12-24
[QUOTE=Scribe_05]I tried editing (viewing) smb.conf and got the message:

(gedit:8410): Gtk-WARNING **: cannot open display:

Sorry to be such a bore but, how do I "Put Right" what I "Put Wrong"? :confused:[/QUOTE]
 Just a thought..how exacly are you trying to view the file ?
By right clicking on the icon in Nautilus, or via a Terminal session command ?

Zimmer

---

### Post by Scribe_05 on 2005-12-24
I have started from scratch so think I should correct anything before I 'Try to Walk'.

To start, I changed PC's, just in case there was a problem with the hardware I was using, and re-installed Ubuntu.

The first thing I noticed was that the program did not 'freeze' when the screensaver kicked in or when I tried to make any changes to it, as it did before, so that is a plus.

I then installed Samba with - 'sudo apt-get install samba' (which is Greek to me) and everything seemed to go fine, but at the end I got the following messages, which are also Greek to me.

Setting up Samba (3.0.14a-6ubuntu1) ...
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
 * Starting Samba daemons..

My question now is, "What do these mean, and what should I correct before proceeding?"

Many Thanks.

---

### Post by Zimmer on 2005-12-25
On the desktop  go to System>Administration>Synaptic Package Manager
(The best way to install Software in Ubuntu ..IMHO...it is what I REALLY like about Ubuntu )

Check both Samba and samba-common packages are marked as installed .
If either are NOT marked as installed, check the little status box on the left of the package name and mark for installation, then click  Apply (at the top of the screen)

Then visit [http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)
and start reading from 
Q: How to add/edit/delete network users?
This will tell you to do the following...
#

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

# Insert the following line into the new file

system_username = "network username"

I will translate this bit for you (cos it confused me at the start)
**If** your  Ubuntu user name is called '**scribe**' 
Then in the Terminal type:
**sudo smbpassword -a scribe**   (and it will prompt you for a password, which does not have to be the same as your Ubuntu user password, and confirmation)
then
**sudo gedit  /etc/samba/smbusers**
...and type the following into the new file..
**scribe = "network username"**
save the file
You now have a Samba user called scribe..
Before you start messing with the smb.conf file re boot and have your Windows machines conected and running and see if you can access their shared folders . When(If) they prompt you for the user and password it is the password you have just set up for Samba.....
For Windows to see your Ubuntu folders you will need to go back and follow the instructions for setting up shares in the link above ...and if set up correctly Windows may ask for that very same Samba user and password to connect to the shared area..

Good luck
Zimmer

---

### Post by Scribe_05 on 2005-12-26
Thank you for the reply.

Everything is fine up to:-

Then in the Terminal type:
sudo smbpassword -a scribe (and it will prompt you for a password, which does not have to be the same as your Ubuntu user password, and confirmation)

However, when I come to this:-

then
sudo gedit /etc/samba/smbusers

I hit 'Enter', and I get the message: 

(gedit:7444) Gtk-WARNING **: cannot open display:

The number following gedit changes with each attempt. :confused:

---

### Post by Zimmer on 2005-12-26
[QUOTE=Scribe_05]Thank you for the reply.

Everything is fine up to:-

Then in the Terminal type:
sudo smbpassword -a scribe (and it will prompt you for a password, which does not have to be the same as your Ubuntu user password, and confirmation)

However, when I come to this:-

then
sudo gedit /etc/samba/smbusers

I hit 'Enter', and I get the message: 

(gedit:7444) Gtk-WARNING **: cannot open display:

The number following gedit changes with each attempt. :confused:[/QUOTE]
This is not a Samba problem, but probably a problem with X
Have a look here..
[http://ubuntuforums.org/showthread.php?t=105360&highlight=open+display](http://ubuntuforums.org/showthread.php?t=105360&highlight=open+display)
try using the nano editor instead ..just to see if that will open the file..

I think you will need to post a new thread for the Gtk-Warning**;cannot open display to attract different 'eXperts'..make sure you post some details of your system/hardware etc.

I'm sorry I haven't any experience of this type of problem. It will be quicker to raise awareness with a new thread and title..

Regards

---

