---
title: "xorg-edgers questions"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-30
I have never used a ppa for anything.  I have too many 10.04 versions that are not doing anything useful.  I always just use the generic drivers as they seem to do every thing I want.

Because of the above, I think it is time for more education.

I have looked at the LP page for xorg-edgers.  Might as well be written in Martian as far as what I get out of it.

This box has a Radeon HD 2400 PRO card in it.  There is an ATI driver on their page and I have tried it under 9.04.

What on earth am I supposed to try from the xorg-edgers folks?  There seems to be about a million choices (at least in my staggered brain when I look at them) and none of them seem to be anything really new 9at least the ones that I understand).

I have a victim OS picked out.  I do not use it much for anything so trying desktop effects (that I set at "none" when I use an OS) will not piss me off.  I just need some dirrection as to what to try.

---

### Post by zika on 2009-12-30
> **ranch hand said:**
> I have never used a ppa for anything.  I have too many 10.04 versions that are not doing anything useful.  I always just use the generic drivers as they seem to do every thing I want.

Because of the above, I think it is time for more education.

I have looked at the LP page for xorg-edgers.  Might as well be written in Martian as far as what I get out of it.

This box has a Radeon HD 2400 PRO card in it.  There is an ATI driver on their page and I have tried it under 9.04.

What on earth am I supposed to try from the xorg-edgers folks?  There seems to be about a million choices (at least in my staggered brain when I look at them) and none of them seem to be anything really new 9at least the ones that I understand).

I have a victim OS picked out.  I do not use it much for anything so trying desktop effects (that I set at "none" when I use an OS) will not piss me off.  I just need some dirrection as to what to try.```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude upgrade
```
That's it. Enjoy!

---

### Post by ronacc on 2009-12-30
PPAs can be a valuable asset I usualy have several added ,they add availability of apps not in the regular repos and also later versions/special builds of apps that are . The maintainers range from ubuntu devs providing builds of later versions of default apps that are beyond the scope of the current blueprint, to normal humans even as you and I providing non-included apps or niche builds .

note: if you are running something from a ppa and find a bug ,file it through the ppa , not the regular channel .

---

### Post by ranch hand on 2009-12-30
I guess I better just do that and see what comes up.

They seem to list  an awful lot of stuff, maybe that is not what you get.

---

### Post by ktp on 2009-12-30
I am sure you already know this...but PPA is "daily" upstream builds of X stack.  If you are going to play with this, you'll be better of getting everything from PPA else X might not work.

---

### Post by ranch hand on 2009-12-30
> **ktp said:**
> I am sure you already know this...but PPA is "daily" upstream builds of X stack.  If you are going to play with this, you'll be better of getting everything from PPA else X might not work.
I am not at all sure what you are talking about.

I did follow this procedure;
> 
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude upgrade

from zika.

Seemed to work.

Booted to the OS and the only result seems to be a scrambling effect on my lower panel.

I will log in later and see what else.

This card seems to be a real problem.  Lucky for me that I do not like the desktop effects and am happy with the generic driver.

The results here are at least not disabling (I think).

Well like I said that OS really is a throw away anyway.  I have those partitions set aside for ISO testing so it will be formated and reinstalled with whatever comes up next.

---

### Post by zika on 2009-12-30
> **ranch hand said:**
> I am not at all sure what you are talking about.

I did follow this procedure;

from zika.

Seemed to work.

Booted to the OS and the only result seems to be a scrambling effect on my lower panel.

I will log in later and see what else.

This card seems to be a real problem.  Lucky for me that I do not like the desktop effects and am happy with the generic driver.

The results here are at least not disabling (I think).

Well like I said that OS really is a throw away anyway.  I have those partitions set aside for ISO testing so it will be formated and reinstalled with whatever comes up next.You can always use ppa-purge script from xorg-edgers to restore the state before You applied xorg-edgers (or, whatever ppa You used)...

---

### Post by ktp on 2009-12-30
> **ranch hand said:**
> I am not at all sure what you are talking about.

I did follow this procedure;

from zika.

OK...think of it as build of entire X stack, including the drivers, for the latest code.  This way you can take the latest code for "drive" and might be broken from day to day (which I personally have not see...might have bugs but what code does not).

To be safe, when installing anything from this PPA, you should upgrade everything...not just say ati drivers because that might not work with X server you have.  Also I said upgrade because most likely there isn't any package on there that you don't already have installed.  So what you did (as zika said) is what should be done.  

As for noticing the difference, you might not see must (which is good, meaning no broken system) since PPA said:

> == New in Lucid ==

Xorg 7.5/xserver master (1.8 to be) with HAL removed. This is *not* installable on karmic, please update to lucid if you want to use it.

This was good PPA (if you like latest code with few bugs) to use in Jaunty for ati driver because rewrite of the open source ati driver and 3D support.  It is still good if you want the latest updated X.

---

### Post by autora on 2009-12-30
> **zika said:**
> You can always use ppa-purge script from xorg-edgers to restore the state before You applied xorg-edgers (or, whatever ppa You used)...

yea, make sure you have ppa-purge installed first

---

### Post by ktp on 2009-12-30
> **autora said:**
> yea, make sure you have ppa-purge installed first

ppa-purge is great to have.

---

### Post by zika on 2009-12-30
> **autora said:**
> yea, make sure you have ppa-purge installed firstIt's a script. You do not install it and You can use it   post-modum.

---

### Post by autora on 2009-12-30
> **zika said:**
> It's a script. You do not install it and You can use it   post-modum.

ummm yea i can? i installed it through kpackage. i can uninstall it too if i want. amazing huh?

---

### Post by Eestlane on 2009-12-30
Just to mention I'm having quite a lot of problems, though the reason might also be the gtk ppa or dist-upgrade. However, KMS, which is probably from edgers ppa, doesn't seem to work well with my Radeon 9800 Pro, that's why I use nomodeset as boot argument to disable KMS.

---

### Post by zika on 2009-12-30
> **autora said:**
> ummm yea i can? i installed it through kpackage. i can uninstall it too if i want. amazing huh?
```
~/stuff$ head ppa-purge
#!/bin/sh
# A script to remove all packages in a PPA and revert back to the normal
# distribution ones.
#
# AUTHORS: Robert Hooker (Sarvatt), Tormod Volden
#
# History:
# v0.1   - 2009-07-28: Initial Revision.
# v0.2   - 2009-07-29: Add warnings, do not remove ppa-purge package
# v0.2.2 - 2009-08-05: Fix command option parsing errors
```
```
~/stuff$ ls ppa* -al
-rwxr-xr-x 1 zika zika  3937 2009-12-05 20:13 ppa-purge
-rw-r--r-- 1 zika zika 15919 2009-12-05 22:38 ppa-purge_0.2.6.tar.gz
```

---

### Post by autora on 2009-12-30
> **zika said:**
> ```
~/stuff$ head ppa-purge
#!/bin/sh
# A script to remove all packages in a PPA and revert back to the normal
# distribution ones.
#
# AUTHORS: Robert Hooker (Sarvatt), Tormod Volden
#
# History:
# v0.1   - 2009-07-28: Initial Revision.
# v0.2   - 2009-07-29: Add warnings, do not remove ppa-purge package
# v0.2.2 - 2009-08-05: Fix command option parsing errors
```
```
~/stuff$ ls ppa* -al
-rwxr-xr-x 1 zika zika  3937 2009-12-05 20:13 ppa-purge
-rw-r--r-- 1 zika zika 15919 2009-12-05 22:38 ppa-purge_0.2.6.tar.gz
```

your point being? i can still install n' uninstall it through kpackage/synaptic. and to quote the xorg edgers ppa

> To revert to official packages, you can **install** the **ppa-purge package** and run "sudo ppa-purge xorg-edgers".

---

### Post by ranch hand on 2009-12-30
I do not feel that removing anything is called for.

I will keep upgrading the OS and it may get better.   I now have 7 10.04 based OS'.  I am on the one that I use for my day time production machine.  I very rarely fool with the one I put this "edgers" stuff on.

I hit all the versions once a day to make sure that the updates don't screw anything before I update this one.  There are really only 3 that are accurate for forcasting the performance on this OS but I check them all as the others are doing other things (like the "edgers" thing and the new OOo on another one and a Lizard upgraded from the 9.10 minimal install).

I also have Lxde on one (with Gnome).

So, this is just another test/demonstration of what something can do for me.  So far, all of 10 minutes on the OS, it is not real promising.

I am not sure at all when the ISO test for 8.04.4 will be but I would think that it would be after A2.  That means that xorg-edgers has quite a bit of time to be fooled with.  I need to do some reading to find out what would be considered a bug even so I better give it some time.

---

### Post by zika on 2009-12-30
> **autora said:**
> your point being? i can still install n' uninstall it through kpackage/synaptic. and to quote the xorg edgers ppaNo point, just answering Your question. Sorry if I did not properly understand You.

---

### Post by zika on 2009-12-30
> **autora said:**
> ummm yea i can? i installed it through kpackage. i can uninstall it too if i want. amazing huh?I understood this as a question. Sorry.

---

### Post by autora on 2009-12-30
> **zika said:**
> I understood this as a question. Sorry.

np man ;]

---

### Post by ranch hand on 2009-12-30
Good things come to those who wait.

I did not have a long wait.  Logged in to this bugger with the "edgers" stuff on it and there were some updates available.  Got them.  Rebooted.  Have a bottom bar that is not scrambled.  This is nice.

Maybe some of you can tell me if this is normal.  This occures no matter what I am using for a driver.

If I have the "visual effects" set for anything but "none" I can not drag a window from one workspace to another.  I have to click on the title bar an move the sucker that way.  Then I get this silly bunch of rectangles that flash on the screen.

This is why I am happy with the generic driver and NO effects.  This other behavior is just silly and slow and gets on my thungas.  I would like one OS to do these things just because it seems to be popular.  I, personally, prefer turds in the punch bowl.

---

### Post by ronacc on 2009-12-30
I use compiz when I have special effects enabled because it seems to give better control over the effects , I'm not even sure how to set them in metacity although I know there is a box you can check in gconf-editor>apps>metacity>general to turn compositing on . You may need to adjust your effects some to get everything working right .

---

### Post by ranch hand on 2009-12-30
I am on my night time OS right now but will check that stuff tomorrow on the Lizard.

Here on 9.04 there does not seem to be anything that will improve things in the gconf-editor.  It does look like you can make it more obnoxious.  I will look into it.

I should probably "enable" compiz and see what damage that does too.  I have actually seen that in action and can't for the life of me see why people put up with that, let alone like it.  I must have a BIG character flaw.

---

### Post by ronacc on 2009-12-31
I find some of the effects obnoxious too but atleast with compiz they are easy to switch on and off . I detest the dammn wobbly windows and turn that off first thing. Also you need some kind of compositing to run some things like some of the docks and gnome-do .A couple of things you wnat to add that arent drug in by the compiz defaults are fusion-icon it gives you a toolbar Icon that lets you switch it on and off eaisly and gives quick access to the settings and also install compiz-config-settings-manager , that gives you full fine grained control over the settings and I like emerald for a theme manager.

---

### Post by ranch hand on 2009-12-31
> **ronacc said:**
> I find some of the effects obnoxious too but atleast with compiz they are easy to switch on and off . I detest the dammn wobbly windows and turn that off first thing. Also you need some kind of compositing to run some things like some of the docks and gnome-do .A couple of things you wnat to add that arent drug in by the compiz defaults are fusion-icon it gives you a toolbar Icon that lets you switch it on and off eaisly and gives quick access to the settings and also install compiz-config-settings-manager , that gives you full fine grained control over the settings and I like emerald for a theme manager.
Thank you for that.

I am back on the Lizard and just ran all my chroot updates.  When I updated that OS I did install the "manager", have had it before.  Never knew about the "fusion-icon" and completely forgot to get "emerald" (had it before too).

I better go back and do that.

I am leaving here pretty soon to cut some fire wood and will be fooling with the "edgers" OS when I get back and have the stuff split and stacked.  Then I see how it works.

---

### Post by mc4man on 2009-12-31
> of me see why people put up with that, let alone like it

some people like to have fancy desktops, myself only want the rotate cube.
Typically have 4 or 5 desktops and flipping them with the scroll-wheel on desktop is an excellent thing ( or scroll area on laptop though the default duration (for slide wall) or acceleration (rotate cube) is too short for laptops.
(scroll on desktop has been disabled by default

If you do enable effects, as previously mentioned you should install cssm or you'll be subject to someone's idea of what effects should be enabled and the default settings ( including some display settings and or workarounds that can have a positive or negative effect.

---

### Post by ranch hand on 2009-12-31
I have just checked on that OS and compiz has, so far, only rescrambled my lower panel.  I had to add the icon manually and the compiz management stuff does not work at all.  Emerald only partially.

I have the effects set on "extra" in appearance, had it on normal but changed to see if it made a difference, if so not noticable.

With compiz enabled, this is an improvement with this card.  It should just freeze the system solid.

I am glad it is on an OS I do not use for anything but playing around with.  The lack of being able to use the workstation applet the way I like to is VERY bad.  The whole thing seems to me to be a real pain and the looks suck.

I have no idea what is wrong, when enlarging the terminal out put for synaptic for instance, with just enlarging it.  Oh no we can't do that.  We must have transparent purple (ghastly shade at that) "ghost" and then have the enlargement when you release the mouse.  Gee let us use resources to get nausiating colors.

I can't see ever using this crap even if I get a box that will do it.

I keep hoping that it will work so that I can show it to someone else.  All the fans of this seem to think it is a selling point.  I am glad it is not default or I would not be using Ubuntu today.  If I had to figure out how to kill this, when I started I surely would have found some distro that did not insist that I use it.

I only mention the default thing because I have seen this advocated here and there on the web (I think on these forums somewhere too).  This is a bad idea.

---

### Post by ronacc on 2009-12-31
I guess compiz just don't like your card , IIRC you have an ati card and I can't help with that , all I've ever used is nvidia . I have never run into any of the artifacts you mention.

---

### Post by BwackNinja on 2009-12-31
> **ranch hand said:**
> I have just checked on that OS and compiz has, so far, only rescrambled my lower panel.  I had to add the icon manually and the compiz management stuff does not work at all.  Emerald only partially.

I have the effects set on "extra" in appearance, had it on normal but changed to see if it made a difference, if so not noticable.

With compiz enabled, this is an improvement with this card.  It should just freeze the system solid.

I am glad it is on an OS I do not use for anything but playing around with.  The lack of being able to use the workstation applet the way I like to is VERY bad.  The whole thing seems to me to be a real pain and the looks suck.

I have no idea what is wrong, when enlarging the terminal out put for synaptic for instance, with just enlarging it.  Oh no we can't do that.  We must have transparent purple (ghastly shade at that) "ghost" and then have the enlargement when you release the mouse.  Gee let us use resources to get nausiating colors.

I can't see ever using this crap even if I get a box that will do it.

I keep hoping that it will work so that I can show it to someone else.  All the fans of this seem to think it is a selling point.  I am glad it is not default or I would not be using Ubuntu today.  If I had to figure out how to kill this, when I started I surely would have found some distro that did not insist that I use it.

I only mention the default thing because I have seen this advocated here and there on the web (I think on these forums somewhere too).  This is a bad idea.

If nothing else, I'd agree that the default color for resize in compiz is bad. Actually, the default animation for resize is annoying.

---

### Post by ranch hand on 2009-12-31
I know that therre are folks on this forum who have said that they had compiz working with an ATI card.

I am just lucky enough to have the Radeon HD 2400 PRO which appears to be one of the worst supported all around.  There is a driver on their website and it does work.   I installed it on the 9.04 I use the most and couldn't hack the crap and got rid of it but I do not think that it worked a lot better than this.

How do you set the irq switches on Ubuntu?  The last time I tried that OS I got some message that something there was not right and I thought I know how to get in so I didn't write down the message.
Couldn't find it and will have to find out how to get in and then recreate the situation to get the message back.  It did have to do with compiz and was probably why I had trouble getting it up in the first place.

I would really like to get this to work as well as it can.  I think the graphics are great on the default.  If, for instance, movie play back could be better that would be fantasticly good.  It looks great on my monitor but I am not sure how it would look on a larger screen if I tried going through the TV (monitor is the Dell 1440x900 19").

---

### Post by ronacc on 2009-12-31
like I said I know nothing about ati cards but if you want to find out about how it will look on your tv , if it is a flatscreen either lcd or plasma it should have a vga input just plug your vga cable in and bootup and use your tv remote to select the vga or rgb input (could be labeled as either ).
happy new year

---

### Post by ranch hand on 2009-12-31
> **ronacc said:**
> like I said I know nothing about ati cards but if you want to find out about how it will look on your tv , if it is a flatscreen either lcd or plasma it should have a vga input just plug your vga cable in and bootup and use your tv remote to select the vga or rgb input (could be labeled as either ).
happy new year
As far as the Happy New Year goes;

As my dad used to say;

"Same to you and yours and see how you like it".

I'll just say "same to you".

Judging  by what we have seen so far, the Lounge Lizard is doing its part to make this a good year.

---

### Post by ranch hand on 2010-01-01
I thought some may be interested in a screen shot.

---

### Post by ronacc on 2010-01-01
I see your corrupted bottom panel, which window decorator are you using ? gtk or emerald ? which ever it is does the other one make any difference ?

---

### Post by VMC on 2010-01-01
> **ranch hand said:**
> I thought some may be interested in a screen shot.

Looks good. Next time on the screen shot, use the "grab the current window" and you won't have the screen shot itself in the picture.

---

### Post by ranch hand on 2010-01-01
ronacc
Right now it is emerald.  I switched to it to see if it would do better.  The panel looks just like it does with gtk.

One interesting other thing is that no matter how set compiz, on any version of Ubuntu (8.10, 9.04, 9.10 or now the Lizard), I get wobbly windows any way.  Even if desktop effects are set at none.  Very entertaining for about the first 3 times you see it.

There is no way to get into the irq settings in my bios on this box.  I thought that was universal although I have never had a box this new.

VMC
I thought about doing another shot after I saw what I had done but it really didn't matter as all that I really wanted was that bottom panel.

That seems to be the only thing that compiz does for me.

I don't stay on there long because boinc is on this install and I really do not like the desktop effects.

---

### Post by ronacc on 2010-01-01
you should be able to switch off wobbly windows with compizconfig-settings-manager ( in terminal  ccsm  or rt click the fusion icon > settings manager  its the last item in the efffects section , I'm in kubuntu on that box right now zsyncing I'll root around in gconf-editor when I get back to gnome to see if I can find a seting there to kill it, I hate the wobblies too .

---

### Post by ranch hand on 2010-01-01
It is off in compiz manager.  Was off when it was installed (I thought it  was on by default).

---

### Post by ronacc on 2010-01-01
hmm I find that strange , it has been default on any time I have installed compiz , its the very first thing I turn off . Obviously something is weird about your install.I wonder if it has to do with the xorg-edgers stuff.I'm totaly lost about radeon cards , I suppose I should stuff one in one of my boxes to torture myself when I've been bad .:lolflag:

---

### Post by ranch hand on 2010-01-01
Well I did have that irq message that I have never figured out as I can't seem to get at them.  Other than that I would say your plan has a lot to said for it.

I will admit that the install is not good.  The only way I got to the "manager" at all was to add the icon to the startup apps list.  I installed the "manager" and assumed it would, as in the past, show up in the menu but it did not.  Only got errors when trying to get it up in terminal, with and without "sudo".

The bugger just doesn't work.

I know that all ATI cards are not as bad as mine and there are some worse.  This one at least does what I want it too.  It would, however, be nice to get it to do this stuff even if I don't want it.

My main question now is if I should file a bug on this with the "edgers" folks or not.  They are turning out updates everyday (so far) and I am not sure that filing is the right thing to do seeing how I can really give no information as I do not really know what this stuff is supposed to do, just what it is doing on my hardware.

---

### Post by ronacc on 2010-01-01
ccsm doesn't show up in the menu you have to access it via the terminal or the fusion icon .what kind of mobo is it that the bios wont let you change the irq's ?I want to know what not to buy:P .When I build my boxes I use MSI or Gigabyte mobos I've always had good luck with them . My gigabyte mobo died about one week before the wty ran out and they repaired it and shipped it back no questions asked within 10 days , none of my MSIs have failed . Your best way out of your graphics problems may be to get an Nvidia card (I am assuming it's a desktop and you can install a video card ) unless you are into heavy gaming you don't need the high $$$ ones . I have a 7300 le in my multimedia box and it drives a monitor and 42 in lcd tv just fine .

---

### Post by ranch hand on 2010-01-01
I am embarrassed to admit that I do not know how to get the mobo info off the machine.  It is probably in the book but we did move and a bunch of stuff is still in limbo some where (it is not in the horse trailer).

It is whatever Dell uses to put this together.  I do not think that anyone would use there mobo to build a box.  They have too much stuff that has weird plugs so you have to buy parts from them.

If there is a way to access the irq I sure can't find it.  I have no edea what they were thinking when that was designed.

It is probably just as well that I couldn't get to it.  I was going to try changing what ever it was that message was about.  Probably would have had t ogo back and change it all back for my other 15 OS' on this box to work right.  I do not think that I want to switch that stuff around just to make that OS happy.

I am going to get on the Dell Ubuntu Mailing list and ask those guys about the irq thing.  I have helped them out enough so I guess it is their turn.

---

### Post by mc4man on 2010-01-01
> to get the mobo info off the machine.

you can try this for basic info ( if that's what you had in mind?
```

sudo lshw -html > hardware.html
```

Will be in home, sectioned up for easy reading ( vs. terminal output

---

### Post by ronacc on 2010-01-01
there are 3 apps in synaptic that you can install to give you hardware info about your machine , hwinfo , hardinfo and sysinfo . all 3 run from terminal , hwinfo prints ALOT of info to the term about your HDW you can cut and paste it to a text file for reference , its supposed to output to a log file for you but I have not been able to make that work but cut and paste does . hardinfo and sysinfo open up windows for a gui view . hardinfo gives more than sysinfo but all 3 are usefull hwinfo gives the most but in a less convenient form .

---

### Post by ranch hand on 2010-01-01
> **mc4man said:**
> you can try this for basic info ( if that's what you had in mind?
```

sudo lshw -html > hardware.html
```Will be in home, sectioned up for easy reading ( vs. terminal output
The lshw was fine and sudo lshw even better.

I tried the whole command last and it was strange.  Can't open it in FF but did fine in Screem or  Gedit.  A clip;
> 
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta name="generator"  content="lshw-B.02.13">
<style type="text/css">
  .first {font-weight: bold; margin-left: none; padding-right: 1em;vertical-align: top; }
  .second {padding-left: 1em; width: 100%; vertical-align: center; }
  .id {font-family: monospace;}
  .indented {margin-left: 2em; border-left: dotted thin #dde; padding-bottom: 1em; }
  .node {border: solid thin #ffcc66; padding: 1em; background: #ffffcc; }
  .node-unclaimed {border: dotted thin #c3c3c3; padding: 1em; background: #fafafa; }
  .node-disabled {border: solid thin #f55; padding: 1em; background: #fee; }
</style>
<title>jak-desktop</title>
</head>
<body>
<div class="indented">
<table width="100%" class="node" summary="attributes of jak-desktop">
 <thead><tr><td class="first">id:</td><td class="second"><div class="id">jak-desktop</div></td></tr></thead>
 <tbody>
    <tr><td class="first">description: </td><td class="second">Tower Computer</td></tr>
    <tr><td class="first">product: </td><td class="second">Dell XPS420</td></tr>
    <tr><td class="first">vendor: </td><td class="second">Dell Inc.</td></tr>
    <tr><td class="first">serial: </td><td class="second">FSSRDG1</td></tr>
    <tr><td class="first">width: </td><td class="second">64 bits</td></tr>
    <tr><td class="first">capabilities: </td><td class="second">smbios-2.5 dmi-2.5 vsyscall64 vsyscall32</td></tr>
    <tr><td class="first">configuration:</td><td class="second"><table summary="configuration of jak-desktop"><tr><td class="sub-first"> administrator_password</td><td>=</td><td>enabled</td></tr><tr><td class="sub-first"> boot</td><td>=</td><td>normal</td></tr><tr><td class="sub-first"> chassis</td><td>=</td><td>tower</td></tr><tr><td class="sub-first"> power-on_password</td><td>=</td><td>enabled</td></tr><tr><td class="sub-first"> uuid</td><td>=</td><td>44454C4C-5300-1053-8052-C6C04F444731</td></tr></table></td></tr>
 </tbody></table></div>

Now this was in 9.04 so it may be different in 10.04.

I copied the terminal out put to gedit and it is GREAT.  Some of that info was not even in the fine print in the manual.

Thanks a bunch.

---

### Post by mc4man on 2010-01-01
If you do the .html it should open in firefox, only decent way to read - see screen

you could just do a plain sudo lshw ( make sure your terminal can scroll back enough lines (terminal -> edit ->  profile prefs. -> scrolling - I think there's a max no matter what you set, I go 3500

---

### Post by ranch hand on 2010-01-01
ronacc
> 
       description: Motherboard
       product: 0TP406
       vendor: Dell Inc.

I will check those other packages too.

mc4man
the quote in my last post was from the hardware.html file generated by;
```

[FONT=monospace]sudo lshw -html > hardware.html

```
I have the same type of info that you have on your shot from copying to gedit from the terminal.

I don't care where it is as long as I have a way to get the info, the more the merrier.
[/FONT]

---

### Post by ronacc on 2010-01-01
hmm I tried the cmd ```
sudo lshw -html > hardware.html
``` and the output opens in FF ok for me ,see screenshot , I think something is wonky with your install .

---

### Post by mc4man on 2010-01-01
> I have the same type of info that you have on your shot from copying to gedit from the terminal.

I can see it now - picking thru the html code

Did you look in your home folder folder for hardware.html?

Ot - you had me going awhile on karmic testing with your names - was searching for a 'lounge lizard' release, ect. *think I finally caught on..

only found an old [koala and lizard]("http://www.myrtlebeachwebdesign.com/koala-lizard.html")

---

### Post by ranch hand on 2010-01-02
> **ronacc said:**
> hmm I tried the cmd ```
sudo lshw -html > hardware.html
``` and the output opens in FF ok for me ,see screenshot , I think something is wonky with your install .
I have not tried that on any 10.04 install yet.  I have only tried it here on a fairly tweeked but very stable 9.04 that I run at night because I can trust it not to crash at all.

The command built a file in the home folder " hardware.html"  -  that is copy/pasted from the results of "ls /home/jak" on this 9.04 respin.  The file will open in gedit or screem but not FF.

I did get a clean copy from terminal with just "sudo lshw"

One thing that I can tell you is that "hardinfo" is one of the default tools in this respin.  That is really kind of nice.

I will have t otry the other 2 as the are not installed.  Don't know if I will do it here or over on one of the test OS'.

mc4man
What I posted is from the hardware.html file.

The good info I just copied from terminal (I go back 5000+ lines) to gedit and saved it.  A lot of real nice info on your box.  I love it.

I will be trying it on one of my Lizards and maybe a Kinky tomorrow just to see if it works better than on this 9.04 respin.  I also have an install of 9.10 minimal upgraded to 10.04 with the gnome desktop on it.  May try it there too as things really do act different without all the baggage brought on board with the ubuntu desktop.  Don't know if I like it or not yet but it is a lot smaller even with OOo and gimp installed.

I don't think much of the names "they" come up with.  It is my box I ca ncall them anything I want.  This is why, when I really want to be clear, I use 10.04 or 9.04 rather than Horny Horse (8.04).  I am looking forward to Mangy Moose.

---

### Post by mc4man on 2010-01-02
Tis really unimportant but little mysteries 'nag' at me 
what would happen if you did this (if inclined
```
sudo lshw -html > hardware.html && firefox hardware.html
```

---

### Post by ranch hand on 2010-01-02
> **mc4man said:**
> Tis really unimportant but little mysteries 'nag' at me 
what would happen if you did this (if inclined
```
sudo lshw -html > hardware.html && firefox hardware.html
```
Well the devil and all his helpers.  I just switched to my daytime OS.  I will do that this evening on the 9.04.

I am going to be trying the thing out on this drive directly and if I have the same results as I did over there I will try it here.

I am just getting dressed and the fires going in their daytime mode (warmer), switching over to testing and checking the forums.

Will report.

---

### Post by ronacc on 2010-01-02
I am rather puzzled as to why FF wont open the hardware.html file when gedit will . Does it give you any message when you open FF and then use file>open file  to try to open it ? have you tried a different browser ? I tried Opera and epiphany and they both also opened the file that LSHW wrote for me . For me when I deliberately try to open a file that FF can't understand it pops up a box identifying the file type and asking what to do with it .

---

### Post by sparker256 on 2010-01-02
> **ranch hand said:**
> I thought some may be interested in a screen shot.

Does your select area to grab work on Lucid? Mine does not.

Bill

---

### Post by ronacc on 2010-01-02
I know you directed the question at RanchHand but thought I would chime in , grab works ok for me on lucid amd64 , see screenshot .

---

### Post by sparker256 on 2010-01-02
> **ronacc said:**
> I know you directed the question at RanchHand but thought I would chime in , grab works ok for me on lucid amd64 , see screenshot .

Thanks for the reply. Mine is working but the selected area is not marked. On Karmic it is marked. Thanks again.
Bill

---

### Post by VMC on 2010-01-02
Well you guys got me interested, since I only use chrome, so I tried

```
sudo lshw -html >abc.html

```
and it works for chrome. Interesting how two of id's are in red.

---

### Post by ranch hand on 2010-01-02
> **ronacc said:**
> I am rather puzzled as to why FF wont open the hardware.html file when gedit will . Does it give you any message when you open FF and then use file>open file  to try to open it ? have you tried a different browser ? I tried Opera and epiphany and they both also opened the file that LSHW wrote for me . For me when I deliberately try to open a file that FF can't understand it pops up a box identifying the file type and asking what to do with it .
I am here on the test platform and tried this on my daytime production OS here and it works as advertised.  Opens very nicely in FF.

As for when it did not open on my "nighttime" production OS (9.04 respin), all I got was a new tab that was blank, no messages, no indication of error.  I do not have another browser installed there and I doubt that I am going to do it due to not wanting to fill the partition with more stuff I don't use.

Here on 10.04 the results look very nice but I think I prefer the terminal output saved to gedit.  There is something, I have no real idea what, that I have never liked about opening files with a browser.

I also tried the apps you mentioned this morning on this platform along with this.  There are some interesting things came out of that.

"sudo lshw -html > hardware.html" does not work for me in chroot.  This could be because I am not doing something I should be.

"hardinfo" and "hwinfo" both work great in chroot.

"sysinfo" does not work in chroot although it tries.  I actually get a flash of frame before it disappears.  I get this from the terminal;
> 
nUhandled Exception: GLib.GException: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-jPK04K4FPK: Connection refused)
  at GConf.Client.Get (System.String key) [0x00000] 
  at Sysinfo.Sysinfo.UpdateFromGConf () [0x00000] 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] 
  at Sysinfo.Sysinfo.Main (System.String[] args) [0x00000] 


I like all of these.  They give a lot of info all at once in one place.  I need to play with them more to find the one I like the best.  One, at least, is going to become a standard feature on future installs.

I have not installed any of them on this OS as I have not tried the ones I did install them on live.  I need to check on sysinfo booted in anyway to make sure it works.

---

### Post by ranch hand on 2010-01-02
> **sparker256 said:**
> Does your select area to grab work on Lucid? Mine does not.

Bill
Works fine for me to.  It out lines the area but that does not persist.  Takes the shot very well.  Nice clean look the way this works.

---

### Post by sparker256 on 2010-01-02
> **ranch hand said:**
> Works fine for me to.  It out lines the area but that does not persist.  Takes the shot very well.  Nice clean look the way this works.
My end result is fine but without the outline was not sure it was working. I am on Nvidia and might be the difference.

Thanks Bill

---

### Post by ronacc on 2010-01-02
I am on nvidia here also , the outline disappears when you release the LMB because it takes the SS at that instant ignoring any delay  .

---

### Post by mc4man on 2010-01-02
for the lshw then you'd probably be happiest with just plain
sudo lshw > hardware
a few other com. ( man lshw

Another interesting set of tools is the sysstat set, I use mpstat occasionally to output a log during encoding to check cpu core usage, ect.

---

### Post by ranch hand on 2010-01-02
I have been studying the man page on this bugger and there is a lot of things that are not right.  I do not know if this is due to changes in lshw or in the OS (primarily a lot of files that are not here that are listed on the man page).

I have to kind of go through man pages a piece at a time to get the gist  of what they are trying to tell me.  This one is neat.

The "> hardware" command is very nice.  The file is 27.2K and the html version is 105.2K.

---

### Post by jwssr on 2010-01-04
For getting hardware and software info plus some other tweaking....I found this on ubuntugeek..it is called ailurus.

In terminal (ilike byobu).

wget [http://ailurus.googlecode.com/files/ailurus_10.01-0revision1_all.deb](http://ailurus.googlecode.com/files/ailurus_10.01-0revision1_all.deb)

sudo dpkg -i ailurus_10.01-0revision1_all.deb


hope this works for you...

---

### Post by ranch hand on 2010-01-04
I didn't even look the sucker up to find out what it is.  I am just going to install it on one of my "throw away" Lizards and see what it does.

Thanks a bunch.

---

### Post by ronacc on 2010-01-04
down here in the swamps I have sunk myself in a pit of aligators up to my butt .something took out my xserver ( the whole 9 yards ) and I borked things even worse trying to fix it ,can't even boot revovery now ,tried to reinstall from jan 3 daily and partman failed specifing manual partions , d/l'd jan 4 daily, same thing , seriously considering a hammer .going to try chroot and fiddle around some more then d/l the alternate and try that .

---

### Post by ranch hand on 2010-01-04
> **ronacc said:**
> down here in the swamps I have sunk myself in a pit of aligators up to my butt .something took out my xserver ( the whole 9 yards ) and I borked things even worse trying to fix it ,can't even boot revovery now ,tried to reinstall from jan 3 daily and partman failed specifing manual partions , d/l'd jan 4 daily, same thing , seriously considering a hammer .going to try chroot and fiddle around some more then d/l the alternate and try that .
Good job.  No sense screwing something without REALLY screwing it.

---

### Post by VMC on 2010-01-04
> **ronacc said:**
> down here in the swamps I have sunk myself in a pit of aligators up to my butt .something took out my xserver ( the whole 9 yards ) and I borked things even worse trying to fix it ,can't even boot revovery now ,tried to reinstall from jan 3 daily and partman failed specifing manual partions , d/l'd jan 4 daily, same thing , seriously considering a hammer .going to try chroot and fiddle around some more then d/l the alternate and try that .

Every time I remember or think of backups, its right after I do something like this. Thankfully its no on your production OS.

---

### Post by ronacc on 2010-01-05
no its a test box ,I learned not to test on my production box , not even on a separate drive . I just learned something else , currently there is no alternate of the daily lives , couldn't find my A1 disk , reinstalled from nov 28 09 live, 300+ mb of updates d/ling now , its past pumpkin time here I'll find out if it worked in the morning.
I've got a seperate /home so even my boinc survived .

---

### Post by ranch hand on 2010-01-05
You really have to wonder why some people do not have separate partitions.

---

### Post by VMC on 2010-01-05
> **ronacc said:**
> ... I just learned something else , currently there is no alternate of the daily lives , couldn't find my A1 disk , reinstalled from nov 28 09 live, 300+ mb of updates d/ling now , its past pumpkin time here I'll find out if it worked in the morning.
I've got a seperate /home so even my boinc survived .

Are you referring to this [daily-alternate]("http://cdimage.ubuntu.com/daily/current/")

---

### Post by ranch hand on 2010-01-05
Well, I do not know about this.  I am on the OS with "edgers" on it and both my panels, which were scrambled yesterday, are clear.

The compiz config manager even allowed me to do away with wobbly windows.

Very little else will do anything on the manager.  Click on unchecked boxs and they stay unchecked, checked boxes stay checked.

May not work real well but it sure looks better.

If it makes a difference I have the "desktop effects set on "extra".

---

### Post by ronacc on 2010-01-05
glad your acne finally cleared up:lolflag: , I have my install fully restored  and starangely enough I didn't have wobbly windows even before I installed compiz . at least you are getting some control over effects . you installed compizconfig-settings-manager and not simple-ccsm didn't you ? simple-ccsm is about worthless , they threw that in because they figured the average user was too stupid to use the real thing .

---

### Post by ranch hand on 2010-01-05
I have the full manager, didn't even know about the other one.  It did not install gracefully and has yet to show up if called from terminal.  The "icon" gets it up though (very slowly).

I think that I will reinstall all this stuff when A2 comes along.  The OS I am using is only there for ISO  testing so it will be wiped at that point for a clean install.  Maybe when I installed it was a bad time for integrating with my system.

I am glad your system is working again.  The little buggers can really get on your thungus.

---

### Post by ronacc on 2010-01-05
when you start compizconfig-settings-mamager from terminal just type ccsm not the full name .

---

### Post by ranch hand on 2010-01-05
Won't start even with sudo.  Kind of strange.

This is  why I figure I will retry all this stuff when I reinstall this partition.  Need to test the A1 ISO and the 8.04.4 ISO (one or the other first, have no idea when the 8.04 will come out).  All ISO testing is on that partition.

Doing it that way due to the custom menu with a symbolic menu entry for "ISO-testing".  Should never have to change the menu entry on that partition, current entry should work for anything I put on there.

---

### Post by ronacc on 2010-01-05
just for grins look at /usr/bin/ccsm and make sure it is set to allow executing ,its a script and mabye the setting got munged .

---

### Post by ranch hand on 2010-01-05
I love the speed of getting to these files on other partitions using nautilus.  Looks set up right to me.

Looking at the script with my ignorant eyes it looks like its main goal is to get dbus to see it.  I know I have had a lot of dbus errors on different variations of 10.04 but usually not on clean installs.  There have been a lot of updates for it.  I wonder if there is something there that tips the balance when using my video card.

---

### Post by ronacc on 2010-01-05
although I started with these infernal things long before there were gui's i have been a mouse fan ever since my amiga .You are right about the script it just checks to see if it has waht it needs and if there is already an instance running and then starts one if there isn't . I have no idea why it would start from fusion-icon and not terminal .That it only partialy works from fusion-icom makes me think maybe its not finding something .

---

### Post by ranch hand on 2010-01-05
Well I am just going to have to wait and keep updating the bugger.  I guess I will have to wait all the way to the Monday (or Tuesday) before A2 for the ISO testing.  Gee whiz, I hate these long waits.

It could be that there is something that I have done to this to make it funky.  Assuming the CD works, A2 will be a clean install.  I am holding a few things like the sources list in a safe place and will just whack them back in there and see what happens.

---

### Post by ranch hand on 2010-01-07
I am getting excited about reinstalling the "edgers"/ISO partition.  This is a strange ride.

I updated my 3 throw away versions this morning and then went to check on them.  The "edgers" one looked really good when it cam up and I was suspicious at once.

Went and checked on "effects" and sure enough it was set on none.  No wonder it looked healthy.  So I clicked on "extra" and it ground away for a while and I get a message that it could not enable effects - no driver available.  Same thing when I tried "normal".

Just updated again (just got back from that partition) and the same deal.  I now am convinced that the stuff was definately not installed right.

Probably something I have done to that install has interfered or it just is not going to work with my card (or maybe whole system).  I will be doing a complete clean install when we get the notice for ISO test for A2.

Well, assuming the CD works.

---

### Post by BwackNinja on 2010-01-07
I'm having radeon issues with xorg-edgers too, so its not just your machine. Should be fixed in a couple days.

---

### Post by ranch hand on 2010-01-07
I am sure that they are on it.  I am glad to hear that I am not alone.

This has been a bad deal from the minute that I put the ppa in my sources list.  Well, really from the moment that I hit upgrade.  Got several warnings that it was not configured when I tried to use it.  Still can't open the "manager" from terminal but can from the icon.

Most of the boxes in the manager are dead.

This has been my main throw away install.  It gets the "dist-upgrade" everyday unless there is something really blatant wrong with that.  There have been some problems but the thing still runs.  It could well be that I have done something that screws this.

The symbolic menuentry for this partition reads "ISO-testing".  It will (hopefully) get 8.04.4 on it someday.  The reinstall for A2 was intended when this was installed.

It is, I admit, pretty clear how important "effects" and compiz are to me that I installed it only on a partition slated be formatted several times in this testing cycle.  I really do not like compiz or effects.

The fact that they do not run on my box has never bothered me, I prefer it this way.

However, now I actually want to see if this will work.  The problems seem interesting too.

So, I have my grub.d and images (gdm, xsplash, debian-theme) folders along with the /etc/default/grub and sources.list files over here on this install so that they can be whacked back into the new install and I can easily continue this experiment.

I am worried about the ISO test due to trying the other day to use a daily.  Sucker booted great.  Installer would not start even in terminal (sudo ubiquity).  Got it to start by "apt-get install ubiquity".  Then the installer/partitioner would not work.

Made partitions in gparted.  Installer still would not get past the partitioner even not having to do anything except recognize what partitions the install should go to.

---

### Post by kansasnoob on 2010-01-07
With or without xorg crack pushers repos the past few days X has been rough.

Pre-alpha 2 ...?

Feels good to me.

---

### Post by ranch hand on 2010-01-07
For me it has been all right, just slightly rough.  I think this is how it should go.

Except for the introduction of grub2 at A2 we really had no problems with 9.10 at this point.  We waited until a lot later and the poor bugger is still suffering some pains.  I think this one is going to work a lot better.

I really can't say why, it just feels right.

The last few updates seem to have improved booting reliability.  This may be wishful thinking on my part but I have one install that throws up the plymouth splash even.  I have been having to boot recovery and startx on that one for several days.

---

### Post by ranch hand on 2010-01-12
Well that install has been replaced with A2.  Inserted the stuff I wanted and saved including the sources.list with "edgers" on it.

My panels seem to work better.  No scrambling.

Icon hasn't shown up yet but the compiz manager is in the menu so who cares.

Wobbly Windows is enabled when I boot up but will respond to being turned off.  Cube does not show up but maybe i don't know what I am doing.

Plymouth works a lot better.

---

### Post by ronacc on 2010-01-12
check that the compiz manager in the menu is compizconfig-settings-manager and not simple-ccsm .

---

### Post by ranch hand on 2010-01-12
Yes it is, I did check that.

---

### Post by ronacc on 2010-01-13
I can't get the nvidia driver to activate yet so no compositing and I can't check for the cube here , If I can get the nvidia driver going I'll see what I can find .

---

### Post by ranch hand on 2010-01-13
Well I don't think it is going to work.  It acts like it did before with the improvement that I can get check marks in the cube boxes and out of the wall boxes.  Doesn't do anything but it is a step in the right direction (I guess).

It is an interesting thing and I spent all of about 45 minutes screwing wit hit today.

---

### Post by ronacc on 2010-01-13
Ok I got an nvidia driver to install , and I'm getting the same result here can check the cube but it doesn't work and extra effects wont activate , I think it has something to do with libgl migrating to mesa, I thought they had that fixed though , it's past pumpkin time here so 'll play some more in the morning .

---

