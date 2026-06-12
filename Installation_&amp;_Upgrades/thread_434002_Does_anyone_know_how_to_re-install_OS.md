---
title: "Does anyone know how to re-install OS?"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2007-05-05
Does anyone know how to re-install os without overwriting all the settings? I cant login no matter what and have tried all of the suggestions I have been given to no avail. Surely Ubunto 7.04 has some kind of feature to re-install the os just in case.If so please let me know how to do this. Thanks in advance.

---

### Post by kidders on 2007-05-06
Hi there,

Operating systems don't tend to provide features like this ... after all, the most likely cause of your problem is a bad application setting that has crept in somehow, so reinstalling your OS *and* keeping the faulty setting won't really change anything.

Why can't you log in?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by dontgetshocked on 2007-05-06
Well, I have to disagree, even windows allow you to re-install the os without affecting the data and also Xandros for one allow you to re-install without losing your data. Sometimes  a setting or app simply is not there and needs to be re-installed and this fixes this. I understand about some settings not being overwritten, however this is not always the case. Thanks anyway though...

---

### Post by jml on 2007-05-06
A little more detail would be helpful.  For example, what version of Ubuntu are you using, has the system worked before, does your computer get to the login screen?  Can you type in your user name and password?  Does it hang before you get to that step?  If you supply a bit more information, someone here is likely to be able to help you.

If you still have the live/install cd, can you boot from it?

Joe

---

### Post by dontgetshocked on 2007-05-06
OS is Feisty 7.04 and it gets past the splash screen and gets to where the login screen should be and the mouse cursor just keeps on spinning and that's as far as it gets.The system worked before, well, I had noticed that when I logged out I would get no screen and would have reset. I had Beryl running at the time I logged out and just before that I unchecked the autologin feature and couldnt get back in. i unistalled Beryl via command line but that didnt help.I now have to use this command to get to the desktop.
sudo /etc/init.d/gdm stop
startx

This gets me my desktop but not all is well. If I choose System/Administration/Login Menu I get the message 
GDM (Gnome Dislpay Manager) is not running
You might in fact be using a different display manager, such as KDM (KDE Display Manager) or xdm. If you still wish to use this feature, either start GDM yourself or ask your system administrator to start GDM.

I still have the live cd and it boots fine.

I also tried using the rescue feature on boot with no success.

---

### Post by hessiess on 2007-05-06
boot the live cd and back up your stuff to a memery stick, external hd, or cd if you can boot it into ram. reinstall os.

---

