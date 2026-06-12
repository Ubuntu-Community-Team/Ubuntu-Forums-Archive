---
title: "Reading Hardy Heron drive in Windows XP"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by lamps06 on 2008-04-28
Does anyone know if the file system changed between Gutsy Gibbon 7.10 and Hardy Heron 8.04?  I ask because I have a dual boot with two separate hard drives, one for Ubuntu and one for Win XP.  Previously I had Gutsy installed on one drive and I had Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) installed on my Windows drive so I could still access my Ubuntu drive in Windows.  Since I upgraded to Hardy I can no longer read my Ubuntu drive in Windows.  I tried uninstalling Ext2 IFS and reinstalling with the newest version to no avail.  When installing, the software recognizes that my Ubuntu hard drive has two linux formatted partitions and I can assign them drive letters, but when I try to access them in Windows I get an error message that the drive is unformatted.  Anyone else having similar problems?  Thanks.

---

### Post by Vermind on 2008-04-28
Hello,
I switched to [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd"), since it also works with my USB memory. I never had a problem reading partitions with Ext2IFS though, except from passive USB storage.

I hope this helps.

---

### Post by lamps06 on 2008-04-28
Hmmm, I tried Ext2Fsd but I was not quite sure how to go about using it.  I checked out the WinXP manager but I did not realize it was a separate program.  And I was not sure how to go about viewing the contents of my Ubuntu disks.  I really liked Ext2IFS because it was essentially invisible and just treated Linux drives like NTFS drives.

Does anyone know if the file system changed changed between Gutsy and Hardy?  I cannot think of any other reason Ext2IFS would stop working.  And I really would like to be able to access my Ubuntu drive in Windows again.  Any word on how to use Ext2Fsd or how to get Ext2IFS working again?  Thanks.

---

### Post by Vermind on 2008-04-29
Hello,
There are no changes in the filesystem in Hardy to my knowledge.

yes, Ext2Fsd is a bit confusing to use at first. Assuming You downloaded the installer, You have to run the setup file that it installs, and then the Ext2Manager. The note about this is in the readme file. After a reboot it works with no changes though.

If You downloaded the manual install one, You have to do a bit more. It's all in the readme files. I haven't used Ext2Fsd for a long time, but it seems to work better than Ext2IFS for me, mainly because Ext2IFS did just the same thing that You describe with my USB memory. It sees that there is a Linux partition on it, but does not allow mounting it. Too bad that Ext2Fsd is not so user-friendly. :(

---

### Post by lamps06 on 2008-04-29
Ah, when I last posted I was pretty tired and frustrated.  I opened the readme file for Ext2Fsd but I did not see any sort of instructions, it just looked like release notes.  Sorry I did not take a little more time to research the usage of the program.

With that being said I believe I figured out my problem with Ext2IFS.  Since I installed Hardy Heron I have not had one single clean shut down.  I always click on the little exit door in the top right corner or I go to System->Quit but then my computer locks up.  I can move the mouse but I cannot click on anything and no keyboard commands are accepted.  At that point I usually just reboot or do a hard shutdown.  Not the best practice, I realize.  At any rate, when I try to read my Ubuntu drive in Windows I cannot read it because of the state in which it was shut down.  I am pretty sure that if I could shut down Ubuntu properly then I would be able to read the drive in Windows.

This brings up my next question:  is anyone else having trouble shutting down Hardy Heron?  I have only waited maybe 15 seconds after attempting to shutdown using one of the above two methods so perhaps I am being slightly impatient, at least in troubleshooting terms.  I suppose I should open a new thread.

Thanks for your help, Vermind.  My apologies for being a bit impatient.

---

### Post by Vermind on 2008-04-29
Hello,
You could try a "manual" shutdown, and post the last message, if any.
End Your session by logging out, then press ctrl-alt-F1, to reach the first virtual terminal screen. (Back with Ctrl-Alt-F7, F8 or F9). Then restart the computer with Ctrl-Alt-Delete.
If the system does not shut down cleanly, take a digicam shot of the screen or write down the last messages, or suspicious-looking ones.

---

### Post by lamps06 on 2008-05-01
Well, I tried what you suggested.  I reached the virtual terminal screen and hit ctrl-alt-delete.  A list of seven processes came up as stopping, shutting down and unmounting.  All succeeded within about five seconds and then the computer rebooted.  This was much faster than trying to shut down within the GUI.  Does this mean that the hold up most likely has something to do with the GUI?

---

### Post by Vermind on 2008-05-01
Hello,
Yes, I think so. Which graphics card do You have?
You could try to disable visual effects in the appearance menu, then trying to shut down. Usually Ubuntu shuts down better without them, especially if You have a graphics card with not so good support, or your visual effects (compiz) has been upgraded from an old 3rd party repository version. Let's see if they are the cause first, and then try fixing them if they are.

---

### Post by Vermind on 2008-05-01
Also on this note, older versions of Compiz did not work very well with the shutdown menu of Ubuntu. After Gutsy, this started working better for me. Also, synaptic and other password dialogs did not work properly, until I went to accessibility settings and ticked the box to show all such dialogs as regular windows.

---

### Post by lamps06 on 2008-05-02
I have an NVIDIA GeForce4 Ti4200 graphics card.  I did a fresh install of Hardy Heron so I have whatever version of Compiz came with Hardy.  I am also running the restricted drivers for my NVIDIA card.

I tried disabling the visual effects and then tried shutting down but it still took more than one minute for the shutdown menu to appear.  When I was running Gutsy with the exact same setup (same graphics card, restricted drivers, using visual effects with Compiz) I had no trouble shutting down.

---

### Post by lamps06 on 2008-11-25
So I eventually resolved my issues with Hardy.

I have now moved on to Intrepid, 8.10, and am having similar issues.  I did a clean install of 8.10 and it works fine.  It shuts down fine.  However, I can no longer use Ext2IFS to read my Ubuntu drive in Windows.  Windows just keeps telling me the drive needs to be formatted.  Does anyone know why this is happening?  I uninstalled Ext2IFS and reinstalled but to no avail, I still cannot read the Ubuntu drive in Windows.

---

### Post by Vermind on 2008-11-25
Hello,
I moved on to [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/") for Windows since the IFS started to present weird problems with my portable HD. I hope it helps you. Setting it up is slightly different; you click a bat in the folder if I remember to register the service, and then set some drive letters via the ext2 manager that comes with it. Also, write support for ext2 is not enabled by default, you have to enable it in the manager. I never had trouble with it.

The only problem with this, as with all other ext2 drivers for windows, is that you cannot run windows programs from the drive. Trying will result in a blue screen talking about some problem mapping memory, and then your machine will reboot in less than half a second.

I would like a setup where I have a portable HD with my laptop windows games and linux games on the same drive, and then I can run the windows games via wine or from native windows, and the Linux games when I am in Linux. This memory-mapping error makes that slightly impossible.

Ext2Fsd seems the best so far, tell me if you like it / if you find better alternatives.

---

