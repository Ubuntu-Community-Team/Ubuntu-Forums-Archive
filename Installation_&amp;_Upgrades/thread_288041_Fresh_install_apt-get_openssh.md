---
title: "Fresh install: apt-get openssh"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Cyklopz on 2006-10-29
I just installed 6.10 Server from a freshly burned Iso.  The install seemed to go just fine.  I boot up and log in and try to install openssh using apt-get and it asks for the install cd.  When it tries to access the cd it just hangs at "0% [Working]" at the command line.  I have waited several minutes but no progress starts.  I do not hear normal access sounds coming from the cdrom but the access light is on (solid, not flashing).

At this point all I can do is reboot the system as it is totally locked up (no caps lock change on keyboard etc.).

As I mentioned above I just used this cdrom drive and disk to do the install minutes earlier so they should be good.  Any ideas on what is wrong?  I searched these forums but did not see anything that seemed to pertain to my issue.

Thanks for any suggestions.

Cy

---

### Post by taurus on 2006-10-29
I don't think you have to install openssh since ssh is already installed on your machine.  And if you don't want to use the CD again, just edit your /etc/apt/sources.list and put a # sign in front of the first line in there, regarding cd-rom...

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Cyklopz on 2006-10-29
Taurus,  thanks for your suggestion.  That allowed the install to proceed normally and now I can remote into this machine.

Still not sure why it is chocking when trying to access the original install cd/cdrom but i will save that for another day.

Thanks again.

Cy

---

### Post by taurus on 2006-10-29
So, you are talking about sshd--openssh-server...  Don't worry about using the installing CD.  Use the net to download and install stuff on your machine then.

---

### Post by h3llfyr3 on 2006-11-19
I had the exact same issue

---

