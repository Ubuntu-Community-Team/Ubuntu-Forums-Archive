---
title: "help!! help!!"
date: 2005-04-03
forum: Installation &amp; Upgrades
---

### Post by wxm505 on 2005-04-03
I am new to Ubuntu.I installed Warty4.10 a month ago.Everything was running well.
Then I tried to upgrade it to Hoary. What I did was that I used Synaptic package manager. I reloaded first but I found I could not connect some of the servers.So I 
gave up and close Synaptic.
When I logged out from this session and wanted to log in , it pop up some error
messages:

[COLOR=Navy]/etc/gdm/Pression/Default: Registering your Session with wtmp and utmp
/etc/gdm/Pression/Default: running : /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var
/run/utmo -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "wxm505"
/etc/gdm/Xsession: Begnning session setup .
Unable to read ICE authority file
/home/wxm505/.ICEauthority[/COLOR]

I can not neither log in gnome nor failsafe with this user(the main user).
what I can do is to log in failsafe terminal with this user or  log in gnome
with any other user.

How can I do to fix it??  any help please:(
Thank u very much indeed.

---

### Post by fizgig on 2005-04-03
There's a file in your directory called something like .ICEauthoritylock.  You need to boot to a console (in the GDM menu) and rename/delete that lock file.  Then you ought to be able to log in normally.

---

### Post by Gandalf on 2005-04-03
see [http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin) to gain access and delete that file

---

### Post by wxm505 on 2005-04-04
That is great!! problem solved .
Cheers mate!!
another issue is I live in uni and use proxy.
When I upgraded from warty to hoary by synaptic
I can connet all the http server but ftp.
When I chose apt-get update , I can connect all the
ftp servers but http.
There must be something wrong about the proxy setting.
I did set the proxy correctly because I can access internet
successfully. 
Any help??

---

### Post by Gandalf on 2005-04-04
[QUOTE=wxm505]That is great!! problem solved .
Cheers mate!!
another issue is I live in uni and use proxy.
When I upgraded from warty to hoary by synaptic
I can connet all the http server but ftp.
When I chose apt-get update , I can connect all the
ftp servers but http.
There must be something wrong about the proxy setting.
I did set the proxy correctly because I can access internet
successfully. 
Any help??[/QUOTE]
 hmmmmm.. i don't know much about proxy, never used them on linux... sorry

---

