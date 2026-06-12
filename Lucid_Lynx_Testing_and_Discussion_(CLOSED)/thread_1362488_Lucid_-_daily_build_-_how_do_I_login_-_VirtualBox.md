---
title: "Lucid - daily build - how do I login - VirtualBox"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ahickey on 2009-12-23
I just downloaded the daily build of 10.04 and booted it in VirtualBox.
I select 'Try Ubuntu without any change toy your computer'
All looked good until I come to the Login screen.
Usually for the LiveCD I go straight to the desktop but for this image I've been asked to login.

As an aside while booting it mentions 'Shadow passwords are now on'.  Not sure if this important.

I'm looking for a way to get to the desktop. Either login or not have to login.

Thanks,
Albert.

---

### Post by proxess on 2009-12-23
Try moving into a TTY and removing *Compiz* before logging in..

```
Ctrl+Alt+F1
```
now log into your account. Just type in your *Username* and *Password*. The following command will remove anything related to *Compiz*.
```
sudo apt-get remove compiz*
```
Now kill your current GDM and restart it. Repeat the killall command a few times to make sure, waiting until the "This process doesn't exist" or something similar shows up.
```
sudo killall gdm
sudo gdm
```
Supposedly your problem is due to no direct hardware graphics rendering in a Virtual Machine. *Ubuntu* comes with *Compiz* by default which requires graphical rendering.

---

### Post by ajgreeny on 2009-12-23
Usually in a live CD, if you logout and then in again, the username is **ubuntu**, and the password is left blank, ie just hit enter.  Give that a try, you may be lucky.

---

### Post by ahickey on 2009-12-23
Thanks for getting back to me so quickly.


@ajgreeny

I tried 'ubunutu' for the username
I'm not given the option to enter a password.

This failed - back to the login screen.

@proxess
If I do [ctrl]-[al]-[F1] I go to a prompt and I am already logged in.  As in I can 'ls' and 'cd /' without any problems.

Did the 'apt-get remove compiz*'
That appeared to work

Then 'sudo killall gdm'
Gave the following error message
gdm: no process found

Then did 'sudo gdm' gave the following two errors

** (gdm-binary-2407) : WARNING: **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary-2407) : WARNING: **: Could not acquire name; bailing out.


It looks like the real problem is that I'm being presented with a login screen when I shouldn't be as I am booting a LiveCD.

---

### Post by meborc on 2009-12-23
you could boot into recovery mode and see what users are registered in the system

edit - but i guess you can't do that with live cd :D

sorry, i'm having a slow day

---

### Post by empty_spaces on 2009-12-23
> 

@ajgreeny

I tried 'ubunutu' for the username
I'm not given the option to enter a password.

This failed - back to the login screen.



Was that a typo or did you actually enter **ubunutu** instead of **ubuntu**?

---

### Post by ahickey on 2009-12-23
Typo - I entered 'ubuntu'

Has anybody else booted the LiveCD for the 23rd Dec.
Does it require you to login or does it go straight to the desktop.

---

### Post by ranch hand on 2009-12-23
You should not enter anything.  It is a live CD.  Sometimes the login pops up.

Did for me the other day.  Usually (on stable releases) if this happens it will boot in ten seconds or right away if you hit enter.

If that does not work I would reboot and check the disk.  I am assuming you checked to be sure you had a good md5sum on your download.

---

### Post by ASriazh on 2009-12-23
I just installed the 12.23.09 daily build successfully. It's a bit tricky though.
It seems the user accounts are messed up. So what i did was to create a new user with home folder, give it a password and make it admin, so i could easily run the installer, which needs superuser rights.
I booted the CD and waited until the login screen appeared, then switched using "ctrl+alt+f1" to a new screen.
after that it was
```
sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin

```
I switched back to "ctrl+alt+f8" and was able to login and start the installer program which is under "system->administration"

-Asriazh

---

### Post by Eclipse. on 2009-12-23
> **ASriazh said:**
> I just installed the 12.23.09 daily build successfully. It's a bit tricky though.
It seems the user accounts are messed up. So what i did was to create a new user with home folder, give it a password and make it admin, so i could easily run the installer, which needs superuser rights.
I booted the CD and waited until the login screen appeared, then switched using "ctrl+alt+f1" to a new screen.
after that it was
```
sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin

```I switched back to "ctrl+alt+f8" and was able to login and start the installer program which is under "system->administration"

-Asriazh

Yes its something to do with the user account.At first I killed X and stoped gdm then tried logging in using startx, X segfault'd with a backtrace although I never paid much attention to it.Logging in as root also gets around the problem.Has there been a bug report filed? I am planning to go back later and debug the issue a bit more.

---

### Post by kansasnoob on 2009-12-23
I tried ubuntu w pword ubuntu, demo w pword demo, and root w pword root. No good.

Oh, and I can get the installer to run, just no Live Desktop.

---

### Post by NCLI on 2009-12-24
> **kansasnoob said:**
> I tried ubuntu w pword ubuntu, demo w pword demo, and root w pword root. No good.

Oh, and I can get the installer to run, just no Live Desktop.

How about no username and no password?

---

### Post by kansasnoob on 2009-12-24
> **NCLI said:**
> How about no username and no password?

Yes. I can just never get past the login screen to run the Live CD.

I haven't tried 12/24 yet.

---

### Post by ranch hand on 2009-12-24
Yup, just like the looping login in Kinky Kitty testing.

---

### Post by mrfelker on 2009-12-24
I'm not sure why you choose the option of instatlling Lucid as (do not touch my computer) rather than immediately installing it to disk.  

That said what is the version of VirtualBox you are using.  On a 64-bit machine versiion 3.1 is brokern - you need to use the earlier version 3.0.12.  During the install - on the screen where you enter your name, password and computer name (I use 'Ubuntu-Lucid-VB-Fedora" for example so its unique on Ubuntu One and I can remember which OS I'm!  there is a button to automatically login.  Use it. It saves hassles.  Sercurity wise you still need to to use "sudo" for system commands.

One thing I found that is a problem is the video.  You may get a message from Ubuntu that it is Low Graphics mode and you can login onece in that mode, debug the problem, drop to command line (I've forgotten the las option.  Use the "Low Graphics mode once  which is the default.  Most likely the video will in fact look fine.  At least for me - I use an onborade NVidia GEforce 6150 nForce 430.  It drove me mad until I discover that you can copy sudo cp xorg.conf.safe-default  (or something similiar)  to xorg.conf.  Reboot and messager goes away.  Increase video RAM from 12 to 32 MB may also help.  Sorry for being a bit off topic - but I assume you'd rather not use "startx" everytime to bring up the GUI

Marty

--------------------------------------------

I just downloaded the daily build of 10.04 and booted it in VirtualBox.
I select 'Try Ubuntu without any change toy your computer'
All looked good until I come to the Login screen.
Usually for the LiveCD I go straight to the desktop but for this image I've been asked to login.

As an aside while booting it mentions 'Shadow passwords are now on'.  Not sure if this important.

I'm looking for a way to get to the desktop. Either login or not have to login.

Thanks,
Albert

---

### Post by ranch hand on 2009-12-24
I don't know about anyone else, but I want to know if the live CD works.  For me it does not.

I am not real interested in installing at all.  I have 5 variations of 10.04  on the test platform right now.

---

### Post by kansasnoob on 2009-12-24
12/24 is still bad! Just tried it.

I will file a bug report.

---

### Post by kansasnoob on 2009-12-24
> **mrfelker said:**
> I'm not sure why you choose the option of instatlling Lucid as (do not touch my computer) rather than immediately installing it to disk.  

That said what is the version of VirtualBox you are using.  On a 64-bit machine versiion 3.1 is brokern - you need to use the earlier version 3.0.12.  During the install - on the screen where you enter your name, password and computer name (I use 'Ubuntu-Lucid-VB-Fedora" for example so its unique on Ubuntu One and I can remember which OS I'm!  there is a button to automatically login.  Use it. It saves hassles.  Sercurity wise you still need to to use "sudo" for system commands.

One thing I found that is a problem is the video.  You may get a message from Ubuntu that it is Low Graphics mode and you can login onece in that mode, debug the problem, drop to command line (I've forgotten the las option.  Use the "Low Graphics mode once  which is the default.  Most likely the video will in fact look fine.  At least for me - I use an onborade NVidia GEforce 6150 nForce 430.  It drove me mad until I discover that you can copy sudo cp xorg.conf.safe-default  (or something similiar)  to xorg.conf.  Reboot and messager goes away.  Increase video RAM from 12 to 32 MB may also help.  Sorry for being a bit off topic - but I assume you'd rather not use "startx" everytime to bring up the GUI

Marty

--------------------------------------------

I just downloaded the daily build of 10.04 and booted it in VirtualBox.
I select 'Try Ubuntu without any change toy your computer'
All looked good until I come to the Login screen.
Usually for the LiveCD I go straight to the desktop but for this image I've been asked to login.

As an aside while booting it mentions 'Shadow passwords are now on'.  Not sure if this important.

I'm looking for a way to get to the desktop. Either login or not have to login.

Thanks,
Albert

I reported two Xorg bugs that were present in the Alpha 1 Live CD. I need to follow up on those bug reports.

In order to do so I must boot a new Live CD.

If we fail to report bugs then things take longer to get fixed. Just verify, reverify, and then report.

Workarounds are NOT bug fixes!

I still have a Lucid that began with the toolchain upgrade from Karmic, that doesn't mean it's just OK.

---

### Post by kansasnoob on 2009-12-24
I hopped onto this one because it also fits:

[https://bugs.launchpad.net/ubuntu/+bug/500198](https://bugs.launchpad.net/ubuntu/+bug/500198)

I don't know if it's related or not. I'll now file a new one.

---

### Post by kansasnoob on 2009-12-24
New bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

I hope I did half-way decent. It's always hard when you can't use the automated procedure.

---

### Post by Jags_FL on 2009-12-25
I just tried Dec-25 Live-CD and its still asking for a password to log-in.

---

### Post by kansasnoob on 2009-12-25
> **ASriazh said:**
> I just installed the 12.23.09 daily build successfully. It's a bit tricky though.
It seems the user accounts are messed up. So what i did was to create a new user with home folder, give it a password and make it admin, so i could easily run the installer, which needs superuser rights.
I booted the CD and waited until the login screen appeared, then switched using "ctrl+alt+f1" to a new screen.
after that it was
```
sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin

```
I switched back to "ctrl+alt+f8" and was able to login and start the installer program which is under "system->administration"

-Asriazh

This does work! I tried it yesterday but somehow it failed, maybe I typed something wrong :confused:

Tried it twice this AM and it worked both times. Thanks!

---

### Post by ahickey on 2009-12-29
> **ranch hand said:**
> You should not enter anything.  It is a live CD.  Sometimes the login pops up.

Did for me the other day.  Usually (on stable releases) if this happens it will boot in ten seconds or right away if you hit enter.

If that does not work I would reboot and check the disk.  I am assuming you checked to be sure you had a good md5sum on your download.

Thanks for the suggestion.

Downloaded the 29/12/2009 LiveCD image and booted in Virtualbox
I left it to boot up when it came to the login option i did not attempt to login.  Nothing happened.
I clicked to login and pressed [enter] to get it to login and it just came back to the login screen.

As mentioned before there is only the option to enter a username and not a password.

So, a strange one.
Any other ideas would be hugely appreciated.

---

### Post by ranch hand on 2009-12-29
Try the stuff in the quote in the post right before yours.  May get you in.

---

### Post by xebian on 2009-12-29
> **ahickey said:**
> Thanks for the suggestion.

Downloaded the 29/12/2009 LiveCD image and booted in Virtualbox
I left it to boot up when it came to the login option i did not attempt to login.  Nothing happened.
I clicked to login and pressed [enter] to get it to login and it just came back to the login screen.

As mentioned before there is only the option to enter a username and not a password.

So, a strange one.
Any other ideas would be hugely appreciated.

If you got to this, it means something is wrong in the boot process and wasn't robust enough to recover back.

---

### Post by ahickey on 2009-12-30
> **xebian said:**
> If you got to this, it means something is wrong in the boot process and wasn't robust enough to recover back.

Xebian: thanks for this.  I did the boot again and caught an error message.  Screen Grab attached.

[    36.877849] piix4_smbus 0000:00:07.0: SMBus base address uninitiaized - upgrade BIOS or use force_addr=0xaddr

I assummed the force_addr=0xaddr should go on the boot options.

I find this strange I expected that Virtualbox would create its own environment that would take this kind of thing into account.

I'm running VirtualBox 3.1.2 r56127 on Windows XP.

This version is quite happy with PuppyLinux, DSL, even the Chrome Image floating around the internet.

It's just Lucid that is causing me trouble.

I just downloaded 9.10 LiveCD from the [www.ubuntu.com](www.ubuntu.com) website and it booted it Live without any problems.
So, it looks like something has changed between 9.10 and 10.04 alpha (2009-12-29)

---

### Post by hette on 2009-12-30
The problem is a corrupt gdm config. Replace all instances of \n in /etc/gdm/custom.conf with an enter and restart gdm.
/etc/gdm/custom.conf should look something like this:```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ubuntu
TimedLoginEnable=true
TimedLogin=ubuntu
TimedLoginDelay=10
```

---

### Post by ahickey on 2009-12-30
> **hette said:**
> The problem is a corrupt gdm config. Replace all instances of \n in /etc/gdm/custom.conf with an enter and restart gdm.
/etc/gdm/custom.conf should look something like this:```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ubuntu
TimedLoginEnable=true
TimedLogin=ubuntu
TimedLoginDelay=10
```


hette:  Thanks for this.
I did [ctrl]-[alt][F1] 
sudo vi /etc/gdm/custom.conf

Removed all the \n entries and then did ```
gdm restart
```

Failed to start gdm

I got the following error.

```
** (gdm-binary:2365): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1:31" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2365): WARNING **:Could not acquire name; bailing out
```


So, still not working.

---

### Post by xebian on 2009-12-30
@ahickey

Try a newer daily build.  A failed live cd boot is not worth hacking into.

---

### Post by strawberry on 2010-01-03
on 03/01/10 daily build live still asking login name.
It should be corrected. annoying feature.

---

### Post by sparker256 on 2010-01-03
> **strawberry said:**
> on 03/01/10 daily build live still asking login name.
It should be corrected. annoying feature.

I hope that you added yourself as affected. We are at 11 people so not sure when this will be fixed.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

Bill

---

### Post by strawberry on 2010-01-03
> **sparker256 said:**
> I hope that you added yourself as affected. We are at 11 people so not sure when this will be fixed.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

Bill

Never mind. ASriazh`s hint works with installing a new user. It was only a remark, and now a thanks for ASriazh.

---

### Post by JCoster on 2010-01-04
> **ahickey said:**
> hette:  Thanks for this.
I did [ctrl]-[alt][F1] 
sudo vi /etc/gdm/custom.conf

Removed all the \n entries and then did ```
gdm restart
```

Failed to start gdm

I got the following error.

```
** (gdm-binary:2365): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1:31" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2365): WARNING **:Could not acquire name; bailing out
```


So, still not working.

I got this as well, so I ran:
```
sudo gdm-restart && sudo gdm
```

Not sure if sudo was necessary for *gdm* but it worked.

---

