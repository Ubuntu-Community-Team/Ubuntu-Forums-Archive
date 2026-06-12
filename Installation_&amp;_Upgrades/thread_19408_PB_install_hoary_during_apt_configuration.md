---
title: "PB install hoary during apt configuration"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by vladimir on 2005-03-11
I'm trying to install the hoary preview but the install freezes during apt installation, with the message 
> Setting up primary installation repository
using CD-ROM mount point /cdrom/
Indentifying [71ec etc.]
Found 2 package indexes, 0 source indexing and 1 signatures
Please provide a name for this Disc such as Debian 2.1r1 Disk 1 :
Does that ring a bell for someone ?
Any idea where I should look first ? (it's not a CD burning pb, I md5sumed the iso that was actually burned on the CD and it"s ok)

Thanks 
Vlad

---

### Post by ganesh on 2005-03-18
I am also having the same problem. I tried to burn CD again with slower speed (4x), but still the same problem.

Any updates?

Thanks for the help.

---

### Post by ganesh on 2005-03-18
Looks like I found the work around.

I took the Debian installation approach :D. At the installation boot prompt, I chose 'server' to install bare minimum packages. My installation was successful. When I got the command prompt, I just did following:

# sudo aptitude update
# sudo aptitude install ubuntu-desktop

I am hoping that 'ubuntu-desktop' with its dependencies installed every thing that installation was suppose to install.

I still do not know why regular install failed on apt config  :sad:

---

