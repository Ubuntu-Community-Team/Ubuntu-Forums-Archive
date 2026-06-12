---
title: "exits back to login screen after boot"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by pgagy on 2010-11-21
I had Kubuntu 10.04 installed, I screwed up a bunch of stuff in it and it would hang after the login screen.  I reinstalled Kubuntu 10.10 (formatted the partition with Kubuntu on it) but I kept my /home partition in tact.  

NOw, when I log in, i starts to load, and then KICKS ME OUT, back into the log in screen.  The user does exist, I can access the user from the console, but when I try to get into Kubuntu, it kicks me back out to login.  What on earth is going on?

I've tried failsafe mode as well as regular login. neither works.

---

### Post by pgagy on 2010-11-21
Could this possibly have something to do with permissions?

---

### Post by pgagy on 2010-11-23
Here's what I did to fix it.  Since nobody helped, I kind of hacked away at it and now it's sort of back up.  

If this happens to you, you can try these steps.  I have my /home on a separate partition, so this may not work for you if you don't.  I heeded that tip when I installed linux, and it paid off.

Also, this problem persisted EVEN AFTER I reinstalled Kubuntu, so eventually I found out it was one of the the /home dirs that had some information in it that was screwing everything up.

Anyway, here's what you can do - there is an easier way (in hindsight below) but this is what I did.  

1. reinstall Kubuntu in the old Kubuntu partition, and create a NEW /home directory (doesn't matter if its a separate partition or not.  )  During the install, make sure you tell the system to mount your "broken /home" as /oldhome or something like that.  

2. once you boot into the new kubuntu, with the new data, open two instances of the file explorer (dolphin), and click on view and choose show hidden files.

3. go to your /oldhome/username dir in your root folder (/) in one instance of dolphin and go to your new /home/username

4. look at all the files and folders that start with a dot in your /home/username, and copy them over to your /oldhome.  Make sure to overwrite all the files.

5. Once you do this, reinstall kubuntu again (yes, I know, a pain), but this time, choose your actual home partition as /home.

6. when you boot into your new kubuntu system, you still have your /home in tact, with most user data, so if you install firefox/thunderbird/vlc/whatever, it will all work as it used to before.

EASIER WAY.

(not tested, but try it)

Boot into a live CD of the same version as your current install

Copy all the files hidden files to your original home (probably stored under /media/drivesomething/home/username/) using same steps as above.  Although you may have to be sudo and use the terminal to do this - not sure.

This way, you don't need to install/reinstall the system.

---

