---
title: "I KNOW 10.04 is not support - trying to upgrade"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2015-11-05
I know... I know... I know... 10.04LTS is no longer supported. If it ain't broke, don't fix it. Well, lately it's been broke - flash crashes firefox on any flash-based site. I am trying to upgrade, but it's not co-operating.

I tried "sudo apt-get dist-upgrade" and it just returns to the command line with out doing anything. 

I tried "Update Manager" but that just gives me a pop-up window that says "Your Ubuntu Release is Not Supported Anymore". I click close and it just freezes. If I move that window, I can see "Reading Database" on the window behind that, but it too is frozen. I have to click the 'X' on the main window and then force that to close. 

I tried "sudo do-release-upgrade" and that exits with "command terminated with exit status 1". The log scrolls so quickly that I cannot see specifically what is causing this, but I do see a lot of 'Ign" (ignore?) and "Err" (error?) instead of "Get" on the lines as they scroll by. 

I REALLY do not want to do a complete wipe and install. Is there anything I can do to actually UPGRADE? Thanks in advance.

---

### Post by v3.xx on 2015-11-05
What about EOL upgrade?

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by grahammechanical on 2015-11-05
My advice is to do a fresh install of Ubuntu 14.04.3.

Ubuntu 10.04 is at end of life. So, it cannot be updated and it is always risky to upgrade an OS that is not fully up to date. Likewise, it is also risky upgrading to a newer version from an OS that has problems. A fresh install, on the other hand, clears away the bad.

It is not the answer you are looking for, but it is the best advice. This wiki page will tell you how to do an End of Life upgrade but you may end up with a worse mess.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You should deactivate any proprietary video driver and reactivate the open source video driver. The change from 10.04 to 12.04 includes a change from the Gnome 2 desktop environment with its Gnome 2 panel user interface to the Gnome 3 DE with the Unity UI. And that is a big code difference. There will be a question mark over success of the upgrade.

Regards.

---

### Post by Bucky Ball on 2015-11-05
This might help, from [here]("http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release"), but I'm with grahammechanical: you may end up with a dog's breakfast. I'd back up and install an LTS, 14.04 LTS would suit you by the sounds. A lot has changed since 10.04, most notably the desktop environment and it's gonna have to happen sooner or later. ;) 

[QUOTE=rubo77]If you want to continue using an outdated release then edit /etc/apt/sources.list and change archive.ubuntu.com to old-releases.ubuntu.com

You can do this with sed

```
sudo sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

then update with

```
sudo apt-get update && sudo apt-get dist-upgrade
```[/QUOTE]

---

### Post by s9032g@comcast.net on 2015-11-05
I have done clean installs several times after poor results upgrading other ways. It isn't hard if a 75 year old can do it. Be sure to use an appropriate tool to clean your system out. For instance SSDs require different programs than hard drives. 

Back up what you need to and just go for it. You will get a trouble free result instead of something cobbled together that you will spend hours to fix.

---

### Post by rebeltaz on 2015-11-05
OK.. I tried the EOL suggestion and that didn't result any differently. 

No... reinstalling is not hard, per say... I do happen to be a computer technician although most of my 25+ years experience is in windoze. I've only been using linux for 5-7 years so I am far from an expert here! 

I had really hoped to avoid the whole "upgrade" path anyway as I do not like the new interface. That's why my one and only windows laptop still runs XP. 

As for ending up with a mess... well, I wouldn't be any worse off really. Either way, I'd be doing a fresh install. Sigh.... I guess I may have to just "do it"  :(

Thanks guys.

---

### Post by Dennis N on 2015-11-05
Ubuntu MATE has essentially the same user interface as Ubuntu 10.04 but with up-to-date software. Try it if you want to keep the look of 10.04.

On Ubuntu 10.04, did you kept Firefox upgraded? Are you using the latest version of flashplugin?

---

### Post by rebeltaz on 2015-11-05
I am looking into MATE now... thanks.

Yes.. Firefox is at the latest version as is flash. As usual, I think the last "update" screwed it up. It was working before that, albeit slowly.

---

### Post by Dennis N on 2015-11-05
> **rebeltaz said:**
> I am looking into MATE now... thanks.

Yes.. Firefox is at the latest version as is flash. As usual, I think the last "update" screwed it up. It was working before that, albeit slowly.

Could also be one of the old add-ons acting up if you have them.

If you install Ubuntu MATE, it will look VERY familiar to you.

---

### Post by rebeltaz on 2015-11-05
Oh... I forgot to say earlier that I completely removed all traces of flash and firefox and did a complete reinstall of that so, there shouldn't be any conflicts there...

The firefox in the repository refused to install for some reason but the one from the firefox site did install.

---

### Post by rebeltaz on 2015-11-05
GRRRRRR.....

OK... I wiped the harddrive and installed a completely fresh version of MATE 15.xx

First thing I did, after the system updated itself, was go to youtube. Nothing added, nothing modified... The freaking browser crashed again. Straight out of the box so to speak. WHAT IN THE ^&$( IS GOING ON!??

Thanks for MATE, though. I do like that. 

Any ideas?

---

### Post by v3.xx on 2015-11-05
See if you can upgrade your video driver.  Go to the last tab in software sources.

```
software-properties-gtk
```

---

### Post by rebeltaz on 2015-11-05
I'm not sure from the "software-properties-gtk" code, but under the "Additional Drivers" tab of 'Software and Updates' it found one proprietary driver and that isn't for the display. It says "using Processor microcode firmware for AMD CPUs from AMD64-microcode (proprietary)"

---

### Post by v3.xx on 2015-11-05
That code just takes you to the same place.

A suggestion

This thread has served its purpose and does not cover the current issue.  A new thread with current issue will draw  in the right viewers.

---

### Post by rebeltaz on 2015-11-05
:) I'll start a new thread... Thank you.

---

### Post by Bucky Ball on 2015-11-05
I really would advise a long-term support release or 15.10 looking at the fact you don't like to upgrade often. Installing 15.04 will see you doing it all again (albeit you can do it a lot easier this time) in January when you'll need to go to 15.10 and then to 16.04 LTS in April. Why not go for the latest interim release, 15.10, which is upgradeable directly to 16.04 LTS and avoid the upgrades from 15.04> 15.10> 16.04 LTS where you can then sit for a two years or more without worrying about upgrades. 

So, 14.04 LTS, supported until 2019, gives you time to put off an upgrade. LTS upgrades directly to the next LTS, 16.04 LTS, leapfrogging the interim releases in between. 16.04 LTS is supported for five years until 2021. Unsure if the LTS support for Mate is the same, but if not five years for LTS, it will be three, as 10.04 LTS was (LTS Ubuntu release is now five rather than three).

Just throwing that in.

---

