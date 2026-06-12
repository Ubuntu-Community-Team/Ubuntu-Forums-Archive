---
title: "How will additional installation affect grub?"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by nickdc on 2012-01-06
I've already got WinXP and Ubuntu 11.10 happily dual booting, both on my main sytem drive: C / sda. I now want to do a further installation of Ubuntu Studio 10.04 (ie older release) onto a separate hard drive (E / sdd) which is formatted NTSF but has loads of unallocated space on it. I assume I can do this by choosing the manual partitioning option during the install process. But will the installer automatically find the existing grub on sda and simply add the new Ubuntu Studio boot option to it (which is what I want)? If not, how do I achieve this?

---

### Post by drs305 on 2012-01-06
I believe the latest versions of Ubuntu still require Grub to be installed (a sore point with some 'power' users). Although there are a few ways to work around this (such as installing Grub to a partition instead of the MBR), the safest and probably best approach is to let Grub install itself. 

If you have the opportunity to install it only to the MBR of the new installation's drive (sdd) do that. Make sure the BIOS still boots from your main drive and you may still have your original Grub controlling things.

Otherwise, after the new installation:
Select your older/original Ubuntu version at boot. Run the first command to put controll of the boot back to the original OS (assuming sda is the designation of your original Ubuntu installation). Run the second command to add the new OS to the original Grub's menu:
```
sudo grub-install /dev/sda
sudo update-grub
```

Watch for upgrades when running your secondary Ubuntu. Certain updates may revert control back to that version's Grub. If it happens, rerun the commands above. 

Note: You can tell which Grub is controlling the boot by noting the first entry on the Grub menu. You might want to add a background image for one or both so you can tell more easily.

---

### Post by darkod on 2012-01-06
No, the installer by default installs its grub2, it doesn't care about other OSs including ubuntu.

If I remember correctly 10.04, what you need to do is: you do the install as normal until you reach the last step/screen. There should be Advanced button. Click it and you will have an option not to install a bootloader (to untick the box). Only after you have done that click the Install button to start the install.

On first boot you will not see Studio in the menu, your 11.10 is still not aware of it. Just boot it and run:
sudo update-grub

It will create option for Studio in the menu.

---

### Post by drs305 on 2012-01-06
I think *darkod* is correct that 10.04 is far enough back that the Advanced tab still offered the option not to install Grub (2). Look for the Advanced option during the latter part of the installation - it's easy to overlook it.

---

### Post by nickdc on 2012-01-06
Thanks, guys, I'll give it a whirl.

---

### Post by nickdc on 2012-01-07
Uh! Can't get the installation to start! Am I missing something here?

First, the downloaded iso image I'm using for Ubuntu Studio 10.04 is called "alternate install dvd". It's the only one I can find and seems very official, but I don't understand what it's alternate *to* ... Does it need special treatment, because ...

Second, it doesn't boot. I've run a check and the data seems ok, but I've tried it in two different drives and neither brings any result. However, once Ubuntu has booted up normally from the hard drive, the install dvd shows up ok (not automatically; it has to be found in Computer), and clicking on it opens it and brings up a message saying it contains software packages and do I want to upgrade. So far I've always cancelled at this stage, in case it then starts to install over the current version on the current drive. Is this correct. The other possibility is that if I click yes i'll get what I'm after, a full install option. Please could I have some guidance on this?

PS I've just had a thought: though my bios is set to boot from cd as its second option, is it possible that being an old machine it can't boot from a dvd? If so, is there anything I can do about this?

---

### Post by darkod on 2012-01-07
Is the image ubuntustudio-10-04-alternate or ubuntu-10-04-alternate? If it says only ubuntu that's the desktop system, only the alternate install image.

Look here for Studio 10.04 images:
[http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/)

---

### Post by nickdc on 2012-01-07
No, it is the ubuntu studio one, from exactly the page you linked to. What should I do?

---

### Post by darkod on 2012-01-07
What do you mean the bios is set to boot from cd-rom as second option? It needs to be first so you boot from the cd not the hdd.

Another option is that you didn't burn the cd correctly. Did you make sure you burn it from image, not just copy files on it?

---

### Post by nickdc on 2012-01-07
I've just tested the install dvd in a laptop and it works fine, booting straight from the dvd into the installation screen, so clearly I've got a hardware or BIOS issue with my desktop machine. Any suggestions? In particular, can someone kindly tell me which file in which folder is the one that kicks everything off (I'm showing my ignorance of Linux here, but in Windows I'd be able to find the relevant setup.exe or whatever; is there an equivalent in Linux???), as maybe I could then run from that. And I'd also be grateful to an answer to one of my original questions: if I choose the option to "upgrade" when the "disk containing software packages" (ie the installation dvd) is detected, will I get an option to do a full install on a different drive or will it start straight away trying to 'upgrade' my current, newer, Ubuntu?

---

### Post by nickdc on 2012-01-07
> **darkod said:**
> What do you mean the bios is set to boot from cd-rom as second option? It needs to be first so you boot from the cd not the hdd.

Another option is that you didn't burn the cd correctly. Did you make sure you burn it from image, not just copy files on it?

Sorry - floppy drive is option 1, cd option 2, hdd option 3

See my previous post (which seems to have crossed with yours) re the authenticity of the dvd.

Thanks for trying to help.

---

### Post by darkod on 2012-01-07
If you click Upgrade it will try to upgrade your ubuntu.

The point of bootable CDs is that you need to boot from them, you can't simply run them. Even for windows running setup.exe works for programs but not for installing windows itself.

You need to find a way to boot your computer from the DVD, it should be able to do that.

---

### Post by nickdc on 2012-01-07
> **darkod said:**
> If you click Upgrade it will try to upgrade your ubuntu.

The point of bootable CDs is that you need to boot from them, you can't simply run them. Even for windows running setup.exe works for programs but not for installing windows itself.

You need to find a way to boot your computer from the DVD, it should be able to do that.


Thanks, that clarifies things. I'm going to try burning the iso image to a different type of dvd,  (- instead of +) in case that makes a difference. If not I'll try the usb route, though that is likely to be a headache as my machine way predates booting from usb and I'm pretty sure the BIOS won't allow it. Whichever way, I'm obviously in for a long haul!

---

### Post by nickdc on 2012-01-07
Finally got there ... almost! 

At about the fifth attempt the dvd did finally boot and I got into the installation process, only to have to abort it when installation of base packages failed. Gave up after two more failed attempts and downloaded Ubuntu Studio 8.04 instead. This did install, without too much difficulty, and is now up and running (thanks for the advice re what to do about grub, which has worked a treat). However, the software I particularly want to run (Kdenlive) isn't available for 8.04, so I want to upgrade it to 10.04 (my original objective). How do I do this? The update manager tells me 10.04 is available, but it refers to Ubuntu, no mention of Studio. How do I ensure it's the full Studio packages that get upgraded?

---

### Post by darkod on 2012-01-07
Sorry, I haven't worked with Studio at all. But if you boot your Studio 8.04 and it says 10.04 is available, if you start the upgrade the logic is that it should upgrade to Studio 10.04 not Ubuntu 10.04.

Another way for a command line upgrade (which might give more details during the process) is to run in terminal:
sudo do-release-upgrade

But not sure if that command goes so far back to 8.04.

---

### Post by nickdc on 2012-01-08
Thanks, darkod, you've been a great help on this one. Before I run the upgrade I'll do a bit more reading on the Studio Forum - there should be something over there, though a post I made there a few days ago before starting this new install got only one reply! That's partly why I came here when I ran into problems installing it. But I'll perhaps try again, though it seems Studio is somewhat in the doldrums at the moment . Pity.

---

