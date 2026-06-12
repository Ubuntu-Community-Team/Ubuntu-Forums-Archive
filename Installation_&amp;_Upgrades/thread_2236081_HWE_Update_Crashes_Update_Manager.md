---
title: "HWE Update Crashes Update Manager"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by eldavar on 2014-07-24
Hello everyone! Update Manager tells me "New hardware support is available".

[IMG]http://goo.gl/Op9HJl[/IMG]

 Clicking the Install button in Update Manager opens the above message explaining that my HWE will no longer be supported after 8/7/14. But, when I click the Upgrade button, Update Manager returns a message stating "Package dependencies cannot be resolved". 

[IMG]http://goo.gl/TMfb4S[/IMG]

A few seconds after the above message pops up, Update Manager crashes. I looked in the System Log Viewer, but there's nothing about Update Manager in there, and I don't know where else to look for the error log. 

Can someone tell me what to do now?

---

### Post by eldavar on 2014-08-01
I decided to look into just installing the unmet dependencies to resolve this. I looked up the first one in Synaptic. 

[IMG]http://goo.gl/Klb9ss[/IMG]

[IMG]http://goo.gl/Qjtwl1[/IMG]

But, when I tried to mark it for installation, the box showing what other packages would also be installed/removed contained a gigantic list of packages! 

[IMG]http://goo.gl/AJ7Hvh[/IMG]

I'm still only a Linux/Ubuntu beginner, so when I saw a bunch of xserver and xorg video packages about to be removed, plus the ubuntu desktop, and even xorg itself, I got nervous. And this was after looking in Synaptic for just the FIRST missing dependency, not to mention that this all started as the result of an error in the update manager. I chose not to proceed with this until I can get some legitimate feedback from an expert. So, is anyone familiar with this? Can you explain some of this to me? Why does it look like so much will be removed? The "to be installed" list is only a handful of packages, so that doesn't seem right either.

---

### Post by kansasnoob on 2014-08-01
Please first run:

```
sudo apt-get update
```

Then post the full output of:

```
sudo apt-get -f install
```

Please wrap the text in code tags using the # at the top of the reply window.

That may provide some clues.

---

### Post by Fiery Spirited on 2014-08-05
I suffer from the same problem and is trying to decide what to do. This whole HEW update seems like a mess. Despite a lot of googling I am still to find a real benefit of having the new HWE, the whole LTSEnablment stack stuff is only for 32-bit computers so the only thing it means for me with a x64 computer is that since I happened to chose 12.04.04 when I installed the computer I must switch kernel despite my computer works very fine already with the current kernel. Had i taken 12.04.01 then I would not had any problems. 

I don't understand why I, who is a deliberate LTS user, should have to deal with this. In practice the only true LTS version is 12.04.01 but this is only clear if you read the small print at the page describing the releases. Currently I am leaning towards avoiding the upgrade until Canonical sort out what is wrong, but make sure I do a full backup. If they force the upgrade on me in two days I will need to reinstall anyway if they have not solved the problem so hopefully they will have it resolved by then I can avoid the hassle.

Anything...enough of ranting. 
One thing I noticed is that the version conflicts for me is of the style 2:1.4.99.1 vs 2:1.4.99.1-0ubuntu2.2 
Your version conflicts seems to be the similar...the package contain references that have a suffix that seems to prevent the package manager to realize it in fact the same version number. If Synaptic acutally manage to install the updated package I think there is a real risk that other packages afterward will have the reverse problem (expecting the version without the suffix).

Possibly the suffix is termporary so that Ubuntu can make the transition to the new kernel and that the regular references will be reinstalled afterwards. In any case I don't think there is any good solutution besides Cannonical fixing the upgrade packages so that it works. Switching kernel version to 3.13 is major change to the system so I would not trust getting the right stuff by manually pulling stuff with Synaptic that is claimed to be missing.

---

### Post by grahammechanical on 2014-08-05
I have seen many threads like this one over the last two weeks. Do not upgrade. That is my advice. I put in an installation of 12.04.4 just to test out this HWE upgrade on my machine and everything worked fine. But others have had a different story to tell. Actually what you are being offered is an early preview of the Hardware Enablement Stack that will be in Ubuntu 12.04.5 when it is released about a day before that warning runs out. Upgrade to 12.04.5 and keep all fingers crossed.

This link gives some explanation. Notice the last chart but one (Ubuntu Kernel Support) and the meaning of EP = Early Preview

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by eldavar on 2014-08-06
The results of ```
sudo apt-get -f install
```don't reveal anything:```
greg@greg-ubuntu:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

