---
title: "getting black screen when switching users in lucid 10.4"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by newbuntuxx on 2010-05-03
Hello All,

I just upgraded from 9.10 to 10.4. I am having the following problem:

When I attempt to switch from the user that I am currently logged into, to another user who is also logged in, I get a black screen. 

To elaborate, here is the exact sequence of events:

```
- Boot ubuntu and login to user A
- Then Click on power menu (top right corner) and select: Switch from A
- I get the login screen
- I select user B and enter my password
- I hit ok
- I am able to login successfully to user B
- Now, I Click on power menu (top right corner) and select: Switch from B
- I select user A from the login screen and enter my credentials, then hit OK
- I get a black screen
```

Now this where I get stuck! The only key combination that works is: Ctrl + alt + F8. This gets me back to a login screen.

Now I obviously can not login to a user who is already logged in because I'll just end up getting a black screen. At this point, the only thing that I can do is login to a user who is not already logged in, assume root privileges and logout all users who are logged in using the command:

```
skill -KILL -u user
```

If, however, all available users are already logged in, then I am left with two options: 
- rebooting or
- switching to a shell (ctrl + alt + f1), and restarting the xserver

I did try to change my session (at the login screen) to gnome-failsafe, xterm, even kde, but still I get the black screen.


Hopefully this is more coherent!

---

### Post by newbuntuxx on 2010-05-03
[COLOR="Red"]SEE Opening post[/COLOR]

editted

---

### Post by newbuntuxx on 2010-05-03
[COLOR="Red"]SEE Opening post[/COLOR]
edited

---

### Post by Pilo on 2010-05-03
> **newbuntuxx said:**
> If I switch from user A to user B and user B is not logged in, then I don't get the black screen issue. However, If I try to switch to a user who is already logged in, I get the black screen issue.
I have precisely the same issue.

---

### Post by Pilo on 2010-05-03
Looks like iomtalach and WolverineFan are having a similar issue over in [http://ubuntuforums.org/showthread.php?t=1467619]("http://ubuntuforums.org/showthread.php?t=1467619")

I'm currently running an nVidia MCP78S [GeForce 8200] with the default open source drivers on a fresh install of Lucid with dual monitors.

I believe the problem (for me at least) is the one reported here: [https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/549632]("https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/549632")
Which appears to share a root cause with: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/555870]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/555870")
[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/546578]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/546578")
These all essentially seem to deal with the gamma values not being reset properly after a fade out.

The suggested work-around of hitting alt-f2 and typing
```
xgamma -gamma 1.0
```
Works partially for me, it restores one of my monitors but not the other (which happens to be the one with my gnome panels unfortunately).

---

### Post by WolverineFan on 2010-05-04
I filed a bug report.  Feel free to chime in with your individual details.

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/574909](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/574909)

---

### Post by WolverineFan on 2010-05-04
> **Pilo said:**
> The suggested work-around of hitting alt-f2 and typing
```
xgamma -gamma 1.0
```
Works partially for me, it restores one of my monitors but not the other (which happens to be the one with my gnome panels unfortunately).

You can specify a display to xgamma:

```
xgamma -display 0.0 -gamma 1.0
```
```
xgamma -display 1.0 -gamma 1.0
```

(My X is a bit rusty, I think that's the right syntax).

I only have one display so I can't test the -display parameter, but I can report that xgamma -gamma 1.0 works for me too.  Seems like an easy enough fix hopefully!  It would be most excellent if this worked reliably!

---

### Post by newbuntuxx on 2010-05-04
Well, this is what I tried so far:
- Removed the password from all users 
tested: still get black screen
- reinstalled gdm
- tested: same thing

In fact, now when I get the black screen, I can't even use any key combination at all! I must reboot to get anywhere.

---

### Post by OwnSurname on 2010-05-08
Same problem here, black screen to nowhere. Sorry guys, I have to write this down clearly: this puzzle me the most, they want to bring Ubuntu to the "normal" user, and then (s)he can't even switch in between two users. Is it *so* difficult to make a small program to switch to another user that work?

---

### Post by maxpoweron on 2010-05-10
I have the same problem on my two PCs; a Dell Dimension 8200 and a Sager NP8690 notebook.  I noticed the problem after I installed the Nvidia drivers for each PC.

---

### Post by BFG on 2010-05-11
I have the same, but slightly worse.

ATI card on 64 bit, with and without restricted drivers, with and without special effects - makes no difference.  When I get the black screen, the system locks up completely. Not even alt+sysrq+o works.

It's fine on a liveUSB, but I added a dual-boot to try lucid out and these lockups are giving the HDD hell.  I have to power off to get out of it and twice I've had "boot disk not found" afterwards.  I can get back, but it's really worrying.

Experimenting further, if I don;t user switch, but try Ctrl+Alt+f2, that's fine, but going back to X with Ctrl+Alt+F7 gives me a lockup again, but this time it's purple.  Purple screen of death?? :confused:

---

### Post by !nkubus on 2010-05-12
I ave the same issue, I must admin that my GF is frustrated every time it happens. she now wants to buy a MAC lol yiiikes ....

---

### Post by Thorndog on 2010-05-12
Desktop with quad 6600 64 bit etc
Exactly the same issue. Black screen of death. My wife is not too pleased because I can't let her use my user and clog up my browser history, mess up cookies etc with ebay and Paypal etc.
This REALLY needs to be a priority bug fix because (hard, power off)reboots are NOT what I want to be doing every day but neither can we all share our desktop with the family or coworkers or whatever. I really don't want to back up to 9.10 either and waste a day no doubt in the process.
Somebody fix this pleeeeasse.

---

### Post by BFG on 2010-05-14
> **Thorndog said:**
> Desktop with quad 6600 64 bit etc

I forgot to mention above.  I have Quad Q9550 with 64 bit. Maybe this is significant. Video Card is a Sapphire 512Mb Radeon HD 4670,

---

### Post by Thorndog on 2010-05-14
> **BFG said:**
> I forgot to mention above.  I have Quad Q9550 with 64 bit. Maybe this is significant. Video Card is a Sapphire 512Mb Radeon HD 4670,
Different video. I have on board Intel chipset, I think it's nvidia. MM I guess I could check but I don't remember how. Still, if it's only 64 bit users....
I also had a problem withrunning Wesnoth, a game and on a forum there it was mentioned that a non response problem to mouse clicks there was cause by the latest libsdl version. Great. Maybe I jumped for Lucid too soon...

---

### Post by leodamasio on 2010-05-16
Hi,
It's not a 64bit only problem. I have the same issue (black screen when switch users) in a 32 bit box.
Regards

---

### Post by emigrant on 2010-05-19
Its really sad to have this problem in the nicely build lucid.
hope some one soon fixes this.

---

### Post by Ubunting biochemist on 2010-05-21
I am also having this problem on a 32-bit box with an ATI video card. Upgrade from Jaunty to Karmic was no problem. My wife is also none to pleased. I would love to see this fixed!! Thanks.

---

### Post by kleo skywalker on 2010-05-23
Hi all,

I have the exact same problem with a clean install of 10.4 on a 32-bit machine. I haven't tried the key combinations mentioned in this thread, so I've had to press the power button and turn off every time.

Does anyone have a solution to this?

Thanks.

---

### Post by dino99 on 2010-05-23
> **kleo skywalker said:**
> Hi all,

I have the exact same problem with a clean install of 10.4 on a 32-bit machine. I haven't tried the key combinations mentioned in this thread, so I've had to press the power button and turn off every time.

Does anyone have a solution to this?

Thanks.

can try:
- remove .gnome
- metacity --replace
- add this ppa: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by emigrant on 2010-05-24
dino u sure about that?
did u test and succeeded?

---

### Post by hillsimon on 2010-05-26
Hi,

I've tried to restart this bug report:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290704](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/290704)

Please click that you are affected by it (at the time of writing this there's a total of 27 affected users).

Simon.

---

### Post by emigrant on 2010-05-27
any kde users have this problem?

---

### Post by hillsimon on 2010-05-28
If you're experiencing this problem and have a NVIDIA graphics card, then I've reported the bug
Please visit and click on the green link to report the bug affects you.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069)
Thanks,
Simon.

---

### Post by OldSlacker on 2010-05-28
Same scanario... black screen after switching users, 32-bit system, nvidia legacy g-force, total freeze with no ctrl-alt options, must power down. For what it's worth Linux Mint 9 has the same issue. Have been running Ubuntu since Hoary Hedgehog, currently on Karmic. First time for this problem. Will not move up to Lucid until this is fixed.

---

### Post by djxcon on 2010-05-28
I believe this was a bug in gnome-screensaver but could be wrong.  A patch to gnome-screensaver came out today in the repos with a description that addresses this issue in part.  I have downloaded the patch but haven't tested.

---

### Post by OldSlacker on 2010-05-28
I found that one on Google, and tried it... completely removed gnome-screensaver... had no effect whatsoever. :confused:

---

### Post by hillsimon on 2010-05-29
Please add yourself to: [https://bugs.launchpad.net/ubuntu/+s...73/+bug/587069]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069")

---

### Post by OldSlacker on 2010-05-30
> **hillsimon said:**
> Please add yourself to: [https://bugs.launchpad.net/ubuntu/+s...73/+bug/587069]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069")

I went to that page, but don't understand what I am supposed to do on it.

On other matters, I can now fully understand why Debian Squeeze is still in "testing". It appears that Ubuntu Lucid should have followed that example. Ubuntu has done a lot for Linux, and that has moved them to the top in popularity, but I believe if the recklessness shown in the past couple  releases continues they will lose that place.

---

### Post by hillsimon on 2010-05-31
> **OldSlacker said:**
> I went to that page, but don't understand what I am supposed to do on it.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069)

You have to register/login to launchpad (top right).
Then you are able to click on a link on top left saying how many people the bug affects and add yourself to the list.
The more people that do this, the more likely it will be fixed.

---

### Post by salemoh on 2010-09-27
I'm getting a black screen when switching users on Lucid installed on Virtual Box. Did this get resolved?

---

### Post by Thorndog on 2010-09-27
I don't have the problem any more and honestly don't rmemeber when that happened. I have since changed motherboard and done a fresh install. I have switches off screensaver completely since I had problems with that and I think that might have been it. Sorry I can't help more.

---

### Post by WolverineFan on 2010-09-27
> **salemoh said:**
> I'm getting a black screen when switching users on Lucid installed on Virtual Box. Did this get resolved?

Yes, this was resolved with a patch to the screensaver code I believe.  Long before 10.04.1.  Pretty sure it had something to do with the fade-to-black stuff.

If you've installed all the latest updates, you have a different issue.

---

### Post by hillsimon on 2010-09-27
Hi,

The problem still persists exists but seems to be related to the particular video driver.

See this one for NVIDIA:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069?comments=all](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/587069?comments=all)

Simon

---

### Post by SentientFluid on 2010-10-12
I had the same issue with a fresh install of 10.04 when using the 173 nvidia drivers. Here's what fixed it on my system:
```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/nvidia-173-kernel-source_173.14.28-0ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/nvidia-173_173.14.28-0ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.28-0ubuntu1_i386.deb
dpkg -i nvidia*deb

```

That will download and then install the nvidia 173 drivers used with 10.10 which do not have this bug.

Of course another option might be to upgrade to 10.10.

---

### Post by hillsimon on 2010-10-20
Extremely grateful to you.
Followed your instructions, haven't had any black screens since.
Thanks.

---

