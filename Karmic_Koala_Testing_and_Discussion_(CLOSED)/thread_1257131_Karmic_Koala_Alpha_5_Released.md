---
title: "Karmic Koala Alpha 5 Released"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-03
Karmic Koala Alpha 5, the fifth milestone release leading to Ubuntu 9.10, has been released. 

The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the latest Alpha**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 

Here's Steve Langasek's announcement on the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"):

[QUOTE=Steve Langasek]Hello Ubuntu developers,

Welcome to Karmic Koala Alpha 5, which will in time become Ubuntu 9.10.

Pre-releases of Karmic are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 5 is the fifth in a series of milestone CD images that will be
released throughout the Karmic development cycle.  The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Karmic. You can download it here:

  [http://cdimage.ubuntu.com/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/releases/karmic/alpha-5/) (Ubuntu)
  [http://uec-images.ubuntu.com/releases/karmic/alpha-5/](http://uec-images.ubuntu.com/releases/karmic/alpha-5/) (Ubuntu Server for UEC and EC2)
  [http://cdimage.ubuntu.com/ports/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/ports/releases/karmic/alpha-5/) (Ubuntu ARM)
  [http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/) (Xubuntu)
  [http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/) (Mythbuntu)

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

Alpha 5 includes a number of software updates that are ready for large-scale
testing.  This is quite an early set of images, so you should expect some
bugs.  For a list of known bugs (that you don't need to report if you
encounter), please see:

  [http://www.ubuntu.com/testing/karmic/alpha5](http://www.ubuntu.com/testing/karmic/alpha5)

If you're interested in following the changes as we further develop
Karmic, have a look at the karmic-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/karmic-changes](http://lists.ubuntu.com/mailman/listinfo/karmic-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Enjoy,
-- 
Steve Langasek
On behalf of the Ubuntu release team

-- 
ubuntu-devel-announce mailing list
[email]ubuntu-devel-announce@lists.ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)[/QUOTE]

---

### Post by ELD on 2009-09-04
I hate to be a pain but in the known issues why is the ATi issue not mentioned, many of us cannot even boot.

---

### Post by 23meg on 2009-09-04
> **ELD said:**
> I hate to be a pain but in the known issues why is the ATi issue not mentioned, many of us cannot even boot.

Any particular bug numbers?

---

### Post by taavikko on 2009-09-04
> **23meg said:**
> Any particular bug numbers?

for example: [bug 419126](https://bugs.launchpad.net/bugs/419126)
Affects people running ATI r600 or higher chipsets.

---

### Post by ELD on 2009-09-04
> **taavikko said:**
> for example: [bug 419126]("https://bugs.launchpad.net/bugs/419126")
Affects people running ATI r600 or higher chipsets.

That is the one, and considering how popular those cards are (in ATi terms) it is a big number.

---

### Post by puccaso on 2009-09-04
cant we do something about chrome9 :(
karmic is of no use to me until chrome9 works, because everything depends on GL (well not everything but unr, clutter, gnome-shell and gnome-do)

cant we do something? please!

---

### Post by jerrylamos on 2009-09-04
ATI radeon mobility 7500 did boot the A5 CD.  I've a radeon Xpress 200 to try yet.

Intel i845 can't get anywhere.  It won't do anything at the first boot menu.

Intel i830 boot hung brown screen, no surprise, since intel drivers 2:2.8.0 and on don't boot on i830 or i845.  I couldn't find a "safe" mode that would work.

i830 install from first boot menu got well into install then got into a problem with copy?  So I did an install with A4 which went fine.

Oh, the updates to current level on karmic have been working, given I use "vesa" on the Intel's and don't use modeset=1 on the ATI's. 

The A5 CD is not so hot for me but I can get around it to get a running karmic anyway.

Jerry

---

### Post by VMC on 2009-09-04
> **jerrylamos said:**
> Intel i845 can't get anywhere.  It won't do anything at the first boot menu.

Intel i830 boot hung brown screen, no surprise, since intel drivers 2:2.8.0 and on don't boot on i830 or i845.  I couldn't find a "safe" mode that would work.

i830 install from first boot menu got well into install then got into a problem with copy?  So I did an install with A4 which went fine.

Oh, the updates to current level on karmic have been working, ..
The A5 CD is not so hot for me but I can get around it to get a running karmic anyway.JerryThis is what I'm afraid of. I have only downloaded A3 and do updates daily. I'm current, but have no way to know if I start from fresh A5 would anything work. The "nomodeset" I don't need anymore, but I still have the older Intel driver 2.4. At some point I will try to use the latest driver again and see what happens. Last time I tried this, it all blew up in my face. I'm using default xorg.conf or rather no xord.conf file.

---

### Post by andrewabc on 2009-09-04
Anyone missing icons in main menus? In submenus icons show up. Missing in Applications, and system. A couple icons missing from places near bottom.

Running alpha 5 from usb.

When I booted volume was turned down all the way.

The wired network icon in top right corner isn't that pretty. Just a black icon.

---

### Post by VMC on 2009-09-04
> **andrewabc said:**
> Anyone missing icons in main menus? In submenus icons show up. Missing in Applications, and system. A couple icons missing from places near bottom.

Running alpha 5 from usb.

When I booted volume was turned down all the way.

The wired network icon in top right corner isn't that pretty. Just a black icon.

There is a topic already on this. go to
System > Preferences > Appearance - Then Interface, Check "Show icons in menus"

---

### Post by noelvh on 2009-09-04
Well I upgraded one of my machines to give it a test, and it looks good sofar. It is not as fast as 9.4 on this system, but it is a bit older. I also was not able to get the intel graphic card working, even using the info for setting it up. I will keep testing it, but I like what I see!

Noel

---

### Post by puccaso on 2009-09-04
i remember reading somewhere, that in gnome 3 they were going to remove icons from buttons, because it is not "elegant" so i guess they're going to remove icons from menu's too, it makes it quite faster actually. .

---

### Post by leech on 2009-09-04
I hate to say it, but if they get rid of the icons in Gnome 3, I simply won't be using it.  After having Icons in menus for so long, especially noticeable was the right click menu in Nautilus, then taking them away, it's a HUGE useability issue.  Sure clean 'em up, or straighten them out so that the little Nancy boys that are pixel counters can be happy, but don't remove something that is quite useable!

Leech

---

### Post by 23meg on 2009-09-04
> **leech said:**
> I hate to say it, but if they get rid of the icons in Gnome 3, I simply won't be using it.  After having Icons in menus for so long, especially noticeable was the right click menu in Nautilus, then taking them away, it's a HUGE useability issue.  Sure clean 'em up, or straighten them out so that the little Nancy boys that are pixel counters can be happy, but don't remove something that is quite useable!

Leech

Disabling the option by default was a prerequisite for clearing up "the mess" on a per-application basis. You can simply re-enable it in gconf if you prefer.

---

### Post by 23meg on 2009-09-04
> **taavikko said:**
> for example: [bug 419126](https://bugs.launchpad.net/bugs/419126)
Affects people running ATI r600 or higher chipsets.

Right, looks like it would have been a good idea to add it, given that a PPA version *seems to* fix it. "*Seems to*" is the catch though; as far as I know the release team tends to prefer not to include non-triaged bugs in the known issues list, and since Bryce Harrington (of all people) has moved the status back to "Incomplete", and there's no data on what exactly causes the issue, we might as well trust the judgement.

---

### Post by Sashin on 2009-09-04
What mess, will Karmic stable have the icons back?

---

### Post by andrewabc on 2009-09-05
In the final will there still be two booting progress bars?
There is the 9.04 booting progress bar (black screen, orange/red progress bar going back and forth), then there is the new grey progress bar that appears after that. Will the grey one (or whatever is decided) be taking over the black one eventually? Looks bad having two different progress bars, one after the other. I know the second grey progress bar has a bug with animation.

---

### Post by tghe-retford on 2009-09-05
> **Sashin said:**
> What mess, will Karmic stable have the icons back?
Only if you enable them - whilst you can. There is talk that the Interface tab in Applications will be removed in Gnome in the future, the gconf options could be removed and looking back at the Gnome bug report that set this off (I've mentioned this in the relevant threads on this forum), Gnome developers are also pushing for the same changes in QT, so KDE *could* in time also be persuaded to lose its icons too. We'll have to wait and see.

There's going to be many a thread when Karmic is released to the public as to where the icons have gone, and if Gnome developers push their icon changes through - war is coming.

---

### Post by tsger on 2009-09-05
> **taavikko said:**
> for example: [bug 419126](https://bugs.launchpad.net/bugs/419126)
Affects people running ATI r600 or higher chipsets.

Here's [COLOR="Red"]_[**how I resolved the ATI bug**]("http://ubuntuforums.org/showpost.php?p=7902691&postcount=11")_[/COLOR].

---

### Post by Sashin on 2009-09-05
I don't like this at all. The icons help quickly identify the menu entries.

---

### Post by Copernicus1234 on 2009-09-06
> **tghe-retford said:**
> Only if you enable them - whilst you can. There is talk that the Interface tab in Applications will be removed in Gnome in the future, the gconf options could be removed and looking back at the Gnome bug report that set this off (I've mentioned this in the relevant threads on this forum), Gnome developers are also pushing for the same changes in QT, so KDE *could* in time also be persuaded to lose its icons too. We'll have to wait and see.

There's going to be many a thread when Karmic is released to the public as to where the icons have gone, and if Gnome developers push their icon changes through - war is coming.

Removing the icons makes Gnome look worse. What is the reason for it? I didnt understand the reason from reading this thread. Someone said "Disabling the option by default was a prerequisite for clearing up "the mess" on a per-application basis." What mess is that?

---

### Post by 23meg on 2009-09-06
> **Copernicus1234 said:**
> Removing the icons makes Gnome look worse. What is the reason for it? I didnt understand the reason from reading this thread. Someone said "Disabling the option by default was a prerequisite for clearing up "the mess" on a per-application basis." What mess is that?

> **Sashin said:**
> What mess, will Karmic stable have the icons back?

[http://ubuntuforums.org/showpost.php?p=7731579&postcount=7](http://ubuntuforums.org/showpost.php?p=7731579&postcount=7)

---

### Post by Regenweald on 2009-09-06
> **23meg said:**
> [http://ubuntuforums.org/showpost.php?p=7731579&postcount=7](http://ubuntuforums.org/showpost.php?p=7731579&postcount=7)

It would not be an online forum if someone was not spouting shock and horror without reading or researching well........ANYTHING.

Anyway, I personally can't wait for the improvements that a standardized look and feel will bring.

---

### Post by ranch hand on 2009-09-06
> **Regenweald said:**
> It would not be an online forum if someone was not spouting shock and horror without reading or researching well........ANYTHING.

Anyway, I personally can't wait for the improvements that a standardized look and feel will bring.
Well all I can say is that this is an alpha and it should work as advertised!!!!!!!!!

Oh, we were warned.

A little reading is a good thing.

---

### Post by muximus on 2009-09-07
Wont shoot it down before trying it out.. but am not very hopeful about it. If ubuntu aims to capture a large user base, graphical assistance to users is essential, and icons go a long way in doing that. Plus, it makes it look pretty. (now.. dont shoot it down just yet.. it is not stability that converted all these new users to linux,  a lot of them are due to the compiz videos posted on youtube and people curious enough to try it out.)

---

### Post by ranch hand on 2009-09-07
> **muximus said:**
> Wont shoot it down before trying it out.. but am not very hopeful about it. If ubuntu aims to capture a large user base, graphical assistance to users is essential, and icons go a long way in doing that. Plus, it makes it look pretty. (now.. dont shoot it down just yet.. it is not stability that converted all these new users to linux,  a lot of them are due to the compiz videos posted on youtube and people curious enough to try it out.)
As has been said many times, you can re-enable the icons, they are not gone, they are just off by default instead of on.

There are some of us that like this very much.  I have never thought much of having images to worship all over my screen (bad attempt at humor).  I really prefer text.

I have not been moaning about this because you could always turn the buggers off.  It is just as easy to turn them on.

---

### Post by ChrT on 2009-09-07
> As has been said many times, you can re-enable the icons, they are not gone, they are just off by default instead of on.

This is precisely what's been bothering me. I don't mind if they're off by default, if that's what the gnome devs decided, but how do you enable them?

---

### Post by taavikko on 2009-09-07
> **ChrT said:**
> This is precisely what's been bothering me. I don't mind if they're off by default, if that's what the gnome devs decided, but how do you enable them?

via "gnome-appearance-properties"
or the hardway with gconf-editor / gconftool-2

---

### Post by Regenweald on 2009-09-07
I'm weird and different i suppose. I can read a menu. When you go to a restaurant, do you need a little picture of a meal or drink in the menu to help you make your selection ? I cannot believe that we have come to the point when reading is a hindrance to ease of use for some. I cannot believe it.

---

### Post by ranch hand on 2009-09-08
> **Regenweald said:**
> I'm weird and different i suppose. I can read a menu. When you go to a restaurant, do you need a little picture of a meal or drink in the menu to help you make your selection ? I cannot believe that we have come to the point when reading is a hindrance to ease of use for some. I cannot believe it.
I love it.  What on earth is wrong with you?  You (pause) you're (pause) you're not literate are you?

Icons are needed.  This is why all fast food joints just have pictures on the cash registers.  Reading is BAD, BAD.

Don't do it again and we will forgive you (but we won't forget).

---

### Post by Regenweald on 2009-09-08
> **ranch hand said:**
> I love it.  What on earth is wrong with you?  You (pause) you're (pause) you're not literate are you?

Icons are needed.  This is why all fast food joints just have pictures on the cash registers.  Reading is BAD, BAD.

Don't do it again and we will forgive you (but we won't forget).

My sincerest apologies! i'll keep my outlandish behavior to myself henceforth :P Shame on me indeed....

---

### Post by VMC on 2009-09-08
> **ranch hand said:**
> ...  I have never thought much of having images to worship ...LOL! That's one for the books. "Images to worship" - It's become a religion

> **taavikko said:**
> via "gnome-appearance-properties"
or the hardway with gconf-editor / gconftool-2

OR for GUI folks

System > Preferences > Appearance > Interface

---

### Post by juancarlospaco on 2009-09-08
Playing Far Cry 2 with Karmic ATM..., 
only searched *"Windows Games"* on Synaptic and PlayOnLinux comes up,
installed, searched for Far Cry 2, next next next next play...
*I hate the nex next part* :)

*Theres Gnome Shell, Quickly and other interesting things on repos*

---

### Post by ericktuk on 2009-09-10
Intel945GM improved a lot, I'm hitting 2734FPS in glxgears, i know it's no benchmark tool but comparing to the 1300 in jaunty I can say I can notice an improvement.
+ Compiz runs a lot smoother 
I like the new theme pingin manages pretty icons.
flash on fullscreen seems to be working properly at last! so kudos for intel video.

---

### Post by andrewabc on 2009-09-10
> **ericktuk said:**
> Intel945GM improved a lot, I'm hitting 2734FPS in glxgears, i know it's no benchmark tool but comparing to the 1300 in jaunty I can say I can notice an improvement.
+ Compiz runs a lot smoother 
I like the new theme pingin manages pretty icons.
flash on fullscreen seems to be working properly at last! so kudos for intel video.

Nice to hear compiz can work on 945 chipset. Does that mean it is possible to run on netbooks (not that you'd want to)? 1.6ghz atom, 1 gb ram, 945 chipset?

I know of lots of people/computers with 945 chipset. Will be interesting when win7 starter on netbooks doesn't have aero, yet people could install ubuntu and get eye candy.

---

### Post by Nipas on 2009-09-11
I wonder if there will be changes concerning the human theme in the final release of karmic.

---

### Post by ma2k1 on 2009-09-11
For Ati read here: [http://www.osnews.com/story/22140/Linux_2_6_32_To_Get_R600_Kernel_Mode_Setting](http://www.osnews.com/story/22140/Linux_2_6_32_To_Get_R600_Kernel_Mode_Setting)

---

### Post by pedja_portugalac on 2009-09-11
Wasn't able to install from both Live CD and alternate. When trying to install from Live CD there was an error on CD, one missed file and today on alternate md5sum was wrong but no errors on CD. Installation was on its final when it block by writing users and passwords and remains like that for to long. Then I hard turn off computer and reboot. I was able to login but nautilus and some "ICE" was complaining about missing folders and so on, there was visible just empty wallpaper and I can move around with pointer. That was all and I have to recover both HDDs, sda (with MBR and wrong GRUB on it) and sdb where actually I have working 9.04 Ubuntu. Thanks clonezilla and sorry 9.10, I'll test it later on my laptop.

---

### Post by rbmorse on 2009-09-11
I had a bad install of today's AMD64 alternate. Told me it couldn't install a necessary file. The md5sum was good for the download and the burn verified properly, so I'm not sure what the problem was. I'll try again with tomorrow's daily.

---

### Post by rbmorse on 2009-09-12
No go with today's LiveCD.  The installer gets confused when the partitioner starts...when I tell it I want to manually select partitions it thinks about thing for a LONG time and then tells me the system has no operating systems installed, which is incorrect and the drive has no root partition specified, which is probably true because I haven't reached that screen, yet. 

Aborting the install at that point (the only option that does anything meaningful) gets me to the LiveCD desktop. I ran gparted and set some partitions manually on the desired drive, but when I re-ran the installer from the desktop icon I achieved the same (lack of) result.

Tomorrow is another build!

---

### Post by jim62146 on 2009-09-12
I downloaded and burned yesterday's alternate install daily. When I attempted to install it the installer died, complaining about missing files. So I grabbed the desktop disk and tried again. At the partitioning stage the partitioner complained I hadn't chosen a root file system. So I gave up and tried again this morning, with the Sept. 12 desktop disk. Same partitioner problem. This was with 2 different hard drives, both with earlier copies of Karmic.

---

### Post by rbmorse on 2009-09-14
Still broken. Today's 64-bit alternate installer  fails with:

Warning: failure trying to run chroot /target  /sbin/ldconfig
no such file or directory. 

but checking the console there's reports that debconf can't find other things. 

Tomorrow's another build!

---

