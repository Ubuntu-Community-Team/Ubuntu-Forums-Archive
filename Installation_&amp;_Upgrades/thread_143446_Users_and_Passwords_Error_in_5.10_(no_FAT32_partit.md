---
title: "Users and Passwords Error in 5.10 (no FAT32 partition)"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by Sigmund on 2006-03-12
I've been trying to install 5.10 on my ThinkPad R40 for the last couple of days and I run into the same problem over and over. When prompted to enter a username during install I keep getting looped.  I enter the full name 'Operator' the username 'operator' and a password, but it keeps sending me back to the first prompt to add a new user.  I've tried everything from simple to complex names and simple to complex passwords.

I've read through a lot of threads.

[http://ubuntuforums.org/showthread.php?t=125200&highlight=username](http://ubuntuforums.org/showthread.php?t=125200&highlight=username)
[http://www.ubuntuforums.org/showthread.php?t=134430&highlight=user](http://www.ubuntuforums.org/showthread.php?t=134430&highlight=user)
[http://www.ubuntuforums.org/showthread.php?t=123425&highlight=user+creation+problem](http://www.ubuntuforums.org/showthread.php?t=123425&highlight=user+creation+problem)

Several people have the same problem, but here's the kicker... I do not have and have never had a FAT32 partition on this machine.  I first tried dual booting with windows (NTFS) but grub didn't like it so I formatted the disk as so:

size mount point format
5GB         /        ext3
30GB    /home     ext3
1.5GB  Swap        swap

I've reinstalled several times formatting the entire disk each time, sometimes using a custom partition set up (as above), and sometimes accepting what the installer sets up.  I still get stuck in this same loop.  If I just 'go back' to the install menu and skip the step I can install, but when I reboot and finish the install I cannot log into the ubuntu desktop, and on one occasion I was left with only a breezy badger prompt asking me to login, never even got to a ubuntu graphic login.

I'm new to linux but not totally new.  I've installed Suse and Mandrake on this machine in the past, but thought I'd try Ubuntu.  I've searched this site and some other's but can't find much info since I don't have a FAT32 partition.  Sorry if it's been covered, but I can't find it.

Thanks for any help you can give.

---

### Post by taurus on 2006-03-12
Try using another name instead of operator to see if you still have the same problem.  Use something like sigmund!!!

---

### Post by Sigmund on 2006-03-12
Yeah, I tried several usernames of various complexities and they all did the same thing.

I was guessing that maybe the names were being stored, and the installer was screwing up so I entered 'root' and a password.  Then went back to the install menu and carried on.  At somepoint during the install (sorry wasn't taking notes) I went to the prompt (Alt-F2?) and logged in as root and did adduser.  I tried to make a username 'operator' but got an error saying something like 'the group 'operator' already exists and cannot be created.  Which is odd because it should have been created as a username not a group. I then entered another name 'gtemp' and was able to create a user with that name.

After the install when it came to loging into ubuntu I was note able to log in as 'operator' or 'root' (I'm still not clear on how ubuntu handles root, but I know the info is available), but I was able to log in as the 'gtemp' name I created with adduser.  That got me into gnome and lets me run programs etc, but I cannot seem to access any system tools. I also have no access to anything in the System/Administration menu, so I"m thinking this 'gtemp' username I made isn't made properly. If I go to the updates button in the upper right I can click "show updates" and it prompts for my password but then does nothing.  I clicked 'install all updates' and played around some more to no effect.  I rebooted hoping that something might happen, and it did.  The computer downloaded a ton of updates so I'm thinking that I have some admin access, but not much.  I'm also now running edubuntu for some reason, which is pretty and all, but slightly less manly than I would like.  

Linux, it's like walking through a jungle with good directions and a general idea of where they'll lead, but then a crazy dude runs up and kicks you in the nuts.

---

### Post by Sigmund on 2006-03-12
Well on my fourth or fifth install attempt I was again able to make a username though the console, by using the expert install mode and switching over to the console after a segment of the install was completed.

I added a username and made it a part of the root group (bad idea?) and that worked a bit.  I was able to log in, but still had no ability to access system tools.  I did a sudo users-groups and opened the user manager that way hoping to be able to add some capabilities to my username.  Besides setting my username to be able to use all the devices and whatnot I never saw an option to add administrative privleges to myself.

I'm trying another install and I'll let the computer do it's thing on this one.  If anyone knows that I'm screwing something up or missing something, let me know cause I'll listen.

---

### Post by Sigmund on 2006-03-12
[QUOTE=taurus]Try using another name instead of operator to see if you still have the same problem.  Use something like sigmund!!![/QUOTE]


You're screwing with me right?  You are literally messing with my mind here.

I reinstalled, let the computer do whatever it wanted and entered 'sigmund' as the username.  No looping back, no problem at all.  ubuntu installed, got to the desktop, I can use the system utilities.  Wow.

I also happened to use a 10 digit alpha and numeric password, vs the 5 digit alpha password I've been using.  I think that had more to do with it than the username.

If that's the case I highly suggest updates to include a note in the installer that you must enter a complex password.  There's no mention of that now.

---

### Post by bdmp on 2006-04-06
I am having the same problem. I don't have a fat32 partition but I do have a fat32 drive. I wonder if that could be it. I really don't want to reinstall. Help me.

---

