---
title: "No GNOME Panels after upgrade"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-09-11
Just upgraded my Satellite Pro laptop which has been running intrepid for some time. I have just done an upgrade as normal, which resulted in a partial upgrade followed immediately by a distribution upgrade and a request for a reboot.

On rebooting I have my normal desktop with the exception of no GNOME panels and no right click menu either. 

Anyone else in the same position? I can get to the command prompt via the safe modes but what to do there?

---

### Post by analystscouch on 2008-09-11
Same happened to me.

Press Ctrl + alt + F1

Login.

apt-get install gnome-panel

---

### Post by BC7333 on 2008-09-11
Similar situation here..

I have xubuntu desktop, so for some reason it booted into that with no gnome session option.

installing gnome panel as posted above restored everything back to normal

Thanks!

---

### Post by analystscouch on 2008-09-11
No probs.

After you have your panels back you might want to go into Synaptic and check ubuntu-desktop is still installed (or kubuntu-deskop etc. if you don't use gnome). I found that it wasn't installed and that meant that non of its dependenices (fast-user-switch applet etc.) had installed either.

---

### Post by scottuss on 2008-09-11
Has anyone submitted a bug report for this?

---

### Post by analystscouch on 2008-09-11
I haven't had time yet. To be honest I'm not totally clear on what happened. Basically I was installing some updates to intrepid using update manager when the laptop restarted causing the install to fail part way through - hence no ubuntu-desktop or gnome-panel. I'm just not sure what failed: update-manager? one of the packages being upgraded? (i think there were about 70!)

---

### Post by scottuss on 2008-09-11
Hmm weird... maybe look through your logs and see what was going on at the time of the restart. It may not actually be a bug then, although if other people are experiencing the same thing.. who knows

---

### Post by Daverobb on 2008-09-11
Hi ,

Same situation with me also.  Mine actually results in the Xfce desktop fully functional. Odd, but I'll trying searching through synaptic for the ubuntu desktop.

*Actually, when I checked in terminal my gnom-panel packages were up to date and ubuntu-desktop is selected in synaptic. Still in Xfce environment though.... *

---

### Post by Swarms on 2008-09-11
I had the same problem, but after I installed panels I could navigate.

But I am unable to install ubuntu-desktop, it says that dependencies are "unresolved". It needs the gnome-applets which I am unable to install through synaptic too.

---

### Post by BCurtisWX on 2008-09-11
Now i'm not blaming anyone, but theres a specific way that you should upgrade during alpha and beta releases.  If you get any warning from update-manager that there is a partial upgrade you need to EXIT out of the update manager and immediately go into your terminals and type "sudo apt-get upgrade".  Through that command there is no risk of losing anything important during an upgrade.  What I am guessing most of you did was a partial upgrade and ignored to look into what was being removed in the first place.  It happens a lot thought.  Just remember this for next time :-)  If you follow the advice on here as to how to fix the problem you'll be okay!

~Brian

---

### Post by BC7333 on 2008-09-11
> **BCurtisWX said:**
> Now i'm not blaming anyone, but theres a specific way that you should upgrade during alpha and beta releases.  If you get any warning from update-manager that there is a partial upgrade you need to EXIT out of the update manager and immediately go into your terminals and type "sudo apt-get upgrade".  Through that command there is no risk of losing anything important during an upgrade.  What I am guessing most of you did was a partial upgrade and ignored to look into what was being removed in the first place.  It happens a lot thought.  Just remember this for next time :-)  If you follow the advice on here as to how to fix the problem you'll be okay!

~Brian

Will try to remember that tip.  

Thanks!
Brian

---

### Post by darkenergy on 2008-09-11
oops i think the thread i just started is about the same issue - sorry, didn't notice the relation earlier.

should pay more attention to avoid partial updates as it seems.

---

### Post by gjoellee on 2008-09-11
I have had the same issue, lucky me I have Gnomr Do (saved the day) so I launched terminal and used the commedn ```
gnome-panel
``` and I went to sessions and clicked on the button "Remember Currently running applications":) And it is fixed

---

### Post by Daverobb on 2008-09-11
Thanks Brian, 

actually you are exactly correct 
```


 Re: No GNOME Panels after upgrade
Now i'm not blaming anyone, but theres a specific way that you should upgrade during alpha and beta releases. If you get any warning from update-manager that there is a partial upgrade you need to EXIT out of the update manager and immediately go into your terminals and type "sudo apt-get upgrade". Through that command there is no risk of losing anything important during an upgrade. What I am guessing most of you did was a partial upgrade and ignored to look into what was being removed in the first place. It happens a lot thought. Just remember this for next time If you follow the advice on here as to how to fix the problem you'll be okay!

~Brian
```

I did do a partial upgrade (I only now remembered) - it worked out for me because once I saw that I had gnome-panel and ubuntu-desktop installed and up to date I just logged back into a gnome session and it was perfect - well the same as before because I haven't been able to get my ATI driver updated yet!  - but that's what you get in an alpha release ...

cheers

---

### Post by danbuter on 2008-09-11
I'm hoping someone submitted a bug, though. I'm really surprised a bug this obvious actually made it into the repos.

---

### Post by BwackNinja on 2008-09-11
Manually updating packages through synaptic gave me no problems, but as BCurtisWX and many others before have said, partial upgrade = bad. Its always good practice whenever you are upgrading and it needs the installation/removal of some packages, not just the upgrading of some packages (aka the partial upgrade) to look over what's happening. If you don't know if something will end well, ask.

---

### Post by jerrylamos on 2008-09-11
> **BCurtisWX said:**
> Now i'm not blaming anyone, but theres a specific way that you should upgrade during alpha and beta releases.  If you get any warning from update-manager that there is a partial upgrade you need to EXIT out of the update manager and immediately go into your terminals and type "sudo apt-get upgrade".  Through that command there is no risk of losing anything important during an upgrade.  What I am guessing most of you did was a partial upgrade and ignored to look into what was being removed in the first place.  It happens a lot thought.  Just remember this for next time :-)  If you follow the advice on here as to how to fix the problem you'll be okay!

~Brian

It would be REALLY HELPFUL!! if the partial upgrade panel would tell us what you just did in the quote.

It would be REALLY HELPFUL!! if the partial upgrade gave us the slightest clue why the the item(s) can't be upgraded.

Most of the time the upgrade sort of works, this time I'm gathering it didn't for a bunch of us.

Thanks for your advice, will try it tomorrow.

Jerry

p.s. reason I'm interested in the upgrades is kernel 2.6.27-2 is plain flat broke on my perfectly standard off the shelf Compaq Presario intel Celeron ATI graphics, launchpad bug #265049. If it was working (at all) I'd just wait to install any upgrades until the partial update situation got fixed.

---

### Post by nanog on 2008-09-11
Sudo apt-get dist-upgrade is much more *fun*.

---

### Post by jerrylamos on 2008-09-12
> **analystscouch said:**
> No probs.

After you have your panels back you might want to go into Synaptic and check ubuntu-desktop is still installed (or kubuntu-deskop etc. if you don't use gnome). I found that it wasn't installed and that meant that non of its dependenices (fast-user-switch applet etc.) had installed either.

Well, there were a succession of dependencies for ubuntu-desktop so they wouldn't install, so the applets won't.

Looks to me like some of the packages are updated/upgraded but not the whole set.

At least it's running sort of after the apt-get install gnome-panel.

Jerry

---

### Post by traxk on 2008-09-16
Ubuntu intrepid Ibex 8.10 alpha-5/kernel 2.6.27-2-generic

I keep on getting this message "the following packages have been kept back: firefox firefox-3.0, firefox-3.0-gnome-support, libdirectfb-1.0-0, linux-generic, linux-headers-generic, linux-image-generic, linux-restricted-modules-generic, smart-core totem, totem-gstreamer, totem-mozilla, totem-plugins, totem-plugins-extra, xorg" (failed to fetch) "GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid release: the following signatures were invalid: BADSIG 2EBC26B60C5A2783"

Ever since september 11 after update/upgrade I can login but there`s no background, panels, desktop or keyboard only blank screen.
I keep this version up to date using session failsafe terminal.
Is there a fix for this issue!?
Thanks
My system: Dell2400-dimension Intel chipset 845G/GL/GV. Dualboot WXP-h/Ubuntu-Linux

---

### Post by traxk on 2008-09-19
Just installed...Intrepid Ibex alpha-6 (alternate live-cd)
Blackscreen after login.
Any solution!?

---

