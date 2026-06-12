---
title: "Ubuntu One and Karmic"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-06-19
I got my invitation for Ubuntu One but it seems to broken ?

ppa install bug:
[https://bugs.launchpad.net/ubuntuone-client/+bug/389363](https://bugs.launchpad.net/ubuntuone-client/+bug/389363)


Also tried to compile the ubuntuone-client but it broke...


Anyone knows how to run Ubuntu One on Karmic ?

--

---

### Post by castrojo on 2009-06-19
I added it manually:

```

deb http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main

```

---

### Post by plun on 2009-06-19
> **whiprush said:**
> I added it manually:

```

deb http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main

```

Thanks whiprush  !

```
plun@plun-laptop:~$ **sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4DA51AF64BD0ECAE**

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4DA51AF64BD0ECAE
gpg: requesting key 4BD0ECAE from hkp server keyserver.ubuntu.com
gpg: key 4BD0ECAE: public key "Launchpad Private PPA for Ubunet" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


plun@plun-laptop:~$ **sudo apt-get install ubuntuone-client**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmenu-cache0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-configglue python-nautilus python-pam python-psyco python-pycurl
  python-pyinotify python-serial python-twisted-bin python-twisted-core
  python-twisted-names python-twisted-web python-zopeinterface
  ubuntuone-storage-protocol
Suggested packages:
  python-pam-dbg libcurl4-gnutls-dev python-pycurl-dbg python-pyinotify-doc
  python-wxgtk2.8 python-wxgtk2.6 python-wxgtk python-twisted-bin-dbg
  python-tk python-qt3 python-profiler python-zopeinterface-dbg
The following NEW packages will be installed:
  python-configglue python-nautilus python-pam python-psyco python-pycurl
  python-pyinotify python-serial python-twisted-bin python-twisted-core
  python-twisted-names python-twisted-web python-zopeinterface
  ubuntuone-client ubuntuone-storage-protocol
0 upgraded, 14 newly installed, 0 to remove and 1 not upgraded.
Need to get 2246kB of archives.
After this operation, 12.4MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

;)

---

### Post by plun on 2009-06-19
Follwup... and it works...;)

[[img]http://www.ubuntu-pics.de/thumb/16734/snapshot3_hw35o7.png[/img]](http://www.ubuntu-pics.de/bild/16734/snapshot3_hw35o7.png)


About Ubuntu one:
[https://ubuntuone.com](https://ubuntuone.com)

It took 2 weeks for me to get an invitation.....

---

### Post by ronacc on 2009-06-19
I wonder how this will compare with Unite that Opera just released in Opera 10beta ?
[http://unite.opera.com/](http://unite.opera.com/)

---

### Post by plun on 2009-06-19
> **ronacc said:**
> I wonder how this will compare with Unite that Opera just released in Opera 10beta ?
[http://unite.opera.com/](http://unite.opera.com/)

Opera/Unite is interesting but doesn't give you a backup for your personal files. 

For more then 2GB Ubuntu One plans is clearly OK..... 10$/10GB/month

Server power/bandwith costs.....;)

---

### Post by ronacc on 2009-06-19
I wasn't looking at it that way , more of a quick and dirty VPN for road trips . does ubuntu one allow you to access from any OS/browser or just another instance of Ubuntuone ? I haven't had time to look into it much yet .

---

### Post by plun on 2009-06-19
> **ronacc said:**
> I wasn't looking at it that way , more of a quick and dirty VPN for road trips . does ubuntu one allow you to access from any OS/browser or just another instance of Ubuntuone ? I haven't had time to look into it much yet .

Ok, Ubuntu One calls Firefox and prompt for a password to Launchpad.

Other findings........:(

- It doesn't support drag&drop for several files.....:shock:

(1000 jpg files might be a challenge to upload)


- MS Skydrive is free for 25GB


--

---

### Post by inportb on 2009-06-19
> **ronacc said:**
> I wonder how this will compare with Unite that Opera just released in Opera 10beta ?
[http://unite.opera.com/](http://unite.opera.com/)

Why Unite when [POW]("https://addons.mozilla.org/en-US/firefox/addon/3002")'s already been around for ages? AFAIK Unite doesn't do SJS, SQLite, or any of the other serverside goodies.

---

### Post by ronacc on 2009-06-19
> **inportb said:**
> Why Unite when [POW]("https://addons.mozilla.org/en-US/firefox/addon/3002")'s already been around for ages? AFAIK Unite doesn't do SJS, SQLite, or any of the other serverside goodies.

Thanks , I'll take a look at that also but to be honest the only reason FF is even on my box is it is default . I've been an Opera user since it "fit on a floppy" :p

---

### Post by biasquez on 2009-06-19
i requested an invitation to ubuntu one 1 month ago but i see this:

You are currently on the waiting list for Ubuntu One. As soon as we can, we'll be sending you an invitation code via email.

---

### Post by tad1073 on 2009-06-20
same here

---

### Post by NCLI on 2009-06-20
> **plun said:**
> Ok, Ubuntu One calls Firefox and prompt for a password to Launchpad.

Other findings........:(

- It doesn't support drag&drop for several files.....:shock:

(1000 jpg files might be a challenge to upload)

Uh, you can just drag&drop files you want to upload to your '~/UbuntuOne/My files' folder.

---

### Post by plun on 2009-06-20
> **NCLI said:**
> Uh, you can just drag&drop files you want to upload to your '~/UbuntuOne/My files' folder.

Thanks and nope.... and its **step 5** and the icon which is broken

[https://ubuntuone.com/support/installation/](https://ubuntuone.com/support/installation/)

The webinterface works but doesn't handle drag&drop.

See if I can fix the icon....;)

---

### Post by plun on 2009-06-20
I failed with the icon....:^o

Found a bug report also.

[https://bugs.launchpad.net/ubuntuone-client/+bug/389627](https://bugs.launchpad.net/ubuntuone-client/+bug/389627)

---

### Post by Bou on 2009-06-20
I don't like the fact that you can only synchronise one particular folder, or that it uses a notification icon. Weren't they trying to get rid of those?

I think, when installed, it should put a tab in nautilus' preferences with a checkbox saying "synchronise files with Ubuntu One" and a list of folders to synchronise, where you could add or remove as many as you want.

Wouldn't you like that better?

---

### Post by castrojo on 2009-06-20
> **plun said:**
> I failed with the icon....:^o

Found a bug report also.

[https://bugs.launchpad.net/ubuntuone-client/+bug/389627](https://bugs.launchpad.net/ubuntuone-client/+bug/389627)

Yeah I got bit by that last night, dobey is already on it. Also, there is a nightly's PPA if you want to bleed more, just replace "beta" with "nightlies" in your ppa URL.

---

### Post by plun on 2009-06-20
> **whiprush said:**
> Yeah I got bit by that last night, dobey is already on it. Also, there is a nightly's PPA if you want to bleed more, just replace "beta" with "nightlies" in your ppa URL.

OK, thanks again.

Bleeding more doesn't help...;)



```
plun@plun-laptop:~$ **killall ubuntuone-client-applet**

plun@plun-laptop:~$ [B]ubuntuone-client-applet --signup
[/B]
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-client-applet", line 510, in __open_folder
    if self.__need_update:
AttributeError: 'AppletIcon' object has no attribute '_AppletIcon__need_update'
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-client-applet", line 476, in __popup_menu
    self.__menu.popup(None, None, gtk.status_icon_position_menu,
AttributeError: 'AppletIcon' object has no attribute '_AppletIcon__menu'

```

---

