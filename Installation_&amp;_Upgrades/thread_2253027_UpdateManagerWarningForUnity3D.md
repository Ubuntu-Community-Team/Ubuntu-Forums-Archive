---
title: "UpdateManagerWarningForUnity3D"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2014-11-16
Update Manager warning was received when attempting to upgrade from 12.4 LTS to latest version (14 ??)

I don't have a separate video card on my system and use the onboard MoBo graphics drivers. Evidently there is a detection by the upgrade software that
I might encounter graphics problems or a slow down in system performance. What is recommended to permit going to 14 w/o 3D support? If I encounter upgrade problems by disregarding the warning can I easily revert back to 12.04? 

***************************************************************************************
 For 12.04 and 12.10, ubuntu-classic (no effects) is also a feasible option. To do this, install the gnome-session-fallback package, and then on the login screen click the gear icon and select "Ubuntu-classic (no effects)".

The gnome-session-fallback package is already installed on my 12.4 version. If this is a workaround OK but I don't see a login screen w/ a gear icon? 
************************************************************************************** 

[https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)  

Updating a system without support for 3d to run the unity shell
When updating your system with Update Manager, you will see a warning if your machine does not have 3D support for running the unity desktop environment. This could happen for several reasons:

Outdated hardware not providing required level of OpenGL support
Too new hardware without driver support yet
Obscure hardware without 3d support
Virtual machines
Binary drivers required but not installed
If you choose to continue anyway, Ubuntu will try to run using software rendering (via LLVMpipe). While llvmpipe is pretty good on modern CPUs, if your video card is old your CPU is likely old too, and it may result in unusable performance.

Alternatives may include sticking with an old ubuntu release or switching to one of the lighter weight derivatives or Debian. For 12.04 and 12.10, ubuntu-classic (no effects) is also a feasible option. To do this, install the gnome-session-fallback package, and then on the login screen click the gear icon and select "Ubuntu-classic (no effects)".

X/Bugs/UpdateManagerWarningForUnity3D (last edited 2012-10-24 21:12:36 by bryce)

---

### Post by ibjsb4 on 2014-11-16
> If I encounter upgrade problems by disregarding the warning can I easily revert back to 12.04?
Nope, the only to go back is reinstall 12o4.
> The gnome-session-fallback package is already installed on my 12.4 version. If this is a workaround OK but I don't see a login screen w/ a gear icon?
Try reinstalling it:
At the login screen press Ctrl + Alt + F1 and log in. Then:
```
sudo apt-get install --reinstall gnome-session-flashback
```
May work, may not.  Never know about version upgrades.

If you want to stick with the classic desktop another option would be Mate.
[http://ubuntuforums.org/showthread.php?t=2252858](http://ubuntuforums.org/showthread.php?t=2252858)

---

### Post by grahammechanical on 2014-11-16
> [COLOR=#000000]I don't see a login screen w/ a gear icon?[/COLOR]

It will not be a gear icon but a Ubuntu icon and it sits top right above the login panel where we type our password. My advice would be not to install gnome-session-fallback before the upgrade to 14.04 as gnome-session-flashback is used in 14.04. The upgrade should upgrade fallback into flashback but the less that has to be upgraded the better in my opinion.

If you are using 12.04 and the graphics adapter cannot run Unity 3D then you should be running on Unity 2D which is no longer available. That is why the message is informing you that you will get is llvmpipe. It can give an approximation of Unity 3D and you might think that it is fine. But for those of us whose graphic adapters can run 3D rendering in hardware it seems a little slow.

In 14.04 when we go to Recovery Mode and then select Resume we load llvmpipe.

> [COLOR=#000000]Binary drivers required but not installed[/COLOR]

If that turns out to be the problem, then after the upgrade go to System Settings>Software and Updates>Additional Drivers tab and activate a proprietary video driver. In 14.04 the Additional Drivers utility has become a tab in Software and Updates. In my opinion, when updating it is best to be using an open source video driver and then activate the proprietary video driver afterwards.

Regards.

---

### Post by ozark_hillbilly on 2014-11-17
> **ibjsb4 said:**
> Nope, the only to go back is reinstall 12o4.

Try reinstalling it:
At the login screen press Ctrl + Alt + F1 and log in. Then:
```
sudo apt-get install --reinstall gnome-session-flashback
```
May work, may not.  Never know about version upgrades.

If you want to stick with the classic desktop another option would be Mate.
[http://ubuntuforums.org/showthread.php?t=2252858](http://ubuntuforums.org/showthread.php?t=2252858)


Are you saying to install gnome-session-_flashback_ prior to the upgrade? I have the gnome-session-fallback package installed under 12.04 and did reinstall it at one point.

---

### Post by ozark_hillbilly on 2014-11-17
> **grahammechanical said:**
> It will not be a gear icon but a Ubuntu icon and it sits top right above the login panel where we type our password. My advice would be not to install gnome-session-fallback before the upgrade to 14.04 as gnome-session-flashback is used in 14.04. The upgrade should upgrade fallback into flashback but the less that has to be upgraded the better in my opinion.

So uninstall fallback before the upgrade attempt?

Is there a easy way to see if I'm using Unity 2D currently?

I am getting conflicting information in this thread on what direction to take. Perhaps I should just leave 12.04 LTS on my machine and forget about new releases. For someone such as myself who is not well versed with "workarounds" in the Linux environment it gets complicated quickly. I wish the staff at Ubuntu would take into consideration these potential problems for users who are limited in their abilities when working with Linux. It's frustrating and I get "cold feet" whenever Update Manager starts telling me there is a new release available. If I can brush up on remembering what steps are required as far as reversion back to 12.04  from a failed upgrade then I may try ignoring the 3D warning and attempt to install 14. Is 12.04 left on my computer in such a manner that I can revert back to it without doing a release download?

My biggest fear is getting the computer "hosed" to where I can't boot it or access data. Then I'm screwed and pissed off at myself for not leaving well enough alone.

---

### Post by ibjsb4 on 2014-11-17
> **ozark_hillbilly said:**
> Are you saying to install gnome-session-_flashback_ prior to the upgrade? I have the gnome-session-fallback package installed under 12.04 and did reinstall it at one point.
I'm saying go ahead with the upgrade and if Fallback does not upgrade to Flashback, you can try a reinstall.

You have backup, right?  Never know, may come in handy.

---

### Post by ozark_hillbilly on 2014-11-17
Just to "cover all the bases" [baseball lingo] what specific measures should I take prior to attempting the upgrade?

I have a CD of 12.04 LTS that was generated around March of 2013. Update Manager has been permitted to do periodic updates when notified. I have a current backup of my /Home area data on a separate hard drive. Is there anything else recommended prior to proceeding?

Thanks.

---

### Post by ozark_hillbilly on 2014-11-17
Another idea I had was to think about just buying an inexpensive graphics card to fit my older Gigabyte MoBo. Something that would meet the requirements of Unity 3D. 

Any suggestions on what to look for when making a purchase like that?

---

### Post by ibjsb4 on 2014-11-17
> **ozark_hillbilly said:**
> Just to "cover all the bases" [baseball lingo] what specific measures should I take prior to attempting the upgrade?
I have a CD of 12.04 LTS that was generated around March of 2013. Update Manager has been permitted to do periodic updates when notified. I have a current backup of my /Home area data on a separate hard drive. Is there anything else recommended prior to proceeding?
Thanks.
I like keeping a backup of installed packages.  I use Synaptic 'Save Markings' for this.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+save+markings&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+save+markings&sa=Search&cof=FORID:9)
And there is our resident answer man on backup.
[http://ubuntuforums.org/showthread.php?t=1905507&p=11593625#post11593625](http://ubuntuforums.org/showthread.php?t=1905507&p=11593625#post11593625)
> **ozark_hillbilly said:**
> Another idea I had was to think about just buying an inexpensive graphics card to fit my older Gigabyte MoBo. Something that would meet the requirements of Unity 3D. 
Any suggestions on what to look for when making a purchase like that?
Maybe grahammechanical will chime in on that, I do not run Unity.

---

