---
title: "upgrade to edgy  &amp; STUCK"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by pokeyflan on 2007-07-23
Hi Folks:

I was helping a friend do the upgrade from Dapper to Edgy.  During the process, he opened a browser (oops); now when he logs in the OS FREEZES.

What can we do to get it to wor and/or reload the upgrade?

thanks!

--chris

---

### Post by Seisen on 2007-07-23
I have done other things while Ubuntu is upgrading so that is not the problem. Did the upgrade finish without any errors?

---

### Post by pokeyflan on 2007-07-23
No, i think the upgrade got stuck around the "cleaning up" stage, so i'm not sure it finished.
Also, my friend was using the upgrade button from the update manager (it was a 2 step process from Breezy) and not the command line.

Now, it starts the boot process & then lands on a blank screen -- any cliues how i can get to a command line from this?

thanks....chris

---

### Post by Seisen on 2007-07-23
Boot into recovery mode and when it gets to the terminal put this in it.

```
sudo dpkg --configure -a 
sudo apt-get -f install
```

---

### Post by pokeyflan on 2007-07-23
A good idea, but i tried that also -- booting into recovery mode & it hangs there after:

"Begin: Initializing /dev ..."
Done.
BeginL Running /scripts/init-premount ...
Done.
Begin: Mounting root file system ...
Begin: Running /scripts/local-top...
Done.
Begin: Running /scripts/local-premount ...
Attempting manual resume
swsusp: Suspend partition has wrong signature?
Done.
kjournald starting. Commit interval 5 seconds.
EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ..
Done."

and then it just HANGS there.  I'm not knowledgeable enough to suss out how to get to a terminal where i can access a command line from there. 
Thanks for your help!

--chris

---

### Post by Circuit99 on 2007-07-23
Before you do anything make sure backup the data on the hard drive. 

(Easy way is use a Knoppix Live CD to boot to RAM then mount system HD then burn data to CD/DVD.) 

Boot system wait until it hangs,

try typing this: 

Ctrl+Alt+F1

( I don't think the following will work, I think alternate CD is a better option )

Then your system should request for User Name and after that Password.

then type

sudo apt-get update

sudo apt-get upgrade

This should work if you have internet connection want to repair broken packages.

This page has useful info that might help:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)


A possible solution to this is to boot into CLI then excess the Edgy CD then start installation. This is possible with the alternate CD, but double check. 

Check this

[http://ubuntuforums.org/showthread.php?t=404179&highlight=alternate+cd](http://ubuntuforums.org/showthread.php?t=404179&highlight=alternate+cd)


This where they got the CD from:

[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)


Good Luck !!!

---

