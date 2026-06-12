---
title: "Auto Login does not allways work"
date: 2009-12-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2009-12-24
I have my Ubuntu 10.04 32 bit set up to auto login and recently it stops  at the login screen. Other times it works correctly. My Ubuntu 9.10 does not have this behavior.

Bill

---

### Post by VMC on 2009-12-24
> **sparker256 said:**
> I have my Ubuntu 10.04 32 bit set up to auto login and recently it stops  at the login screen. Other times it works correctly. My Ubuntu 9.10 does not have this behavior.

BillIt works okay for me. I started at alpha1 and just kept lucid updated. I wonder if you have this problem from one of the last daily iso's, like 12/23/09 ?

---

### Post by sparker256 on 2009-12-24
> **VMC said:**
> It works okay for me. I started at alpha1 and just kept lucid updated. I wonder if you have this problem from one of the last daily iso's, like 12/23/09 ?

I have installed the 121609 daily build then upgraded from there. It seems to have recently started like in the last couple of days.

Bill

---

### Post by Roosje on 2009-12-25
I have the same problem on 64 bit version, sometimes with, sometimes (most?) without autologon, and still nvidia troubles :-( Whole 9.10 Alpha seemed a lot more smooth than this time, ah well alpha testing ;-)

---

### Post by kansasnoob on 2009-12-25
I've noticed the same thing. X appears to begin to start but then it falls back to login.

---

### Post by ronacc on 2009-12-25
no problem with my lucid (gnome) install but Kubuntu 10.04 won't auto login ever , have to enter PW each time .

---

### Post by VMC on 2009-12-25
> **ronacc said:**
> no problem with my lucid (gnome) install but Kubuntu 10.04 won't auto login ever , have to enter PW each time .

Your right. I just installed the latest current and I had to enter my id and pw. At least it isn't of the looping variety that some folks are experiencing on Gnome.

---

### Post by ranch hand on 2009-12-25
> **VMC said:**
> Your right. I just installed the latest current and I had to enter my id and pw. At least it isn't of the looping variety that some folks are experiencing on Gnome.
Are you running in VB?  That is where the problem in Ubuntu are happening.  It is a fault in the LiveCD ISO.

If anyone is having this problem, confirm it at;

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

There is a work around from ASriazh;

[http://ubuntuforums.org/showpost.php?p=8557427&postcount=22](http://ubuntuforums.org/showpost.php?p=8557427&postcount=22)

---

### Post by VMC on 2009-12-25
> **ranch hand said:**
> Are you running in VB?  That is where the problem in Ubuntu are happening.  It is a fault in the LiveCD ISO.

If anyone is having this problem, confirm it at;

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

There is a work around from ASriazh;

[http://ubuntuforums.org/showpost.php?p=8557427&postcount=22](http://ubuntuforums.org/showpost.php?p=8557427&postcount=22)

No, not running in VB. But I have to enter id & pw every time. Using Kubuntu only. No problem using Ubuntu alpha1.

---

### Post by ranch hand on 2009-12-25
I just wondered when you were mentioning the looping login on Ubuntu.  I haven't see anyone complaining about that (could be I missed it).

The LiveCD is a real problem and has been for a while.

---

### Post by VMC on 2009-12-25
> **ranch hand said:**
> I just wondered when you were mentioning the looping login on Ubuntu.  I haven't see anyone complaining about that (could be I missed it).

The LiveCD is a real problem and has been for a while.

I'm not sure anymore. There's a lot of talk about that login appearing all over the place. My updated Ubuntu alpha1 has not problems, its the current Kubuntu 10.04 that requires login. Even after I set up for auto login.

---

### Post by ranch hand on 2009-12-25
I am not a big fan of KDE and usually don't fool with Kubuntu but. it's all your fault, because of this I just finished downloading Kubuntu A1.

I will see what it does to me.  I will change one of my Ubuntus to auto login too.  I just do not do that normally, not sure why not really, just don't.

---

### Post by ranch hand on 2009-12-25
Nice of them to package a "cdimage" that won't fit on a CD.

---

### Post by ronacc on 2009-12-25
they warn about that in the known issues . use a dvd or usb stick .

---

### Post by VMC on 2009-12-25
> **ranch hand said:**
> Nice of them to package a "cdimage" that won't fit on a CD.I never use CD's anymore, unless for my music. I always use DVD/RW's I never know if I going to keep them that long.

Regarding Kubuntu vs Ubuntu. I too have been a long time Gnome user, but I was reading up on KDE4 and tried it first on PC-BSD. It was very stable on that BSD system.

Then I got hold of a karmic dvd that had all the *buntus, so I thought what the heck and installed Kubuntu. If for no other reason as something new to learn.

As far as the two go regarding Lucid, Ubuntu Gnome is by far the more stable one. Kubuntu crashes constantly. And yes I know we are still in testing stage, but if you gauge the two, Gnome works very well at the early stage(for me).

 My Kubuntu Karmic on the other hand is very stable.

---

### Post by ranch hand on 2009-12-26
Well, I finally got Kubuntu installed.  Did not boot into it.  Wasted too much boinc time on a very kshakey Live Ksession.  There is some kfool thing that crashed both times as soon as I booted so that I did not have in the kmenu either a partition editor or a terminal.

I went back to Jaunty on my main drive and partitioned from there.  Kbooted back to the LiveCD and went to install and the kfool thing must effect the installer too.  alt+f2, if held down for more than 15 seconds, allowed me to "sudo ubiquity" and get installed.

I checked the "automatic log in" option.  I will try it in the morning, I promise.  I am going to chroot into it to tweek grub to my liking, which will be easier than using that helpless FM in Kubuntu (unless it has changed) and update the bugger.

I do not know if aptitude works in Kubuntu.  I hope so.  I do not use it normally but from what I have seen of Kpackage Manager - well I need something that works without raising my blood pressure to the point that I could be an alternative energy source.

Is there a real menu available for Kubuntu?  I do not care who stole that krappy idea from whom, it is bad in MS and it is bad in Linux (I have a KDE Mandriva too).

---

### Post by ranch hand on 2009-12-26
Well, I can see why you guys use aptitude.  I don't think I will though.

"sudo aptitude update" went well.  "sudo aptitude safe-upgrade wanted to remove the ...7 kernel but was not going to install the ...9 kernel.  Yup, I am chicken.

I think I will stick to apt-get that is now upgrading, holding more back (doing 267 packages - aptitude was going to do 383) so I will have a little more work but I will always have a kernel installed.

---

### Post by VMC on 2009-12-26
> **ranch hand said:**
> ...kfool thing must effect the installer too.  alt+f2, if held down for more than 15 seconds, allowed me to "sudo ubiquity" and get installed....Is there a real menu available for Kubuntu?  I do not care who stole that krappy idea from whom, it is bad in MS and it is bad in Linux (I have a KDE Mandriva too).
Funny, but ubiquity worked perfectly for me under Kubuntu. I had to fiddle around to get it to work under Ubuntu.

Regarding the menu you spoke of. Are you referring to "kicker"?

BTW-Kubuntu 9.10 is almost perfect.

I see why there are a lot of complaints regarding Kubuntu. Specialty right now. It gets hit on two fronts. (1) 10.04 testing and (2) Kde4.4 beta2. So if you run into problems with Ubuntu 10.04, same problem pops up under Kubuntu. Then if KDE beta2 runs into problems you have THAT to deal with. It would be like Ubuntu testing AND Gnome 3 being worked on together.

---

### Post by ranch hand on 2009-12-26
Auto-Login does not work.  I do not know if it works in Ubuntu or not but I don't think I have seen complaints about it.

What I want is a menu that allows you to see what is there without wading through several screens.  This is why all my MS installs ended up with shortcuts all over the desktop, a silly solution for a stupid menu system,

Surely there is, in linux, someone somewhere, that has come up with a menu that just shows you what is in there.

There are things that are going to bother someone in any OS Desktop Manager.  Ubuntu sure does for me.  So do Lxde and Xfce.  I use all three of them and have the Gnome Desktop on one too, to try (no opinion yet - good first impression).

There are a number in KDE that bug me too.  The menu, though, is the deal breaker.  I am sure that there are a lot of folks that love it.  I completely and absolutely hate it with a passion.  I am not compatible with it at all.

So what I want is an alternative.  I would love to have Kubuntu back in my loaner drive to show folks, but I need to get in and keep it up to date and become kfamiliar with the system.  It will not happen until I have a different menu option.

---

### Post by VMC on 2009-12-26
> **ranch hand said:**
> Auto-Login does not work.  I do not know if it works in Ubuntu or not but I don't think I have seen complaints about it.

What I want is a menu that allows you to see what is there without wading through several screens.  This is why all my MS installs ended up with shortcuts all over the desktop, a silly solution for a stupid menu system,

...
I'm sure your talking about kicker. Its the "blue circle K" at bottom left. Make sure Widgets are unlocked, then right-click and chose "switch to classic menu style" and see if that's more to your liking.

Regarding auto login. Yes, it works for Ubuntu 10.04, but NOT for Kubuntu 10.04. I hope if gets fixed though.

---

### Post by ranch hand on 2009-12-26
So now if we could only get to the desktop on Ubuntu LiveCD without changing permissions it would be great.  I wonder if the installer partitioner can be set to format with out crashing,  I haven't really tried it since A1.

I will have a look at this "kicker" business sometime today.  I have several installs that are due being checked today besides, of coarse, this one.

Thanks for the tip.

---

### Post by ranch hand on 2009-12-26
OK, that was fun.  Where in flinderation are these widgets?  All I can find is reference to "remote widgets" which sound intrusive.

Is this the point of KDE, to keep people without a life busy fiddling with there desktop?

---

### Post by kansasnoob on 2009-12-26
> Is this the point of KDE, to keep people without a life busy fiddling with there desktop?

Well, to me, it's like clutter on top of clutter. Almost like Windows!

I don't know why anyone would prefer KDE but my daughter does.

To me one of the coolest things about Ubuntu is the ability to change from one to the other.

Aysiu stays up on that:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Look at the "Playing around" section.

---

### Post by ranch hand on 2009-12-26
Well I got the menu deal straight and it is an improvement.  I then logged back in here to update and do some other things while letting boinc run.

I will log in there again tonight or tomorrow.  When I logged in earlier it was on auto just fine.  Kinda weird.

I am with kansasnoob on this one for sure.  At least when I was over there I got rid of the god awful blue background.  I would rather look at the chocolate induce diahria  brown of the gdm all day.

---

### Post by VMC on 2009-12-26
> **ranch hand said:**
> OK, that was fun.  Where in flinderation are these widgets?  All I can find is reference to "remote widgets" which sound intrusive.
Maybe you have them locked. Look either top right of screen or bottom panel bottom-right. They are inside that "cashew" looking thingy.

Here is what my screen looks like. I got rid of the blue.


Now if you look at my picture. The Widgets stuff is very top right or very bottom right. Click in there and you can add Widgets and other things.

---

### Post by ranch hand on 2009-12-26
I finally found the stuff.  I think KDE is a pain.  Probably a personality defect.  Just do not like it.

I like your wall paper.  Nice.

What is with the "desktop folder"?  Is it there just because someone was bored and thought the desktop needed MORE krap or what?  That is really ugly.

I know the version (what ever it is) that Mandriva 2009-1 has does not have that and the desktop looks much better for it.

---

### Post by ronacc on 2009-12-26
been meaning to leave a post but wanted to be back in KDE before I did to check a couple of things . You can change the default filemanager to konqueror ,left click K menu > settings>system settings > default applications > filemanager . also if you like dual pane file managers krusader is a good one for kde , very configureable ,its in the repos . To add widgets to the pannel use that "cashew" looking thing VMC mentioned , to add them to the desktop right click on a blank space on the DT and select add widgets , a bar will popup showing installed widgets double clicking starts them , in the top row > get new widgets brings up a selection where you can install from a local file or download new ones . also KDE-look.org is a good place to find widgets .You can get rid of that desktop folder , just right click on it and a toolbar will let you shut it off .
Now I've got a question for VMC , How did you change your wallpaper I can't find that setting ?

---

### Post by ranch hand on 2009-12-26
Right click on the desktop and click on the desktop something (last option  I think).   I hunted that down in a hurry.

I am on Jaunty on my main drive or I would check the actual option.  It is the obvious one.

---

### Post by ronacc on 2009-12-26
damn how did I miss that , must be encroaching senility , or enduring stupidity , I don't know which is worse :confused:

---

### Post by dagrump on 2009-12-26
Talk about a hijack, let's just wonder over to this...
Auto login yeah...
I've seen this on 3 boxes, it doesn't happen often, all 3 are gnome boxes. It's never happened back to back, just outa the blue!

---

### Post by ranch hand on 2009-12-26
Ah, embrace grumpy geezerhood.  I am real good at both of those.

Hey, you have to be good at something.

---

### Post by ronacc on 2009-12-26
I may be a geezer but I've got the worlds worst case of peter pan syndrome , gracefully my a**:lolflag:

---

### Post by dagrump on 2009-12-26
Ah WTH threads lost any way.
Ya call that a mid life crisis, & ya buy vette & chase women 20 years younger than you. Careful least you catch one, ya won't be able to afford another spin.

---

### Post by VMC on 2009-12-26
> **dagrump said:**
> Talk about a hijack, let's just wonder over to this...
Auto login yeah...
I've seen this on 3 boxes, it doesn't happen often, all 3 are gnome boxes. It's never happened back to back, just outa the blue!

Someones trying to hijack the hijacker. but if we must give it back...

I have never had any issues with auto login with Ubuntu Gnome.
Kubuntu on the other hand doesn't work. Or it works in parts.
I was able to get the login to show my user name and nothing in the password box, and then I just hit return and it went through.
I got it to work that way through:
"SystemSettings>Advance>loginManager>Convenience", then I messed around in that area for a while. Not a true auto login.

---

### Post by dagrump on 2009-12-27
That's way to deep to dig for a stupid login setting. That's kubuntu? 
Do you get a homely login screen too? Gnome is not attractive, but it would seem the issue pops up on the laptop more than the desktops. 
Guess I should just not turn it off.

---

### Post by ranch hand on 2009-12-27
if you do not turn it off, you will avoid any problem, you will also miss the FUN of being part of the solution.

We are in testing.  This is not a competition to see who can keep the sucker running.  The whole point is to break it now so it can be fixed.  The more hardware involved the better the fix.

At least half of the real problems with grub2 in the release of 9.10 was on hardware that I did not recognize as being mentioned in the testing forum.  The real bugs got pretty well handled for the hardware involved in testing.

The upshot is that we need bug reports from as many people (to get it verified) on as diverse hardware as we can get (to make sure it works on all hardware).

---

### Post by dagrump on 2009-12-27
Doesn't due much good if the only thing you can offer is "every so often my auto login don't work."
It will boot & auto login fine, & then,sometimes it asks for a password. 
I just type in my password, I really don't notice it till later & then I realize it happened.
Oh the stupid thing is already shutdown, it was in my way.

---

### Post by zika on 2009-12-27
> **sparker256 said:**
> I have my Ubuntu 10.04 32 bit set up to auto login and recently it stops  at the login screen. Other times it works correctly. My Ubuntu 9.10 does not have this behavior.

Bill Behavior like that happened, while testing karmic, or was it in Jaunty, when **preload** is installed. Did You, by any chance, install, or do You have that package installed?

---

### Post by sparker256 on 2009-12-27
> **zika said:**
> Behavior like that happened, while testing karmic, or was it in Jaunty, when **preload** is installed. Did You, by any chance, install, or do You have that package installed?
I just checked and not I do not have preload installed but I have not had the the problem in about 10 reboots so not sure what is going on.

Bill

---

### Post by VMC on 2009-12-27
> **dagrump said:**
> That's way to deep to dig for a stupid login setting. That's kubuntu? 
Do you get a homely login screen too? Gnome is not attractive, but it would seem the issue pops up on the laptop more than the desktops. 
Guess I should just not turn it off.

I get no login screen using Ubuntu Gnome. It goes straight to desktop. My auto login works.

Kubuntu is another issue. I'll have to check the OP's title again to see if this was specific for Ubuntu or just auto login in general.

---

### Post by ronacc on 2009-12-27
timed autologin shows the standard gnome (or kubuntu) login screen with blah blah will login in X(counts down) sec and a small analog clock that runs down , kubuntu's doesn't work yet though . I use timed login during a dev cycle to give myself a chance to change sessions  in case the desktop goes into one of its crashing loops or black screens .

---

### Post by ranch hand on 2009-12-27
The OP was speaking of Ubuntu.  This is weird in Kubuntu and I did some research to make sure it was KDM and was going to log in this morning and file a bug.

Didn't do it.  Logged in last night before shutting this drive down and it went fine, auto login worked even.  This morning it will not boot at all and I couldn't get x to start through recovery either.  I will try later.

---

### Post by ronacc on 2009-12-27
hmm seing your post I loggged out of gnome and rebooted into Kubuntu , I had updated last night but not rebooted kubuntu ,I went straight back to Gnome to get boinc and my torrents going again . Kubuntu booted ok but still no autologin for me I updated again and only got 2 updates kubuntu usplash and kubuntu defaults either of which looked like it could cause problems but I rebooted again ok , try updating from console or editing your xorg.conf (if you have one) to use vesa .

---

### Post by ranch hand on 2009-12-27
Wow, I just got back to Ubuntu to get my boinc going instead of fighting with Kubuntu and read your post.

I did not have an xorg. conf file.  I had a xorg.conf.failsafe file that I pulled up in gedit from here and saved as xorg.conf.  I called for vesa.  Didn't work.

I think that if I had login required I may be able to get into the system under some other option, those only possible if you have the login page.  As I do not have a clue as to how to change that from the CLI, I am giving up.  I do not like KDE anyway.

This is one of the reasons that I never use auto login.

I think filing a bug in Kubuntu is the same as in Ubuntu - "ubuntu-bug kdm" should do the trick.  But there does not seem to be a lot of interest in filing by people that actually run the bugger so I don't care either.

I can install some thing useful on those partitions now.

---

### Post by VMC on 2009-12-27
> **ranch hand said:**
> ...I think filing a bug in Kubuntu is the same as in Ubuntu - "ubuntu-bug kdm" should do the trick.  But there does not seem to be a lot of interest in filing by people that actually run the bugger so I don't care either.Thanks, but I got this weird error from terminal before going to bug report:

```
$ ubuntu-bug kdm
kfmclient(1909)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-vmc/ksycoca4"
: Fatal IO error: client killed

```

Regardless, I was sent to the LP to file a bug. There were several about no auto login, so I choose [#495057]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/495057") and clicked, "It affects me too".

---

### Post by caryb on 2009-12-27
Thanks for the great Idea lads! I have this problem with Kubuntu where you have to login twice, (have bug where it fails the 1st login) by using the autologin feature it fails the autologin then I login as usual:lolflag: 


BTW I guess being a security Nazi I don't like machines that autologin but I have made this exception as I know it will fail the 1st attempt.


Cary

---

### Post by ronacc on 2009-12-27
added my metoo to one of the autologin bugs , I have a couple of other I'd like to report but they occur during shutdown and if I click on report bug it tells me not enough info to report and then shuts down not sending me to LP. I get the samething without the shutdown (not enough info to report) if I click on the crash report icon during a session and try to report a crash , mabye has to do with VMC's  ksycoca4 error . I don't like this new bug report system , If you try to file a report manualy it just sends you back to use ubutnu bug . It may cut down on bad reports and dupes but it also makes it hard to report legitimate bugs if ubuntu bug fails for some reason , they need an override button .

@ Cary theres a bug open on that login twice add your metoo .

---

### Post by jerrylamos on 2009-12-28
"Auto Login" does NOT work on this IBM ThinkCentre A30 with i845 intel video graphics.  I get a black screen with cursor.  Launchpad bug #499102.

XFCE4 works auto login.  Gnome doesn't.

LXDE works auto login.  Gnome doesn't.

So I turned off auto login to get Gnome to work.

I'm the only one that ever uses this computer, and autologin would save some time since with Lucid battles I reboot frequently.

?

Jerry

---

