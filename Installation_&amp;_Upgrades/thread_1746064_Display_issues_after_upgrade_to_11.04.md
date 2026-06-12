---
title: "Display issues after upgrade to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by thomasmilo on 2011-05-01
[ATTACH]190694[/ATTACH]

[ATTACH]190695[/ATTACH]

I had a working and currently updated installation of 10.10.  After upgrade I have display issues I am not able to correct or diagnose on my own.  The graphics issues in terminal 7 make it hard to work there, but I have access to tty 2 and so forth.  I just don't know what to do there.  Attached are two files showing errors:  xsession-errors and dmesg.  If someone expert can take a look and make recommendations, that would be very cool.  Also, if you need more data, let me know what to run and post for you.  Thank you in advance.

---

### Post by thomasmilo on 2011-05-02
What a fiasco!!!
I am choosing Ubuntu Classic at log-in.  It seems to help a little, but the windows are still slow and unmanageable and the panels have yet to reappear.
10.10 was working perfectly on my harware, but this is a mess.
Can anyone tell me where to go from here?
Thx.

---

### Post by gwilym on 2011-05-02
Same as above, upgraded and even in classic mode screen is a mess and everything is very, very slow. Disaster. Help !

---

### Post by MAFoElffen on 2011-05-02
> **thomasmilo said:**
> [ATTACH]190694[/ATTACH]

[ATTACH]190695[/ATTACH]

I had a working and currently updated installation of 10.10.  After upgrade I have display issues I am not able to correct or diagnose on my own.  The graphics issues in terminal 7 make it hard to work there, but I have access to tty 2 and so forth.  I just don't know what to do there.  Attached are two files showing errors:  xsession-errors and dmesg.  If someone expert can take a look and make recommendations, that would be very cool.  Also, if you need more data, let me know what to run and post for you.  Thank you in advance.
Read both. 

1. Are you using 32bit or 64bit?

2. What is your hardware base, video base and monitor?

3. Have you read this sticky? [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by thomasmilo on 2011-05-02
I am using a 5 year old Dell Dimension tower.  HW info attached.

Logging into Gnome desktop is still not working, but I am using LXDE desktop and have no trouble logging into that.  I read the thread but was not able to find anything that helped me at that time.

I tried a bunch of suggestions from various posts.  May have made it worse.  Deleted the ICEauthority file that seemed to prevent my logging in right after the upgrade to 11.04.

Deinstalled and reinstalled Nautilus.

Deinstalled and reinstalled gdm.

Now when I select gnome shell or gnome desktop at GUI login, the machine works for a long time but all I can see is the cursor pointer and a black screen.  As I said, LXDE desktop is working.

Thanks for any suggestions.

---

### Post by thomasmilo on 2011-05-03
And the monitor is a Samsung SyncMaster 175v.

---

### Post by thomasmilo on 2011-05-03
I just installed the latest updates, the first following upgrade to dist ver 11.04.  The behaviour is unchanged.  I can use LXDE.  But when I choose Ubuntu Gnome Shell Desktop at log-in, I hear the Ubuntu music, the screen goes to black, I can move the mouse cursor, the computer works away with lots of disk activity for a couple minutes and then I get the following error message:
QUOTE
Oh no! Something has gone wrong.  A problem has occurred and the system can't recover.  Please log out and try again.
END QUOTE

At that point, when I click log out, it takes me back to the GUI login and I can select LXDE and log in with no problem.

Any suggestion on how to get the Gnome desktop shell working?  Anybody?

---

### Post by mchojrin on 2011-05-03
Hi:

  I'm having a hard time too. I recently made the upgrade from a perfectly healthy 10.10 installation to a 11.04 and now, whenever I log in using my old session I get a "Xsession unsupported number of arguments(2)".

  I don't know what that means. I could successfully login, but I don't have any panels or window borders :p

  Anyway, right now I have installed gnome3 and it seems to be working fine, but still... what is going on?

---

### Post by frankvdh on 2011-05-03
There's not a lot of detail in what's posted here, but does [this]("http://ubuntuforums.org/showpost.php?p=10761831&postcount=2") sound like the kind of issues you're having?

In particular, have you tried logging in with "Ubuntu Classic (No Effects)" selected?

---

### Post by thomasmilo on 2011-05-03
At the GUI login, I have the following selections to choose from:
Gnome/Openbox
KDE/Openbox
KDE/Plasma
LXDE (desktop I am currently using)
Openbox session
Recovery console
Ubuntu Gnome Shell Desktop (won't start, as mentioned above)
User Defined Session

Classic is not mentioned.
Earlier in the thread I posted the dmesg output, xsession errors from right after I upgraded to 11.04 as well as a description of my hardware, in case any of that might indicate what might me wrong.  

Thx.

---

### Post by Rodrigo on 2011-08-06
> **mchojrin said:**
> Hi:

  I'm having a hard time too. I recently made the upgrade from a perfectly healthy 10.10 installation to a 11.04 and now, whenever I log in using my old session I get a "Xsession unsupported number of arguments(2)".

  I don't know what that means. I could successfully login, but I don't have any panels or window borders :p

  Anyway, right now I have installed gnome3 and it seems to be working fine, but still... what is going on?

THIS!... it's my exact same problem :(
I really have no clue whats going on with my Ubuntu Session after the upgrade, my Lubuntu on the other hand works great.

---

