---
title: "Cannot update"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by JBauer5 on 2010-10-26
I'm having trouble updating.  Using the update manager fails and I see the message:

dpkg: parse error, in file '/var/lib/dpkg/available' near line 23288 package libbonoboui2-common':
 'Conflicts' field, reference to 'libbonobous2-0': version contains ' '

I've tried 
sudo dpkg --configure -a

and

sudo dpkg --remove --force-remove-reinstreq libbonoboui2-common

and

sudo dpkg --remove --force-remove-reinstreq libbonobous2-0

All give the same error message.  Any ideas what I can do?

---

### Post by irv on 2010-10-26
Hey, check out this post:
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")
I was having trouble updating also and I did it this way.

---

