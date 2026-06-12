---
title: "How to arrange mounting of drives?"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by egg on 2005-02-23
Hi,

(first off, im a noob)

I have dev/hda1 as my first and main drive with the OS on. I've just added a new hard drive, partitioned it and formated it as /dev/hdb1.

Following some guides, I ended up mounting it as '/data'. So the folder data is in the main root folder. I did chmod it 777.

The thing is.. I want this physical drive to be accesible to my home account.. and the smb shares tied to that. At the moment, of course, I don't see the data drive.

What's the best way to have this set up, so the new drive is sitting/accessible to my standard home account?

thanks!

---

### Post by alastair on 2005-02-23
The obvious way is just to mount it somewhere like :

/home/<YOU>/data

rather than /data.

No need for "chmod 777" - just make it owned by you (chown <your login>).

---

### Post by egg on 2005-02-24
thanks, that's what I thought. 

I had read somewhere, not to mount it on an existing home partition... wasn't really sure though...

---

