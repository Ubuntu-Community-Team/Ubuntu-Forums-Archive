---
title: "VirtualBox seems to have just deleted itself ??"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by john294 on 2016-08-29
I have Virtualbox installed on my Linux workstation now for at least half a year, running Windows 7 as a guest system.
I had it running this morning, then shut it down (selecting "save the active state" for faster reboot).

Now this afternoon, i wanted to work on some stuff under the windows environment and wanted to fire Virtualbox back up.
However now I got this strange warning:
```
Failed to execute command "VirtualBox %U".
Failed to execute child process
"VirtualBox" (No such file or directory)
```

What???? 

Virtualbox is also not recognized as installed in the Ubuntu Software center. The commands "vitrualbox" and "VBox" are now missing from my /usr/bin/-folder. However in my /usr/bin/ folder I DO find "VBoxClient",  "VBoxControl" and "VBoxService".
I certainly did not delete or uninstall them or use anything requiring sudo, as far as I can remember...

The only thing that may be somewhat related is the Software centers request to do a "partial upgrade" today, which lead to an error message about some lib3xml stuff not being able to be updated. I can't remember what exactly the issue was, but virtuabox was still running at the time and had no problems. 

I can still find the folder for the virtualbox VM in my home folder, so I have great hopes of maybe just reinstalling virtualbox and trying to reuse that same VM. But this whole thing DOES make me kind of nervous...

Any Ideas on what may have happened?

BTW: I am running Ubuntu 14.04.5 LTS with the xfce4 desktop.

EDIT:
Here's the first 15 lins of the last logfile I found in my VM-folder:
```

VirtualBox VM 4.3.36_Ubuntu r105129 linux.amd64 (Jan 27 2016 12:09:06) release log
00:00:00.454423 Log opened 2016-08-29T07:21:51.813706000Z
00:00:00.454425 Build Type: release
00:00:00.454428 OS Product: Linux
00:00:00.454429 OS Release: 3.13.0-93-generic
00:00:00.454430 OS Version: #140-Ubuntu SMP Mon Jul 18 21:21:05 UTC 2016
00:00:00.454457 DMI Product Name: Precision T5610
00:00:00.454463 DMI Product Version: 01
00:00:00.454555 Host RAM: 80502MB total, 56316MB available
00:00:00.454558 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.454559 Process ID: 854
00:00:00.454560 Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.519683 Installed Extension Packs:
00:00:00.519700   VNC (Version: 4.3.36 r105129; VRDE Module: VBoxVNC)
00:00:00.528450 UIMediumEnumerator: Medium-enumeration finished!

```

So it states that the executable should be in "/usr/lib/virtualbox". So i've checked there, and that Folder does not exist anymore, either!

---

### Post by ajgreeny on 2016-08-29
Run command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log | grep virtualbox
``` to see if virtualbox has actually been removed recently by the system in that partial update.  The output will give you a date and time in the line, if any appear, and look something like ```
/var/log/dpkg.log.1:1167:2016-07-24 21:31:41 remove virtualbox-5.1:amd64 5.1.2-108956~Ubuntu~trusty <none>
```

As the Software-centre does not see it at the moment it may be worth trying to install (or reinstall) the version of virtualbox you had before; that should see the VMs in the folder and run them without a problem, as long as your difficulties are not more deeply involved in the dpkg system in some way

---

### Post by deadflowr on 2016-08-29
> I can still find the folder for the virtualbox VM in my home folder, so I have great hopes of maybe just reinstalling virtualbox and trying to reuse that same VM. But this whole thing DOES make me kind of nervous...
It's designed to do that, so not a problem on that end.
Once you re-install the vms will auto show in the virtualbox panel.
I think they also show in whatever state they where in when last run. ie, saved or powered off or whatever state you left them in.

> The only thing that may be somewhat related is the Software centers request to do a "partial upgrade" today, which lead to an error message about some lib3xml stuff not being able to be updated. I can't remember what exactly the issue was, but virtuabox was still running at the time and had no problems. 
Never run any partial upgrades when offered without doing a full and thorough review of what is going to happen.
Whenever a partial upgrade is offered you can initiate it by selecting the partial upgrade option, but when you reach the page explaining how much will be needed to download and the approximate time to do so, look at the Details section and toggle that to expand.
Then toggle each of the 3 sub-levels (install, upgrade, remove) and review what each will do.
In partial upgrades you can check these before anything happens.
If you see something amiss then you can still cancel the upgrade.
And then wait a little while to see if perhaps something with the upgrader was bonkers and was later fixed to run correctly.

Also note that while the remove section might only list a couple of packages.
When you actually run that part, the removal will also try to remove packages that have already been deemed removable.
ie: if you run the *sudo apt-get autoremove* command, and have listings show up there, those listings will show up during the actual removal process is run, but they [s]would[/s] might not have shown up during the Details output.
So when you get to that remove part double check what is shows as being set to remove and you can still back out it (choosing the keep option).
Then if you want you can try removing packages more piece-meal manually, to prevent a massive glutch and problems resulting from such glutches.

If that make any sense at all.

---

### Post by john294 on 2016-08-30
@ajgreeny: Thanks a lot. I checked the log files as you suggested, and indeed I found an entry for the removal of virtualbox dating from yesterday. So the partial upgrade is indeed to blame.
@deadflowr: Good to know. I will be more carefull with partial upgrades, and will try to avoid them in the future.
When the partial upgrade message First popped up here, I did google it though  (because I did not know what it would do). The common consensus seemed to be that it should be safe, and would even be a good idea,  as it would repair/remove any broken packages. So it turns out its not so safe after all, and needs a little closer inspection...

---

### Post by john294 on 2016-08-30
Ok, so I just reinstalled virtualbox from the software center, and everything seems to work fine (inlcuding my already existing Windows guest VM). I'll just beware of partial upgrades from now on ...

---

