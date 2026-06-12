---
title: "I don't have root user password, Need an mp3 player.."
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by rsercano on 2013-12-10
Hi, as i mentioned at the title i need an mp3 player for my ubuntu 10.04 and i don't have a root password. So can you post me a link to download a zip package or something else which i can listen my mp3 files on ubuntu. Thanks in advance. (btw i can't even install mp3 plugin for rhytmbox - need root pass.)

---

### Post by fantab on 2013-12-10
To do things as root you must use 'sudo'. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
MP3 codec is found in the package, 'ubuntu-restricted-extras' along with 'flashplayer' and more.
You can install it from Terminal with:
```
sudo apt-get install ubuntu-restricted-extras
```
... you will be asked for a password, type in your user password. You can't see it as you type... just type it and hit 'enter'.

---

### Post by drmrgd on 2013-12-10
It's going to be difficult to play MP3s without being able to install packages.  I'm assuming when you say you don't have root password it means that you're not the sysadmin or owner of the computer you're on (please clarify if I'm wrong).  Probably the easiest way, assuming that's the case, is the ask the sysadmin nicely to install ubuntu-restricted-extras so that you can listen with Rythmbox.  

You could try to download an MP3 player and build it from source, putting the files in a location for which you have permissions.  But, as I've found after a quick look, most of these packages require a host of dependencies and such that would ultimately require root access to install.  So, if you can't do it the conventional way, it's going to be tough.

---

### Post by oldos2er on 2013-12-10
Ubuntu 10.04 desktop version is no longer supported, so it's repositories have been moved to old-releases. Important to know if and when you obtain permission to install any packages.

---

### Post by Dennis N on 2013-12-10
Apparently you can still install a package for 10.04 using the original repositories - I just this morning (Dec 10) installed keepassx on Ubuntu 10.04 in the usual way using apt-get. I assume this is because the 10.04 server is still supported until Apr 2015, so the repositories are open. I suppose there are no updates, however, for desktop.

So if you have sudo privileges, you probably can install a player. 

Lucid packages still listed here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by oldos2er on 2013-12-10
Good to know, thank you.

---

### Post by mastablasta on 2013-12-11
hmm in windows this issue is easilly solved with various portable players and mostly opensource portable programs & codecs. is there nothing similar in linux (like portable apps)? and if so why not?

perhaps some older version of VLC in this link?: [http://portablelinuxapps.org/](http://portablelinuxapps.org/)

edit: you'd probabyl still need admin rights to make the file executable or am i wrong?

---

### Post by monkeybrain20122 on 2013-12-11
Why is anyone still using 10.04?

---

### Post by rsercano on 2013-12-12
i can't use sudo or apt-get or any command that needs root password. @mastablasta i'm trying your link now but can't open VLC. Should i do someting else, i checked  "Allow file executing as a program"

---

### Post by rsercano on 2013-12-12
@drmrgd thats sad to hear... I just got only one folder that i got perrmisson to use. I wanted to download player to that location and open it :(

---

### Post by deadflowr on 2013-12-12
> **rsercano said:**
> i can't use sudo or apt-get or any command that needs root password. 

I don't understand.
Did you do something that removed your user from the sudo or admin groups?

By default, nothing anyone does with Ubuntu requires a root password.
All elevated usage is normally done through sudo, which gives the user root rights, as it where. 
If you setup the system, then the password you used at installation would be the password to use.
If you didn't setup Ubuntu yourself, or forgot what the password is that you used when you set it up
(password is required during setup, you cannot proceed with the installation without making one)
then follow this to reset the password
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
if you're not sure if you are in the sudo group post the output for
```
id youruser'sname
```
(replace youruser'sname with your username)
and see if sudo or admin(two of the more common group given rights within sudoers)are listed.
if either are, then you have the abilty to run as root through sudo.
If no listing for either of those, then post it and we'll work to get them for you.

---

### Post by rsercano on 2013-12-12
Actually that computer is a remote setuped pc. And root is a remote person that i can't talk often. So i can't use admin rights.

---

### Post by drmrgd on 2013-12-12
> **rsercano said:**
> @drmrgd thats sad to hear... I just got only one folder that i got perrmisson to use. I wanted to download player to that location and open it :(

After your initial post, I did a very brief and quick Google search for lightweight MP3 players for Ubuntu that you might be able to install locally within your own directory.  Unfortunately - and like I said, I didn't research this extensively - it seems that you still need to install codecs to handle the MP3s or other libraries to make the MP3 player function.  I don't think any of that would be possible without root permissions.  So, you might be stuck here unfortunately.  Maybe someone will come up with something, but given the replies so far, it's looking a bit grim.  Sorry :(

---

### Post by rsercano on 2013-12-12
@drmrgd well, thanks for your concern at least ;( .I will make do with youtube..

---

