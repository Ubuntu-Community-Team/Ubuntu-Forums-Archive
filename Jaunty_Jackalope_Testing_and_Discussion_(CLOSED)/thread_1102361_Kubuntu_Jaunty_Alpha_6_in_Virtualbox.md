---
title: "Kubuntu Jaunty Alpha 6 in Virtualbox"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jtuchscherer on 2009-03-21
Hi there,

I have two virtual machines with Jaunty Alpha 6 set up. One runs Xubuntu with LXDE and Evolution (wanted to test the MAPI functionality). The other runs (or better tries to run) Kubuntu.

On the Xubuntu machine I was able to install the Guest Additions with this little trick where you modify the install.sh to recognize the Xserver version 1.6.0. I am very impressed with Jaunty and love it. I find myself using the Virtual machine in Fullscreen mode and not even using the host system anymore.

But the Kubuntu machine is a totally different story. I already have trouble to log in after a vanilla install. Once I am in, I make sure to upgrade everything. Then I restart and install the Guest additions. After another restart I cannot log in anymore. It starts kdm nicely with mousepointer integration and in a high resolution, but whenever I try to log in (this also applies to a failsafe log in) the machine just hangs and I cannot do anything besides a reset. 

Does anybody else have this problem with Kubuntu?

Thanks

---

### Post by jtuchscherer on 2009-03-22
Bump,

Is there nobody running Kubuntu 9.04 in Virtualbox? As I said before, the Xubuntu install is rock solid and I didn't do anything different when I installed Kubuntu. But still the later doesn't allow me log in at all.

Any information or hints are welcome.

thanks

---

### Post by Reiger on 2009-03-22
No. I run it on both of my 'physical' machines. However, lately I have noticed that when I reboot my machine sometimes X/kdm/kwin will not properly start up. However, the machine which really suffers from the problem also runs a beta Catalyst driver (fglrx) (the only thing which lets me have the nice desktop effects, but more importantly solid 2d performance without artefacts cropping up ever so often) ...

Problem description on my Catalyst machine:
(1) X/kdm starts (log on screen appears). So far so good. Only a very few times have I had a blank black screen appear there which required reboot. Consistently less than with Intrepid and previous production Catalyst driver anyways. (Probably because so little of my HD4870 is actually supported that there isn't anything to break over a driver upgrade really...)
(2) Log in -> KDM & splash screen take turns 'grabbing' the screen. In more than half the cases splash + plasma win the 'fight'. Otherwise, I just get the KDM log in background (no log on screen, mind you: just the background). Requires Ctrl+Alt+F2 & additional steps to fix.
(3) When I get to the desktop/plasma all is as rosy & sweet as it could be. It just works then. 
(4) Setting desktop effects sets me back to (2) excepting that it is KDM versus Plasma this time round...

I happen to be in a 'study at home' time-of-term so I don't reboot the laptop as often. (Only with reboot-required upgrades.) But in about 50% of all cases I do get this blank black screen. Another reboot fixes it consistently.

---

### Post by jtuchscherer on 2009-03-27
I found the problem.

By using the special routine to install the GA I created a /tmp directory as root. Later when I tried to log in X tried to write something in the tmp folder but didn't have the rights. Changing the rights on the tmp folder fixed my problem.

---

### Post by robfish on 2009-03-31
I installed Guest Additions in the normal way (with no errors) but now all I get is a terminal session.

What exactly did you do with the permissions on the /tmp folder?

---

### Post by flightmaker on 2009-04-02
I installed Jaunty as a Virtualbox VM a few days ago. To get the Guest Additions to install properly (I was getting just a terminal instead of the graphical login) I put the error message into Google, found a fix for the installer script, then it installed.

Now I have backed up and restored to my Jaunty VM, the home directories of the real machine (running Gutsy), and restored the user accounts by editing passwd, shadow and group, which works. I can now log into the VM using the restored password.

BUT, when I log out, the login screen goes black and remains black. I don't know what to do with it other than tell the VM to do an acpi shutdown, or whatever, and start again. The I get the login screen again after a restart.

So, somebody thinks it's because of the privileges to /tmp/ being wrongly set by the flawed GA installer? I'll check this tonight when I get home and see if I can get it working.

---

### Post by robfish on 2009-04-02
The fix (for me and others) can be found at....
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15512](http://forums.virtualbox.org/viewtopic.php?f=3&t=15512)

---

### Post by flightmaker on 2009-04-02
Yes, I've been there already and edited install.sh to get the GA to install.

It all works now, at least kmail and gramps do, which are the only applications I've so far tried out, apart from the blank login screen when I logout.

---

