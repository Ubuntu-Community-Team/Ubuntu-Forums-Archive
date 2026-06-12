---
title: "Invisible mouse pointer after 13.04 upgrade"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by zlot on 2013-05-02
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote          [favorite]("http://askubuntu.com/questions/289631/xuost-13-04-mouse-pointer-invisible-after-upgrade#")            [/TD]
[TD="class: postcell"]               I just installed 13.04 and I couldn't help but notice that  the mouse pointer is invisible on the desktop. It appears in apps once I  manage to launch them with the invisible pointer. Help!  ps this is a VMWare VM, and I don't THINK that's relevant in this case,  but you never know....
  PPS I ***am*** able to see the pointer on "Xubuntu Session" and default(which looks to be "Xubuntu Session") [desktops]("http://askubuntu.com/questions/289631/xuost-13-04-mouse-pointer-invisible-after-upgrade#").  fortunately, I had a bunch of desktops installed. I'm still working on  this - I just upgraded - if I come up with a solution, I'll be sure to  post. Next, I will try a different login screen(Using gde,  presently....)

ppps  The other login screens don't matter, although this reminds me to mention the pointer is visible on all the login screens - gde, kde, or the kdlite, or whatever the last one is....
      
[/TD]
[/TR]
[/TABLE]

---

### Post by MAFoElffen on 2013-05-03
Reset your Unity profile... has been a problem that some things didn't get translated well using the 12.10 unity profile with 13.04...

Install the unity-tweak-tool
```

sudo apt-get install unity-tweak-tool

```
Then do a reset via:
```

unity-tweak-tool --reset-unity

```
That will reset the profile back to the default settings... but it will all be a 13.04 Unity default profile.

---

### Post by zlot on 2013-05-03
Terminal takes exception to the reset:
E: Command line option --reset-unity is not understood

I had hoped a reboot would accomplish a reset, but although your first line worked fine, I still have no mouse pointer after a reboot.
Thanks for the attempt, at any rate.
So I went to the Tweak Tool itself, changed the cursor, losing it entirely(invisible, stilll functional with a bit of imagination), then reset to default and returned to my original condition. I'm going to reboot in hopes that by doing something with the Tweak Tool, I'ver written a reset config file. If it works, I'll edit this post with the info, if not, then I'm pointless still.

---

### Post by MAFoElffen on 2013-05-03
Sorry, was doing multiple things at once... Cutting Marble; splitting rounds from a tree I cut up this morning, sharpening a chainsaw, working on my opensource project and answering posts. I corrected my last post... it should have been 
```

unity-tweak-tool --reset-unity

```

---

### Post by zlot on 2013-05-03
I tried that to no avail. Not only that, I managed to REALLY wreck the Ubuntu desktop. Now I have NOTHING, save for a doc file and 2 shortcuts! No notification bars - no NOTHING. I tried to remove and reinstall unity...and something went very wrong! I even managed to wreck the system default/Xubuntu session, but I seem to have that back, albeit slightly altered - nothing major. I'm going to try to find the commands for reinstalling Unity, and hopefully, the notification bar will return as well. I just hope I can pull that together!

---

### Post by zlot on 2013-05-03
Amazingly enough, the Ubuntu desktop is restored, but still without the mouse pointer....
I'm getting a bit spastic now - I did a couple of things, one of which was to move a config file. I think that might have done it.

---

### Post by MAFoElffen on 2013-05-04
I guess the best advice for the moment is "Remember to breath" and "Don't take things too seriously, your computer is not life and death" There is nothing there (system wise) that can't be recreated.

Unity right? Let me research if I can find what file in Unity has the mouse reference/mapping.

---

### Post by MAFoElffen on 2013-05-04
Okay--

Please post the results of:
```

cat /usr/share/icons/default/index.theme && sudo update-alternatives --display x-cursor-theme

```
Sort of it my output looks like this:
> 
mafoelffen@maferr-ubuntu-1:~$ cat /usr/share/icons/default/index.theme && sudo update-alternatives --display x-cursor-theme
[Icon Theme]
Inherits=DMZ-White
x-cursor-theme - auto mode
  link currently points to /usr/share/icons/DMZ-White/cursor.theme
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/DMZ-Black/cursor.theme - priority 30
/usr/share/icons/DMZ-White/cursor.theme - priority 90
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.


---

### Post by zlot on 2013-05-04
Thanks so much for your interest. this appears to be a fairly common problem as I search the annals of Google and Ubuntu!
Obsession can be fun!
And I might accidentally even learn something, although the best I can do right now is Google. Linux commands just don't want to stick in my head!
At any rate, my output is similar to your with a few extras....
[Icon Theme]
Inherits=DMZ-White
[sudo] password for frank: 
x-cursor-theme - auto mode
  link currently points to /usr/share/icons/DMZ-White/cursor.theme
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/oxy-black.theme - priority 40
/etc/X11/cursors/oxy-blue.theme - priority 40
/etc/X11/cursors/oxy-white.theme - priority 50
/etc/X11/cursors/oxy-yellow.theme - priority 40
/etc/X11/cursors/oxy-zion.theme - priority 40
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/DMZ-Black/cursor.theme - priority 30
/usr/share/icons/DMZ-White/cursor.theme - priority 90
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.


Thanks again!
~Z~

ps What cracks me up about all this is how the pointer appears in app windows, but not on the desktop or the toolbar on the edge of the window, or and Ubuntu menu that may appear in the app window(copy, paste, select, &tc.) So, for instance, I can use Thunderbird or Firefox pretty easily, but if I want to launch another program from the launcher it's tricky. And while I suspect this has little to do with VMWare, just to be safe I DID reinstall VMWare tools. The fact it's a virtual machine actually helps, because I can tell where the pointer is by hitting ctrl-alt, which takes the mouse OUT of the VM and avails it to the VMWare program or the real computer. I just click and it's back in virtual Ubuntu. But from what I've been reading, this is an Ubuntu problem, not a VMWare problem.

---

### Post by MAFoElffen on 2013-05-04
I'm wondering what would happen if you installed and configured another cursor theme... such as 
```

sudo apt-get install oxygen-cursor-theme oxygen-cursor-theme-extra

```
Then in the dconf editor... I can't remember if that is a default app or extra. If not default, it is worth installing... Anyways, then go tp org.gnome.desktop.interface... cursor theme. (see attached photo).

---

### Post by zlot on 2013-05-04
I went ahead and installed the cursor theme, but......***_since my dconf editor has NO contents<!!!>_*** I can't switch to it.
Couriouser and couriouser.
Surely ALL my config files can't be missing...but something sure is up with that. At one point I did attempt to reset the Unity configuration - Oh, that's right that was your suggestion - so that should have written a cile for that, yet dconf editor shows NOTHING in ANY of the categories.
I've been using the Ubuntu desktop just to see if anything doesn't mystically change on its own, but maybe I need too d/l a 13.04 image, burn it and hopw Ubuntu has a repair install....or just trash the whole damn thing and start from scratch. On a cosmic scale, it wouldn't be all that much of a disaster, as the main reason for my Ubuntu VM is just to do email - it's not like it's my main and only PC, although there would be a certain satisfaction in getting to the bottom of this. Surely there's a repair install. I might just try that....but don't stop with the suggestions...Come to think of it, I also have a couple month old mirror of this VM that I could still maintain my email without a risk, I need to verify that it's still there, and my email is all happy and functional, then see if I can do a repair.....

---

### Post by zlot on 2013-05-05
dconf editor is still blank, but a reinstall over the original succeeded, although it was a little ugly, reporting that it was unable to install all the packages. Nothing serious seems missing AND I HAVE A VISIBLE MOUSE POINTER!!!
<Wa-hoo>
So my original setup is preserved, at least for the most part, and the missing pointer problem is eliminated, if not actually solved.
Thanks much for your help and interest. Much appreciated!
~Z~

---

### Post by user_of_gnomes on 2013-06-16
So what exactly resolved your problem? Reinstalling the dconf editor even though it wasn't installed by default?

I'm having the same problem with a newly installed Lubuntu 13.04 right now.

---

### Post by zlot on 2013-06-16
A mere 6 weeks feels like an eternity ago, but it looks like I really meant a reinstall of the _whole O/S_ over the original, which, all things considered, wasn't really all that drastic since everything worked out all right. If there's a less drastic fix(and I'm sure some expert could come up with it), I certainly still don't know what it is.

---

### Post by user_of_gnomes on 2013-06-17
> **zlot said:**
> A mere 6 weeks feels like an eternity ago, but it looks like I really meant a reinstall of the _whole O/S_ over the original, which, all things considered, wasn't really all that drastic since everything worked out all right. If there's a less drastic fix(and I'm sure some expert could come up with it), I certainly still don't know what it is.

Unfortunately, that did not solve the problem for me! I will have to continue to experiment.

---

### Post by zlot on 2013-06-17
Wow - sorry to hear that....if a reinstall didn't fix it, I wouldn't know what to do. Failing anything else, a COMPLETE fresh install would be the only thing, but then there goes all your programs and work. Good luck!

---

### Post by Ed_Wei on 2014-04-21
This fixed it for me:

> gsettings set org.gnome.settings-daemon.plugins.cursor active false[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]
From [http://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/](http://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/)[/FONT][/COLOR]

---

### Post by imacamper on 2014-05-24
> **Ed_Wei said:**
> This fixed it for me:

[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]
From [http://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/](http://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/)[/FONT][/COLOR]

Thank you so much.  This worked for me as well.

Cheers,

Drew

---

