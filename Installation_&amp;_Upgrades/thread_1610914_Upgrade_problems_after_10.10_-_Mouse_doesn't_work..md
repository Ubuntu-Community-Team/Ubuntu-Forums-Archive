---
title: "Upgrade problems after 10.10 - Mouse doesn't work."
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Hangwire on 2010-11-01
Hi people, after I upgraded from 10.04 to 10.10, the left click on my mouse does not work. I can right click anything i want but I cant select it, nor can I click on icons. Is there any way to return gnome to its default settings, since my desktop has been customized and maybe the upgrade wasnt too happy about that.

Any help or suggestions are welcome. :)

---

### Post by Hangwire on 2010-11-01
Bump?

---

### Post by LordOfTheBoards on 2010-11-01
Hi!

Have the same problem on my desktop, which was upgraded through the command line. The mouse works perfectly on my laptop with a fresh 10.10 install. Would love to see a solution!
lotb

---

### Post by Hangwire on 2010-11-01
another shameful bump

---

### Post by Hangwire on 2010-11-01
> **Hangwire said:**
> another shameful bump

yet again...

---

### Post by Hangwire on 2010-11-04
This has happened after a fresh install of Ubuntu now. 
I went back to 10.04 in hopes of the problem never happening again. 
Please, someone must report this as a bug.

---

### Post by mörgæs on 2010-11-04
Your bumping does not help getting answers. It only annoys people who might otherwise answer.

> **Hangwire said:**
> Please, someone must report this as a bug.

'Someone' should be you, since you are the one who knows the error best.

---

### Post by Hangwire on 2010-11-04
First of all, bumping is a way to up the topic - a person that knows and has confronted the issue might be online on a different time than when I posted the topic. It will probably sink by then. 

Second, you could give me a link, since im new to linux and the ubuntu community. Me and google will do that though.

Third, if there are truly people that get annoyed by questions they know the answer to when bumped, I doubt they have great social skills. Also, do not speak for a wide range of people.

Bug will be reported.

---

### Post by johnerskine2010 on 2010-11-05
I'm having a similar problem with my upgrade from 10.04 to 10.10, except my keyboard doesn't work as well.

See here

[http://ubuntuforums.org/showthread.php?t=1612593](http://ubuntuforums.org/showthread.php?t=1612593)

This seems to be a common set of problems.

---

### Post by SteveHillier on 2011-06-02
I had this problem.  Broken mouse, broken keyboard.
I plugged a different USB mouse in the front USB and the mouse worked.  
I grovelled on the floor.  Unplugged the mouse from the back of the computer and plugged it in again.  It worked.
I did the same with the keyboard and it worked.  No more that 2-3 minutes after the upgrade it was working without problems.

---

### Post by MickeyPilgrim on 2011-06-02
I am having a similar problem after upping from 10.10 to 11.04  The mouse clicks are not effective. I'm locked out and after a day and a half am beginning to doubt I'll ever see my Evolution e-mail again.

The real bug seems to be that Ubuntu invites us to click a button and upgrade. That's just bad. It looks like the only reasonable way is to back up all files, e-mail, bookmarks, etc. and then do a new install

MickeyPilgrim

---

### Post by scruffyeagle on 2011-08-22
> **Hangwire said:**
> Hi people, after I upgraded from 10.04 to 10.10, the left click on my mouse does not work. I can right click anything i want but I cant select it, nor can I click on icons. Is there any way to return gnome to its default settings, since my desktop has been customized and maybe the upgrade wasnt too happy about that.

Any help or suggestions are welcome. :)

I came here to post about a similar problem in a fresh install of v10.40 LTS. I'm currently working on a Toshiba Satellite A205 notebook, w/ a Logitech marble mouse on USB (much better than touchpad!). The modifications I've done to customize the installation so far are:
*) Let the Update Manager do an automated update
*) Removed Assistive Technologies (can't stand that AT API bug that makes other programs & the desktop freeze),
*) Installed gufw & activated firewall
*) Created 2nd profile to be Admin, and changed 1st profile to be User
*) Installed Gimp & Inkscape w/ extras
*) Installed ALSA extras
*) Adjusted mouse to be left-handed w/ longer double-click on both profiles
*) Changed the desktop theme to Clearlooks w/ customized colors on both profiles
*) Adjusted font sizes everywhere on both profiles
*) Customized Firefox w/ NoScript, AdBlocker, & Image Zoom on both profiles

I'd gotten into setting up a profile in Evolution Mail, in the User profile. I'd adjusted all the Preferences. I'd adjusted the layout of panes. I was adding (currently empty) folders as subfolder under Inbox as storage locations for filing email. I was working fairly quickly. I'm not the world's greatest typist and this laptop keyboard isn't the same as working on a regular keyboad, so I may have accidentally hit some key combination (Ctrl/something?) to cause this problem...?

Anyway, I found that suddenly the menu-click wouldn't work. I could select existing folders, but not get the menus via the mouse. I screwed around with various Ctrl/Alt/Shift/Click combinations, and couldn't get the menu-click function back. I decided to exit Evolution for restarting it, hopeing that would restore mouse functions in the program. I discovered that the menu bar items wouldn't react at all to the mouse. I used Alt-f and got the File menu to drop down, then discovered that the menu bar was now reacting to the presence of the mouse pointer. Going back to the folders list, I could select them but not get menus - and, once I'd clicked on a folder, the menu bar was again unresponsive to the mouse. Note, there were also times when nothing at all would respond to the mouse, including the window controls, and the program's title box in the bar at the bottom of the screen. I eventually closed Evolution by using the Alt-f to get the file menu, and then selecting "Quit".

What seems significant, is that the mouse disfunctions continued after Evolution was closed. I decided to come here to the forums to post an inquiry, seeking help. After starting Firefox, the menu bar wasn't reacting to the mouse. I got into my bookmarks by using an Alt key combination. Working here in the forums, the mouse seemed to regain functions. Before posting, I searched thread titles, looking for threads that seemed to be on similar subjects. (That's how I found this thread.)

I don't know if the mouse disfunctions are going to continue once I finish posting this and exit Firefox, or whether they'll continue once I reboot the system - but, if anybody can help me resolve this, I'd be very grateful.

---

### Post by scruffyeagle on 2011-08-22
I'm back again, w/ something strange to add. After I'd shut down the Toshiba machine, I connected the marble mouse to my Dell Inspiron 9400, and turned that on. First thing I did, was open up Evolution for doing my mail. I replied to an email I received, created a new subfolder for filing messages - and, THE MOUSE QUIT WORKING PROPERLY. The pointer could be maneuvered normally, but it was as if the clicks simply weren't being processed. I ended up exiting Evolution w/o finishing my email, because of that. Starting up FF to come here, the mouse still wouldn't work right. It activated FF, but it took 3 clicks on the icon to do it. I ended up shutting down FF. Trying to exit the Ubuntu session, it wouldn't work right. But, after a few attempts at it, when I clicked on the power button, I got a small drop-down menu as if I'd done a menu click there. I didn't want that, and clicked on an unused space in the middle of the top bar. Right after that, the mouse started working properly again.

This machine also is set up w/ v10.04 LTS - but, it's a completely different machine. The fact that the same disfunction is occurring on both machines, when doing the same function, in the same program, can't be a coincidence. I've done creation of multiple subfolders in an Evolution mail folders list more than once previously, but I've never seen this mouse problem before now. I did email yesterday, but today was the first time recently that I've actually sent a message outbound. (It was sending a message, that gave me a "sent" email needing a new subfolder for filing it into.) My Dell system didn't download anything today, re. software updates, but it did yesterday. The Toshiba downloaded updates today, during installation setup.

I think this is the proper question: Was there an update released recently, for Evolution? If the answer is "yes", then it should be withdrawn and the previous version restored immediately. Because, I think that's the cause of my mouse problems.

Important question: Is there any way to reverse recent updates in software?

If there is, then please explain to me exactly how it's done. A recent update is the ONLY possible explanation for a problem I've never seen before occurring on 2 entirely separate installations, while doing exactly the same tasks, in the same program, on different machines.

I suppose it would be proper procedure, to have others verify that this problem is also on their machines now. I'm fairly sure it's connected with / caused by the creation of subfolders in the folders list. I should also mention that I did manage to make at least 8 or 9 subfolders in a row, before the 1st instance of this problem disrupting the workflow. And, restarting Evolution, I was able to make just one subfolder before it happened. It's also possible it's connected with the steps off the root. In this case, I was making subfolders 3 tiers deep away from root; for example: Inbox/Family/Heather/Received from Heather.

It occurs to me now, that I really should have made this the intialization of a new thread, since I've become convinced it's a bug in Evolution. But, I don't know how to change it to being that, after being posted in this thread, and I know there's general rules against duplicating posts. Maybe, a moderator would want to do this change?

---

### Post by jediknight64 on 2011-08-22
> **MickeyPilgrim said:**
> I am having a similar problem after upping from 10.10 to 11.04  The mouse clicks are not effective. I'm locked out and after a day and a half am beginning to doubt I'll ever see my Evolution e-mail again.

The real bug seems to be that Ubuntu invites us to click a button and upgrade. That's just bad. It looks like the only reasonable way is to back up all files, e-mail, bookmarks, etc. and then do a new install

MickeyPilgrim

Hi. I've encountered this problem in the past with 10.04 and this seems to work for both the mouse freeze and the keyboard freeze.

 
-Open a terminal <Cont+Alt+t> on your keyboard
-type "sudo rmmod psmouse"
-press enter
-type in your password when asked
-press enter
-type "sudo modprobe psmouse"
-press enter

  Hopefully, this should unfreeze your mice!

---

