---
title: "Shutdown/Restart failure, No Sound and Unable to Mount After Upgrade"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by ppallett on 2010-07-22
I am using Ubuntu 10.04 on a dual-boot system with Windows 7.  Yesterday I upgraded from 2.6.32-23 to 2.6.32-24.  After that, pressing the shutdown button and selecting shutdown or restart (whether on the login page or after I've logged in) will only bring me back to the login page.  I can shutdown or restart if I do sudo shutdown now, but I'd prefer to use the GUI.  Also, there is no sound now (not a big deal, but still not good).  And I can't access my storage partition  (not the windows7 partition, but a third ntfs partition with data on it).  I get the error message that I am unauthorized to mount.  I have the only account on this computer, so I should be authorized.  This one is a HUGE problem for me, because I need to be able to access my data for work.  None of these were problems before the upgrade.  

Oh yeah, and quickstart is not enabled.  Also, if I go to Power Management, and try to alter what to do when Power Button is pressed, my only option is Ask Me.  I know these have been problems/solutions to the shutdown/restart problem in the past.

---

### Post by quixote on 2010-07-24
No solution here.  I haven't got that update yet.  Now I'm not sure whether I'll be pushing the update button or not.  Anybody else run into something like this?

What kind of computer and graphics do you have?

---

### Post by clownen on 2010-07-25
I'm also facing these kind of problems. No sound, not authorized to mount usb hard drives. Problem is with 2.6.32-24 kernel. I have Nvidia graphics.

---

### Post by rdaussa on 2010-07-30
Same issue !! any solutions yet?

edit
I just uninstalled Flash Plugin 10. Everything works now.

---

### Post by ariadacapo on 2010-08-05
Exact same issues here (no sound, unable to shutdown/restart, not authorized to mount). Glad to see I’m not alone!

Hardware is HP Compaq nc6000 laptop. Both the original 10.04 kernel, 2.6.32-21, and the one available on update, 2.6.32-24, display the problem.

Problem is occasionnal, about 50% of the time I get a "normal" boot.


> **rdaussa said:**
> 
edit
I just uninstalled Flash Plugin 10. Everything works now.

I doubt it really solved the problem - I don’t believe Flash has anything to do with the OS’s ability to use the hardware. 
In my case Flash is not installed.

---

### Post by ariadacapo on 2010-08-05
I think this is bug [#544139]("ttps://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139"), please have a look and indicate that it affects you if this is the case.

---

### Post by JohnElway on 2010-08-20
I also had this same set of problems but I fixed them by installing the policykit package:

```
sudo apt-get install policykit policykit-gnome policykit-desktop-privileges
```

Then rebooted:

```
sudo reboot
```

---

### Post by quixote on 2010-08-20
Interesting.  What do the policykit packages do? I.e. what gave you the idea that that was where the problem might lie?  I thought they dealt with passwords or something. ??

---

### Post by Lokiii on 2010-08-27
I have the exact same issue. Though usually I can resolve it by rebooting x number of times until it works. However, when i Reboot it again chances are it wont work any more..

Will try the install the policy kit though.. If it sorts things out I would be relived but also puzzled :S

---

### Post by Lokiii on 2010-09-02
And it worked! Thanks so much!

I am completely lost as to why it works though :S

---

### Post by Lokiii on 2010-09-04
Sorry for the bump but after updating to 2.6.32-24 the problem is back :(

---

### Post by JohnElway on 2010-09-05
Sorry, I forgot about this thread. 

I'm not quite sure what the policykit package is for, but I found the install command in an old thread discussing these same issues and it seemed to solve a lot of peoples' problems. Sure enough, it worked for me as well. I probably should have made it clear that I didn't come up with the solution myself, nor did I really understand it.    

@Lokiii Sorry I can't really give you much advice. I guess you can just use the previous version of the kernel and see how things work when the next new kernel is released.

---

### Post by DandyDon on 2010-09-05
Under Preferences-Sound-Output, make sure the speakers aren't muted. That did the trick for me.

---

### Post by Lokiii on 2010-09-06
> **DandyDon said:**
> Under Preferences-Sound-Output, make sure the speakers aren't muted. That did the trick for me.

You are forgetting the fact that the loss of audio is just one of the symptoms. Failing to mount drives and shutdown/restart properly are other issues seemingly unrelated to audio. 

Have no idea what causes this issue but it sure annoying..

---

### Post by Fluffgar on 2010-09-06
> **ppallett said:**
> pressing the shutdown button and selecting shutdown or restart (whether on the login page or after I've logged in) will only bring me back to the login page.  I can shutdown or restart if I do sudo shutdown now, but I'd prefer to use the GUI.  Also, there is no sound now (not a big deal, but still not good).  And I can't access my storage

I had this problem yesterday and not being an ubuntu expert could only reinstall the OS from live disk. If it happens again I will try JohnElway's "policy kit" solution. 

I don't know if it's the same problem as ariadacapo suggested ([#544139]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139")). The bug link was missing an "h" at the beginning of "https" when I click it as well.

---

### Post by Fluffgar on 2010-09-07
> **JohnElway said:**
> I also had this same set of problems but I fixed them by installing the policykit package:

```
sudo apt-get install policykit policykit-gnome policykit-desktop-privileges
```Then rebooted:

```
sudo reboot
```

Holy crap, this really does work. 

(Yes the sound/mounting problem did happen again, but fortunately Mr.Elway's fix worked).

---

### Post by fpohlmann2 on 2010-09-17
Thank you Fluffgar,

You saved my life!!!!

Thank you so much.

---

### Post by rmhopper on 2010-10-10
I have an HP Compaq laptop nc6000 running lucid 10.04 and have all the same symptoms described here.  I installed the policy packages as described here above and it worked (Sound hardware was found, Gnome shutdown was successful) through exactly one reboot before all the symptoms returned.  Any other suggestions?

---

### Post by rmhopper on 2010-10-10
OK, the fix for me does appear to be the Lucid consolekit patch described in comments 124 and 125 of bug 544139 ([https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/544139/+index?comments=all)) located at [https://launchpad.net/~cjwatson/+archive/ppa](https://launchpad.net/~cjwatson/+archive/ppa).  Three boots so far, and all is good.

---

### Post by keerthi on 2011-03-13
Thanks a lot :popcorn:. Policy Kit trick worked for me as I've encountered the same issue in sound/pendrive/shut down etc. on Ubuntu 10.04

---

