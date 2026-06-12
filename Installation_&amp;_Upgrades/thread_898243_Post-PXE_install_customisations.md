---
title: "Post-PXE install customisations"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Goobie81 on 2008-08-23
Hey guys - I've got pxelinux setup with netboot, an extracted copy of the ubuntu server CD which the netboot image mounts over NFS and installs with settings from a kickstart file loaded via http (boot loader, auth, packages, etc)

I'm trying to figure out how to change my cd 'image' that  i install from to create a custom installation.

I'm not trying to create a Live boot CD, or alter the package/repo lists etc, I just want be able to pre-load configs & settings etc onto machines

eg. Populate a bunch of scripts into /usr/local/sbin
    Edit files in /etc/skel (profiles etc)
    Overwrite the postfix main.cf with another one
    SSH keys, LDAP authentication settings
       
etc etc

My current solution is to use a script with %post-install to retrieve a tar file which does all this, but i was looking for something more elegant. 

Does any know how i can do this? Can i setup Ubuntu server on a random machine, configure it to exactly how i want and then somehow image it?

---

