---
title: "From 5.10 to 6.05 via Update manager : lost my usernames after reboot"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2006-06-03
*** Subject title is 6.06 and not 6.05 sorry ***

Upong starting my 5.10, my update manager told me there was a new Drapper version. On its right, the button Install was there. I clicked it. It started to do the whole installation. On 2-3 occasions it asked me if I wanted to replace or retain some files, I said replace on all of them. I figured since it is an upgrade, it should retain minimal systam configuration data preferences.

Before rebooting, it told me some files were no longer supported. I said Next knowing they would be tagged for removal. It then removed about 31 componants. Then it rebooted. 

So far no problems.

At the logon screen, I tried several combinations of what I though my logon was (it used to display a list of logon that I would simply click and enter password). But no matter what I tried, it kept telling me either username or logon is wrong and that I should be carefull about upper cases.

What am I suppoed to do now ?

Download the ISO and reinstall everything ????

Is there a default admin username/password I could use to logon ???

---

### Post by Browser_ice on 2006-06-03
Anyone ???

---

### Post by llamakc on 2006-06-03
Did you get around to enabling root's password before upgrading? If so, CTRL-ALT-F1 and login as root, check the file /etc/passwd for your login name.

Not to say you've done this but any possibility CAPS LOCK is on?

---

### Post by Browser_ice on 2006-06-03
I'm a noob when it comes to Linux.

TO do this, I would have to know the root pasword. I don't.

I had 2 usernames on it : mine as admin and another one (don't think it would be admin).

---

### Post by llamakc on 2006-06-03
What locale do you use? 

You can still CTRL-ALT-F1 to the TTY and try to login there with the username: admin and the password you BELIEVE it to be.

---

### Post by Browser_ice on 2006-06-04
I finaly managed to get my username back.  It wasn't lost.

I had 2 different usernames on my Linux. I simply logged on with the other one. Did a bit of search for the username folders and found what was my original one. It was a simple underscore that I had forgotten when trying to logon.

So I'm back on my regular username now.

I'm trying to find out how to have on the startup screen, the list of all username logons. I had this before but don't remember how I did it. Trying to find it in the Help files but so far, didn't find it.  I'm not finding the Help files search option very effective. Can anyone tell me how to do it so I don't look for hours in the help files ?

---

