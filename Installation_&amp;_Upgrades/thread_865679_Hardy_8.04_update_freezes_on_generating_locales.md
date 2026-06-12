---
title: "Hardy 8.04 update freezes on generating locales"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by gwen on 2008-07-20
I just attempted to update to Hardy 8.04 and everything went fine until the "Generating locales" portion, at which point the process froze. It displays this:
```
Generating locales...
en_AU.UTF-8...
```
And then it just sat there for more than an hour, at which point I decided to close the installer and try again. Same thing happened. I tried logging out, which froze before seeing the login screen. When I restarted and logged in again, it froze right afterwards. And when I say froze for all instances, mouse and keyboard inputs are not locked out, but it just sits there and does nothing, no matter what I do. I restarted again and went into recovery mode, trying to manually do dpkg, which does the same thing with hanging on "generating locales". No other apt-get commands are accepted, saying that dpkg was interrupted and must be run manually.

I tried searching for solutions for this, but found nothing useful that helped. Can anyone help get the system running again? I don't care about Hardy (and actually from what I read after encountering this problem, I don't really want to upgrade to it), I just want a usable system back. When I went into recovery mode, the only options for the kernel boot were 7.10, so I am assuming it hasn't upgraded yet, but I still can't boot.

---

### Post by shichuan on 2008-07-20
I am having exactly the same problem. anyone has a fix for this? if not, is there a way to restore the system? i have very important data in it. i can't afford to reformat.

---

### Post by siberoptik on 2008-07-21
Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

---

### Post by lou2261 on 2008-07-21
Hello everyone,
   I am having the same exact problem.  I went through the steps given by siberoptik (thanks by the way!).  I went into recovery mode for xxx.14.  I first tried the dpkg repair broken files.  It seemed to finish.  However resuming normal boot up then failed.  I restarted again, went into recovery mode for xxx.14 again, selected the root option (sign in as root, or root terminal...something like that).  I got a prompt.  I tried the dpkg--configure -a. It was aborted.  
   Thanks in advance for any advice and suggestions.  
lou

PS.  The version 8.04 seems to have been installed.  Now my only options for booting are 8.04.  However,  after signing nothing happens.

---

### Post by Joeri Spitaels on 2008-07-22
[This is a copy of my message on 
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)
]

The steps taken by jdaviescoates worked partially for me too.
I didn't think of choosing a different kernel. As I was upgrading from
7.10 I just used the default 2.6.22.15 kernel.

The only way to stop the machine from hanging while generating those
resource files was a CTRL-ALT-DEL and then a hard press on the
hardreset button (sounds like Windows 98 doesn't it ;-) )

Next I rebooted into 2.6.22.15 recovery mode from grub. I chose to be
dropped into a root shell. There I could launch:

dpkg --configure -a

and afterwards

reboot

That got me to the Gnome logon screen. A normal logon from there would
hang though because of X not being configured completely apparently.
So after another hard reset I succesfully logged into a Gnome Failsafe
session (change the session at the logon screen).

From there I had to

sudo dpkg --configure -a

in a terminal once again which generated those resource files in less
than a second. The rest of the pending packages (including X and the
latest 2.6.24 kernel) installed smoothly as well.

HTH,
JSP

PS: While in the root recovery shell I experimented with setting the
locales package on hold as such:

echo locales hold | dpkg --set-selections

and auditing the unfinished packages with

dpkg -C

but that turned out to be unnecessary.

---

### Post by mariourk on 2008-07-22
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

Worked for me. Thanks! Althoug I had to run [i]dpkg --configure -i[/u] a second time, after I rebooted my pc. Another erboot after that and all was ok.

---

### Post by thirdmoth on 2008-07-22
I have had exactly the same problem as described in this thread. The fixes proposed seemed, at first, to work fine. I managed to get dpkg --configure -a to complete its business, and now, upon repeating the command, it does nothing. However, neither xdm, gdm, or kdm will work. xdm and kdm will allow me to login, but after this the login window goes away and the system sits there doing nothing while displaying the background graphic. gdm does not even get to the login screen, simply sitting there with the spinning cursor, which pauses every few seconds as the screen flashes once, this process continuing indefinitely.

I am not sure if this is a problem with the X configuration or not. I can start in recovery mode and run the xfix tool, but this has no effect, nor does replacing /etc/X11/xorg.conf with a backup copy have any effect. I am not an expert on X11 configuration. Short of trying to completely remove X11 and reinstall it from the shell, I am at a complete loss. I have never had a problem like this before.

Any suggestions?

Thank you.

---

### Post by navigation_uk on 2008-07-22
Okay I've definitely got the same problem going on...but I've been using Linux for about three days now and half of what you said above makes pretty much no sense. If I cancel and reboot can i carry on using ubuntu 7.whatever or have a got to regroup some brain cells and do more than click on a button? Any help would be lush

---

### Post by navigation_uk on 2008-07-22
Okay top advice to those that have been using ubuntu for three days is that the windows reboot to sort it out does not work. Top advice to those that have been using ubuntu for three days and couldn't care less if they lose what is on the partion then wait till the problems sorted and install from your cd or whatever again then do the upgrade. In the mean time use windows which still plays all your music and video, and even streams on the internet.

---

### Post by cuteboi on 2008-07-22
I went with the kill -9 method of stopping the locales from being generated, after finishing the updates, I ran the recovery app with the x.14 kernel, and it finished configuring the locales on its own, no other problems have come up.

---

### Post by gwen on 2008-07-23
I tried the suggested fix and booted the .14 kernel, ran dpkg, and it worked and upgraded to 8.04. However, it still does not log in, and when I try to run dpkg again, it outputs a bunch of lines, followed by this:
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.

```
I waited a long while before upgrading to Hardy - you would think bugs like this would be worked out by now. Why are so many people having trouble upgrading and no solutions to fix this?

---

### Post by yclian on 2008-07-23
Hit into the same issue, solved by booting into recovery mode and run dpkg.

Cheers guys!

---

### Post by Sef on 2008-07-23
> I waited a long while before upgrading to Hardy - you would think bugs like this would be worked out by now. Why are so many people having trouble upgrading and no solutions to fix this?

There are too many hardware variations to check out.  Not all hardware works with any operating system.  Most people do not have a lot of problem, but the ones who have problems write to ask for solutions for their problems.

---

### Post by ample on 2008-07-23
what seems to work for most people is loading a different kernel or booting into recovery mode and running dpkg --configure -a.  some of us(myself included) need a little extra something.  what finally worked for me was logging into failsafe mode and running dpkg --configure -a.  this is after i tried booting into recovery mode, loading a different kernel, and booting into recovery mode of a different kernel.  i think i ran dpkg --configure -a 5 or 6 times before the failsafe route worked.  try different variations and that should take care of most problems.

-ample

---

### Post by gwen on 2008-07-24
I ran dpkg --configure -a at least 10 times in various kernel recovery modes (I think I have 14, 15, and 27). I don't see a failsafe mode - am I missing something? None of the kernels boot past the login screen and none of them allow dkpg to complete.

Although I have gotten past the generating locales and that problem was solved, it still fails to configure the rest of the files and exits with a 'too many errors' failure because of dependency on other unconfigured packages. I tried configuring them manually, but it's like a tree where each lower one depends on something else. For the first end I reached (dbus), it said the package cannot be found. I tried installing it, but it failed. I was thinking of removing it and reinstalling again, but I am afraid to mess with the core files and risk having to reinstall. Is there a way to fix this without a clean install?

---

### Post by ample on 2008-07-24
failsafe GNOME is under Options at the bottom left of the login screen, or press F10 at the login screen. do not choose recovery mode if you want to try failsafe because you need to get to the login screen.

-ample

---

### Post by fari81 on 2008-07-24
Same problem here (on two Dell laptop Inspiron 600m and 6000). On the first one I tried the recommended dpkg ..., but couldn't get it working. So I just booted it up in recovery mode, backed up my data on an external hard drive and then installed Hardy from scratch. On the other one, I can't afford to format the hard drive. So, I've just left it there struggling with the installer. It's know a couple of hours that it is trying to generate locales (localedef process is burning %98 of CPU time). I'm gonna wait and see what happens.

---

### Post by dmooreng on 2008-07-24
I had this same problem and had to go through the process described in reply #5, i.e. run "dpkg..." in recovery mode, reboot, then run "sudo dpkg..." in failsafe mode, reboot, "home free".  The key here is to realize that the two modes are different.  The recovery mode "configure" lets you get to the login screen, where you choose the failsafe mode from the drop down that comes up when you press the "options" button in lower left corner.  This get you into a session where you can bring up a terminal to run the "sudo dpkg...".  Once it completes, you should be able to reboot and have thing running normally.  At least, this worked for me.

Oh... and thanks Joeri for bailing me out!!

---

### Post by toallpointswest on 2008-07-25
Okay, what if you ran into this problem, but happened to have been trying to do a remote upgrade via ssh. What options do I have?

---

### Post by ample on 2008-07-25
try forwarding X

-ample

---

### Post by toallpointswest on 2008-07-25
> **ample said:**
> try forwarding X

-ample

Currently I can't ssh back into the box, what should be showing on the console?

---

### Post by ample on 2008-07-25
> **toallpointswest said:**
> Currently I can't ssh back into the box

you cant login or you cant do anything once you are logged in?

---

### Post by toallpointswest on 2008-07-25
> **ample said:**
> you cant login or you cant do anything once you are logged in?

I can't login :( I have a user at the console but I don't know what to tell them yet.

---

### Post by ample on 2008-07-25
if you cant ssh back into the machine you may need to walk the user through some of the suggestions mentioned earlier(recovery mode and failsafe login).  i dont much about updating through ssh and the problems that can arise.

-ample

---

### Post by Spooky5 on 2008-07-25
> **gwen said:**
> I tried the suggested fix and booted the .14 kernel, ran dpkg, and it worked and upgraded to 8.04. However, it still does not log in, and when I try to run dpkg again, it outputs a bunch of lines, followed by this:
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.

```

I am also getting this error. I cannot get to the log-in screen as I had mine set to automatically log-in. When I try to boot into the system all I get is a blank screen. :(

---

### Post by gwen on 2008-07-26
> **ample said:**
> failsafe GNOME is under Options at the bottom left of the login screen, or press F10 at the login screen. do not choose recovery mode if you want to try failsafe because you need to get to the login screen.

-ample

I got it working now by logging into the failsafe mode. Everything seems to be working fine now. Thanks a lot for your help! :) And good luck to anyone still having issues.

---

### Post by mauris on 2008-07-26
And the same problem here (presario v2000, 64). I followed steps from the post #5 and the upgrade is running now again. Still waiting though. Will have to wait before upgrading my presario v3000) ;)

---

### Post by kamiokande on 2008-07-27
I came across the same problem with my m1330. After following the instructions given on the first page of this thread, everything seems to be working fine. Thanks!

---

### Post by Janeleaper on 2008-07-28
I have a Dell Inspiron 530 loaded with 7.10.  I had the same problem as described at the beginning of this thread when I tried to upgrade to 8.04.  

I'm new to Linux/Ubuntu and so asked for advice in the beginners forum and ended up reinstalling 7.10.

I've now got the cd for 8.04.  I'm actually going to try it on another computer currently running Windows XP.  However, if I did use the cd to upgrade my Dell Inspiron would I get the same problem as when I tried the upgrade from a download?

---

### Post by clay.michaels on 2008-07-28
GG to HH, same problem. Rebooted, and the system went FUBAR.

Now the "Loading" screen (with the orange progress bar under the logo) bounces right and left forever.

Any ideas?

I would not mind re-installing or "repairing" or similar, as long as I can keep my Home folder intact. I might actually prefer it, in fact. I have made some software mistakes that I wouldn't mind wiping out. The GG LiveCD I am on now sees my FS just fine, but I don't have any backup media large enough for a tenth part of my stuff...

Clay

---

### Post by ubuntal on 2008-07-29
> **gwen said:**
> I just attempted to update to Hardy 8.04 and everything went fine until the "Generating locales" portion, at which point the process froze. It displays this:
```
Generating locales...
en_AU.UTF-8...
```


Same here. Just went "ps -fe |grep locale" and then "kill -9" the locale-gen process. 

Had to do this five or six times, and the killed processes went zombie, still consuming the CPU time, but the upgrade finished OK even though quite slowly.

After the reboot went ```
sudo localedef --no-archive -i en_AU -c -f UTF-8 en_AU.UTF-8
``` which fixed the locale.

---

### Post by flower71 on 2008-07-30
Thanks for the info, that was much faster than rebooting and running the dpkg command again!  We just killed the offending process each time it came up (about 13 times) and finally made it through the install.

---

### Post by rednamer on 2008-07-31
> **gwen said:**
> I tried the suggested fix and booted the .14 kernel, ran dpkg, and it worked and upgraded to 8.04. However, it still does not log in, and when I try to run dpkg again, it outputs a bunch of lines, followed by this:
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.

```
I waited a long while before upgrading to Hardy - you would think bugs like this would be worked out by now. Why are so many people having trouble upgrading and no solutions to fix this?

I have this same exact problem. Can't seem to get past it no matter what I try suggested in this thread.

When I go to login screen I get "Authentication failed" -popup immediately after entering my user name. The same also comes from a console, "Login failed" immediately after entering the user name. Obviously I should get 'dpkg --configure -a' to finish in order to get things done.

I'm now downloading an installation CD, hopefully it can clean up this mess. Any other suggestions on fixing this issue are highly appreciated.

---

### Post by pbhill on 2008-07-31
Having the exact same problem. Is there a real fix for Hardy or should I just reinstall Feisty (which was fine)? I don't understand any of the gobbledygook above... How about some help for non-technical folks?

---

### Post by ubuntal on 2008-07-31
> **pbhill said:**
> I don't understand any of the gobbledygook above... How about some help for non-technical folks?

The moment the install freezes, run the terminal (Start menu - Accessories - Terminal). A window should pop up showing something like this ```
ubuntal@machine:~$
```

Enter "top" and press Enter (this step is optional, just for you to see what's going on inside the box).

```
ubuntal@machine:~$ top
```

You should see a localedef process at the top, consuming the CPU at about 99%. You should kill it.

To quit the top list, just click the "q" button. Now you need to find out the localedef's id.

In the terminal window enter ```
ubuntal@machine:~$ ps -fe | grep locale
```

You should see something like this ```
ubuntal@machine:~$ ps -fe | grep locale

root      17061  15634  0 11:21 ?     00:01:14 localedef some-options-here...
root      15634  1      1 11:20 ?     00:02:29 locale-gen some-options-here...


```

This means that the upgrade is executing locale-gen, and locale-gen is executing localedef. To kill the bad process, enter (note: in your case the number will be different, just enter your number instead of 15634)

```
ubuntal@machine:~$ sudo kill -9 15634
```

The update should now continue. If it freezes again, kill locale-gen again (the number will again be different).

Then after the upgrade and restart, open a terminal window and enter

```
ubuntal@machine:~$ sudo localedef --no-archive -i en_AU -c -f UTF-8 en_AU.UTF-8
```

In your case it's probably en_US instead of en_AU. To check it's been fixed, go

```
ubuntal@machine:~$ locale
LANG=en_AU.UTF-8
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE="en_AU.UTF-8"
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=

ubuntal@machine:~$ exit

```

Hope this makes sense.

---

### Post by jules98 on 2008-07-31
Hi all,

I have the same problem. With "pstree" I see that the hanging process is "gzip":

hardy(24415)
+dpkg(8598)
+language-suppor(26213)
+install-languag(26218)
+locale-gen(26219)
+locale-gen(26232)
+localedef(26261)
+gzip(26262)

May that help to trouble shoot...

BR, Jacques-D.

---

### Post by thesurgeon on 2008-07-31
Your a star Ubuntal. I have been trying to  fix this for a few days now and had to reinstall to 7.04, then upgrade via the internet for 2 hours and again up to 8.04. This is deffinetly the fix for this bug. I have tried all the other posts and other pages and this is the only one that deffinetly works. Thanks an endless amount.

---

### Post by pbhill on 2008-07-31
I am anxious to try Ubuntal's fix, but can't get Ubuntu to boot... all I get is a screen with vertical lines. I've tried safe mode, etc. Do I have to start from scratch and reinstall Gutsy Gibbon or Feisty? (I now have two computers down with this problem, and have had to resort to XP!) Why did I think I should upgrade when all was well?

---

### Post by pbhill on 2008-08-01
OK, now I've tried Ubuntal's fix on the second machine. I can at least boot into Ubuntu on that one. I get a message saying that HAL has failed to initialize. I go through the steps as outlined by Ubuntal, but after killing locale-gen, it get the message "Unable to resolve host Ubuntu" 

bhill@Ubuntu:~$ ps -fe | grep locale
root      4218     1  0 17:30 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sda1 /media/sda1 -o rw,locale=en_US.utf8
root      5707  5705  0 17:31 pts/0    00:00:00 /bin/sh -e /var/lib/dpkg/info/locales.postinst configure 2.6.1-1
root      5708  5707  0 17:31 pts/0    00:00:00 /bin/sh /usr/sbin/locale-gen
root      5722  5708  0 17:31 pts/0    00:00:00 /bin/sh /usr/sbin/locale-gen
root      5751  5722 99 17:31 pts/0    00:01:09 localedef --no-archive --magic=20051014 -i en_AU -c -f UTF-8 en_AU.UTF-8
pbhill    5773  5753  0 17:33 pts/1    00:00:00 grep locale
pbhill@Ubuntu:~$ sudo kill -9 5751
sudo: unable to resolve host Ubuntu
[sudo] password for pbhill: 
pbhill@Ubuntu:~$

Any ideas? Thanks in advance!

---

### Post by Gargoth on 2008-08-01
> **pbhill said:**
> OK, now I've tried Ubuntal's fix on the second machine. I can at least boot into Ubuntu on that one. I get a message saying that HAL has failed to initialize. I go through the steps as outlined by Ubuntal, but after killing locale-gen, it get the message "Unable to resolve host Ubuntu" 

bhill@Ubuntu:~$ ps -fe | grep locale
root      4218     1  0 17:30 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sda1 /media/sda1 -o rw,locale=en_US.utf8
root      5707  5705  0 17:31 pts/0    00:00:00 /bin/sh -e /var/lib/dpkg/info/locales.postinst configure 2.6.1-1
root      5708  5707  0 17:31 pts/0    00:00:00 /bin/sh /usr/sbin/locale-gen
root      5722  5708  0 17:31 pts/0    00:00:00 /bin/sh /usr/sbin/locale-gen
root      5751  5722 99 17:31 pts/0    00:01:09 localedef --no-archive --magic=20051014 -i en_AU -c -f UTF-8 en_AU.UTF-8
pbhill    5773  5753  0 17:33 pts/1    00:00:00 grep locale
pbhill@Ubuntu:~$ sudo kill -9 5751
sudo: unable to resolve host Ubuntu
[sudo] password for pbhill: 
pbhill@Ubuntu:~$

Any ideas? Thanks in advance!

You killed the wrong process, you should be killing the locale-gen. in the case of your example it would be sudo kill -9 5722

---

### Post by Orion-KOS on 2008-08-02
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

THANK YOU!!!  this definately did the trick for me!

-Be Alert          The world needs more lerts.

---

### Post by toallpointswest on 2008-08-02
Okay all, I solved my version of the problem only something interesting happened that threw me off track...

My first mistake, I tried to upgrade remotely....DON'T!!! 

After my first mistake I had to go on-site to upgrade the system only to discover that the /var/lib/dpkg and /var/cache/apt directories had been deleted or had otherwise disappeared. This caused the dpkg --configure -a to fail.  

Turns out that after the reboot the system didn't mount my separate /var partition and instead created a /var directory in the root partition and put some data (minus EVERYTHING that dpkg and apt needs to run) in it. Which was very misleading initially. 

After puzzling that out, and remounting the correct /var the upgrade went smoothly except for a freeze on kaddressbook (yeah, no idea), but another reboot, and a dpkg --configure -a, followed by a apt-get install -f and everything appears to be normal. 

All in all, I can say ...don't upgrade remotely and Ubuntu devs this is something to look into resolving. Thanks!

---

### Post by pd71sat on 2008-08-03
> **ubuntal said:**
> Same here. Just went "ps -fe |grep locale" and then "kill -9" the locale-gen process. 

Had to do this five or six times, and the killed processes went zombie, still consuming the CPU time, but the upgrade finished OK even though quite slowly.

After the reboot went ```
sudo localedef --no-archive -i en_AU -c -f UTF-8 en_AU.UTF-8
``` which fixed the locale.

**Ubuntal**, thanks for saving my bacon. I had the exact same problem upgrading on a Fujitsu A310 laptop. 
I followed your suggestion, opened a new terminal window and entered the following commands 

ps -ef | grep locale 

to find the processes active with '*locale-gen*'. Issued
the command 

sudo kill -9  [SIZE="1"]xxxxx  yyyyy[/SIZE] [[SIZE="1"]zzzz[/SIZE]] 

where [SIZE="1"]xxxxx, yyyyy[/SIZE] (and [SIZE="1"]zzzz[/SIZE] optional depending on the number of '*locale-gen*' processes; sometimes 2, 
sometimes 3) were the PID's.

Had to do this 4 times for a total of 9 processes. The upgrade 
finally completed and gave a long list of packages that were 
incompletely installed as follows;

[B]locales language-pack-en language-pack-gnome-en-base language-pack-gnome-en sun-java5-jre 
sun-java6-jre ubuntu-minimal sun-java5-bin ia32-sun-java5-bin sun-java6-bin ia32-sun-java6-bin[/B]


Rebooted, and as you posted I entered the 'localedef ...' command. Afterwards I did the following;

sudo apt-get update

<added the wine respository> (This is optional; go to 
[www.winehq.org](www.winehq.org) if you want to get updated wine)

sudo apt-get dist-upgrade

The system after installing wine in my case, then rebuilt the 
locales that had hung-up during the upgrade, and then finished 
configuring the eleven (11) packages listed above.

Many thanks again for your suggestions.

---

### Post by DarkSim on 2008-08-04
> **Joeri Spitaels said:**
> stuff that fixed my borked upgrade

Thanks. That worked like a charm.

---

### Post by pbhill on 2008-08-04
Ok, I took the easy way out and reinstalled Hardy from the website. Went quite smoothly. I have Home on a separate partition, so I didn't have to do much tweaking. No more upgrading for this guy! Ubuntu needs to straighten out this sort of thing if they really want to become known as user-friendly. Many of us just want a system that simply works without constant tinkering!

---

### Post by cypherpunks on 2008-08-05
Here's another one with the very same issue.

I'm currently installing, did a:
sudo killall -9 locale-gen

Guess it'll get sorted out eventually without having to do a crapload of reboots.

For the record, it sucks mightily that this crap seems to happen to so many people. Better bug testing is needed!

And, (as a programmer myself), saying "There are too many hardware combinations to test" is a total cop-out. Generating locale data is about as hardware-unrelated it can get. This isn't a hardware-dependency issue. 

This is an issue of flaky, badly written software, and nothing else.

---

### Post by JohnnyC44 on 2008-08-05
Well, I got bit by this too.  The upgrade from Fiesty to Hardy on my Dell E1505n (Dell-installed Ubuntu) went flawlessly a while back.  So I waited three months for all the bugs to get worked out, and then this AM fired up Update Manager and ran the upgrade to Hardy.

Got to Generating locales and it stopped with maxed out memory.  I used ubuntal's post (#35) to kill locale-gen several times to keep the upgrade moving forward.  Several nasty messages at the end including one that said Update Manager wasn't installed and another telling me the upgrade didn't work and as a consequence I would have a very unstable OS.  I got my normal display to come up after rebooting twice, but now wireless won't connect -- it sees the connection, asks me for the password and then nothing happens.  I never really looked at any other issues with my newly-unstable Ubuntu OS.

This is a complete FUBAR, and avoidable based on cypherpunks' comment in post #46 above.  And Sef, even if it is a hardware issue after all, I understand that it would be impossible to check out all hardware variations -- but Dell sold LOTS of E1505n notebooks with Fiesty installed to newbies like me.  This has been a very disheartening experience.  If I end up having to do a fresh install, I believe it will be to Win XP.  Sorry guys, but I've got better things to do with my time than keep up with the steep learning curve of buggy new versions every six months....

---

### Post by sav74sac on 2008-08-06
Question -

Is there any way in the shell to run 'dpkg --configure -a', and then use the ps/kill technique when the locale problem comes along?

That would help those of us who can't get back into the desktop environment....

Thanks for any help

---

### Post by newbuntuxx on 2008-08-07
[COLOR="Red"]> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck[/COLOR]


Thank you, that worked smoothly!

---

### Post by ample on 2008-08-10
can a dev make this a sticky post? i think the problem warrants it

---

### Post by mvdberg112 on 2008-08-11
Yes, I had the problem:
```
Generating locales...
en_AU.UTF-8...
```just this morning.

First solution was a reboot, and the system came back just fine, but when I tried to install a program called "locate" I got a few errors because apt/dpkg was not consistent. It advised to run:
```
sudo dpkg --configure -a
```
This worked, but it hang again on en_AU.UTF-8.
My solution was to swich to the text terminal, and kill that process. (I just forgot the name, but they have the name locale in it.)
Further, I noticed:
-killing some the ...locale... processes did not work. 
-a gzip was also running and it seemed to me that that was the last started program.  Trying to kill it did not help.

After killing the process, the upgrade process would continue with the next step, but then later on it would try configure the locale again because another package required it (which is correct). Same procedure: kill it from the command line. After that a reboot and again run the dpkg, and this time it was able to configure the locale.

My theory is: during the upgrade process, it uses some software that is already on the system (perhaps gzip or a program that gzip uses), but that piece of software does not work fine with the new 8.04 kernel and packages when it comes to installing the locales. Hence, it hangs. After the upgrade is complete, this piece of bad-software is upgraded to the 8.04 version and works now fine. Hence, the locales reconfiguration runs fine.

Hope this feedback helps the developers.
They have done a great job. Although this little thing concerns me, since I was not able to fix it with the GUI and did not have internet access (Gnome did not work nice and firefox did not start at all during the upgrade process, perhaps another issue; so I could NOT check the forum for help...).
Overall the system is really improved: some CD mounts that did not work, work now. The 'Control Centre' is great.

Wish list for future versions:
1. Parted standard installed in Control Centre
2. Format of CD-RW or DVD-RAM to be used same way as floppy disk in right-mouse button menu of file manager
3. A good Tree view in the file manager or the apple approach (the filemanagers in Linux are great, but all the good options should be combined to make the strongest ever; if I could program I would do it, but I cannot)
4. More tutorial style manual. Sometimes, the manual tells what we can fill in in the options, but I want to know what the options are good for or I am looking for a topical help. Like: how do I use a CD-RW? This might be not just one function, this is a tutorial-topic. I have tried to contribute on this point, but did not find a lot of response.

---

### Post by falkenberg_cph on 2008-08-12
Worked for me. thanks!
/Carsten

> **Joeri Spitaels said:**
> 
That got me to the Gnome logon screen. A normal logon from there would
hang though because of X not being configured completely apparently.
So after another hard reset I succesfully logged into a Gnome Failsafe
session (change the session at the logon screen).

From there I had to

sudo dpkg --configure -a

in a terminal once again which generated those resource files in less
than a second. The rest of the pending packages (including X and the
latest 2.6.24 kernel) installed smoothly as well.

---

### Post by KennethP on 2008-08-12
Thanks Shichuan.

Worked after the second dpkg --configure -a

You made my day!

Ken

---

### Post by jolmash on 2008-08-13
Hello everyone,
I am having the same exact problem, the steps Siberoptik posted worked for me, THANKS SIBEROPTIK!!!!!

---

### Post by edward4130 on 2008-08-16
I have the same issue I am past the Locales but get this:
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
```

this question was aksed but was never resolved, I can do it 40 more times but nothing is changing.Sux since I needed 8.04 for a new application but my machine was running so stable as a myth/ ubuntu box.... now I have a terabyte and a half for useless data since I can't get to a login screen.  Someone please help.  I built this and made it do many things but this has me stumped.

---

### Post by stephan0h on 2008-08-17
unfortunately many "solutions" fly around for this problem - but the only one that helped me was this one. thanks!

---

### Post by brainsik on 2008-08-17
Alright, I documented this all over the place. I put it on the HardyUpgrades help page, answered someone's "Ubuntu question", and opened a Launchpad bug about this. I can't believe this wasn't documented on the help page.

[https://bugs.launchpad.net/update-manager/+bug/258879](https://bugs.launchpad.net/update-manager/+bug/258879)

Documented everything here:
[http://brainsik.theory.org/.:./2008/ubuntu-710-gutsy-804-hardy-upgrade-freeze](http://brainsik.theory.org/.:./2008/ubuntu-710-gutsy-804-hardy-upgrade-freeze)

Thanks siberoptik!! How did you know to go to the 2.6.22-14 kernel?

---

### Post by stephan0h on 2008-08-18
i googled it, i found it here, and it worked for me. maybe you documented it elswhere - i just didn't find it. sorry.

---

### Post by Sir Jake on 2008-08-18
I'm having this same issue with it hanging at en_US.UTF-8...
Issues is I did this from ssh server is a few hours away so not able to just go down there and boot into grub, is there any steps I could do to fix this from ssh I still have access to my ssh right now.

---

### Post by EmmaDad on 2008-08-18
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

This basically worked for me with a couple of tweaks...

First, my kernel numbers weren't quite so orderly, my latest was 2.6.22-15 (I think) and so I went to the prior one which was 2.6.20-17 (again, I think). Basically I think the trick is just go down to the second from the top on the grub menu.

After it booted, a GUI login never appeared, but I was able to SSH in and run the dpkg command remotely. It completed, I did a normal reboot and things seem to be ok now.

BTW, my 8.04 upgrade was immediately following a 7.04->7.10 upgrade.

Thanks. (Edited to correct kernel numbers.)

---

### Post by stephan0h on 2008-08-19
> **Sir Jake said:**
> I'm having this same issue with it hanging at en_US.UTF-8...
Issues is I did this from ssh server is a few hours away so not able to just go down there and boot into grub, is there any steps I could do to fix this from ssh I still have access to my ssh right now.

There's a configuration file for grub (don't know the name) where you can set the kernel to boot up next time. But this still includes a reboot.

---

### Post by Sir Jake on 2008-08-19
Would this be the file? sudo nano /boot/grub/menu.lst
I know I had to edit this file before when I changed kernels so it would load first.

---

### Post by d3uterius on 2008-08-19
I've got the same problem as gwen, and tried to repair it with your advices, but it was stuck at the same en_AU.UTF-8 every time i tried the dpkg --configure -a
After 4 times of doing that and rebooting from the wingoze button, i set up on hold the locales, it gave me a bunch of errors, and now it's stuck on the blue screen after i introduce the user and pass...Please, any idea how to solve it?

---

### Post by Janeleaper on 2008-08-19
I've got difficulties too.  After running the upgrade from 7.10 kernel xxx14 I had difficulty getting my computer to boot.  Eventually did it from 8.04 xxx14 in recovery mode.  Now I have what looks like my old 7.10 desktop with a black margin down the left hand side.

I tried running dpkg etc in terminal, but get the message 'superuser privileges needed'.  I type in my password but get the message ' message not understood'.  

Does anyone have a clue what I should do next. Please?

---

### Post by d3uterius on 2008-08-20
I tried again and got more and more errors,now the root shell from the recovery menu has a limited working, i tried to save my data to another partition in order to install 8.04 from scratch, but even the copy command doesn't work, mount doesn't work, it does not recognize any of the other hard disks i have....so i guess the stinky winblows will save my day with the "explore2fs" program and after tha data rescue, install from scratch...too bad. I had the same problem with my laptop,4 weeks ago, but there was no winblows on it to rescue the data.

---

### Post by Sir Jake on 2008-08-20
> **stephan0h said:**
> There's a configuration file for grub (don't know the name) where you can set the kernel to boot up next time. But this still includes a reboot.

When I go into that file and edit what kernel boots up, 2.6.22-14-rt  then reboot the system would I then get ssh control again once the server reboots? If so that should then work for me to update from there I would think. I just don't want to have to call the tech from the Datacenter to help fix it. :)  That costs some good cash :P
Thanks for any help.

---

### Post by DavidTangye on 2008-08-21
> **ubuntal said:**
> Same here. Just went "ps -fe |grep locale" and then "kill -9" the locale-gen process. 

Had to do this five or six times, and the killed processes went zombie, still consuming the CPU time, but the upgrade finished OK even though quite slowly.FYI: This did not work for me.

---

### Post by DavidTangye on 2008-08-21
> **siberoptik said:**
> 
[LIST=1]
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.Unfortunately i had to remove the previous kernel to get sufficient space to do the upgrade, so this option is not open for me.
[/LIST]

---

### Post by DavidTangye on 2008-08-21
I have allowed the installer to submit [a bug report]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/259956"). It submitted it under the catchy title "[SIZE=3]package update-manager 1:0.87.30 failed to install/upgrade: ErrorMessage: SystemError in cache.commit(): E:Sub-process /usr/bin/dpkg returned an error code (1)"!!

Edit: [/SIZE]This report is a duplicate of [Bug 249340]("https://bugs.launchpad.net/bugs/256653") which has 21 duplicates and counting  :-) , and is currently triaged and a fix is commited.

---

### Post by DavidTangye on 2008-08-21
> **gwen said:**
> I waited a long while before upgrading to Hardy - you would think bugs like this would be worked out by now. Why are so many people having trouble upgrading and no solutions to fix this?I did exactly the same for the same reason. Now this main machine that I REALLY did not want damaged is just that - completely stuffed, once I reboot it, according to what I have read here. To say I am annoyed is an extreme understatement. This sort of stuff-up should not be happening if this software is going to be taken seriously by anyone outside of current Linux users.

***Its a major bug when an upgrade wrecks your machine.***

---

### Post by Sir Jake on 2008-08-21
Yeah that kind of sucks, I am scared to reboot my server now. :(

---

### Post by DavidTangye on 2008-08-21
> **Sir Jake said:**
> Yeah that kind of sucks, I am scared to reboot my server now. :(I found that the old kernel 2.6.22-15-generic was still there, with its initrd and modules, so I have just decided to bite the bullet, and try reboot into it. On reboot I found that the problem remains, in that version of the kernel; ie 'dpkg --configure -a' immediately hangs at the same place.  On reflection, this is not surprising as that is the kernel use dduring the upgrade. Perhaps the 2.6.22-14-generic (or earlier?) is indeed needed to get dpkg --configure -a'  to recover the system (and to get a successful upgrade to Hardy in the first place).

So now this machine is now happily booting Puppy Linux and I can get on with work until this Ubuntu fiasco is sorted out.

It makes me wonder though if I should be considering Mint or PCLinuxOS. I certainly found PCLinuxOS very impressive in the past, and an old neighbour who is very new to Linux has been very happy with Mint as his first platform on Linux.

ps I think I would leave your server completely alone, and hope that a new kernel will be released and that you will be able to upgrade to it. However I am not confident that the kernel you are running is not terminally defective in that regard, so upgrading will be doomed to fail at the same step.

---

### Post by DavidTangye on 2008-08-21
Progress. I could recover my Hardy system by booting into the new Hardy kernel,[ as reported now on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/259956"), repeated here...
> The problem appears to be only in the latest version of gutsy, ie 2.6.22-15-generic.

Others on the forum report 2.6.22-14 being ok to recover and complete a dist upgrade by running 'dpkg --configure -a'  from a recovery boot (init 1 ie 'single'), and I have just run 'dpkg --configure -a' using  hardy 2.6.24-19-generic successfully from a recovery boot. So far I appear to have a gui session running normally.

There must be something in 2.6.22-15 that is clashing with the locale stuff which is what is surfacing to wreck dist upgrades.

---

### Post by geekas on 2008-08-21
Yes I too had the upgrade to Hardy come off the rails and had to resort to another partition to find this forum. I took siberoptik's advice:
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.



Good luck
but my system had a twist in the tail. The dpkg stopped, complaining of too many errors. After running it about 5 times it was getting no better so I redirected it's output to a file:

dpkg --configure -a > errors.txt

and errors.txt said:

Setting up dbus (1.1.20-1ubuntu1) ...
Warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory
The user `messagebus' already exists. Exiting.

So I changed to the /run directory and made a dbus directory:

mkdir dbus

and ran dpkg again. This time it went all the way. After a reboot the Heron took off and I had my system back with no major dysfunctions except a couple of firefox plugins (so far). Thanks to siberoptik and the many contributors to this forum. :)

---

### Post by DavidTangye on 2008-08-21
I note that some people here are not from Australia, and others do not indicate where they are from. It would be useful to know if this is a problem with just the en-AU locale.

Is this problem only related to the en_AU locale, or are there some of you (eg from outside of Australia) who do not have en_AU locale defined anywhere, yet still get this problem?

---

### Post by Janeleaper on 2008-08-21
I had the problem and I'm in Alberta Canada.

---

### Post by DavidTangye on 2008-08-21
> **Janeleaper said:**
> I had the problem and I'm in Alberta Canada.Great. Have you included the Australian locale ie en_AU, in your system?

---

### Post by Sir Jake on 2008-08-22
I have the same issue and I only used US. :(
Looking onto my grub file I see kernel xxx.14  on the list, do you think loading that would fix this error?

---

### Post by DavidTangye on 2008-08-22
> **Sir Jake said:**
> I have the same issue and I only used US. :(
Looking onto my grub file I see kernel xxx.14  on the list, do you think loading that would fix this error?It seems so. [siberoptik]("http://ubuntuforums.org/member.php?u=628992") indicated in post #3 here that 'dpkg --configure -a' fixed the problem using this kernel. Also I found that booting the new hardy kernel  2.6.24-19 also allowed  'dpkg --configure -a'  to run successfully. The problem at this stage would therefore appear to be in kernel xxx.15 - the currently latest gutsy kernel.

Don't forget to boot into init level 1 (recovery mode).

As [I noted on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/259956") when you run 'dpkg --configure -a' you get something like this slightly edited listing"
> Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
... etc
  en_ZW.UTF-8... done
Generation complete.

Setting up ubuntu-minimal (1.102) ...
Setting up language-pack-gnome-en (1:8.04+20080708) ...
Setting up language-pack-en (1:8.04+20080708) ...
Setting up language-pack-gnome-en-base (1:8.04+20080527) ...
 * Reloading GNOME Display Manager configuration...       [80G  [33m*[39;49m Changes will take effect when all current X sessions have ended.

Setting up language-pack-en-base (1:8.04+20080527) ...
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
... etc again
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
 * Reloading GNOME Display Manager configuration...       [80G  [33m*[39;49m Changes will take effect when all current X sessions have ended.Good luck ;)

---

### Post by hebuntu on 2008-08-22
After upgrading and the process freezing at locale, i rebooted into the recovery mode of the previous kernel, did the dpkg --configure -a, 
then rebooted into latest kernel, ran same command, rebooted again and all was fine.

---

### Post by hitspace on 2008-08-23
is there anyway someone could walk me through this because ubuntu wont let me log on as an administrator just keeps "loading". Is there any command i can run during the boot sequence in safe mode that will let me fix this problem . I REALLY dont want to go nuke then install ubuntu again. If there is any coincidence this happens everytime i try to upgrade. Every time i get the guts to upgrade to heron it screws me over like this :( someone plz help ...

---

### Post by gatenby_jp on 2008-08-23
the answer to your problem ... is in one of the earlier posts in this thread ... you need to reboot in recovery mode for the previous kernel ... in otherwords the one before you started the upgrade process

---

### Post by hitspace on 2008-08-23
The problem i have though above that is the grub loader only shows xxx.15 and xxx.17 . I was under the impression i needed to log in under xxx.14 to fix the problem in the method sibertopik did .

---

### Post by Partyboi2 on 2008-08-23
It shouldn't matter as long as it is a previous kernel, so in your case xx.15

---

### Post by DavidTangye on 2008-08-23
> **hitspace said:**
> The problem i have though above that is the grub loader only shows xxx.15 and xxx.17 . I was under the impression i needed to log in under xxx.14 to fix the problem in the method sibertopik did .xx.17? Is that a new fix just out? The problem was with xx.15. Try recovery booting xx.17, and run the 'dpkg --configure -a' command from there. Read the above posts carefully. You will see that I fixed this machine by using the partly upgraded Hardy 2.6.24-19 kernel, However, on reflection, I probably got the initial upgrade further progressed by carefully killing just the localedef and parent prcoesses, so the upgrade progressed through to updating the kernels and recording this in the grub menu.

Edit: AFAIK: There IS no later kernel for gutsy than 2.6.22.15, eg in archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/, we have linux-restricted-modules-2.6.22-15-generic_2.6.22.4-15.11_i386.deb dated June 19. I find no evidence of any 2.6.22-17.

---

### Post by hitspace on 2008-08-23
I managed to log into a fail safe session and typed the command sudo dpkg .... but the next line it loads is the one that hangs. Am i doing something wrong here? Im running this on a dell m600 should i just reinstall the older versions after wiping ?

wait in what script should i type the dpkg command root intrid ... ?

---

### Post by DavidTangye on 2008-08-23
> **Partyboi2 said:**
> It shouldn't matter as long as it is a previous kernel, so in your case xx.15No, I think that the problem might be specifically in the 2.6.22.15 version.

---

### Post by Partyboi2 on 2008-08-23
> **DavidTangye said:**
> No, I think that the problem might be specifically in the 2.6.22.15 version.
Then I stand corrected :)  thanks for pointing that out.

---

### Post by DavidTangye on 2008-08-23
> **hitspace said:**
> I managed to log into a fail safe session and typed the command sudo dpkg .... but the next line it loads is the one that hangs. Am i doing something wrong here? Im running this on a dell m600 should i just reinstall the older versions after wiping ?

wait in what script should i type the dpkg command root intrid ... ?I cannot say for certain, but I am fairly sure that the fail-safe session is not the place to run the dpkg command. Instead, when you boot, choose the '(recovery mode) grub menu option. It starts the kernel and basic services only, then in gutsy drops you into a shell. There you are in 'init level 1' as root. Run the command there. Then hit ctrl-alt-del to initiate a reboot.

---

### Post by hitspace on 2008-08-23
im wondering though if i tried ubuntals fix which was killing the unresponsive process how exactly do i do that because i cant get the "top" command to work in any script i open.

---

### Post by DavidTangye on 2008-08-23
> **hitspace said:**
> im wondering though if i tried ubuntals fix which was killing the unresponsive process how exactly do i do that because i cant get the "top" command to work in any script i open.```
ps -ef
```

---

### Post by jjtstan on 2008-08-24
I've got the same problem as Edward4310.  When I boot up & hite Esc (GRUB?) I get three kernel options, 2.6.22-19-generic, 22-15-generic, 22-14-generic, and their recovery modes. 

I initially booted into kernel 22.14's recovery mode and ran dpkg -- configure -a, and the system hung on generating locales.  I didn't think to kill the locale generation processes, rebooted and tried again, and then tried running dpkg --configure -a in kernel 15 and kernel 19.  

Now there's no locale problems, but no matter which kernel I boot into, I get the same errors as Edward4310:

dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.eric (recovery mode), -15 

If I try going into GNOME failsafe mode, the login & password are typed in using giant characters (the text entry boxes are normal size, but the text I'm entering looks like it's 48-point font, so I only see a small portion of the characters), and then I get a plain beige screen with no icons, no menus, no nothing.  The mouse tracks around, but there's nothing to click on, no way to raise a terminal window.  

I was running Gutsy 7.10 on a Dell Inspiron 530 with Nvidia graphics card (Dell-installed Ubuntu).

Any suggestions where to go from here?  

Alternatively, instructions on how to copy my hard disk's contents onto a portable hard drive using the command line in recovery mode would be appreciated. Then I could just re-install the entire OS.

---

### Post by Janeleaper on 2008-08-24
This is a Dell related problem.  I had it too on my Dell 530.

I'm not technically competent, but I got good help on the Dell forum.  Look for my thread there.

---

### Post by Janeleaper on 2008-08-24
This was Prinknash's advice to me - which worked:

After pressing F2, you enter 'Setup'.
- At the 'Integrated Peripherals' screen, go to SATA mode and select RAID (rather than the default IDE)
- Save changes and reboot.


The only problem I was left with was a black margin down one side of the screen.  That can be dealt with by using the monitor buttons to auto-adjust.

---

### Post by jjtstan on 2008-08-25
Okay, I'm continuing to fail in new and spectacular ways.  Updates on this other thread: 

[http://ubuntuforums.org/showthread.php?p=5661158#post5661158](http://ubuntuforums.org/showthread.php?p=5661158#post5661158)

Any help appreciated.

---

### Post by hubie on 2008-08-25
I've got the hang on en_AU.UTF-8 as well.  Does anyone have an idea why I am using the AU locale anyway?  Does it generate all the locales by default, and AU just happens to be the first one it comes to?  When I originally installed, I told it I live in the US, etc.

---

### Post by hubie on 2008-08-25
I followed the instructions from the third post and it worked out well for me.  I had to reboot once and do the [FONT="Fixedsys"]dpkg --configure -a[/FONT] command a second time, but now all is well.  My thanks to all who gave helpful advice in this thread.

Because I got the update to continue, I answered my above post regarding the AU locale.  It does do all the locales and the AU is the first on the list.

---

### Post by jjtstan on 2008-08-26
My problem got solved, and Hardy is up and running, all data preserved.  

I put the details in the related thread over in the Dell forum. 

Thanks again to everyone for their help.

---

### Post by wlangston on 2008-08-27
> **gwen said:**
> I tried the suggested fix and booted the .14 kernel, ran dpkg, and it worked and upgraded to 8.04. However, it still does not log in, and when I try to run dpkg again, it outputs a bunch of lines, followed by this:
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.

```
I waited a long while before upgrading to Hardy - you would think bugs like this would be worked out by now. Why are so many people having trouble upgrading and no solutions to fix this?

I got to the same place.  I found this thread (see post #15):
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=766448&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=766448&page=2)
So I rebooted into the newest kernel recovery mode (I actually don't think it matters at this point) and ran 
```
dpkg --configure -a > error.log
``` like it says.  Before the message above I got the same warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory.  I created the directory ```
mkdir /var/run/dbus
``` and re-ran ```
dpkg --configure -a
``` and everything worked perfectly after that.

Good luck.

---

### Post by z0r on 2008-09-06
Whenever I tried to kill localedef, nothing would happen. Even kill -9 had no effect. The only way I could stop the process was to reboot, and most of the time I had to do a hard power off (by holding the power button down for a while).

In the end I had to de-select the en_AU locale to get it past this step. I edited
```
/var/lib/locales/supported.d/local
```
and removed the line:
```
en_AU.UTF-8
```
Then I ran this again:
```
dpkg --configure -a
```
This time it generated all the locales successfully, including en_AU. I'll try re-selecting it when I finish upgrading to 8.04.

---

### Post by dgray_from_dc on 2008-09-07
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

Thanks!  You just saved my VAIO from the scrap heap.

---

### Post by Rockling on 2008-09-12
Hi 
Killed the locale gen and rebooted but when i ran 
sudo localedef --no-archive -i en_AU -c -f UTF-8 en_AU.UTF-8 
nothing happend
so I ran
sudo dpkg --configure -a
and it installed all the locales and finished the install

Thanks for the help

---

### Post by gdoeben on 2008-12-30
> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

Having the same problems as described above I have tried the procedure with xxx.14 and xxx.15 but in both cases the 'dpkg --configure -a' command ended up in unsolved dependency problems. The root of these problems was the kde-en-base-language package. Then I removed the kde package with 'sudo aptitude remove kde' and then everything worked fine. Even my 'kile 2.0' LaTeX editor still worked although kile  is a kde-program. 

gdoeben

---

