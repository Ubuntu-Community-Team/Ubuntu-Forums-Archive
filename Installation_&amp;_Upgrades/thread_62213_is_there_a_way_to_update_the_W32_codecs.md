---
title: "is there a way to update the W32 codecs?"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by occy8 on 2005-09-03
I'm getting problem on some streams. Both in Ubuntu and Windows.
In windows I updated my codecs but the W32 codecs have not been updated for a while. 
Can I add codecs myself, how does this work? I noticed a few people having problems with streams lately.

---

### Post by bjweeks on 2005-09-03
Is the codecs on list? [http://www.linuxdevices.com/news/NS9819663983.html](http://www.linuxdevices.com/news/NS9819663983.html)

---

### Post by occy8 on 2005-09-04
no one is a mms and one is a asx file

I found this for the mms 
[http://geocities.com/majormms/](http://geocities.com/majormms/)

but when I ./configure
it stops here

checking for ptrdiff_t... yes
checking for xine-config... no
checking for XINE version >= 0.9.5... no
*** The xine-config script installed by XINE could not be found
*** If XINE was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XINE_CONFIG environment variable to the
*** full path to xine-config.
configure: error: *** You should install xine first ***

I have totem-xine installed
what to do?

---

### Post by doclivingston on 2005-09-04
You'll need t install the package "libxine-dev". If ./configure complains that it can't find something, check to see if the development package installed.

---

