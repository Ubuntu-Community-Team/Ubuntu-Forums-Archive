---
title: "Upgrade to 20-16 Fiesty Fawn Broke Xwindows"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by mikey5555 on 2007-09-04
Hello all...
 I updated the kernel from 2.6.20-15-generic to 2.6.20-16-generic this morning and my X will no longer work.  I have a Nvidia RIVA TNT2 video card in an AMD Sempron 2600+ system.  After the upgrade/update the system wanted to restart in order to apply the changes.  BIG mistake!!!!!  Now, my X no longer works, and booting to the previous kernel (2.6.20-15-generic) also fails to load X.  
NOTE:  I had just been trying to enable desktop Effects from the **System->Preferences-> Enable Desktop Effects** menu item.  It appeared to finish without a problem.  I then noticed that there were "Recommended Updates" waiting to be downloaded and installed.  I have never had a single problem with UBUNTU (started with Edgy Eft several months ago) and it's updates.  I see from the posts that many people are experiencing significant and varying  problems after this update.  
I suspect that the reason the 2.6.20-15-generic kernel won't boot into X has something to do with the implementation of "Desktop Effects".  I did not reboot after enabling Desktop Effects before I accepted the Upgrade.  Can someone tell me how to "un-do" the Desktop Effects (and possibly remove the update to 2.6.20-16-generic until the problems with this update/upgrade are fixed)  when I am unable to get back into the X environment?  Hopefully this would correct the problem with 2.6.20-15-generic not being able to start the X windows system.  
BTW:  as a fairly recent user of UBUNTU, I am wondering if this sort of problem is typical with UBUNTU kernel updates/upgrades?  I'd hate to think I have made a poor decision to make the change from MS OS to UBUNTU.  MS has killed several machines for me over the years.  I had hoped to get all the systems in our office swapped to UBUNTU over the next few months, but now I hesitate to continue with the conversion for fear of completely ruining our productivity, and p-----g off everyone in the office (especially after having ardently campaigned for just such a conversion, based on the "Robustness" of Linux/UBUNTU.
Interestingly enough, I have 2.6.20-16-generic running on one of my home systems, and it accepted the update without a hitch.  It is running an Intel processor and an ATI video card with Desktop Effects enabled, and accepted the update without any complaints.  Could this be more specific to Nvidia video cards?  Or.... did I just get lucky with my home system?  

Frustrated and Confused....

mikey5555

---

### Post by rsambuca on 2007-09-04
Which drivers are you using for your video?  It seems that the majority of problems that have been encountered with the recent updates are occuring to those that have used alternate methods of installing the video drivers.

---

### Post by mikey5555 on 2007-09-04
rsambuca,
I obtained the driver via Synaptic, and I believe it was the "Restricted" driver (or something like that).  It has been several months since I setup that system  with UBUNTU 6.10 Edgy Eft, the "upgraded" to 7.04 Feisty Fawn.  I've been taking all suggested/recommended updates since original installation wiothout a single problem.  

Regards....

mikey5555

---

### Post by rsambuca on 2007-09-04
Can you boot in recovery mode?  I would try just changing the driver to "nv" in  your xorg.conf until this gets sorted out.  You should be able to edit the xorg.conf from a live CD, if you have one handy.

---

### Post by rsambuca on 2007-09-04
You might want to check out this thread.  Someone has reported success via re-installing certain packages.

[http://ubuntuforums.org/showthread.php?t=541795](http://ubuntuforums.org/showthread.php?t=541795)

---

### Post by soma4me on 2007-09-04
Mikey5555,

Hi, I have similar problem, still **unresolved** though ([http://ubuntuforums.org/showthread.php?t=542215](http://ubuntuforums.org/showthread.php?t=542215)).   Fortunately, I can still use 20-15 kernel.

I've installed Feisty Fawn clean from CD, and it recognized my video card (nVidia 7300 GT) without any intervention, no xorg.conf changes were needed, it automatically used nvidia-glx restricted driver.

There are a lot of reported problems on this kernel upgrade, some people are recommending to use nVidia  native Linux driver, and I'm still searching if there are any other ways before taking that last step.

Good luck!! - we both need it.:(

---

### Post by mikey5555 on 2007-09-04
**rsambuca and soma4me,**
Unfortunately, the problematic system is at my office and I am not.  I will be trying these "solutions" 1st thing wednesday morning, and I shall gladly report/post my results (good or bad) as I go through them.  
**rsambuca**, I can boot into Recovery Mode at a command prompt, and I do have my "Live CD" handy.  are you suggesting that I should boot from the CD and edit or install from there?  Or, would it be more appropriate to boot to the Recovery Mode on the actual hard disk, and proceed from there?  
BTW:  I saw this statement in one of the threads mentioned above: 

[B][I]I thought there was some thing buggy about 2.6.20-16-generic . so i didn't install it either . I went straight to 2.6.22-10-generic
I haven't had any problems with 2.6.22-10-generic [/I][/B]  

Is this saying that there is a 2.6.22-10-generic kernel available?? If so, is it finished and available or is it some sort of "pre-release" or "Beta" version?  That's a pretty big jump from 2.6.20-16-generic if I understand it correctly.....???

Regards....
mikey5555

---

### Post by mikey5555 on 2007-09-05
soma4me & rsambuca,
I got my system going again **with X** by simply booting into Recovery Mode for the 2.6.20-16-generic" kernel, and editing my xorg.conf and changing the "Driver" specification in the "Generic Monitor" section from "nvidia" to "nv" (without the quote marks).  Rebooted normally and my X desktop is back!  
Thanks to all for your input.  I'm glad it was as simple as it was, in the end.  
Here's hoping everyone 's recovery/repair is as straight forward.

Regards...
mikey5555

---

### Post by rsambuca on 2007-09-05
Just keep in mind that if you want 3D desktop effects you will eventually have to reinstall the nvidia drivers.

---

### Post by soma4me on 2007-09-05
rsambuca,

Excellent!   Thanks, I'll try the same tonight.   One clarification: you've changed the Device section where the video card is defined, correct?  Something like this:

> 
[FONT="Courier New"]Section "Device"
   Identifier  "nVidia..."
   Driver       "nvidia"
   BusID       "PCI:......"
EndSection[/FONT]


You've changed "nvidia" to 'nv" -- is this correct?

Also, can you be more specific about "reinstall nvidia driver"?   Have you done so?

Again, thanks a bunch, this is very helpful.

---

### Post by wkulecz on 2007-09-05
Stuff like this gives Ubuntu a black eye.  Had the same issue with an early update to 6.10

Blame the "proprietary" drivers if you insist, but the system upgrade tool should not be pushing these kernel updates without proper dependencies being fulfilled for the Xserver driver in use.  Fact is, confined to the "free" Xserver driver I could not use Ubuntu for performance reasons and I'm not doing anything 3D.

Bottom line, do what I do.  Decline all Kernel updates until you see proof it does something you need *and* all the other necessary bits have also been updated to match.

--wally.

---

### Post by rsambuca on 2007-09-05
But I update immediately and haven't had a problem with the nvidia drivers.  It seems pretty hit and miss, though.

---

### Post by juniorsonny on 2007-09-05
This is the first kernel update I didn't have any trouble.  Everything works great.

---

### Post by mikey5555 on 2007-09-06
soma4me,

---

### Post by mikey5555 on 2007-09-06
soma4me
    I simply cd to /etc/X11 and edit xorg.conf.  Changed the following line from **nvivia** to **nv**  :
[I]
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"[/I]     <---this is what I changerd to **nv**

Hope this helps you with your probs.  Luckily I did not need to re-install anything, just changed the Driver to nv and saved.  

Regards...

mikey5555

---

### Post by soma4me on 2007-09-06
mikey5555,

Thanks a bunch.   Will try it tonight and report the result.

---

### Post by mikey5555 on 2007-09-06
soma4me
FYI - It turns out that my Nvidia TNT2 video card is "to old" for the drivers that support the "Desktop Effects'.  I will ge loosing this card in favor of a newer Nvidia, or possibly one of the several used ATI cards I have lying around.  my ATI Radeon 7500 card, on my home pc, runs the Desktop Effects with absolutely no problems using the "Restricted" driver.  
Just thought this might be helpful.....

Regards...
mikey5555

---

### Post by soma4me on 2007-09-06
mikey5555,

I finally got in 20-16 kernel!!! Just as you've indicated -- changing the driver to 'nv'.   Awesome!!

Now I'm in 20-16, I want to re-enable retricted driver -- people never seems to be satisfied with what they have, isn't it? :) As expected, when I used restricted-manager, it tells me I don't need one.

I'm thinking of re-installing the restricted modules, what's your thought?

Thanks again.

---

### Post by soma4me on 2007-09-07
Mickey5555,

I finally fixed the problem by re-installing the restricted modules for 2.6.20-16!!!

I boot into the recovery mode from GRUB menu.    At command line, do the following:

```
apt-get update
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

now you can boot into the new kernel normally :) (You may need to install other restricted modules)

Hope this also help other frustrated people out there -- Ubuntu is great, but without the helping people in this forum, like yourself, Ubuntu is nothing!

---

### Post by mikey5555 on 2007-09-07
soma4me.
Glad to have actually given something *back* to the community, and pleased that it was helpful to you.  
Let me know how the "Restricted Drivers work for you.  I would like to know just wnat model Nvidia card you're using, and wheather you can enable and use the "Desktop Effects" with the "Workspaces on a Cube" option.  That is an awsome way to have 4 seperate desktops, easily accessable, and each being used for a different purpose.  It really makes your desktop less cluttered with several windows open.

Regards....
mikey5555

---

### Post by soma4me on 2007-09-07
mickey5555,

I have nVidia GeForce 7300GT card.    After the fix, I used the machine for extra couple of hours and did not see any problem, OpenGL, 3D stuff all very normal and snappy.

I will tried the Desktop Effect a bit before the crash, the wiggling window was making dizzy :) But I'll enable it tonight and see if still works OK.

Gotta go back to something boring -- work.....:)

---

### Post by soma4me on 2007-09-08
mickey5555,

Tried out desktop effect -- the window still wiggles, so I guess it's normal :)

Something strange, or maybe I just don't understand it, did happen though, when I eventually disable desktop effect after playing with a bit, I lost my GDM panel, and since I have only one panel on the desktop, I was left with a GUI without access to any menu access, I had to manually execute gdm-panel to get it back.     Besides that, all seems to be good.

Sorry I am helping you much.

---

### Post by mikey5555 on 2007-09-08
soma4me.
It's not the "wiggle" I find impressive, but the "Workspaces on a Cube" that I relly like.  Makes it easy to have several differently arranged desktops, and keep certain apps on a particular "face" of the cube... really neat!  I dinn't like the "wiggle" windows, either.
Glad to hear all seems normal, now.  I have not encountered the problem with loseing the GDM panel.  Does this happen avery time you disable Desktop Effects?  Does it come back if you restart the system?  Let me know what you discover....

Regards...

mikey5555

---

### Post by soma4me on 2007-09-09
mikey5555,

Here is what happened to me when I tried the Desktop Effect -- I usually have 4 workspaces in a panel, when I enable Desktop Effect, it got cut down to one.   I added 3 more back in, play with Desktop Effect a bit, then disable it, the first time was OK.

I re-enable Desktop Effect again, while I was playing around, an update notification came up, I did not want to apply the update while in Desktop Effect, so I disabled it again, then the panel disappear!

To bring it back I had to create a launcher for 'gnome-panel'....Did not try to reboot and see if it comes back.

Question:   How do you use the desktop cube? what key combination do you 'flip' the cube?  I've see Beryl's Cube, it's really cool! not sure what Gnome's Cube looks like...

Thanks.

---

### Post by aev on 2007-09-11
My X disappeared after upgrading from Edgy to Fiesty. 

I changed Driver form "nvidia" to "nv" (/etc/X11/xorg.conf) and got the X back.

this worked for me.

Just my 50c.

edit:

then I made sure I had the nvidia-glx-new package intstalled and used Envy to get right configuration. Worked.

---

### Post by pauln600 on 2007-09-26
Upgrading to 7.04 broke my Xwindows - the log file is at

  [http://www.picolist.org/Xorg.0.log](http://www.picolist.org/Xorg.0.log)

I haven't installed any proprietary drivers.  A copy 
of /etc/X11/xorg.conf is at
 
   [http://www.picolist.org/xorg.conf](http://www.picolist.org/xorg.conf)

Tried to recover via dpkg-configure xserver-xorg, which worked
the last time this happened (which was just a couple of weeks
ago as a result of an upgrade to 6.10), but no joy.

Any ideas?

Thanks,
Paul N.

---

