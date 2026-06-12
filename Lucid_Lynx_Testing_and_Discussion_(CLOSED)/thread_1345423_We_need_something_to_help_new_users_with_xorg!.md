---
title: "We need something to help new users with xorg!"
date: 2009-12-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SunnyRabbiera on 2009-12-04
In most newer distributions the old xorg.conf file is gone, HAL is being left behind in favor of devicekit/ UDisks.
HOWEVER now to set up your system the way you want you know have to shut down x and enter console mode and enter sudo Xorg -configure
This is quite complicated, one might have hardware you cannot get working via auto config so there has to be an easy way to get your hardware where you want it without the extra BS.
Lucid is supposed to be LTS, we need to have a backup to avoid tghe issues we have with Karmic.
We need to have some sort of front end, a helper to assist users set up hardware easily...
No terminals, no hard edge configuring, just something to aid both the new user and the seasoned user who is tired of manually editing/creating a new xorg configuration.

Vote up in brainstorm!

[http://brainstorm.ubuntu.com/idea/22804/](http://brainstorm.ubuntu.com/idea/22804/)

---

### Post by phenest on 2009-12-04
I haven't had to configure xorg for quite a while now. in fact, not in the last year. Time would be better spent on getting hardware working OOTB so as to not need any special configuring software. We need bug reports, not more software.

---

### Post by jerrylamos on 2009-12-04
> **phenest said:**
> I haven't had to configure xorg for quite a while now. in fact, not in the last year. Time would be better spent on getting hardware working OOTB so as to not need any special configuring software. We need bug reports, not more software.

Don't know about you, but on three of my four test systems I had a terrible time with karmic just trying to get it to boot up into something readable.  That went on for months.  

On Jaunty after a few minutes my Thinkpad screen became unreadable blotches.  Kernel problem fixed by an update months after RC.

Lucid I've had to use "nomodeset" already depending on the state of the updates.

With Ubuntu Alpha's and Beta's for over the last year there have been periods of months where they didn't work on intel and/or ati graphics.  Granted they usually straighten out by RC time, except even Intrepid I had to disable Compiz to get anything usable.

For a class I've been looking into sample demo's of Slax, Fedora, Suse, Knoppix, Debian.  They've all booted up readable and most have a "safe" mode which I haven't had to use.  

I vote for a "safe" mode for ubuntu that really is safe will work no matter what, and a pointer to someplace like:
Ubuntu multimedia and video forums:
" Sticky: [all variants] Comprehensive Multimedia & Video Howto"

Another choice is always to say:
"If ubuntu screws up video, don't give up linux altogether, try Knoppix" 
or something like that.

Jerry

---

### Post by VMC on 2009-12-04
> **jerrylamos said:**
> Don't know about you, but...Another choice ..to say:
"If ubuntu screws up video, don't give up linux altogether, try Knoppix" 
or something like that.I'm about at that point myself. I still need XP just to still use Skype reliably. Maybe its Skype's proprietary software or not, but it just fails miserably on any Ubuntu. Maybe Knoppix...

---

### Post by SunnyRabbiera on 2009-12-04
> **phenest said:**
> I haven't had to configure xorg for quite a while now. in fact, not in the last year. Time would be better spent on getting hardware working OOTB so as to not need any special configuring software. We need bug reports, not more software.

So you think, tell me then what happens when hardware detection fails and you are stuck at a low resolution of 720 x 400, you have no way to easily configure your monitor settings.
Gnome or KDE's monitor tool only gives you a max resolution of 800x600 when your real max resolution is 1600x1200...
You have no way of editing your monitor resolution by hand or otherwise unless you restart X and use command line.
This is not user friendly, this is not a good situation to have.
Just because you have had no issues with setting up hardware doesnt mean others dont.
Bug reporting can only go to far, what if you are in a pinch and the bug you filed never gets resolved?
If ubuntu is to compete with Windows or OSX we must focus on tools that are easy to use and help new users.
Dont just tell folks to go bug reporting, it wont solve the issue if we dont have some sort of helper tool.
Ubuntu Karmic has given many folks issues, if we are to truly stand out and stand up against Microsoft and Apple we must have something

---

### Post by castrojo on 2009-12-04
> **SunnyRabbiera said:**
> This is not user friendly, this is not a good situation to have.

You're right, but the answer isn't another tool, it's to fix it so it never breaks.

---

### Post by SunnyRabbiera on 2009-12-04
> **whiprush said:**
> You're right, but the answer isn't another tool, it's to fix it so it never breaks.

Yes but a tool does help, the issues people are having with Karmic should be our reasoning for creating tools to make things easier.

---

### Post by nanog on 2009-12-04
I wonder how common this is. 

I own or administer over 30 boxes (dell, hp, and lenovo/ibm) that range from netbooks to multi-core workstations and have not had a single x problem in karmic. I think we do need a front end for xrandr and nvidia problems but it really does seem like these problems are going to work themselves out as xrandr get more polish and wider adoption (talking about you nvidia...grrrrrr).

---

### Post by SunnyRabbiera on 2009-12-04
> **nanog said:**
> I wonder how common this is. 

I own or administer over 30 boxes (dell, hp, and lenovo/ibm) that range from netbooks to multi-core workstations and have not had a single x problem in karmic. I think we do need a front end for xrandr and nvidia problems but it really does seem like these problems are going to work themselves out as xrandr get more polish and wider adoption (talking about you nvidia...grrrrrr).

I just like safety nets, why make things complicated?

---

### Post by RockDoctor on 2009-12-04
An xorg autoconfiguration tool that always works perfectly sounds nice. However...

1. My monitor doesn't report usable information about itself. Native mode is 1680x1050, but until X gets a lot smarter than it is now, that's going to continue to require a modeline in xorg.conf. 

2. My new desktop has on-board Nvidia G9100 graphics. X doesn't work with nv. X doesn't work with nouveau. However, X does work with the nvidia driver. How the kernel going to know which module to load? And how is X going to know which driver to use?

Bottom line: we need something to help users with xorg

---

### Post by RAOF on 2009-12-04
> **RockDoctor said:**
> An xorg autoconfiguration tool that always works perfectly sounds nice. However...

1. My monitor doesn't report usable information about itself. Native mode is 1680x1050, but until X gets a lot smarter than it is now, that's going to continue to require a modeline in xorg.conf. 

Actually, X is quite smart enough to handle this right now; what we're missing is a little bit of support in gnome-display-properties for manual configuration.

Also, have you filed a bug?  Xorg & kernel developers are interested in quirks for the various types of broken hardware.

> **RockDoctor said:**
> 
2. My new desktop has on-board Nvidia G9100 graphics. X doesn't work with nv. X doesn't work with nouveau. However, X does work with the nvidia driver. How the kernel going to know which module to load? And how is X going to know which driver to use?
...

By running "jockey-text" from the console and installing the nvidia binary drivers, which will write out an xorg.conf setting 'nvidia' as the driver?  If neither nv nor nouveau support that card you won't be able to boot the livecd anyway.

---

### Post by RockDoctor on 2009-12-04
> **RAOF said:**
> Actually, X is quite smart enough to handle this right now; what we're missing is a little bit of support in gnome-display-properties for manual configuration.

Also, have you filed a bug?  Xorg & kernel developers are interested in quirks for the various types of broken hardware.



By running "jockey-text" from the console and installing the nvidia binary drivers, which will write out an xorg.conf setting 'nvidia' as the driver?  If neither nv nor nouveau support that card you won't be able to boot the livecd anyway.

Bug reports have been filed. As for booting the livecd, I'm typing this on my desktop booted from the Dec 3 livecd iso unetbootin'd to a USB flashdrive. The good news is it boots without messing around. The bad news is that the display resolution won't go higher than 800x600 when I boot like this.

---

### Post by RAOF on 2009-12-05
Oh, well.  At least Lucid's nv works for you a bit, then.

From there, installing the nvidia drivers is easy; we should offer to do it automatically.

---

### Post by psyke83 on 2009-12-05
RAOF, whiprush & others,

While I completely agree that Xorg needs to be fixed so that it never breaks, would it be possible to re-enable the script that generates a blank xorg.conf template as it did on Jaunty?

I'm not asking for Lucid to ship with a configuration file by default, just for a convenient* way to generate a configuration file to streamline the process of troubleshooting server/driver settings. I believe this will also help your cause in getting users to report driver quirks.

*Since Karmic, we need to do the following:
[LIST]
[*]Stop any running Xorg/display manager processes;
[*]Invoke "sudo Xorg -configure";
[*]Move the xorg.conf.new file in the working directory to /etc/X11/xorg.conf.
[/LIST]

Prior to Karmic, all we needed to was to invoke "sudo dpkg-reconfigure xserver-xorg".

---

### Post by SunnyRabbiera on 2009-12-05
> **psyke83 said:**
> RAOF, whiprush & others,

While I completely agree that Xorg needs to be fixed so that it never breaks, would it be possible to re-enable the script that generates a blank xorg.conf template as it did on Jaunty?

I'm not asking for Lucid to ship with a configuration file by default, just for a convenient* way to generate a configuration file to streamline the process of troubleshooting server/driver settings. I believe this will also help your cause in getting users to report driver quirks.

*Since Karmic, we need to do the following:
[LIST]
[*]Stop any running Xorg/display manager processes;
[*]Invoke "sudo Xorg -configure";
[*]Move the xorg.conf.new file in the working directory to /etc/X11/xorg.conf.
[/LIST]

Prior to Karmic, all we needed to was to invoke "sudo dpkg-reconfigure xserver-xorg".

Thats what I am on about, the process is more complicated in Karmic

---

### Post by RAOF on 2009-12-05
What about if there were a skeleton xorg.conf in /usr/share/xserver-xorg or such?

---

### Post by psyke83 on 2009-12-05
> **RAOF said:**
> What about if there were a skeleton xorg.conf in /usr/share/xserver-xorg or such?

Yes, that would be a perfectly acceptable compromise... :)

---

### Post by jerrylamos on 2009-12-05
> **RAOF said:**
> What about if there were a skeleton xorg.conf in /usr/share/xserver-xorg or such?

Amen!

Sure would be a big help to me!

I don't know what high speed high tech pc's the X developers use, but the resulting X code won't run right as booted on various of my test pc's like us ordinary folk use.

Somehow someone decided X was all fixed for all situations the developers were interested in so there was no need to provide a scaffold xorg.conf file or a "safe" mode boot like other linux's do.

For Intrepid, Jaunty, Karmic, now Lucid I've had to drop into command line mode to try to figure out what broke this time on the "black screen of death".  I can sort of hobble along with primitive "nano" with the considerable assistance from Ubuntu forum postings of other people who have had problems too.  I'm not alone.

Jerry

---

### Post by ronacc on 2009-12-05
regardless of how bulletproof X becomes there will always arise some situations where human managed adjustment will be necessary , any thing that will make that less painful will be welcome .

---

### Post by Gina on 2009-12-05
For some reason my Lucid screen has dropped to 1024x768 max res :(  I can't find any way to increase it.  The "Hardware Drivers" menu item doesn't do anything - I used to be able to install the nvidia proprietary driver.  Though the OOTB driver was working perfectly and giving me the native 1680x1050 screen res.

---

### Post by Gina on 2009-12-05
I installed the nvidia 185 driver and it's dependencies using synaptic.  When I rebooted I had the full resolution.  And the NVIDIA X Server Settings tool.  :)

---

### Post by Hiram on 2009-12-06
Don't forget that all the tutorials on how to configure your X server will be useless for new users since the don't know the creating the xorg.conf file is good enough.

There are thousands of tutorials like "add this line to device section in xorg.conf to enable feature X"

unfortunatly most of the are already obsolete but some still have value.

For those people who need powersavings options, xinerama modelines or other special tricks to make their hardware work normal, it would be nice to provide a skeleton xorg.conf or something similar

---

### Post by Gina on 2009-12-06
When I installed the nvidia driver (see above) it created the xorg.conf file containing it's info.

---

### Post by benjamonk on 2009-12-06
> **SunnyRabbiera said:**
> So you think, tell me then what happens when hardware detection fails and you are stuck at a low resolution of 720 x 400, you have no way to easily configure your monitor settings.
Gnome or KDE's monitor tool only gives you a max resolution of 800x600 when your real max resolution is 1600x1200...


I, like many others, have this exact same problem:

I have posted threads here

[http://ubuntuforums.org/showthread.php?t=1346500](http://ubuntuforums.org/showthread.php?t=1346500)

and here on launchpad

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/92704](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/92704)

but noone has been able to offer me ANY advice.

Can anybody please help me? I don't want to go back to windows but at this rate I will just have to.

---

### Post by Gina on 2009-12-06
Just stick to earlier versions of Ubuntu that work alright for your main work.  This is development testing and you must expect problems.  No doubt it'll be fixed in due course.

---

### Post by lswb on 2009-12-06
> **RAOF said:**
> 
By running "jockey-text" from the console and installing the nvidia binary drivers, which will write out an xorg.conf setting 'nvidia' as the driver?  


Like that's really obvious to a newbie.

---

### Post by Gina on 2009-12-06
I didn't know that one and I've been with Ubuntu since 5.04 and on and off with other Linux distros before that.

---

### Post by RAOF on 2009-12-06
> **lswb said:**
> Like that's really obvious to a newbie.

He said that neither nv nor nouveau worked for his card (pre-Lucid).  That means that the LiveCD won't boot, so we've already lost the newbie.

---

### Post by lswb on 2009-12-06
> **RAOF said:**
> He said that neither nv nor nouveau worked for his card (pre-Lucid).  That means that the LiveCD won't boot, so we've already lost the newbie.

Not really, see post #12

---

### Post by ranch hand on 2009-12-06
Oh I think we have lost the noob here.  I know that if the first CD I tried came up with that kind of resolution I would be using Mandriva, RPMs included, right now.  Or maybe PCLOS-gnome.

There is no way I would have installed the sucker.

I am glad Hardy did not do that because I really do not like RPMs.

---

### Post by collinp on 2009-12-06
I have never really had problems with X.

Although a configuration utility would be nice, a more permanent solution would be to improve Xorg's dynamic hardware detection and configuration (which is how you can live without an xorg.conf file) so we don't have to deal with xorg.conf files at all.

---

### Post by Gina on 2009-12-07
> **Hellow said:**
> I have never really had problems with X.

Although a configuration utility would be nice, a more permanent solution would be to improve Xorg's dynamic hardware detection and configuration (which is how you can live without an xorg.conf file) so we don't have to deal with xorg.conf files at all.I have had problems with X and still get them at times.  To be sure all graphics cards are going to be detected correctly and fully covered would be impossible IMO.  New cards are being developed all the time.  So I really think a "manual override" is needed for special cases.

And I might add that I dumped MS Windows because I felt I didn't have the user control!!  I'm sure many others will think the same.

---

### Post by jbernardo on 2009-12-07
> **Gina said:**
> I have had problems with X and still get them at times.  To be sure all graphics cards are going to be detected correctly and fully covered would be impossible IMO.  New cards are being developed all the time.  So I really think a "manual override" is needed for special cases.

And I might add that I dumped MS Windows because I felt I didn't have the user control!!  I'm sure many others will think the same.

Couldn't have said it better. Also, add to those situations that you simply can't automate the people that use XBMC and have a LCD TV connected via HDMI. Most LCD TVs lie, so you have to add modelines to xorg.conf to be able to run them at 1920x1080@60Hz, @50Hz and @24Hz. DDC isn't reliable at all on these cases. I really don't believe that Xorg will ever be able to automate all these situations.

And one of the reasons I dumped MSFT OSs was precisely the removal of control from the users.

---

### Post by RAOF on 2009-12-07
> **jbernardo said:**
> Couldn't have said it better. Also, add to those situations that you simply can't automate the people that use XBMC and have a LCD TV connected via HDMI. Most LCD TVs lie, so you have to add modelines to xorg.conf to be able to run them at 1920x1080@60Hz, @50Hz and @24Hz. DDC isn't reliable at all on these cases. I really don't believe that Xorg will ever be able to automate all these situations.
...

As I mentioned before, this could be happily accommodated by a relatively simple extension to System->Preferences->Display, a place that's much more discoverable than xorg.conf or its editors.

---

### Post by Gina on 2009-12-08
> **RAOF said:**
> As I mentioned before, this could be happily accommodated by a relatively simple extension to System->Preferences->Display, a place that's much more discoverable than xorg.conf or its editors.Yes, that's what we need :)  I hope it will be implemented before long.

---

### Post by jbernardo on 2009-12-08
> **RAOF said:**
> As I mentioned before, this could be happily accommodated by a relatively simple extension to System->Preferences->Display, a place that's much more discoverable than xorg.conf or its editors.

And which will force users to install gnome or kde - my XBMC machine doesn't have either, and doesn't need them. Why force everyone to use a DE when there is no need for one? You can add that extension for the DE users, but a skeleton xorg would make a lot more sense for those that don't need one of the two big DEs. And I am assuming that that kind of applet would show at the same time with the same functionalites on both DEs...

Please, don't complicate stuff for advanced users just to make things easier for newbies.

---

### Post by buzzmandt on 2009-12-08
> **jbernardo said:**
> And which will force users to install gnome or kde - my XBMC machine doesn't have either, and doesn't need them. Why force everyone to use a DE when there is no need for one? You can add that extension for the DE users, but a skeleton xorg would make a lot more sense for those that don't need one of the two big DEs. And I am assuming that that kind of applet would show at the same time with the same functionalites on both DEs...

Please, don't complicate stuff for advanced users just to make things easier for newbies.

This is flawed philosophy. You should not want to make it more diffcult for new users just to accomodate the status quo of advanced users. Most new users will be using either KDE or GNOME. The advanced users that don't use a DE are advanced enough to edit their own xorg. The new users want to be able to point and click. The advanced users are the ones that can get under the hood.

The display properties is the way to go. I have geforce 5500 and restricted hardware did not recognize it. I tried installing from nvidia website, but it wouldn't work. I have installed this driver a thousand times, I am not a newb. It would not install properly. NV driver is the only thing that works and display properties would only give max of 800x600. I had to edit xorg in order to gain higher resolution. A new user should not have to do this, an advanced user can do it easily enough. I would be very happy with a point and click solution.

---

### Post by jbernardo on 2009-12-08
> **buzzmandt said:**
> This is flawed philosophy. You should not want to make it more diffcult for new users just to accomodate the status quo of advanced users. Most new users will be using either KDE or GNOME. The advanced users that don't use a DE are advanced enough to edit their own xorg. The new users want to be able to point and click. The advanced users are the ones that can get under the hood.

The display properties is the way to go. I have geforce 5500 and restricted hardware did not recognize it. I tried installing from nvidia website, but it wouldn't work. I have installed this driver a thousand times, I am not a newb. It would not install properly. NV driver is the only thing that works and display properties would only give max of 800x600. I had to edit xorg in order to gain higher resolution. A new user should not have to do this, an advanced user can do it easily enough. I would be very happy with a point and click solution.

Flawed? Flawed is removing existing options that are useful for advanced users (like having a easy way to generate a editable xorg.conf skeleton) just because you added a point and click option for the newbies. I'm not saying to not add something for the unskilled crowd. I'm asking to not remove options from the advanced users. In what is that flawed? Is (k)ubuntu supposed to be a newbies only distro, becoming more and more hard to use for advanced users while doling out a windows like pap for the less demanding ones, forcing one to go through one thousand clicks to do something that would be easy to do uncommenting a line from a text file?

---

### Post by nanog on 2009-12-08
> As I mentioned before, this could be happily accommodated by a relatively simple extension to System->Preferences->Display, a place that's much more discoverable than xorg.conf or its editors.

Sigh. I remember having that conversation several development cycles ago. 

We need a simple python gui for this:

```
 xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
```

Its ridiculous to require a newbie to RTFxrandrM.

---

### Post by RAOF on 2009-12-08
> **nanog said:**
> Sigh. I remember having that conversation several development cycles ago. 

We need a simple python gui for this:

```
 xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
```

Its ridiculous to require a newbie to RTFxrandrM.

Indeed; that's (almost) exactly it.  Add a little bit of gnome-settings-daemon integration, and a button to apply it system wide for the gdm screen, and you're almost all there.

I'm not sure if it was several dev cycles ago; I seem to remember it in Karmic, though.  It really does just need someone to write the code.

For those people wanting an xorg.conf editor, how does **xorg-options-editor-gtk** work for you?

---

### Post by lswb on 2009-12-08
> **nanog said:**
> 
...
We need a simple python gui for this:

```
 xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
```


There are already several gui front ends in the repos for this: arandr, gnome-randr-applet, grandr, lxrandr, perhaps others. I like the name grandr best but they all suffer from the common FOSS affliction of having names with no apparent reference to their purpose. Maybe one or more of them is good enough to be included in a default install?

Of course if X won't run at all, a cli solution is still needed.

---

### Post by phenest on 2009-12-09
> **jbernardo said:**
> Flawed?

Yep! Why do you want a command line option for this if you're not running a DE?

I wish I had a problem with my graphics so I could sympathise here, but I have discovered I can happily run the nv driver at full res (1920x1200), without a xorg.conf file at all. In fact, with the nvidia driver, the only thing in my xorg.conf file is that the nvidia driver is specified. There are no other options in it.

---

### Post by jbernardo on 2009-12-09
> **phenest said:**
> Yep! Why do you want a command line option for this if you're not running a DE?

Do I really need to comment after this observation?
1 - If I'm not running one of the two top DEs, I do need a way to generate a xorg.conf I can edit, or a DE independent utility to configure it (preferably one that doesn't drag a few thousand libs with it).
2 - If xorg won't start, I can't use some GUI based utility to generate a editable xorg.conf.
3 - If I'm using XBMC or other frontend on a set top box or similar, the only way to tune xorg might well be editing xorg.conf over a ssh connection. A xorg.conf skeleton, like the one that was generated by "dpkg-reconfigure xserver-xorg" would help a lot. A GUI tool? No use for it.

Well, maybe it is time for me to grow out of (k)ubuntu.

---

### Post by phenest on 2009-12-09
> **jbernardo said:**
> Do I really need to comment after this observation?
1 - If I'm not running one of the two top DEs, I do need a way to generate a xorg.conf I can edit, or a DE independent utility to configure it (preferably one that doesn't drag a few thousand libs with it).
2 - If xorg won't start, I can't use some GUI based utility to generate a editable xorg.conf.
3 - If I'm using XBMC or other frontend on a set top box or similar, the only way to tune xorg might well be editing xorg.conf over a ssh connection. A xorg.conf skeleton, like the one that was generated by "dpkg-reconfigure xserver-xorg" would help a lot. A GUI tool? No use for it.

Well, maybe it is time for me to grow out of (k)ubuntu.

Ah, so you meant if X has failed?

To respond to point 3: what about "Xorg --configure"?

---

### Post by KJ55 on 2009-12-10
> **psyke83 said:**
> RAOF, whiprush & others,

While I completely agree that Xorg needs to be fixed so that it never breaks, would it be possible to re-enable the script that generates a blank xorg.conf template as it did on Jaunty?

I'm not asking for Lucid to ship with a configuration file by default, just for a convenient* way to generate a configuration file to streamline the process of troubleshooting server/driver settings. I believe this will also help your cause in getting users to report driver quirks.

*Since Karmic, we need to do the following:
[LIST]
[*]Stop any running Xorg/display manager processes;
[*]Invoke "sudo Xorg -configure";
[*]Move the xorg.conf.new file in the working directory to /etc/X11/xorg.conf.
[/LIST]

Prior to Karmic, all we needed to was to invoke "sudo dpkg-reconfigure xserver-xorg".

Many Thanks psyke83!

In desperation, I used "Xorg -configure" command in recovery mode after dropping to the root command line (console), and this xorg configuration tool worked in **Ubuntu 8.04.3**.  

"Xorg -configure" created a "xorg.conf.new" file in the /root directory with all the settings (specific graphics driver and monitor, etc).  After successfully testing the x server using this xorg.conf.new file by following the supplied command on the monitor, I copied and renamed it as xorg.conf to the /etc/X11 directory.  Restarted Ubuntu, and my desktop was back.

BTW, the "dpkg-reconfigure xserver-xorg" command in Ubuntu 8.04.3 now "only" configures the keyboard and mouse in the xorg.conf, and NOT the graphics card and monitor.   

Also, the "fix X server" in recovery mode on Ubuntu 8.04.3 could not successfully configured and setup the x server for my replacement graphic card on my existing Ubuntu 8.04.3 installation.


So, for Ubuntu 8.04.3, if "fix X server" in recovery mode doesn't work try using the "Xorg -configure" command to setup the x server.  (IMO, it replaces the now useless "dpkg-reconfigure xserver-xorg" command).  

It would be more newbie user friendly if the "Xorg -configure" command just created a file named xorg.conf in the /etc/X11 directory, but I'm not complaining.  It recovered my x server desktop.:D

---

### Post by phenest on 2009-12-10
> **KJ55 said:**
> "Xorg -configure" created a "xorg.conf.new" file in the /root directory with all the settings (specific graphics driver and monitor, etc).

It would be more newbie user friendly if the "Xorg -configure" command just created a file named xorg.conf in the /etc/X11 directory, but I'm not complaining.  It recovered my x server desktop.:D

Xorg --configure creates a xorg.conf.new file in whatever directory you happen to be in at the time. I couldn't find any options that could change this. Try Xorg --help for all options, which incidentally gives this error under Jaunty:
```
Fatal server error:
Unrecognized option: --help

```

---

### Post by seeker5528 on 2009-12-10
> **RAOF said:**
> As I mentioned before, this could be happily accommodated by a relatively simple extension to System->Preferences->Display, a place that's much more discoverable than xorg.conf or its editors.

Generally speaking the stuff you need to edit xorg.conf to accomplish, should not be part of the display preferences.

For the extreme situations there should be options on the safe boot menu to, if nothing else, at least get you working good enough to get to your desktop so you can get on line and get more help.

I'm not opposed to having a seperate utility that would make modifications to the xorg.conf as an alternative to try before creating/editing the xorg.conf by hand.

The stuff that can be accomplished using xrandr should not be done in xorg.conf, they should be handled using the display preferences or other desktop/window manager specific mechanism or by a desktop independent utility that can be included in the start up of the users chosen environment, using whatever mechanism the users chosen environment provides, so the options get applied in a user specific way after log in.

Later, Seeker

---

### Post by lswb on 2009-12-10
> **phenest said:**
> 
...Try Xorg --help for all options, which incidentally gives this error under Jaunty:
```
Fatal server error:
Unrecognized option: --help

```
Only because Xorg doesn't use -- for its options, try Xorg -help

---

### Post by reub2000 on 2009-12-10
Well on my dual-head setup, all versions of Ubuntu simply clone the display. What's worse, is that it uses a 60Hz refresh rate and one of my monitors is a CRT. Fedora 12 recognizes and configures everything beautifully on my setup.

---

