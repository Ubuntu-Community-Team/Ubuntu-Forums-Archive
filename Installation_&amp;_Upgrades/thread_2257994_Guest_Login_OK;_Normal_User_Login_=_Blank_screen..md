---
title: "Guest Login OK; Normal User Login = Blank screen."
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by Kurt_Alan on 2014-12-24
I just did a clean install from UNetbootin on a flashdrive of Xubuntu 14.04, 64 bit.  After several reboots during the config process, after logging in successfully to my user account I arrive at at my default xfce desktop wallpaper, pointer, no right click and no panels. I don't know how to access a terminal.

I am functional in Guest account except that I do not have permission for sudo.  And I can even see the programs that I installed my my user account.

I know there is a thread here on this topic, as well as other places, but I am having trouble understanding some of the solutions and/or they are more complicated (for me) than a reinstall.  But I'd rather fix the problem, so I am starting fresh with this post.

---

### Post by ajgreeny on 2014-12-24
It sounds as if the window-manager is not running and a simple command should get you going again.
However, I can't remember the default keyboard shortcut for a terminal in Xubuntu as I change several of my shortcuts to what I have been using for many years, but try **Ctrl+Alt+T** or **Windows-key+T** and then run command **xfwm4** to get the window manager running; it sounds as if it has not started at login for some reason.

**Alt+F2** may get you to the "Run" dialogue where you can also run command xfwm4, but I'm not sure if the Alt+F2 depends on the window-manager; worth a try.

If lack of window-manager is the problem it will hopefully always run at startup once you get it running again from this attempt.

---

### Post by Kurt_Alan on 2014-12-24
@ajgreeny --

Thanks. I shall try this now. If the keyboard shortcut doesn't work I'll try your recommended command via cold boot, Shift, Recovery, mount, command. Just found a post this morning from someone else with the same problem. Weird.

---

### Post by Kurt_Alan on 2014-12-24
> **ajgreeny said:**
> It sounds as if the window-manager is not running and a simple command should get you going again.
However, I can't remember the default keyboard shortcut for a terminal in Xubuntu as I change several of my shortcuts to what I have been using for many years, but try **Ctrl+Alt+T** or **Windows-key+T** and then run command **xfwm4** to get the window manager running; it sounds as if it has not started at login for some reason.

**Alt+F2** may get you to the "Run" dialogue where you can also run command xfwm4, but I'm not sure if the Alt+F2 depends on the window-manager; worth a try.

If lack of window-manager is the problem it will hopefully always run at startup once you get it running again from this attempt.

@ajgreeny --

Follow-up to your suggestions:

--Keyboard commands are operational in Guest log-in but sudo is disabled by default.
--Keyboard commands are NON-operational via User, where I'm having my problem.
--Command is available in Recovery Mode.  Command ```
 sudo xfwm4
``` failed with this message: ```
 Gtk - WARNING **: cannot open display 
```

Any other ideas??

I'd like to fix the problem rather than re-install.  If I re-install and this problem re-occurs again, I'm back to square one. Besides, another poster here is having the same problem!

---

### Post by MAFoElffen on 2014-12-24
Go to the second post in my sticky (link in my sigline). In that post, look for the link to the instructions to remake and set permissions for the `/.Xauthority file. Since it is working in guest, the driver is working, so it seesm to point to a problem with user permissions or profile. Most of the time it is permission with the .Xauthority file.

If you can only get to that via root from grub rescue menu, then after following those those instructions, follow those up at the root prompt via:
```

chown <userName> /home/userName/.Xauthority

```
replacing userName with the name of the user...

Also in that post, if for some reason you need to go in as a Single mode, there is a link to instructions to boot into single mode...

If, for some reason, the only way you can get is using a guest account... let me know and I'll tell you how to get to a root prompt from there.

---

### Post by ajgreeny on 2014-12-24
You could try the following commands from the command line you get to from Ctrl+Alt+F1 after logging in there with username and password (password will not show on screen, just like terminal)

  ```
ps aux | grep xfwm4
xfwm4 --replace
```

  The first will give you two lines of output if it is running, something like
```
<user>    2075  0.0  0.1 166932 13280 ?        S    10:17   0:03 xfwm4 --replace
<user>    6316  0.0  0.0  18940   916 pts/1    S+   22:15   0:00 grep --color=auto xfwm4
```
The second restarts xfwm4 if it is not running.  If it's not running the previous command gives just a single line of output; the second of the two in my example.

---

### Post by Kurt_Alan on 2014-12-24
> **ajgreeny said:**
> You could try the following commands from the command line you get to from Ctrl+Alt+F1 after logging in there with username and password (password will not show on screen, just like terminal)

  ```
ps aux | grep xfwm4
xfwm4 --replace
```

  The first will give you two lines of output if it is running, something like
```
<user>    2075  0.0  0.1 166932 13280 ?        S    10:17   0:03 xfwm4 --replace
<user>    6316  0.0  0.0  18940   916 pts/1    S+   22:15   0:00 grep --color=auto xfwm4
```
The second restarts xfwm4 if it is not running.  If it's not running the previous command gives just a single line of output; the second of the two in my example.

@ajgreeny --

From recovery mode, the first code did give me the output you described.  However, the second code gave me the same error message as before, "cannot open display."

---

### Post by Kurt_Alan on 2014-12-24
> **MAFoElffen said:**
> Go to the second post in my sticky (link in my sigline). In that post, look for the link to the instructions to remake and set permissions for the `/.Xauthority file. Since it is working in guest, the driver is working, so it seesm to point to a problem with user permissions or profile. Most of the time it is permission with the .Xauthority file.

If you can only get to that via root from grub rescue menu, then after following those those instructions, follow those up at the root prompt via:
```

chown <userName> /home/userName/.Xauthority

```
replacing userName with the name of the user...

Also in that post, if for some reason you need to go in as a Single mode, there is a link to instructions to boot into single mode...

If, for some reason, the only way you can get is using a guest account... let me know and I'll tell you how to get to a root prompt from there.


@MAFoElffen --

From recovery mode, I entered ```
 chown lucas /home/lucas/.Xauthority
``` and the result was "changing authority of."  However, after loggin on to User, I am still left with my default desktop but no panels and no right click function.  Now, maybe I jumped the gun.  I am now going to follow up on your reading suggestions and see if I missed something. I will report back.

---

### Post by Kurt_Alan on 2014-12-24
@MAFoElffen --

Reporting back.  I read your essay "Reset Authorities Profile for Logging into X."  From Recovery root, I entered ```
 sudo rm .Xauthority 
``` per your first of four suggested lines but the syntax must have been incorrect as I received a "no file" response.

I don't understand why the issue is with permissions. My password is accepted under User and I have no difficulty logging in.  The problem is with missing session items . . .

---

### Post by MAFoElffen on 2014-12-25
In the linux graphics layer You have Grub2, the Linux Kernel and XServer. KMS spans netween the three to carry over graphics options. Between that and your desktop, you have the graphical login manager. After-market video drivers attach as modules through XServer and the kernel... The Desktop, which XFCE4 is, goes on top of that layer.

There is global services that affects the computer overall for all users and services. Then there is settings that are different for each user and have profiles for each user.

.Xauthority is one file that XServer checks for the user that is logged in. It checks for permissions for that user each time it starts. That is a file that sometimes gets boinked during updates. Most common is that updates are done with root permissions, so sometimes the ownership of that file mistakenly gets changed to root... So when  user tries to log into there own, they get a message saying X can't start, because there is a permission problem with their own profile file. If that file is not there, XServer will not start... with no Xserver, nothing for other layers (like the desktop) to bind to.

The "." in the start of a Linux file name, denotes that file as a hidden file or hidden directory. Since that file for that user is now confirmed as being okay, the next logical diagnostic step would be to suspect the desktop profile file for that user. The good thing about user profiles, is that when a new user is added, those profiles do not exist. Meaning, the first time they use something and change something, a new profile is created. Sooo... if a profile file got corrupted, if you delete it and restart that program, it will recreate a new profile with default values and properties. (At least for graphics and browsers...)

Those profiles setting for your desktop and other various programs are contained in two different hidden directories: "~/.cache" and "~/.config"... Most people will tell you to delete both those directories. BUT, that will reset everything for that user, except the desktop. 

So... if you got panels back, but they are screwed up... just delete the desktop profile for that user by:
```

rm -rf /home/userName/.gconf
rm -rf /home/userName/.gnome

```
Change the userName to the name of the user.... Some guides also say to remove ".gnome2"... but that contains keyrings and sometimes cause their own other kinds of problems if removed. i only delete that after doing the above and testing that first. That should reset the desktop to show again as with default settings. Most Profile files are actually changes from a program's fresh installed defaults.

EDIT-- This could have been much shorter, but I always figure not to assume... and that some one should understand what they are doing, instead of doing something blindly.

---

### Post by Kurt_Alan on 2014-12-27
@ MAFoElffen and others who have helped with this problem . . . 

No, I appreciate the extensive explanation. Unfortunately, although your recommended solutions "took" in recovery mode, they had no effect on my problem.  So I decided to reformat and start over.

If you google: "Xubuntu no panels" you will find that this has been an Xubuntu problem for several years.  There seem to be various "solutions," effective for some; others not.

Xubuntu is my sweetspot, after running away screaming, then loving, then running away screaming again from Unity.  My work-around for this Xubuntu problem, which I have experienced for the first time--but apparently I am not alone--is that I will dual-boot and run in parallel, yes, Ubuntu 14.04, TT, Unity, and keep it light.  This will be my fallback OS that I can use if I "lose" Xubuntu and need to troubleshoot it, as well as have a fallback OS.

---

