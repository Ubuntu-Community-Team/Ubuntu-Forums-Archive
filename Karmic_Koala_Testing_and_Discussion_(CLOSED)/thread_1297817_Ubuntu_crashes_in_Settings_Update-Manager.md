---
title: "Ubuntu crashes in Settings Update-Manager"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-10-22
When I call System - Administration - Update-Manager and select "Settings" a blank window shows and the system instantly crashes. Requires restart.

Michael

---

### Post by awam66 on 2009-10-22
> **Yumi said:**
> When I call System - Administration - Update-Manager and select "Settings" a blank window shows and the system instantly crashes. Requires restart.

Michael

No problem here with my Sony Vaio NR10E laptop running latest Karmic.
You don't say anything about your setup. That might help others who know more than I.

---

### Post by ajgreeny on 2009-10-22
What happens if you try getting to the same places using synaptic ->Settings ->Repositories?

---

### Post by philinux on 2009-10-22
> **Yumi said:**
> When I call System - Administration - Update-Manager and select "Settings" a blank window shows and the system instantly crashes. Requires restart.

Michael

Until the cause is determined, dont hit the power button to restart try first, alt>printscreen>k. If that doesn't work then use REISUB, [http://lifehacker.com/298891/gently-restart-a-frozen-system](http://lifehacker.com/298891/gently-restart-a-frozen-system)

---

### Post by Yumi on 2009-10-22
Calling Synaptic has the same effect. Just System - Administration - Synaptic and it crashes.
-A small white sqaure undecorated window with no contents appears.
-Bars are greyed
-For some seconds that round turning clock apears
-Then nothing, only the mouse pointer can move
-every so often the HD Indicator light flashes

Alt + PrtSc + k brings up a black screen, Then the login shows and works.

Michael

---

### Post by philinux on 2009-10-22
> **Yumi said:**
> Alt + PrtSc + k brings up a black screen, Then the login shows and works.

Michael


Good then at least you can log back quickly. All the above does is kill the x seesion and take you back to the gdm login.

How about doing a command line update, that might even fix your problems.
```
sudo apt-get update && sudo apt-get upgrade
```

Post back if you receive any errors.

---

### Post by Yumi on 2009-10-22
Phillinux, I followed your advice, that calling the terminal caused the same error. Logged into xterm session and entered sudo .... as suggested. 

Downloads lots of files but then>
Fetche 144 kb in 6s 
W: Failed to fetch http:/ftp.jaist.ac.jp/pub/LInux/ubuntu/dists/karmic/universe/source/Sources.bz2 Hash Sum mismatch

E: Some index files failed to download. they have been ignored, or old ones used unstead.

I try to switch mirror from command line and try a different one.

Michael

---

### Post by Yumi on 2009-10-23
Just remembered that this problem started when I went back to Jaunty due to Grub Error 17. Instead of finding the reason, I upgraded to Karmic again. Seem the upgrade failed to repair whatever went wrong in Jaunty.

As I had other issues as discussed in other threads, I decided to reinstall Jaunty again, then do a straight upgrade to Karmic. Up to now everything is ok apart from the sound, but this is a different issue.

Thanks for the advice

Michael

---

