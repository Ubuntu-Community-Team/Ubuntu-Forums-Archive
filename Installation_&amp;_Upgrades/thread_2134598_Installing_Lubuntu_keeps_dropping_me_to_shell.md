---
title: "Installing Lubuntu keeps dropping me to shell"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by oxf on 2013-04-11
Hi,

I'm trying to put Lubuntu 12:10 on my Acer Aspire One netbook. 

I created the live USB and first hint of trouble came when I tried to boot from the live USB. After the initial screen where you choose live CD/install/memtest etc it starts, the Lubuntu screen flashes up and then drops me to the shell with terminal cursor etc.

I decided that maybe that was just a quirk with my hardware so tried a full install instead. That appeared to load OK so I let it do the install. Again after booting it just drops me to a shell. The specific error message is:

```
Ubuntu 12:10 acer tty1

acer login: * Starting
* Starting crash report submission daemon

acer login:
```

My specfics are:
Acer Aspire One
Processor Atom N2600
Integrated graphics
Mem 1GB

Anyone else had this problem and any ideas how to get this installed and running?

Thanks

Caitlin

---

### Post by ajgreeny on 2013-04-11
If you now login at the shell with your username and password (password will not be shown on screen, not even as ***) then use command **startx**, do you get any error messages that help.  It may tell you that an xsession is already running, even though it has crashed, but it's worth a try.

---

### Post by oxf on 2013-04-11
> **ajgreeny said:**
> If you now login at the shell with your username and password (password will not be shown on screen, not even as ***) then use command **startx**, do you get any error messages that help.  It may tell you that an xsession is already running, even though it has crashed, but it's worth a try.

Thanks for the reply..

I cant paste the result of startx as this is a different laptop but in short I get this:

```
Initializing extension xxxxxxxx........  
(many lines here)
Loading extension GLX

Fatal server error:
no screens found

server terminated with error (1) closing log file
Xinit: giving up
Xinit: unable to connext to X server
```

The strange thing is I can boot Ubuntu from a USB just fine. I wanted to use Lubuntu because I like it's simplicity and speed and the fact it does not have Unity.

---

### Post by Bashing-om on 2013-04-11
oxf; Hi !

Let's get a bit more info:
From that log in terminal after you have logged in, instead of the command "startx";
What results from the terminal command:
```
sudo service lightdm
``` in trying to start Xserver.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by oxf on 2013-04-13
Thanks for the reply Bashing-om,


```
sudo service lightdm

Usage /etc/init.d/lightdm COMMAND
```

I have no idea what this means!

Caitlin

---

### Post by ajgreeny on 2013-04-13
Try "sudo service lightdm start" as it is asking for a command for the service.

---

### Post by oxf on 2013-04-14
OK sorry, I was displaying my ignorance there!

Well that command results in:
Multiple "loaded plugins "xxx" 
followed by:

```
Skipping profile in /etc/appamor.d/disable: usr.sbin.rsyslogd
* Starting AppAmor profiles           (OK)
* starting MTP server ntpd             (OK)

```

followed by flashing cursor which wont accept any more commands even "sudo halt"

---

### Post by oxf on 2013-04-21
Well I've been doing a bit of googling around on this one. Now I admit that I don't fully understand this but this is what I've found. There seems to be some history of incompatibility between Lubuntu and the Cedar Trail drivers for the Intel Atom chips (N2600 in my case). As yet I've not found a suggested way  around this. I don't understand enough to fix this so I can only hope maybe things might be better when 13.04 gets released? 

What I also can't understand is why Ubuntu will work fine on this machine but not Lubuntu?

---

