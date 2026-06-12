---
title: "Synaptic Package Manager - Server Missing Files"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by nettle on 2006-06-21
I'm new to ubuntu, what I see I definitely like.  However, I'm trying to install the build-essential packages and it looks like the packages I want don't exist on the server, i.e., a gcc compiler and make utility:

[http://us.archive.ubuntu.com/ubuntu/pool/main/g/](http://us.archive.ubuntu.com/ubuntu/pool/main/g/)
[http://us.archive.ubuntu.com/ubuntu/pool/main/m/](http://us.archive.ubuntu.com/ubuntu/pool/main/m/)

Any ideas on how to proceed?  Wait until the server is updated?  Change a repository url in package manager? (how?)  Go back to old school installs?  
~~~~~~~~~~~~~~~~~~~

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ntu20_i386.deb](http://us.archive.ubuntu.com/ubuntu/...ntu20_i386.deb)
403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb)
403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb)
403 Forbidden [IP: 146.137.96.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/....b4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/....b4-1_i386.deb)
MD5Sum mismatch
nettle is online now   	Edit/Delete Message

---

### Post by dwood on 2006-06-21
[QUOTE=nettle]
Any ideas on how to proceed?  Wait until the server is updated?  Change a repository url in package manager? (how?)  Go back to old school installs?[/QUOTE]

It appears something is wrong with us.archive.ubuntu.com at the moment (not that I have any clue).  I've temporarily started using aus.archive.ubuntu.com (Australia, I believe) - you can do that by editing /etc/apt/sources.list and changing the server names as necessary.  Then just click "reload" in Synaptic and that should refresh your package list so you can get the files you need.

---

### Post by krewemaynard on 2006-06-21
[QUOTE=dwood]It appears something is wrong with us.archive.ubuntu.com at the moment (not that I have any clue).  I've temporarily started using aus.archive.ubuntu.com (Australia, I believe) - you can do that by editing /etc/apt/sources.list and changing the server names as necessary.  Then just click "reload" in Synaptic and that should refresh your package list so you can get the files you need.[/QUOTE]

You can also take the 'us.' out of us.archive.ubuntu.com out and it'll work, instead of using 'aus.' I just ran into this problem today, as did a friend of mine. Hopefully it'll get fixed soon.

---

### Post by nettle on 2006-06-21
Yeah, I change the URI in synaptic package manager, and used one of the mirrors.  Also, I found out how to go about it manually, on the command line.  The package manager was easy peasy, after I figured out what I needed to do, which is essentially elucidated here in the previous replies to my post.

Thanks folks!

---

### Post by houstonbofh on 2006-06-21
What is odd is that there is no place telling us what is wrong, or how long until a fix.  <sigh...>  Yes, me too.

---

