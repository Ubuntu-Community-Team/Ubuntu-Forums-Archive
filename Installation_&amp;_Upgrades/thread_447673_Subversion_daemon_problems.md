---
title: "Subversion daemon problems"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by CandelaMedia on 2007-05-18
I'm trying to install/configure subversion on Feisty Fawn

I seem to have got basic svn working and now want to progress to accessing from a Windows XP client (stop laughing!).

So my approach was nice and simple,  run up svnserve as a daemon and bobs your proverbial dad's bro.  However, my daemon fails to start!!

If I start/stop the daemon I get the following message:
*svnserve: Can't bind server socket: Address already in use*

I've had a look with netstat (although I'm not sure I'm driving that right) and can't see anthing thats using port 3690.

So all in all I'm stuck!

Any clues?

---

### Post by CandelaMedia on 2007-05-18
Some more details for you gurus out there!

The svnserve script I'm using is per the How To by Jerome Gotangco as follows:

*svnserve -d -r /usr/local/svn/svnrepo*

Oddly, if I run this from a terminal, it appears to start ok, no binding message.

However, even startiing like this I can't seem to connect in via TortoiseSVN.  I'm using the connection URL of *svn:///UBUNTU-DEV1/usr/local/svn/svnrepo* but I get the following error:

**Can't connect to host*: No connection could be made because the target machine actively refused it*

I'm sinking fast here so any assist greatfully received

---

