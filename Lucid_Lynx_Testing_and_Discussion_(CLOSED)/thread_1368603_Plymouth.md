---
title: "Plymouth?"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-12-30
I'm trying to get Plymouth up-and-running on a Karmic install, but am getting no answers in the main forum--I'm guessing because no one in there's using it--so I thought this might be the best place to find some answers.

Basically, I installed Plymouth from the PPA for the Plymouth Devels and removed usplash. Now, there's only text and no graphical splash. I also have KMS on and running. I know through ps that /sbin/plymouthd is running and can run plymouth-set-default-theme without any errors.

Any ideas?

---

### Post by wilee-nilee on 2009-12-30
The only thing I noticed about the plymouth ppa is that the last build was 23 weeks ago.

---

### Post by Starks on 2009-12-31
The PPA mentioned is the worst approach possible and will never get you what you want.

---

### Post by moore.bryan on 2009-12-31
If the PPA isn't a good option, what is? I'm really interested in testing-out Plymouth, but Lucid is completely unstable on my system, so that's not really an option.

---

### Post by Jordanwb on 2009-12-31
I think plymouth is in the official repo (don't quote me on that) but I can't get it to work either. I had to add a kernel param. Something like "gfxpayload=1024x768@32" or something like that.

*Edit* I checked my third party repos, and the plymouth PPA is not listed. When my laptop starts I get a "failed to connect to plymouth", ureadahead terminated, and plymouth-log (something like that) terminated.

---

### Post by moore.bryan on 2009-12-31
You had to do more than just add "gfxpayload=true" to your grub2 file?

Oh, and Plymouth is only in the Lucid repos, not Karmic.

---

### Post by Jordanwb on 2009-12-31
> **moore.bryan said:**
> You had to do more than just add "gfxpayload=true" to your grub2 file?

Oh, and Plymouth is only in the Lucid repos, not Karmic.

I'm not sure. Plymouth works when I shut down, but not when I boot up (I did not add the gfxpayload param), it does change the console resolution though which looks nice.. Now xorg sometimes fails to detect my graphics card. :confused: This is why I didn't upgrade gdm, because the gdm shipped with 10.04 A1 worked.

*Edit*

One of the plymouth related errors is "mountall: Failed to connect to Plymouth"

---

### Post by ranch hand on 2009-12-31
If you have a search engine you can find the package on the Ubuntu site and download it and the dependencies.

Or you could enable the lucid repos for the purpose of downloading the bugger.

If it works or not on 9.10 will be an adventure for you.  I hope 9.10 works after you do this.

---

### Post by Jordanwb on 2009-12-31
Considering I'm in the "**Lucid Lynx** Testing and Discussion" forum I'm talking about 10.04. Perhaps that is what moore.bryan is talking about.

This thread was also posted about plymouth: [http://ubuntuforums.org/showthread.php?t=1357117](http://ubuntuforums.org/showthread.php?t=1357117)

---

### Post by moore.bryan on 2009-12-31
> **ranch hand said:**
> If you have a search engine you can find the package on the Ubuntu site and download it and the dependencies.

Or you could enable the lucid repos for the purpose of downloading the bugger.

If it works or not on 9.10 will be an adventure for you.  I hope 9.10 works after you do this.

> **Jordanwb said:**
> Considering I'm in the "**Lucid Lynx** Testing and Discussion" forum I'm talking about 10.04. Perhaps that is what moore.bryan is talking about.

This thread was also posted about plymouth: [http://ubuntuforums.org/showthread.php?t=1357117](http://ubuntuforums.org/showthread.php?t=1357117)

Ranch Hand: I was thinking of trying that... I'm not too afraid of breaking my install because it's relatively fresh anyway. I just can't use the Lucid Alpha because it is far too unstable on my netbook.

Jordanwb: As in my original post, I was trying the developmental threads because I was getting very little input in the general threads. I figured that was because so few people are trying out Plymouth, perhaps because of the previously aforementioned PPA issues.

Thanks for everyone's help... I'm going to try and install via Synaptic with the Lucid repos temporarily enabled and I'll post back.

---

### Post by moore.bryan on 2009-12-31
Okay... some change, but I'm not too sure if its progressive or regressive.

Here's my setup: Asus EeePC-1005HA, running Ubuntu Netbook Remix 9.10, kernel 2.6.33-020633rc2-generic, GDM 2.29.1-0ubuntu9, Plymouth 0.8.0~6.

Now, instead of the "routine" boot message about not being able to find a splash image, there are a number of messages about udev being replaced later. I can't see all the messages because (a) they scroll too quickly and (b) there are no such messages in any of my /var/log files. I know from previous experience the latter is a known bug developers seem uninterested in fixing; i.e., boot messages are not logged any where.

So, is this progress or regress?

---

### Post by Jordanwb on 2009-12-31
The udev messages are related to a rule created by hplip. The "problem" occurs in /lib/udev/rules.d/56-hpmud_support.rules:

```
# HPLIP udev rules file. Notify console user if plugin support is required for $

ACTION!="add", GOTO="hpmud_rules_end"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="pid_test"
SUBSYSTEM!="usb_device", GOTO="hpmud_rules_end"

LABEL="pid_test"

# Check for LaserJet products (0x03f0xx17).
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="??17", ENV{hp_model}="$sysfs{product}", ENV{hp_test}="yes"

ENV{hp_test}=="yes", RUN+="bin/sh -c '/usr/bin/hp-mkuri -c &'"

LABEL="hpmud_rules_end"

```

Where it says "SYSFS" or "sysfs", replace it with "ATTRS". This reminds me, I have to fix my udev rule for my Creative ZEN.

*Edit* If you don't have any HP printers, you can uninstall the hplip package.

---

### Post by moore.bryan on 2009-12-31
Thanks... I'll change, reboot, and post back.

Well, some more interesting movement forward... on shutdown, I had a Plymouth screen with the Ubuntu logo. On startup, just a lot of text, including the udev stuff still.

---

### Post by Jordanwb on 2009-12-31
If you boot into recovery mode you may be able to see the udev problems.

---

### Post by moore.bryan on 2009-12-31
Okay... I got rid of the other udev errors; they were related to a different file, but the same basic principal as the one above.

I am now *convinced* the Plymouth issue Jordanwb and I are experiencing is related to a resolution problem, since we both get the proper shutdown screen. I've tried every gfxpayload setting in grub to no avail. Also, hwinfo --framebuffer only gives me 800x600 and 640x400 choices, even though the display runs at 1024x600x32@60. I've tried setting that in the grub config file; nothing. I've also tried *every* setting hwinfo gives me; also nothing.

Argh.

---

### Post by moore.bryan on 2009-12-31
The more I read around the Internet, the more I'm convinced about the framebuffer/resolution issue. For example, as per [this]("https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience") document,
> We will use an Upstart job to manage Plymouth, and it will be started once the kernel DRM or framebuffer driver is added to the system and stopped when the display manager is started, or the boot sequence otherwise completes.
Since "sudo hwinfo --framebuffer" **does not** list the 1005HA's default 1024x600x32@60 resolution, I'm guessing the default resolution is set well after boot, possibly by X. If that's the case, I'm not sure how to get the appropriate resolution set by grub2... if that's even possible.

---

### Post by Jordanwb on 2009-12-31
I tried adding "gfxpayload=1024x768x24@60" and "gfxpayload=1280x800x24@60" and neither worked. It worked before, sortof.

---

### Post by Rallg on 2010-01-02
On my Asus EEE 1005HA, Lucid takes awhile to boot. Apparently it is looking for Plymouth (I see a message on the black and white screen), then it eventually goes about its business and continues boot without difficulty. I've been updating via Terminal (sudo aptitude update && sudo aptitude safe-upgrade).

After reading through the above thread, it seems like this is not a big deal. Synaptic does not show Plymouth, whatever it is. The only nuisance factor, AFAIK, is the delayed boot.

---

### Post by moore.bryan on 2010-01-02
Rallg: I find your situation very strange because, AFAIK, Lucid is *supposed* to have Plymouth installed *by default* as the boot-up manager (for lack of a better term). Plymouth is in the Lucid repos; perhaps you should install it?

---

### Post by scradock on 2010-01-02
The "active" version of the hpmud_support.rules file is the one in /etc/udev/rules.d, rather than the one in /lib

HTH anyone else trying to get rid of the annoying but obviously not fatal error message.

---

### Post by Rallg on 2010-01-02
Sorry, when I wrote that Plymouth was not listed via my Synaptic, I was on my karmic partition. Now I've switched to lucid.

My lucid had libplymouth2 installed, but not Plymouth. During boot, there was a message "unable to connect to plymouth" on the black and white screen before the lucid login animation appeared. But after the short delay, boot proceeded normally, it seems.

I installed Plymouth via Synaptic (along with some other support file), and on reboot the black and white screen disliked it even more than before (that is, a longer error message). But it still booted. I rebooted again, same message. So I remove Plymouth and went back to the shorter error.

I don't see any problem with the system. Mind you, I have not exercised it thoroughly. Originally I installed the released desktop version of karmic (not the remix) on this partition, then migrated to lucid via upgrade. Since then I've been using aptitude safe-upgrade, not the update manager. About 10 x-org-server related packages have been held back. Again, this is Asus EEE HA1005HA.

---

### Post by plun on 2010-01-02
If you have time.....

File a bug or investigate the mountall package

[http://packages.ubuntu.com/lucid/mountall](http://packages.ubuntu.com/lucid/mountall)

mountall breaks plymouth for the moment.  

```
apt-cache showpkg mountall

apt-cache showpkg plymouth
```

Basic about Plymouth:
[http://www.freedesktop.org/wiki/Software/Plymouth](http://www.freedesktop.org/wiki/Software/Plymouth)

..

---

### Post by digv on 2010-01-02
For me the problem was the --attach-to-session switch that plymouthd is started with. I filed [bugreport, 502494]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/502494") that shows what I did to get plymouth working.

---

### Post by plun on 2010-01-03
> **digv said:**
> For me the problem was the --attach-to-session switch that plymouthd is started with. I filed [bugreport, 502494]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/502494") that shows what I did to get plymouth working.

Ok... nice finding !

For me it just fixes the error "Mountall, could not connect to Plymouth", no plymouth starts.

Running on my laptop, ATI-graphics-open source driver.

I did a sudo dpkg-reconfigure linux-image-`uname -r` after changing the file.

Confirmed the bug anyway !

---

### Post by moore.bryan on 2010-01-03
> **plun said:**
> File a bug...
I've already added my info to one of the *many* bugs on Launchpad about this... I was hoping things would move a little faster on this since Plymouth will be completely replacing Usplash & Xsplash *soon*.

> **plun said:**
> ... or investigate the mountall package
This might seem like a silly question, but what would *mountall* have anything to do with *Plymouth*? I've seen the other threads discussing a mountall error when trying to load Plymouth, but I don't get that.

> **plun said:**
> Basic about Plymouth:
[http://www.freedesktop.org/wiki/Software/Plymouth](http://www.freedesktop.org/wiki/Software/Plymouth)
Thankfully, this was one of the first pages I checked and am on the mailing list; alas, no responses at all. :-(

> **digv said:**
> For me the problem was the --attach-to-session switch that plymouthd is started with. I filed [bugreport, 502494]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/502494") that shows what I did to get plymouth working.
Hmm... very interesting suggestion, digv; I wonder why that would have anything to do with it. Just for ha-ha's, I did as your post suggested, but no love.

I *was* finally able to catch one of the error messages I've been seeing at boot:
> init: plymouth-log main process (753) terminated with status 111
This seems minor, but I thought I'd put it out there.

Thanks for all the suggestions, so far.

---

### Post by plun on 2010-01-03
> **moore.bryan said:**
> 
This might seem like a silly question, but what would *mountall* have anything to do with *Plymouth*? I've seen the other threads discussing a mountall error when trying to load Plymouth, but I don't get that.



Perhaps a good start is to open this URL and check dependencies....

[http://packages.ubuntu.com/lucid/mountall](http://packages.ubuntu.com/lucid/mountall)

As you can see there is a dependency with libplymouth.

Mountall is also a pure Ubuntu package and probably "WIP" by Scott James Remnant...

Maybe there are more challengies with upstart and initramfs...:confused:

---

### Post by moore.bryan on 2010-01-03
plun: as soon as I saw your post, I realized I spoke--er, wrote--too soon. In all my research, I read a lot about how Plymouth does so much more than just a pretty splash... I should have realized it's connection with something like mountall; however, like I wrote, I don't have mountall installed and I receive no errors about it. Do you think installing it--although it will break Plymouth--would be progressive?

You can count me in as confused, as well.

---

### Post by plun on 2010-01-03
> **moore.bryan said:**
> plun: as soon as I saw your post, I realized I spoke--er, wrote--too soon. In all my research, I read a lot about how Plymouth does so much more than just a pretty splash... I should have realized it's connection with something like mountall; however, like I wrote, I don't have mountall installed and I receive no errors about it. Do you think installing it--although it will break Plymouth--would be progressive?

You can count me in as confused, as well.

Well.... there are a bunch of packages involved.

```
plun@plun-laptop:~/android/tools$ apt-cache showpkg mountallPackage: mountall
Versions: 
2.3 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages
                  MD5: b5b5a27fc0e8063ef1226a39fb8ecf70


Reverse Depends: 
  upstart,mountall
  initramfs-tools,mountall 2.0~
Dependencies: 
2.3 - makedev (0 (null)) libc6 (2 2.9) libdbus-1-3 (2 1.2.16) libnih-dbus1 (2 1.0.0) libnih1 (2 1.0.0) libplymouth2 (2 0.8.0~-6) libudev0 (2 147) policycoreutils (3 2.0.69-2ubuntu4) usplash (3 0.5.47) upstart (3 0.6.3-2) 
Provides: 
2.3 - 
Reverse Provides: 

```

As I wrote this is "Work in progress"..... but maybe someone can nail the bugger....;-)

---

### Post by moore.bryan on 2010-01-03
Never mind... I lied; I *do* have mountall installed, but from the Karmic repos (version 1.0), so I'm upgrading now and will let all know how badly I break my system.
;-)

Alright, now I'm *really* confused. Installing mountall (2.3) from the Lucid repos broke *absolutely nothing*. In fact, I didn't even receive any mountall error messages. Huh?

---

### Post by zika on 2010-01-03
In the context of messages generated in boot process, does anybody get **/etc/update-motd.d/91-release-upgrade exited with return code 1**...?

---

### Post by MacUntu on 2010-01-03
Well, mountall cannot connect to Plymouth, because Plymouth isn't running. Doesn't sound like a mountall problem to me. Removing the '--attach-to-session' part like described in the bug report didn't make the warning go away for me (Nouveau via git: kernel, libdrm, driver).

---

### Post by plun on 2010-01-03
It works with Lucids kernel, discussed within the bug report.

---

### Post by digv on 2010-01-03
The issues could be different with different chipsets.  I have an Asus 1005HA with Intel graphics.

I added some info on how I did the troubleshooting to the bug-report.

---

### Post by ranch hand on 2010-01-03
> **digv said:**
> The issues could be different with different chipsets.  I have an Asus 1005HA with Intel graphics.

I added some info on how I did the troubleshooting to the bug-report.
There are a lot of folks here from 9.10-testing when this rush for speed really got underway.  We certainly had a lot of different problems on different hardware then.  No reason for it to be any different now.

At least most of us can boot in.

I will be looking at your bug report some more and check on your trouble shooting.  Thanks for letting us know you added to it.  I am pretty new and trouble shooting is a definate weakness.

---

### Post by Jordanwb on 2010-01-04
> **scradock said:**
> The "active" version of the hpmud_support.rules file is the one in /etc/udev/rules.d, rather than the one in /lib

HTH anyone else trying to get rid of the annoying but obviously not fatal error message.

I checked /etc/udev/rules.d/ first but the file was not there. After a few reboots I was able to get the path and it was in /lib/whatever. I changed the file I had referred to and the "error" went away. It even worked for the guy who started this thread. [IMG]http://img705.imageshack.us/img705/2889/emotcolbert.gif[/IMG]

> **plun said:**
> mountall breaks plymouth for the moment.

I see.

> **zika said:**
> In the context of messages generated in boot process, does anybody get **/etc/update-motd.d/91-release-upgrade exited with return code 1**...?

I think I saw that. Odd since I did a fresh install.

---

### Post by moore.bryan on 2010-01-05
Some interesting developments:

When I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/502583"), I was told by one of the developers there isn't *supposed* to be a Plymouth splash screen because it hasn't been implemented yet.

Interesting.

---

### Post by Jordanwb on 2010-01-05
> **moore.bryan said:**
> Some interesting developments:

When I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/502583"), I was told by one of the developers there isn't *supposed* to be a Plymouth splash screen because it hasn't been implemented yet.

Interesting.

Then why is gdm blocked if plymouth is not installed? It's sortof like getting a wagon if you don't even have a horse.

---

### Post by moore.bryan on 2010-01-05
> **Jordanwb said:**
> Then why is gdm blocked if plymouth is not installed? It's sortof like getting a wagon if you don't even have a horse.
What do you mean "gdm [is] blocked?"

---

### Post by Jordanwb on 2010-01-05
I was wrong in my previous post, the existence of usplash on the system blocked the upgrade of gdm.

---

### Post by ranch hand on 2010-01-05
Yes, why do you say that?  I still get a login screen.  The stuff that came before that is xsplash.

---

### Post by Jordanwb on 2010-01-05
> **ranch hand said:**
> Yes, why do you say that?

Uh... :confused:

> **ranch hand said:**
> I still get a login screen.

I have autologin enabled.

> **ranch hand said:**
> The stuff that came before that is xsplash.

AFAIK xsplash was never installed with 10.04 A1.

---

### Post by ranch hand on 2010-01-05
Yes xsplash was installed.  The gdm depends on its image file for its image.  Xsplash is what gives you the lovely chocolate induced diarhia colored screen before you get you desktop (I think you get that with auto login but I am not sure).

I know auto login is popular but even if I used it on my stable releases  I wouldn't on a pre-release version.  I want the option of gnome-failsafe and xterm for these buggers.

---

### Post by Jordanwb on 2010-01-05
> **ranch hand said:**
> Yes xsplash was installed.  The gdm depends on its image file for its image.

Odd, I don't recall removing xsplash or ever seeing it when A1 first booted. Oh well.

> **ranch hand said:**
> Xsplash is what gives you the lovely chocolate induced diarhia colored screen before you get you desktop (I think you get that with auto login but I am not sure).

:-&

> **ranch hand said:**
> I know auto login is popular but even if I used it on my stable releases I wouldn't on a pre-release version. I want the option of gnome-failsafe and xterm for these buggers.

So far the only problem I've encountered is that a fsck causes gdm to terminate.

---

### Post by ranch hand on 2010-01-05
Hmm, every time fsck runs on mine it kicks me into "low graphics" and then the login comes up (usually).  At that point if I use the option to "restart" from there it boots fine the next go around.

Plymouth turns off most of the stuff like xsplash and usplash (we still had that early on).  It is still there in the background.

---

### Post by Jordanwb on 2010-01-05
> **ranch hand said:**
> Hmm, every time fsck runs on mine it kicks me into "low graphics" and then the login comes up (usually).  At that point if I use the option to "restart" from there it boots fine the next go around.

Yes that's the same problem I have. A bug has already been filled.

---

### Post by zika on 2010-01-06
> **ranch hand said:**
> Hmm, every time fsck runs on mine it kicks me into "low graphics" and then the login comes up (usually).  At that point if I use the option to "restart" from there it boots fine the next go around.

Plymouth turns off most of the stuff like xsplash and usplash (we still had that early on).  It is still there in the background.You do not need to restart. Go to tty[1 2...] login and do```
sudo service gdm restart
```

---

### Post by ranch hand on 2010-01-06
> **zika said:**
> You do not need to restart. Go to tty[1 2...] login and do```
sudo service gdm restart
```
Now hold on here,  wouldn't this take more time than just hitting restart?

If it is not slower then I will have to admit that I have no idea how to do it anyway.  I have heard of folks doing this in several different distros of linux.  I have never been able t ofigure out how in flinderation you do this.

I understand that the tty level has to do with the user privileges that you have when logged in, but how you log in to these is beyond me.

---

### Post by zika on 2010-01-06
> **ranch hand said:**
> Now hold on here,  wouldn't this take more time than just hitting restart?

If it is not slower then I will have to admit that I have no idea how to do it anyway.  I have heard of folks doing this in several different distros of linux.  I have never been able t ofigure out how in flinderation you do this.

I understand that the tty level has to do with the user privileges that you have when logged in, but how you log in to these is beyond me.*_Ctrl-Alt-F1_* gets You in tty1. Login. Type **sudo service gdm restart**. You're in gdm. If You want to logout from tty1, *_Ctrl-Alt-F1_*. Type **exit**. To get into gdm *_Ctrl-Alt-F7_*. It works for me. Neither PC nor me likes reboot... To much memories of W$... I guess. Enyou!

---

### Post by ranch hand on 2010-01-06
You know I have never really gotten serious about finding how to do this but I have run a search or two when it has come up and have never found this information.  That is not to say it isn't out there, just that my searches did not turn it up easily.

Thank you very much, I will add this to my growing arsenal.

---

### Post by Jordanwb on 2010-01-06
> **zika said:**
> You do not need to restart. Go to tty[1 2...] login and do```
sudo service gdm restart
```

Sometimes it is very hard to do this because I can't even see the console output since it gets shoved off the screen. Also sometimes the console "flashes" which makes it harder.

---

### Post by uBeer on 2010-01-06
> **Jordanwb said:**
> Sometimes it is very hard to do this because I can't even see the console output since it gets shoved off the screen. Also sometimes the console "flashes" which makes it harder.

But no longer with help of kms! TTY switching is really fast, no flashes and native resolution :D

---

### Post by Jordanwb on 2010-01-06
> **uBeer said:**
> But no longer with help of kms! TTY switching is really fast, no flashes and native resolution :D

Yes it is very fast but when gdm terminates, it sometimes causes the screen to go crazy.

---

