---
title: "Attempting to install Ubuntu in VirtualBox..."
date: 2013-09-22
forum: Installation &amp; Upgrades
---

### Post by EvilJam on 2013-09-22
I get this message: "This computer currently has no detected operating system... " and offers two options, "Erase Disk" or "Something Else." 
If I was running Windows I would simply erase disk, but I run OS X.  And, the "something else" option, which essentially requires a disk partition gives me this... "no root file system is defined." 
WTH ?

---

### Post by santosh83 on 2013-09-22
> **EvilJam said:**
> I get this message: "This computer currently has no detected operating system... " and offers two options, "Erase Disk" or "Something Else." 
If I was running Windows I would simply erase disk, but I run OS X.  And, the "something else" option, which essentially requires a disk partition gives me this... "no root file system is defined." 
WTH ?

Your title seems to indicate you're installing Ubuntu within VirtualBox as a guest OS? Is that right? If so, then unless you're using some paritioning strategy within the virtual harddisk image, your Ubuntu will be installed into an empty new virtual harddisk image file. In that case you can simply tell it to use the whole disk. Unless we know whether you're trying to install Ubuntu within a VM or on bare hardware and in the former case, whether you're using an existing virtual harddisk or creating a new one, we can't say anything further.

---

### Post by EvilJam on 2013-09-22
I have no idea.  Just following VirtualBox instructions [from here...  ]("http://osxdaily.com/2012/03/27/install-run-ubuntu-linux-virtualbox/")There is no box to create a User Name, so... guess I'm a Guest.  Expected VirtualBox to write the config with the info provided during install, but... alas... get that error message.  Will continue to continue...  Thanks!

---

### Post by mastablasta on 2013-09-23
folow these instead: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

create the virtual disk and install to it.

---

