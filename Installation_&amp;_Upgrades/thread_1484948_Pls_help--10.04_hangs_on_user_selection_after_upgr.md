---
title: "Pls help--10.04 hangs on user selection after upgrade"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by ysaric on 2010-05-16
I recently went the upgrade route and something went wrong either with the download or the installation or 10.04 and my hardware are having issues.  I am looking for some advice for either fixing what is wrong or getting some additional data backed up to USB before wiping the partition and starting new.

My computer is dual-boot using Grub2, the other OS being Windows Vista.  I can get to Windows Vista fine via GRUB.  When I select Ubuntu (says kernel 2.6.31-21) though I don't get very far.

At this point I can get 10.04 all the way to the user selection screen, where it immediately freezes, forcing a hard reset.  I can boot into recovery mode, but if I select failsafeX it freezes at the first screen that comes up--the notice you are running in low res graphics mode.

When I did the upgrade from 9.10 to 10.04 I used the update tool in Ubuntu.  However I also now have a 10.04 install CD.

My graphics cards are twin NVidia 9600s in SLI.  I would say it is a graphics card problem since the first graphical screen that comes up both in regular boot (the login screen) and failsafeX (the notice screen) I get a hard lock.  However booting off the CD it loads the desktop just fine!

I would just wipe clean however my last data backup was partial and there is some stuff I would like to go back in and get.  However neither method I have used to try and go back in to get what I need has succeeded.  I have a 320G USB drive I use for backing up certain data.  If I boot using the CD, it gives me an error message about the isntaller then goes to desktop (which works fine, even though I can't get past the login screen when booting 10.04 from the hard drive)  I can then plug in the USB drive fine and it shows up, but some of the files on the Ubuntu installation don't give me permission to copy them. There is an 'X' on the icon and I don't know whether there is a way to get me authenticated in order to copy them from the CD desktop.

Alternatively, I can get to a root prompt if I boot into recovery mode (not the CD, just recovery mode from GRUB). I assume I can move them from there and that the permissions issue won't be a problem but when I plug in the USB drive I don't get any errors but I am not seeing it show up in /media.  Also if I put a DVD-RW (all I have on hand) into my DVD-RW drive maybe I could back the data up to that, but I'm not familiar with how to do that from the command line.

If I could get to a point where I could verify that I have this extra bit of data backed up then I wouldn't have any problem wiping the partition and starting over.

So, any bit of advice on either of these--either the freeze problem or the backup problem, that would be super much appreciated.

**Just as a note, I am not a Ubuntu expert but I can find my way around pretty well.  If there is some additional information I can get, I would be happy to try.

---

### Post by bruceschaller on 2010-06-06
I have the same problem and there is a workaround for actually using the system.  

On boot, select recovery mode.  
Then select drop to root prompt with networking.

type 'login'
enter username and pw

type 'startx'

that should get you back into gnome.  it's kinda a pain, but it works and you don't need crazy technical know-how.  I'll try running an update and see if it works itself out....ya never know...

good luck!

---

