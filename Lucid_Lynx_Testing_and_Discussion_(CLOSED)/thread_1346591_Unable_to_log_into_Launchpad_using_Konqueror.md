---
title: "Unable to log into Launchpad using Konqueror"
date: 2009-12-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-12-05
I'm using the latest version of Kubuntu kernel 2.6.32-6 64bit and am trying to log into Launchpad via Konqueror (4.3.3). I'm asked to log-in with my usual username and password. Konqueror asks whether I want to save these details (to which I agree). I'm unable to log-in as I just get pinged back to the main launchpad page where I'm not logged in. 
It's suggested that I may need to enable cookies but the cookie handler service can't be enabled (see attached). It says I can't manage cookies on my PC!
Is anyone else seeing this ?
Is there something that I'm missing ?
I can log into Launchpad via Ubuntu 10.04 with no problems.

---

### Post by ajgreeny on 2009-12-05
It looks as if the screenshot shows you on the general settings of Konqueror, not the cookies setings further down the list on the left, but perhaps the picture is as far as you can get?

If that is the case, I suspect ypu need to make a new profile, or whatever it is called in Konqueror, which I think you will find in ~/.kde/share/apps/konqueror.

Try renaming that folder, restart konqueror, and see if it then works properly.

---

### Post by Kevbert on 2009-12-05
Thanks for the reply. I'll try it out later as Kubuntu 10.04 is not my default OS on this PC and post back the results.
Edit: Whenever I try to change the cookie settings I get the same message as shown in the previous screenshot. If I close Konqueror and then reopen it the setting (that I've just made) is there regardless of the message. The profiles folder was just where you said it was and the file is called webbrowsing. I've renamed this and still get the same problem.
I'm also getting daemons crashing, so it may be a bad install. Also when I log-in I have to log-in twice every time, prior to the kdewallet asking for permissions to connect wireless. I may try a clean install tomorrow.

---

### Post by Kevbert on 2009-12-06
So much for a re-install. With today's build of Kubuntu 10.04 I've just found an [[COLOR="Red"]Ubiquity bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/493173"). I'll just have to wait for the Alpha 1 release and then try again.
Someone found a workaround for the Ubiquity bug, but unfortunately I still get the same problems with a clean install of the daily build.

---

