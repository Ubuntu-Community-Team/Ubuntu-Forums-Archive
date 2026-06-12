---
title: "recycling splash screen - after upgrade to 9.10 Karmic"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by daklein on 2009-12-30
Hi,  I have upgraded to 9.10 from 9.04 working installation, using update manager.  Have intel 82865g integrated video.   Not able to boot normally to the graphical interface login panel.

After grub screen, it shows momentarily which partition it's booting (I think that what it says, it's fast),  then one time shows the ubuntu three people in a circle icon.   next it shows the pretty ubuntu (is this the usplash screen) screen, a soft light illuminating the ubuntu name from above, with the moving line underneath.    after 5-10 seconds, the screen goes blank, and the pretty ubuntu splash screen shows again.    for another 5-10 seconds.  ad infinitum.

selecting older kernels in grub give basically similar behavior, won't get to login panel.

I can boot using the recovery kernel option, and startx will work (as root at least).  the /etc/X11/xorg.conf file looks normal, it is the default failsafe one.

any help or advice is severely appreciated in advance.   thanks,   Dale

---

### Post by phillw on 2009-12-30
Hi & welcome to the forums,

If you head over here --> [http://ubuntuforums.org/showthread.php?t=1144761](http://ubuntuforums.org/showthread.php?t=1144761)

I'm hoping you'll be pleasently surprised - just have a read through the posts until you get to the end :)

If you're still stuck, post back & we can have a further look - but it looks like they got it solved.

Regards,

Phill

---

### Post by daklein on 2009-12-30
Thank you for the advice, I'm sorry still doesn't work though. 

it did have already the latest xserver-xorg-video-intel, according to apt.
but for fun, I removed it and installed again with apt
>sudo apt-get remove xserver-xorg-video-intel 
   this also removed xserver-xorg-video-all, so added that back also
>sudo apt-get install xserver-xorg-video-intel
>sudo apt-get install xserver-xorg-video-all

rebooted that way, and still same.

next, added this line 
  Option "DRI" "off" 
to device section of /etc/X11/xorg.conf,   per 9.04 release notes  [http://www.ubuntu.com/getubuntu/releasenotes/904#Display%20freezes%20with%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Display%20freezes%20with%20Intel%20graphics%20cards)

rebooted again, still same.  normal boot after grub screen keeps the fancy ubuntu with line screen for about 10 sec, then goes all black screen for about 2 sec, then the fancy screen again, repeatedly.

any more suggestions please?  :confused:

---

### Post by daklein on 2009-12-30
seems like this must be fixed already, do I not have the correct sources selected (proposed and backports)?    

I selected proposed and backports, and then ran update manager.  there are updates to xserver-common, xserver-xorg-core,    maybe these will make the difference?

and the answer is:    doa!!!   no,  still about the same.       it repeatedly shows the splash screen.

---

### Post by daklein on 2009-12-30
Next I tried the advice at the end of this thread, removing GDM.
[http://ubuntuforums.org/showthread.php?t=1335435](http://ubuntuforums.org/showthread.php?t=1335435)

when running the cmd to install WDM, it brought up a text gui and allowed a choice of KDM or WDM.   at first I chose KDM.   it also fails in the same way, keeps looping and not getting to the login panel.  (only difference is the pretty blue kde theme splash screen, ooh, fancy).     so then removed KDM, and installed WDM.    this did work, at least normal users can log in.   it's a little rough though, logging out of one user, then try to login in another user and it hangs on the login gui panel.

how could I figure out why GDM is not getting to the login panel.       seems to be a problem with GDM.            

Thanks!  Dale

---

### Post by daklein on 2009-12-31
so next, I read through here:    [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

and did workaround 'a',  (after re-installing gdm to create the problem again...)  and then editing xorg.conf to specify vesa.

now it will bring up gdm login panel and allow login

any advice welcome please.   but I guess this might be solved enough for me.  seems to work.  little sad that it took a couple days to figure it out.

---

