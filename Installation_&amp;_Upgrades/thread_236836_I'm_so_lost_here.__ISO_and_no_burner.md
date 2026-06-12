---
title: "I'm so lost here.  ISO? and no burner"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by jangnim on 2006-08-15
Okay so I loaded UBUNTU on this laptop.  It has no cd burner or anything so wonderful as that so I am not certain what to do. When I loaded the OS it came up with an upgrade page that in turn downloaded 182 files.  Before that began a message came up saying there was a new version.  I downloaded the file and determined it is an ISO.  I extracted it to my home directory but now I'm just stuck on what to do.  What program file do I run to begin the upgrade installer?  I looked around the forum a bit but found nothing that was exactly what I needed so I'm hoping somebody can guide me a bit.

I'm not new to unix/linux, but my older versions were from the early 90's and there have been lots of changes since then.  I'm not even certain how to work with ISO files.  

Thanks to all in advance for any help.

---

### Post by cstudent on 2006-08-15
What version of Ubuntu did you install?

---

### Post by jangnim on 2006-08-15
Ubuntu 5.10 I think it is called breezy badger or some such thing.

---

### Post by cstudent on 2006-08-15
You can try doing a dist-upgrade using apt-get. You would most definitely want to be using broadband and not dialup.

You can do that by doing the following from a terminal window.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.breezy

```
```

gksudo gedit /etc/apt/sources.list

```

In gedit under the Search menu use the replace feature. Replace breezy with dapper for all instances. You should probably comment out any non-official repositories you have enabled by putting a # at the beginning of the repository link line. Save the file and close it. Before going further, you should be sure to back up any data you don't want to take a chance on losing.

```

sudo apt-get update

```
```

sudo apt-get dist-upgrade

```

---

### Post by zxee on 2006-08-15
[http://ianconnor.blogspot.com/2006/07/installing-ubuntu-on-dell-poweredge.html](http://ianconnor.blogspot.com/2006/07/installing-ubuntu-on-dell-poweredge.html)

The above link may just work for you. Or do a search on installing without cd.
Hope that helps.

---

