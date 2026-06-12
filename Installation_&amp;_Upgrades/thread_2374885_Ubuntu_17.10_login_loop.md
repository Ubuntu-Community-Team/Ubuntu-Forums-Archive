---
title: "Ubuntu 17.10 login loop"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by aridus on 2017-10-20
I upgraded my Dell XPS yesterday to Ubuntu 17.10. I am able to login with Unity, but not via either of the other two options (that would lead to gnome): the login screen simply returns (a login loop, if you wish). I have searched for solutions to this but to no avail. This laptop has been through several versions of Ubuntu without previous problems.

If anybody has any suggestions, I would be grateful.

---

### Post by dino99 on 2017-10-20
which graphic it is ?
by default, ubuntu open a wayland session : there are known issues with some nvidia drivers & with radeon cards
at the login step, select a x11 session

---

### Post by aridus on 2017-10-20
Thank you. Graphics card:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```

I have tried both the default wayland and x11 sessions, but to no avail: it is a login loop for both.

---

### Post by aridus on 2017-10-20
Some further information on this problem. Following the advice in [https://askubuntu.com/questions/450545/login-loop-14-04-but-guest-account-is-accessible](https://askubuntu.com/questions/450545/login-loop-14-04-but-guest-account-is-accessible), I used 

ls  -ld  ~/.*authority

and found  

-rw------- 1 aridus aridus 118956 Oct 20 10:50 /home/aridus/.ICEauthority
-rw------- 1 root root    100 Oct 20 10:30 /home/aridus/.Xauthority

Again, following the advice in this thread, I used 

sudo  chown  aridus:aridus  ~/.Xauthority

and now I have 

-rw------- 1 aridus aridus 118956 Oct 20 10:50 /home/aridus/.ICEauthority
-rw------- 1 aridus aridus    100 Oct 20 10:30 /home/aridus/.Xauthority

However, I can still only login with Unity, and not via wayland or x11.

---

### Post by solitaire on 2017-10-20
Can you access the grub boot menu?
Try using an older kernel see if you can log in to the required desktop. 

(I've an Nvidia card in my box and I get the logon loop every time a new kernel is installed. I need to manually reinstall the Nvidia drivers every time.
Due to DKMS is not rebuilding when a new kernel is installed.)

---

### Post by aridus on 2017-10-20
Thank you for this interesting idea, which I have tried. I can roll back to the 4.10 kernel, but it does not resolve the situation.

---

### Post by aridus on 2017-10-21
I have now followed the instructions at [https://askubuntu.com/questions/551991/ubuntu-stuck-on-login-screen](https://askubuntu.com/questions/551991/ubuntu-stuck-on-login-screen) (but replacing lightdm with gmd3, and including a purge of gdm and ubuntu-desktop, and reinstall) but to no avail.

I've read a number of links and threads but have found no further suggestions. Does anybody have any other ideas?

With grateful thanks

---

### Post by aridus on 2017-10-21
Having just read this thread [https://askubuntu.com/questions/846862/stuck-in-login-ubuntu-14-04-after-trying-everything](https://askubuntu.com/questions/846862/stuck-in-login-ubuntu-14-04-after-trying-everything)

I ran sudo ubuntu-drivers devices and found that intel-microcode could be installed. Did so, but it did not help.

---

### Post by solitaire on 2017-10-21
Can you see anything in /var/log/syslog ?

Boot into recovery mode and take a look at the syslog.
Look for any "gnome-session" or "gnome-session-binary" or "gnome-shell" errors

Or any errors or fails you see in the log file. That should help narrow down the problem.

---

### Post by damienjbyrne on 2017-10-21
Hi there, I was having the exact same issue. I had been using gnome with a number of shell extensions enabled. I renamed this file:

~/.config/dconf/user

And then I could log in, but without a number of my gnome customisations. I tried re-enabling a few of the extensions and it seems that any that modify the top bar make it crash.

---

### Post by aridus on 2017-10-21
Thank you @solitaire. I am not sufficiently knowledgeable to know what I am looking for but I tried a login under Wayland and for that time found the following:

Oct 21 18:42:20 martin gnome-session[2005]: gnome-session-binary[2005]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
Oct 21 18:42:20 martin gnome-session-binary[2005]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1

Oct 21 18:42:21 martin gnome-session[2005]: gnome-session-binary[2005]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Oct 21 18:42:21 martin gnome-session-binary[2005]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Oct 21 18:42:21 martin gnome-session-binary[2005]: Unrecoverable failure in required component org.gnome.Shell.desktop

---

### Post by aridus on 2017-10-21
@damienjbyrne Under 17.04 I had at one point installed gnome, and then removed it. So, I followed your suggestion,, and renamed ~/.config/dconf/user 

It removed all of my custom settings in Unity but has not allowed me to boot into Ubuntu on Wayland or X11. Is there a gnome-specific configuration file that I could try deleting?

---

### Post by aridus on 2017-10-22
I am reporting here that I gave up on this. Obviously there was something stuck somewhere, so to speak, but I was wasting too much time trying to fix it. I therefore did a fresh install of Ubuntu 17.10 but this did not solve the problem (I have / and home on separate partitions and did not format the home partition).

I therefore deleted all hidden files and folders in the home partition, and reinstalled, and now the login loop has gone.

---

### Post by aridus on 2017-10-22
With thanks to all of those who tried to help, but I gave up on this after spending a long, futile time trying to resolve the situation.

I have resinstalled Ubuntu 17.10 but, as I have / and home on separate partitions, I had to first of all delete all hidden files and folders in the home partition (an attempt without doing this did not resolve the situation). Following resinstallation the login loop has gone.

---

### Post by ulysses77 on 2017-10-28
Alright, I'm having the exact same issue and it's absolutely driving me nuts. What the heck can I do to get Ubuntu to just act normally? I don't get what's causing this issue

---

### Post by aridus on 2017-10-29
A clean install was, unfortunately, my only solution.

---

### Post by jkapelus on 2017-10-30
> **aridus said:**
> A clean install was, unfortunately, my only solution.

Mine only started looping after installing a few new gnome extensions.

journalctl -b showed 'org.gnome.Shell.Desktop' killed by signal 11.

In "/home/$USER/.local/share/gnome-shell/extenstions/", I "rm -f -r" each extension directory that I recognised as recent.

After a reboot, the login loop was solved.

---

### Post by comexmix on 2017-10-30
I solved this issue easily by doing the following:
Start Ubuntu. At the login use the following keys CTRL+ALT+F2 to enter the terminal.
Once logged in, type: 
sudo apt-get update
Then
sudo apt-get upgrade
it will prompt you to configure errors with a dedicated line. Just write it and let it run. 
It worked fine for me. Ubuntu 17.10 running now and it looks great.

---

### Post by baddison1 on 2017-10-30
I have just completed a brand new fresh install of ubuntu 17.10.  I followed all previous hacks and instructions to disable wayland server.  I can confirm I'm using x11 by doing "echo $XDG_SESSION_TYPE".  It returns "x11".  When I install any of the NVIDIA drivers, it causes a consistent boot loop and I cannot get to the login screen at all.  I am able to boot into GRUB and mount files system as ROOT to uninstall all traces of nvidia.   I can now boot into xorg - X11, but the video is HORRIBLE, slow painting of screens, still videos with sound and no movement.  I have even tried older versions of NVIDIA drivers and not just the newest ones....all with the same exact result: BOOT LOOP.  I am confused as to why the drivers do not work.  I understand that wayland is not yet compatible with nvidia for 'buntu 17.10 as yet.....but I am not using wayland, I'm using XORG.  

so confused

---

### Post by baddison1 on 2017-10-31
> **comexmix said:**
> I solved this issue easily by doing the following:
Start Ubuntu. At the login use the following keys CTRL+ALT+F2 to enter the terminal.
Once logged in, type: 
sudo apt-get update
Then
sudo apt-get upgrade
it will prompt you to configure errors with a dedicated line. Just write it and let it run. 
It worked fine for me. Ubuntu 17.10 running now and it looks great.

@comexmix  did you already have nvidia drivers installed when you performed this? do the drivers need to be installed "outside" of Ubuntu 17.10 ?

---

### Post by sunnybharel on 2018-01-09
Here is how I solved this issue:

In /var/logs/syslog I noticed:
[IMG]https://photos.app.goo.gl/fY845PclQx53v49w2[/IMG][ATTACH=CONFIG]278102[/ATTACH]
[IMG]https://photos.app.goo.gl/fY845PclQx53v49w2[/IMG]

The solution:
[ATTACH=CONFIG]278101[/ATTACH]

---

### Post by warren-sensei on 2018-01-20
So, this problem showed up for me the other night, and I've gone through and tried each proposed solution, one by one, with no results. 
Any new thoughts?

---

### Post by warren-sensei on 2018-01-20
So, this problem showed up for me the other night, and I've gone through and tried each proposed solution, one by one, with no results. 
Any new thoughts?

This might be a n00b-type question but, while I can log in from the shell command line, I can't start gnome-shell ("gnome-shell unsupported session type"). I can do "startx", but it loads a slightly different version of Gnome that doesn't quite work the way I had Gnome running under normal conditions - a couple different icons (Ubuntu Software Center, for instance), workspace configuration I set up with gnome-shell extensions, theme is just slightly different... it's probably unrelated to the core problem of the login loop, just Gnome being started weirdly because I'm not going through the usual channels, but confusing.

---

### Post by joeprusa on 2018-02-01
> **warren-sensei said:**
> So, this problem showed up for me the other night, and I've gone through and tried each proposed solution, one by one, with no results. 
Any new thoughts?

This might be a n00b-type question but, while I can log in from the shell command line, I can't start gnome-shell ("gnome-shell unsupported session type"). I can do "startx", but it loads a slightly different version of Gnome that doesn't quite work the way I had Gnome running under normal conditions - a couple different icons (Ubuntu Software Center, for instance), workspace configuration I set up with gnome-shell extensions, theme is just slightly different... it's probably unrelated to the core problem of the login loop, just Gnome being started weirdly because I'm not going through the usual channels, but confusing.


OK, I found a solution:

```
sudo apt remove upstart --purge
```

Thanks to everyone at 
[https://plus.google.com/u/0/+fuxoft/posts/MHtu75S6JVK](https://plus.google.com/u/0/+fuxoft/posts/MHtu75S6JVK)

---

### Post by mildayil on 2018-02-11
I can confirm that "**sudo apt remove upstart --purge**" fixed this problem for me...  I tried every hack in the forum and was afraid to purge the upstart because using upstart in Grub was sometimes the only way to get my machine to boot.  I took the plunge, and voila, Gnome is beautiful!@

---

### Post by johnnyparafango on 2018-02-22
> **sunnybharel said:**
> Here is how I solved this issue:

In /var/logs/syslog I noticed:
[IMG]https://photos.app.goo.gl/fY845PclQx53v49w2[/IMG][ATTACH=CONFIG]278102[/ATTACH]
[IMG]https://photos.app.goo.gl/fY845PclQx53v49w2[/IMG]

The solution:
[ATTACH=CONFIG]278101[/ATTACH]
Thanks worked for me

---

### Post by ppp.yang on 2018-03-05
This works. Anyone upgrades from 16.04 to 17.10 and has the login loop can try this method. upstarts is not used anymore. Why not delete it!!!!!!!

---

### Post by ww-xs4all on 2018-03-26
> **mildayil said:**
> I can confirm that "**sudo apt remove upstart --purge**" fixed this problem for me...  I tried every hack in the forum and was afraid to purge the upstart because using upstart in Grub was sometimes the only way to get my machine to boot.  I took the plunge, and voila, Gnome is beautiful!@

thx, worked for me

---

### Post by xdz0611 on 2018-04-06
Well, I can also confirm that "sudo apt remove upstart --purge" fixed this problem for me... I have upgraded my laptop from 16.04 to 17.10 some days ago. Luckily, I found this solution so I can enjoy gnome desktop now. Thanks everyone.

---

### Post by elad21 on 2018-04-07
"sudo apt remove upstart --purge" worked for me as well. It is a bit frustrating that it isn't the first thing to appear in the answers though.

---

### Post by emiliosanchezcortezon on 2018-06-24
Thankkkk you. I upgraded the pc of my wife and i was gettting mad. I could not even load recovery mode. Then I found your solution and ...IT WORKED!.  sudo apt remove upstart --purge  You save my life.

---

### Post by tquinn10 on 2018-08-12
Did not work for me, on 16.04

---

### Post by coolboi567 on 2019-01-18
I had the same issue in Ubuntu Bionic  18.04.1 LTS.

Turns out it was caused by installation of [B]
indicator-multiload
[/B]
I had installed **Nvidia-390 driver for my Sony Vaio** week back and it was working perfectly.

Most probably, this applet was not compatible with Nvidia driver installed on my machine.

After removing the applet it was working fine.
```
 sudo apt-get remove --purge indicator-multiload 
```

---

