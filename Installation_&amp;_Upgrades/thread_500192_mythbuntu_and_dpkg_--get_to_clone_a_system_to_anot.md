---
title: "mythbuntu and dpkg --get to clone a system to another one?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by bone2006 on 2007-07-13
If I took a PC and put a fresh copy of ubuntu 7.04 and the installed all my applications that I wanted.   Then I ran this command:

dpkg --get-selections > installed-software.log

Saved the file somewhere else.

reformatted my computer

Grabbed a copy of mythbuntu alpha 2, which is based off of 7.10  and installed it, then took the file and ran this command:

sudo dpkg --set-selections < installed-software.log && apt-get dselect-upgrade 

Would this workout alright?  meaning if I wanted to bring over all the things I like about ubuntu with my system with all the applications I have installed over to a mythtv box would this work?

Where I'm getting at is that I have one computer with ubuntu 7.04 in one room and I have a PVR with mythtv in my livingroom, yet I want all my applications from my ubuntu 7.04 to be put on my mythtv system, so I'd like to clone it over.  

Just want to see if this would work.  I probably wouldn't do this until ubuntu 7.10 final and mythbuntu 7.10 final, but just wanted some feedback.

Thanks in advance

---

### Post by Redlazer on 2008-03-25
I could be wrong, but I cant see any reason why it wouldnt work.

I just did it to recover from a recent format, and it (so far) has worked like a charm.

Good luck!

-Fred

---

