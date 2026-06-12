---
title: "Nvidia Desktop Effects Not Available for Kernel 2.6.34..."
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by casparov on 2010-06-07
Hi, Everyone...

I had a really irritating problem w/ DVD recognition, which was NOT solved--though the advice was very knowedgeable--and involved changing the Lucid kernel, in this case to 2.6.34.  Thread: [http://ubuntuforums.org/showthread.php?p=9422831#post9422831](http://ubuntuforums.org/showthread.php?p=9422831#post9422831)

The method I used for changing the kernel is found here: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)  However, I would not have attempted this action had not the article indicated that I would be given a boot option on which kernel would be loaded.  All I have now is 2.6.34--there is no option available to me upon booting the PC.  I assume I could go back to the stock kernel, somehow.  I would now like to roll back things to the default kernel, but the link in this paragraph explaining how is very confusing to me.  

Now that I have changed the default kernel and my drive is still not consistently recognized, I cannot enable the desktop effects (Nvidia 3D capability), even after installing (what the system thinks is) the appropriate driver. Also, I now get an error in trying certain Web news videos that my system "no longer supports opengl".   (Card  is a 512MB NVIDIA GeForce 8400 GS, which ran very well under the Lucid default release, installed April 30.  I have downloaded the most current Linux driver for this card [NVIDIA-Linux-x86-195.36.24-pkg1.run] from the company's site.)  

Does anyone have any ideas on how to restore the original Lucid kernel--at least I had an okay system at that point.

Thanks so much,  C.

---

### Post by VastOne on 2010-06-07
> **casparov said:**
> Hi, Everyone...

I had a really irritating problem w/ DVD recognition, which was NOT solved--though the advice was very knowedgeable--and involved changing the Lucid kernel, in this case to 2.6.34.  Thread: [http://ubuntuforums.org/showthread.php?p=9422831#post9422831](http://ubuntuforums.org/showthread.php?p=9422831#post9422831)

The method I used for changing the kernel is found here: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)  However, I would not have attempted this action had not the article indicated that I would be given a boot option on which kernel would be loaded.  All I have now is 2.6.34--there is no option available to me upon booting the PC.  I assume I could go back to the stock kernel, somehow.  I would now like to roll back things to the default kernel, but the link in this paragraph explaining how is very confusing to me.  

Now that I have changed the default kernel and my drive is still not consistently recognized, I cannot enable the desktop effects (Nvidia 3D capability), even after installing (what the system thinks is) the appropriate driver. Also, I now get an error in trying certain Web news videos that my system "no longer supports opengl".   (Card  is a 512MB NVIDIA GeForce 8400 GS, which ran very well under the Lucid default release, installed April 30.  I have downloaded the most current Linux driver for this card [NVIDIA-Linux-x86-195.36.24-pkg1.run] from the company's site.)  

Does anyone have any ideas on how to restore the original Lucid kernel--at least I had an okay system at that point.

Thanks so much,  C.

Are you sure that you do not have the old kernel in your grub but are just not seeing it?  When you boot, are you seeing a grub screen?  I have updated to 2.6.34 and the restricted driver nVidia drivers are working perfectly for me but if I want to go back to 2.6.32, I have that option.  

Read [_[COLOR="Green"]this[/COLOR]_]("https://wiki.ubuntu.com/Grub2") and pay specific attention to 

#

GRUB_HIDDEN_TIMEOUT=0

    *

      The hidden timeout option is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
    *

      On single-OS systems, the menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: This setting is not used, as determined by the 
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    *

      0 The menu will not be displayed. There will be no delay.
          o The user may force displaying the menu as the computer boots by holding down the SHIFT key (single-OS computers only).
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key. 
                + If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected. 

#

GRUB_HIDDEN_TIMEOUT_QUIET=true

    * true - No countdown is displayed. The screen will be blank.
    * false - A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value.

---

### Post by casparov on 2010-06-07
V.One... 

Thank-you so much for taking the time to help me w/ the GRUB boot options.

I have not altered my values yet but have booted the machine using the shift+hold and discovered the menu.  Unfortunately, I have booted each kernel option (the default *32.22 and *32.21, as well as *.34) and my Visual Effects refused to be enabled, even if just selecting the normal option.

The machine just encounters a loop, where it searches and installs the driver then directs a restart.  Upon restarting, an error message at the Appearance tab states that the effects are not available.  (I have also gone the route of changing the driver selection through System/Administration/Hardware drivers, which directs the default and recommended driver.)  

So, I don't know what to do now that I, seemingly, can direct which kernel is loaded.  As I mentioned in the original post, I do have the newest driver from NVIDIA sitting on the desktop but am not sure how to load that.

Another thing (seemingly unimportant)... The only way I can access my favorite video (from the UK) is via Livestation, and now that application only states that, "This system does not support opengl." Would the restricted driver get around that error?

Somehow the kernel change corrupted something. 

Thanks again, C.

---

