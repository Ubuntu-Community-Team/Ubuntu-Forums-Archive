---
title: "Problem with graphics display after full install"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by gbswales on 2011-08-02
I ran live CD 11.04 on my main computer and everything worked fine - it recognised my dual display and everything. (though it automatically started up the standard desktop rather than the new one with the sidebar (which is ok with me)  However when I installed ( alongside windows using the same CD and running from the live install desktop) everything seemed to go fine until after the reboot - and it now shows the new desktop on one monitor only.  I went in to manage the displays thinking one may have been disabled BUT it is only seeing one of the two identical displays.

Is there a way of switching to the original desktop - I have looked through the settings panel but cant see an obvious way to do this. To me it is crazy that the live CD worked fine but the full install did not.  I cant even see where it has installed as windows disk manager is not showing me any partitions.  Before the install I deleted the partition on the drive I wanted it to install to but the install did not offer me a choice of disks and installed somewhere but didnt bring up gparted or anything like it - I hope it has installed on this disk but I dont know if it did or not.  (this is a full install not a virtual one like wubi) 

I was really hopeful from seeing the live CD that this was at last a version which would not require me ever to use command line stuff but I now have a version installed that doesnt work and no idea (short of reverting to a windows back up) how to restore everything as it was before I installed it.

Why oh why is no Ubuntu install straightforward.

Can anyone help me to sort out reverting to the old desktop through the GUI and getting it to recognise both my displays

---

### Post by bcbc on 2011-08-02
I can't help out with the multiple displays, but if you want the old desktop, at the logon screen click on your user name and before entering your password, look on the bottom of the screen and change the session from *Ubuntu* to *Ubuntu classic*

---

### Post by steve11911 on 2011-08-04
The real power and value of the linux operating system is found there where the little cursor blinks.Takes some  getting  used to and you'll have to think while paying attention to details but the learning curves are well worth traversing... IMHO.

That said, and with only a little regret, I'll ask you to open a terminal and post the results from:

lspci

and then the results of:

xrandr -q

====

From the ubuntu package manager (lots of really cool stuff there) you can grab :
 grandr
manages multiple screens ( gui)
===

For partition related tasks I prefer to boot from a gparted live cd...you can get one here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

(be careful...)

---

