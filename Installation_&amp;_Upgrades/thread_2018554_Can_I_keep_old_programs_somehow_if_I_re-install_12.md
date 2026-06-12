---
title: "Can I keep old programs somehow if I re-install 12.04?"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by gabmuks on 2012-07-06
Hello and good day.

So far I have been unable to get a working browser
that doesn't crash flashplayer.

Google Chrome works best. But then the updates somehow disabled
the browser. Ubuntu forums was able to get Chrome working again
but now no flashplayer.

I have an old computer that I have not updated.
Chrome still works great on that computer.

The only thing I can think of is to re-install 12.04
to try to get rid of whatever is interfering with Chrome.

Is there some way that I can save my installed programs
and video driver? (I do not really know what driver I ended up
using, but it works great.)

Thank you for your time

Best regards

Pat L.

---

### Post by oldfred on 2012-07-06
You can create a list of installed apps:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If you are bandwidth limited and installing exactly same version you can copy .debs but need the space to back them up.

Location of downloaded debs
/var/cache/apt/archives/


Not sure about video driver. I have always installed the default that system suggests for nVidia.

All your settings are in /home, it that a separate partition or are you planning on backing it up. But if you restore everything as it is, then you may just have the same issues?

---

### Post by gabmuks on 2012-07-06
Hello and thank you for replies.

Does anyone know of a site with a working download of Ubuntu 12.04?


So far I've tried two that lockup.

The last was from releases.ubuntu.com.

---

### Post by oldfred on 2012-07-06
You should be able to download from the main Ubuntu site. But many sites also mirror the ISOs. It depends on what part of the world you are in. From Ubuntu updates can be from over 200 sites and it can ping each to see which may be faster. ping does not guarantee faster download but gives some idea. But you have to change that yourself.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by gabmuks on 2012-07-06
Thank you for kind reply  Old Fred.

I had to install  11.10 CD and then update to 12.04.

It's the only sure way that I've found so far.

Any way... re-installing the 12.04 didn't eliminate the Google Chrome problem.

It just don't make any sense...

On my old 2003 computer,  I can remove and re-install Chrome,
and it works perfectly! 
But on my 2007 computer, everything works except Chrome.

---

### Post by oldfred on 2012-07-06
Start a new thread with your Chrome issues in the title and any details you have. Someone may know more about that issue.

---

### Post by gabmuks on 2012-07-07
Okay. Thanks Old Fred for kind reply.

I will close this thread and start new one


Best regards

Pat L.

---

