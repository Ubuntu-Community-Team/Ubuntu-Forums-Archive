---
title: "Rhythmbox: No samba support?"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tom-ubuntu on 2008-09-21
Hi there,

Just started playing around with 8.10 doing my daily 'work'.

I can not set my library folder to

"smb://server/music"

like I could previous versions; "operation not supported".

Any ideas?

Cheers
Tom

---

### Post by zolookas on 2008-09-21
Have you tried going to Places->Connect to server and connecting to your server? I think samba server then should be included in file open dialog. I can't test it myself, because i have no samba servers in my network.

---

### Post by howefield on 2008-09-21
can't give you the answer but just to say I can't play music from my samba shares either, you are not alone,  I need to copy them over to a local disk.

Hope someone can share the answer if there is one :guitar:

zolookas is correct in that once connecting to the samba server makes them show up in the file open dialogue but Rhythmbox doesn't want to open the files.

---

### Post by tom-ubuntu on 2008-09-21
Thanks for the replies, guys.

Yes, with nautilus for example I can connect to the share and also play them in Totem. It is only Rhythmbox.

---

### Post by UbuWu on 2008-09-22
Did you file a bug?

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+filebug](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+filebug)

---

### Post by tom-ubuntu on 2008-09-22
> **UbuWu said:**
> Did you file a bug?

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+filebug](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+filebug)
Just filed a bug: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/273294)

Hope this is correct and usefull, first one I filed. If not, please tell me how to improve/correct. Thanks.

---

### Post by UbuWu on 2008-09-22
You explained the problem very well. One more useful thing to include is the version of rhythmbox you are currently running. I tagged the bug as a potential regression in intrepid.

---

### Post by tom-ubuntu on 2008-09-22
Many thanks. I added the version of the apps affected (IMO).

---

### Post by UbuWu on 2008-09-22
It is best to get the versions from synaptic so you have the full version number. You are probably using rhythmbox 0.11.6svn20080916-0ubuntu1. This is important because e.g. there could be a 0.11.6svn20080916-0ubuntu2 fixing this problem and with only 0.11.6 it would be impossible to know which one you had.

---

### Post by cariboo on 2008-09-22
If you install smbfs you can manually mount your shares until the problem is fixed,

```
sudo mount //server/music /media/music
```

Jim

---

### Post by tom-ubuntu on 2008-09-23
UbuWu: package version updated for Rhythmbox and Samba

cariboo907: Thanks for the tip. It is just a parallel installation on my notebook. I do not listen to music there. Just testing a little bit and trying to help out.

---

### Post by tom-ubuntu on 2008-10-04
Bug reported upstream as requested:

[http://bugzilla.gnome.org/show_bug.cgi?id=554980](http://bugzilla.gnome.org/show_bug.cgi?id=554980)

(still not working as of today)

---

