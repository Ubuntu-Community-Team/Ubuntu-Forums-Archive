---
title: "HELP! Can't log into normal Gnome session"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by lethalfang on 2010-11-06
I just installed 10.04.1 i386 into a friend's computer, but I can't properly log in!
Every time I type the password into the login screen to start Gnome Session, it goes right back into the login screen! FAILSAFE Gnome and XTerm works, but the normal Gnome does not. 
Anyone has any idea what the problem is, and how to fix it?

Thanks!

EDIT:
The Video Card is 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01) (prog-if 00 [VGA controller]).

---

### Post by Barriehie on 2010-11-06
> **lethalfang said:**
> I just installed 10.04.1 i386 into a friend's computer, but I can't properly log in!
Every time I type the password into the login screen to start Gnome Session, it goes right back into the login screen! FAILSAFE Gnome and XTerm works, but the normal Gnome does not. 
Anyone has any idea what the problem is, and how to fix it?

Thanks!

At the login screen select gnome and see if starting a new session rather than the previous saved one works.

---

### Post by lethalfang on 2010-11-06
> **Barriehie said:**
> At the login screen select gnome and see if starting a new session rather than the previous saved one works.

That's been the problem. If I select normal GNOME session, it goes right back to the login screen. Another symptom of the problem is that the Number Lock key isn't remembered when the screen goes back to the login screen.
I can only log onto the FAILSAFE GNOME or XTerm.

---

### Post by Barriehie on 2010-11-06
From grub login via single-user mode and go to /home/user_name/.gnome2/ directory and mv ./session to ./session.bak.  That file contains the failsafe startups and the default startups.  By renaming it you won't lose anything and the session manager should recreate it.

HTH

---

### Post by ranser on 2010-11-06
I have quite the same problem with my Lubuntu 10.10.
Although the DE is different it acts in a similar fashion.
In my case I have a hunch it is related to the fact that I might not have any more space on my hard disk. I started downloading a huge torrent and forgot to point transmission to the right partition under win xp. After a while I got the message "not enough disk space" or similar, I deleted the torrent and the folder with the content and then went to Trash and tried to empty it and couldn't. Next to each file I got a message like: deleting failed and so on. 
After that when trying to log on it wouldn't let me. After entering name and password it takes off and then goes back to password field. If anyone has any idea please help us.
Sorry to intrude upon your thread but it seems it's the same problem.

---

### Post by lethalfang on 2010-11-06
> **Barriehie said:**
> From grub login via single-user mode and go to /home/user_name/.gnome2/ directory and mv ./session to ./session.bak.  That file contains the failsafe startups and the default startups.  By renaming it you won't lose anything and the session manager should recreate it.

HTH

~/.gnome2/session directory does not exist on my computer. I did a fresh install of 10.10 and it still has never been able to get into normal gnome session, only safe mode.

---

### Post by Barriehie on 2010-11-06
> **ranser said:**
> I have quite the same problem with my Lubuntu 10.10.
Although the DE is different it acts in a similar fashion.
In my case I have a hunch it is related to the fact that I might not have any more space on my hard disk. I started downloading a huge torrent and forgot to point transmission to the right partition under win xp. After a while I got the message "not enough disk space" or similar, I deleted the torrent and the folder with the content and then went to Trash and tried to empty it and couldn't. Next to each file I got a message like: deleting failed and so on. 
After that when trying to log on it wouldn't let me. After entering name and password it takes off and then goes back to password field. If anyone has any idea please help us.
Sorry to intrude upon your thread but it seems it's the same problem.

Have you tried emptying the trash via the cli?
/home/user_name/.local/share/Trash/ and then 2 subdirs under Trash that are called files and info.

---

### Post by Barriehie on 2010-11-06
> **lethalfang said:**
> ~/.gnome2/session directory does not exist on my computer. I did a fresh install of 10.10 and it still has never been able to get into normal gnome session, only safe mode.

Hmm, got me then.  I jumped to Debian at 8.04...

Edit: Is there a .gnome ANYTHING in your home folder?

---

### Post by lethalfang on 2010-11-06
> **Barriehie said:**
> Hmm, got me then.  I jumped to Debian at 8.04...

Edit: Is there a .gnome ANYTHING in your home folder?

Yes, inside ~/.gnome2 there are:
accels/
keyrings/
nautilus-scripts/
panel2.d/

---

### Post by Barriehie on 2010-11-06
> **lethalfang said:**
> Yes, inside ~/.gnome2 there are:
accels/
keyrings/
nautilus-scripts/
panel2.d/

Since that file doesn't exist this shouldn't hurt.  Save the below code as /home/your-username/.gnome2/session .   If it doesn't work you can always delete the file.

```

0,Program=nautilus
0,CurrentDirecty=/home/your-username
1,Program=gnome-panel
1,CurrentDirectory=/home/your-username
2,Program=metacity
2,CurrentDirectory=/home/your-username
```

Note that you'll have to correct the /home/your-username part and I'm going with metacity since something is screwed up and compiz is way more resource intensive.

---

### Post by lethalfang on 2010-11-06
> **Barriehie said:**
> Since that file doesn't exist this shouldn't hurt.  Save the below code as /home/your-username/.gnome2/session .   If it doesn't work you can always delete the file.

```

0,Program=nautilus
0,CurrentDirecty=/home/your-username
1,Program=gnome-panel
1,CurrentDirectory=/home/your-username
2,Program=metacity
2,CurrentDirectory=/home/your-username
```

Note that you'll have to correct the /home/your-username part and I'm going with metacity since something is screwed up and compiz is way more resource intensive.

I tried it, and it has no effect. Hmm.....

---

### Post by Barriehie on 2010-11-06
> **lethalfang said:**
> I tried it, and it has no effect. Hmm.....

I'm stumped.  What does it do if you try logging in as root? I know, to be avoided but at this point...

---

### Post by lethalfang on 2010-11-06
I don't know if video card has anything to do with it, but here it is: 
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: VIA Technologies, Inc. Device 0000
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at dfef0000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] AGP version 2.0
	Kernel modules: viafb


When I try to log into normal GNOME, it seems as though it wants to, but before the panel can be fully loaded (in the process of being loaded), it turns into black, and then goes right back into the login screen.

---

### Post by lethalfang on 2010-11-06
Ahh, after some googling with the video driver, I found this solution and it worked: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520")

Thanks for all the help, Barriehie!

---

### Post by Barriehie on 2010-11-07
> **lethalfang said:**
> Ahh, after some googling with the video driver, I found this solution and it worked: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520")

Thanks for all the help, Barriehie!

Glad you got it albeit later than sooner!  So this is [Solved].

---

### Post by ranser on 2010-11-07
> **Barriehie said:**
> Have you tried emptying the trash via the cli?
/home/user_name/.local/share/Trash/ and then 2 subdirs under Trash that are called files and info.

I did empty it from cli and it works fine now. Thank you Barriehie.

---

