---
title: "jaunty 'add-apt repository'"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by littlepeon on 2009-12-20
hello all....
just read somewhere else about adding ppa:launchpad repositories in karmic (article writer was using 'mint linux'). the article mentioned that this could be used with the following code:
sudo add-apt-repository ppa:bisigi
is this new command 'add-apt-repository' just available in karmic or better?
googled it, but couldn't find any answers...searching the forum yielded a clue:

 "add-apt-repository is provided by the package python-software-properties"

i have this package in jaunty...but the command 'add-apt-repository' yields a command not found error. i know that this command is not needed as i could edit my sources.list manually or by gui----its just that i find this command interesting and would like to add it if at all possible. its just the point that this would be neat to use....
does anybody know if this is available to jaunty or less users?
is there any backports of python-software-properties that would enable this 'feature'????

thanks in advance
-Peon

---

### Post by porl on 2009-12-20
as far as i know, it is a karmic only thing, not available in earlier versions.

---

### Post by SilverWave on 2010-01-05
[Install The Newest Firefox ppa with command "add-apt-repository" (9.10 & above)]("http://ubuntuforums.org/showthread.php?t=1352580&pp=75")

> _Install the latest: Firefox-3.6b6pre & Firefox-3.7a1 Packages._

A new command in Karmic makes it easy to add a PPA repository and its  key, all at once.

**Gain access to the latest ubuntu-mozilla-daily ppa.**
     Code:
     sudo add-apt-repository ppa:ubuntu-mozilla-daily 


Yes Karmic and above.

---

### Post by defensorfedei on 2010-03-04
I know this thread is a little old, but you can install the the Karmic version of python-software-properties, in Jaunty.  

Go to: [http://ns2.canonical.com/karmic/all/python-software-properties/download](http://ns2.canonical.com/karmic/all/python-software-properties/download)

Select a mirror, download, and install.

Then the 'sudo add-apt-repository' should work.  It worked for me when I added the dockbarx repository.

---

### Post by rana_mum on 2010-12-20
> **defensorfedei said:**
> I know this thread is a little old, but you can install the the Karmic version of python-software-properties, in Jaunty.  

Go to: [http://ns2.canonical.com/karmic/all/python-software-properties/download](http://ns2.canonical.com/karmic/all/python-software-properties/download)

Select a mirror, download, and install.

Then the 'sudo add-apt-repository' should work.  It worked for me when I added the dockbarx repository.

but will this changing of python properties affect previously installed software in jaunty??

---

