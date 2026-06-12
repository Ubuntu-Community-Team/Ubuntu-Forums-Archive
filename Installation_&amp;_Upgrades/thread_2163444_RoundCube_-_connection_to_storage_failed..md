---
title: "RoundCube - connection to storage failed."
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by kikstart on 2013-07-18
Hi All, 

I have spent a lot of time reading posts and different websites trying to get Roundcube to work with no luck.
There many threads and posts out there which I have tried, the only install guide that works to the point of successful (web installer tests) results on the web installer is official install instructions below -: 

[http://trac.roundcube.net/wiki/Howto_Install](http://trac.roundcube.net/wiki/Howto_Install)

After following the guidelines i still cannot log into Roundcube keep getting 'unable to connect to storage'
The sql database roundcube and usercube user are created and privileges set,  so i'm unsure what is causing this issue when the installer webpage gives me green results on my set-up. 

_setup installed_
Ubuntu Server with KUbuntu desktop. 12.04.2 LTS & 4.8.5 KDE
Roundcubemail 0.9.2
Postfix (and postfix admin) email working well.
Courier IMAP
SpamAsssassin, ClamAV, Postgrey, Amavisd
MySQL
PHP
Apache

Any advise or help would be most appreciated..

---

### Post by Boab1993 on 2013-07-18
Hello kikstart

If you just simply want a good install of roundcube, you can install it automatically via the synaptics package manager. 
Just search roundcube in it and all packages required will be shown,just double click the top item and follow the instuctions.

Hope this helps

---

### Post by kikstart on 2013-07-18
Hi Boab1993,

All packages are installed except postgreSQL,  as i'm using MySql..  thanks for the advise.

I have installed previously the downloadable packages (older version of roundcube) and they failed to even work with mysql let alone install correctly. 

So I'm at a brick wall in regards to getting this working..  i cannot log into the 'usercube' account in roundcube.   Eventually I want to link this into postfix.

---

### Post by Boab1993 on 2013-07-18
Excellent, now we know where the problem lies, sadly it looks like its with mySQL
Try entering this as a command in mySQL

CREATE DATABASE roundcubemail;
GRANT ALL PRIVILEGES ON roundcubemail.* TO yournamel@localhost IDENTIFIED BY yourpassword ;

Then enter FLUSH PRIVILEGES

See how that goes

---

### Post by kikstart on 2013-07-18
I've already done the privileges on the account in mysql.

This guide is basically what I've followed, but the issue is i cannot log into roundcube.   

[http://www.upubuntu.com/2012/02/how-to-install-roundcube-webmail-071-on.html](http://www.upubuntu.com/2012/02/how-to-install-roundcube-webmail-071-on.html)

---

### Post by Boab1993 on 2013-07-18
I see. It seems to have everything there, only thing id say is it doesn't mention to enter 'FLUSH PRIVILEGES' during rights set-up.
If the only a problem with logging in it can be a number of things.
What kind of email account are you using(Gmail, hotmail, etc)?
It can also be a problem with the SMTP & IMAP configuration

Run through what you did during the setup, the more information the easier it'll be!

---

### Post by kikstart on 2013-07-19
Thanks for your help Boap1993, most appreciated.

This is the thread which basically is my set-up. 

[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

My telnet tests show IMAP is working and i can send and receive email.

Next stage was I then installed Roundcube,   I've tried package install of roundcube and also the manually installing latest version from the developers website (obviously customize to my set-up domain / email etc.)  The latest/manual install 0.9.2 is better results during testing. 

I did have a thought if maybe an encrypted home directory may be causing the issue?   as I am running KUbuntu-desktop on Ubuntu server.

I have recreated the roundcube database and account and set the privileges and imported the tables, but again i get the same results.. 

Any ideas or thoughts?

---

### Post by Boab1993 on 2013-07-19
Thank you for the appreciation, its always nice to hear feedback!

Its a good hunch, it is highly possible an encrypted home folder could be throwing up errors, if you are sending/recieveing mail from your home folder.
Exploring it would be a matter of changing your postfix address to outside your home folder, i.e. root, but this is not advised according to the tutorial you have linked.

If it turns out that is the case, easy way out is to: 
Copy all files from your home folder to another folder of any type, just make sure you don't delete it.
Delete the home folder.
Make a new folder called 'home'
Move your the original files back in.

This actually 'un-encrypts' your home folder.

Try it out, it can't hurt. Just make sure to backup.

Since its connection errors, my thoughts are still around configuration files and IMAP etc, I'll look into it a bit more.

If you can get your apache logs up here, it would show some sort of anomaly hopefully

Good luck!

---

