---
title: "Ubuntu server on virtual box does not boot"
date: 2017-09-06
forum: Installation &amp; Upgrades
---

### Post by asssamm on 2017-09-06
Hi I have tried to increase the volume of the hard disk on my ubuntu server which is installed on my virtualbox. Now I cannot boot it lost the boot sector.
I have tried to repair it with Boot Repair Disk, here is the report. [http://paste.ubuntu.com/25478011/](http://paste.ubuntu.com/25478011/)
Any idea how to recover this?

---

### Post by SeijiSensei on 2017-09-06
How hard would it be to spin up another instance of Server and copy over any customizations you have made?  An hour or two maybe?  That's going to be more efficient than trying to repair your current instance.

After you have done this, make a snapshot backup of the virtual machine and store it in a safe place.  Then you will always have a working image to use in the case of disasters like this.  Nightly backups, preferably to another physical machine rather than the VM host, are a must if you're running a server as well.  You should expect your server to crash at any time.  I've run a lot of servers, and I learned that rule the hard way.

---

### Post by asssamm on 2017-09-06
thanks for your quick reply SeijiSensei.
I thought about that, however,  there are so much customisation and old legacy data on this machine which I need to have access.
Does this [COLOR=#000000]Boot Repair Disk report give any indication of what the problem is?[/COLOR]

---

