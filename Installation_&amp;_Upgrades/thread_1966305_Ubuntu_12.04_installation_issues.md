---
title: "Ubuntu 12.04 installation issues"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Soupy Twist on 2012-04-26
Hi, I tried upgrading from 64-bit Oneiric Ocelot to Precise Pangolin earlier on my laptop, and after what seemed like an eternity and a half, it finished and restarted, I logged in, the top bar and the Unity bar showed up, but the Unity bar's icons were all blank, and I also couldn't move my mouse. I shut down and restarted it, only to find that it still didn't work. Thankfully, I'm still able to boot into Windows 7, the primary OS on my laptop.

Anyway, I'm trying to figure out how I'm going to go about fixing Ubuntu 12.04. One idea I have is getting rid of it completely, removing the partition and GRUB, and re-installing from a disk, but I don't know exactly how to go about doing that without screwing everything up. I apparently need a Windows 7 installation disk to do that, which I was never given with the purchase of this laptop.

If anybody can help, please do so.

---

### Post by cadiolis on 2012-04-27
I'm having a similar issue.  Just installed Precise and upon logging in the unity panel is essentially missing.  If I use the super key I can see the dash but no panel.

Also, all of my windows are launching at the top with a height of zero.  I have to expand each one.  Super annoying

---

### Post by jadtech on 2012-04-27
the update hasnt finished there are lib files that couldn't install
if you can get to a term window try to continue using sudo apt-get

---

### Post by Soupy Twist on 2012-04-27
> **jadtech said:**
> the update hasnt finished there are lib files that couldn't install
if you can get to a term window try to continue using sudo apt-get
Well, why would they release the update unfinished? That's just completely stupid. Anyway, what's the key combination for opening a Terminal window, and what should I search for with apt-get?

---

### Post by jadtech on 2012-04-27
its not unfinished something happened during the down load  and or unpack aging  something didn't unpack right the install got out of order cause dependency issues..

---

### Post by jadtech on 2012-04-27
try sudo apt-get update
sudo apt-get upgrade 
no doubt there will be a list of a few if not several hundered

 easyer yet if you can get to the update manager  :)

---

### Post by jadtech on 2012-04-27
here is another in the same place as you  they got the upgrade to continue and finish , your not the only one with this issue  there is a known bug it just dont effect everyone 

[http://ubuntuforums.org/showthread.php?t=1966323](http://ubuntuforums.org/showthread.php?t=1966323)

---

### Post by Soupy Twist on 2012-04-27
> **jadtech said:**
> try sudo apt-get update
sudo apt-get upgrade 
no doubt there will be a list of a few if not several hundered

 easyer yet if you can get to the update manager  :)
It won't let me access the Terminal. I kept hitting Ctrl+Alt+T to no avail. And I can't move the cursor at all. I'll try booting in Recovery Mode and see if that works.

EDIT: Nope, that didn't work. I'ma need a fresh install from a disc. How do I go about doing so without rendering my entire laptop useless?

EDIT AGAIN: Tried fooling around a little more, found out that the key combo for Terminal is Ctrl+Alt+F1, was able to access the Terminal in Recovery Mode, it was glitchy in the regular mode, but none of the update/upgrade commands returned any sort of solution.

---

### Post by jadtech on 2012-04-27
> **Soupy Twist said:**
> It won't let me access the Terminal. I kept hitting Ctrl+Alt+T to no avail. And I can't move the cursor at all. I'll try booting in Recovery Mode and see if that works.

EDIT: Nope, that didn't work. I'ma need a fresh install from a disc. How do I go about doing so without rendering my entire laptop useless?

EDIT AGAIN: Tried fooling around a little more, found out that the key combo for Terminal is Ctrl+Alt+F1, was able to access the Terminal in Recovery Mode, it was glitchy in the regular mode, but none of the update/upgrade commands returned any sort of solution.

```
sudo apt-get dist-updgrade -f 
```

---

### Post by cancelledczech on 2012-04-27
Jadtech, thanks for the info on fixing the upgrade. I, too, had an incomplete install and this got me back up and running! Thanks.

---

### Post by Soupy Twist on 2012-04-27
> **jadtech said:**
> ```
sudo apt-get dist-updgrade -f 
```
Tried that, and all the other apt-get commands that would be relevant. And I tried them all with -f and --fix-(something, I forget the word it told me to use) but nothing worked at all. I'll just try them again, but it's looking like I need to get rid of everything and reinstall.

---

### Post by jroa on 2012-04-27
You can download the liveDVD .iso, burn it to a disk, and boot the disk.  Then, you can try jadtech's suggestions from the liveDVD.  It that still does not work, you could always use the live environment to re-install Ubuntu.  Grub will be updated in the process.

---

### Post by jroa on 2012-04-27
Oh, and I almost forgot.  You mentioned that you did not receive a recovery disk with your computer.  You can boot to Win 7 and make one.  I can't remember the exact process, but if you search help for "make recovery disk", you should get details.

---

### Post by trondhuso on 2012-04-29
I downloaded and burned a 12.04 64-bit CD and booted it. It does not show the menu that makes me choose Live CD or anything.

Anyone know why this happened? Could it be that the CD was wrongly burned?

Anything I can do to test? And where can report this if it is a bug?

---

### Post by jroa on 2012-04-29
If the 64 bit version is the correct one for your computer, you can check the .iso file to make sure it is not corrupt by doing an md5 checksum test.  If the .iso is good, then try _burning_ it to a disk.  I underlined burning because because you have to make a burned disk, not just a data disk.  When you burn it, make sure you do it at the slowest speed possible.  These steps should create a bootable disk.

If you need a recommendation for a checksum program or a disk burning program, let me know.

---

