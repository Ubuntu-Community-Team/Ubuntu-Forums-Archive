---
title: "How to reinstall Ubuntu 11.04 after a failed upgrading to 11.10?"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by bookjohn on 2011-10-25
I had a dual boot system with windows 7 and Ubuntu 11.04. The boot loader was Grub 1.99 from which i can select windows 7 or Ubuntu 11.04. It worked very well until last week when I started Ubuntu and followed the prompt to upgrade to 11.10 before make any research.

First, the upgrading to 11.10 was failed. The GUI just stopped there with a watermark saying unsupported hardware - I could not log on.

Then I wanted to get my 11.04 back. I booted from Ubuntu 11.04 USB stick and tried to reinstall ubuntu 11.04 over the upgraded 11.10, but the installation GUI  stopped when I clicked continue button after it had confirmed free disk space, power source connection and network connection - I had not chance to reach the screen to allocate disk space. I tried with 11.10 Live CD to install, but the installation program stopped there as well.

Then I guessed perhaps I should remove the old installation of Ubuntu before new installation, and then I deleted ext4 partitions, but I still could not make install program run, and I had broken my Grub boot loader!

Now I cannot boot into Window 7, and cannot install Ubuntu. I really need help!

My system: Acer aspire 7750G, i7-2630QM, AMD Radeon HD 6850M 1GB.

---

### Post by critin on 2011-10-25
With live 11.04, look at Disk Utility or gparted.  Make sure the old ubuntu partition has been deleted cleanly. (just for your own benefit.)
Go to desktop and Install.  Don't leave the computer alone, stay with it.  When it gets to the os page, choose to install side-by-side with windows.  It will make its own partitions.  It will install grub and give you the dual boot--you won't have to do anything.  You know that if you're reinstalling (sorry).

It will overwrite the old os or it will install on the deleted partition, (free space)  whichever is needed.  [I]

 <<<I tried to reinstall ubuntu 11.04 over the upgraded 11.10, but the  installation GUI  stopped when** I clicked continue button after it had  confirmed free disk space,** power source connection and network  connection - **I had not chance to reach the screen to allocate disk  space.**[/I]**>>>**

I don't understand what happened here.  It sounds contradictory to me.   It shouldn't continue until you'd chosen where to put it, but you had if you clicked 'continue'.  If you only have Windows, choosing side-by-side is the easiest for new users but make** sure** the second partition is truly gone or it will install **inside the **Windows partition, side-by-side-- leaving the empty partition still empty--bad.    According to the size of the windows partition, they may end up being pretty small partitions.

You should see only windows taking all the space in disk utility.  If there is still an empty 2nd partition, choose that when installation asks where you want it installed.

If all this confuses you let me know, I'll try to explain it clearer.  lol

---

