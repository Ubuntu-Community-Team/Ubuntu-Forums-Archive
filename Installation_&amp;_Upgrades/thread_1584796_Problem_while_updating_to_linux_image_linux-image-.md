---
title: "Problem while updating to linux image linux-image-2.6.32-25-generic (2.6.32-25.44)"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by shaquille on 2010-09-29
Hi,
   I am using the latest Ubuntu 10.04 Lucid lynx. Sometimes ago while i am updating my operating system to linux-image-2.6.32-25-generic (2.6.32-25.44) with update manager, after downloading all the files it was running the installation. During installation suddenly my pc turned off, may be for some power issue. Then while i again start my pc and tried to restart the update process the update manager show me a message.

[COLOR="Red"][SIZE="3"][COLOR="Black"]Not all updates can be install[/COLOR][/SIZE][/COLOR]
Run a partial upgrade, to install as many as updates as possible

This can be caused by:
* A previous upgrade which didn't complete.
* Problem with some of the installed software.
* Unofficial software packages not provided by Ubuntu.
* Normal changes of a pre-release version of Ubuntu.

Then I tried to open the synaptic package manager. But it didn't open either and show another message which suggest to run the command in the terminal: "sudo dpkg --configure -a". 
[IMG]http://www.facebook.com/photo.php?pid=1591653&fbid=1607585036600&id=1445401420[/IMG]
And unluckily it wasn't work. and show the messgae: "dpkg: parse error, in file '/var/lib/dpkg/updates/0103' near line 0:
 newline in field name `#padding'"

Now what can i do?

---

### Post by P4man on 2010-09-29
Have a look here:
[http://ubuntuforums.org/showthread.php?t=385886](http://ubuntuforums.org/showthread.php?t=385886)

(leave out the "sudo apt-get install samba" since you dont need samba)

---

### Post by shaquille on 2010-09-30
> **P4man said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?t=385886](http://ubuntuforums.org/showthread.php?t=385886)

(leave out the "sudo apt-get install samba" since you dont need samba)

Thanx a lot, that works.

---

