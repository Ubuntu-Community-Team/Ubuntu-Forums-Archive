---
title: "Login at login screen produces return to said screen."
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Maupertus on 2009-10-25
For some reason, all of a sudden, the following happens.
If I boot up my computer, choose Ubuntu in GRUB, I get the login screen. If I log in with correct credentials, everything seems to happen as it should, but after the bongo's, I'm get back at the login screen.

I've rebooted and restarted the pc numerous times, but it won't let me in Ubuntu. 

After going into safe mode I tried starting Ubuntu via the 'startx' command, but the system stalled after trying to start x.

Can someone tell me how I should address this really big nasty problem?

---

### Post by TrueTom on 2009-10-25
You can try the Gnome Failsafe session at the login screen for the time being...

---

### Post by twright on 2009-10-25
Probably the fastest way to fix this is to login via the terminal and move your config files to stop them from breaking gnome. Just press ctrl+alt+f6, login and type in these commands:
```

mkdir config-old
mv .* config-old

```

After this you should reboot and everything should work again. Note this will reset the config of some applications but you can copy back any settings you need.

Good luck :-)

---

### Post by Maupertus on 2009-10-25
That seems to work. Hoped that when I logged out and then in again with a normal session, the fluke would be over, but no...

Something happens that throws me back to the login screen.

Edit: sorry twright, I was responding to TrueTom, I wil try your solution now)

---

### Post by Maupertus on 2009-10-25
> **twright said:**
> Probably the fastest way to fix this is to login via the terminal and move your config files to stop them from breaking gnome. Just press ctrl+alt+f6, login and type in these commands:
```

mkdir config-old
mv .* config-old

```

After this you should reboot and everything should work again. Note this will reset the config of some applications but you can copy back any settings you need.

Good luck :-)

Hey Twright, 

did you maybe make a typo, or did I do something very wrong? ;)
I get the following message:

mv: cannot move '.' to config-old/ Device or service busy
mv: cannot move '..' to config-old/ Device or service busy

Kind regards

---

### Post by twright on 2009-10-25
oops, that should not happen (it looks like mv behaves differently to rm)
never the less, did it work?

if not try
mv -i .* config-old
and say no when it prompts you for . and ..

---

### Post by Maupertus on 2009-10-25
If I now login with the Failsafe Gnome session, I can see how all settings have reverted to the original clean install settings.

However, I can still not login using a 'normal' gnome session.

---

### Post by twright on 2009-10-25
> **Maupertus said:**
> If I now login with the Failsafe Gnome session, I can see how all settings have reverted to the original clean install settings.

However, I can still not login using a 'normal' gnome session.
In that case something is probably broken at a system level, it might thus be easier to do a fresh install especially considering that a new version of Ubuntu is being released in 4 days anyway (you can download the release candidate now and beat the rush).

If not did you make any recent changes to your system - it would be unusual for it to just break.

---

### Post by Maupertus on 2009-10-25
I was afraid we might come to that conclusion. 

I've never had a problem this severe with Ubuntu, not even while Beta-testing. Didn't even have any extra ppa's or exotic repositories added.

---

### Post by flipper9 on 2009-10-25
I had the same issue.  I rebooted, then couldn't login.  I logged into failsafe gnome, but couldn't connect to wireless.  Deleted some hidden config files in my home directory, then rebooted and could successfully login but still can't connect to wireless.  Not sure what is going on.

---

### Post by flipper9 on 2009-10-26
Okay, I reformat, reinstall Karmic...everything fine.  Run all the updates, reboot...can't login...getting the same problem, start to login, get the drums, then logged out back to GDM.  Tried deleting the .compiz folder of settings, but that didn't help.  Bleh, not sure what is going on.  Totally unuseable.

Installed Virtualbox non-OSE, ubuntu-x-swat, audacity in addition to the vanilla install.

---

### Post by flipper9 on 2009-10-26
I deleted all hidden folders and files in my home directory, no change in behavior.  Still can't login into regular Gnome.

---

### Post by Maupertus on 2009-10-26
I haven't reinstalled yet, but this isn't giving me any hope.

What hardware are you running.

I'm experiencing these problems on a Eee Pc 904 HA.
Intel integrated graphics cards GM450
1 GB Ram.

Dual Booting Windows 7

I checked my ppa's and I lied, I have the webkit and midori ppa's installed. I've had the x-org testers ppa enabled, but haven't had it enabled for a couple of weeks now.

---

### Post by flipper9 on 2009-10-26
I have an Asus Eee PC 1000h, Intel Atom procesor 1.6ghz, 1gb RAM, 160gb SATA hard drive, built-in Intel graphics.

Maybe the intel graphics are screwing up?  I'll be forced to reinstall...maybe this time I won't enable the updated graphics.  I'd submit a bug report, but I don't know yet what to report as who knows what is messing up.

---

### Post by Maupertus on 2009-10-26
Ah, the 904HA and 1000H(e or a) have basicly the same hardware. I can see a pattern evolving.

---

### Post by twright on 2009-10-26
Well I am on the eeepc 1000h with no such problems so I doubt it is anything impacting all users.

The one thing I do see in common though is that you both had updated version of the Intel drivers. Karmic has much nicer Intel drivers anyway so could you test again with a Vanilla install.

If you don't have any luck after a fresh install I suggest submitting a bug on launchpad - you can probably get some more debug info first as well.

@flipper9
Were these installed on Karmic or before

---

### Post by Maupertus on 2009-10-26
> **twright said:**
> Well I am on the eeepc 1000h with no such problems so I doubt it is anything impacting all users.

The one thing I do see in common though is that you both had updated version of the Intel drivers. Karmic has much nicer Intel drivers anyway so could you test again with a Vanilla install.

If you don't have any luck after a fresh install I suggest submitting a bug on launchpad - you can probably get some more debug info first as well.

@flipper9
Were these installed on Karmic or before

Depends, I don't know if flipper uses the x-org-testers, and even has made a custom install using it.

---

### Post by twright on 2009-10-26
> **Maupertus said:**
> Depends, I don't know if flipper uses the x-org-testers, and even has made a custom install using it.
ubuntu-x-swat contains similar, partially stable packages - in any case I recommend you try the live cd as it is probably the most likely way to fix your system unless it is a hardware problem.

---

### Post by Lieter on 2009-10-26
I'm having the same problem with kubuntu and ubuntu 9.10 on the same computer. 

I have my /home on a seperate partition and mount it on both installs. On ubuntu i can log in, no problem there. but Kubuntu(kdm) throuws me back to to the login screen. Not mounting /home works fine. I find a bit odd that i cannot log in with no KDE configs in my ~ and no errors are displayed in kdm.log. auth.log confirms a successfull login.

Any ideas

---

### Post by twright on 2009-10-26
> **Lieter said:**
> I'm having the same problem with kubuntu and ubuntu 9.10 on the same computer. 

I have my /home on a seperate partition and mount it on both installs. On ubuntu i can log in, no problem there. but Kubuntu(kdm) throuws me back to to the login screen. Not mounting /home works fine. I find a bit odd that i cannot log in with no KDE configs in my ~ and no errors are displayed in kdm.log. auth.log confirms a successfull login.

Any ideas
Well this problem is quite common if your configs get corrupted - try deleting the kde ones and it should work fine.

---

### Post by Brandon Williams on 2009-10-26
I am having the same problem on xubuntu since applying upgrades yesterday. The only upgraded packages that look like they could have anything to do with the problem are: dbus, dbus-x11, and hal.

After the failed login attempt, .xsession-errors says:
```
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (gnome-screensaver:2880): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
xfdesktop[2902]: starting up
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfwm4: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfdesktop: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```

If I switch to a console with Ctrl+Alt+F1, log in, and restart gdm with:
```
sudo service gdm restart
```
I can then switch back to the gdm screen and successfully log in.

I'm not certain which package to open the bug against. Any suggestion? Or has anyone else opened a bug already that I can confirm?


FWIW ... I am not having this problem on my Dell Mini 10v running the lpia architecture version of Karmic, and it is fully up to date with the repos, too. That said, the lpia repos appear to be a bit different than the i386 ones. For example, on lpia, I can't install xserver-xorg-input-all due to an dependency problem between xserver-xorg-input-vmmouse and xserver-xorg-core.

---

### Post by twright on 2009-10-26
> **Brandon Williams said:**
> I am having the same problem on xubuntu since applying upgrades yesterday. The only upgraded packages that look like they could have anything to do with the problem are: dbus, dbus-x11, and hal.

After the failed login attempt, .xsession-errors says:
```
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (gnome-screensaver:2880): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
xfdesktop[2902]: starting up
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfwm4: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfdesktop: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```If I switch to a console with Ctrl+Alt+F1, log in, and restart gdm with:
```
sudo service gdm restart
```I can then switch back to the gdm screen and successfully log in.

I'm not certain which package to open the bug against. Any suggestion? Or has anyone else opened a bug already that I can confirm?


FWIW ... I am not having this problem on my Dell Mini 10v running the lpia architecture version of Karmic, and it is fully up to date with the repos, too. That said, the lpia repos appear to be a bit different than the i386 ones. For example, on lpia, I can't install xserver-xorg-input-all due to an dependency problem between xserver-xorg-input-vmmouse and xserver-xorg-core.
I would just submit the bug against Ubuntu, it probably needs more diagnosis to be specific

---

### Post by WorLord on 2009-10-26
I *JUST* had, and fixed, this problem on my computer.  A Dell Dimension 3000, Intel i865G video hardware.

The problem: I had the Ubuntu-X-Swat repository enabled.  The 2.9.0 driver has long since been moved to Karmic proper, but the repo contains new Mesa packages which break everything. 

Failsafe Gnome works because it loads 2d GNOME with no 3d-drivers or Compiz; what's actually happening is X is failing to load with UXA on the Intel Chipset. 

HOW I FIX: 
-Boot into failsame Gnome.  
-Open Synaptic.  
-Disable the Ubuntu-X-Swat repository.  
-Find the packages it installed (should be in the "Installed: Local or obsolete" category).  
-Highlight everything with the word "Mesa" in it, and CTRL+E to choose to use the Karmic repo version of these files.  
-Apply.
-Reboot

Things are working just fine for me now.  I've left the Ubuntu-X-Swat repo disabled, because I only used it for the new Intel driver in the first place.

---

### Post by Brandon Williams on 2009-10-26
I am using the nvidia driver and I do not have the Ubuntu-X-Swat repo enabled. Mine may be a different problem if your solution solves the issue for everyone else.

Nevertheless, I opened [bug 461277](https://bugs.launchpad.net/ubuntu/+bug/461277). If anyone else see symptoms similar to what I described and your problem is _not_ a result of using the Ubuntu-X-Swat repository, please log on to launchpad and mark the bug confirmed.

---

### Post by twright on 2009-10-26
As I said this is a rather generic bug as any consistent crashes in X look like this. The usual solution is to delete config files as I said but if there is a larger bug on a system level then this will not help.

---

### Post by Maupertus on 2009-10-26
> **WorLord said:**
> I *JUST* had, and fixed, this problem on my computer.  A Dell Dimension 3000, Intel i865G video hardware.

The problem: I had the Ubuntu-X-Swat repository enabled.  The 2.9.0 driver has long since been moved to Karmic proper, but the repo contains new Mesa packages which break everything. 

Failsafe Gnome works because it loads 2d GNOME with no 3d-drivers or Compiz; what's actually happening is X is failing to load with UXA on the Intel Chipset. 

HOW I FIX: 
-Boot into failsame Gnome.  
-Open Synaptic.  
-Disable the Ubuntu-X-Swat repository.  
-Find the packages it installed (should be in the "Installed: Local or obsolete" category).  
-Highlight everything with the word "Mesa" in it, and CTRL+E to choose to use the Karmic repo version of these files.  
-Apply.
-Reboot

Things are working just fine for me now.  I've left the Ubuntu-X-Swat repo disabled, because I only used it for the new Intel driver in the first place.

This worked for me as well!

Now, this has to be a n00b question, but euhm.... how do I out my old configs back? I tried pasting everything from config-old into .config, but it hasn't done the trick.

Very happy my problem is solved!

---

### Post by twright on 2009-10-26
> **Maupertus said:**
> This worked for me as well!

Now, this has to be a n00b question, but euhm.... how do I out my old configs back? I tried pasting everything from config-old into .config, but it hasn't done the trick.

Very happy my problem is solved!
You should not put them in .config (actually you should probably delete that now), just copy them straight into your home folder.

---

### Post by Maupertus on 2009-10-26
> **twright said:**
> You should not put them in .config (actually you should probably delete that now), just copy them straight into your home folder.

I'm going to buy you a digital bunch of flowers and cook you digital dinner twright :)

Things like this always make me regret the fact that when I started with warty back in the day, I didn't dive deeper in the backend of linux.

---

### Post by flipper9 on 2009-10-26
> **twright said:**
> Well I am on the eeepc 1000h with no such problems so I doubt it is anything impacting all users.

The one thing I do see in common though is that you both had updated version of the Intel drivers. Karmic has much nicer Intel drivers anyway so could you test again with a Vanilla install.

If you don't have any luck after a fresh install I suggest submitting a bug on launchpad - you can probably get some more debug info first as well.

@flipper9
Were these installed on Karmic or before

I was running Karmic from the late Alphas with the xorg-edgers (bleeding edge) drivers for the longest time with no issues until the past couple of days.  After the reinstall, I decided to be a little more conservative and use the x swat updates PPA (more stable) video drivers in case some unstable video driver is causing the problem.  On the next reinstall, I'll just go with the Intel drivers that come with stock Karmic.

---

### Post by twright on 2009-10-26
> **flipper9 said:**
> I was running Karmic from the late Alphas with the xorg-edgers (bleeding edge) drivers for the longest time with no issues until the past couple of days.  After the reinstall, I decided to be a little more conservative and use the x swat updates PPA (more stable) video drivers in case some unstable video driver is causing the problem.  On the next reinstall, I'll just go with the Intel drivers that come with stock Karmic.
There is not much point in running any of those ppas in Karmic as the Intel drivers are nice and uptodate anyway.

@Maupertus
Nice to hear it is working again :-)

Don't worry, you learn all this terminal stuff soon enough, its just a matter of doing it.

---

### Post by flipper9 on 2009-10-26
> **twright said:**
> There is not much point in running any of those ppas in Karmic as the Intel drivers are nice and uptodate anyway.

@Maupertus
Nice to hear it is working again :-)

Don't worry, you learn all this terminal stuff soon enough, its just a matter of doing it.

I reinstalled Karmic and updated using the stock repositories.  No issues so far with the Intel drivers packaged with Karmic.  I'll avoid the temptation to upgrade my drivers! :D

---

### Post by twright on 2009-10-26
> **flipper9 said:**
> I reinstalled Karmic and updated using the stock repositories.  No issues so far with the Intel drivers packaged with Karmic.  I'll avoid the temptation to upgrade my drivers! :D
Great, nice to see it working for another person :-)

---

### Post by Praxicoide on 2009-10-27
I'm on Jaunty and it indeed appears to be a problem with the ppa mesa packages. I had this problem today too; I couldn't log in except through the 2.6.28 kernel because that one had no special effects (blacklisted Intel, the whole reason why I had the ppa packages).

I didn't want to upgrade to Karmic until after the official release, so what I did was to download the corresponding mesa karmic debs (just the ones I had installed) manually, and then I nstalled them with dpkg. I rebooted and I can again log in with special effects (I couldn't get them through Synaptic, because even after changing the repositories, for some reason it assumed the packages were already downloaded).

---

### Post by twright on 2009-10-27
> **Praxicoide said:**
> I'm on Jaunty and it indeed appears to be a problem with the ppa mesa packages. I had this problem today too; I couldn't log in except through the 2.6.28 kernel because that one had no special effects (blacklisted Intel, the whole reason why I had the ppa packages).

I didn't want to upgrade to Karmic until after the official release, so what I did was to download the corresponding mesa karmic debs (just the ones I had installed) manually, and then I nstalled them with dpkg. I rebooted and I can again log in with special effects (I couldn't get them through Synaptic, because even after changing the repositories, for some reason it assumed the packages were already downloaded).
Good to see it working again for you too.

As a general rule, you will be more stable with a testing release, even if it is still in development, than with a less tested frankendistro backporting some packages and running them together in weird combos.

In any case it is probably close enough to Karmic's release to upgrade now (beat the rush on the servers).

---

### Post by BornTwisted on 2009-10-27
Thumbs up for the advice, worked for me too. Had the Login problem with a fresh install of Xubuntu 9.10 RC.

Had the files saved off already so no need to backup, so just removing the .config folder did the trick.
```
rm -r ~/.config
```

Thanks :)

Just started re-applying the settings one by one and logging in and out in between and can confirm that the problem comes back after I change the screen resolution.

Anyone know how to get around this? According to "Hardware Drivers" in System I'm not using any proprietary drivers (Using a Radeon X1550 64-bit).

---

### Post by BornTwisted on 2009-10-28
To further refine the fix and to keep the config's of some other programs in tact you can just delete the xcfe4 folder.

```
rm -r ~/.config/xfce4
```

---

### Post by twright on 2009-10-29
> **BornTwisted said:**
> To further refine the fix and to keep the config's of some other programs in tact you can just delete the xcfe4 folder.

```
rm -r ~/.config/xfce4
```
Well it depends on what you are running - I would backup any config file first though

---

