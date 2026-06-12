---
title: "Uninstall Firefox 3"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by chrisch on 2008-02-08
I installed Firefox 3 Beta here 
[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)
and I want to revert back to 2.X.  Version 3 has a lot of nice features but I run into a lot of browser compatibility issues with it.  I don't want to have to reinstall the ubuntu-desktop, and I have tried replacing the Firefox folder with that from 2.x tar ball but it still says I am running version 3.  Any thoughts?

---

### Post by orange2k on 2008-02-08
I used the same how-to and have the same problem...
However, now I use Swiftweasel which works perfectly...:)
[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

---

### Post by zvacet on 2008-02-08
Look in folder that you created by untaring package and there should be **install** an **read me** files.In one of them you will (hopefully) find how to unistall package.

---

### Post by corevette on 2008-02-08
last resort you can just download it here
[http://www.mozilla.com/en-US/firefox/?from=getfirefox](http://www.mozilla.com/en-US/firefox/?from=getfirefox)
if you don't care if it's in the repositories or not

---

### Post by chrisch on 2008-02-08
I installed Swiftweasel and it does work fine.  Thanks.

I never could find a way to roll back Firefox.

---

### Post by confused57 on 2008-02-08
> **chrisch said:**
> I installed Swiftweasel and it does work fine.  Thanks.

I never could find a way to roll back Firefox.
Maybe you could use Ubuntuzilla to install the latest stable version of firefox:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by chrisch on 2008-02-09
I have never heard of Ubuntuzilla, but it worked fine.  I had to change my launcher from firefox to firefox.ubuntu.

Thanks for all the help.

---

### Post by ericesque on 2008-02-14
I used the same instructions and rolling back is still giving me a headache.  I don't understand the whole dpkg-divert stuff that he uses in the tutorial.  I guess this is what I get when I use commands I don't recognize!  

I really want to get 3 beta 3 installed the way it's supposed to be... I guess we'll see if I can pull that off.

---

### Post by evil_cat on 2008-02-16
> **ericesque said:**
> I used the same instructions and rolling back is still giving me a headache.  I don't understand the whole dpkg-divert stuff that he uses in the tutorial.  I guess this is what I get when I use commands I don't recognize!  

I really want to get 3 beta 3 installed the way it's supposed to be... I guess we'll see if I can pull that off.


I totally agree with you but I install swiftweasel and everything works fine for me now.
In fact I wanted to install Firefox 3 because it is believe to have a better performance, up to now Swiftweasel is perfect

---

### Post by zvacet on 2008-02-16
You have Firefox 3 in synaptic if you still want to try it.

---

### Post by evil_cat on 2008-02-17
> **chrisch said:**
> I installed Firefox 3 Beta here 
[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)
and I want to revert back to 2.X.  Version 3 has a lot of nice features but I run into a lot of browser compatibility issues with it.  I don't want to have to reinstall the ubuntu-desktop, and I have tried replacing the Firefox folder with that from 2.x tar ball but it still says I am running version 3.  Any thoughts?


According Ubuntu Geek step:

--------------
START

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

END
--------------

When you type 'firefox' in terminal --> FIREFOX 3 is launched
But when you type 'firefox.ubuntu' --> FIREFOX 2 is launched

The step below shows how I managed to get things right

**Step1:**
OPEN terminal
[B]
Step2:[/B]
TYPE gksudo nautilus
[B]
Step3:[/B]
This step is a bit tricky so please follow
OPEN usr/bin
FIND firefox and firefox.ubuntu files
RENAME firefox to firefox.out
RENAME firefox.ubuntu to firefox
RENAME firefox.out to firefox.ubuntu

It works out for me, if the problem persists DOWNLOAD swiftweasel

---

### Post by zvacet on 2008-02-17
If you install it from synaptic it will show as another app,meaning you wll have two buttons.It will not upgrade your existing firefox.

---

