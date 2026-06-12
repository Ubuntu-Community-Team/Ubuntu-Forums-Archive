---
title: "dpkg won't work"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Ludwig7666 on 2007-10-10
I was in the add and remove app and was on firefox when this happened. On firefox I was on virtualbox.org site and instead of downloading then installing it all I hit was open with gdebi package installer (default) (by mistake :P). It frozed the window so I couldn't close it. Even after a machine restart I still can't use dpkg. I can't install/remove or update anything now.

This is the Warning it gives me now.
(Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.)

Ignore the @programmer. lol I'm for sure no programmer, just a habit of naming my computers Progammer for some odd reason. :P Well anyways, this is what happens when I type in the warning commands.

(ludwig@Programmer:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_CA    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/universe Packages
Fetched 4B in 1s (3B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ludwig@Programmer:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ludwig@Programmer:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
ludwig@Programmer:~$)

I am a newbish to linux also. Hopfully this isn't to bad. Cause then I'm really screwed with my GBs of data :P damn dvd burner I think is broken!

---

### Post by forestpixie on 2007-10-10
you need to use sudo

```
sudo dpkg --configure -a
```

---

### Post by Ludwig7666 on 2007-10-10
I did and just did it again.. all i get is 

ludwig@Programmer:~$ sudo dpkg --configure -a
Password:
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
ludwig@Programmer:~$


EDIT: oops didn't use sudo the first time. my bad. :P but after useing sudo that's what I get..

---

### Post by forestpixie on 2007-10-10
try 

```
sudo apt-get install -f
```

---

### Post by Ludwig7666 on 2007-10-10
I get this 

ludwig@Programmer:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ludwig@Programmer:~$

---

### Post by forestpixie on 2007-10-10
oooh and round and round you go :(

try this 

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

it was virtualbox - right?

---

### Post by Ludwig7666 on 2007-10-10
Yes, I was trying to install Virtualbox.

ludwig@Programmer:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox
Password:
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
ludwig@Programmer:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
ludwig@Programmer:~$ 


this is what I get from that.

Any way to reinstall dpkg? :P remember newb to linux.

Am I suppost to see dpkg in the system monitor? I don't think I can see it.

---

### Post by Ludwig7666 on 2007-10-10
I went into the folder named DPKG

The files I do see is 

available
available-old
diversions
diversions-old
lock
statoverride
statoverride-old
status
status_old
status-old

What's up with that old? Maybe I did something really screwed up somewheres?? :P

---

### Post by forestpixie on 2007-10-10
no they're backups - not sure how to go about this now.

I've got to go now - it's time to work

try searching for,or variations of the error

dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

see if you can replace it with an empty file

I'll be back later

---

### Post by Ludwig7666 on 2007-10-10
sure thing. thanks for trying with the time you had. :)

---

### Post by Rui Pais on 2007-10-10
hi,
try:
```
sudo dselect update
```

if that didn't restore /var/lib/dpkg/status you have to replace by the backup:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_BAD
sudo cp -a /var/lib/dpkg/status-old /var/lib/dpkg/status
```

good luck

---

### Post by Ludwig7666 on 2007-10-10
AWSOME! thanks man. that worked. I had to force remove virtualbox after but it worked.. I could update and remove the other apps I wanted with no problem.

---

### Post by Rui Pais on 2007-10-10
Excellent!

btw, which the one did the trick? 
I know that dselect update restores /var/lib/dpkg/available but i'm not sure about /var/lib/dpkg/status... or it was the copy of backups that worked?

---

### Post by Ludwig7666 on 2007-10-10
i did the first one and it did nothing. I do remember that I could of changed the file names before so that's why the second one worked.. I guess i should of read the full persons problem then just jumping right to the answer. lol wasn't the same problem of course. :P


Now I got the first problem I had to begin with. The package installer froozed up again on me and i can't close the window. 
I tried

ludwig@Programmer:~$ sudo dpkg --remove --force-remove-reinstreq vitrualbox
Password:
dpkg: status database area is locked by another process
ludwig@Programmer:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
ludwig@Programmer:~$ 

I'm not going to touch anything till I know what I'm doing :P I'm sure this time it's easier to fix this time.

---

### Post by Ludwig7666 on 2007-10-10
This is the file

virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb

All I would do is right click it and open with Gdebi package installer..

Nevered really installed anything this way. Is that the correct way? Only installed with the normal add/remove apps if i even used it.

---

### Post by Rui Pais on 2007-10-10
> **Ludwig7666 said:**
> i did the first one and it did nothing. I do remember that I could of changed the file names before so that's why the second one worked.. I guess i should of read the full persons problem then just jumping right to the answer. lol wasn't the same problem of course. :P

Sorry, i don't quite understand you here :( (bad English reader here...)

After using the backup i think it's advisable run the first command again just in case anything need to be done "under the table"...

> 
...
ludwig@Programmer:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
ludwig@Programmer:~$ 

I'm not going to touch anything till I know what I'm doing :P I'm sure this time it's easier to fix this time.

Thats message usually simply means that another instance of dpkg is already running...
Close any running synaptic, gdebi or update-manager running (this one can be running on background)  and try again.

---

### Post by Ludwig7666 on 2007-10-10
> 
Quote:
Originally Posted by Ludwig7666 View Post
i did the first one and it did nothing. I do remember that I could of changed the file names before so that's why the second one worked.. I guess i should of read the full persons problem then just jumping right to the answer. lol wasn't the same problem of course. :P

Sorry, i don't quite understand you here (bad English reader here...)

No problem. I actually suck at english and it's my main and only langauge I use. :P
English is the hardest to learn. Also it don't help that I'm Dyslexic :) 
I used the first code you gave me and it did not work. Then I tried the second code and that did work. Before I even posted this I guess I or something changed the file name. You helped getting the correct ones back.


I checked my system monitor and I don't see anything saying update-manager, gdebi, synaptic. Or are those the background processes?

---

### Post by Ludwig7666 on 2007-10-10
Oh I found a Gdebi-gtk. It's sleeping with 26mbs of mem on it.

I know in windows it could be dangerest to turn off the wrong processer so is this one safe to turn off?

---

### Post by Ludwig7666 on 2007-10-10
gksu
gdebi-gtk
dpkg
frontend
whiptail
preinst


That's how the processes are after another in the list. Seemed to be linked together?

---

### Post by Rui Pais on 2007-10-10
Ok, back again.

yes, you seems to have at least 2 processes that lock dpkg database, gdebi and  dpkg itself (probably a stale one). You can kill any of them in a terminal:
```
sudo killall -9 dpkg
sudo killall -9 gdebi-gtk
sudo killall -9 gdebi
```

No problem with the "killing" (such thing it's only dangerous in old Windows, that shared memory pool across processes :-|)

Or if you want/can you may prefer reboot to ensure that all processes are closed and only the needed ones are running.

About installing a deb, yes you click on it and get gdebi, or better, you can install on a terminal:
```
sudo dpkg -i virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb
```

That will show any error/warning messages and if anything goes wrong, closing the terminal will terminate too any process associated, instead of larking like zombies around as they did before.

hope that helps.

---

