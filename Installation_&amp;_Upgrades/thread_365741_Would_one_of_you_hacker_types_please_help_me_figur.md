---
title: "Would one of you hacker types please help me figure this out"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by humbll on 2007-02-20
I would like to see a howto for using Truecrypt to COMPLETELY encrypt the ENTIRE Edgy installation (swap, /home /root, everything) I have some ideas but perhaps you may be able to do it better. I know this should be possible because there is an article in these forums about doing this in dapper drake. 

Perhaps we could install Edgy on a small partition, set up the truecrypt partitions, then install or transfer Edgy to them using images of the small partition, then run fdisk to convert the original partition to Linux swap, then encrypt that.

Anybody else feel free to post your ideas about this here, too.

Developers: In this day and age we should have the capability to select this as an option from the install CD and have it automatically implemented. Security is a very necessary thing to have with all of the identity theft, corporate & govt espionage, popularity of easily stolen laptops, etc. We the people would love to have this capability as an option upon installation!

Many thanks to all of you crackerjacks working on this and all other open source projects, we really appreciate everything you people do.

---

### Post by Stephen Howard on 2007-02-20
Why Truecrypt rather than the usual linux crypto packages?

---

### Post by Stephen Howard on 2007-02-20
I've also never been clear on the advantage of encrypting /root.  I merely encrypt /swap, /tmp and my personal partition.  Who cares if anyone sees /root when you've kept all your personal stuff in its own partition.

---

### Post by orb9220 on 2007-02-20
And you have to recompile truecrypt evertime the kernel changes. So how would the system boot up if a new kernel breaks truecrypt?

The reason I use truecrypt is for a fat32 partition which xp and ubuntu share. I can run truecrypt  in winxp or ubuntu to access.

If you want to encrypt all linux partitions I would not recommend this with truecrypt.

They are slow to complaints when stuff breaks and behave like "Oh linux version why would you use that."

They are concetrating on Vista compatibility right now. And have dropped their plans for a Gui for linux version.

They give the feeling that linux is not important for their time and resources.

---

### Post by Stephen Howard on 2007-02-20
> They are slow to complaints when stuff breaks and behave like "Oh linux version why would you use that."That's a bit of a worry - if they stopped updating their module, users who entrusted their data to Truecrypt would be screwed.

...and then there's the license - its not GPL so the distros will never maintain a version.

Not sure I trust 'em - they have the feel of a Windows company that is just playing at linux.

---

### Post by humbll on 2007-02-24
Thank to all of you for the insight, after more research i have decided to go with this:
[http://www.ubuntuforums.org/showthread.php?t=293299&page=2](http://www.ubuntuforums.org/showthread.php?t=293299&page=2)
 It works well.

---

