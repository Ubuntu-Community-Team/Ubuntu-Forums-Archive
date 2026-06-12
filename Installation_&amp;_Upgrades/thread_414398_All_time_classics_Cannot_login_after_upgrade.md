---
title: "All time classics: Cannot login after upgrade"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by october1917 on 2007-04-19
Please help me:

I did everything as i had. I upgraded, averything went fine, and the computer restarted. After loading GRUB (the only OS is Ubuntu) there started the reiser fs testing (which shows if the fs is clean or not). It said that there is no /dev/hda4 partition but there is! and many more that i couldn't remember.

After that it anded to a comand line, as root. I wrote "startx" and it returned "startx is not istalled, you have to run apt-get install xinit". So i did and it returned "apt is not installed, you have to run apt-get install apt"!!!!!!! As you can understand nothing colud be done.

So i wrote "reboot". Then the dydtem started to load "ASPI modules" and many more, and finally the login screen apeared! I wrote username and passdw and it returned "user "myuser" doesn't seem to exist.Whould you like to use /root as homefolder?" Of course i afreed and again it couldn't login because the session lasted too little.

I thought that it sould be an fstab problem, so i loged in using the Live cd, mounted the / partition and fixed fstab replacing the UUID value in the firts collumn with the /dev/device (/dev/hda1 /dev/hda2 and so on). I rebooted but nothing new happened.

Do you think that could there be a solution, or i have to do i clear new installtion?

Thank you.

---

### Post by october1917 on 2007-04-19
Also do you thing that my problem is close to any other of all those posted here, in order to foloow the instuctions?

---

### Post by bwhite82 on 2007-04-19
Wow, dunno what happened here bud. Would it hurt to do a clean install? To answer your question, I've seen A LOT of folks having trouble with the "upgrade" option.

---

### Post by october1917 on 2007-04-19
No, but it should be better if i could fix it doing just some clicks!

I don't think that my problem matches the others, eh? Anyway, a friend of mine did clean install and he also faced problems.

Something more: do you think that after this bad experience, may Ubuntu release a new download? Because i'm scared a little bit to do a clean install and have to face the same bugs. Do you think i have to wait for some days, or there will no fixed version released officially?

---

### Post by bwhite82 on 2007-04-19
This is one of the downsides to having that 6-month release cycle. Ubuntu bases their "stable" releases off of Debian's "unstable" images. Generally, it's not a bad idea to wait to do an upgrade until some time has passed, and some fixes have been released. And yes, a lot of folks are having problems with clean installs as well. It's really your call.

---

### Post by october1917 on 2007-04-20
I fixed it. See my post here for more information.
[http://ubuntuforums.org/showthread.php?p=2490227#post2490227](http://ubuntuforums.org/showthread.php?p=2490227#post2490227)

---

### Post by realGaurab on 2008-04-27
> **october1917 said:**
> I fixed it. See my post here for more information.
[http://ubuntuforums.org/showthread.php?p=2490227#post2490227](http://ubuntuforums.org/showthread.php?p=2490227#post2490227)
I have the same problem as well.

I upgraded to 8.04 yesterday. Whenever I try to login, it tries to load up my desktop, but then immediately after I see my desktop, the screen goes blank and takes me to the login screen again.

I tried going to your link and trying to do you fix but the file partitions in /proc is empty. :confused:

I am currently logging in from FailSafe GNOME mode and I can use the same login and password and everything (including add/remove applications) is working fine. I wonder what the problem is.

---

