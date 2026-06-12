---
title: "pxelinux.0...error: not a valid image"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by DollaBillz217 on 2007-03-29
I am attempting to do a network install of Fedora Core 6 for a diskless workstation using the PXE boot method, a DHCP server, FTP server, and a kickstart installation.  My projected goal is to be able to issue unattended installs to computers at some remote sites I have across the country.  I have set up and confgiured my ftp and dhcp servers, as well as their config files, but everytime I go to boot the client I get the following error:

Searching for server (dhcp)...
Me: xxx.xxx.0.35, server: xxxxxx, Gateway xxx.xxx.0.1
Loading xxx.xxx.0.122:/ks/pxelinux.0  error:not a valid image
Unable to load file
<sleep>
<abort>

I have tied just about everything to fix this issue.  Can anyone PLEASE help me with this issue.  I have posted 5 different positings as linuxforumns.org and have yet to get a single reply.  I have been stuck on this for over a week and I need some help.  If there is any other information needed, please let me know.  Thanks!

:confused: $Billz:confused:

---

### Post by EmmEff on 2007-03-29
Where did you get the pxelinux.0 file from?

BTW, this is a Ubuntu forum...  you might get more topical help from [http://forums.fedoraforum.org](http://forums.fedoraforum.org).

Also, there are a number of HOWTOs out there explaining how to do this.  I just did it a week or so ago and had no problems.  I'm sure you've just missed a step or copied a wrong file somewhere.

---

### Post by DollaBillz217 on 2007-03-30
Yes I am aware of the several how-to's explaining how to do this.  I think I might have read all of them and I still am having no luck.  I have tried mimicking all of them out there with no luck.  I got my pxelinux.0 file from [www.kernels.org](www.kernels.org).  Ive downloaded three different ones.

---

