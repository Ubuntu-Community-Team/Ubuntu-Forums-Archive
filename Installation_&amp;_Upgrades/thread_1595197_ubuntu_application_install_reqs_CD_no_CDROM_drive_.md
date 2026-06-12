---
title: "ubuntu application install reqs CD no CDROM drive possible?"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by neilevan814 on 2010-10-13
Hi,

I have been trying to figure out how to get the ubuntu installation process to read from their CDR to complete an install.  I do not have a cd drive in this system.

I have tried to do a sudo mount -t iso9660 -o loop /my/iso /media/ISO or /media/cdrom or /media.cdrom0

none of these options are recognized by the ubuntu installer.

Is there a way?

---

### Post by _duncan_ on 2010-10-13
[[COLOR="Blue"]_This_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1549847") link might help you. I was able to get it to work with Lucid 10.04, but encountered problems with the new Maverick 10.10.

Another possibility is to create a bootable ubuntu USB stick. I have no experience with this process though.

---

### Post by neilevan814 on 2010-10-13
No, that won't help either..but its good info for something else.  

What is happening is say you want to install an additional application, my instance..flashplugin-nonfree.  I start synaptic start the install and then I get prompted to insert the ubuntu install disc.  Can't do that.

Is there away to have that install look for the disc somewhere else.

---

