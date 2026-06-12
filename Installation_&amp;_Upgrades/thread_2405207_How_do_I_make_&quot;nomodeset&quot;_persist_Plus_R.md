---
title: "How do I make &quot;nomodeset&quot; persist? Plus Related display size problem"
date: 2018-11-02
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2018-11-02
I've just set a 2nd-hand desktop Windows 10 machine to dual boot Ubuntu 18LTS, with details shown here [https://ubuntuforums.org/showthread.php?t=2405146](https://ubuntuforums.org/showthread.php?t=2405146)  and am grateful for help received here to achieve this.

To do this I had to edit in "nomodeset" via pressing "e" at the Grub menu, in order to overcome the USB bootable stick appearing to stall, caused by the Nvidia graphics card. Otherwise I only got the Bionic Beaver screen.
It worked, though the display was now oversized for the screen. 

Having successfully done this for the set-up, I restarted, and once again the screen stalled until I again re-started, and added "nomodeset" in at the grub menu again.

Is there a way of making the "nomodeset" edit persist? It'll be a real pain having to edit it every time. (In simple steps, please! :-)  )

And while Ubuntu duly comes up, it's still oversized, so I'd like a way of  setting it to fit the screen rather than missing a section down the  right hand side. Does "nomodeset" need anything further adding to it to have the right sizing effect?


Thanks for continuing help. I'm seriously dependent on basic instructions in this forum to make anything work!

---

### Post by oldfred on 2018-11-02
You should only need nomodeset until you correctly install the nVidia driver.

If you install the wrong nVidia driver, you must purge, or you get conflicts and never get it working.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]
[/URL]

---

### Post by Richard_York on 2018-11-03
Thanks, that looks hopeful.
It'll be tomorrow before I get chance to try this, then will probably need guidance on how to purge and correctly install when I do!

---

### Post by Richard_York on 2018-11-04
[post quickly deleted, I just moved on a step]
I opened the geforce drivers link, and it's currently downloading NVIDIA-Linux-x86-390.87.run   onto the desktop machine. (I'm using an older laptop for this conversation)
Having downloaded, what step to I take to install this and if need be purge what's already in, please?

And am I in danger, in the process, of upsetting the function of Windows? Upgrading the graphics card resulted in the guy in the shop spending some time trying to fix a bug which meant Windows was convinced that there was a 2nd and even 3rd screen, and trying to display there rather than on the real screen. I don't want to get back to that again.

Thanks for your help.

---

### Post by oldfred on 2018-11-04
Do not install the .run file.

Instructions were not to download, the Ubuntu repository has versions slightly modified to work better with Ubuntu:
Updated driver search by nVidia model, [COLOR=#ff0000]do not download[/COLOR], just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

The other links show the install options.
You can use Software Updater, settings button, Additional drivers tab. Choose recommended.

You can also use terminal and the links above have the specific commands to run.

---

### Post by Richard_York on 2018-11-04
My slip, sorry. It's only downloaded, not applied, so I trust will be easily deleted.

I haven't yet persuaded it to take screenshots, but going via the Software Updater as you say, that machine is now showing as follows
*<starts>*
 
NVIDIA Corporation GK208B (GeForce GT710)
 This device is using an alternative driver.
*[empty option circle]* Using NVIDIA dfriver metapachage from nvidia-driver-390 (proprietory, tested)
*[option circle already with orange filler]* Using X.OrgX server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
[I]
[Then at the bottom of the screen the following][/I]
No proprietary drivers are in use.
A proprietary driver has private code that Ubuntu developers can't review or improve. Security and other updates are dependent on the driver vendor

*<ends>*

I'm thinking, between the pre-filled in circle and the note at the foot of the screen,  that the X.Org X server one is the one to go for, but rather than making any more assumptions and so having to purge anything, I'll await your next before pressing anything.

Thanks again.

---

### Post by oldfred on 2018-11-04
The filled in circle is the driver you are using.

You want to check the -390 driver as that should be the correct driver for your nVidia card. (that was what you found in search?)

You can take screenshot and easily attach with Forum's advanced editor and the paperclip icon. Attach screenshots, do not post in line.
       Post #4 Change to 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Your screen should have been similar to this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Richard_York on 2018-11-04
Yes, the screen was similar. For some reason the computer didn't appear to respond to the "Print scrn" key, hence my typing it all in.

The driver I found in my search was Nvidia-Linux-x86-390.87, the one I mistakenly downloaded.
Is this close enough to "Nvidia-driver-390" which is what the software updater screen box offers?

Thanks

---

### Post by oldfred on 2018-11-04
That should be driver you want.
What is in repository is not always the very newest but will work.
If nVidia made changes that are security related, it will not take long and your driver will be updated. 
But drivers that are considered legacy do not get many updates.

There is a screenshot application. I have not used print screen key since XP days.

[LIST]
[*]Open *Screenshot* from the [COLOR=#6C6C6C][Activities]("xref:shell-introduction#activities")[/COLOR] overview.

[/LIST]

---

### Post by Richard_York on 2018-11-04
I'm typing this on the new machine, which started easily into Ubuntu 18.04 with no hitches and now displays the screen at the right resolution and size, so I'm very relieved.
Wonderful - thanks again. Problem solved.

PS Link to "Activities" overview tells me "address not understood" but that's not a problem. I can simply use Firefox for screenshots now i can see it all on one screen!

---

### Post by oldfred on 2018-11-04
I copied that from the screenshot app & it highlighted it automatically. It should not be.
It really is activities on your system, not in Firefox. If default gui, lower left corner.

---

### Post by Richard_York on 2018-11-04
Aha - thanks again!

---

