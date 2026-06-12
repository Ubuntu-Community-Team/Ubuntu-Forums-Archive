---
title: "total noob need help loading programs i download"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by FreedomRider on 2005-09-03
where can I find clear easy instructions for loading stuff I download ie: new irc client or p2p apps

thanks

---

### Post by plb on 2005-09-03
have you looked into synaptic? its installed with ubuntu and should contain pretty much everything you would want to install

---

### Post by Crimguy on 2005-09-04
[QUOTE=FreedomRider]where can I find clear easy instructions for loading stuff I download ie: new irc client or p2p apps

thanks[/QUOTE]
 Couple things you need to do.

First, understand what type of file you're downoading, based on the file extension.  .rpm is a application package for redhat-based systems.  .deb is a package for debian based systems.  .tar.gz and tar.bz2 are archives of programs.  

Second, read the man pages (i.e. open a console and type "man ****") for dselect, apt, and tar.

Much of what you download from sites will be compressed files, either gz or bz2.  You should save the file where you wish to eventually unpack it.  I keep a "download" directory in my home directory for this.  to open the gz file type tar -zxvf *filename*. Each one of those letters (z x v and f) all are options for the tar command.  x is extract,  f means you are running tar on a file, v means the terminal should output some text to reflect whats being done, and z means the file should be run through either gzip or gunzip to extract it (it needs to be not only unzipped, but also untarred).  IIRC bzip2 files use the same command except you would substitute the z with a j (don't ask me why it's a 'J').

After  you extract it, navigate into the directory where you extracted everything, read the install.txt or readme.txt for further instructions.  Hopefully you didn't download a source tarball ;-D

---

### Post by Crimguy on 2005-09-04
One other thing:  After you do the above, you need to figure out where the actual executible binary is, usually in /usr/bin or some such place.  You can search for it using a file browser, or more quickly find it by typing 'which *applicationname*'.  THat only works if it was installed into one of your $PATH directories.  If it shows up after typing the which command, you can run it by typing it's name.  If not, you must type the full path of the binary.

---

