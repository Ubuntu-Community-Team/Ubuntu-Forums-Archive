---
title: "Jaunty Alpha 2 Released"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nhandler on 2008-12-19
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-December/000516.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-December/000516.html)

> Hello Ubuntu developers,

Welcome to Jaunty Jackalope Alpha-2, which will in time become Ubuntu 9.04.

Pre-releases of Jaunty are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

Alpha 2 is the second in a series of milestone CD images that will be
released throughout the Jaunty development cycle.  The Alpha images are
known to be reasonably free of showstopper CD build or installer bugs, while
representing a very recent snapshot of Jaunty. You can download it here:

  [http://cdimage.ubuntu.com/releases/jaunty/alpha-2/](http://cdimage.ubuntu.com/releases/jaunty/alpha-2/) (Ubuntu)
  [http://cdimage.ubuntu.com/kubuntu/releases/jaunty/alpha-2/](http://cdimage.ubuntu.com/kubuntu/releases/jaunty/alpha-2/) (Kubuntu)
  [http://cdimage.ubuntu.com/xubuntu/releases/jaunty/alpha-2/](http://cdimage.ubuntu.com/xubuntu/releases/jaunty/alpha-2/) (Xubuntu)

See [http://wiki.ubuntu.com/Mirrors](http://wiki.ubuntu.com/Mirrors) for a list of mirrors.

Alpha 2 includes a number of software updates that are ready for large-scale
testing.  Please refer to [http://www.ubuntu.com/testing/jaunty/alpha2](http://www.ubuntu.com/testing/jaunty/alpha2) for
information on changes in Ubuntu.

This is quite an early set of images, so you should expect some bugs.  For a
list of known bugs (that you don't need to report if you encounter), please
see:

  [http://www.ubuntu.com/testing/jaunty/alpha2](http://www.ubuntu.com/testing/jaunty/alpha2)

If you're interested in following the changes as we further develop
Jaunty, have a look at the jaunty-changes mailing list:

  [http://lists.ubuntu.com/mailman/listinfo/jaunty-changes](http://lists.ubuntu.com/mailman/listinfo/jaunty-changes)

We also suggest that you subscribe to the ubuntu-devel-announce list
if you're interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of
approved specifications, policy changes, alpha releases, and other
interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Bug reports should go to the Ubuntu bug tracker:

  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Enjoy,
-- 
Steve Langasek
On behalf of the Ubuntu release team


---

### Post by plun on 2008-12-19
Well. I am not going to give you a star.....

> **Known Issues**

As is to be expected at this stage of the release process, there are several known bugs that users are likely to run into with Jaunty Alpha 2. We have documented them here for your convenience along with any known workarounds, so that you don't need to spend time reporting these bugs again:

    *

      A new XServer, version 1.6, is included in Alpha-2. The binary proprietary drivers -fglrx and -nvidia are not yet supported for this server and will exhibit various serious issues if run against it. Users of these drivers are encouraged to wait or to switch to the corresponding open source drivers (-ati and -nv respectively) in the meantime. 308410
    * While the user-space component of the EXPERIMENTAL nouveau X driver is available in Alpha-2 universe, the kernel modules this driver requires to work are not yet available. The kernel modules should be uploaded soon after Alpha-2.
    *

      Users of Intel i845 or i865 video chipsets are unable to load X, getting an error message of "Fatal server error: Couldn't bind memory for BO front buffer". Users on these systems are advised to wait for a resolution to this bug before upgrading. 304871
    *

      The OEM mode on Kubuntu images fails after reboot in Jaunty Alpha 2. Investigation of this issue is ongoing. 309482
    *

      Choosing the "encrypt home" option on the Ubuntu server or alternate CD will cause the installation to fail at user setup time. As a workaround, you can set up an encrypted home for your user after install using the steps described in [https://bugs.launchpad.net/bugs/309541](https://bugs.launchpad.net/bugs/309541).
    * Manual partitioning doesn't work with the Kubuntu desktop CD in Jaunty Alpha 2, and with the Ubuntu desktop CD you will not be able to edit partitions as part of manual partitioning. As a workaround, you can install using one of the automatic partitioning options if appropriate, or else you can install using the alternate CD instead.
    *

      Installation to RAID from the alternate and server CDs fails with an error that no devices are marked for Linux RAID autodetect. Investigation of this issue is ongoing. 309555
    *

      Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the DontZap option in xorg.conf. A GUI tool to simplify setting xorg.conf options is under development and will be available in a later Alpha release.


Thats it......):P

---

### Post by Gina on 2008-12-19
:lolflag:  I'm always happy to thank developers - I love Ubuntu and always grateful :)

---

### Post by ronacc on 2008-12-19
> **Gina said:**
> :lolflag:  I'm always happy to thank developers - I love Ubuntu and always grateful :)

I too am always happy to thank them  , but mabye they should not be so tied to the release schedule  that they release an alpha with serious known problems with all 3 major graphics  card lines . that kind of seems counter productive .

---

### Post by DougieFresh4U on 2008-12-19
> **ronacc said:**
> I too am always happy to thank them  , but mabye they should not be so tied to the release schedule  that they release an alpha with serious known problems with all 3 major graphics  card lines . that kind of seems counter productive .

My exact thoughts!!

---

### Post by igknighted on 2008-12-19
It's an alpha... why do you need 3d support?  You can test most anything without 3d, and in some ways it helps because it will discourage people from using it as their sole desktop.

Anyone have a fast mirror to get it?  Both the official cdimage site and the torrent are projecting about 24hrs...

---

### Post by ShirishAg75 on 2008-12-19
igknighted, try using the metalink. Download first the metalink file either using the browser or using wget 

```
$ wget http://cdimage.ubuntu.com/releases/9.04/alpha-2/jaunty-desktop-i386.metalink
```Then using aria2c download the actual ISO 

```
$ aria2c -c jaunty-desktop-i386.metalink 
```The -c flag is to continue. You should get higher bandwidth. This of course would need the aria2 package installed. 

Let us know how it goes :)

I specifically use metalink so it doesn't hit the servers as much while I'm able to use http as well as bittorrent at the same time (useful for higher bandwidths)

---

### Post by ronacc on 2008-12-19
> **igknighted said:**
> It's an alpha... why do you need 3d support?  You can test most anything without 3d, and in some ways it helps because it will discourage people from using it as their sole desktop.
.

some people can't even get to their desktops 3d or 2d with xorg in its current state of disarray , for a daily build that is acceptable but in my opinion it is a mistake to put out a "milestone" in that condition , probably better than 80% of people trying the alpha will be affected to some extent , how many people have anything other than ati,nvidia or intel graphics ?  no I didn't forget via I just don't think they are a major player . As to why people "need" 3d , it is an integeral part of the modern desktop for anyone with the gpu horsepower to handle it . I have nvidia graphics and a 1680x1050 ws lcd and I can tell you that an 800x600 display which is all low graphics gives me is unuseable .

---

### Post by RAOF on 2008-12-20
> **ronacc said:**
> ...
I have nvidia graphics and a 1680x1050 ws lcd and I can tell you that an 800x600 display which is all low graphics gives me is unuseable .

The nv driver will get you 1680x1050.  If it doesn't, file a bug; it should.  In the fairly near future, the nouveau drivers should be installable from Universe, and they would also (probably) support your card.

As far as I'm aware, the majority of ati, intel[1], and nvidia cards should be working right now.  The open-source drivers get rebuilt against the new X pretty much immediately.  People using the closed-source drivers get to wait on nVidia or AMD's pleasure, as always.

[1] Yes, there's that "could not bind bo to whatever" bug.

---

### Post by igknighted on 2008-12-20
> **ronacc said:**
> some people can't even get to their desktops 3d or 2d with xorg in its current state of disarray , for a daily build that is acceptable but in my opinion it is a mistake to put out a "milestone" in that condition , probably better than 80% of people trying the alpha will be affected to some extent , how many people have anything other than ati,nvidia or intel graphics ?  no I didn't forget via I just don't think they are a major player . As to why people "need" 3d , it is an integeral part of the modern desktop for anyone with the gpu horsepower to handle it . I have nvidia graphics and a 1680x1050 ws lcd and I can tell you that an 800x600 display which is all low graphics gives me is unuseable .

Actually, most intel and ati users can live their merry lives with 3d, thanks to the intel (only a small minority affected), ati, and radeonhd drivers.  Even many nvidia users could use nouveau if they really needed 3d.  And you should be able to get your native res with one of the open source drivers.  As mentioned before, if you cannot, please file a bug.  That's why it's alpha.

Where did I ever say people don't need 3d?  I said, 3d is not necessary to fulfill the purposes of testing what needs to be tested right now.

Oh... thanks ShirishAg75.  I only ended up getting 178 kbps, but that's a whole lot better.  I'll have to remember that trick.

EDIT: Fedora had a whole release used by millions that AMD never released a working binary driver for their graphics.  It's such an easy fallback to grab the binary driver, but there is so much good work that goes into these open sourced drivers, what's the harm of giving those a chance, especially for testing an early alpha?  You might be pleasantly surprised.

---

### Post by Gina on 2008-12-20
I currently have two machines running Jaunty.  One the AMD64 desktop with nvidia (180 driver) and 1650x1050 screen  working fine for what I use (I'm not using compiz - maybe I should test it).  The other is my laptop - AMD Athlon XP with integrated old ATI graphics and default driver with 1024x768 screen,  Both systems run fine with full size display at their native resolution.

I find Jaunty perfectly usable using the updates - not tried installing Alpha 2 yet - downloaded it last night.

---

### Post by RAOF on 2008-12-20
> **igknighted said:**
> ...
Even many nvidia users could use nouveau if they really needed 3d.  And you should be able to get your native res with one of the open source drivers.  As mentioned before, if you cannot, please file a bug.  That's why it's alpha.
...

For those playing at home, the nouveau (and mesa) packages in Ubuntu do *not* contain the 3D driver.  (a) Upstream does not support[1] 3d with nouveau in any way, and (b) the 3d support requires using the gallium branch of mesa, which will basically break all other free 3d drivers.

[1] "Support" as in "we don't care if it doesn't work".

---

### Post by DavidONE on 2008-12-20
I couldn't even get it to install - some problem with setting up partitions (sorry, I tried late last night and didn't make notes).

It does seem like this is sub-standard to be released as a milestone.  I'll wait 'til the next alpha and see if it gets any better.

---

### Post by mdurham on 2008-12-20
> **DavidONE said:**
> I couldn't even get it to install - some problem with setting up partitions (sorry, I tried late last night and didn't make notes).

It does seem like this is sub-standard to be released as a milestone.  I'll wait 'til the next alpha and see if it gets any better.

I had the same problem with 64 bit version. Can't get past partitioning. Can't even close the dialog, have to press the reset button.
Hopeless!
Cheers, Mike

---

### Post by pelle.k on 2008-12-20
> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the DontZap  option in xorg.conf.
Respectfully; this is simply ridiculous! I do appreciate the fact that we can turn it on, but isn't this exactly the kind of dumbing down we would expect from OSX or windows vista?
I use ubuntu/linux because it doesn't treat me like a child. Maybe ubuntu is heading in another direction? (maybe it always was, just i didn't notice it?)

---

### Post by Gina on 2008-12-20
I'm afraid I'm inclined to agree.

---

### Post by amano on 2008-12-20
This is not an Ubuntu only change. This decision was made by upstream (X.org) and Ubuntu decided to stick with this decision, but offer an easy GUI way to re-enable the old behaviour.

Blame upstream and not Ubuntu for what you call "Dumbing down".

---

### Post by amano on 2008-12-20
--

---

### Post by castrojo on 2008-12-20
> **pelle.k said:**
> Respectfully; this is simply ridiculous! I do appreciate the fact that we can turn it on, but isn't this exactly the kind of dumbing down we would expect from OSX or windows vista?
I use ubuntu/linux because it doesn't treat me like a child. Maybe ubuntu is heading in another direction? (maybe it always was, just i didn't notice it?)

How is this "dumbing down"?

How is removing a seemingly arbitrary random keystroke that kills your xserver "dumbing down"?

---

### Post by pelle.k on 2008-12-20
> Blame upstream and not Ubuntu for what you call "Dumbing down"
Fair enough. Thanks for the explanation.

> How is this "dumbing down"?

How is removing a seemingly arbitrary random keystroke that kills your xserver "dumbing down"? 
Maybe is was bit too dramatic about this.
It's a bit like when kubuntu (back in the days) removed the "window" menu from konqueror - a perfectly good feature removed because it's "too complicated".
The combination ctrl-alt-backspace isn't anything i usually hit "by mistake", and it's a really good feature. I do, however, have apps locking Xorg to the degree that i have to ctrl-alt-backspace Xorg to get the desktop back to a usuable state. So, my own wish (and i stress that, knowing i do not represent the whole community) is that it shouldn't be removed by default. But who's to argue with upstream, or the delvelopers, since my idea of what ubuntu is supposed to be, and what the developers want it to be may differ. I admit as much.

---

### Post by plun on 2008-12-20
> **pelle.k said:**
> Respectfully; this is simply ridiculous! I do appreciate the fact that we can turn it on, but isn't this exactly the kind of dumbing down we would expect from OSX or windows vista?
I use ubuntu/linux because it doesn't treat me like a child. Maybe ubuntu is heading in another direction? (maybe it always was, just i didn't notice it?)

Yup....  +1

How can a user accidently trigger  Ctrl-Alt-Backspace  :confused::confused:

One case can be to follow a forum or manual advice which doesn't mention that all apps must be closed... but then this users learns it... 100% sure !

Another way is to add a GUI to this command.... "Please close/save all work" > Ok for restart....:)

---

### Post by DavidONE on 2008-12-20
Advanced user (everyone here): set CTRL+ALT+BACKSPACE to kill server, if you want - 60 seconds work

My mum: "I meant to hit Ctrl + Alt + L to lock the screen but I think I did something else and everything disappeared!  What do I do?!"

Linux is for everyone, folks - and the newbies / casual users need to be protected from arbitrary and destructive options.

It's a good decision.

---

### Post by aamukahvi on 2008-12-20
You can always switch to a TTY and restart GDM. Or just re-enable to shortcut. No biggie.

---

### Post by tripinva on 2008-12-20
> **aamukahvi said:**
> You can always switch to a TTY and restart GDM. Or just re-enable to shortcut. No biggie.

Yes, walking someone through that ought to be a joy.  I don't hand-configure each computer I have to walk people through over the phone or IM.

"Press Ctrl+Alt+F1... now put in your name and password.  Type 'sudo ps space dash capital A, space then that little line symbol near enter--yes, the one with the backslash on it--space, then grep space *dm and press enter.  Now, see that number?  Yes, that one.  Type 'sudo kill and then that number.'"

Or, better, when the server kills tty.  Mine doesn't work sometimes after X locks up.

"Press Ctrl+Alt+F1... You're just getting a blank screen? Oh well, hold the power button. Nothing you can do."

How does one go about undoing this horrible decision locally?  There's a link in the announcement to a page that doesn't exist, and I can't seem to locate any information on reenabling it for myself.

- Trip

---

### Post by Naddiseo on 2008-12-20
> **aamukahvi said:**
> You can always switch to a TTY and restart GDM. Or just re-enable to shortcut. No biggie.

Except when the TTYs don't work, and you can't ssh in. and there's something wrong with my computer that's stopping vesa and nv from working :( so I can't use ANY video drives at the moment. Meh, reinstalling for now.

---

### Post by mattduckman on 2008-12-20
i kinda like openSUSE's (and possibly other distros') solution to the kill-X problem:

push ctrl+alt+backspace once, the computer beeps, push ctrl+alt+backspace again within a couple seconds to restart.

that way, new users will learn to never push that key combo again without having to lose their work.

---

### Post by Gourgi on 2008-12-20
> **mattduckman said:**
> i kinda like openSUSE's (and possibly other distros') solution to the kill-X problem:

push ctrl+alt+backspace once, the computer beeps, push ctrl+alt+backspace again within a couple seconds to restart.

that way, new users will learn to never push that key combo again without having to lose their work.

nice :D
this sounds clever !

---

### Post by ronacc on 2008-12-20
> **whiprush said:**
> How is this "dumbing down"?

How is removing a seemingly arbitrary random keystroke that kills your xserver "dumbing down"?

ctrl+alt+bkspc has been the "quick kill" for X for as long as I can remember . and how is it more "arbitrary" than any other shortcut combo ? and just how is it harder to learn than "sudo /etc/init.d/gdm stop  >  pwd" then "sudo init 3" . I also suppose that in windows it is soooo easy to know (intuitivly) what ctrl+alt+delete does ?  Trying to make things so that you have to learn not even the simplest thing IS dumbing down

---

### Post by castrojo on 2008-12-20
> **ronacc said:**
> ctrl+alt+bkspc has been the "quick kill" for X for as long as I can remember . and how is it more "arbitrary" than any other shortcut combo ? and just how is it harder to learn than "sudo /etc/init.d/gdm stop  >  pwd" then "sudo init 3" . I also suppose that in windows it is soooo easy to know (intuitivly) what ctrl+alt+delete does ?  Trying to make things so that you have to learn not even the simplest thing IS dumbing down

Restarting an X server is not "even the simplest thing". The fact that users have to even know how to do it is wrong. I don't know why you think I care about what windows does - pretty sure that a random keystroke in windows doesn't kill their gui with no explanation though.

---

### Post by ronacc on 2008-12-21
sometimes the ability to kill x is a necessary thing , especialy during a dev cycle . pretending that oops's don't happen and that you can be completely mindless about the workings of your OS is just plain dumb . I suppose next they will want to block alt>sysreq>RSEIUB now thats a real likely combo for some one to hit by mistake ! Until all software is perfect the ability to quickly and eaisly kill an xserver gone beserk is a nice thing to have , is there a possibility that you could lose your unsaved work ? yes but hitting reset will lose it just as fast , and don't give me that bit about grandma hitting ctrl>alt>bkspc when she ment ctrl>alt>l I've got big hands and I can't reach the bkspc without lifting my hand off the home row , granny must be one heck of a typist.

---

### Post by castrojo on 2008-12-21
> **ronacc said:**
> sometimes the ability to kill x is a necessary thing , especialy during a dev cycle . pretending that oops's don't happen and that you can be completely mindless about the workings of your OS is just plain dumb.

Of course. I think you misunderstand my point.

> I suppose next they will want to block alt>sysreq>RSEIUB now thats a real likely combo for some one to hit by mistake ! Until all software is perfect the ability to quickly and eaisly kill an xserver gone beserk is a nice thing to have , is there a possibility that you could lose your unsaved work ? yes but hitting reset will lose it just as fast , and don't give me that bit about grandma hitting ctrl>alt>bkspc when she ment ctrl>alt>l I've got big hands and I can't reach the bkspc without lifting my hand off the home row , granny must be one heck of a typist.

I have my hands on ctrl-alt all the time, usually I am going left to right with my arrow keys to switch desktops, and when I get to a desktop with a browser sometimes I want to go back, and I hit backspace ... sometimes I have my hands on ctrl-alt, sometimes not, but it kills my x server. Anyway, that's not important...

Let me make one thing clear. I am not saying that the ability to kill an X server should be removed. I am saying that I .. as a user should never be able to kill an xserver in the first place.

If you bone up your xorg.conf or are trying some experimental thing and you feel the need to kill your xserver, then by all means, rock on with your bad self. 

If the X server is broken anyway, then ctrl-alt-backspace is just a rope ... it feels like "hey man, I just jumped over a cliff and you took away my rope, that's kind of crap" .. when the reality is, you jumped over a cliff and having a rope isn't going to help you anyway because you're already half-way down, so how about we just fix it so there isn't a stupid cliff in the first place so please stop worrying about the stupid rope ...

---

### Post by ronacc on 2008-12-21
Ah you navigate with the keyboard , being a touch typist , when my hands are on the keyboard they are on the " home keys" ( middle row of letters , specific letters fdsa  jkl; ) . I am not sure what you mean by
 >  Let me make one thing clear. I am not saying that the ability to kill an X server should be removed. I am saying that I .. as a user should never be able to kill an xserver in the first place.   

If you mean that an ordinary user should not have the need to kill an xserver that is desireable, but does not and never will correspond to reality , software is imperfect, hardware fails . We should never need seatbelts in our cars or crash helmets on our motorcycles either , welcome to the real world . If you mean that no user ( even an administrator ) should not have the authority to kill an xserver that is just plain nuts .

---

### Post by pelle.k on 2008-12-21
Now I just feel lika bad, bad troll. Look what i did ma.
Wish i could ctrl-alt-delete this thread! ;)

---

### Post by igknighted on 2008-12-22
> **RAOF said:**
> For those playing at home, the nouveau (and mesa) packages in Ubuntu do *not* contain the 3D driver.  (a) Upstream does not support[1] 3d with nouveau in any way, and (b) the 3d support requires using the gallium branch of mesa, which will basically break all other free 3d drivers.

[1] "Support" as in "we don't care if it doesn't work".

Thanks for the correction, I don't use nvidia so I wasn't sure of the driver's state.  Someday...

---

### Post by reg-sux on 2008-12-23
> **plun said:**
> Yup....  +1

How can a user accidently trigger  Ctrl-Alt-Backspace  :confused::confused:



much more easy than you think. It has happened to me on several occasions over the years already.

For instance, when I want to change virtual desktops, and start doing Ctrl-Alt-"->", and if I spot something I want to delete, and I keep the Ctrl-Alt on, WAM!

It's odd, but it happens. I had already disabled Ctrl-Alt-Backspace a long long time ago.

---

### Post by plun on 2008-12-23
> **reg-sux said:**
> much more easy than you think. It has happened to me on several occasions over the years already.

For instance, when I want to change virtual desktops, and start doing Ctrl-Alt-"->", and if I spot something I want to delete, and I keep the Ctrl-Alt on, WAM!

It's odd, but it happens. I had already disabled Ctrl-Alt-Backspace a long long time ago.

OK....

I was trapped within KDE4 yesterday with a crashed X until I found that Ctr-Alt-Del works.

A nice solution would maybe to connect this command to the **Log Out** GUI.. ?

This is also an important Linux standard question  !  maybe something for FreeDesktop ?

---

### Post by Gina on 2008-12-23
> **plun said:**
> 
A nice solution would maybe to connect this command to the **Log Out** GUI.. ?Is KDE different from Gnome?  On my Ubuntu systems Ctrl+Alt+Del goes to the logout/shutdown/restart dialog.  Am I mising something here? :confused:

---

### Post by pelle.k on 2008-12-23
> Is KDE different from Gnome? On my Ubuntu systems Ctrl+Alt+Del goes to the logout/shutdown/restart dialog. Am I mising something here
You're confusing ctrl-alt-del with ctrl-alt-backspace. ctrl-alt-delete does indeed trigger the logout dialog (not the shutdown dialog in my case, on intrepid).
Even so, with a broken X, no dialog would show, so i guess the opensuse method (ctrl-alt-backspace) is the best solution to this problem yet.

---

### Post by plun on 2008-12-23
> **Gina said:**
> Is KDE different from Gnome?  On my Ubuntu systems Ctrl+Alt+Del goes to the logout/shutdown/restart dialog.  Am I mising something here? :confused:

Well.. I dont know what a standard says.

For me it is Ctrl-Alt-Backspace for a X-restart.

Ctrl-Alt-Del is just an emergeny exit and works sometimes.

The Log Out GUI nevertheless catches running apps..."Please save all work"

The majority will probably use the Power button anyway...:-k

The OpenSuse way is OK for me....

---

### Post by jfernyhough on 2008-12-23
> Let me make one thing clear. I am not saying that the ability to kill an X server should be removed. I am saying that I .. as a user should never be able to kill an xserver in the first place.

The number of times I've had X (or more likely Compiz) freeze only to be saved by a CTRL-ALT-BKSP... or when Compiz fails to initialise properly and leaves me with no window decorations... or when GNOME fails to initialise for some reason and leaves me with no panels... it's one of those things I love about Linux compared to the other major players - complete control. It's my process - why shouldn't I be able to kill it?

Of course, I /could/ instead SSH in and shutdown GDM or try and kill the offending application, but if I'm not on a network or have a spare machine handy, or haven't set up SSH (typical of most users) I can't do that.

Of course, I /could/ do a CTRL-ALT-F[1-6] to switch to a console, unless Compiz has locked and is ignoring the binding, or the nvidia driver I need for Compiz has messed up the console display, or...

At the very least this should be an installation option.

The thought that the majority of careful users (who know which keys they are pressing) are babied for the carelessness of a few is mind-boggling. Trying not to be blunt, but it's like keeping a whole class in detention because one (who is known) threw a brick through the window. Being able to accidentally kill the X server (and that probably only once or twice, as people tend to learn) is not why people don't use Linux.

Plus, why are we trying to make Ubuntu into Mac OS X? OS X has already been done. By Apple. Can we not move on?

---

### Post by adult swim on 2009-01-02
> Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the DontZap option in xorg.conf. 

what is this DontZap option in xorg.conf to enable ctrl+alt+bkspc?  does it belong in a certain section?

---

### Post by plun on 2009-01-02
> **adult swim said:**
> what is this DontZap option in xorg.conf to enable ctrl+alt+bkspc?  does it belong in a certain section?

According to release notes for Alpha 2

    * DontZap

**This page does not exist yet. You can create a new empty page, or use one of the page templates.**


[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/46618](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/46618)


Wont fix ????   Yes I am in a bad mood...sorry...:(

---

### Post by adult swim on 2009-01-02
:D thanks mate!

---

### Post by plun on 2009-01-02
> **adult swim said:**
> :D thanks mate!

Great you got it...:D

I am going to play Duke Nukem...:(
(most stupid game I knows ](*,) for Debian lovers...)

---

