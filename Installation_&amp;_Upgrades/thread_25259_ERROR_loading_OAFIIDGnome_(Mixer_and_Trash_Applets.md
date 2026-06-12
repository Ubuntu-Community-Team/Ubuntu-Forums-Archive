---
title: "ERROR loading OAFIID:Gnome (Mixer and Trash Applets)"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by iminj on 2005-04-09
On a fresh hary installation, the system booted with a BROKEN ubuntu desktop. Using synaptic, I removed and then reinstalled the desktop. Synaptic no longer reporting a broken desktop.

Now, when I start the system, I receive 2 errors when GNOME loads:

Panel encountered a problem with loading OAFIID:GNOME_MixerApplet
Panel encountered a problem with loading OAFIID:GNOME_TrashApplet

There is NO trash bin on my desktop, and no mixer icon (although I do have sound, and can open the OSS Mixer thru the GUI - applications > Sound and Video > Volume Control).

Anyone able to provide some assistance to fix these errors?

-iminj

---

### Post by normanya on 2005-05-14
Hey!

I also got this message :

---
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/mixer/prefs;background=none:;orient=down;size=x-small;locked_down=false

Do you want to delete the applet from your configuration?
---


I did not know which package was concerned. I googled my problem and found out that a lot af people have the same issue without solution. So I just tried to install some packages. So, actually, you need to (re)install "gnome-applets" (and its dependencies "gnome-applets-data"). That's it!

After few investigation, in my case, I found out that the "GSwitchIt" installation uninstalled "gnome-applets". That's why I also got :

---
The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".
Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/applet_0/prefs;background=none:;orient=down;size=x-small;locked_down=false
---

Have fun!

---

### Post by anando on 2005-09-03
Hi

I was fooling around with my new install of Ubuntu Hoary 5.04, and then at some point after I logged in, I got a message stating that *my network applet is not working and if I wanted to remove it from my list of configuration*. Like a fool I clicked yes, and now I can't see it in the list of applets ([FONT=Lucida Console]you know when you right click on the panel --> add to panel --> shows a list of available applets[/FONT]). Presumably when I did that it was hashed out from some file that lists all the applets - can someone please help me ? I have tried re-installing gnome-applets package and gnome-applets-data package - but it does not help.

Thanks,
Anando.

---

### Post by Skebaristi on 2005-09-06
I've got the same problem as the thread starter, but when I try to reinstall the gnome-applets-data package, I get this error message:

Preparing to replace gnome-applets-data 2.10.1-0ubuntu2 (using gnome-applets-data_2.10.1-0ubuntu2_all.deb) ...
Unpacking replacement gnome-applets-data ...
dpkg: error processing gnome-applets-data_2.10.1-0ubuntu2_all.deb (--install):
 unable to stat `./usr/lib/bonobo/servers/GNOME_CharpickerApplet.server' (which I was about to install): I/O-virhe
dpkg-deb: subprocess paste killed by signal (Katkennut putki)


What can I do??

Thanks

EDIT: I managed to fix it by removing the packages first and then installing again, now stuff's in working order again  :)  Except that I had to manually repair something (read: press enter multiple times to agree, not knowing what it did  :razz: ) after rebooting, but it has nothing to do with this topic, I hope...

---

### Post by randylikesdrums on 2006-12-03
THANK YOU! you have saved me so much time!

Randy

> **normanya said:**
> Hey!

I also got this message :

---
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".


Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/mixer/prefs;background=none:;orient=down;size=x-small;locked_down=false

Do you want to delete the applet from your configuration?
---


I did not know which package was concerned. I googled my problem and found out that a lot af people have the same issue without solution. So I just tried to install some packages. So, actually, you need to (re)install "gnome-applets" (and its dependencies "gnome-applets-data"). That's it!

After few investigation, in my case, I found out that the "GSwitchIt" installation uninstalled "gnome-applets". That's why I also got :

---
The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".
Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/applet_0/prefs;background=none:;orient=down;size=x-small;locked_down=false
---

Have fun!

---

### Post by mlissner on 2007-12-07
The only solution I could figure out for this was: ```
aptitude search applet | more
```
Then I did an ```
aptitude reinstall [any applet preceded by a v or an i in previous step]
```

This essentially reinstalled all the applets on my system, and that did the trick. What a pain. I have no idea what caused this either.

---

### Post by msmalin on 2007-12-08
I just had to deal with this as well.  At first I just tried reinstalling gnome-applets-data and gnome-applets, then restarted gdm, but that didn't work out, I still got the same error.

So I tried it again, but I first completely stopped gdm then reinstalled gnome-applets:

```
sudo /etc/init.d/gdm stop
sudo aptitude reinstall gnome-applets
```

It's working ok for me now.  If that doesn't work for you then try reinstalling gnome-applets-data as well.

---

### Post by helpdeskdan on 2008-05-21
gnome-applets - thanks Msmalin!  It appears mine somehow got uninstalled.  When I went to reinstall them, they weren't there.  Installed them, booted gdm, and everything is back and I don't have to reinstall.  Thanks!

---

