---
title: "OOPS, Upgraded to Dapper?"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by RRS on 2006-03-25
I seemed to have mistakenly installed Dapper Drake over Breezy Badger and now can't start X, and who knows what other problems.

Here's the sequence of my missteps as near as I can remember:

I was following the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=142481") to allow read/write mounting of my NTFS partition.(running dual boot w/windowsxp)

After a few unsuccesful attempts at installing the various Fuse components I folowed [this link]("http://ubuntuforums.org/showthread.php?t=148359") found towards the end of the thread.

Since this appeared to answer my problems I began following the instructions. This is when I began to notice potential new problems.

"get update" appeared to load alot more items then I remembered from when I'd previously enabled the resticted/multiverse repositories and then the "module assistant" appeared to compile and install considerably more items then the tutorial indicated.

As these items were flashing down the screen I was able to read enough to suspect that I may have been performing a complete upgrade to Dapper but decided anything I may try to do to stop the process would simply break something anyway so I let things continue.

After the processs completed I still couldn't mount windows as read/write so I decided move on to other things for a while.

I noticed the "upgrades available" notification and went ahead and let the package manager do it's thing while catching up on some emails, etc. I then rebooted as requested to finish the update/upgrade.

Upon reboot I realized I was now booting Dapper instead of Breezy but then was told X couldn't start. I shutdown and went to bed.

So I guess now I've got a couple choices to make:
[LIST=1]
[*]Use the CD to reinstall Breezy (probably simplest and safest)

[*]Try to repair/configure X and whatever else needed to go ahead and start using Dapper early
[/LIST]
Due to the challenge I find the second option desirable but my extreme "Newbie" status seems to advise against it and I would need a lot of "handholding" type instructions.

Since I'm not even sure I've posted in the correct place any advice or guidence would be highly appreciated.

Sorry for such a long posting but I wanted to be sure and provide enough info for troubleshooting.

Thankyou in advance.

---

### Post by petervk on 2006-03-25
I did the same a while ago. I wanted a new version of some program in dapper and just downloaded all the dependancies from the ubuntu packages site. It completely borked my breezy install, but I was able to save it. 

If you still have internet access look up "Apt-pinning". There is a way to tell apt to prefer packages from breezy over any version from dapper (regardless if it is a higher version number)

Then you need to restore your /etc/apt/sources.list to an original config without any references to dapper. ( eg: "sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup" then "sudo nano /etc/apt/sources.list" )

Then after you sources.list is back to normal, run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
(dist-upgrade is just a better form of upgrade that works better for large updates)

Oh, and if you need a command prompt, after the computer is booting hit "ctrl-alt-F1" to switch to a text based login. ("ctrl-alt-F1" will switch you back to the non-working X) Login using your normal user name and password.

On the converse, you could try doing a full upgrade to Dapper by changing your sources.list to a dapper one, and then doing the dist-upgrade. But this may not work perfectly, and dapper isn't quite finished yet. (I'm using it anyways and it runs fine)

---

### Post by petervk on 2006-03-25
[Apt-pinning to beginners]("http://jaqque.sbih.org/kplug/apt-pinning.html")

Here's the walkthrough.

At the command prompt (terminal, text login, whatever)
```

sudo nano /etc/apt/preferences

```

Type the following into the open file:
```

Package: *
Pin: release a=breezy
Pin-Priority: 1000

Package: *
Pin: release a=dapper
Pin-Priority: 0

```

Save and exit nano. (ctrl-o, ctrl-x)

Then
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list

```
change every occurance of the word "dapper" back to "breezy"
The commented lines (lines beginning with a "#") do not matter as apt skips them. Just the lines that start with "deb" or "deb-src"
After all the "dapper" references are gone, Save and exit nano. (ctrl-o, ctrl-x)

Then:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

If everything is all working, then thank me. Otherwise post again.

Oh, and if you ever want to upgrade to dapper you'll have to delete that /etc/apt/preferences file or it really won't work.

---

### Post by RRS on 2006-03-25
Thanks, especially for 2nd post with the walkthru.

A command prompt is no problem as X won't even start. Last night I was able to log in and also operate as sudo so if I can avoid typo's should be alright.

Internet access probably OK but I'd be totally lost trying to search the net without a GUI.

I probably won't have a chance to try your instructions till later this evening but I'll let you know the results.

Thanks again.

---

### Post by RRS on 2006-03-26
I finally had time to follow your instructions late last night but had limited success I'm afraid.

I only had to change one item from dapper to breezy in the sources list and both grub and the terminal log-in screen show Breesy 5.10 with the orignal kernel versions.

I still get the "x not set-up correctly" type error boxes after initial boot but the only options are to view the configuration or not start. Not start brings up the terminal log in. "view" shows the kernel conf. etc. While there's no menntion of dapper it lists the kernal dates as 3-11-06, and also shows as trial(or similar term)

Just realised I should have written the above info down instead of trying to recall it from my own memory, sorry. I can get the exact #'s and terms later if needed.

What I did think to make notes on though was the "apt-get dist-upgrade" results;

"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"
"1 not fully installed"
"setting up gnome -btdownload(0.0.22 -1ubuntu3)"
"/var/lib/dpkg/info/gnome-btdownload.postinst: line 5: gconfig-schemas: command not found"
"dpkg: error processing gnome-btdownload  (--configure): subprocess post-installation script returned error exit status 127"
"errors were encountered while processing: gnome-btdownload"
"E: sub-process /user/bi/dpkg returned an error code (1)"

Though this seems the likely source of my problem I don't yet have the knowledge or experience to properly iinterpret, let alone repair the above errors.

My next step was "sudo dpkg-reconfigure xserver-xorg" and this seemed to be going well until the color page. when I tried to change from 4 to 8, I got a message about attempting to change a previous setup and was kicked back to a terminal prompt.

So. am I still doing something wrong? Or do I possibly have more then one problem?

In the interest of learning and enjoying the challenge (one of my prime original reasons for diving into Linux) I would like to resolve this "glitch". But if I'm getting into an area with too steep a learning curve for a novice a reinstall is still an option if recommended.

Thanks for advice and patience.

---

### Post by petervk on 2006-03-27
I might suggest a reinstall. I don't know exactly what is screwing up on your computer, and if you don't have a lot data that will be lost its probably your quickest/easiest solution.

I bet there is a solution without reinstalling, but it could take you a few days to find out exactly what it is. A reinstall will take an evening.

Sorry, but reinstalling may be your best bet.

---

### Post by RRS on 2006-03-27
Haven't had Ubuntu on machine long enough to accumulate any valuable data with it, but how would a reinstall affect my windows partition?

Though I have a corrupted boot.ini file in xp so currently can't use it (batting 1000, aren't I?) I'm still hoping to find a repair for that too.

So if I can get slightly better then 50-50 odds of a reinstall not affecting my windows partition consider it a done deal.

Thanks for the help and advice.

---

### Post by funkydan2 on 2006-03-27
Easiest solution might be just to upgrade your whole system to Dapper.  It's pretty darn reliable at the moment, and you'll get lots of new versions of software.

It'll take a few hours to download all the updates on even a middle-speed broadband connection, but you don't need to sit in front of your computer whilst it does its thing - just run "sudo apt-get dist-upgrade" before you go to bed and it should be almost done by morning.

---

### Post by RRS on 2006-03-27
Will the upgrade reconfigure X in the proccess?
 
Also, it was by accessing the Dapper repositorys that I screwed things up in the first place. I was trying to install Fuse so I could write to NTFS and repair windows.

On the other hand it's already broke so why not? I can still reinstall Breezy later.

I'll post the results in the morning.

---

### Post by funkydan2 on 2006-03-27
Accessing the dapper repos did screw things up for you, but you were trying to create a mixed system.  Using packages from only one version is always going to be a safer option, even when that release us in serious development.

I'm not sure if some auto detection of Xorg is done during a dist-upgrade, but at the running "sudo dpkg-reconfigure xserver-xorg" after your dist-upgrade should prove more successful than your current situation.

---

### Post by RRS on 2006-03-28
[QUOTE=funkydan2] run "sudo apt-get dist-upgrade" [QUOTE]

As I was entering the command I remembered I'd dissabled the Dapper repositories. Decided to "enter" anyway, sure enough, same gnome error message as before.

I'll double check for complete instructions in the Dapper forums before trying again tonight.

Thanks again for all your advice and patience.

Edit; sorta messed up on quote function, must be too early in a.m. for typing.

---

### Post by RRS on 2006-04-01
Sorry about delay, finally had a chance to upgrade to Dapper last night.

Proccess seemed to go well; gnome/X start now, still same username/pasword, desktop setup and all that appear to have been transferred ok. Even appears to have saved Firefox settings during upgrade to 15.

Do still have a resolution bug with x though. Initially was something like 240 x 180 w/now options in system>preferences>resolution dropdown. Ran "reconfig......xorg" and manually set for 1024 x 768 and my monitors sync range. Now I have the choice in dropdown of 800 x 600 and 640 x480, useable but still no option for 1024 x 768.

Computer is a budget emachines with a "no name" CRT monitor.

Should I try a manual edit of /etc/X11 or ......??

Also, as this is a new problem, should I start a new thread, maybe in the Dapper forum?

Thanks for advice and patience.

---

