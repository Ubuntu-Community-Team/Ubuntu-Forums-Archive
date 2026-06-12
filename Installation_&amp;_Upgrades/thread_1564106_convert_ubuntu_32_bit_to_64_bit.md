---
title: "convert ubuntu 32 bit to 64 bit"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2010-08-30
Is it possible to convert ubuntu 32 bit to 64 bit on an existing installation.

---

### Post by presence1960 on 2010-08-30
> **jamesbon said:**
> Is it possible to convert ubuntu 32 bit to 64 bit on an existing installation.

no. You must do a clean install.

---

### Post by TNT1 on 2010-08-30
> **presence1960 said:**
> no. You must do a clean install.
dammit. Really?

---

### Post by howefield on 2010-08-30
> **TNT1 said:**
> Really?

Really.

---

### Post by TNT1 on 2010-08-30
> **howefield said:**
> Really.


Great. I'll wait till April next year then.

---

### Post by dino99 on 2010-08-30
why not pae kernel instead ? that way you can fully use your ram

---

### Post by jamesbon on 2010-08-30
Please tell some thing that I understand.

---

### Post by dino99 on 2010-08-30
> **jamesbon said:**
> Please tell some thing that I understand.

what are you not understanding ? may be you need to glance at synaptic kernel packages first

---

### Post by howefield on 2010-08-30
> **jamesbon said:**
> Please tell some thing that I understand.

Please tell us something that you don't understand ?

---

### Post by jamesbon on 2010-08-31
What I understand till now is that I need to format every thing and do a clean install.
If that is the case then I want to keep a copy of the existing 32 bitOS on my machine.
So how do I go about installing in an empty partition keeping one already existing.
I asked this question here and after one reply I am waiting for what more to be done.
[http://ubuntuforums.org/showthread.php?t=1564113](http://ubuntuforums.org/showthread.php?t=1564113)
Can any one suggest any thing on above thread?

In past I have done this with Fedora and OpenSuse etc but I am not clear for many things
1)Partitioning schema how to find out which partitions are alive in existing Ubuntu installation
2)Grub entries since I am not clear with UUID part.

---

### Post by ilovelinux33467 on 2010-08-31
you can make a backup of your home folder if you do decide to reinstall to 64 bit ubuntu so you can copy all your documents back to your new installation. I don't think the same thing go's for apps just documents

---

### Post by rawlins02 on 2010-08-31
I'm also considering fresh install of 64-bit, just a few weeks after installing 32-bit Lucid.  Got a lot of packages installed. Curious how one could use Synaptic's "Generate Package Download Script" to get proper 64-bit packages of everything I now have re-installed.  I envision one command (or click) and presto!

---

### Post by oldfred on 2010-08-31
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

You may also want to and then be sure to include in your backup of home, I run this as part of my backup so I have the most current versions in my backups:
dpkg --get-selections > ~/ubuntu-files
cp /etc/apt/sources.list ~/sources.list.backup

---

### Post by rawlins02 on 2010-08-31
Very handy oldfred.  But would there be inconsistencies if one saves these package lists from a 32-bit system and then installs those packages to a fresh install of 64-bit?  In other words, are 32-bit versions different from 64-bit versions, and would 32-bit packages get installed on the 64-bit OS?  Or perhaps Ubuntu and Synaptic have that all figured out.

---

### Post by oldfred on 2010-08-31
The list it creates are just the names. It is not the versions. So if reinstalling to a new system it will install the latest updated version and if you are on a 64 bit system it will install the 64 bit version. Only if there is not a program (obsoleted) will it not install.

If you want a list with versions 

List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

---

### Post by PaulReaver on 2010-08-31
> **TNT1 said:**
> Great. I'll wait till April next year then.

wtf?  Have I missed something,  are they not releasing meerkat (10.10) in october?

---

### Post by tommcd on 2010-08-31
> **PaulReaver said:**
> wtf?  Have I missed something,  are they not releasing meerkat (10.10) in october?
Yes, they will be releasing Maverick 10.10 in October:
[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

---

### Post by howefield on 2010-09-02
> **PaulReaver said:**
> wtf?  Have I missed something,  are they not releasing meerkat (10.10) in october?

He might just like the name... or simply not want maverick.

[http://www.markshuttleworth.com/archives/478](http://www.markshuttleworth.com/archives/478)

Maverick Meerkat due 10th October 2010
Natty Narwhal due 28th April 2011

---

### Post by TNT1 on 2010-09-02
> **PaulReaver said:**
> wtf?  Have I missed something,  are they not releasing meerkat (10.10) in october?

Yes, they are, but I'm a confirmed LTS dude...

---

### Post by TNT1 on 2010-09-02
> **howefield said:**
> or simply not want maverick.

[]("http://www.markshuttleworth.com/archives/478")1

Exactly. As previously noted somewhere on this forum, Meerkats scare the cr@p out of me. Which is weird, cause we used to live in the bush, and had a cobra at the bottom of the tree that my tree-house was in, and I saw it kill a meerkat from a sort of birds eye position...

---

### Post by howefield on 2010-09-02
> **TNT1 said:**
> Yes, they are, but I'm a confirmed LTS dude...

Then you won't want Natty either...

---

### Post by TNT1 on 2010-09-02
> **howefield said:**
> Then you won't want Natty either...

Yeah, but I'll put it on a test machine at least....

---

### Post by jamesbon on 2010-09-03
Here is what I did 
I had an empty partition on my machine worth 45 GB so I installed the 64 bit Ubuntu 10.04 so that I can try things in it.I also have 32 bit installed so that if some thing goes wrong I can always revert back.
Consider having such a feature in next releases of Ubuntu.

---

