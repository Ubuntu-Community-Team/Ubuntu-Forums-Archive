---
title: "Cannot install Kubuntu Lucid (alpha 1) in VirtualBox"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nortexoid on 2010-01-02
I've set up Windows XP off a CD just fine in VirtualBox but I can't do the same with Kubuntu Lucid from an iso stored on a NTFS partition. Here's what happens.

I add a new machine with OS type "Ubuntu". I have a dynamic disk installed under IDE Primary Master and my Lucid iso as IDE Secondary Master (CD/DVD). I run the virtual machine and it boots the iso. I click "English" and then I'm presented with the Kubuntu menu. I click on "Install Kubuntu" but it just loads the live CD (i.e. option 1 to Try Kubuntu). When it finally loads the live CD I click on the "Install Kubuntu..." icon but it doesn't do anything. In Konsole when I run "ubiquity kde-ui" all I get back is "sock_file=/home/ubuntu/.kde/socket-ubuntu/kdeinit4__0".

Is this a problem with the alpha 1 Lucid iso, VirtualBox, me?

---

### Post by clhsharky on 2010-01-02
HI


Sorry I cant help but Lucid testing here
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Good luck

Sharky

---

### Post by t0p on 2010-01-02
I would suggest you look in the forums on virtualbox.org for info/advice on installing Lucid.  Also check out these forums and maybe the wiki for VirtualBox info.  Lucid is at an early stage of development, so you probably won't find a perfect HOWTO on virtualisation.  Really you should experiment with settings and document your discoveries as you may be at the sharp end of Lucid virtualisation.

---

### Post by nortexoid on 2010-01-03
Thanks for the replies. I've installed Kubuntu Karmic just fine in virtualbox so it's obviously the Lucid alpha 1 iso that is causing problems. I'll file a bug.

---

