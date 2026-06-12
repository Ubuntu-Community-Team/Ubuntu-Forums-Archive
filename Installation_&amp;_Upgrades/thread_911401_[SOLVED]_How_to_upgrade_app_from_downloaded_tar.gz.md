---
title: "[SOLVED] How to upgrade app from downloaded tar.gz"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by timvn on 2008-09-05
Hi

How do I upgrade to a new version of an application downloaded as a tar archive and installed manually using configure / make / install etc?  

I installed xmlcopyeditor-1.2.0.1 this way and now I need to replace it with xmlcopyeditor-1.2.0.2.  I'm a bit lost -- while the app icon shows in my Applications menu I can't find it using Applications > Add/remove, neither is it in Synaptic (nor Aptitude so far as I can see), and if I try  apt-get remove xmlcopyeditor-1.2.0.1, it doesn't find the application.

Do I need to remove it in the first place or can I upgrade it in one step after downloading the new versions tar archive (only available as .tar.gz). How do I go about it?

Thanks,
Tim

---

### Post by father time on 2008-09-05
Message Deleted.

---

### Post by timvn on 2008-09-05
Thanks Father Time.  Unfortunately that post only deals with retaining preferences, which I'm not concerned about.  I know the developer would be helpful because he has been with other things, but I came to the Ubuntu forum  because this was a general Linux question I hoped could be answered here.

I've found that to remove the app I could just use make uninstall as I still had the original installation directory.  So I'll just do a fresh install of the new version -- just wondered whether there was a better way...

---

### Post by zdude on 2008-09-05
Instead of make install, try using sudo checkinstall (it is installed via Synaptic) it will create a debian package file and it shows up in synaptic. I use it all the time. Only bad thing is depending how it's versioned, Ubuntu will notify you that it needs upgrading.

---

### Post by father time on 2008-09-05
Message Deleted.

---

