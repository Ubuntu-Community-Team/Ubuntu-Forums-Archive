---
title: "PureFTPd Broken After Upgrade to 12.04"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by greg_jones2 on 2014-06-08
I'm a noob so please, any info you need ask and give me a command, I will get it for you. (Yes I already did a Search, Google is a good friend, and I'm not the type to register for a forum without searching first)

I recently upgraded a server running 10.04, ISPConfig, MySQL, Apache & PureFTPd.

The Upgrade went smoothly except MySQL had issues. (After 2 days of fighting I was able to fix this.)

The other problem created by this upgrade is I can not login via FTP anymore.  I keep getting a '530 Authentication Failed' error.

What I have done so far:
[LIST]
[*]Recreate FTP User in ISPConfig.
[*]Create different user in ISPConfig.
[*]Try to connect to different sites in ISPConfig.
[*]Uninstall PureFTPd (common & mysql using apt-get & aptitude and purged)
[*]Reinstall PureFTPd
[/LIST]

All the above have not worked.  I am at a loss, please help.

---

### Post by Ubi_one_2014 on 2014-06-09
how did you create the users?

virtual ( with mysql)or local?

---

### Post by greg_jones2 on 2014-06-11
> **Ubi_one_2014 said:**
> how did you create the users?

virtual ( with mysql)or local?

I created users through the ISPConfig Control Panel.  I'm just guessing but I would guess those are created through mysql and are virtual users, right?

---

### Post by greg_jones2 on 2014-06-14
I don't believe I stumped this whole community.

---

### Post by greg_jones2 on 2014-08-10
Can anyone give me any ideas?  I cannot FTP into my server.  I don't want to have to reinstall everything just to gain FTP access again.

---

### Post by SteveHillier on 2014-10-15
I don't know if this thread is still live but I too have had big problems getting pure-ftpd to work with ISPConfig.
Ahhh...
But I have not got it going.
There were a whole lot of red herrings about using TLS over FTP and then I hit on it
I set up the client 'lcuk'. I set up an ftp user 'lcuk-ftp' under that client.  So when I put in the username in FileZilla I typed in 'lcuk-ftp'.
Then I looked at the ftp user name in ISPConfig console and noticed that the ftp username was prepended with the client name.
So I typed in lcukftp-lcuk as my username in Filezilla and....

Connected beautifully.

If this helps anyone

---

