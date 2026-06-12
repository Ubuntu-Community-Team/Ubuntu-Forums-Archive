---
title: "Kinda' freakin' out: Dapper crashed after formatting"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Steve S. on 2006-06-05
I wanted a clean install from Hoary to dapper, so saved my data to a second drive and put in the Dapper cd.

Everything went great until it got to a certain point (after it formatted the drive) and said dapper crashed, report to moderator, or whatever.

So, I'm running on the live cd right now.  Obviously I have an internet conection.  It is an i386 on an AMD Athlon.

What is the quickest, most efficient way to get my system up and running using the internet to get dapper going on my system?!

---

### Post by mscman on 2006-06-05
Well if you're simply looking for a clean install, I would say your best bet would be to start over again.  I'm not sure how much work it would take to try and salvage your current install.  It may cost you more time in the long run.

---

### Post by Steve S. on 2006-06-05
I just tried again using the same cd.

Got this message:
```
Error while running 'modprobe -v amd76xrom'
```

and then:
```
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code None; see /var/log/installer/syslog and /var/log/syslog
```

I have no problem starting over again. The question is, can I start over again using the internet via this live cd that I have in there now?  If so, how do I do that?

---

### Post by Steve S. on 2006-06-06
Tried it from a different source on a newly burned disk: same result.

Is there a way around this?  Can I still run dapper?  Or do I have to set up breezy?

---

### Post by Patsoe on 2006-06-06
If I understand correctly, you're running the LiveCD but are not using that to install? If you have no "special requirements" you can just install from the LiveCD, keeping the internet connection open for asking help while you're at it.

The fact that the LiveCD runs properly, suggests that you can indeed install Dapper. However I have no idea what the error messages mean - I would guess that amd76xrom is a module that is needed for AMD761/2 chipsets - do you have a motherboard like that? (most people have nVidia, ATi or VIA chipsets...)

---

### Post by Steve S. on 2006-06-06
Incorrect.  This came from using the livecd, it booted up great (looks really cool too!).  I could get internet with my wireless and everything...but, when I went to install, it did about 91% of it, well after formatting the drive, and it stopped in it's tracks, giving that error message that I mentioned before.  Livecd continued to run, but it wouldn't install.  I'll have to check on spec's for the motherboard...don't remember off the top of my head.

I'm thinking of putting breezy on there and just trying to upgrade (assuming breezy works!).  Anyone have the link to the breezy iso?

Unless, of course, we can deal with this error message directly.  Any ideas anyone.

---

### Post by rcarring on 2006-06-06
May I suggest you try with the alternate Dapper install cd?

This requires less ram and you have more control over the installation process.

---

### Post by Steve S. on 2006-06-06
[QUOTE=rcarring]May I suggest you try with the alternate Dapper install cd?

This requires less ram and you have more control over the installation process.[/QUOTE]

Sounds like a good suggestion.  Where might I locate such an installation cd?  Downloadable iso I suppose?

---

### Post by rcarring on 2006-06-06
I'll give you the link:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

This is on the cdimage site. I am hoping that someone may be able to point you to the official release alternate cd, but hopefully it will be the same as this one.

---

### Post by Steve S. on 2006-06-06
[QUOTE=rcarring]I'll give you the link:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

This is on the cdimage site. I am hoping that someone may be able to point you to the official release alternate cd, but hopefully it will be the same as this one.[/QUOTE]

Thanks, rcarring, I'll download it and give it a shot.  Hopefully this is the right one.

---

### Post by deweese on 2006-06-06
Use either a Breezy install disc and then upgrade or use the alternate install disc of Dapper.  Others including myself had crashes trying to install fom live cd Dapper.

---

### Post by Steve S. on 2006-06-06
[QUOTE=deweese]Use either a Breezy install disc and then upgrade or use the alternate install disc of Dapper.  Others including myself had crashes trying to install fom live cd Dapper.[/QUOTE]

Ahhh...the post I was looking for.

Ok, I've got both options ready...we'll try it again ASAP.

Thanks, everyone.

---

### Post by Steve S. on 2006-06-07
Well, tried dapper from the install (read:not live) cd and it failed on me, but I think that could have been the physical cd itself (I used an old cd-rw) so I used the Breezy cd.  It worked like a charm.

Then tried to upgrade and it told me everything was current, although it was still on breezy.  Then the update manager informed me that there was a more recent version, but that I should check the website for more information to download it.  Ok, knew that, but it didn't get me any step closer to having dapper.  Tried a couple of different routes (as I remember, changing "breezy" to "dapper" in the /etc/apt/sources.list file was part of it) but couldn't get it to upgrade.  Well, it would say it was, then wouldn't change anything, saying that everything was current, although everything was clearly still breezy.

So, tonight we are going to try using the cd upgrade alternative and see how that goes.

---

### Post by Patsoe on 2006-06-07
An exact description of upgrading can be found here: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Good luck :)

---

### Post by Steve S. on 2006-06-07
[QUOTE=Patsoe]An exact description of upgrading can be found here: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Good luck :)[/QUOTE]

Yep, that's what I did...or at least one option I tried (I checked the forum for the best format, then tried it).

But, like I said, haven't tried the upgrade via cd yet, so will try that next.  If you're keeping track, now I've tried the livecd, then non-livecd install, then breezy w/ upgrade via the internet, and tonight we'll try the breezy w/ upgrade via the alternative cd.

Ahhhh....Linux determination (it must work somehow!).:wink:

---

### Post by Steve S. on 2006-06-08
Ok, looks good, well, sort of.

I used the alternative Dapper and ran through the whole process.  Near the end, I wasn't watching it, but it made the little login-bongo sound.  I went over to check the screen, and it had nothing on it, no green light (flat screen monitor).  I went ahead and logged in anyway, and it sounded like it logged in fine, but I can't see it.

One of my Linux mentors, giving quick advise, said that my X wasn't confrigured properly, so hit CTRL+ALT+F1 and configure it.  He didn't have time to explain how to configure it from there.

Anyone have any advise on how to go about this?  The video card is an ATI Radeon, if that is of significance.  Also, I have other "regular" monitors, if switching to one of those while I fix this problem would help.

---

### Post by Steve S. on 2006-06-09
No one has figured out what the crap I've done?

I'll continue on in case someone in the future encounters the same oddities.

Ok, I tried it again last night, thinking it was because I had set my resolutions too high.  Did the install again (text install from the alternative disk) and apparently it is reading my flat-screen as a wide screen 'cause the only options it gave me for the screen resolutions were way outside of the max range for my monitor.  Same problem as last time...can't even fix it outside of the X screen 'cause all the words are outside of what I can see.

So, in the past with Hoary, I set up the install with a standard monitor and then just switched to the flat screen and it worked fine.  We'll try that tonight and see if it works.

Anyone with any comments on whether or not I am on the right track, please chime in.

---

### Post by Patsoe on 2006-06-09
So if you hit Ctrl+Alt+F1, you do have a useable resolution in text mode, right?

Then you can manually reconfigure the options for X by typing ```
sudo dpkg-reconfigure xserver-xorg
```

This will ask for your password again, then gets you into a menu that just asks questions (a lot) about your graphics/monitor. You should be able to select the right resolutions manually there.

When it's finished, just restart X by Ctrl+Alt+F7 then Ctrl+Alt+Backspace.

---

### Post by Steve S. on 2006-06-09
[QUOTE=Patsoe]So if you hit Ctrl+Alt+F1, you do have a useable resolution in text mode, right?

Then you can manually reconfigure the options for X by typing ```
sudo dpkg-reconfigure xserver-xorg
```

This will ask for your password again, then gets you into a menu that just asks questions (a lot) about your graphics/monitor. You should be able to select the right resolutions manually there.

When it's finished, just restart X by Ctrl+Alt+F7 then Ctrl+Alt+Backspace.[/QUOTE]

Thanks for the response, Patsoe.

I hit ctrl+alt+f1, and could see it until my typing gradually lead me off the screen to where I could only make out the top of the words that I was typing.  So, no, the resolution was a little off, but was at least on the screen somewhat.  But still couldn't see enough to do anything about it.  

However, this was the first time I re-installed.  Last night after re-installing and re-checking the screen resolutions I only noted that the monitor clicked off when X was activated.  I'll recheck again tonight to see if going to command can save me some work.  Thanks for the reminder.

But, if it's anything like the first time, then I won't be able to see what I'm typing; it will be just lower than what I can see on the screen.  So, we may have to start over with a different monitor and try from there.

---

### Post by Steve S. on 2006-06-09
Yeah, baby!  We are in!

Patsoe, your configuration worked perfectly!  Thank you much!

And Dapper looks great!

---

