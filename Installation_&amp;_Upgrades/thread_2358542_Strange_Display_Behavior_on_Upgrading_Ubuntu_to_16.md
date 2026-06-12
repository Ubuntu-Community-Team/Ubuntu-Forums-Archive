---
title: "Strange Display Behavior on Upgrading Ubuntu to 16.10"
date: 2017-04-14
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2017-04-14
I've been running Ubuntu 16.04 LTS quite happily since it came out.  The recent news about the impending death of Unity combined with curiosity about the new KDE 5.9 Plasma desktop motivated me to upgrade.  I figured I'd upgrade to 17.04 first and then install the Kubuntu desktop environment.  I never got that far.

I found the installation guide in [http://www.omgubuntu.co.uk/2017/04/how-to-upgrade-to-ubuntu-17-04](http://www.omgubuntu.co.uk/2017/04/how-to-upgrade-to-ubuntu-17-04) and followed it.  First, in the System Settings, I went into Software and Updates and in the Updates tab changed the "Notify me of a new Ubuntu version:" to "For any new version".
I then used the terminal and ran the commands "[COLOR=#333333]sudo apt update && sudo apt dist-upgrade" and finally "[/COLOR][COLOR=#333333]sudo do-release-upgrade -d".  (I now understand that adding the '-d' at the end was unnecessary, but I don't know if it caused my problem or not.)

The update appeared to proceed normally, all packages were fetched and installed, and in a couple of hours it prompted me to reboot for Ubuntu 16:10.  Once I did, however, everything fell apart.
Now, starting at the login prompt, the screen flashes about every second, occasionally freezing for a minute or two.  When flashing, it goes completely black, then back to the display, and then black again.  I'm lucky I'm not epileptic.

I was hoping I could get past this and continue my upgrade to 17.04, but that now fails with the message:

"[/COLOR]Calculating the changes

Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu"

I don't think any of these applies, but I'm pretty much stuck now.  Is there a recommended course of action for where to go from here?  Am I going to need to do an install from scratch?

---

### Post by oldfred on 2017-04-14
Was/Is your 16.04 fully updated?
Are you running any propriety graphics like nVidia or AMD? Or other drivers?

I typically keep the most current LTS version as my main working install.
And then install in a separate 25GB / (root) partition anything I want to experiment with.

---

### Post by llanitedave on 2017-04-14
Hmm, yes I did have an Nvidia graphics driver installed, although I thought I had disabled third-party software prior to the upgrade.  Maybe that wasn't what I did.  The system was definitely up to date.

I went ahead and did a reinstall, and Ubuntu is back to working normally.  The KDE side, though, still seems very unstable, and as much as Plasma 5.9 has been hyped lately, I fear it still may be to buggy to be usable.

---

### Post by RobGoss on 2017-04-15
Can I ask why would you want to upgrade from **16.04.2 **"LTS" to **16.10**, which will be it's end of life in about two more months or so. Trying to upgrade using the internal upgrade method doesn't work very well in my opinion

I think a clean installation is the bet way to go it will save you a lot of time and trouble

---

### Post by llanitedave on 2017-04-16
> **RobGoss said:**
> Can I ask why would you want to upgrade from **16.04.2 **"LTS" to **16.10**, which will be it's end of life in about two more months or so. Trying to upgrade using the internal upgrade method doesn't work very well in my opinion

I think a clean installation is the bet way to go it will save you a lot of time and trouble

My intent was to upgrade to 17.04, so that I could have access to Kubuntu with Plasma 5.9.  I fell for the hype,essentially. But since you ca't leapfrog versions in an upgrade, I had to upgrade to 16.10 first.  And everything fell apart before I could take the next step to 17.04, so I had to fall back to a clean install.  It's working now, and I'm using Kubuntu, but there's definitely a learning curve.  I prefer Unity, but since it's going away, I need to get accustomed to my chosen alternative.

---

### Post by Perfect Storm on 2017-04-17
You could set kde to look like unity with globalmenu and forth: [https://store.kde.org/p/1167950/](https://store.kde.org/p/1167950/)

---

