---
title: "Need to reinstall"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2011-04-22
I have a Dell Mininetbook.  I repartitioned and shrunk the windows partition and then installed ubuntu 10.10 to this.  I also made a linux swap file.  
 
I then installed ubuntu to this ext4 partition.  Well, it doesn't really run that well and is quite slow and not what I was looking for.  I have another netbook with the ubuntu netbook installed and it runs fine.
 
I would like to uninstall the 10.10 and then install the netbook edition.  Do I use gparted to delete the ext4 partition and then keep the swap file?  Or do I need to delete that and remake it. Or, will the new install of the netbook ubuntu use that swap file?
 
Thanks,

Dennis

---

### Post by mörgæs on 2011-04-23
If you want to reinstall, best is to remove all partitions related to the present Ubuntu installation, but I would recommend that you find the reason before changing anything.

First of all, what does the **top** command tell you?

---

