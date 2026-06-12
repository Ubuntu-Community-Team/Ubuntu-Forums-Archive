---
title: "New Install Transfering PPAs to Current Ubuntu Version"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by wewantutopia on 2014-06-10
Hello, I've decided to upgrade my systems from 12.04 to 14.04.

When I upgrade my systems I keep them all the same by, among other things, copying my /etc/apt/sources.list.d folder, /etc/apt/trustdb.gpg, and /etc/apt/trusted/gpg files from the existing system to the new.  I then (using synaptic) mark all installed programs on the existing system and install them on the new system.  Finally, I copy the home folder (using rsync) from the existing system to the new one (to maintain all settings etc).

Going from 12.04 to 14.04, how can I easily update all the PPAs to Trusty from Precise?

Thank you!

---

### Post by ajgreeny on 2014-06-10
Depending on which ppa repos you have now, my main recommendation is to proceed with great care; you may not need any ppas.

Some of the old ppas may not exist for 14.04, resulting in error messages when you try to update, and some others may not be necessary as 14.04 may well have the version of a package that the ppa for 12.04 provided for that version of Ubuntu.

It would be better to just make a list of the files in sources.list.d with ```
ls /etc/apt/sources.list.d > ppa.txt
``` and the refer to the ppa.txt file in your home and check if they are available for 14.04

---

### Post by monkeybrain20122 on 2014-06-10
Basically, you go to /etc/apt/sources.list.d/ and change the file names from 'precise' to 'trusty' and then edit each file again changing all occurrences of 'precise' to 'trusty'. Save all changes and then run 
```
sudo apt-get update
```

This can be done easily with gui. Open Software&Updates, go to Other Software, which will show a list  of all the ppas, then just edit each one and change 'precise' to  'trusty', then reload.

As ajgreeny said some ppas for Precise may not be available for Trusty so you should check first. If ppa no longer works for Trusty just delete the files with its name in /etc/apt/sources.list.d

---

### Post by wewantutopia on 2014-06-11
Thanks for the replies.   I got it resolved successfully using a combination of both of your suggestions.  I first went through the ppa.txt in 14.04 to see what is in the software center/ no longer needed (like the mtp fix).

Thanks!

---

