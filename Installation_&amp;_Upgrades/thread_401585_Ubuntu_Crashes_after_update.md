---
title: "Ubuntu Crashes after update"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Gibran on 2007-04-04
Hello everyone, I'll try to be as detailed as possible so that you may have a better idea of what's happening. Last night I did a few upgrades that appeared on my list, I can't remember which ones unfortunately, but I had manually searched for updates earlier in the day so it must have been something recent (I **Think** Xorg or something like that was on the list). I hadn't used Windows in a full week now (something I'm ecstatic about, though it's been a bit of a challenge with a few things!) and for the first time this morning I booted from it to copy some sensitive files to an USB memstick. 

After that I rebooted to go back to Ubuntu and the login screen appeared, which I had disabled. I found it odd but once I went in I saw the splash screen and the top and bottom bars loading, but then the screen went black with only the cursor visible for a few seconds and then kicked me out to the login screen (It didn't boot from the start where you see the motherboard starting, but only the Nvidia driver and then the login screen again). I tried entering with KDE and it loaded with no problems, though once I tried loading Beryl the screen went black as it had on GNOME and kicked me to the login screen once more.

I went with failsafe Gnome and I got the following error:
> Unable to determine the address of the message bus Try 'man dbus-launch' and 'man dbus-daemon'

My bet would be that Beryl is causing the system to crash because of the latest update? I don't think booting the Windows partition had anything to do with it, but I figured I should mention it. What can I do to load my beloved Ubuntu under GNOME again? Thanks in advance!<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by Sqwishy on 2007-04-04
If you had a recent xorg update that's probobly the problem, you need to reinstall your drivers, its easiest with envy [[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)] then it should be fine.
this happened to me today and this is what i did.
:D

---

### Post by KingCharles on 2007-04-04
Yeap. Same here. I was able to pin down the problem after loading a "Failsafe XTerm" session.

The problem you are describing does happen when you have beryl installed and running by default in your default session options.

I had it that way, so I had to run synaptic, uninstall beryl and then, go back in with the normal session. I do not know how to access the session default config files (if someone can point that out to me I'd appreciate it).

Anyway, is back to good ol' metacity for now, until beryl gets fixed. I tried also installing Compiz, and the same happened, so I'm certain it has to do with a graphic library that got updated, and broke compatibility with the compositing engines.

Good luck :)

====================
EDIT: 
--------------------------------------------
Oops! I just reinstalled the NVidia Drivers and that seems to have gotten rid of the problem.
Du doo de duum ']

---

### Post by Gibran on 2007-04-04
Same here! I used Envy as  Sqwishy  advised. The link was down but I found it on google: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") I'm back on Linux and lovin' it, thanks! :guitar:

---

### Post by jerrybme on 2007-04-05
I have the same issue, I found that it's related to GL crashing X. I went from beryl to Metacity but as soon as my GL screensaver kicked in it crashed again. Going to reinstall Nvidia drivers now to see if that helps.

Jerry

Update, yes reinstalling the Nvidia drivers fixed the issue. Evidently the update I did yesterday did something to the xgl modules that Nvidia didn't like...

---

### Post by djseto on 2007-04-06
how can I install envy if I cant even get to my GNOME desktop?

---

### Post by rohan2k on 2007-04-10
First, sorry for my poor english, i'm from argentina.

Remove beryl-manager and gnome-settings daemon (.desktop files) from your /.config/autostart directory.
Next, open a gnome session. (the gnome panel isn't there)
Next, open a terminal. Send "killall gnome-panel" and try to execute gnome-panel again.

For me, it's done. Gnome sessions works fine, but beryl-manager not.

I try reinstall dbus and beryl, but no results.

Any ideas?

Best regards, 

Cesar

---

