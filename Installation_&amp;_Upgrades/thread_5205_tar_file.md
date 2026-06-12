---
title: "tar file"
date: 2004-11-16
forum: Installation &amp; Upgrades
---

### Post by trivialpackets on 2004-11-16
Hey all, things are going smoothly thus far, but I have one tarball program for my email First Class client for school for linux.  Can anyone give me what commands I need to throw at it to open it up and install.

tried tar -zxvf fcc......

that just unzipped it basically into folders, so that didn't resolve my issue.  Let me know all.

---

### Post by dataw0lf on 2004-11-16
Perhaps I'm not understanding you correctly.... you tar -zxvf <program>, and it gunzipped and untarred it into a directory? That's what that command does.  If you wish to install it, I suggest cding into it's directory, reading the README, and following the instructions detailed therein.  
dataw0lf

---

### Post by trivialpackets on 2004-11-16
I don't believe there was a read me file there.  i checked out the directories that were created, I'm not @ home now, but I don't believe there was one.  I'll take a look later and comment back at you.  Thanks.

---

### Post by madsen on 2004-12-08
I've got a .deb and a .rpm of the First Class Client (Yeah, my university also forces that crap on their users!).
It's at: [http://lillesvin.net/files/](http://lillesvin.net/files/)

When you've got the .deb, simply do:
  sudo dpkg -i fcc_7.1-17_i386.deb
It'll then install itself in the /opt dir, so it'll be easiest to make a symlink from /usr/bin to it, with:
  sudo ln -s /opt/firstclass/fcc /usr/bin/
Then simply run it with 'fcc'.

---

