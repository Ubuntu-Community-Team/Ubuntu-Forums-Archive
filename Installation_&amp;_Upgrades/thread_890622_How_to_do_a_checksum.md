---
title: "How to do a checksum?"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by David4 on 2008-08-15
Hi
need to do a checksum on an ISO download and cannot remember how to do it, I have the code/file to place on the utility but for the lights of me just cannot remember/find the utility I used, remember was a file?.
thanks
David

---

### Post by iaculallad on 2008-08-15
> **David4 said:**
> Hi
need to do a checksum on an ISO download and cannot remember how to do it, I have the code/file to place on the utility but for the lights of me just cannot remember/find the utility I used, remember was a file?.
thanks
David

On your terminal:

```
md5sum filename.iso
```

---

### Post by David4 on 2008-08-15
thank you very much,I am not in Ubuntu, downloaded an ISO copy of GUFI into my WIN XP download folder, before I convert this ISO file I like to make sure is OK, GUFI site provides the checksum value, not sure how to do this, I remember doing it with Ubuntu 8 
thanks
David

---

### Post by iaculallad on 2008-08-15
> **David4 said:**
> thank you very much,I am not in Ubuntu, downloaded an ISO copy of GUFI into my WIN XP download folder, before I convert this ISO file I like to make sure is OK, GUFI site provides the checksum value, not sure how to do this, I remember doing it with Ubuntu 8 
thanks
David

Just compare whatever hash value displays when you issue the command i mentioned above with the value posted on that site. If they are equal, then you're all good to burn the ISO file to a media. Just be sure that you burn it at a lower speed to lessen the chances of corrupting burned data.

---

### Post by David4 on 2008-08-15
Sorry, do not want to be a pest.
I am on windows xp, have the ISO file downloaded, again, in windows, how to run the checksum.
thanks
David

---

### Post by iaculallad on 2008-08-15
> **David4 said:**
> Sorry, do not want to be a pest.
I am on windows xp, have the ISO file downloaded, again, in windows, how to run the checksum.
thanks
David

Here, try reading this [page]("https://help.ubuntu.com/community/HowToMD5SUM") from Ubuntu Community on how to do MD5 testing. It gives an option on how to do it in windoze.

---

### Post by Pro-reason on 2008-08-15
> **David4 said:**
> Sorry, do not want to be a pest.
I am on windows xp, have the ISO file downloaded, again, in windows, how to run the checksum.
thanks
David
To be honest, this is not a Windows forum, so you can't expect us to help you with Windows software.

Try [http://downloads.activestate.com/contrib/md5sum/Windows/](http://downloads.activestate.com/contrib/md5sum/Windows/)

---

### Post by David4 on 2008-08-15
iaculallad
thank you very much, I believe this is what I need, thank you again for your patience
David

---

