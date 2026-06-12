---
title: "No gui login after upgrading 17.10 to 18.04"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by Ron_Zoscak on 2018-04-26
After upgrading to 18.04 from 17.10, there is no gui login screen.  The purple Ubuntu screen appears briefly, then a console screen with what looks like the results from fsck, then a console login prompt.  If I login and then run startx I get my normal desktop, but with a window that asks for my password to unlock keyring.  Auto-login is OFF, logging in as a user, not root.

Running "sudo cat /etc/X11/default-display-manager" in a terminal window outputs "/usr/sbin/gdm3".  

"About" screen:
Ubuntu 18.04 LTS
Memory 7.7 GiB
Processor Intel® Core™2 Quad CPU Q8200 @ 2.33GHz × 4
Graphics AMD® Cedar
Gnome 3.28.1
OS type 64-bit
Disk 117.6 GB

Software & Updates -> Additional Drivers -> "No proprietary drivers are in use."

---

### Post by Claus7 on 2018-04-26
Hello,

1) there is no need to run the command you mention as root

2) maybe changing your display manager to lightdm might have better results. You could try, and since its lighter, you might decrease your boot time as well. 

3) from my experience some session types are working better with some display managers

4) reinstalling gdm3 might be an option as well, having fully removed it from your system first (just end up having one display manager installed though and reboot from change to change).

Regards!

---

### Post by Ron_Zoscak on 2018-04-26
It started working again.  As far as I can remember, all I did was re-enable a software source that the upgrade had disabled, [http://ppa.launchpad.net/jcfp/sab-addons/ubuntu](http://ppa.launchpad.net/jcfp/sab-addons/ubuntu), and then updated with Software Updater.

---

### Post by dsansom on 2018-05-05
could you say how. I have just upgraded to 18.04 and it goes straight to console, 
I can then run startx but it goes to unity
I want the old login screen back where I can select gnome fallback and have everything how it was.

---

### Post by bill81 on 2018-05-08
I have the same problem.  I can run startx and I get the gnome desktop.  But i cannot get automatic log in to work.

---

### Post by Hodor on 2018-05-09
Best to start your own thread I think.

---

### Post by jduff on 2018-05-18
Yes, I think for some computers the upgrade is broken because I can't get to the login page either.

Clearly though it must be working correctly for some people. 

How are they making it to the login page?

---

