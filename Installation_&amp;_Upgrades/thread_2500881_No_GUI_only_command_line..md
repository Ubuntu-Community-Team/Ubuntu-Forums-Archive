---
title: "No GUI only command line."
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by bkz81 on 2024-09-14
I was doing updates this morning and saw an upgrade to the latest version. It was in process but my screen went black midway,  and now It won't go back to GUI. I get a white crash screen when i type startx. I have the nvidia 570 drivers.

I am not sure what commands or updates that are needed to fix this.

---

### Post by yancek on 2024-09-14
What version release of Ubuntu were you using (updating from) and what were you updating to?  Are you using Ubuntu or one of the many derivatives?  Did the screen just go into sleep mode?  Did you try moving the mouse, hitting a key on the keyboard?  Did you lose power?  If this is a laptop, did you have it plugged into a power source when doing the update?  Do you get any output on screen after typing startx?

---

### Post by bkz81 on 2024-09-14
> **yancek said:**
> What version release of Ubuntu were you using (updating from) and what were you updating to?  Are you using Ubuntu or one of the many derivatives?  Did the screen just go into sleep mode?  Did you try moving the mouse, hitting a key on the keyboard?  Did you lose power?  If this is a laptop, did you have it plugged into a power source when doing the update?  Do you get any output on screen after typing startx?

Thank you for your reply back.  Thankfully i have the box dual booted with Windows 11.  I was upgrading from 22.04 to 24.04 via GUI.  I am using just Ubuntu desktop.  Sleep was disabled. I moved the mouse and tapped the keyboard but nothing was happening.  No power was lost during the upgrade.  I have attached a few screenshots.   When i log into the command prompt and put in startx i get a "Oh no something went wrong"  The second screenshot is when i hit ESC on the ubuntu screen i see a lot red.   Last was the straight to login prompt after boot.  [IMG]https://ubuntuforums.org/attachment.php?attachmentid=294236&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294237&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294238&stc=1[/IMG]

---

### Post by TheFu on 2024-09-15
Can you restore from a recent backup and try again?
Be certain to fully patch the OS _BEFORE_ trying the upgrade.

---

### Post by bkz81 on 2024-09-15
> **TheFu said:**
> Can you restore from a recent backup and try again?
Be certain to fully patch the OS _BEFORE_ trying the upgrade.

Nope. I didn't have that setup which is definitely my fault.

---

### Post by bkz81 on 2024-09-15
I did some more digging on this and YouTube and found out that the following command of "sudo apt install ubuntu-desktop" did the trick.  Once it installed the screens came up with only a mouse cursor.  I let it do it's thing for a few more minutes but it wasn't doing anything so i just powered off and on again and was given a log in prompt.  I am back up and running, with a few things i need to reinstall and or adjust.

---

### Post by TheFu on 2024-09-15
Would be smart to setup backups for both the OS and your data ASAP.  Eventually, all storage devices fail. They don't always tell us before the failure, so automatic, versioned, backups, are generally the best answer.  Backups can also help with security and troubleshooting, because with versioned backups, we can see what settings and programs changed over time.

Lots of people have been using "**Timeshift**" for their OS backups for a while now. The Timeshift guys don't recommend using it for personal data, but just for the OS. It has a GUI and I've seen it work in the last few weeks.  For personal data, basically your files and settings that are in your HOME directory, there are many tools, but the one that is also pretty easy to setup and understand is called "**Back In Time**".  It isn't perfect, but it is pretty great.  

Both of these tools are in the repos. Both have simple GUIs.  Both can share the same external USB-connected HDD with a native Linux file system for backup storage and both are automatic and relatively fast.  

Backups are 20% of the issue.  It really is about the restore. We don't do backups just to "have them". We do backups to be able to restore - the easier the better.  That's the 80% that matters most. 

**About backup HDDs**

Considering that an external USB backup HDD is about $25/TB (2TB is $50, 4TB is $100), there's really not much reason that almost anyone can't have good backups. If you are willing to buy an internal HDD and put it into a $20 external USB enclosure yourself, you can save money for 5 minutes with a screw driver. Internal HDDs are about $15/TB, so $30 for 2TB which is a break even point but $60 for 4TB is clearly cheaper to put into your own USB enclosure.  This also avoids some of the non-standard things the USB enclosures do and their much shorter warranties.  Typically, any USB HDD gets a 90day to 1yr warranty.  If you buy a cheap internal HDD, it will have 1-3 yr warranty. Inside, they are nearly identical HDDs. Do yourself a favor and buy internal HDDs to get the longer warranty, then install them into a USB case if you don't have room inside your PC case (sorry laptop people).

**Timeshift Restores**
Timeshift restores after a little issue or after a huge - dead-disk - issue come down to running the Timeshift program either from the OS install or from a Try Ubuntu environment, it will probably automatically find your Timeshift backup storage, show you a list of "snapshots", you pick where you want it restored, select one of the snapshot versions,  and press the "restore" button.  Come back in 15-60 minutes and you have your OS as it was at the time of that snapshot. Easy.

**Back In Time Restores**
For restoring your HOME directory stuff, Back In Time creates directory trees that look like mirrors of the entire directory structure, just with date-time labels for the top directory.
They are in YYYYMMDD-HHMMSS/ directories, so you'll know which are for what times.  Just work your way down into the directory you want to restore a file or directory or entire everything from, and just copy those files back to where you want them to be in your HOME directory.  I'd use **rsync**, but using a file manager is probably fine for most data and config files.

Both these tools are easy to install. Easy to setup. Easy to use for restores, which is why we bother with backups. They have wizards.  I also believe that the practice of actually doing backups extends the life of data on HDDs.  Every time the backup tools look at the source files to decide if anything has changed, that reading of the bytes lets the drive see what the electrical charge is and if it is a little lower than it should be, the drive firmware will re-write the data, freshening it.  When that happens, there's an opportunity for the data to be validated.  Further, if the re-write has a failure, the drive firmware will relocate the data to a spare block and you'll never be impacted by it, probably.

---

