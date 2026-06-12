---
title: "Icons &amp; Graphical Images Lost upon Upgrade to 16.04 Xenial"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by linuxguruwanabe on 2016-08-17
I started upgrading from 15.10 to 16.04 and hung around long enough to answer a question about keeping/updating rcS (I chose update); then went to sleep.  In the morning the Acer-Aspire-5516 had shut down.

Upon boot up, even at the login dialog box, I could see that icons and graphics were 'missing'.

The wallpaper is black (not my wallpaper).
The following graphics on the lxpanel are missing (replaced with "unable to download icon" a white page, with red 'x' in the middle):[INDENT]Menu lubuntu "spark" (and ALL of the icons in the menu)
File Manager PCManFM
Web Browser
Iconify all Windows
Volume control
Battery Status
WiFi menu
Shutdown menu
[/INDENT]

My desktop Trash Can Icon is missing.

When I run Synaptic, it warns me that I don't have "administrative privileges" (which is not the case prior to the update).

There are icon graphics and _menu items_ that are missing in several different applications.

In PCManFM, no folder/file icons appear; the filenames do appear. The files/folders are there and can be clicked/used.

Example of menu items is in "galculator"; only the "View->Basic Mode" menu item appears.  The "View->Buttons" menu item appears, ONLY if I mouse-over it.

I have rebooted.

When I try :
```

:~$  sudo apt-get update
[sudo] password for XXX:
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease      
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease       
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
W: No sandbox user '_apt' on the system, can not drop privileges
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by mörgæs on 2016-08-18
You posted a snip of terminal output. Did you read what is says?

---

### Post by linuxguruwanabe on 2016-08-18
Yes, I did; but, I don't really understand what it means I should do about it.
I don't know what "Hits:" means.
I don't know what the "W:" or "E:" means.
I don't know what a "sandbox user" is or what "drop privileges" means.
I don't know why "dpkg" was interrupted; I didn't press ctrl+c.
I  don't know what that command line "sudo dpkg..." will do to my system,  if it will address my issue or just address something else.

I only posted it as a potential clue as to the state of my machine.

Like my name suggests a guru wanabe.

I  infer that you're telling me to go ahead and run the 'sudo dpkg...'  command; so I am.  It looks like it's configuring hundreds of packages.   Will return with feedback.

Thank you for your time

---

### Post by linuxguruwanabe on 2016-08-18
Thank you.

I guess that the computer shut down before update/upgrade was completed, but after all the packages were downloaded.

The 'sudo dpkg..." command completed the configuration of the downloaded, but not yet configured, packages?

To be clear, that fixed it.

Thank you again.
Much Respect

---

### Post by mörgæs on 2016-08-19
Good, please mark the thread solved using Thread Tools.

---

