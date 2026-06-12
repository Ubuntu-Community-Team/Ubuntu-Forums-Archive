---
title: "Jaunty Boots to a black screen with cursor"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eluminx on 2009-04-18
I need some help, about 3 days ago i installed some updates to my Jaunty 64bit box.  I forget exactly what updates they were.  So i kept using the box as usual, after about a day i decided to restart the box due to other reasons.  The process proceeded as usual, it got up to the logon screen.  So i input my name and pw,, but after that i am greeted by a black screen with nothing but a cursor.  Is not the circle (it's thinking) cursor is the regular arrow like cursors icon. It never reaches a desktop, i am able to move the cursor around but the black screen remains for as long as i leave the computer on.

I've logged in recovery mode and did some updates today but unfortunately the issue still persist.  Anyone have any suggestions that's not to reinstall (yet)?

---

### Post by eluminx on 2009-04-18
So i been researching as much as possible but the threads that i find are only talking about intel graphics.

My config is jaunty x64, C2D, ECS Mobo, NVidia 8600gs, 3gig ram, 1x120hdd, 1x250hdd and 1x640hdd.  I tried removing compiz, and compiz-core by logging into tty1, but still no dice.

---

### Post by SpenceMakesSense on 2009-04-18
I have the same problem with 32-bit any help?

---

### Post by olskar on 2009-04-18
Cool, I posted about this in General Help earlier today since I had the problem in Intrepid; [http://ubuntuforums.org/showthread.php?t=1129265](http://ubuntuforums.org/showthread.php?t=1129265)

I have since done everything I can think off. Actually all the threads (not many) I have found on this talks about nvidiacards. That is something we have in common.

I have now installed xubuntu-desktop and choose that in the gdm to have at least something to work with. Does that work for you? That would show it is a gnome-related error.


Will reinstall later.

---

### Post by bennachie on 2009-04-18
I occasionally experienced what may have been a related in 8.10 (the usual symptom was not a black screen, but one having only a background and white bars at the top and bottom). However, the glitch has not (yet?) struck in 9.04. Incidentally, I never experienced either version of the lock-up in Fedora installations with parallel versions of the Gnome desktop, so the problem may relate to some interaction between Gnome and Ubuntu, rather than being simply a Gnome issue.

My usual recourse was to shut down and restart, being particularly careful not to touch the mouse or keypad until the complete desktop appeared. Have you tried <alt-sysrq-k> (the unlikely successor to <ctrl-alt-bksp>)?

---

### Post by eluminx on 2009-04-19
> **olskar said:**
> Cool, I posted about this in General Help earlier today since I had the problem in Intrepid; [http://ubuntuforums.org/showthread.php?t=1129265](http://ubuntuforums.org/showthread.php?t=1129265)

I have since done everything I can think off. Actually all the threads (not many) I have found on this talks about nvidiacards. That is something we have in common.

I have now installed xubuntu-desktop and choose that in the gdm to have at least something to work with. Does that work for you? That would show it is a gnome-related error.


Will reinstall later.

Well unfortunately i can't change the WM from gdm since the skin/theme i set for it doesnt have the choice to change the WM.  I uninstalled the nvidia drivers to see if that was the issue, but it didn't help.  Here is another odd bit, when i start up in recovery mode and i type startx at the command line, i get a desktop BUT my mouse and keyboard are frozen therefore useless.  Does anyone else get this???

---

### Post by olskar on 2009-04-19
> **eluminx said:**
> Well unfortunately i can't change the WM from gdm since the skin/theme i set for it doesnt have the choice to change the WM.  I uninstalled the nvidia drivers to see if that was the issue, but it didn't help.  Here is another odd bit, when i start up in recovery mode and i type startx at the command line, i get a desktop BUT my mouse and keyboard are frozen therefore useless.  Does anyone else get this???

All you have to do is edit your /etc/rc.conf. Look for the line that begins with XSESSION= and just replace gnome

---

### Post by eluminx on 2009-04-19
> **olskar said:**
> All you have to do is edit your /etc/rc.conf. Look for the line that begins with XSESSION= and just replace gnome

simple as that huh?  Thanks i will give this a go.

---

### Post by eluminx on 2009-04-20
k so i am back with more trouble, i tried looking for the rc.conf file but it was not in the /etc directory.  It was actually nowhere to be found.  But thats not the problem any more, i went ahead and reinstalled ubuntu, since i have a /home in a separate partition, but here is my problem now.  With the fresh install of ubuntu 9.04 i still just get a black screen and no desktop.  But i installed Xubuntu-desktop to see if that would work, when i tried to log in it spews some errors about it being unable to access my /home files and folders (pictures, music, etc etc).  So i fired up my live cd again and tried to view my /home partition and all that is showing is 2 files a readme file and a Access your private data file.

Now i know what these are, but i remember setting this up about a month ago and i had never had problems before.  So now i don't see any of my files i had in my /home partition and i cant access the partition with xubuntu.  Does this mean my files are gone or are they just encrypted and if they are encrypted how do i access them with a new ubuntu installation?

I tried to activate the private folder but it just kept saying the pw was wrong when i know is right because is the same pw i use to log in to my ubuntu installation.  Besides the only reason i set this private folder up was just to see how it worked i never even used it or put any files in it.

Any help would be greatly appreciated it, hopefully i dont have to format my /home partition just yet, i have plenty of files i need in there.

---

### Post by arqbrulo on 2009-04-22
Well, I will not be able to help you with your latest problem, but I might have found out what's wrong with your original problem. One of the posts said something that all posts on another thread had an Nvidia card in common. Well, earlier today I did a system upgrade on my 9.04RC and I only had one package to upgrade "nvidia-common". After restarting my system, I was on the "black with cursor" screen. I went to my command line and removed "nvidia-common" restarted my gdm and everything started working again. I think that's where the problem is.

---

### Post by eluminx on 2009-04-22
> **arqbrulo said:**
> Well, I will not be able to help you with your latest problem, but I might have found out what's wrong with your original problem. One of the posts said something that all posts on another thread had an Nvidia card in common. Well, earlier today I did a system upgrade on my 9.04RC and I only had one package to upgrade "nvidia-common". After restarting my system, I was on the "black with cursor" screen. I went to my command line and removed "nvidia-common" restarted my gdm and everything started working again. I think that's where the problem is.

Well unfortunately i re-installed jaunty a day ago so i was unable to try this solution, but i appreciate you taking the time to post it.  

I was able to get my desktop back up and running with Gnome now, but the lost files still persist.  I have the .private folder and i see that is about 18gigs big, so hopefully all my files are still there.  I was able to mount it but it still shows up empty.  I hope the files havent been corrupt yet, i'm hoping someone can help me try to recover those files.

---

