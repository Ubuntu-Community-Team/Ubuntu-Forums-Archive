---
title: "Bug #409641: Ubuntu Karmic Koala Does Not Boot In Graphi"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by #11u-max on 2009-08-05
i am using ubuntu karmic koala alpha 3.


 when i boot up, i get the normal ubuntu artwork but then it drops down to a shell.
i expected it to do this, but i expected it to go into graphical mode after i logged in.
 

if it makes any difference, i upgraded to karmic koala alpha 3 from ubuntu jaunty jackalope through "update-manager -d.
 

i would really appreciate any help that i can get on this subject!
 

thank you!
-chris nettles, avid ubuntu user.

---

### Post by #11u-max on 2009-08-05
[             Bug #409641:]("https://bugs.launchpad.net/bugs/409641")        
          This report is public [edit]("https://bugs.launchpad.net/ubuntu/+bug/409641/+secrecy/++form++")[IMG]https://bugs.launchpad.net/@@/spinner[/IMG]
       
        **Ubuntu Karmic Koala Does Not Boot In Graphical mode**

---

### Post by taavikko on 2009-08-06
If the gdm is brought up and logging in causes the drop to shell:
Add new user and try to login via it, if the other user account works, then the issue lies within the current setup

If the boot sequence will take you to directly to shell after usplash, type "startx" after login
to see what happens.

Check that "/etc/X11/default-display-manager"
contains the line "/usr/sbin/gdm"

If any restricted drivers in use (fglrx) remove them and test again.
If manually edited menu.lst, revert the changes

---

### Post by tahina on 2009-08-06
I got the same functionality when I had set /var/log to be tmpfs (in ram, not on a hdd, so the info there was gone with every reboot), as per suggestions [here]("https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes"), to reduce writes to the ssd.

Now, apparently gdm needed there to be /var/log/gdm in order to function. Here's a report on that:

[https://bugs.launchpad.net/gdm/+bug/405227](https://bugs.launchpad.net/gdm/+bug/405227)

---

