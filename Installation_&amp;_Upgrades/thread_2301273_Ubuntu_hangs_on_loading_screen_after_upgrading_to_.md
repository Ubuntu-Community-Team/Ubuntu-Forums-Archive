---
title: "Ubuntu hangs on loading screen after upgrading to 15.10"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by alison3 on 2015-11-01
Okay so I upgraded from 14.10 to 15.10 today... no errors, no problems, nothing... so it told me i needed to restart complete the upgrade and so I did... but when ubuntu (Or lubuntu as it's what I use normally) loaded, it was stuck on the loading screen... the little dots all lit up but then nothing happened.   I thought maybe it just needed to clean up or something of the sort like silly ol Windows does after an update but nothing ever happened.  I waited about 20 minutes.  

So I restarted and pick an older kernel and that seems to work.  


I'm guessing i need to reinstall a graphic driver or something, I dunno.  I'm using the fglrx-updates driver.  I remember hearing that you should always uninstall the graphic drivers before upgrading but I didn't think about that this time.  Maybe that's the problem?

Here's the thing... I love Ubuntu and I love Linux but I probably shouldn't be using it cause I'm kind of an idiot when it comes to the solutions.    But if someone could give me some step by step instructions or ideas on how to possibly fix this I'd really appreciate it.  Thanks so much.

EDIT
Okay so I tried to uninstall fglrx-updates and rebooted and it worked just fine.  So I thought I needed to reinstall the drivers... so I did but now it just goes to a black screen.  The old kernels don't work, nothing does.  It'll go past the lubuntu loading screen sometimes, but then it just stops.  Even loading in graphic safe mode or whatever doesn't do any good.  ugh

---

### Post by howefield on 2015-11-01
You may be seeing this [bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888").

The updated driver is in the proposed repository (if it hasn't already made its way out) - you might try enabling the proposed repository, reloading your sources and then try additional drivers again.

If you enable the "proposed" repository you probably want to disable it once you have the driver.

---

### Post by alison3 on 2015-11-01
Thanks for replying but I'm sorry but how do I do any of this when it just loads a blank screen?


EDIT
To clarify, I'm running in Windows (and I hate it) right now because I have a duel boot. 

Lubuntu will go past the boot up screen, then it just flashes from black to more black (like my monitor is being turned on and off) and I don't know how to get into a terminal otherwise to fix this.  Everything I see says I need to be in the log in screen but I can't get that far.... IS there some way i can force it to not use the driver?

---

### Post by howefield on 2015-11-01
> **alison3 said:**
> Thanks for replying but I'm sorry but how do I do any of this when it just loads a blank screen?

You said you could boot to a previous kernel with good results ?

Do that and uninstall the proprietary driver.

Then load Software Sources and enable (tick) the option Pre-released updates (wily-proposed) from the Updates tab. Close and you will be prompted to update your software sources, do it.

The working driver should now be available via Additional Drivers.

---

### Post by howefield on 2015-11-01
Sorry, just noticed that you have Ubuntu in the thread title but lubuntu within the text of your post. What are you using ?

Not that it matters much, just the terminology might be very slightly different.

---

### Post by alison3 on 2015-11-01
> You said you could boot to a previous kernel with good results ?

Read the edit:

> EDIT
Okay so I tried to uninstall fglrx-updates and rebooted and it worked  just fine. ** So I thought I needed to reinstall the drivers... so I did  but now it just goes to a black screen.  The old kernels don't work,  nothing does.  It'll go past the lubuntu loading screen sometimes, but  then it just stops.  Even loading in graphic safe mode or whatever  doesn't do any good.  ugh**

also just went to the blank screen and tried to load a terminal with the keyboard, it didn't do anything, 

and Im using lubuntu but as you said, doesn't make much difference

---

### Post by alison3 on 2015-11-01
oh wow... I am so... i don't even know anymore

Windows decided i HAD to do some upgrade to it... so I did and then when it rebooted the internet wouldn't work... i can see my moden, it's running just fine.  So I was kinda freaking out but after rebooting like 3 times it worked and I made that message above.. then it stopped working again and using my phone the best solutions I found was to do a system restore... so that's what I did... when it rebooted, i forgot to select to go into Windows and sat here annoyed at myself as Linux booted, and as I was about to select 'reboot' it dawned on me that it's... like working now?...


I didn't do anything, why is it working now?  should I Just keep fglrx off or try reinstalling it?... I'm so confused now... but im going to bed it's 7 AM already...

---

### Post by lambdafox on 2015-11-01
When you restart your system, hold down the shift key.  This will bring up the boot menu, before loading the normal lxde desktop.

Choose advanced options, recovery mode,  drop to root shell prompt. Once there

```
mount -o rw,remount /
apt-get purge fglrx*
```

(You do not need sudo, because you are already root.)

This will let you boot with the open-source driver.

The proprietary drivers in the Ubuntu repositories have a bug(s?).  They do not work properly with the gcc compiler 5.0  --  the default on Wiley.

> [COLOR=#000000] I'm kind of an idiot when it comes to the solutions. But if someone could give me some step by step instructions or ideas on how to possibly fix this I'd really appreciate it[/COLOR]

Based on this comment, I strongly suggest you _***do not***_ enable the "proposed" repository.  Please learn from my mistakes on that one, lol!! :rolleyes:

Download either the 32-bit or 64-bit versions of the .deb files from these three package pages on ubuntuupdates.org:

1. [fglrx-updates-core]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-updates-core")
2. [fglrx-updates]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-updates")
3. [fglrx-amdcccle-updates]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-amdcccle-updates")

Now you need to install those 3 deb files. I use Xubuntu.  I just opened my file manager and right clicked, and installed using the Ubuntu Software Center application.  If PCManFM does not have a similar option, you may have to use dpkg.(Happy to help if you need further help here...)  If you use software center, it will complain the file is of bad quality.  This simply means that it has not been through the normal review / release process.

In either case, install them in the order listed above.

xvba-va-driver is not yet in the Wiley repository; so, you will need to download the deb you need for it from [here]("https://launchpad.net/ubuntu/wily/+package/xvba-va-driver"). Now install  this deb.

Next do this in your terminal:

```
sudo apt-get install libva-glx1 libva-egl1 vainfo
```

```
sudo amdconfig --adapter=all --initial
```
Reboot and Enjoy :D

> **howefield said:**
> ...Now edited to include corrections from howefield.  Thanks, howefield!

---

### Post by howefield on 2015-11-01
> **alison3 said:**
> ..also just went to the blank screen and tried to load a terminal with the keyboard, it didn't do anything,...

From the grub menu select "Advanced options for Ubuntu" then "Recovery Mode" then "Drop to a root shell prompt" If you don't get the grub menu at boot, pressing the shift key whilst booting should make it appear.

If as is likely, you find yourself in read only mode, use the following command..

```
mount -o rw,remount /
```

You can then run

```
apt-get purge fglrx*
```

to remove the non working driver, that should allow you to boot to a working desktop, and the choice is either stay with the open source driver till the updated proprietary driver makes it out of proposed or enable the proposed repository (remembering to disable the proposed repository after getting the driver installed). Downloading and installing the deb package files as described above is a third option but not one I'd endorse.

> **alison3 said:**
> I didn't do anything, why is it working now?  should I Just keep fglrx off or try reinstalling it?... I'm so confused now... but im going to bed it's 7 AM already...

Leave it unless you have an issue :)

---

### Post by alison3 on 2015-11-01
> **lambdafox said:**
> 

Next do this in your terminal:

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

```
sudo amdconfig --adapter=all --initial
```
Reboot and Enjoy :D

I ran into a problem here... i got this error message when doing this step:

```
Package xvba-va-driver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'xvba-va-driver' has no installation candidate

```

also by [COLOR=#000000] "proposed" repository do you mean I should do this?

[/COLOR]https://wiki.ubuntu.com/Testing/EnableProposed[COLOR=#000000]

Thanks for all the help everyone, at least i can see a screen now... honestly if I have to wait for fglrx to work for a little while, that's fine, it'd be nice to have it again but I'm not going to have a fit about it if this is as best as we can do.



> [/COLOR][COLOR=#000000]to remove the non working driver, that should allow you to boot to a working desktop, and the choice is either stay with the open source driver till the updated proprietary driver makes it out of proposed or enable the proposed repository (remembering to disable the proposed repository after getting the driver installed). Downloading and installing the deb package files as described above is a third option but not one I'd endorse.[/COLOR]
[COLOR=#000000]
so... if I don't do that, how do I know when fglrx is working properly to download?[/COLOR]

---

### Post by lambdafox on 2015-11-01
Glad you are making progress!  Howe is exactly right, the menu says "recovery mode" not advanced option now.  I will edit my previous post to correct that.  

> **alison3 said:**
> I ran into a problem here... i got this error message when doing this step:

```
Package xvba-va-driver is not available ...

```

And I apologize, I had the same problem but forgot to include it in my prior message.  [You can download the deb you need from here.]("https://launchpad.net/ubuntu/wily/+package/xvba-va-driver")


> **alison3 said:**
> also by [COLOR=#000000] "proposed" repository do you mean I should do this?  [/COLOR]ttps://wiki.ubuntu.com/Testing/EnableProposed ...[COLOR=#000000]

That is what was suggested earlier.  The procedure you are following replaces that option, and based on your comments is a better path for you.[/COLOR]
[COLOR=#000000]
[/COLOR]> **alison3 said:**
> [COLOR=#000000]Thanks for all the help everyone...[/COLOR]

So many have helped me, it is the least I can do, LOL

---

### Post by alison3 on 2015-11-01
Howe and [COLOR=#000000]lambdafox, thank you SO MUCH!


Everything is running smoothly now!  I tried your fix, Fox that you posted, and it's running now.  I'm so glad too because I was trying to hook my HDMI to my TV and it wouldn't work using the Xorg driver (no idea why) so I did as you posted and it's fine now... so... do I need to do anything?  Is it safe now?  Will it update as it needs to or do I need to add something?

I disabled wily-proposed updates as well, so hopefully that'll help out too.[/COLOR]

---

### Post by lambdafox on 2015-11-03
Now that it is working, you should be good to go.  The fglrx deb's you installed have the same version number as those in the proposed repository.  When they get moved over to the regular repo, your machine won't do anything because you already have these.  Higher versions, when they come, will replace the ones you have now.

I thought it might be helpful for me to expand on why enabling proposed is not the best idea for you.

That repository is where bug-fixes go for people to try out before they are released to the general public in the regular repositories.  When you enable it, any and every package in your system might get updated with an untested fix.  People who use it must be ready for frequent bugs / problems.  People with more linux & programming mojo than you or I have help debug those updates before they go into the regular repo.

---

