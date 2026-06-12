---
title: "How to change sources.list in a mini.iso image?"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by servant74 on 2012-06-26
I would like to set up a apt-cache server, but would like to change mini.iso image to point to my local apt-cache server, which then points 'out'.

I need this because I have a slow internet connection that is shared with others...

Suggestions?  Thanks

---

### Post by servant74 on 2012-08-14
I too live on a low speed link.

You should be able to do a loopback mount of 'mini.iso' then use 'vi' to update it appropriately, close it, then reboot the ISO.

[http://askubuntu.com/questions/46646/how-to-edit-iso-images-including-bootable-isos](http://askubuntu.com/questions/46646/how-to-edit-iso-images-including-bootable-isos) says to use ISO Master, but I haven't.

[http://www.atoztoa.com/2009/11/editing-iso-image-in-ubuntu.html](http://www.atoztoa.com/2009/11/editing-iso-image-in-ubuntu.html) says the same, but with more detail.

---

