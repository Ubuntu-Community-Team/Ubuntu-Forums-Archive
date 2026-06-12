---
title: "Ubuntu 7.10 is buggy as hell"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Bitch-Face Jones on 2007-10-21
Okay, so I upgraded to Ubuntu 7.10 from 7.04 yesterday.  After wrangling with some issues with the nVidia driver I was using (I was using the binary drivers from nVidia, and switched to Ubuntu's "restricted" driver which was slightly newer) I've had nothing but weird problems.  These include:

[LIST]
[*]**The OpenGL desktop sucks** On my old system I used beryl, which was a bit buggy a nd slow, but at least worked.  Now apperently beryl and compiz have been merged into a signle package, compiz-fusion.  Frankly, neither beryl nor compiz were that great to begin with, but this compiz-fusion thing seems to be like Voltron for crap.  When I go to "GL desktop" from the system preferences menu, nothing happens.  When I try it again, the GL desktop settings dialog appears, but none of the changes that I make take place.  The GL desktop tray icon seems to randomly appear in the taskbar, but doesn't seem to be able to communicate with other processes (if I try to save my session in Gnome when the compiz icon is in the taskbar trey, the session manager just hangs and finally pukes up an error about the compiz trey icon, and invoking the GL desktop settings from the trey icon dosen't do anything) That, and compiz-fusion doesn't have any of the features that I liked in beryl to begin with (transparent windows, etc.)

[*]**Can't change font settings** I didn't like the way the subpixel smoothed fonts looked in Ubuntu 7.10, so I went into the font settings and tried changing them to 'best shape'.  When I clicked the 'best shape' radio button, my cpu usage shot up to 100% and nothing else happened.  The fonts dialog was completely unresponsive (although the close button still worked, for some reason.)  Now, whenever I go into the Appearance dialog and click the Fonts tab, my cpu usage goes to 100%, and the dialog just hangs until I click close.

[*]**wtf is 'trackerd'** When I first booted into Ubuntu 7.10, I noticed that some process (trackerd) was taking up 50% of the CPU time on both of my processors.  When it was still doing the same damn thing after running for a day, I killed the process and uninstalled tracker.  My system still works fine (desktop search hasn't been affected, either) so god knows what that thing was for in the first place.
[/LIST]

I dunno, I guess I should have listened to that quiet, nagging doubt in the back of my head that said upgrading to 7.10 would be a bad idea.

---

### Post by buzzmandt on 2007-10-21
> Name
trackerd - indexer daemon for tracker search tool
Synopsis
trackerd [--disable-indexing] [-t|--turbo] [--enable-debug] [--enable-evolution] [--enable-thunderbird] [--enable-kmail] [WatchDirectory1 WatchDirectory2...]
Description
trackerd indexes documents and extract metadata to provide quick search capabilities. By default, trackerd will index the documents stored on the folders defined in the file ~/.Tracker/tracker.cfg; if a folder is provided as parameter, trackerd will index all the documents stored under this folder, and its sub-folders.

[http://linux.die.net/man/1/trackerd](http://linux.die.net/man/1/trackerd)

---

### Post by Bitch-Face Jones on 2007-10-21
> **buzzmandt said:**
> [http://linux.die.net/man/1/trackerd](http://linux.die.net/man/1/trackerd)

Right, I just think it's pretty ridiculous that tracker's default behavior is to continuously take up a ton of CPU time, even if it the process is 'niced' to a low priority.

---

### Post by Bitch-Face Jones on 2007-10-21
Oh yeah, I don't get a startup screen, either, and I can't switch to another console from my X session.  I think this is because the framebuffer module isn't loading, but I'm not sure why that would be happening.

---

### Post by BoardDWorld on 2007-10-21
I think perhaps that in regards to effects you're going about things in an out-dated method. 

With Compiz-Fusion, both on Feisty and Gutsy, everything is controlled via the "Advanced Desktop Effects Manager". Gutsy doesn't have this package by default install it with the following:

```
sudo aptitude install compizconfig-settings-manager python-compizconfig
```

Now with Gusty you manage your effects at System ---- Preferences ---- Appearance ---- Visual Effects. If you go there now you will see that there are 3 options. With the packages above installed you will have the 4th "custom" option. There is no task-bar icon, do you change your effects that often?

I used the git repo's for Compiz-Fusion on Feisty so i had the most up to date packages and it was ALWAYS completely stable other than 3D gaming (This has now been fixed in Gutsy)

---

### Post by BoardDWorld on 2007-10-21
P.S. After all the fine work that has been done it isn't very nice making a statement that "7.10 is buggy as hell" in Ubuntu forums. It would have been more correct to say "Help,  don't know quite what I'm doing"...

---

### Post by Bitch-Face Jones on 2007-10-21
> **BoardDWorld said:**
> P.S. After all the fine work that has been done it isn't very nice making a statement that "7.10 is buggy as hell" in Ubuntu forums. It would have been more correct to say "Help,  don't know quite what I'm doing"...

Well, what I'm experiencing are bugs, and I do know what I'm doing, thank you.  The Appearance dialog becomes completely unresponsive (even when I click on tabs other than Fonts.)  This is a bug.  There are two separate methods for managing compiz,  one of which - the one which is supposed to be the simple one - does not work.  This is a bug.  If I boot into my system and immediately start running into issues which I have no control over, then I would say that my assertion of Ubuntu 7.10 being buggy is accurate.  Sorry if I've offended you by badmouthing your favorite OS.

---

### Post by jrickard on 2007-10-22
AND you have the added benefit of being quite correct.  That this software was ever released is absolutely inexcusable.  All the monkey spunk I"ve been going through to get their release CD to even 
boot was just a joke.  Now, a black screen on the boot off the hard drive.  There are 3000 messages on here from people with exactly the same problem (and I guess they all don't have a clue either) and 
no help.

I'm disgusted with Ubuntu.  This is a mess.  Kids with compilers run amuck.

Jack Rickard

---

### Post by Wiebelhaus on 2007-10-22
The OP's Nick is amazingly appropriate considering he's bitching.

---

### Post by rsambuca on 2007-10-22
It has been smooth sailing for me.  Did you guys upgrade or install fresh systems.  If you upgraded, did you use outside repositories in Feisty?  Did you use non-supported installers?

---

### Post by dagrump on 2007-10-22
Now, I must admit I do not upgrade, I do clean installs. I've been running Gutsy since tribe2 on 2 different test boxes & since tribe 4 on my laptop.
It has been a very well behaved release compared to edgy, upgrades should be avoided like the plague.
If you've customized your install you are most like to have some things get broken. That being said you might start by uninstalling beryl & compiz-fusion, reboot &  reinstall compiz-fusion, & the settings manager. That might clean up some of the issues.

---

### Post by kamaboko on 2007-10-22
> **Bitch-Face Jones said:**
> Well, what I'm experiencing are bugs, and I do know what I'm doing, thank you

Yeah, got to be PC here.  It's only buggy if it's a MS product.  For all other OS's one has to say, "help...I don't know what I'm doing".  :lolflag:

---

### Post by cannontrodder on 2007-10-22
I'd previously installed Edgy then upgraded to Feisty. I hadn't clean installed Feisty though, I just upgraded a base install of Edgy. I then tended to install the video card acceleration and wireless afterwards.

 My upgrade to Gutsy hasn't gone as smoothly as these hacks have got in the way. I had to use Envy to install nvidia. Perhaps there was a package I needed to install but it just didn't seem to want to accept my settings in the new graphical x config screen. If I do another clean install of gutsy, I might just wait until I can enable restricted packages before trying to get acceleration going again.

On the other hand, fwcutter and the firmware for my wireless card are working now. It *seems* more stable but sometimes it is a struggle to get it to connect to the network initially. The fact the driver stays pretty stable when it is up makes me think a clean install of Gutsy will resolve any configuration issues. 

All in all, though, I've spent the best part of a couple of hours trying to fix it. I'm wondering what I *needed* to upgrade for though. I think I'll wait a *bit* longer before being tempted by that upgrade button again.

---

### Post by flinkman on 2007-10-23
the sad truth is: gutsy is indeed buggy as hell. to a degree that makes it unusable:
- the new xserver configuration gui does not work at all, i had to write my xorg.conf by hand and have to use the command line everytime i change monitor setup. the irony with this is, that use one of the rare chipsets with full opensource support by the manufacher: intel gma. actually i specificialy bougt a computer with this chipset because i knew it is the only one with free drivers.
- compiz does not work, again with one of the few free drivers actually supporting 3d
- mounting usb attached luks encrypted volumes worked flawlessly with feisty, no chance with gutsy
- the "window list" (aka "taskbar") applet in the gnome panel crashes constantly (well, it not even crashes - it hangs, makeing the whole panel irresponsive, and taking 100% cpu time)
- thunderbird mail crashes all the time
- network-manager just dissapears from time to time
- cpu freqency scaling is totaly missconfigured, i used powetop to analyse wakeup causes, finding that the top cause is "powernowd" a deamon with is totaly useless on newer cpus (core2) so i uninstalled it. result: scaling does not work anymore, i had to modprobe acpi-cpufreq by hand to get scaling back.

all this is really frustrating...

now all i can hope is that the soon arriving fedora8 will deliver a working operating system.

---

### Post by cannontrodder on 2007-10-23
I posted ^^^^ just up from here and am now happy to say everything is working better for me.

My solution? Backup user data and rebuild it! The xorg auto config dialog did not even show up this time, I just got a standard nvidia open-source driver powered x server and a reminder about restricted modules. In there were notices for my soft-modem, nvidia card and my broadcom BCM4306 wireless network card.

Configuring the nvidia drivers was as simple as clicking on 'enable' in the restricted modules manager . Direct rendering worked perfectly afterwards. It's nice to have Envy as another option, but I think it is largely redundant as the performance I am getting is the best I have ever had from this card under Linux.

As for the wireless settings, I had often used ndiswrapper with the bcmwl5.sys extracted from the windows driver zip my laptop manufacturer provide. To cut a long story short, it doesn't work 100% of the time and cannot be relied upon. I got the same problem with fwcutter using the link to firmware they provide in the install dialog BUT if I over-ride that and tell it to get the firmware from my bcmwl5.sys file - it works!

So it was a painful upgrade but a painless install and I now have better wireless and video performance than I have ever had. And compiz works very well for me, it even applies wobbly windows to VirtuaBox when running XP. I have no complaints at all now, so well done for Gutsy. I'm still a little worried about doing an update but it's clear the issue were caused by custom hacks that once held my video and wireless settings in place. Now they are more officially supported, things should be better in the future.

---

### Post by flinkman on 2007-10-24
well these are my problems after a fresh install, not after an upgrade from feisty.

---

### Post by scott2004 on 2007-10-25
With regard to "bugs" I can only speak for myself and my experiences in installing i386 and amd64 versions on 4 separate machines have been amazingly positive. Indeed, I've found each successive version of Ubuntu since 6.04 to be an encouraging improvement on previous versions. Perhaps the problems above users have been complaining about are hardware incompatibilities.

In any case, it's extremely disrespectful to the numerous volunteer developers and other contributors to describe Ubuntu as "buggy as hell". If you find a bug or bugs, file bug reports---that's what will help improve the product. 

Assuming you are bonafide Ubuntu users and not just out to tar the product, please take a moment to contemplate the meaning of "Ubuntu", of GNU, of open source and free software. It all boils down to community and cooperation and the vitriolic comments of some of the above users really have no place in this environment.

If you're so unhappy with Ubuntu that you have to go on a public tirade, then please, go back to Vista where you can have many more bugs and pay top dollar for them.

Otherwise, show some appreciation for what is made available to you for free and for the countless contributors who have donated their time and talent.

Scott

---

### Post by Em-Buntu on 2007-10-25
> **jrickard said:**
> AND you have the added benefit of being quite correct.  That this software was ever released is absolutely inexcusable.  All the monkey spunk I"ve been going through to get their release CD to even 
boot was just a joke.  Now, a black screen on the boot off the hard drive.  There are 3000 messages on here from people with exactly the same problem (and I guess they all don't have a clue either) and 
no help.

I'm disgusted with Ubuntu.  This is a mess.  Kids with compilers run amuck.

Jack Rickard

I got the black screen also following the upgrade.
It forced me to start anew with a fresh install. Following that, I got the black screen again, so I rebooted and used the limited graphics boot option. This booted minus the GUI. Once it completed, I was left at the command line. I exited from this, and the system booted into Gutsy. 
You are correct in that the upgrade procedure seems to be lacking in sufficient testing prior to release and causes too many needless issues.
However, realizing that nothing free is truly free, and early releases can cause you to have to put in some sweat equity.

Overall, I'd say that Gutsy has a lot of increased functionality, however the issues with Firefox browsing/IPV6 or whatever is causing the bad browsing experience is inexcusable. To be considered a real Windows alternative, this base feature needs to work almost flawlessly out-of-the-box.

---

### Post by BinaryMadman on 2007-10-26
@Em-Buntu,

What problems are you having with Firefox and IPV6?  You could disable IPV6 in Firefox by entering "about:config" in the address bar and typing 'disableIPv6'.  Choose the first item to come up and set the value to "True".  To disable it from Linux altogether, follow this [quick guide]("http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html") (you can replace vim with gedit if need be).

Regarding Ubuntu being "buggy as hell", I have not experienced anything that has been mentioned so far in this thread.  Much more stable than previous versions, for me at least.

> It would have been more correct to say "Help, don't know quite what I'm doing"...
Well said.  I was a tutor at my old college and I noticed there were two types of people who would come in: those who didn't understand how something worked and politely asked for help, and those who came in starting arguments in a backhanded way of asking for help.  There are quite a few of the latter in this thread.

Instead of starting a thread about how "Ubuntu is buggy as hell", how about starting a thread asking "How can I get Xyz to work properly?"  There are plenty of nice people here willing to help.  [**Ubuntu**]("http://en.wikipedia.org/wiki/Ubuntu_(ideology)")

---

### Post by guitard00d on 2007-10-28
> **BoardDWorld said:**
> P.S. After all the fine work that has been done it isn't very nice making a statement that "7.10 is buggy as hell" in Ubuntu forums. It would have been more correct to say "Help,  don't know quite what I'm doing"...

I have to disagree...I know full well what I'm doing in Linux and have been at it ever since Gentoo was "the new kid on the block".

7.10 is buggy as hell, all previous versions installed on all of my machines with absolutely zero problems. The "fine work" you mention that went into 7.10 is more like "let's hurry up and get this thing out the door so we can stick to our 6 month release schedule promise". They've succeeded in smearing egg all over their faces and making themselves look like fools and probably succeeded in scaring away a lot of potential OEMs that were anxiously awaiting the new release.

Facts are facts...If it wasn't buggy as hell, there sure wouldn't be so many messages from people complaining about installation problems that they've never had before. *snip*

---

### Post by High Camp on 2007-10-28
> **BinaryMadman said:**
> 
Well said.  I was a tutor at my old college and I noticed there were two types of people who would come in: those who didn't understand how something worked and politely asked for help, and those who came in starting arguments in a backhanded way of asking for help.  There are quite a few of the latter in this thread.


I agree, there are too many people in here simply saying this doesn't work, it sucks. I tried to upgrade 3 times and had errors so I backed up my data and did a fresh install and now everything works perfect. Yes it took me a day to do this but if I add up all the time I spent fixing stuff in XP it was much longer. 

Coming in here and saying Ubuntu sucks is sort of like going into a biker bar and saying bikers suck. You're talking to the wrong crowd and you can expect to be the least popular person in the room, WHICH YOU ARE.

In addition, if you are currently running  XP and want to run Vista (not that I recommend it) could you simply click an upgrade button or download the cd, burn, and install? Hands down the answer is no. 

My mother bought a laptop and the first thing I did was wipe Vista and put XP on it. The reason for this is that MS often leaves some major security holes in their systems. I'm happy to say that as far as I can tell this is generally not the case with Linux.

That's my $0.02CAD (it's worth more in Canadian).

---

### Post by prit on 2007-11-02
I have been a Ubuntu user for the last 3 versions - Dapper, Fiesty and Edgy. I just loved and promoted Ubuntu. Distributed CD's. Educated friends and family about Ubuntu. I ran my servers on Ubuntu.

I upgraded to Gutsy and started having problems. So I removed the partition and then did a clean install. Things looked good initially. Then I realized that the network does not work. Wired or wireless - both dont work. Then I read that you have to disable IPv6. I will try it later. But my question is - why should you do this? If the previous versions didnt have a problem, Gutsy should be better. 

Rather than promising releases every 6 months, a highly tested quality version would be more appreciated. 

At this point I tried out PCBSD. This worked extremely well for me on my Averatec 3200 laptop. Flash, WMV, streaming music and video - all worked out of the box. They have a great installer PBI - that can be used to install common application in a single click.

---

### Post by jcollins on 2007-11-02
I just downgraded to 7.04. I am very sorry to admit it but 7.10 is definitely not ready. 7.04 is bug free for me. I am a hardcore Ubuntu fan, and I really hope that this doesn't give them a bad name since Dell is shipping this version.

Bugs I noticed were horrible wireless support, when changing wireless networks, it would not switch for anything and since there is no force refresh, it is very difficult to connect anyway.

Also the gdm was screwed up for the longest time, turns out that it doesn't like refresh rates. I fixed that one though.

I am just glad that I didn't upgrade my server to 7.10, I had a feeling.

---

### Post by fdv1 on 2007-11-03
I'll throw my 2c in. I've been using Kubuntu since 510 and increasingly moreso with each version.

Though he was being funny, **kamaboko**  said it best: "It's only buggy if it's a MS product. For all other OS's one has to say, 'help...I don't know what I'm doing.' 

-Shrugs- 

I do a clean install every time to avoid issues like these. 710 brought things I had never even seen before, most notably the [hal-storage-removable-mount-all-options refused uid 1000 error]("http://ubuntuforums.org/showthread.php?t=601210"). Never mind beryl, the printing system, and using apt-get that made the system lock up(!). 704 never did any of this.

So, yeah. I appreciate the work that goes into each release. But I think it's WAY out of line to tell anyone that they're doing the wrong thing by posting that they have problems with a new version. If they want to hint at it, or if they want to outright b-tch about it, I don't care what tone they use. I want to read about the problem, weigh their experience, and decide if it's them, or the software. And in this case, I think it's the software. It's one thing not to tolerate the tone of his message, *but not tolerating the content* is another thing entirely.

---

### Post by masai489 on 2007-11-16
I totally agree with this statement. To not be able to take the criticism is a little fanboyish. I love this system like the next man and am really trying to get off of suckysoft. But I shouldn't have to reinstall my entire os when it's supposed to be an "update/upgrade". I'm a guru with MS and I've never lost my email settings or graphical settings the way I did now. And I have begged for help and really haven't gotten any concrete answers on how to get my system back the way it was. I had compiz/fusion running beautifully. Now I can't even open the Compiz setting manager without getting this error:
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
Now honestly, I have no idea what to do. I had to see what was the problem when the shortcut didn't work so I ran the command from the console and got the above. And Thunderbird..I had that running great, retrieving my yahoo emails and now it's all gone. I've moved the folder as everyone said to do and still can't see any of my emails...my settings are all off. So ok..great a lot of people did a lot of hard work but if it's causing the amount of problems it is, and no one has any real answers, then I have to agree...7.10 is buggy as hell!

:guitar:

---

### Post by Chriswaterguy on 2007-11-16
I'm glad to be away from Windows, but I haven't stopped swearing at my computer. I consider this a worthwhile investment of effort both for myself, and for the cause ([low cost computing]("http://www.appropedia.org/Low_cost_computer_guide"), ICT for Development) that I support. I really want Ubuntu to be good. But at the moment, I would certainly not recommend a newbie to try Ubuntu or any other Linux I know* unless they have geeky friends very close by. Geeky friends will definitely be needed. 

The following "solution" is the kind of thing I find most frustrating in Linux, including Ubuntu (note that the frustration is directed at the software and lack of organized documentation, more than at the commenter): 

> **BoardDWorld said:**
> I think perhaps that in regards to effects you're going about things in an out-dated method. 

With Compiz-Fusion, both on Feisty and Gutsy, everything is controlled via the "Advanced Desktop Effects Manager". Gutsy doesn't have this package by default install it with the following:


So, we're *supposed* to do it with a package that is not installed, that we don't find out about unless we trawl through forum postings? Something is wrong here. But this is typical in Ubuntu (can't comment on other distros). Obvious things like microphone settings - turned off by default. Why? A download page that implies "Download, install and have fun!" when it should be linking to tutorials and giving several key bits of friendly advice. 

And buggy? Yes. It sure doesn't work smoothly, and partly that's through lack of documentation, and partly through bugs. 

It doesn't seem as buggy as my install of  Xubuntu 7.04, which was appalling - but that may have been from trying to tweak it, which I'm now avoiding (in my fresh install of Ubuntu 7.10) and maybe from trying to install certain programs with a near total lack of clear instructions. I'm getting there slowly - but like I say, I would NOT recommend this to a newbie without a good support team of geeky friends.

*I might recommend OpenSUSE from what I've heard, but haven't tried it myself. Geeky friends still very, very desirable.

---

### Post by kjurkic on 2007-11-16
I was an Ubuntu fan until the "upgrade" from 7.04 to 7.10, which broke at least 2 EXTREMELY critical (to me) items:

CD burning - I now only get coasters (BTW makeisofs was BROKEN in 7.04 too)


VMplayer - Needed for some development work. the *upgrade* process killed my VMware, did not TELL me it was going to break it BEFORE I started, did NOT offer to fix it, and now when I try to install new from VMware, I get error that it is already installed (but its NOT!! Or at least it is broken).

I am not a noob; I have performed hundreds of installs since I first played with slackware in the mid-90's. I do not consider myself hardcore linux guru, but I have enough experience to say this is a BROKEN O/S. I should NOT have to perform a clean-sheet install; I might as well move back to Microshaft products if this is going to be the recommended procedure.

I know that the developers cannot test all possible combinations of hardware & software; but I fell victim to the upgrade nag screen (7.10 is now available, do you wish to upgrade?) If Ubuntu wishes to maintain its momentum, the developers should consider removing the upgrade facility, & informing users that they should plan fresh installs instead. I cannot convince others of the benefits of linux when there is no DEMONSTRABLE improvement in the end user computing experience. It is even harder when technically proficient folks, such as the posters here, get bitten so badly.

:-k

Ken

---

### Post by masai489 on 2007-11-17
This should be pinned. There are serious problems and help is needed in addressing them.

---

### Post by Chriswaterguy on 2007-11-18
This would be at least partly solved by being more upfront and honest about the problems. Don't leave people to find out through painful experience that suspend doesn't work, or that they need to do some fancy geeky stuff to get a certain feature to work. Own it, be upfront and say "you'll have to tweak some things and be careful with programs X, Y and Z - but it's worth it! And you can help us to make it better by filing bug reports and adding to the wiki!"

I appreciate the software and the community, but these are really spoiled by this false representation of Ubuntu as a package that can be just downloaded and used without expecting problems. **This is misleading**.

---

### Post by rsambuca on 2007-11-18
> **Chriswaterguy said:**
> This would be at least partly solved by being more upfront and honest about the problems. Don't leave people to find out through painful experience that suspend doesn't work, or that they need to do some fancy geeky stuff to get a certain feature to work. Own it, be upfront and say "you'll have to tweak some things and be careful with programs X, Y and Z - but it's worth it! And you can help us to make it better by filing bug reports and adding to the wiki!"

I appreciate the software and the community, but these are really spoiled by this false representation of Ubuntu as a package that can be just downloaded and used without expecting problems. **This is misleading**.

The problem is that it is completely hardware dependent.  For most, things do just work.  for others, things don't.

---

### Post by Chriswaterguy on 2007-11-18
> **rsambuca said:**
> The problem is that it is completely hardware dependent.  For most, things do just work.  for others, things don't.

Not sure if it's "completely." Suspend, for example, seems to not work on a lot of laptops, possibly all. I'm using a Thinkpad, which is supposed to be the most compatible laptop for Linux. 

Anyway, my point still holds - a lot of people have a lot of difficulties. Pretending everything will be easy is misleading. Making some simple effort in this regard would be something - even if just a readme.txt file that pops up after installation, also available via the download page. It wouldn't solve everyone's problems, but it might make a lot of them easier to solve or at least avoid. 

Considering how much work is put in overall, this is a very small thing that would have so much value.

---

### Post by mimsmall on 2007-11-19
Fresh Install of Gutsy. HP pavilion ze4000. Worked fine with Dapper. Evolution and Thunderbird email clients will not access SMTP server.

---

### Post by leftclick on 2007-11-20
<rant style="geek:100%;">

First of all, the statement "Ubuntu 7.10 is buggy as hell" is boundless.  There is no reference point; buggy compared to what?  

- Compared to CP/M 3.1?  Yeah sure it is, but it also has a million more features!  
- Compared to Windows Vista?  You're kidding right?  
- Compared to some other distro, such as Ubuntu 7.04 or YourNeighboursLinux 3.14159?  Well go install that then, open source is all about choice.

That said, the title was obviously intended to draw attention, and that it did to some degree.

In response to the thread as a whole, I think some people are expecting far too much.  If some things are broken, fix them, or go back to what you had before.  The things that people are complaining about aren't show-stoppers anyway, for the most part.  Do you go to the fonts tab of the settings dialog that often?  Do you really need a framebuffer (why not just use a vga console)?  If you really need all these things to work, and you can't find help on the forums, pay for some support.  I bet it will still cost less than Vista.

As a developer, I find it impressive that there can be a one-click solution to upgrading the entire OS.  I have done this on 2 different laptops, both with custom kernels, and both went mostly smoothly (one won't run compiz, the other will but won't run gl applications e.g. glxgears).  Migration can represent a difficult problem, and there are many poor solutions out there.  This is not one of them.

</rant>

---

### Post by ImpressMe on 2007-11-22
> **BoardDWorld said:**
> P.S. After all the fine work that has been done it isn't very nice making a statement that "7.10 is buggy as hell" in Ubuntu forums. It would have been more correct to say "Help,  don't know quite what I'm doing"...

[-( So, bugs are user errors? =;

No, it would not be more correct to say that. We had tons of problems with 7.10 and the recent huge amount of updates tells me, that once again we where release candidate testers. I have tried that with another Ubuntu release.

Linux isn't impressively compatible with all the hardware out there, and it fails in a spectacular way now and then. It is not the users fault, and demanding that they go here and explain the problem as THEIR fault is arrogant.

Do you remember Windows 95? If it crashed it would check the file system during the next reboot, telling people that to avoid this error message they should shut down  their computer correctly! CORRECTLY! The damn OS froze and forced you to kill it, and then they accused YOU of doing something wrong. User error my ****.

That is essentially what you told the OP. Don't expect people to come here as humble servants. Let them cry out. We have all been there with Linux. If you want a constant grateful tone from your user base then you should work in North Korea.

---

### Post by nuir on 2007-11-23
> **Chriswaterguy said:**
> Not sure if it's "completely." Suspend, for example, seems to not work on a lot of laptops, possibly all. I'm using a Thinkpad, which is supposed to be the most compatible laptop for Linux.

Well, just for the record, suspend works perfectly for me, I'm using a Lenovo. In fact, Gutsy has been in my case the least buggy of all my previous installations. My biggest one yet was the tiny emblems in nautilus. Gutsy works fine both in my laptop and my desktop. (clean install on both of them). Wireless worked from the beginning, and so did everything for me.

I'm not saying my system is bug free, but most of my problems are bugs that haven't been solved for quite some time, like my laptop not recognizing a network cable access unless going into suspend mode... but thankfully none of them are really serious. But to be honest, there are still MANY things not just right, not yet at least. 

I totally agree that you cannot expect a new user to know that a certain package, not installed, is needed to configure something already there by default (compiz, scim, etc). Or that maybe a lot of things may go wrong because of previous packages installed, or that for whatever unknown reason his/her hardware seems to work fine in the LiveCD but not when Ubuntu is fully installed. (All of these happened to me in previous versions).

To avoid some of these problems I never upgrade to a new version, always do a clean install. Instead of having a separate /home partition, I just put my documents in a /documents partition, everything else gets reformatted (including /home). But even though Ubuntu forums are just one of the greatest online community I've been to, it still may be too much for new -and not so new- users, who may just stick to their pre-installed Windows or whatever else they are comfortable with...

Ubuntu is still a work in progress, and is not fully mature yet, but given the other choices out there... I'm totally convinced this is one of the best.

---

### Post by Lagos on 2007-11-23
ill have to agree. this is my first time using ubuntu, so i cant compare it to older versions, but i was shocked at how many bugs i keep running into. everyone always says how stable linux is, yet this reminds me of the the win95 days. 

here are some of the bugs/issues i ran into. 

installer:
fails to properly detect my monitor, and therefore refuses to load up into the desktop (live cd), giving an error msg that it failed to initialize the display.  Workaround: turn off monitor during bootup, so that it just defults to 60htz. this is the first time ive ever seen an os have a problem with a monitor. 

gparted:
works great, but crashes after it just made a change.
workaround: just keep relaunching it.

installer:
good luck if you are trying to install the OS in 800x600 from the live cd desktop. while everything functions correctly, the install menu cant be resized, so it ends up that the BACK/NEXT buttons get cut off at the bottom of the screen and cant be pressed.

wifi: the OS seems to not want to connect to any secure wifi point that has SSID broadcasting turned off.
workaround: turn on ssid

wifi driver wrapper:
not really a bug but a dumb issue..
ubuntu gives you parts of the app preinstalled, but not the whole thing. you have to download the gui and some utility package. problem is, that you need an internet connection to do this. why not just include the whole damn app!?!?!?!

suspend hybernate:
dont work at all. they just hang. 

start up:
sometimes the os will stop during boot up. reset the power, and it boots back up perfectly. 

etc...etc...etc..

despite all of this, and more issues that ive run into, i have to say that i really do like the OS. i just wish they would iron out all the obvious issues.

was feisty more stable for most people? do you think it might be worth while to try to downgrade to it?

---

### Post by woland on 2007-11-23
This thread has slided to personalities too much for my taste.

Lets be practical. The fact that Gutsy's bugs are much more annoying that it was with Edgy.
Now the question is what can be done about that?
[LIST=1]
[*]To figure out the reasons for the most of the problems and to make a HOWTO on  a trouble free Gutsy install.
[*]To downgrade to Edgy
[*]To switch distro
[/LIST]

Personally I prefer that first option. Unfortunately I lack the expertise and time to do that.

I believe that we need to pass this notion to Ubuntu development team.

---

### Post by barbex on 2007-11-23
> **Lagos said:**
> 
good luck if you are trying to install the OS in 800x600 from the live cd desktop. while everything functions correctly, the install menu cant be resized, so it ends up that the BACK/NEXT buttons get cut off at the bottom of the screen and cant be pressed.


This has been pissing me of since Breezy (5.10)! My Multimedia server has a little screen with only 800*600 and every day I find some dialog in the system where I can't see "Apply" or "Cancel". Yes, bigger is better but please make this stuff resizable so I can at least see what I'm doing.

---

### Post by willie_wang on 2007-11-28
:) :) :) :)

Ok. Some solutions to the original post. I have to admit that I found exactly the same problems... I must thank the Ubuntu development staff, you're doing a stunning job - so much so, that even complete noobs with a brain cell count I can sum up using my fingers and toes can work out (eventually) how to get the most of Ubuntu... so, here goes! :)
**1.**

> When I go to "GL desktop" from the system preferences menu, nothing happens. When I try it again, the GL desktop settings dialog appears, but none of the changes that I make take place.

If this problem occurs, try uninstalling the GL Desktop menu option by going to Synaptic PM and uninstalling "gnome-compiz-manager". You need to be using the "compizconfig-settings-manager" instead, along with "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-main". it's up to you if you want to install the extra compiz-plugins.

This will create a new menu item under System > Preferences > Advanced Desktop Effects Settings.

**2.**
> That, and compiz-fusion doesn't have any of the features that I liked in beryl to begin with (transparent windows, etc.)

In the Advanced Desktop Effects Settings you'll be able to do everything you were able to in the buggy GL Desktop AND MORE... just takes a little playing about (which is actually soooo much fun) to learn what all the options do.

**3.**
> The GL desktop tray icon seems to randomly appear in the taskbar, but doesn't seem to be able to communicate with other processes (if I try to save my session in Gnome when the compiz icon is in the taskbar trey, the session manager just hangs and finally pukes up an error about the compiz trey icon, and invoking the GL desktop settings from the trey icon dosen't do anything)

The GL Desktop tray icon can be very buggy on some machines. It was on mine too. There's a much better alternative that is just as good! It's called the fusion-icon. [CLICK HERE and Follow the instructions here to get it]("http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/").

Press Alt-F2 for the application and type in "fusion-icon" to launch the tray icon. If you want your system to load this on boot, just go to System > Preferences > Sessions > Additional Startup Programmes and then add fusion-icon to the program list.

Hope this helps someone. It took me a good hour to figure this one out myself!

:KS

Anyway, thanks again to everyone who contributes to these forums. You've all encouraged me to do the same. And thanks again to all the Ubuntu Developers and testers! This post'll probably be missed by everyone, hehe :) , but here's trying anyhow :)

---

### Post by buntunub on 2007-11-28
All in all, Gutsy probably does take the record for the most unstable release yet. Its a mixed bag though, because what does work, works well, and its enough to keep me coming back for more. The REALLY annoying bugs are all graphics related, which puts them into the critical bug catagory in anyones book. Other than the completely worthless "Screens and Graphics" utility, which borked my system up to no end, and the "unbreakable X", which combined with the former, really did a one - two punch on my somewhat limited command line talents. Then, direct rendering just decided to stop working, and my Nvidia driver just seemed to go on vacation for some crazy reason unbeknownst to me. Suspend and Hibernate work flawlessly time and again on my HP Lappy. In fact, EVERYTHING worked out of the box on my Lappy, including the webcam, keys, and wireless. And then, there was the Dual-monitor fiasco that turned my Lappy experience sour real quick. Cant say that Feisty was flawless either, because all the things that worked out of the box in Gutsy, failed badly in Feisty.

---

### Post by Habu on 2007-11-28
Wow, it interesting how different people have different experiences.

In my case, I upgraded to 7.10 from 7.04. I run the advanced desktop with the cube and transparent windows and other effects, like wobbly windows, turned on (with an old Gateway 1 GHz AMP Atholon, 512 MB DRAM, Nvidia Ti4400 video). The only problem that I've noticed is a runaway process that usually occurs after the PC is sitting idle overnight. Seems to be Xorg, but not sure about that, yet. Problem is solved by logging out/in. Not desirable, but not a show stopper. I can burn CD's, rip CD's, connect to my MP3 player, websurf, etc.

For a free OS, I can't really complain. I've had worse experiences with MS OS's. I appreciate the work that Ubuntu's dev's are doing.

Also, I don't want to minimize the problems others are having. Believe me, I've been there. But, the fact that Ubuntu is working well for many of us shouldn't be ignored either.

---

