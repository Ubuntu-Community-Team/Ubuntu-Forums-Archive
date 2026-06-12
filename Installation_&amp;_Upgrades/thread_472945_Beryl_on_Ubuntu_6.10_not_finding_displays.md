---
title: "Beryl on Ubuntu 6.10 not finding displays"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by haden9 on 2007-06-13
Good afternoon guys, I recently installed Xgl and Beryl on my system which is a m5550, with an ATI Mobility Radeon x1400 with native resolution 1280x800. The situation is everytime I run the beryl-manager command through the terminal I get 

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

And some window options dissapear and basically I cant close open windows or move them at all. Any ideas, could somebody help me plz :popcorn:

---

### Post by dannyboy79 on 2007-06-13
there is a statement at the way bottom on how to fix this, the link:
[http://www.pricechild.co.uk/?feed=rss2&p=37](http://www.pricechild.co.uk/?feed=rss2&p=37)
however, thru internet explorer, the link doesn't work, the xml code doesn't get converted to a webpage so it's hard to read. it may because I am at work though, maybe my work blocks some websites from coming thru???

here's a bug report that has you problem mentioned at the bottom as well: [https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394](https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394)

gogle is your friend when trying to solve stuff. :-)

---

### Post by haden9 on 2007-06-15
I tried doing a LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl but all I got was my screen to reset and to get back to the session manager window. I am able to run beryl, although all i get are windows with blank spaces and completely unusable and also slow graphics. Is there something I am doing wrong, thanks for helping me out dannyboy, let me know if you need additional info from me.

---

### Post by haden9 on 2007-06-15
Its working now Dannyboy thanks!!! I had to use these ATI drivers ati-driver-installer-8.35.5-x86.x86_64.run by the way and reconfigure everything from scratch using the links below lol. 



[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#IMPORTANT_PLEASE_READ_BEFORE_BEGINNING](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#IMPORTANT_PLEASE_READ_BEFORE_BEGINNING)

and

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

Its looks freaking awesome!!!! THx again!!!!:popcorn:

---

### Post by dannyboy79 on 2007-06-15
right on, I was going to ask if you were using the proprietary drivers!! I have a guy I was trying to help get his ATI card and beryl working but since I have Nvidia and I use compiz, I couldn't end up getting it working for him, would you do me a huge favor and drop him a line thru PM and pioint out anything that was incorrect in the guides or maybe some tips he should look out for? his screenname was xboxmodder3 or somehting very similar. I know for sure it start with xboxmod..... He's in my gaim buddy list so if you're willing to try to help him, I'll post back with the screenname after I get home around 4:30 central time.,

---

