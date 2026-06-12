---
title: "Edgy Update-Manager doesn't see Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by antar on 2007-04-21
I've tried

```
gksu update-manager -c
gksu update-manager -c -d
```

both options with gksudo instead, both trying in the terminal and in the launcher, I have all the repositories checked, I'm getting both "Important security updates" and "Reccomended updates," I've tried hitting check... nothing. I've made sure I have the latest version of Update-manager.

Nothing. Nada. Zilch. Update-manager still refuses to give me that little button.

I've found other users complaining of the problem but have found no solutions.

I'm trying the "alternate cd" upgrade method but am wondering what the heck's going on.

Any help would be greatly appreciated. Thanks.

---

### Post by antar on 2007-04-21
One thing, though I've read elsewhere it's not a problem:

when I run the commands from the terminal, I get messages saying "warning: could not initiate dbus ." Then, when I hit "check," I get a longer message starting with "could not send the dbus Inhibit signal: did not receive a reply..."

---

### Post by antar on 2007-04-21
The install CD asked to look for more updates online. I let it do so and it froze. Lovely.

---

### Post by antar on 2007-04-21
Okay--I may have been a bit hasty. I ran the upgrade from the Install CD without the new packages and am only NOW getting the updates--there are 189 of them; I'll be lucky if I get them all in half-an-hour.

So the installer may not have frozen after all, it just wasn't telling me that it was downloading the updates.


The upgrade so far seems to have gone smoothly. At the very least, it's no worse than it was...

---

### Post by cmavr8 on 2007-04-22
Hello. How do you upgrade from the cd? I have downloaded/burnt the normal Feisty Fawn cd but no upgrade option...

Do I need the alternate one?

---

### Post by cyrxi on 2007-04-22
[QUOTE=antar]Nothing. Nada. Zilch. Update-manager still refuses to give me that little button.[/QUOTE]

I'm having the same issue on one of my laptops.  This morning an update for the Update Manager (to 0.45.3) was available, so I installed it.  After install I go the "magic little button" but decided not to upgrade at the time.  Now no matter how many times I try to run the update manager or check for updates, I can't get it back.  I could try command line install, but as it's "not recommended" I'd rather not.  I also don't feel like taking the time to download the new install CD when the "upgrade" button should be there...

---

### Post by cmavr8 on 2007-04-22
Maybe it's the update-manager's version.. Maybe 0.45.2 let's you upgrade to Feisty but not 0.45.3.

I'll try downgrading to 0.45.2

---

### Post by cyrxi on 2007-04-22
> **cmavr8 said:**
> Maybe it's the update-manager's version.. Maybe 0.45.2 let's you upgrade to Feisty but not 0.45.3.

I'll try downgrading to 0.45.2

That seems to be exactly the problem.  See the following thread:
[http://ubuntuforums.org/showthread.php?t=416558&page=3&highlight=no+update+button](http://ubuntuforums.org/showthread.php?t=416558&page=3&highlight=no+update+button)

Also let me know how the update goes for you :)

---

### Post by lugburz on 2007-04-22
I have the same problem but I don't trust to downgrade a packages, this don't seem a "clean" method.:( 

The ubuntu team said nothing about this issue?

---

### Post by cmavr8 on 2007-04-22
Ok, tried the suggested 
$ mv .update-manager .update-manager.old
command and the button is present again!

Upgrading right now...
(although pc has a problem and shuts down when left unattended, so I'll try keeping it busy..)

---

### Post by crazy88 on 2007-04-22
I believe that I have a similar if not the same problem with update-manager not recognizing that an update is available.  Running Update-Manager version 0.45.2.
Error I see is:

jay@ubuntu:// $ gksu "update-manager -c"
warning: could not initiate dbus
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py", line 166, in download
    uri=urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 358, in open
    response = self._open(req, data)
  File "/usr/lib/python2.4/urllib2.py", line 376, in _open
    '_open', req)
  File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.4/urllib2.py", line 573, in <lambda>
    lambda r, proxy=url, type=type, meth=self.proxy_open: \
  File "/usr/lib/python2.4/urllib2.py", line 580, in proxy_open
    if '@' in host:
TypeError: iterable argument required

---

### Post by cyrxi on 2007-04-22
I downgraded the Update Manger to 0.45.2 (which I did not mind doing since I only upgraded it this morning) - the button re-appeared, I clicked it, and the upgrade took about 3 hours and is done - everything booted normally, so we'll see how it goes from here.

---

### Post by joncheyne on 2007-04-23
> **cyrxi said:**
> I downgraded the Update Manger to 0.45.2 (which I did not mind doing since I only upgraded it this morning) - the button re-appeared, I clicked it, and the upgrade took about 3 hours and is done - everything booted normally, so we'll see how it goes from here.

I tried this bit (and the removing the folder) and  all I got was the offer to re-upgrade to 0.45.4 again! :confused: 

Still no button. Bug logged ...

---

### Post by pgilmon on 2007-04-25
I have update-manager 0.45.2 (never asked me to install 0.45.3). The update to feisty button wouldn't appear. I'm behind a proxy, but I could get the updates (I think apt is configured to use the proxy in /etc).

Finally, the button appeared when I configured the proxy in Synaptic and in Gnome (System -> Preferences -> Network Proxy). So seems to have something to do with the proxy.

---

### Post by mandela on 2007-04-25
hey..try this..it worked for me.
[http://ubuntuforums.org/showthread.php?t=422430](http://ubuntuforums.org/showthread.php?t=422430)

---

### Post by crazy88 on 2007-04-28
I restarted dbus as suggested with 
> sudo /etc/init.d/dbus restart
It seemed to restart fine, but still no luck with update-manager.

>  gksu "update-manager -c"
warning: could not initiate dbus
Unhandled exception in thread started by <bound method MetaRelease.download of <MetaRelease object (UpdateManager+MetaRelease+MetaRelease) at 0xb69045f4>>
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py", line 166, in download
    uri=urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 358, in open
    response = self._open(req, data)
  File "/usr/lib/python2.4/urllib2.py", line 376, in _open
    '_open', req)
  File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.4/urllib2.py", line 573, in <lambda>
    lambda r, proxy=url, type=type, meth=self.proxy_open: \
  File "/usr/lib/python2.4/urllib2.py", line 580, in proxy_open
    if '@' in host:
TypeError: iterable argument required

---

