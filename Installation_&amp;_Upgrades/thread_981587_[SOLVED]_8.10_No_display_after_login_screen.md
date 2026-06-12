---
title: "[SOLVED] 8.10 No display after login screen"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by emackey3k on 2008-11-13
Hello,

I had upgraded to 8.10 from 8.04 and all worked fine.  But since I had always upgraded from all the way back from Edgy without ever doing a fresh install I thought it was time.  I used a live cd and the installation went fine, no errors.  When I boot up I can get to the login screen fine but after I login all I get is either a black screen or a brown screen.  I am able to get to the failsafe terminal.

Does anyone know if I can edit the xorg.conf  file or something to allow me to boot?

---

### Post by emackey3k on 2008-11-13
Oh, forgot I have a dell dimension 2400 with integrated graphics and 2 gigs of ram.

---

### Post by emackey3k on 2008-11-13
I found the answer by looking around the forums some more. 

In the fail safe terminal I uninstalled compiz and it booted fine.  

 Originally Posted by jerrylamos  View Post
Any number of us are having problems with 8.10 compiz. My thinkpad gets a black or tan screen instead of a desktop. The workaround in Launchpad Bug #259385 is:

boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If later on you want to try compiz you can install it with Synaptic. As of today compiz still freezes my pc. The "official" fix is blacklisting some graphics hardware so that compiz won't start.

Jerry

p.s. might help if you listed your hardware

---

### Post by ddweerasiri on 2008-11-13
My problem is similar. But I completely format the hard drive and had a fresh install.
Installation was successfully completed.
I choose the mount path as "/".
When I startup the machine after login screen appears and after I enter the user name and the password system automatically freezes. Keyboard doesn't respond. But mouse responds.
I tried by changing the session to failsafe GNOME to failsafeGNOME but the result was the same.
Please help me on this case.

---

### Post by emackey3k on 2008-11-14
I may not be the best person to help you.  Can you get to the failsafe terminal?  If you can get there does it recognize the keyboard then?

---

### Post by wmslayton on 2008-11-27
Those sudo commands solved my problems with white screen after 8.10 installation on 2.0 Ghz HP Pavilion 504n. Although the term wasn't "rescue", it was obvious which to use. Works perfectly now. Thanks!

---

### Post by AndrewTheArt on 2008-12-09
I can confirm the steps above work -- 

Get to the log-in screen, select "Session", select "Failsafe Terminal"

run


sudo apt-get remove compiz
sudo apt-get remove compiz-core


reboot

---

### Post by knightmuzic on 2008-12-14
I have the same problem as the original thread poster, except I don't have compiz installed on my computer. My comp is a Compaq Presario 600 series with an NVIDIA graphics card.

I had upgraded my OS via apt-get.

---

### Post by rayburn on 2008-12-27
Thank you so much for posting this solution, I too was struggling with a Dell Dimension 2400 install until I came across this thread.

Removing compiz/compiz-core as detailed above worked for me.

:P

---

### Post by adrian-g on 2008-12-27
This also worked for me (with a Dell Optiplex GX260), although the term at the login screen is a bit different than the answer emackey3k states.

Thank you!

---

