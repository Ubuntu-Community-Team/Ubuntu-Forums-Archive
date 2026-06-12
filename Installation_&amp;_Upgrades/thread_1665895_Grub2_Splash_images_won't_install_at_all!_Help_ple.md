---
title: "Grub2 Splash images won't install at all! Help please."
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Krishna2134 on 2011-01-12
Hey guys, newbie here.
I got my hands on a copy of Ubuntu 10.10 and migrated from Windows 7, and I'm pretty firm on what OS i'll stick with.
(Hint: Ubuntu)

So I heard you can install a Splash image for GRUB.
Well, I'm running Grub 1.98.

I followed the instructions on the Wiki--I installed the grub2 splash images, and used sudo gedit to edit the config file in the debian folder. I saved it after I finished editing it.

At first I decided to get a pic from the internets (640x480 and converted to TGA via GIMP) and put it in /usr/share/images/grub. I did that, put the correct path, and when I ran sudo update-grub it didn't do anything.

I thought to use the pre-installed images (I saw it in a forum post here) and not even THAT worked.
I correctly edit the config file but when I update GRUB in the terminal I don't see the line where it says it installed the boot image.

Can anyone help this new user?
Thanks :)

(Btw. I love randomly shaking my open windows all over the screen because my graphics settings are on "extra". XD)

Update: sudo update-grub2 doesn't work either!

---

### Post by sikander3786 on 2011-01-13
Welcome to the forums :-)

There is a GUI Tool recently developed to serve the purpose. Might help you out.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)
courtesy of forum member *drs305*

---

### Post by Quackers on 2011-01-13
See item 8 in this guide, by drs305, as it can depend on which version of grub you are using
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Krishna2134 on 2011-01-13
> **sikander3786 said:**
> Welcome to the forums :-)

There is a GUI Tool recently developed to serve the purpose. Might help you out.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)
courtesy of forum member *drs305*

I've tried the GUI, but when I  came to selecting the image, it couldn't find it, (I put it on my Desktop) and it didn't show up there, I tried saving it in PNG and TGA format.

Thank you guys for your help!!

---

