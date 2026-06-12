---
title: "Uninstalling SQLite 3.5.9"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by alj on 2008-11-10
I've just installed Xubuntu on an a very old machine to run some python scripts through the day. However, SQLite 3.5.9 has a known issue with division that wasn't in the previous versions. It's completely screwed my database up. 

I'm new to linux but I have tried to download and install SQLite 3.6.4. The compilation and installation went ok, but I still have 3.5.9 there when I look at it through SQLite Manager. 

I used the Synaptic Package Manager to remove 3.5.9 but I think that there are a load of libsqlite files still there with lots of dependancies. 

(Sorry .. but things were so much easier with XP!)

ALJ

---

### Post by vcii on 2010-06-10
I realize this response is a little late, but to future googlers--
I solved this problem by downloading the source amalgamation & configure tar ball ([http://www.sqlite.org/download.html](http://www.sqlite.org/download.html)).  I ran `./configure` with the --prefix set to the root of the existing installation, probably /usr for Mac OS X users and /usr/local for Linux users, and simply ran `sudo make uninstall`.  (For less standard installations you can use the configure options like bindir and libexecdir to point to where the installed headers, library, and executable is, though if you didn't do it or don't remember what you did, good luck!).  
Once these are removed you can re-run configure to set the new installation directories, then make, ..., make install.

---

### Post by hppillai on 2011-07-30
> **vcii said:**
> I realize this response is a little late, but to future googlers--
I solved this problem by downloading the source amalgamation & configure tar ball ([http://www.sqlite.org/download.html](http://www.sqlite.org/download.html)).  I ran `./configure` with the --prefix set to the root of the existing installation, probably /usr for Mac OS X users and /usr/local for Linux users, and simply ran `sudo make uninstall`.  (For less standard installations you can use the configure options like bindir and libexecdir to point to where the installed headers, library, and executable is, though if you didn't do it or don't remember what you did, good luck!).  
Once these are removed you can re-run configure to set the new installation directories, then make, ..., make install.

Thanks for the comments. I was searching for uninstalling and re-installing sqlite3. worked fine

HPP

---

