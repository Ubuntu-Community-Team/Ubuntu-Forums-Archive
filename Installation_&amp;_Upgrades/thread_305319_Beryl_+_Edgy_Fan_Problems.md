---
title: "Beryl + Edgy Fan Problems"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by mthakur2006 on 2006-11-23
Hi all,
I recently installed a clean edgy eft and installed beryl. Everything is working absolutely perfect - just the thing that fan comes on more often than not and runs for longer irrespective of me using beryl or not. That is, the fan continues to come on and remain on for even when beryl is not running. This did not happen when I installed just edgy....it happened after I installed beryl.....any suggestions??

Please see my signature to see what I am running :)

---

### Post by mthakur2006 on 2006-12-03
any help at all???

---

### Post by PapaWiskas on 2007-02-12
This is happening to me as well.  Clean install of Uberyl.

Anyone have any ideas?

---

### Post by PapaWiskas on 2007-02-12
I read this thread and thought, hey the only difference since I installed Edgy vs my Dapper install is this program called Beagle.  And since I am semi ignorant, and have no real clue as to what Beagle is nor do I care at the moment, because my fan noise was driving me nuts.  I disabled Beagle, then uninstalled it and removed it from my startup session.  Fan noise stopped.

Here is original thread that gave me a clue.

[http://www.ubuntuforums.org/showthread.php?t=342203&highlight=fan+in+edgy](http://www.ubuntuforums.org/showthread.php?t=342203&highlight=fan+in+edgy)

Which then took me to here....

[https://launchpad.net/ubuntu/+source/beagle/+bug/64326](https://launchpad.net/ubuntu/+source/beagle/+bug/64326)

which then prompted me to run sudo gnome-session-properties Go to my Startup Programs and remove the Beagled reference.

No more excessive fan....:popcorn:

---

### Post by mthakur2006 on 2007-02-16
Thanks for the reply man, but that doesnot solve the problem and I am not bothered anymore as I sold off the machine :)

---

