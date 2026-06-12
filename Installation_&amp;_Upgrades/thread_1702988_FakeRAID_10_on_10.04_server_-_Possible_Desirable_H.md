---
title: "FakeRAID 10 on 10.04 server - Possible? Desirable? How to?"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by thenatman on 2011-03-08
Hi everyone!
Long time lurker first time poster. I'm writing today to ask about RAID, specifically fakeRAID, and I hope this is the right place to do so. My company recently purchased PC components for a server, which a coworker and I recently assembled. We hope to put Ubuntu 10.04 server on it, and although I know this isn't the newest version, this is being requested for compatibility reasons. The motherboard is an ASUS M4A89GTD Pro, and the hard drives are four one-terabyte Western Digital drives.

My supervisor has requested a RAID-10 setup, specifically one "configured via the BIOS", which I take to mean fakeRAID (this may in fact be my first mistake?). As I have not set up a RAID array before, off to Google I went. One of the first articles I came across was this one, which, while potentially informative, was somewhat daunting off the bat:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

At the top, in big red letters:  [COLOR=Red]**"FakeRAID is not supported by Ubuntu. Trying to install Ubuntu on such a  partition could easily result in the loss of all your data."**

[COLOR=Black]OK Jose. But then I found this:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

[/COLOR][/COLOR]**Dmraid active by default on Desktop CD**

 Dmraid  "fake raid" devices are supported out-of-the-box on the Ubuntu 10.04  LTS Desktop CD, and are detected and activated by dmraid on boot.  Ubiquity will offer to install on the RAID array, and not on the RAID  members. 
The  automatic activation of dmraid can be disabled with the "nodmraid" boot  option, available by pressing F6 in the CD boot menu. This can be  useful for setups which have fakeraid metadata present on the disks, but  where dmraid activation would be undesired or cause problems. 
[COLOR=Red]
[COLOR=Black]
Hmm, this apparently contradicts the first statement. Looking closer, this applies specifically to the Desktop edition, but I do not know why they would support fakeRAID for desktops and not servers, if this is indeed the case?

Then I found this:
[https://bugs.launchpad.net/ubuntu/lucid/+source/grub-installer/+bug/568050](https://bugs.launchpad.net/ubuntu/lucid/+source/grub-installer/+bug/568050)

So it's a bug?!

Well, in short, my supervisor seemed pretty set on "configuring it in the BIOS", whatever this can be taken to mean. 

Out of desperation, and receiving somewhat conflicting results, I tried to do it on my own. I went into the BIOS, set up SATA 1-4 to be RAID drives, restarted, and popped in the 10.04 server install disk.

After saying that I had a RAID setup, the installer took me to the partition screen, where I was presented with...nothing. The dialog said "below is your partition scheme", and nothing was displayed. If i attempted to continue, the system complained about lacking a boot volume. 

So I went back two steps, unchecked "I have a RAID setup", and attempted to go from there. Quasi-success?! After proceeding a few steps, it complained "Unknown file system",  and a shell prompt appeared with the error "GRUB recovery". 

Using the BIOS again, I ran an erase tool, which only recently finished.

Now I am unsure where to go. Is this indeed a FakeRAID setup? Is FakeRAID supported by 10.04 server? If so, is it indeed preferable to a pure softRAID? Also, how would I set up a fakeRAID?

If Fakeraid is not preferable, is this how I would do a softRAID?:
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

Sorry to throw so many questions at you! Admittedly I am quite confused. We are a small company with very little experience, and incidentally our supervisor is out for the next few days sick, and though it seems that he's more knowledgeable, he wouldn't be able to help. I appreciate any guidance you can provide. 



[/COLOR][/COLOR]

---

### Post by ronparent on 2011-03-08
First off, I have installed 10.04 desktop on a raid0. As you found, the FakeRAIDHowTo has not been updated for 10.04 on and should be disregarded.

There was a regression in that a bug in gparted distributed with 10.04 impeded the installation necessitating applying a workaround. That workaround involved merely booting the cd to a live session and installing kpartx to the session to permit gparted to see the raid drive. The installation could then be performed within that same live session by starting the installer and selecting the manual partitioning option during the partitioning step. Without the workaround you get a failure in formating the target drive as you experienced. 

The next hurdle was that grub2 was usually not properly installed with the boot loader portion on the raid as the boot device. That could be immediately fixed by opening a terminal window within the same session and reinstalling grub 2 using the two step method outlined (see **[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2**). Just remember that the root partition you are mounting to the /mnt location is the raid partition you just installed to. And, if you are booting off the raid the target for the boot loader in the second step is the raid drive itself as given by **ls /dev/mapper** (the first item listed after control). It is all really simple once you have worked through the inherent limitation inadvertently built into 10.04.

Finally be sure the raid10 level is supported for the specific raid chipset you are using on your MB (type **dmraid -l** in a terminal). You didn't say and I couldn't determine from the Newegg site. Just because it is supported in windows doesn't mean it is supported by dmraid. The activation of the raid give a clue as to which chipset the raid is operating on (ie **sudo dmraid -ay**).

I know this is more complicated than it should be but post if you have more questions. Good luck.

Note: is there a specific reason you are using the fakeraid approach as opposed to using a linux software raid? Unless you are needing windows access to the raid drives there is no compelling reason to depend on the MB chip set.

---

