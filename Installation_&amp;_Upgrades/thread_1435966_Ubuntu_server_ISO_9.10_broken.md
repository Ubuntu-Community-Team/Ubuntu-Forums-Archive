---
title: "Ubuntu server ISO 9.10 broken?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by fhendrik on 2010-03-22
Hi folks,

I've just downloaded Ubuntu server (ubuntu-9.10-server-amd64.iso) and the automatic installation fails with the following message:

[INDENT]Failed to retrieve the preconfiguration file

The file needed for preconfiguration could not be retrieved from file:///cdrom/preseed/ubuntu-server.seed. The installation will proceed in non-automated mode.
[/INDENT]

The seed files are on the CD, in the right place, but they aren't readable even when accessed from another computer (less says 'read error').

Is there anything I can do to fix this?

cheers
Hendrik

---

### Post by fhendrik on 2010-03-22
P.S. Looks like I've got a corrupted CD image. Will try redownloading.

---

### Post by phillw on 2010-03-22
> **fhendrik said:**
> P.S. Looks like I've got a corrupted CD image. Will try redownloading.


Hi, corrupt iso is a pain. 

Pulling together the various parts of the community documentation, along with experience of seeing and helping people with boot cd's I've put together a quick check-list for making the CD's

It's in my Signature Link, or directly here --> [http://forum.phillw.net/viewtopic.php?f=4&t=36](http://forum.phillw.net/viewtopic.php?f=4&t=36)  (It links back to the community documents, just saves me typing it all out each time ;) )

Regards,

Phill.

---

### Post by fhendrik on 2010-03-23
I was actually looking for an MD5 sum, but I couldn't find it on the download page. I think you can only find it if you browse the server directory. Would be helpful to have it on the download page.

Anyway, it was indeed a corrupt download. I fetched the image again via BitTorrent and it worked.

thanks for the help
Hendrik

---

