---
title: "Karmic stuck in a loop at login"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by K7AAY on 2009-10-17
Karmic boots, shows the splash screen, prompts for my password, then blinks, clears the screen, and again prompts for my password. How might I look into what causes this? Worked fine for about a week, with the only prior problem random lockups (solved today by doubling the RAM to 1GB in my HP Pavilion xe2113us, which survived four passes through MEMTEST, six hours and three reboots before the loop problem occurs).


> **louieb said:**
> Have you been using** sudo **when you should be using **gksudo** for graphical apps?
That can cause problems with xorg. Check the owner of ~/.Xauthority - change it back to you if its not.

I went to Recovery Mode through GRUB, but could not find .Xauthority in my root. 
Thank you, all, for your attention to this problem.

---

### Post by kansasnoob on 2009-10-17
I'd try starting in recovery mode. If the boot menu is hidden, which is common if you have only one operating system installed, and if this was an upgrade from Jaunty running legacy grub you should be able to view the boot menu by pressing the ESC key just after the system screen passes, whereas if it's a fresh install running grub2 you'll need to press the Shift key to display the menu.

Once you get the boot menu to show up you should see a recovery mode for each installed kernel, so choose to boot into recovery mode for the latest kernel, and let it run watching for text describing possible errors or problems. Make notes, being able to fully describe a problem is very helpful on the forums.

When recovery mode is finished you'll be dropped to a screen with several options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd first run dpkg, then when it's complete run xfix, and then try to resume boot.

---

### Post by K7AAY on 2009-10-17
> **kansasnoob said:**
> I'd try starting in recovery mode. If the boot menu is hidden, which is common if you have only one operating system installed, and if this was an upgrade from Jaunty running legacy grub 

Was a new install, not an upgrade

> you should be able to view the boot menu by pressing the ESC key just after the system screen passes, whereas if it's a fresh install running grub2 you'll need to press the Shift key to display the menu.

Once you get the boot menu to show up you should see a recovery mode for each installed kernel, so choose to boot into recovery mode for the latest kernel, and let it run watching for text describing possible errors or problems. Make notes, being able to fully describe a problem is very helpful on the forums.

When recovery mode is finished you'll be dropped to a screen with several options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd first run dpkg, 

292 upgraded packages and 5 new packages underway now.> 

then when it's complete run xfix, and then try to resume boot.

Will report again when dpkg finishes.

---

### Post by kansasnoob on 2009-10-17
Wow! You may be able to skip the xfix.

---

### Post by louieb on 2009-10-17
> but could not find .Xauthority
Just looked at my Karmic install home directory. 
I have  ~/.Xauthority in my Hardy install (v8.04), but not in  Karmic.   

Hope the dpkg and/or  xfix works. Good luck.

---

### Post by K7AAY on 2009-10-18
> **kansasnoob said:**
> Wow! You may be able to skip the xfix.

now I have Linux 2.6.31-14 in grub, but the same problem persists.  will now try xfix as dpkg didn't help.

---

### Post by K7AAY on 2009-10-18
> **louieb said:**
> Just looked at my Karmic install home directory. 
I have  ~/.Xauthority in my Hardy install (v8.04), but not in  Karmic.   

Hope the dpkg and/or  xfix works. Good luck.

There is *no* xfix on the recovery menu now. 

What do I do now?

---

### Post by kansasnoob on 2009-10-18
Yipes! I've never seen that happen, are you sure you can't "arrow down or arrow up" to find xfix?

Do you know what graphics card you have?

---

### Post by K7AAY on 2009-10-18
> **kansasnoob said:**
> Yipes! I've never seen that happen, are you sure you can't "arrow down or arrow up" to find xfix?

Very sure. I rebuild laptops for Freegeek.org and have taught there. Very familiar with 8.04LTS and somewhat surprised there's such a difference in Karmic.

> Do you know what graphics card you have?

ATI Radeon Xpress 200M


And, thank you, kansasnoob, for following me through this. I am surprised at the lack of response from others here.

---

### Post by Mercury_Alpha on 2009-10-18
Have you done any partial upgrades recently? Beta Ubuntu builds will often prompt you to do this, and they end up installing new packages whose dependencies have not been updated, causing a conflict. Also, "old" packages are sometimes removed during a partial upgrade, to prevent a conflict -- but no replacements are installed, which can break the boot-up chain or cause problems elsewhere.

You also mention that adjusting your RAM seemed to temporarily fix the problem. You may want to consider lowering the speed of your RAM. I was having all kinds of weird glitches until I lowered my RAM from 400MHz to 333MHz (which is annoying, since all my sticks are rated for 400MHz).

If the problem turns out to be caused by a partial upgrade, you're probably going to have to go through your recent apt logs, looking for updates that removed packages. Then identify what packages were installed in those partial upgrades, remove them, re-install the versions you had before the partial upgrades, and re-install the packages that were removed when you did those partial upgrades.

Edit: Alternatively, you can wait a couple more days until the RC is released, then burn that ISO to a CD and install it. However, this method relies on having a separate /home partition, since you would be using the RC to replace your root partition (and whatever  other non-/home partitions you may have manually created).

---

### Post by K7AAY on 2009-10-18
> **Mercury_Alpha said:**
> Have you done any partial upgrades recently? Beta Ubuntu builds will often prompt you to do this, and they end up installing new packages whose dependencies have not been updated, causing a conflict. Also, "old" packages are sometimes removed during a partial upgrade, to prevent a conflict -- but no replacements are installed, which can break the boot-up chain or cause problems elsewhere.<snip>

If the problem turns out to be caused by a partial upgrade, you're probably going to have to go through your recent apt logs, looking for updates that removed packages. Then identify what packages were installed in those partial upgrades, remove them, re-install the versions you had before the partial upgrades, and re-install the packages that were removed when you did those partial upgrades.

Not having the GUI editors I know makes that very problematic.

> Alternatively, you can wait a couple more days until the RC is released, then burn that ISO to a CD and install it. However, this method relies on having a separate /home partition, since you would be using the RC to replace your root partition (and whatever  other non-/home partitions you may have manually created).

If I boot from a Live CD, may I copy what's in /home off to an external USB attached HD?



> You also mention that adjusting your RAM seemed to temporarily fix the problem. 

It fixed another problem, not this problem.

> You may want to consider lowering the speed of your RAM. I was having all kinds of weird glitches until I lowered my RAM from 400MHz to 333MHz (which is annoying, since all my sticks are rated for 400MHz).

I don't see that I have that capability in the CMOS settings of this HP Pavilion ze2113us laptop. Can that be adjusted within Linux?


And, thank you, Mercury Alpha, for both the thoughtful responses as well as the chuckle from your profile pic.

---

### Post by kansasnoob on 2009-10-18
> **Mercury_Alpha said:**
> Have you done any partial upgrades recently? Beta Ubuntu builds will often prompt you to do this, and they end up installing new packages whose dependencies have not been updated, causing a conflict. Also, "old" packages are sometimes removed during a partial upgrade, to prevent a conflict -- but no replacements are installed, which can break the boot-up chain or cause problems elsewhere.

You also mention that adjusting your RAM seemed to temporarily fix the problem. You may want to consider lowering the speed of your RAM. I was having all kinds of weird glitches until I lowered my RAM from 400MHz to 333MHz (which is annoying, since all my sticks are rated for 400MHz).

If the problem turns out to be caused by a partial upgrade, you're probably going to have to go through your recent apt logs, looking for updates that removed packages. Then identify what packages were installed in those partial upgrades, remove them, re-install the versions you had before the partial upgrades, and re-install the packages that were removed when you did those partial upgrades.

Edit: Alternatively, you can wait a couple more days until the RC is released, then burn that ISO to a CD and install it. However, this method relies on having a separate /home partition, since you would be using the RC to replace your root partition (and whatever  other non-/home partitions you may have manually created).

If you'd bother to read you'd see that the OP had nearly 300 updates after running dpkg! No partial update was involved.

To me this is clearly an X problem. Sadly documentation regarding the Karmic version of X is either lacking or I'm too stupid to find it.

If the prior "we" need to fix it, if the latter I'm just screwed!

---

### Post by kansasnoob on 2009-10-18
> **K7AAY said:**
> Very sure. I rebuild laptops for Freegeek.org and have taught there. Very familiar with 8.04LTS and somewhat surprised there's such a difference in Karmic.



ATI Radeon Xpress 200M


And, thank you, kansasnoob, for following me through this. I am surprised at the lack of response from others here.


Sorry I've found no solution, but this is why I "multi-boot". I can keep at least one stable OS on my machine and if one lets me down I can just boot into another.

---

### Post by Mercury_Alpha on 2009-10-18
> **kansasnoob said:**
> If you'd bother to read you'd see that the OP had nearly 300 updates after running dpkg! No partial update was involved.

Yes, I did "bother" to read it. Because one particular update involves X number of packages does not mean that an *earlier* upgrade was not a partial or otherwise problematic. His issue predates doing the dkpg recommended in this thread, so the results of that dpkg are not necessarily related to the symptoms of his issue.

---

### Post by K7AAY on 2009-10-18
> **Mercury_Alpha said:**
> Yes, I did "bother" to read it. Because one particular update involves X number of packages does not mean that an *earlier* upgrade was not a partial or otherwise problematic. His issue predates doing the dkpg recommended in this thread, so the results of that dpkg are not necessarily related to the symptoms of his issue.

I didn't do any partials. 

The preceding problem of random freezes, I think was not related to the login problem. IMHO.

Everyone here is helping, and I am grateful to you both for your help.

---

### Post by VMC on 2009-10-18
I have .Xauthority file on my sytem and its just an empty file.
Look at ".xsession-errors" and ".xsession-errors.old" for any pertinent information. Their inside you home dir.

Here's any thought. I wonder if gdm is messed up. 

```
$ aptitude show gdm|grep Ver
Version: 2.28.0-0ubuntu19

```

You might just uninstall it then re-install it.

During your 290+ package updates, did anything stand out? Did you follow it through a terminal?

I use ```
sudo aptitude update && sudo aptitude full-upgrade
``` I watch each and every piece of update going by. I check before hand to see what's getting installed or updated.
After everything gets download I make sure everything is installed correctly. Sometimes I even copy & paste into a text editor and slowly go over what happened at a slower pace. Just to make sure.

Another thought. Someone else recently had a defective video card that drove him nuts until he replaced it with an older one to test, and that one worked. That pavilion is probably a laptop so that won't work. Another test would be to fire up the livecd and just use the cd for a few minutes. Just to make sure it doesn't freeze up. Then check what the cd and karmic found using lspci.

---

### Post by kansasnoob on 2009-10-18
> **Mercury_Alpha said:**
> Yes, I did "bother" to read it. Because one particular update involves X number of packages does not mean that an *earlier* upgrade was not a partial or otherwise problematic. His issue predates doing the dkpg recommended in this thread, so the results of that dpkg are not necessarily related to the symptoms of his issue.

Sorry for the "snark". That's never appropriate.

However far too many recent problems are getting passed off as "partial upgrade"issues.

Regardless, I apologize, bad behavior is always wrong and I behaved badly.

---

### Post by kansasnoob on 2009-10-19
Latest thoughts:

(1) Try booting into a previous kernel.

(2) From recovery mode go to "netroot" and run the command:

```
sudo apt-get install xorg-driver-fglrx
```

Then reboot again.

If it fails try recovery mode again ......... and xfix (if it's there). If there is no xfix try netroot and the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

AMD really dropped the ball as far as ATI support and they really don't seem to give a ****!

That said I'm experiencing the same response regarding support for my sound card. It worked great in Gutsy, Hardy, Intrepid, and Jaunty. Now it's like, "so sad, you're screwed"!

---

### Post by K7AAY on 2009-10-19
> **VMC said:**
> I have .Xauthority file on my sytem and its just an empty file. Look at ".xsession-errors" and ".xsession-errors.old" for any pertinent information. They're inside you home dir.

Here's any thought. I wonder if gdm is messed up. 

```
$ aptitude show gdm|grep Ver
Version: 2.28.0-0ubuntu19

```

You might just uninstall it then re-install it.

That's the version I have.

sudo apt-get --purge remove gdm
sudo apt-get -autoremove
    {reboot}
sudo apt-get install gdm

Same problem as before... plus now the LCD monitor is out of sync.

> During your 290+ package updates, did anything stand out? Did you follow it through a terminal?

Yes,  and no, nothing *I* recognize as *unusual* but it flew by pretty fast.  Henceforth, I pipe the output to a text file, fer sure.> 

I use ```
sudo aptitude update && sudo aptitude full-upgrade
``` I watch each and every piece of update going by. I check before hand to see what's getting installed or updated.
After everything gets download I make sure everything is installed correctly. Sometimes I even copy & paste into a text editor and slowly go over what happened at a slower pace. Just to make sure.

Another thought. Someone else recently had a defective video card that drove him nuts until he replaced it with an older one to test, and that one worked. That pavilion is probably a laptop so that won't work. Another test would be to fire up the livecd and just use the cd for a few minutes. Just to make sure it doesn't freeze up. Then check what the cd and karmic found using lspci.

Next step on the menu.

---

### Post by K7AAY on 2009-10-19
> **kansasnoob said:**
> Latest thoughts:

(1) Try booting into a previous kernel.

(2) From recovery mode go to "netroot" and run the command:

```
sudo apt-get install xorg-driver-fglrx
```
kernel 2.6.31-11-ge
Error! Your kernel source for kernel 2.6.31-11 generic cannot be found at /lib/modules/2/6/31-11-generic/build or /lib/modules/2/6/31-11-generic/source.

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree. You must run a dkms build for kernel 2.6.31-11-generic (i686) first. 

> 

Then reboot again.

If it fails try recovery mode again ......... and xfix (if it's there). 

 Still no xfix> 

If there is no xfix try netroot and the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

     Package 'xserver-org' is not installed and no info is available.

sudo apt-get install xserver-org

     Couldn't find package xserver-org

-

Still no joy.

---

### Post by kansasnoob on 2009-10-19
Arrrgh! Color me stumped.

---

### Post by Victormd on 2009-10-19
I'm having the same issues (mythbuntu/xfce beta) - just ran into this thread today so I'm going to try some of the steps when I get home and see what I come up with - just a note, the last upgrade/update I did WAS a partial upgrade...

Switching to tty6 and sudo apt-get update shows that I have 15 packages that need to be installed but can't install them without the GUI (not sure why)...

My main problem here is that I'm used to gnome not xfce and the location of some of the system files that my limited knowledge allows me to check, I can't find...

---

