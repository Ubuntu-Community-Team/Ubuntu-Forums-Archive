---
title: "Installing Oracle 10g AS (10.1.3) on Ubuntu"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by john_dalke@cwb.ca on 2010-08-19
I am posting this as it may be useful to other Ubuntu users.

I am a new user to Ubuntu an I recently tried to install Oracle AS 10g onto Ubuntu 10.04 desktop. I downloaded the Oracle AS 10g software from the Oracle site, unzipped, and attempted to run the ./runInstaller -igonoreSysPrereqs. I attempted this several times and every time I received the following message: 

**[COLOR=Red]"Error in writing to directory /tmp/OraInstall2010-08-18_01-35-53PM. Please ensure that this directory is writable"[/COLOR]**

This lead me to believe there were permission issues with the oracle user account which was misleading. After a day of searching the internet I found the following suggestion which lead me to the TRUE problem: 

"[COLOR=Red]This message is often misleading, there are many other reasons. Run OUI with the debug option to get clearer informations:

./runInstaller -ignoreSysPrereqs -debug[/COLOR] 
([http://kr.forums.oracle.com/forums/thread.jspa?threadID=647315](http://kr.forums.oracle.com/forums/thread.jspa?threadID=647315))

I ran this an it lead me to the true problem which was ZIP files were missing required for the install. This particular software is downloaded in 5 files which need to be unzipped into one install directory. Once I place file #2 into the install directory every thing work properly.

Bottom line - anytime you try and install an Oracle product use the '-debug' option so you get the true error and don't waste time going down the WRONG path.

---

### Post by ectospasm on 2010-08-19
This is good to know.  I am about to attempt an 11g install on my Lucid workstation at home.  I'll comment soon on how it goes!

---

