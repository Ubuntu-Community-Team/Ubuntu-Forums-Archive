---
title: "Abnormal CPU use with Gnome Shell"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by mpiter on 2011-10-19
I upgraded to Ubuntu 11.10 on a one-core laptop.  With Gnome shell, Xorg eats between 50 and 60 % of my CPU and gdl_box eats the rest of the CPU.  That makes the computer unusable, though I could use it with Compiz and another mode than Gnome shell to have a normal CPU consumption.

I then upgraded in the same way on a 8-thread laptop (Intel i7 processors).  With Gnome shell, Xorg and gdl_box take each a full thread at 100 %, i.e., eating 2 full threads out of 8.  The computer is still very fast, but the processor temperature increases to 75 degrees C leading to fans turning at full speed.

I saw in other threads people having a similar issue with Unity, but not with Gnome shell.  The small laptop has an ATI card while the big one has an Nvidia one.  Does anyone has a suggestion about what is happening and how to solve the problem?  Thanks in advance for any piece of information.

---

### Post by musicwurm on 2011-10-20
> **mpiter said:**
> I upgraded to Ubuntu 11.10 on a one-core laptop.  With Gnome shell, Xorg eats between 50 and 60 % of my CPU and gdl_box eats the rest of the CPU.  That makes the computer unusable, though I could use it with Compiz and another mode than Gnome shell to have a normal CPU consumption.

I then upgraded in the same way on a 8-thread laptop (Intel i7 processors).  With Gnome shell, Xorg and gdl_box take each a full thread at 100 %, i.e., eating 2 full threads out of 8.  The computer is still very fast, but the processor temperature increases to 75 degrees C leading to fans turning at full speed.

I saw in other threads people having a similar issue with Unity, but not with Gnome shell.  The small laptop has an ATI card while the big one has an Nvidia one.  Does anyone has a suggestion about what is happening and how to solve the problem?  Thanks in advance for any piece of information.

I am having this exact same issue on my Toshiba laptop. I am having it even when I boot to "classic." Anybody?

---

### Post by ve1uxe on 2011-10-20
It's gdl_box (Google Desktop Linux).  If you kill the process, CPU returns to normal.  I went ahead and removed the google-desktop-linux package from my systems as it's no longer supported.

---

### Post by mpiter on 2011-10-20
> **ve1uxe said:**
> It's gdl_box (Google Desktop Linux).  If you kill the process, CPU returns to normal.  I went ahead and removed the google-desktop-linux package from my systems as it's no longer supported.

Thanks a lot.  That was the solution.  I did not dare to kill the process because I did not know what it was.  I also removed the package from my computer and it works like a charm.  Gnome 3 is the first desktop that seduces me a lot since Compiz + Gnome 2 or Compiz + XFCE4.  Thanks.

---

### Post by feistybird on 2011-10-21
I have the Same problems with [gdl_box (Google Desktop Linux)]("http://askubuntu.com/questions/51460/google-desktop-hotkey-ctrlctrl-doesnt-work") after Upgraded to Ubuntu 11.10 recently

FYR. I just disabled the **'Quick Search Box'** in the Google Desktop Preference, and the problem is solved.

Screenshot is attached.

---

### Post by sunjunhuoyun on 2011-10-24
Unfortunately, I have met the same problem when I upgrade to 11.10.
I also disabled the 'Quick Search Box' in the Google Desktop Preference, but the problem still exist.

Anyone has another solution?

---

### Post by mpiter on 2011-10-24
> **sunjunhuoyun said:**
> Unfortunately, I have met the same problem when I upgrade to 11.10.
I also disabled the 'Quick Search Box' in the Google Desktop Preference, but the problem still exist.

What about completely discarding Google Desktop: ```
aptitude purge GD_name
``` (I do not remember the name of the package)?  I did it, and is solved the problem for me.

---

### Post by sunjunhuoyun on 2011-10-28
> **mpiter said:**
> What about completely discarding Google Desktop: ```
aptitude purge GD_name
``` (I do not remember the name of the package)?  I did it, and is solved the problem for me.
Thank you for your kindly reply.
I need Google Desktop to search my computer to find files. So I can't discard Google Desktop. 
Is these any good solution?
Thanks.

---

### Post by mpiter on 2011-10-29
> **sunjunhuoyun said:**
> Thank you for your kindly reply.
I need Google Desktop to search my computer to find files. So I can't discard Google Desktop. 
Is these any good solution?
Thanks.

I do not know.  Because Google stopped supporting that package and even took it away from their Web site to be sure that nobody would download it again, I think the best solution is to find a replacement.  You can search the forums to see if something good exist or start a new thread asking that question.

---

### Post by feistybird on 2011-11-21
> **sunjunhuoyun said:**
> Thank you for your kindly reply.
I need Google Desktop to search my computer to find files. So I can't discard Google Desktop. 
Is these any good solution?
Thanks.

I'm still using Google Desktop Linux for my desktop search... Tracker/Tracker-needle is so useless , it can't even index PDF files unless rebuild manually with proper configurations.

I noticed that the GDL tray icon flickers a lot in the Gnome 3 so I guess this is what caused very high CPU Load. Unfortunately there is no way to hide the tray icon in Gnome 3 Desktop, so I log in to Unity Desktop , and hide the GDL icon rom the notification area using this trick here [http://www.webupd8.org/2011/04/how-t...tion-area.html](http://www.webupd8.org/2011/04/how-t...tion-area.html), but blacklist GDL instead of whitelist it - you may also you dconf-editor to change this too.

Not sure if this made any difference, but my GDL actually became much more stable after this tweak! I mean the high CPU load could occasionally happen sometimes when running too much programs altogether in Unity, but not very often now.

---

### Post by feistybird on 2012-02-06
Lowering gdl_box process priority seems solving the high CPU usage problems on my Ubuntu 11.10.

Just in case anyone is interested in, I ran Google Desktop Linux with the following scripts placed in the 'Autostart':

```
#!/bin/sh
/opt/google/desktop/bin/gdlinux start
sleep 2
renice +10 `pgrep gdl_service`
renice +15 `pgrep gdl_config`
renice +20 `pgrep gdl_box`
```

Also make sure that the 'gdlinux' must NOT be whitelisted in the Unity panel's system tray:

dconf-editor:
[IMG]http://i570.photobucket.com/albums/ss145/feistybird/screenshot_001.jpg[/IMG]

---

### Post by dwitkin on 2012-03-01
Hello. The link in the post below doesn't work. Can you re-post the link or the exact name of the article? I'm having the same problem with gdl_box and way to find a way to continue using Google Desktop. I've already reduced the nice value to 19, but that doesn't solve the CPU usage -- it just lowers the priority so the system is usable.

Or is there a way to completely remove the Gnome 3 notification area? Blacklisting gdl_box would be better for me, though, because I use the notification area for other applications.

Thanks for your help.


> **feistybird said:**
> I'm still using Google Desktop Linux for my desktop search... Tracker/Tracker-needle is so useless , it can't even index PDF files unless rebuild manually with proper configurations.

I noticed that the GDL tray icon flickers a lot in the Gnome 3 so I guess this is what caused very high CPU Load. Unfortunately there is no way to hide the tray icon in Gnome 3 Desktop, so I log in to Unity Desktop , and hide the GDL icon rom the notification area using this trick here [http://www.webupd8.org/2011/04/how-t...tion-area.html](http://www.webupd8.org/2011/04/how-t...tion-area.html), but blacklist GDL instead of whitelist it - you may also you dconf-editor to change this too.

Not sure if this made any difference, but my GDL actually became much more stable after this tweak! I mean the high CPU load could occasionally happen sometimes when running too much programs altogether in Unity, but not very often now.

---

### Post by mrule on 2013-03-26
I am having a similar problem and google-desktop-linux is not installed.

---

