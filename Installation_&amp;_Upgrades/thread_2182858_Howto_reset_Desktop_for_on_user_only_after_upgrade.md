---
title: "Howto reset Desktop for on user only after upgrade"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2013-10-22
After upgrading to 13.10, my default users does not see the desktop.

I get the Login screen, but when I log in, I can only see the mouse cursor, but nothing else.

I've created a brand new user, and that works fine, so I just need to figure out how to reset the desktop for the old user without loosing all other configurations in the process.


The one difference I found looking in syslog between the working and the dud Desktop is the working Desktop message is
 The Device in both case is the monitor


..... colord: Device added: ......
......colord: Automatic metadata add ........


One the old account I get

------ colord: Device removed ......

------ colord: Profile removed .......
Plus a bunch of Network manager warnings (which I don't get on the new account)

---

### Post by lister171254 on 2013-10-22
Check a few more threads and tried a few thigs including deleting .Xauthority and the compiz-1, metacity folder under .config


One of these things worked briefly as I managed to get in, but after a reboot, I'm left with a mouse cursor but no Desktop. The other (new) account work ok.

---

### Post by neelson2 on 2013-10-23
I had and have the same problem with unity (panel, launcher) not appearing on login. The only solution i found was to open the terminal with a keyboard command and install(sudo apt-get install) and run ccsm where you could enable the unity plugin again, which i find very annoying. I also would like to know if there is a way to reset ubuntu settings.

---

### Post by lister171254 on 2013-10-24
Negative. As I can't see the screen after login, I can't run ccsm. Tried to run ccsm without a GUI for the account I have the problem with, and get the message that it can't open a display. 

So I still have my original account that I can login after the upgrade, but cannot see anything other than the mouse cursor and an account that was created after the upgrade, which works perfectly.

There must be some files in the old account that cause it to not work.

Thanks

---

### Post by lister171254 on 2013-11-22
I have figured out that the cause of the problem is the fact that I have a soft link for .cache to one of my encrypted drives.

After the upgrade, something now needs access to .cache, which of course is only mounted via encfs after I log in.

My setup did not have any problem prior to the latest version

---

