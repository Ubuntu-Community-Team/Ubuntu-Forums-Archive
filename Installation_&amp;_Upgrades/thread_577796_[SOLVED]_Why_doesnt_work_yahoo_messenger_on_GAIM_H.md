---
title: "[SOLVED] Why doesnt work yahoo messenger on GAIM? How can that fixed?"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by the_analyzer on 2007-10-16
can anyone help me because it says wrong username. I dont know, i tried changing the host, or the ports, with the yahoo messenger info pages.
thnx

---

### Post by perlluver on 2007-10-16
One would guess, Gaim is no longer being produced, it is now known as Pidgin.  I have no problems running yahoo messenger in Pidgin.

---

### Post by the_analyzer on 2007-10-16
but pidgin wasnt at add/remove applications, do you know where I can download it, and after that should I delete gaim?
Another question about pidgin, it supports MSN? right?

---

### Post by perlluver on 2007-10-16
You can get pidgin at [www.pidgin.im](www.pidgin.im), however it was in the add/remove programs under internet.  Yes it also supports MSN.

edit: Yes you can delete GAIM if you would like.

---

### Post by perlluver on 2007-10-16
You can also try synaptic.  Just search for pidgin, it is under all the gaim files.  You will want to install pidgin and pidgin-data.  Or also sudo apt-get install pidgin.

---

### Post by santiagoward2000 on 2007-10-16
I don't think the problem is Gaim, I still haven't upgraded to Pidgin and I still can connect to Yahoo. Perhaps is just some temporary network error? How long have you been getting this error?

---

### Post by the_analyzer on 2007-10-16
I searched at the synaptic, and wasn't there.

---

### Post by perlluver on 2007-10-16
Did you also try running sudo apt-get install pidgin in a terminal?

Edit:  What system are you running?  Feisty, Gutsy?

---

### Post by santiagoward2000 on 2007-10-16
> **perlluver said:**
> Did you also try running sudo apt-get install pidgin in a terminal?

Actually, Pidgin is not in Feisty's repository, it was added to Gusty.

---

### Post by perlluver on 2007-10-16
Yeah I kind of figured that, that's why I asked.

---

### Post by santiagoward2000 on 2007-10-16
> **perlluver said:**
> Yeah I kind of figured that, that's why I asked.

LOL, sorry, I wrote it before you edited your post...

---

### Post by perlluver on 2007-10-16
So that wouldn't show up in apt-get either would it?

---

### Post by santiagoward2000 on 2007-10-16
Hmm, nope. You had to add some 3rd party repository if you wanted pidgin to show up on Synaptic or apt-get, but I don't know anyone that has it (although I'm quite sure there must be at least one).

---

### Post by perlluver on 2007-10-16
Automatic Installation
Add to /etc/apt/sources.list: 
deb [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports
If you want source as well: 
deb-src [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports
Use Synaptic to reload and upgrade, or run the following command in a terminal window (note: dist-upgrade is required particularly if you are still using GAIM packaged by Ubuntu): 
sudo apt-get update; sudo apt-get dist-upgrade
Enjoy!

---

### Post by santiagoward2000 on 2007-10-16
> **perlluver said:**
> Automatic Installation
Add to /etc/apt/sources.list: 
deb [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports
If you want source as well: 
deb-src [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports
Use Synaptic to reload and upgrade, or run the following command in a terminal window (note: dist-upgrade is required particularly if you are still using GAIM packaged by Ubuntu): 
sudo apt-get update; sudo apt-get dist-upgrade
Enjoy!

LOL, I told you there must be one :lolflag:
NICE!

---

### Post by the_analyzer on 2007-10-16
Hey I tried to edit that file, but I think I dont have the permission. I dont know. Im the administrator here, who has the permission?

---

### Post by perlluver on 2007-10-16
You are the administrator, but you have to type sudo to get superuser rights.

---

### Post by santiagoward2000 on 2007-10-16
> **the_analyzer said:**
> Hey I tried to edit that file, but I think I dont have the permission. I dont know. Im the administrator here, who has the permission?

On a console type:
```
sudo gedit /etc/apt/sources.list
```

Then put your password. That should do it.

---

### Post by perlluver on 2007-10-16
> **santiagoward2000 said:**
> On a console type:
```
sudo gedit /etc/apt/sources.list
```

Then put your password. That should do it.

Thanks, wasn't sure how to get that. :)

---

### Post by santiagoward2000 on 2007-10-16
> **perlluver said:**
> Thanks, wasn't sure how to get that. :)

You're welcome! Glad to help!

---

### Post by the_analyzer on 2007-10-16
thanks a lot guys that your are helpin me but I editet the file (I wroted that line in the end, righ? )any way when I enter the commands they show me some errors like follow

my username:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
my username:~$ 

I tried with synaptic, i searched ther pidgin, but nothing was there. what is the problem with ubuntu guys? Always is this hard and unstable?

---

### Post by santiagoward2000 on 2007-10-16
> **the_analyzer said:**
> thanks a lot guys that your are helpin me but I editet the file (I wroted that line in the end, righ? )any way when I enter the commands they show me some errors like follow

my username:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
my username:~$ 

I tried with synaptic, i searched ther pidgin, but nothing was there. what is the problem with ubuntu guys? Always is this hard and unstable?

I believe that's an error in the Sources connection. Maybe it will work later...

---

### Post by perlluver on 2007-10-16
You can try restarting too, sounds like something else is using the installation process.

---

### Post by the_analyzer on 2007-10-16
Thank you very much
yes i found it in synaptic now, it showed to the update system too. anyway i installet pidgin, but i get an error when I try to connect with yahoo.
maybe I have changed before into a wrong host. 
look at the snapshot.

---

### Post by perlluver on 2007-10-16
try scs.msg.yahoo.com port 5050

---

### Post by wolfen69 on 2007-10-16
[http://www.getdeb.net/](http://www.getdeb.net/) has pidgin. install data file first. to install the files, just double click.

---

### Post by the_analyzer on 2007-10-16
thnx, but it stayed a little bit, and than was connected,  I activated new  email notification, but no alert were. But nevermind. 

THANKS YOU GUYS THAT HELPED ME, YOU ARE GREAT, UBUNTU COMMUNITY IS GREAT.
I wish, the system to be like that too, but if it does not, will be.

---

### Post by perlluver on 2007-10-16
If solved please mark as solved in the thread section.

Edit: Thread Tools at top.

---

