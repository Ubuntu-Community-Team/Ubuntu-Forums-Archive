---
title: "Install Asterisk 1.4 on gutsy 7.10"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by phi1ip on 2008-02-01
Hello,

Is there a howto for installing asterisk on ubuntu 7.10?

The asterisk.org website seems to be geared to other distributions.
 
I thought.... i saw it for ubuntu somewhere sometime ago. I am running the 64 bit desktop version.

any suggestions would be great. maybe i should be using the server version.....

---

### Post by Partyboi2 on 2008-02-02
make sure you have universe repo ticked under software sources (System>Admin>Software Sources)
then
```
sudo apt-get install  asterisk
```


---

### Post by phi1ip on 2008-02-05
Thanks, that worked a treat. but i cannot get gastman to connect.

next is configuring. the website below has descriptions, 
[http://www.voip-info.org/wiki/index.php?page=Asterisk+config+manager.conf](http://www.voip-info.org/wiki/index.php?page=Asterisk+config+manager.conf)
but has a different format to what was in my system. below is my file. i managed to work out that i needed to create a user on ubuntu that was a member of the asterisk group to read and write these files.
 
below is my manager.conf file in /etc/asterisk/ 
-----------------------------------------------------------------------------------------------------------
;
; Asterisk Call Management support
;

; By default asterisk will listen on localhost only.
[general]
enabled = yes
port = 5038
bindaddr = 127.0.0.1

; No access is allowed by default.
; To set a password, create a file in /etc/asterisk/manager.d
; use creative permission games to allow other serivces to create their own
; files
#include "manager.d/*.conf"

so i created the file below as described in the above file, and kind of similar to what was in the description on the [www.voip-info.org](www.voip-info.org) website above.

phil.conf file below
------------------------------------------------------------------------------
secret=blackjac

permit=127.0.0.1/255.255.255.0
read=system,call,log,verbose,command,agent,user
write=system,call,log,verbose,command,agent,user
------------------------------------------------------------------------------

so i installed gastman. then fire it up. enter "127.0.0.1"
then enter 'phil' and 'blackjac' for username and password.

then i get    "logging in" but then "disconnected from remote host.

any suggestions? have i missed something? have i created the file right? password? etc????

---

### Post by phi1ip on 2008-02-05
or can someone recommend a better source of info for me to look at, to work it out by myself.....

any help would be appreciated. or suggestions on how to go about it....

---

### Post by Partyboi2 on 2008-02-05
One of these might help
[https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)
[http://www.asteriskdocs.org/](http://www.asteriskdocs.org/)
[http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/30/Setting-up-Asterisk-with-Faktortel-on-Ubuntu--HOWTO](http://www.lynchconsulting.com.au/blog/index.cfm/2008/1/30/Setting-up-Asterisk-with-Faktortel-on-Ubuntu--HOWTO)
[http://www.onlamp.com/pub/a/onlamp/2003/07/03/asterisk.html](http://www.onlamp.com/pub/a/onlamp/2003/07/03/asterisk.html)

---

### Post by rgunn on 2008-02-19
[http://www.voip-info.org/wiki/view/How+to+install+Asterisk+1.4+and+FreePBX+2.3.1+in+Ubuntu+Linux&view_comment_id=15498](http://www.voip-info.org/wiki/view/How+to+install+Asterisk+1.4+and+FreePBX+2.3.1+in+Ubuntu+Linux&view_comment_id=15498)

the version in the repo is asterisk 1.1.4 not 1.4 try the above link and let us know how u go

---

