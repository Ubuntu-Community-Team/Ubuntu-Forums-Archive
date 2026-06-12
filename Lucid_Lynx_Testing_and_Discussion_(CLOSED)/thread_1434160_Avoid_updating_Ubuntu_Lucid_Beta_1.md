---
title: "Avoid updating Ubuntu Lucid Beta 1"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2010-03-19
**[Fixed versions of the packages on now in archive.ubuntu.com, will be making there way to the mirrors soon.]**

There have been some updates that came out after the release of Ubuntu Lucid Beta 1 that break gnome-panel and nautilus. If you have install or upgraded to Ubuntu Lucid beta 1, please avoid applying more updates for now. The problem will hopefully be fixed soon.

*Please note: Installing Ubuntu Lucid beta 1 is safe, the problem are with some new updates that came out after the beta release.*

Thanks,
T-V

---

### Post by aviramof on 2010-03-19
Too late i already did it and now i need to install it again or restore from backup i made but tell me something does this problem effect the dvd version because i'm downloading it now if i install it would i have the problem in the installer itself or would 
it happen only after i download updates?
 
thanks in advance.

---

### Post by Technoviking on 2010-03-19
Maybe the bug for gnome-panel.
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)
and maybe the bug for nautilus
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/542359](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/542359)

---

### Post by Anduu on 2010-03-19
Exactly what kind of timeframe are we talking here?

I updated 2 hours ago and everything seems fine.Can I assume logging out will mess things up or should I have noticed immediately?

---

### Post by Technoviking on 2010-03-19
> **Anduu said:**
> Exactly what kind of timeframe are we talking here?

I updated 2 hours ago and everything seems fine.Can I assume logging out will mess things up or should I have noticed immediately?

Hopefully soon, but maybe a couple of days. Matter how difficult of a fix it is and then getting built and uploaded to the repos.

T-V

---

### Post by castrojo on 2010-03-19
Don't log out. I have someone looking at it now.

---

### Post by Anduu on 2010-03-19
> **whiprush said:**
> Don't log out. I have someone looking at it now.

Thanks I'll wait for the all clear :)

---

### Post by sosafan1 on 2010-03-19
Is there a way to roll that update back, or will we have to wait?

*Any* way to get the panel back right now?

Of course this happens while I'm extolling the virtues of Linux to my wife, and complaining about having to build a Windows machine b/c we just got a Canon printer that only supports Windows.

Murphy!!

---

### Post by aviramof on 2010-03-19
ok i'll continue downloading the dvd version and wait for the problem to be fixed before installing more updates.

---

### Post by Technoviking on 2010-03-19
> **whiprush said:**
> Don't log out. I have someone looking at it now.

Thanks whiprush and thanks the devs for their quick response.

T-V

---

### Post by bshosey on 2010-03-19
If you right click on the desk top you can create a launcher and name it what ever and type in the command field "gnome-panel" you can then double click on that new launcher and then the panels will be there. I am going to do this until it is fixed.

---

### Post by VMC on 2010-03-19
I'm assuming this also applies to us that haven't installed beta, but have kept updates current. 

Do you have a list of the updated files to avoid?

edit: i just read the other topic, and it does effect us.
Luckily I have put off updating for a couple of days, waiting for a newer zsync file.

---

### Post by wfp on 2010-03-19
Thanks for the heads up was wondering why I was booting to a empty desktop. As always in a rush to download,and install instead of reading the stickies.

---

### Post by castrojo on 2010-03-19
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

Appears to be a problem with cdbs.

For those of you stuck with a purple screen and grumpy wife, hit alt-t, that will launch a terminal and run "gnome-panel".

---

### Post by Zerp64 on 2010-03-19
Well this is interesting. I'm having this problem too, but for me I'm just getting the purple wallpaper. No icons either, which I'm supposing others are getting. Still, I think this is the same problem as the one described here. At least I know that me tweaking my xorg isn't the cause of this problem.

Lucid is rockin' except for this.

---

### Post by sosafan1 on 2010-03-19
Alt+T doesn't do anything for me. Anyone else having this issue? I can't right-click, Ctrl+t, or Alt+F2, etc.

The only thing I can go is Ctrl+Alt+F1 and Alt+F7 to get out.

If I press volume up and down on my machine, I can see the volume icon on the desktop adjusting properly. If I Ctrl+right arrow it moves to the next desktop.

It seems that I just can't figure out how to run gnome-panel.

Any other suggestions?

---

### Post by godhika on 2010-03-19
It's Strg+Alt+t for me Edit: Reed Strg as Ctrl ;)

---

### Post by sparker256 on 2010-03-19
Its Ctrl+Alt+t for me

---

### Post by Zerp64 on 2010-03-19
> **whiprush said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

Appears to be a problem with cdbs.

For those of you stuck with a purple screen and grumpy wife, hit alt-t, that will launch a terminal and run "gnome-panel".

Oh, and a better idea would be to edit /usr/share/applications/gnome-panel.desktop and nautilus.desktop and move the "X-Ubuntu-Gettext-Domain=whatever" to the bottom of the file. After that nautilus starts up okay, but you need to add gnome-panel to your list of startup applications to get it running.

There's probably a way to do this to all affected *.desktop files... any ideas?

---

### Post by sosafan1 on 2010-03-19
Thanks, guys. I'm now successfully posting this message from my Ubuntu box again.

It ended up being Ctrl+Alt+T to get the terminal.

Then running gnome-panel from there.

I can just do this until this bug gets worked out. I'd rather have to do this knowing good developers are working on the problem than using Windows any day of the week.

Thanks again!

---

### Post by sosafan1 on 2010-03-19
> **Zerp64 said:**
> Oh, and a better idea would be to edit /usr/share/applications/gnome-panel.desktop and nautilus.desktop and move the "X-Ubuntu-Gettext-Domain=whatever" to the bottom of the file. After that nautilus starts up okay, but you need to add gnome-panel to your list of startup applications to get it running.


I did this, and still can't go to, say, places from the panel and choose Documents. When I do, I get an error 

Could not open location file:///home/user/Documents.
No application is registered as handling this file.

Is that what you guys are getting, too?

---

### Post by Zerp64 on 2010-03-19
> **sosafan1 said:**
> I did this, and still can't go to, say, places from the panel and choose Documents. When I do, I get an error 

Could not open location file:///home/user/Documents.
No application is registered as handling this file.

Is that what you guys are getting, too?

Never said it'd fix that ;).

But yeah, I'm getting that too.

---

### Post by godhika on 2010-03-19
> **sosafan1 said:**
> 
Could not open location file:///home/user/Documents.
No application is registered as handling this file.

Is that what you guys are getting, too?

Yup. Same here

---

### Post by swoll1980 on 2010-03-20
Well this sucks. Will this be fixed in an update or do we have to find a way to fix it?

---

### Post by david20063 on 2010-03-20
> **sosafan1 said:**
> I did this, and still can't go to, say, places from the panel and choose Documents. When I do, I get an error 

Could not open location file:///home/user/Documents.
No application is registered as handling this file.

Is that what you guys are getting, too?

I am getting this error too but if I open a terminal and type
```
sudo nautilus
```it lets me view my files as a superuser...is there permission error not letting me view them without being a superuser?

---

### Post by sosafan1 on 2010-03-20
Yeah, that's what I figured. Just wanted to make sure that I wan't alone, and obviously I'm not.

I'll just have to do all my file management the old school way...from the terminal!

---

### Post by Zerp64 on 2010-03-20
gnome-panel.desktop
nautilus.desktop
empathy-accounts.desktop
empathy.desktop
evolution-2.2.desktop
evolution.desktop (remove first line)

..And others are affected. What program (if any) writes these?

> Well this sucks. Will this be fixed in an update or do we have to find a way to fix it?

Just do what I did: start an xterm session, launch gnome-panel, fix the gnome-panel.desktop and nautilus.desktop files, and add gnome-panel to startup. It doesn't completely fix everything, but it's a start.

---

### Post by swoll1980 on 2010-03-20
> **Zerp64 said:**
> gnome-panel.desktop
nautilus.desktop
empathy-accounts.desktop
empathy.desktop
evolution-2.2.desktop
evolution.desktop (remove first line)

..And others are affected. What program (if any) writes these?



Just do what I did: start an xterm session, launch gnome-panel, fix the gnome-panel.desktop and nautilus.desktop files, and add gnome-panel to startup. It doesn't completely fix everything, but it's a start.

Thanks I'll just hang tight until we get an official explanation.

---

### Post by Regenweald on 2010-03-20
I actually read a sticky to my benefit :) Guess I'll upgrade around Sunday. Thanks admin and devs....

---

### Post by VMC on 2010-03-20
> **Regenweald said:**
> I actually read a sticky to my benefit :) Guess I'll upgrade around Sunday. Thanks admin and devs....

Yes, me too. This is one case where being late to update was a blessing.

---

### Post by Tungsten Tide on 2010-03-20
SMBus base address bug:
relates to users of vmare and virtualbox who get a bios flickering problem:

[http://www.khattam.info/2010/01/30/solved-virtualbox-ltsp-smbus-base-address-uninitialized-upgrade-bios-or-use-force_addr0xaddr/](http://www.khattam.info/2010/01/30/solved-virtualbox-ltsp-smbus-base-address-uninitialized-upgrade-bios-or-use-force_addr0xaddr/)

---

### Post by Kenny_Strawn on 2010-03-20
It's interesting that the Nautilus bug also affected Jaunty, and was posted twice. I'm sure the same method they used to fix Jaunty's version of the bug can also be used in Lucid.

---

### Post by alienexplorers on 2010-03-20
Updated from Alpha3 to Beta1 and ran all updates and system still functions normally.  Don't know why everybody is having problems.

---

### Post by psyke83 on 2010-03-20
> **alienexplorers said:**
> Updated from Alpha3 to Beta1 and ran all updates and system still functions normally.  Don't know why everybody is having problems.

Because you either didn't log out yet, or you're using an outdated regional mirror.

---

### Post by k3lt01 on 2010-03-20
> **psyke83 said:**
> Because you either didn't log out yet, or you're using an outdated regional mirror.Well I update before 7am this morning and its now 4.13 pm. My system has been rebooted numerous times going back and forth between Karmic and Lucid about 3 times each in that time and I have not had one issue with Lucid today.

My Karmic desktop on the other hand is an entirely different kettle of fish and is about to get some terse words ;) lol.

P.S. I use the main mirror for Lucid.

---

### Post by Elfy on 2010-03-20
> **Technoviking said:**
> There have been some updates that came out after the release of Ubuntu Lucid Beta 1 that break gnome-panel and nautilus. If you have install or upgraded to Ubuntu Lucid beta 1, please avoid applying more updates for now. The problem will hopefully be fixed soon.

*Please note: Installing Ubuntu Lucid beta 1 is safe, the problem are with some new updates that came out after the beta release.*

Thanks,
T-V
Thanks for the sticky T-V :)

> **Technoviking said:**
> Thanks whiprush and thanks the devs for their quick response.

+1 to that 

T-V

> **VMC said:**
> Yes, me too. This is one case where being late to update was a blessing.

It was here too :)

---

### Post by elegant55 on 2010-03-20
The title of the thread may be misleading to some people. It actually should be read as "Avoid POST beta 1 updating".

So if you installed updates up to beta 1 or maybe earlier today that would not cause problem.

Probably because the beta freeze has been lifted and a bunch of on held updates has been sent to the repository later this day and some of the packages have problems now cause critical problems. So don't install the updates when they appeared after you refresh the update-manager later today.

---

### Post by madjr on 2010-03-20
wouldnt be a bad idea if ubuntu came with some sort of timemachine/timevault program that **auto-saves/bacups/creates image before applying updates** and/or restore in case of breakage

am always afraid of updating anything (sometimes even on final releases)

probably next in the list of things to implement

---

### Post by vishalrao on 2010-03-20
yay! finally some live action real life *breakage* !!! :lolflag: it was getting a little boring this lucid beast...

---

### Post by Zerp64 on 2010-03-20
> **vishalrao said:**
> yay! finally some live action real life *breakage* !!! :lolflag: it was getting a little boring this lucid beast...

That's what I thought. It's been going really smooth so far.

Updates have been pushed out for a bunch of progs. I'll update if they happen to fix this problem.

---

### Post by wgrant on 2010-03-20
We're working on fixing this right now. We expect that the main mirror will have the critical fixes in around two hours, but only time will tell, and some applications may need further fixes afterwards.

For now, do not upgrade.

---

### Post by Elfy on 2010-03-20
> **wgrant said:**
> We're working on fixing this right now. We expect that the main mirror will have the critical fixes in around two hours, but only time will tell, and some applications may need further fixes afterwards.

For now, do not upgrade.

Thanks for keeping us advised  :)

---

### Post by NightwishFan on 2010-03-20
Workaround for a usable desktop:
Log in and press ctrl+alt+t to get a terminal, type:
```
gnome-panel
```
Press alt+f2 and type:
```
nautilus
```

Desktop should be usable, do not close terminal. You may also be able to press alt+f2 again and run:
```
killall gnome-terminal && gnome-terminal
```

See how it works for you, I am currently logged in on beta doing this.

---

### Post by wgrant on 2010-03-20
The important i386 and amd64 updates are built, and should be available on the main archive mirror in around an hour. Some applications will remain broken afterwards, but the desktop itself should function fine.

---

### Post by Evil Dax on 2010-03-20
ctrl-alt-t did the trick for opening terminal
and running gnome-panel brought desktop back to live.

:-)

(found out that running ctr-alt-f1 and started firefox --display=X:0, and came here)

---

### Post by Jags_FL on 2010-03-20
@ NightwishFan

```
Log in and press ctrl+alt+t to get a terminal, type:
gnome-panel
```

that did the trick for me, many thanks :D

---

### Post by esims89 on 2010-03-20
Awesome, should have looked at the sticky.
Thanks for the quick update.

---

### Post by dino99 on 2010-03-20
Does devs sometimes take care of changes files they use ?
Look at package:  make 3.80+3.81.b3.1-1  :o

---

### Post by dcstar on 2010-03-20
Somewhere there is a six year-old being told:

"I told you NOT to touch that!"    :tongue:

---

### Post by ViRMiN on 2010-03-20
Just updated and picked up the new updates and gnome-panel and nautilus are working properly again.  Cheers! ;)

---

### Post by wgrant on 2010-03-20
The critical updates (gnome-panel and nautilus, both version 1:2.29.92.1-0ubuntu3) are now on archive.ubuntu.com for i386 and amd64. Other architectures will have to wait for an hour or two more, as will some of the other broken applications.

Complete normality should be restored within a few hours!

---

### Post by Evil Dax on 2010-03-20
updated&rebooted, and everything seems to e back to normal.

Great & fast job guys!

---

### Post by Kazade on 2010-03-20
There seem to be more problems. I updated this morning and Nautilus and Gnome-panel broke - but also Empathy and Evolution and probably others. The cause is broke *.desktop files in /usr/share/applications to fix it you need to move the first line of the file to the last line.

Has this been reported? I can only see talk of Nautilus and Gnome-panel.

---

### Post by wgrant on 2010-03-20
That's because those are the critical ones which broke the desktop. Other applications which are currently rebuilding are Empathy, Evolution, gedit, GNOME Disk Utility, Rhythmbox and Totem. They will be available on most architectures in around 40 minutes.

That fixes all known instances of this bug, and I'm scanning for anything else that might be broken right now.

---

### Post by 3rdalbum on 2010-03-20
Funny. I updated 5 hours ago on my netbook and I don't see any problems. I'll wait until tomorrow to apply updates on my desktop though :-)

---

### Post by fenririx on 2010-03-20
I need to start checking the posts prior to starting my ubuntu machine, i updated and everything went crazy, restarted and now the gnome panel is missing cant even bring up the terminal

---

### Post by Kazade on 2010-03-20
> **wgrant said:**
> That's because those are the critical ones which broke the desktop. Other applications which are currently rebuilding are Empathy, Evolution, gedit, GNOME Disk Utility, Rhythmbox and Totem. They will be available on most architectures in around 40 minutes.

That fixes all known instances of this bug, and I'm scanning for anything else that might be broken right now.

Well, that covers all the instances I'm seeing after just updating again:

luke@Hydrogen:~$ head -n 1 /usr/share/applications/* | grep Gettext
X-Ubuntu-Gettext-Domain=evolution-2.28
X-Ubuntu-Gettext-Domain=evolution-2.28
X-Ubuntu-Gettext-Domain=gedit
X-Ubuntu-Gettext-Domain=gnome-disk-utility
X-Ubuntu-Gettext-Domain=rhythmbox
X-Ubuntu-Gettext-Domain=totem

---

### Post by Jags_FL on 2010-03-20
> **wgrant said:**
> The critical updates (gnome-panel and nautilus, both version 1:2.29.92.1-0ubuntu3) are now on archive.ubuntu.com for i386 and amd64. Other architectures will have to wait for an hour or two more, as will some of the other broken applications.

Complete normality should be restored within a few hours!


Simply awesome! Many thanks for the rapid response guys =D>

---

### Post by szirakitamas on 2010-03-20
> **bshosey said:**
> If you right click on the desk top you can create a launcher and name it what ever and type in the command field "gnome-panel" you can then double click on that new launcher and then the panels will be there. I am going to do this until it is fixed.

yes, it was first time after upgrading, i've found this "solution", i made icons for gnome-terminal and gnome-panel, but it worked only after i was creating a new user and tried to login that account. there where no more this option. just the mouse pointer. :)

edit: i see the updates came out. :) thx

---

### Post by fenririx on 2010-03-20
Wow tat was a fast fix Ty gys for all the help and the quick fix from the ubuntu gods:D

---

### Post by goldsniper on 2010-03-20
thanks... i was waiting for this fix!! good job, devs..

---

### Post by nhayday on 2010-03-20
Hopefully the PPC architecture fixes will follow shortly.

---

### Post by cosmicbuff on 2010-03-20
thats blazingly quick :shock:, thanks devs , will try it out.

---

### Post by geoffe on 2010-03-20
Brilliant, rapid response, guys. Now back to full stream!

---

### Post by up2early on 2010-03-20
Updated Lucid through Update manager, rebooted and all lost functionality returned. Desktop loads and all Places now load. Fantastic job with this fast bug fix.

---

### Post by wgrant on 2010-03-20
Fixed versions of all broken applications are now on archive.ubuntu.com, except for sparc and armel which are still missing a few.

If you have further problems while fully upgraded, please file bugs.

---

### Post by nhayday on 2010-03-20
Is this for PPC versions also.

---

### Post by wgrant on 2010-03-20
> **nhayday said:**
> Is this for PPC versions also.

Yes, all of the PowerPC binaries are now fully published.

---

### Post by Soul-Sing on 2010-03-20
thx fixing this devs.

---

### Post by RJMacReady on 2010-03-20
Unfortunately, not fixed. Just did an update and now the gnome panels don't appear.

EDIT: Oh wait, no. A second lot of updates have fixed the problem.

---

### Post by zob on 2010-03-20
Are you using the main server to upgrade. Some others are delayed as far as I understood.
Did you see a lot of fixes for empathy and evolution to?
You can have at look in /var/log/aptitude.

My empathy version f.x is, 2.29.93-0ubuntu2.


I updated 10 mins ago. All is working fine here on a netbook remix.

---

### Post by StuM on 2010-03-20
The last couple of days I've been trying out Docky, but this morning I decided I didn't like it, so attempted to add the bottom panel back.  Messing around with panels has been troublesome for me with Lucid, requiring a restart when adding a new panel.  So this morning when 'add panel' did nothing again, I thought 'no problem, a restart will solve it'.  Except when the desktop returned I had no panels left!  I thought I'd broken something.

I was about to post on the forums for some help, when I noticed the sticky... It wasn't my fault after all... :D

(Panels / Menus all back to normal now.  Thanks for the quick fix.)

---

### Post by OGpmpdog on 2010-03-20
Hi All,

I'm a Linux Newbie, having jumped aboard a little more than a year ago with Intrepid Ibex...I must be stoked - this is the 1st time Ive ever played with a BETA release.

I still have trouble installing software...It was soooo cool to just refresh the update manager.

Thanks for the quick fix!! 

Your work is greatly appreciated!:P

---

### Post by Technoviking on 2010-03-20
Fixed versions of the packages on now in archive.ubuntu.com, will be making there way to the mirrors soon.

T-V

---

### Post by _h_ on 2010-03-20
> **Technoviking said:**
> Fixed versions of the packages on now in archive.ubuntu.com, will be making there way to the mirrors soon.

T-V

Thanks for the notice TV, I've disabled my updates for now until confirmation of them being on the mirrors.

---

### Post by victor9098 on 2010-03-20
Oh you crazy kids developing this...  did you guys do this just to make sure we had not fallen asleep with this development cycle? Everything was going so sweet, and you leave this Easter egg for the beta. Well we are awake now and will promise not to nod off again.

Seriously, thanks for getting on top of this issue and fixing so quick, just shows why everything Ubuntu is so much better comapred to anything out there. Now just need to fix Bug #1 ;)

---

### Post by Uncle Spellbinder on 2010-03-20
Indeed. Very glad to see this issue addressed pretty quickly.

---

### Post by zulli1942 on 2010-03-20
Thank you Dev team for jumping on this. 1st time I have seen this happen with a release in Ubuntu, I've been running it since 6.10. That speaks to the quality of the team.

---

### Post by slakkie on 2010-03-20
IMO, this thread convinces me that the development releases should also use $DIST-updates repo. Every release point $DIST-updates moves to $DIST repo's and that way you can easily restore the previous working package.

---

### Post by Tide9 on 2010-03-20
The new updates solved all my desktop problems resulting from the previous updates. Many thanks to all the Ubuntu developers for all the great work they do.

---

### Post by Keyper7 on 2010-03-20
Now that the fixes have arrived, shouldn't the title be changed to "for God's sake, please update Lucid Beta 1"? :)

---

### Post by emarkay on 2010-03-20
To Clarify:

All Beta1 Discs made on release day and from now on are OK.
The issue was a "bum" set of updates.
Those bad updates are now gone forever (except in archives).
No need, from now on, to do anything about this issue.

Thus can we remove this as "Sticky"? 

Big thanks to the Devs who got this corrected!

And, a nice "heads-up", this was, for the unexpected reminder that this is still Beta Test!

---

### Post by Anduu on 2010-03-20
Great work devs :KS

---

### Post by dabomb1022 on 2010-03-20
Too late, have to re-install...

---

### Post by Anduu on 2010-03-20
> **dabomb1022 said:**
> Too late, have to re-install...

[COLOR="Red"]**You do not have to reinstall!**[/COLOR]

When the login screen appears hit Ctrl-Alt-F1 for the text login.

Log in and sudo aptitude -q update && sudo aptitude -q safe-upgrade

---

### Post by SuperVectorGirl on 2010-03-20
Before I found this thread, I was having the same problem opening Documents, got the error message "Could not open location 'file:///home/.../Documents' No application is registered as handling this file", but I upgraded Nautilus from the synaptic, and it seems to be working now, aside from the Pictures file loading up then disappearing (it doesn't if I load/import an image from within another program, for ex. Inkscape), a problem I have had since Karmic.

---

### Post by armageddon08 on 2010-03-20
I've just installed Lucid Beta 1. Is it safe to update now? Just wanna make sure...

---

### Post by Anduu on 2010-03-20
> **armageddon08 said:**
> I've just installed Lucid Beta 1. Is it safe to update now? Just wanna make sure...

Seriously?!
The answer is 5(count em FIVE...) posts above you.

---

### Post by armageddon08 on 2010-03-20
> **Anduu said:**
> Seriously?!
The answer is 5(count em FIVE...) posts above you.

OOps sorry.....got it...
:oops:

---

### Post by reiki on 2010-03-20
Mine is still telling me it's a partial. Should I download a fresh iso and start over? I got the iso just about as soon as I saw it on the mirror yesterday afternoon (eastern US for time reference).

---

### Post by 23meg on 2010-03-20
> **Keyper7 said:**
> Now that the fixes have arrived, shouldn't the title be changed to "for God's sake, please update Lucid Beta 1"? :)

Let's make sure all archive mirrors have synced up before doing that.

---

### Post by Anduu on 2010-03-20
> **reiki said:**
> Mine is still telling me it's a partial. Should I download a fresh iso and start over? I got the iso just about as soon as I saw it on the mirror yesterday afternoon (eastern US for time reference).

sudo aptitude -q update && sudo aptitude -q safe-upgrade should avoid any partial upgrade mishaps.

---

### Post by FrancoNero on 2010-03-20
> **Anduu said:**
> [COLOR="Red"]**You do not have to reinstall!**[/COLOR]

When the login screen appears hit Ctrl-Alt-F1 for the text login.

Log in and sudo aptitude -q update && sudo aptitude -q safe-upgrade

when i'm in text mode i have no wireless. so how to update? (currently have no ethernet)

ctrl alt f2 does not bring up a terminal window when i'm in this panel/nautilus-ness environment.

who can help me?

---

### Post by Anduu on 2010-03-20
You could try booting into recovery mode and select Netroot login.Not sure if it would enable wireless though.

Is there no way you can direct connect?

---

### Post by FrancoNero on 2010-03-20
no wireless in that mode. tried. my ethernet plug thing is broken, so my laptop is basically wireless-only at the moment

---

### Post by dabomb1022 on 2010-03-20
I luckily had cairo dock so I made a  custom launcher and updated to fix the problem. I couldn't right click on the desktop so thats all that worked for me.

---

### Post by Anduu on 2010-03-20
> **FrancoNero said:**
> no wireless in that mode. tried. my ethernet plug thing is broken, so my laptop is basically wireless-only at the moment

Dang.

Sorry but getting wireless up and running from console is beyond my knowledge :(

Try Ctrl-Alt-t maybe.

---

### Post by dabomb1022 on 2010-03-20
> **SuperVectorGirl said:**
> Before I found this thread, I was having the same problem opening Documents, got the error message "Could not open location 'file:///home/.../Documents' No application is registered as handling this file", but I upgraded Nautilus from the synaptic, and it seems to be working now, aside from the Pictures file loading up then disappearing (it doesn't if I load/import an image from within another program, for ex. Inkscape), a problem I have had since Karmic.
Same here but the update fixed it.

---

### Post by FrancoNero on 2010-03-20
so I guess I do have to reinstall. It sucks that wireless doesn't work in text mode... I don't get why, I mean isn't network-manageer always running, and the only difference about text mode is that well, there's only text?

---

### Post by Anduu on 2010-03-20
> **FrancoNero said:**
> so I guess I do have to reinstall. It sucks that wireless doesn't work in text mode... I don't get why, I mean isn't network-manageer always running, and the only difference about text mode is that well, there's only text?

Opps you replied as i edited.

Login to your blank desktop and Ctrl-Alt-t ?

---

### Post by FrancoNero on 2010-03-20
ctrl alt t does NOTHING :)

---

### Post by NightwishFan on 2010-03-20
If you "updated" to lucid it is disabled because it is on Karmic. If you fresh install lucid it is enabled. (I think so anyway)

---

### Post by FrancoNero on 2010-03-20
i fresh installed lucid (when we were at alpha 3). no update from karmic

---

### Post by Anduu on 2010-03-20
Gah!

Well I'm out of ideas...sorry man :oops:

---

### Post by FrancoNero on 2010-03-20
no problem. since i'm dual booting, i'll just stay on karmic for afew more weeks and then make the complete switch come RC.... I mean I was just curious and playing around with lucid, I should've known better than to even think I could work with it before late beta / early RC state

---

### Post by NightwishFan on 2010-03-20
That is what I did as well. Odd. Well, you can manually tell the program to open on your xserver from the console, however I forget how.

---

### Post by samcompton on 2010-03-20
I too realized this issue after the update yesterday.  I have run updates today but, the problem persist.  The only way gnome-panel opens on startup is if I have it listed in my Startup Applications.  Should this issue be gone or are we still waiting for a fix?

---

### Post by venkatad on 2010-03-20
> **sosafan1 said:**
> I did this, and still can't go to, say, places from the panel and choose Documents. When I do, I get an error 

Could not open location file:///home/user/Documents.
No application is registered as handling this file.

Is that what you guys are getting, too?

HI I fixed this problem by going into synapticmanager and type there mautilus and upgrade where ! is shown that fixed.problem

---

### Post by smokin74 on 2010-03-21
where can i get these updates? - my gnome panel and nautilus are still 1.2.28 - still no desktop for me!!!

---

### Post by meborc on 2010-03-21
> **smokin74 said:**
> where can i get these updates? - my gnome panel and nautilus are still 1.2.28 - still no desktop for me!!!

did you try update+dist-upgrade or just upgrade? maybe something needs to be removed... try with dist-upgrade (but be aware of the possible removal of some packages... check what is upgraded and/or removed before you proceed)

---

### Post by smokin74 on 2010-03-21
i was using synaptic :oops: whats the correct syntax for aptitude or apt (apologies)?

---

### Post by meborc on 2010-03-21
> **smokin74 said:**
> i was using synaptic :oops: whats the correct syntax for aptitude or apt (apologies)?

sudo apt-get update && sudo apt-get dist-upgrade

but only say Y if you see that there are no important packages that are going to be removed

---

### Post by smokin74 on 2010-03-21
done that and i get 0's - ie nothing to update - is it a repository isssue then ?

---

### Post by meborc on 2010-03-21
> **smokin74 said:**
> done that and i get 0's - ie nothing to update - is it a repository isssue then ?

maybe... what does your /etc/apt/sources.list file look like? ;)

---

### Post by tr33m4n on 2010-03-21
No updates have fixed anything... I'm still starting gnome-panel, nm-applet etc from terminal... probably gonna have to rebuild :( however just wondering, where are those .desktop entry files located? might as well have a fiddle with them

Cheers
Dan

---

### Post by tr33m4n on 2010-03-21
Never mind, rebuilding now

---

### Post by mc4man on 2010-03-21
> No updates have fixed anything.

Have you tried restarting?

All the affected .desktops are in/usr/share/applications, though note that several, once properly written will not be seen.
Generally speaking when a .desktop in /usr is proper and usable it will be seen as an icon, when not proper and unusable as a text icon.

If you browse /usr/share/applications from another install or live cd then they will all be seen as text icons and the previously improper 1st. line quite visible.
Though the updates have fixed all the one I saw as wrong (eighteen)

If you wanted to ck. gnome-panel then 
```
 gedit /usr/share/applications/gnome-panel.desktop
```

or gksu gedit ..... to edit
(though gedit was also one of the affected apps...

---

### Post by FrancoNero on 2010-03-21
any new ideas on what to do without ethernet? how do I activate wirless from the text-mode? I know it's on, but it's not connected to my usual access point.... so i can't really do updates (ethernet broken)....

---

### Post by samcompton on 2010-03-21
I don't know if this has anything to do with it but, I gave up and did a fresh install with beta 1.  Before with Alpha 5 I was using Human theme.  I noticed now after a fresh install of beta 1 Human theme is not installed.  Maybe this is why I still had no gnome-panel even after following everyone's advice in this thread.

---

### Post by smokin74 on 2010-03-21
> **meborc said:**
> maybe... what does your /etc/apt/sources.list file look like? ;)
id love to post it to you but i can only run one prog at a time at the moment from a xterm login = ctrl+alt+T doesnt work - i can initiate gnome-panel to get the drop down menus, and nautilus via sudo - however even that is limited as  i cant mount certain drives when it feels like it -

as i have no minimise button or a dock to put them on you have to close the prog (and lose the clipboard contents) to run something else - 

which mirror site definately has the .29 updates on it - surely i can just point my sources.list to that and away i go??

any help appreciated 

chris

---

### Post by sebastianabate on 2010-03-22
> **FrancoNero said:**
> any new ideas on what to do without ethernet? how do I activate wirless from the text-mode? I know it's on, but it's not connected to my usual access point.... so i can't really do updates (ethernet broken)....

Check this thread

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by dartmusic on 2010-03-23
> **StuM said:**
> The last couple of days I've been trying out Docky, but this morning I decided I didn't like it, so attempted to add the bottom panel back.  

I tried loading Docky this morning (March 23rd) and Docky won't run.  I believe it was a Mono error, if I read the info in Terminal correctly.  I'm at work now, but, wondering if anyone has any trick to get it to run in Lucid, or if I should just wait for updates and cross my fingers!

Thanks.

---

