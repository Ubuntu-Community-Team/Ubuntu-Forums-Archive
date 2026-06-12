---
title: "Firefox Seg Fault Core Dumped"
date: 2008-08-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-08-14
discovercard.com
paypal.com

sites that use java are locking up and causing seg faults.

Anyone else experiencing this?

---

### Post by Naddiseo on 2008-08-14
I might have submitted this one. Got Seg faults trying to play music files on Wiki, which uses a java applet. My report is #257501.

---

### Post by Robertjm on 2008-08-15
add verizonwireless.com to the list too!

(Makes it kind of hard to pay my phone bill) :(

---

### Post by eeclark on 2008-08-16
> **Robertjm said:**
> add verizonwireless.com to the list too!

(Makes it kind of hard to pay my phone bill) :(

I have to use Opera to get to the sites...you may want to try it.

---

### Post by psyke83 on 2008-08-16
> **eeclark said:**
> discovercard.com
paypal.com

sites that use java are locking up and causing seg faults.

Anyone else experiencing this?

As far as I can see, those sites don't use java (javascript is not the same). Paypal's main site does use Flash, however, and there's a well-known problem with Flash. See [bug #239182]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182") and you can find a testing package that fixes the issue on my [PPA]("https://launchpad.net/~psyke83/+archive").

---

### Post by eeclark on 2008-08-17
Thanks.
Since the folder /etc/adobe was not created I made it myself. (saw on the penguin.swf that these folders may NOT be on your system and that you need to create them yourself).

Then I did a vi mms.cfg
entered
```

WindowlessDisable=true

```
closed by Firefox, reopened firefox and now discovercard.com works just fine.

---

### Post by psyke83 on 2008-08-17
> **eeclark said:**
> Thanks.
Since the folder /etc/adobe was not created I made it myself. (saw on the penguin.swf that these folders may NOT be on your system and that you need to create them yourself).

Then I did a vi mms.cfg
entered
```

WindowlessDisable=true

```
closed by Firefox, reopened firefox and now discovercard.com works just fine.

Thanks for confirming. The flashplugin-nonfree deb in my repository should already pre-install the /etc/adobe/mms.cfg file, by the way.

---

### Post by Robertjm on 2008-08-17
Just to clarify... Are you creating the file within the newly created /etc/adobe folder??

Robert

> **eeclark said:**
> Thanks.
Since the folder /etc/adobe was not created I made it myself. (saw on the penguin.swf that these folders may NOT be on your system and that you need to create them yourself).

Then I did a vi mms.cfg
entered
```

WindowlessDisable=true

```
closed by Firefox, reopened firefox and now discovercard.com works just fine.

---

### Post by psyke83 on 2008-08-17
> **Robertjm said:**
> Just to clarify... Are you creating the file within the newly created /etc/adobe folder??

Robert

The way it works is a little rough. When the package is installed the file is created, and when the package is removed, the file is deleted. User customization may get lost, but in reality there is a per-user location for the configuration file if you need to customize Flash further.

Besides, upon the release of Firefox 3.0.2 (and nspluginwrapper 1.1.0 for 64bit users), we can remove this workaround.

---

