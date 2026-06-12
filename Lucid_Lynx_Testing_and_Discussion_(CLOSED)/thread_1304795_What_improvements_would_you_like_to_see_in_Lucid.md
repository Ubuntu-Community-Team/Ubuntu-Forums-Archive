---
title: "What improvements would you like to see in Lucid?"
date: 2009-10-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2009-10-29
This is the one I would like to see:

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

Now this is a pretty big feature to do but for Lucid I would at least like to have deltas for package lists (ie. the files you download with apt-get update to see if there is an update).
This would save time and bandwidth for all.

---

### Post by Robin Nixon on 2009-10-29
Networking - Networking - Networking!

Make it so I can connect to any network drive anywhere I'm allowed and STAY connected after a restart WITHOUT having to edit any config files. I mean, let this all happen with point and click the way other operating systems such as, well, OS X and Windows allow, for example :)

---

### Post by whoop on 2009-10-29
[https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)

I know it's all possible already, but make the configuration a little easier, or at least get some up to date usable documentation on this stuff.

There are allot of companies not moving to linux because of this. What are you gonna do if it's a total hassle to setup a network where any user can get to his/her own account from any computer. It's not like they are asking for useless functionality. Why is all the documentation either incomplete or outdated?

---

### Post by MacUntu on 2009-10-29
An AeroSnap rip-off (yeah I know about compiz's grid plugin, but that's not the same).

[http://brainstorm.ubuntu.com/idea/20560/](http://brainstorm.ubuntu.com/idea/20560/)

---

### Post by TrueTom on 2009-10-29
Fixing bugs while not breaking things that already worked would be a start...

---

### Post by ViRMiN on 2009-10-29
RAID, LVM and crypto installation options via Live CD maybe?  Is that possible?

---

### Post by froggyswamp on 2009-10-29
Sound, finishing the boot experience and the software center. And if Chrome goes final and has a _good_ adblock-like extension make it default (Ubuntu is about speed, especially on netbooks, remember?).

edit: anyway, where are the daily Lynx ISOs? kidding..

---

### Post by gnomeuser on 2009-10-29
BtrFS support. Lucid will most likely ship with .32 (or later), Chris Mason states that this kernel will have a btrfs version he is comfortable giving to early adopters. Karmic was a perfect time to add preview support, now it's just overdue.

Death to AppCenter, aptdaemon, xsplash - welcome our plymouth and PackageKit overlords (hey I can wish for sanity, it doesn't mean it will happen).

Removal of Ubuntu One from the default install or a release of the server side code - sorry I still don't trust my data to source I can't see and I do expect better from a Linux company.

Pulseaudio finally being implemented as recommended by upstream.

Banshee as the new default mediaplayer.

Chromium instead of Firefox.

Working A/V for MSN in Empathy (this should be doable, upstream now has 2 full time people working on Empathy).

---

### Post by TrueTom on 2009-10-29
> **MacUntu said:**
> An AeroSnap rip-off (yeah I know about compiz's grid plugin, but that's not the same).

[http://brainstorm.ubuntu.com/idea/20560/](http://brainstorm.ubuntu.com/idea/20560/)

+1 

Though, thanks to Gnome Shell investing time in Compiz got pretty pointless.

---

### Post by stef70 on 2009-10-29
> **zekopeko said:**
>  I would at least like to have deltas for package lists 

I agree with that! Probably not trivial to implement since the package lists are updated quite often and you can't really expect to store more than a few diff files on the server.  

An alternative method could be to provide a smaller file giving only the version number of each package. That should be enough to figure out if updates are available for the installed packages.

---

### Post by Merk42 on 2009-10-29
> **gnomeuser said:**
> Pulseaudio finally being implemented as recommended by upstream.[SIZE="4"]**+1**[/SIZE]

Having  done a clean install I see my webcam still has issues with Skype. Also I've already seen a few threads in General Help where the solutions were "remove pulseaudio, use alsa".

---

### Post by Reiger on 2009-10-29
> **MacUntu said:**
> An AeroSnap rip-off (yeah I know about compiz's grid plugin, but that's not the same).

[http://brainstorm.ubuntu.com/idea/20560/](http://brainstorm.ubuntu.com/idea/20560/)

Unless I am much mistaken the feature is in KDE in 2 separate Kwin effects... 

Anyways what I would like: additional hardware signatures in a device driver. {0x0B05, 0x1761} and {0x1761, 0x0B05 }. In the rt2870 driver; in kernel 2.6.32.

Merci en avant,

---

### Post by zekopeko on 2009-10-29
> **Merk42 said:**
> [SIZE="4"]**+1**[/SIZE]

Having  done a clean install I see my webcam still has issues with Skype. Also I've already seen a few threads in General Help where the solutions were "remove pulseaudio, use alsa".

Isn't this Skype's problem?

---

### Post by stef70 on 2009-10-29
Easy mount/umount of fuse filesystems via the Disk Mounter applet in gnome (with dialog to enter password if needed).

As of now, they only appear in the applet after I mount them manually using sshfs or encfs. The applet provides an Unmount action but it does not work.

---

### Post by zekopeko on 2009-10-29
> **whoop said:**
> [https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)

I know it's all possible already, but make the configuration a little easier, or at least get some up to date usable documentation on this stuff.

There are allot of companies not moving to linux because of this. What are you gonna do if it's a total hassle to setup a network where any user can get to his/her own account from any computer. It's not like they are asking for useless functionality. Why is all the documentation either incomplete or outdated?

This would rock! The question is how do you display options for average businesses while avoiding having X server running?
I like how the OSX server has a GUI for enabling common servers roles. But on the other hand it's wasting resources if it has a GUI running.

One option would be to have a stripped down GNOME, only with an application running that can configure those things (like the Install Ubuntu menu option boots directly into Ubiquity).
Or even better.

Have a small web server that talks to a settings daemon. That way you could simply go to a web address and click the things that you want. Something like Deluge does e.g. having a daemon that sends things over to the GUI on another computer.

---

### Post by lykwydchykyn on 2009-10-29
> **zekopeko said:**
> This would rock! The question is how do you display options for average businesses while avoiding having X server running?
Browser interface?

Samba 4 sounds like the ticket, but it's anyone's guess when that will be ready.

---

### Post by zekopeko on 2009-10-29
> **gnomeuser said:**
> BtrFS support. Lucid will most likely ship with .32 (or later), Chris Mason states that this kernel will have a btrfs version he is comfortable giving to early adopters. Karmic was a perfect time to add preview support, now it's just overdue.

I get the feeling that you think this is Fedora. Fedora might like doing this sorts of things because it targets more technically inclined people but Ubuntu likes things at least that are stable.

> Death to AppCenter, aptdaemon, xsplash - welcome our plymouth and PackageKit overlords (hey I can wish for sanity, it doesn't mean it will happen).

I like what mpt is trying to do with USC. Far better then the mess that is Packagekit-gnome/kde.

> Removal of Ubuntu One from the default install or a release of the server side code - sorry I still don't trust my data to source I can't see and I do expect better from a Linux company.

This is just short sighted of you. Ubuntu One can become a killer app for Ubuntu and Linux. The protocol is open and nothing is stopping people from creating their own servers. And it's not like it's forced upon you.

> Pulseaudio finally being implemented as recommended by upstream.

Perhaps the PA creator could engage directly with Ubuntu folk and point the ways they fail in this?

> Banshee as the new default mediaplayer.

I hope they fix show stoppers by Lucid. Finally having a great looking and performing player would rock.

> Chromium instead of Firefox.

I would use Chromium only for the Netbook Remix. Firefox is probably better for  vanilla Ubuntu.

> Working A/V for MSN in Empathy (this should be doable, upstream now has 2 full time people working on Empathy).

I don't see this being a problem. Considering the rapid development Empathy has seen in Karmic I hope the effort persists and we see great things in Lucid.

---

### Post by zekopeko on 2009-10-29
> **lykwydchykyn said:**
> Browser interface?

Samba 4 sounds like the ticket, but it's anyone's guess when that will be ready.

Yeah I was thinking along those lines. Like Deluge does it.
Decouple the server from the client interface.

---

### Post by celticbhoy on 2009-10-29
+1 for chromium - although it would need some time to get it ready for first choice.

---

### Post by Merk42 on 2009-10-29
> **zekopeko said:**
> Isn't this Skype's problem?

Considering Skype 2.1 ONLY uses Pulseaudio, it is a webcam problem at best.
Regardless the other threads in General Help I was talking about weren't just exclusive to Skype problems.

---

### Post by whoop on 2009-10-29
> **zekopeko said:**
> 
Have a small web server that talks to a settings daemon. That way you could simply go to a web address and click the things that you want. Something like Deluge does e.g. having a daemon that sends things over to the GUI on another computer.

Yep, browser interface would do it. To be perfectly honest I would have no problem doing everything in the command-line (everything to keep my server headless). We definitely need an up to date howto/tutorial (for minimal and/or maximal functionality) to say the least. 
I mean, this is the most accurate howto I ever found on the net: [http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3) and its for ubuntu **7.10**
This is even more important for LTS releases.

---

### Post by PilotPaul on 2009-10-29
I'd like to see improved mobile phone integration and synchronisation...its the only thing Windows does better any more, and that's largely down to the application software supplied by the manufacturers...be nice if ubuntu coped with at least the mainstream mobile phones out of the box...

---

### Post by pythonscript on 2009-10-29
+1 on domains! I know a lot of people in a corporate environment that would consider moving to Linux if this were possible. The file permissions model would already work for something Group Policy-like anyways (because if you're not sudo, you can't do certain things anyways) as well as the removal of Ubuntu One. I realize it's Canonical's paid service... but I'm not paying for it, so why should the software be included?

---

### Post by castrojo on 2009-10-29
> **gnomeuser said:**
> Pulseaudio finally being implemented as recommended by upstream.

The kernel bits Lennart recommends will be in the Lucid kernel (they're upstream now).

> 
Banshee as the new default mediaplayer.

Chromium instead of Firefox.

Working A/V for MSN in Empathy (this should be doable, upstream now has 2 full time people working on Empathy).

There won't be large changes to Lucid like the switching out of default apps,  however the MSN/Empathy thing should be doable. (I had a sticky in the last dev forum about it)

---

### Post by whoop on 2009-10-29
> **lykwydchykyn said:**
> 
Samba 4 sounds like the ticket, but it's anyone's guess when that will be ready.

I have some (partial) problems with samba 4:

1: It doesn't help me now (obvious, like you stated).
2: It's primarily aimed and windows interoperability. Although I am all for interoperability, I would like to see interoperability as a plus and functionality within linux as a **must**.

Even though this all works already in linux, nearly no one will get this up and running because nearly no one will know how. And the problem is no one can find out how, cause there is no accurate, complete, detailed and up-to-date documentation on this topic.

---

### Post by lykwydchykyn on 2009-10-29
> **whoop said:**
> I have some (partial) problems with samba 4:

1: It doesn't help me now (obvious, like you stated).
2: It's primarily aimed and windows interoperability. Although I am all for interoperability, I would like to see interoperability as a plus and functionality within linux as a **must**.

Even though this al works already in linux, nearly no one will get this up and running because nearly no one will know how. And the problem is no one can find out how, cause there is no accurate, complete, detailed up-to-date documentation on this topic.

I know what you mean; it'd be nice to see something like 389 Directory Server get a nice interface and point-n-click client interface.  But you KNOW that as soon as Ubuntu came out with some kind of directory solution, the first thing people would want to know is if it worked with their Windows machines.  

I guess we can always hope that Novell will open source eDirectory. :)

---

### Post by stef70 on 2009-10-29
ARM based netbooks could well be the next big thing in 2010:

[http://www.engadget.com/2009/01/09/pegatron-and-freescale-team-for-low-power-ultra-cheap-netbooks/](http://www.engadget.com/2009/01/09/pegatron-and-freescale-team-for-low-power-ultra-cheap-netbooks/) 
[http://www.geek.com/articles/chips/arm-to-shake-up-netbook-market-with-dual-core-cortex-a9-20090917/](http://www.geek.com/articles/chips/arm-to-shake-up-netbook-market-with-dual-core-cortex-a9-20090917/)

If they become a reality, I will be seriously considering replacing my current laptop. 

Support for ARM is already started at [http://www.ubuntu.com/products/whatisubuntu/arm](http://www.ubuntu.com/products/whatisubuntu/arm) but, looking at the current release notes, they still seem far from being ready for mainstream use.

---

### Post by Vanishing on 2009-10-29
-more security
-boot time(of course)
-look and feel(who doesnt..o.o)
-performance..
-entertainment(games, audio video)
-more cloud plz..
-more ubuntuers or linuxers!!!!
am i too greedy?:p

---

### Post by bluebyt on 2009-10-29
[QUOTE=whiprush]The kernel bits Lennart recommends will be in the Lucid kernel (they're upstream now).[/QUOTE]

Sorry I don't understand this statement whats is kernel _bits_? and who is Lennart?

---

### Post by Garyu on 2009-10-29
> **Robin Nixon said:**
> Networking - Networking - Networking!

Make it so I can connect to any network drive anywhere I'm allowed and STAY connected after a restart WITHOUT having to edit any config files. I mean, let this all happen with point and click the way other operating systems such as, well, OS X and Windows allow, for example :)

Having been on Windows 7 RC for half a year, I have to say I love the networking part there. Sharing files over a network was never easier. I also love the fact that I can transfer settings for e-mail etc over the network, so I can keep a copy on each of my machines of identical Outlook folders/accounts/etc. 

So yeah, networking. Easy networking for dummies. 'Cause it also saves time for those who know what they're doing.

---

### Post by jrothwell97 on 2009-10-29
Documentation, documentation and documentation.

Seriously, at present, Ubuntu's help system is inconsistent and highly incomplete. The help file for GNOME Terminal, for example, provides no information for a first-time user on how to actually *use* the terminal, what the basic commands are, why you *shouldn't* run sudo rm -rf / *, etc.

Also, although Karmic's revised UX is nice, Lucid must focus on *polish*. Make the look consistent across every single app, regardless of whether it uses Qt3, Qt4, GTK, plain X, whatever. Fix the nagging issues like the bizarre "nipple" in the top left corner of the window, the oversized toolbar buttons, etc. etc. Make it plainly obvious that you have to go to the user switcher menu to shut down the machine, and to the Software Store/Centre/whatever to install things.

Also, there are various other things that need fixing ASAP, namely:

[list][*]Nautilus is far, *far* too sluggish. On my system it took eleven seconds to start up and another four to enumerate the contents of my home folder (10 items!). When I boot into Windows, a similar folder is opened in a flash. The same applies to opening a folder in Thunar and Dolphin.
[*]Evolution, in its present state, is *astonishingly* mediocre. Its UI is nasty (I challenge you to look at the toolbar and say, without mousing over, which one is "stop" and which one is "delete") and it has a propensity to quit, randomly, without explanation upon execution of the most mundane task, such as entering a task into the task list. It needs fixing.
[*]OpenOffice.org is also slow, also has a nasty UI, is also buggy and needs major improvement.
[*]It needs to be far easier to find this place to seek assistance: at the moment, the link on the Ubuntu website is buried under several layers of links.
[*]It should be simpler to download the Firefox Flash plugin, MP3/MPEG2 codecs, etc. etc.[/list]

Also, thinking more of long-term goals, it would be good to see a home-oriented video editing app, á la iMovie or (Microsoft) Windows (Live) MovieMaker/Movie Maker [whatever it's calling itself this week], an automatic backup utility in the vein of Time Machine. The second will certainly be easier to implement when Btrfs (or Apple's Amazing Invisible New File System from the future) is in place, since copy-on-write makes backups a hell of a lot easier.

Consider that my 2¢ worth.

---

### Post by Reiger on 2009-10-29
Lennart is the main (only?, at least he's the vocal one) Pulseaudio developer IIRC. The kernel bits are AFAIK the implementation side for rtkit: which is about having the ability to ask the kernel to adjust its scheduler on the fly (to real time scheduling). 

For obvious reasons you want to run your media in (near) real time; but for equally obvious reasons (near) real time is less than optimal for ordinary desktop use which requires more switching between various program contexts.

---

### Post by Merk42 on 2009-10-29
> **jrothwell97 said:**
> Also, there are various other things that need fixing ASAP, namely:

[list][*]Nautilus is far, *far* too sluggish. On my system it took eleven seconds to start up and another four to enumerate the contents of my home folder (10 items!). When I boot into Windows, a similar folder is opened in a flash. The same applies to opening a folder in Thunar and Dolphin.
[*]Evolution, in its present state, is *astonishingly* mediocre. Its UI is nasty (I challenge you to look at the toolbar and say, without mousing over, which one is "stop" and which one is "delete") and it has a propensity to quit, randomly, without explanation upon execution of the most mundane task, such as entering a task into the task list. It needs fixing.
[*]OpenOffice.org is also slow, also has a nasty UI, is also buggy and needs major improvement.[/list]
Well Ubuntu/Canonical can do little to change those as they are made by GNOME and Sun

> **jrothwell97 said:**
> [list][*]It needs to be far easier to find this place to seek assistance: at the moment, the link on the Ubuntu website is buried under several layers of links.[/list]
Yeah, I think it'd be nice if there were a link to it on [Ubuntu Start Page](http://start.ubuntu.com/9.10/)

> **jrothwell97 said:**
> [list][*]It should be simpler to download the Firefox Flash plugin, MP3/MPEG2 codecs, etc. etc.[/list]
You try and open an mp3 and it goes "oh hey I need to get a codec" you click apply and it does so. Same with Flash.  How much easier can it be :confused: (having them preinstalled is illegal)

---

### Post by cb951303 on 2009-10-29
> **zekopeko said:**
> 
Perhaps the PA creator could engage directly with Ubuntu folk and point the ways they fail in this?

why? every other distro out there knows how to do it and PA devs explained the appropriate method on their site few ubuntu releases ago. why should they engage with ubuntu folk when ubuntu folks doesn't give a rats *** about it.

---

### Post by jrothwell97 on 2009-10-29
> **Merk42 said:**
> Well Ubuntu/Canonical can do little to change those as they are made by GNOME and Sun

Not exactly. Since they're open source, there's nothing to stop them making changes which then [i]might[/o] be accepted upstream by the GNOME project, Novell, Sun, etc. Of course, it'd make a certain Mr. Stallman very unhappy, but you can't please everyone.

> **Merk42 said:**
> You try and open an mp3 and it goes "oh hey I need to get a codec" you click apply and it does so. Same with Flash.  How much easier can it be :confused: (having them preinstalled is illegal)

It's still not as simple as it *could* be. For example, the plugin-fetching functionality is broken with some websites *cough* YouTube *cough* It'd also be nice to see this functionality implemented for Silverlight/Moonlight, since that's starting to proliferate on the 'net.

My most immediate concern, however, is documentation and polish, both from usability and code standpoints.

---

### Post by sim-value on 2009-10-29
Better Bluetooth Functionality!
After Pairing services should be discovered and made ready for use. For example for connection over network manager!

There is nothing more Painful(big expection ATI drivers) ive ever done in Ubuntu than trying Bluetooth dialup ...

---

### Post by gnomeuser on 2009-10-29
> **bluebyt said:**
> Sorry I don't understand this statement whats is kernel _bits_? and who is Lennart?

Lennart is the PulseAudio lead developer. The kernel bits in question is a simple upstream blessed patch that gives the scheduler a secure and standardized way to grant real time privilages to processes. This makes PA perform better, Ubuntu elected to ignore this advice for Karmic (despite requests coming from upstream via the Ubuntu PA maintainer to the kernel team as early as August).

They also applied plain wrong patches and changed defaults - the end result will be that Lennart will get to deal with the complaints from these changes. Something he most certainly does not deserve, and I would fully understand if he was to close any bug from Ubuntu and Ubuntu users as WONTFIX till Ubuntu follows his recommendations.

[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

---

### Post by gnomeuser on 2009-10-29
> **whiprush said:**
> The kernel bits Lennart recommends will be in the Lucid kernel (they're upstream now).


Now comes the question.. will you follow upstreams recommendations, to the letter, in the future so as to not get him flooded in undeserved complaints and hatred?

> 
There won't be large changes to Lucid like the switching out of default apps,  however the MSN/Empathy thing should be doable. (I had a sticky in the last dev forum about it)

That is simply sad, now it will be a full year till a proper media player which is made of awesome will be default. As I said before, we should have lived with the regressions in Karmic and basked in it's glory now.

---

### Post by bluebyt on 2009-10-29
Thanks Reiger and gnomeuser for the explanation!

---

### Post by Ellipsis on 2009-10-29
+1 for Chromium but only in Netbook Remix 

-Theme improvements. 
-Continuing the Papercuts project. 
-BUG FIXES-A LOT OF THEM

Also more Ubuntu One integration
+ source release for server side code.

---

### Post by Neon Lights on 2009-10-29
Work with a project (PiTiVi?) to provide a simple movie maker app
Continue fixing Papercuts, look/feel and usability are very important things.
and yes, packagekit would be pretty nice... :)

---

### Post by zekopeko on 2009-10-29
> **whiprush said:**
> There won't be large changes to Lucid like the switching out of default apps,  however the MSN/Empathy thing should be doable. (I had a sticky in the last dev forum about it)

Why not? If upstream fixes show stoppers I don't see why Banshee can't become the default music player.

---

### Post by zekopeko on 2009-10-29
> **cb951303 said:**
> why? every other distro out there knows how to do it and PA devs explained the appropriate method on their site few ubuntu releases ago. why should they engage with ubuntu folk when ubuntu folks doesn't give a rats *** about it.

So that people don't come barfing on his doorstep for Ubuntu's sucky implementation.

---

### Post by zekopeko on 2009-10-29
> **gnomeuser said:**
> That is simply sad, now it will be a full year till a proper media player which is made of awesome will be default. 

This sucks.

> As I said before, we should have lived with the regressions in Karmic and basked in it's glory now.

I disagree. I was all for Banshee becoming the default IF it fixed the show stoppers and released 1.6 before feature freeze. Alas this did not happen.

---

### Post by papangul on 2009-10-29
Karmic is unusable on my pc since audio is almost non-functional, due to PA issues. I hope this gets fixed in lucid.

---

### Post by castrojo on 2009-10-29
> **gnomeuser said:**
> Now comes the question.. will you follow upstreams recommendations, to the letter, in the future so as to not get him flooded in undeserved complaints and hatred?

The RT patches Lennart wanted were queued up for upstream kernel releases and our kernel team made the decision not to backport those changes for various reasons (they touched the scheduler in ways which we didn't want past freeze).  

I am not a developer, my job is to open dialogues with upstream; I can assure you that the decisions to not backport the changes were not taken lightly, and that myself, jono, and Rick Spencer (the desktop team lead) have had a call with Lennart on how to improve this in the future. Audio is very complicated, so I suppose you're going to have to trust that we're talking to Lennart to fix this.

> That is simply sad, now it will be a full year till a proper media player which is made of awesome will be default. As I said before, we should have lived with the regressions in Karmic and basked in it's glory now.

Unfortunately, Aaron could not commit to a release cycle for Banshee when I talked to him at GCDS. I am also sad about this. :(

---

### Post by gotsanity on 2009-10-30
> **MacUntu said:**
> An AeroSnap rip-off (yeah I know about compiz's grid plugin, but that's not the same).

[http://brainstorm.ubuntu.com/idea/20560/](http://brainstorm.ubuntu.com/idea/20560/)

I figured this one out the other day along with the help of a couple of others on the forums. Howto is here: [http://ubuntuforums.org/showpost.php?p=8185993&postcount=9](http://ubuntuforums.org/showpost.php?p=8185993&postcount=9)

---

### Post by gnomeuser on 2009-10-30
> **papangul said:**
> Karmic is unusable on my pc since audio is almost non-functional, due to PA issues. I hope this gets fixed in lucid.

Are you sure it is PulseAudio and not ALSA driver bugs?

---

### Post by excogitation on 2009-10-30
I was trying to share my UMTS connection the other day - and afaict there is no **easy** (gui) way of doing that.

Since (imho) "the internets" is the most important thing to have access to from a computer there should be
an easy way to share your internet connection from any device to any device.
(e.g. UMTS <-> Ethernet <-> wlan <-> USB <-> bluetooth <-> irda)

I didn't manage to share my internet connection with an iMac through wlan nor bluetooth (using gui that is).
What a shame.

---

### Post by papangul on 2009-10-30
> **gnomeuser said:**
> Are you sure it is PulseAudio and not ALSA driver bugs?
More than 100%, because when I choose 'oss' as output instead of pulseaudio from the settings of audacious, vlc ,mplayer, etc, sound is perfectly ok.

I had filed a bug at alsaproject([https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646)), thinking that it is alsa related, but now I am convinced it is due to PA.

---

### Post by pressureman on 2009-10-30
Drop Evolution, since it has done anything but what its name implies for about the last four years. Replace with Thunderbird 3. I know it's still in beta, but it's probably more stable and faster than Evolution, and the Lightning calendar addon with Google Calendar connectivity is already much nicer than Evolution's calendar.

Thunderbird also has a way better IMAP implementation that actually supports IDLE. The only thing that Evolution _might_ have over TBird is libmapi, for Exchange connectivity... and which is due any decade now.

---

### Post by zekopeko on 2009-10-30
> **excogitation said:**
> I was trying to share my UMTS connection the other day - and afaict there is no **easy** (gui) way of doing that.

Since (imho) "the internets" is the most important thing to have access to from a computer there should be
an easy way to share your internet connection from any device to any device.
(e.g. UMTS <-> Ethernet <-> wlan <-> USB <-> bluetooth <-> irda)

I didn't manage to share my internet connection with an iMac through wlan nor bluetooth (using gui that is).
What a shame.

Try creating an ad hoc network. Google for instructions.

---

### Post by froggyswamp on 2009-10-30
Put back the option to close the notification.

It's one of the few areas where Fedora is better cause it doesn't force the user to wait.

---

### Post by froggyswamp on 2009-10-30
> **pressureman said:**
> Drop Evolution, since it has done anything but what its name implies for about the last four years. Replace with Thunderbird 3. I know it's still in beta, but it's probably more stable and faster than Evolution, and the Lightning calendar addon with Google Calendar connectivity is already much nicer than Evolution's calendar.
No no no, while the majority of users would prefer Thunderbird 3 cause it's clearly better than Evolution, Canonical wouldn't move over cause their (Ubuntu) devs are already comfortable with Evolution and will throw at you any reason not to move over, just throw a few (half-truth) reasons like "better integration", "users are accustomed with Evolution", "it's the default in Gnome so less work", etc.
But if you touch an even more important subject (which Evolution leads to) I'm pretty sure you'll be banned (as troll or whatever). I don't need troubles.

---

### Post by qamelian on 2009-10-30
> **froggyswamp said:**
> No no no, while the majority of users would prefer Thunderbird 3 cause it's clearly better than Evolution, Canonical wouldn't move over cause their (Ubuntu) devs are already comfortable with Evolution and will throw at you any reason not to move over, just throw a few (half-truth) reasons like "better integration", "users are accustomed with Evolution", "it's the default in Gnome so less work", etc.
But if you touch an even more important subject (which Evolution leads to) I'm pretty sure you'll be banned (as troll or whatever). I don't need troubles.
Um, no. Evolution is simply a better solution for a PIM. If the only option I had was Thunderbird and Lightning, I would have no choice but to go back to Windows and Outlook, because T&L simply doesn't provide the functioanlity I need in my work environment, while Evolution does. T&L has maybe 70% of the features I require in a PIM solution for work. The combo just isn't good enough to be the default solution yet.

---

### Post by note32 on 2009-10-30
get rid of evolution replace with thunderbird

songbird insted of rhythmbox

i'd like to see google's web browser 

faster boot time over all a more stable system

---

### Post by Seventh Reign on 2009-10-30
Chromium replacing Firefox is a terrible idea.  Neither Chrome nor Chromium are anywhere near ready for everyday use.  Neither render some websites correctly, both crash constantly.  The interface is worse than IE 7/8. It is going to take a massive amount of time and work before Chrome/Chromium are even close to being a decent browser.  

Ohhh its fast .. I'd rather wait ONE extra second and have a correctly rendered website.

---

### Post by gjoellee on 2009-10-30
I would like to see:

[LIST]
[*]Improvements with Firefox. Why is it so slow in Ubuntu?
[*]Faster boot times
[*]A better boot experience (what's the deal with two different splash screens?)
[*]Artwork improvements. I am tired of the Human theme, and I don't think it is possible to get a worse wallpaper then what is default in Karmic! Hardy and Ibex was had cool wallpapers, Jaunty and Karmic wallpapers are boring. Who wants a boring desktop?! :(
[*]Performance improvements
[*]I more fancy installer would by a nice feature
[*]Thunderbird replacing Evolution (I find Evolution slow and hard to use. It also has a lack of features!)
[*]Banshee replacing Rhythmbox
[*]A cleaner apt output. Is is so messy! Take a look a pacman in Arch...!!!
[*]Improved wireless
[*]Improved sound (so I don't have to install Gnome ALSA Mixer to make the sound work)
[*]Improved media abilities
[*]and more...
[/LIST]

---

### Post by Merk42 on 2009-10-30
> **Seventh Reign said:**
> Chromium replacing Firefox is a terrible idea.  Neither Chrome nor Chromium are anywhere near ready for everyday use.  Neither render some websites correctly, both crash constantly.  The interface is worse than IE 7/8. It is going to take a massive amount of time and work before Chrome/Chromium are even close to being a decent browser.  

Ohhh its fast .. I'd rather wait ONE extra second and have a correctly rendered website.
Crashing I could see since it's beta and what not (though I personally haven't had issues)
The interface is up for debate, I like it, but if you don't well that's your opinion.
Not rendering correctly though? Considering it uses Webkit, which is what non-beta Chrome, Safari, and optionally Epiphany use, I'd love to see some examples.

> **gjoellee said:**
> I would like to see:

[LIST]
[*]A better boot experience (what's the deal with two different splash screens?)[/list]
One is usplash (for fallback and to run fsck), the other is the newer xsplash.  I'm pretty sure in Lucid the plan is to have usplash so quick it isn't noticable and/or only in case of emergencies such as an error

> **gjoellee said:**
> [list][*]Artwork improvements. I am tired of the Human theme, and I don't think it is possible to get a worse wallpaper then what is default in Karmic! Hardy and Ibex was had cool wallpapers, Jaunty and Karmic wallpapers are boring. Who wants a boring desktop?! :([/list]
Not going to happen until GTK+3. Besides you already got a change in theme, icons, boot and wallpaper just now in Karmic!

> **gjoellee said:**
> [list][*]I more fancy installer would by a nice feature[/list]
"more fancy" meaning what exactly?  The fact that it got the addition of the slideshow alone caused grief from some users.

---

### Post by Eestlane on 2009-10-30
Wilder good performance support for older hardware. So we could have nicer article than this:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_karmic_old&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_karmic_old&num=1)

---

### Post by pressureman on 2009-10-30
> **froggyswamp said:**
> No no no, while the majority of users would prefer Thunderbird 3 cause it's clearly better than Evolution, Canonical wouldn't move over cause their (Ubuntu) devs are already comfortable with Evolution and will throw at you any reason not to move over, just throw a few (half-truth) reasons like "better integration", "users are accustomed with Evolution", "it's the default in Gnome so less work", etc.

OpenSolaris uses GNOME, and they install Thunderbird (2.x) by default. AFAIK, Evolution isn't installed by default.

> **qamelian said:**
> Um, no. Evolution is simply a better solution for a PIM. If the only option I had was Thunderbird and Lightning, I would have no choice but to go back to Windows and Outlook, because T&L simply doesn't provide the functioanlity I need in my work environment, while Evolution does. T&L has maybe 70% of the features I require in a PIM solution for work. The combo just isn't good enough to be the default solution yet.

Maybe I'm not a power user of Evolution then (or maybe those really cool features are just too well hidden). I always thought Evolution's featureset paled in comparison to Thunderbird + Lightning. What's more, you can pimp your Thunderbird with addons, which seem to be developing faster than any of the plugins for Evolution, some of which are _very_ old now. Evolution is terrible at rendering HTML emails too (which is a minefield in itself). At least we know that TBird is going to use a damn good rendering engine.

Unless Evolution vastly improves their IMAP stack in the next release to properly support IDLE, I'll be switching to Thunderbird once and for all. Polling an IMAP server every n minutes as if it were a POP3 server is crazy. I expect to be notified of new mail the moment it arrives on the remote server.

Have you tried one of the nightly builds of Lightning under TBird3? They're significantly further along than the last snapshot (0.9 I think). And it _looks_ a lot slicker than Evolution.

I don't recall TBird ever crashing on me... but if I had a dollar for every time that Evolution went loopy... well.. 'nuff said.

---

### Post by qamelian on 2009-10-30
> **pressureman said:**
> I always thought Evolution's featureset paled in comparison to Thunderbird + Lightning.
Nope. T&L may have the feature set for home use and SOHO/small business, but it doesn't cut it in my work place.
> What's more, you can pimp your Thunderbird with addons, which seem to be developing faster than any of the plugins for Evolution, some of which are _very_ old now. Evolution is terrible at rendering HTML emails too (which is a minefield in itself). At least we know that TBird is going to use a damn good rendering engine. 
I pretty much have to disagree with all your points here. I CAN'T pimp my Thunderbird with any thing except add-ons that are tested and approved by the Security guys in the IT department in our corporate headquarters. The penalty for violating this rule is instant dismissal. I have yet to see Evolution fail to render a correctly crafted HTML email, ever.I have on the other hand had Thunderbird crash on me irreparably corrupting my mail store requiring me to restore it from backup. This happened too many times for my liking which prompted me to switch to evolution for home as well as business use.

> Unless Evolution vastly improves their IMAP stack in the next release to properly support IDLE, I'll be switching to Thunderbird once and for all. Polling an IMAP server every n minutes as if it were a POP3 server is crazy. I expect to be notified of new mail the moment it arrives on the remote server.
Again, I need to disagree. Thunderbird does not and never has worked well with my IMAP account at work, but Evolution has always been pretty much bullet-proof.

> Have you tried one of the nightly builds of Lightning under TBird3? They're significantly further along than the last snapshot (0.9 I think). And it _looks_ a lot slicker than Evolution.
I prefer the look of Evolution and I continue to test T&L periodically (last time was 2 weeks ago). It's improving but still doesn't meet my needs. End of story.

> I don't recall TBird ever crashing on me... but if I had a dollar for every time that Evolution went loopy... well.. 'nuff said.
As I said above, my experience has been the opposite. I found Thunderbird nightmarish to use. I want to like it, because I love Firefox and most other Mozilla efforts, but every attempt at using T-bird for any length of time results in loss of valuable time that I cannot afford.

---

### Post by garba on 2009-10-30
> **whoop said:**
> [https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)

I know it's all possible already, but make the configuration a little easier, or at least get some up to date usable documentation on this stuff.

There are allot of companies not moving to linux because of this. What are you gonna do if it's a total hassle to setup a network where any user can get to his/her own account from any computer. It's not like they are asking for useless functionality. Why is all the documentation either incomplete or outdated?

Totally agree, setting up something like that should be a streamlined process, the way it is now is more like tying countless pieces together. I'd love something like roaming profiles and cached credentials for disconnected login on linux.

---

### Post by exploder on 2009-10-30
> I CAN'T pimp my Thunderbird with any thing except add-ons that are tested and approved by the Security guys in the IT department in our corporate headquarters. The penalty for violating this rule is instant dismissal.

This type of policy exists in many companies. Evolution is built with corporate use in mind. Thunderbird's development has been lacking and Mozilla seems to give Windows users more priority than Linux users.

I have to agree with qamelian on mail clients. It would make more sense to participate more actively in Evolutions development rather than switch to Thunderbird. I would rather stick with an mail client that places focus on Linux users needs than go with an e-mail client that gives us little priority.

---

### Post by pressureman on 2009-10-30
> **qamelian said:**
> I CAN'T pimp my Thunderbird with any thing except add-ons that are tested and approved by the Security guys in the IT department in our corporate headquarters. The penalty for violating this rule is instant dismissal.

I'm sure many companies have similar policies for software, which is why a carefully selected set of TBird addons that provided similar functionality, installed by default or as a meta-package, would get around the problems of expecting users to install addons.

> **qamelian said:**
> I have yet to see Evolution fail to render a correctly crafted HTML email, ever.

Do much web development? Evolution fails on pretty much everything except HTML 3.2. Most of us stopped using HTML 3.2 about the same time we stopped using MS FrontPage and learned CSS. Sure, Evolution displays the content, but probably not in the style it was intended. I also frequently see Evolution stall while loading images in an HTML email, or simply fail to load them ever. Thunderbird loads them in under a second, and it displays perfectly.

> **qamelian said:**
> Again, I need to disagree. Thunderbird does not and never has worked well with my IMAP account at work, but Evolution has always been pretty much bullet-proof.

TBird works pretty damn well with DoveCot. If your IMAP account at work is on an Exchange server, then that would explain a lot of your problems. IMAP support is hardly a priority for a company that uses MAPI on their mail clients.

I'm not saying TBird is suitable for enterprise users, since that is really like saying Outlook Express is suitable for them. But at the same time, how many home users run Outlook (eg. the corporate verision), considering it's not included in the cheapest version of MS Office?

If you like Evolution or are dictated by company policy to run it, do so... I think I've run out of patience with it though. Seriously, go and look at their previous roadmaps, then their changelogs. The same stuff keeps cropping up again and again, and never gets implemented Developers are too afraid to delve into the CORBA mess still lurking in the code. It's gonna take a lot of work to get that particular mail client to live up to its name.

---

### Post by Ellipsis on 2009-10-30
The "replacing evolution with Thunderbird idea" is good in that like Firefox it gives users a cross platform application that they may be already comfortable with. Of course since I don't use desktop clients I don't really care... maybe built in Prism to create applications for Zoho, Gmail would be bigger on my to-do list than this.

---

### Post by omarly on 2009-10-30
I just tried to get a friend of mine to convert. He is a gamer and has a brand new mashine, 8 kernels and so on...., Earlier he has tried to install ubuntu, but when he came 2 the partitioning part, it had stopped him when he tried to cope on his own. I got him going up on the beta 9.10, but he just got the win7 in the mail, so he had lots of hours to play.

He is interested in getting his big-screen and all the things on his home going on Myth, and he is a RALLY big tech-freak, but if the part about partitioning in the install prosess could be made a bit more accessible for previous windows users I think a lot of new users could be won.

Seems like its quite a gap in understanding that part. I can remember i had 2 read a bit about it too.

We did an install on a split ssd and we had to format the part of the disk 2 ext3 before i could guide him to complete.

I still don't understand why he didn't follow my adwise to convert completely, but his loss.

Just love the new 9.10 64 install on my laptop!!!! WWWOOOOWWW

---

### Post by ktp on 2009-10-30
> **gnomeuser said:**
> 
Death to AppCenter, aptdaemon, xsplash - welcome our plymouth and PackageKit overlords (hey I can wish for sanity, it doesn't mean it will happen).

Removal of Ubuntu One from the default install or a release of the server side code ....

Pulseaudio finally being implemented as recommended by upstream.

Chromium instead of Firefox.


> **zekopeko said:**
> This is the one I would like to see:

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

I can live with these :lolflag:

---

### Post by Merk42 on 2009-10-30
> **omarly said:**
> I just tried to get a friend of mine to convert. He is a gamer and has a brand new mashine, 8 kernels and so on...., Earlier he has tried to install ubuntu, but when he came 2 the partitioning part, it had stopped him when he tried to cope on his own. I got him going up on the beta 9.10, but he just got the win7 in the mail, so he had lots of hours to play.

I've installed both.
In both cases you have to partition and/or format your drive. Are you saying Windows 7 makes this clear, and Ubuntu doesn't? If so how?

The difference usually with installing Ubuntu vs Windows is that for the majority of users, Windows is **already installed**

---

### Post by whoop on 2009-10-30
> **garba said:**
> Totally agree, setting up something like that should be a streamlined process, the way it is now is more like tying countless pieces together. I'd love something like roaming profiles and cached credentials for disconnected login on linux.

I've created an ubuntu idea for this: [http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/) on brainstorm. Please vote, and let it be heard!

Frankly I don't expect this problem solved for Lucid. This scares me a bit. I know allot of people have the technology up and running thanks to rickyjones and his wonderful howto: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)
This howto is for ubuntu 7.10 (end of life now) and some folks (one of them is me) got it working for 8.04 LTS (albeit using some deprecated stuff).
I expect breakage when upgrading to Lucid (which is an LTS, mind you), and total confusion by people trying to set this up on a fresh install, as most will only have rickyjones's howto to work with.

---

### Post by excogitation on 2009-10-31
> **zekopeko said:**
> 
[QUOTE=excogitation;8194564]I didn't manage to share my internet connection with an iMac through wlan nor bluetooth ([SIZE="6"]using gui that is[/SIZE]).
What a shame.

Try creating an ad hoc network. Google for instructions.[/QUOTE]

Well ... really? You could have added a lmgtfy link ...

All I can say is that sharing your internet connection should be easy as pie
(just **my opinion**) - and yes ... I just might be too stupid to do it - or maybe it's just a pita atm.

---

### Post by vishalrao on 2009-10-31
@OP (zekopeko) - yep, zsync/rsync/delta-debs is the one im looking forward to too! perhaps it could be updated for karmic as well lets see...

that and also:

1. Faster boot...
2. Moar installer, boot, desktop BLING! plzzzz :lolflag:

---

### Post by uBeer on 2009-10-31
> **excogitation said:**
> All I can say is that sharing your internet connection should be easy as pie
(just **my opinion**) - and yes ... I just might be too stupid to do it - or maybe it's just a pita atm.

Sharing your internet connection is in fact quite easy, but maybe a little hard to discover at first.

System > Preferences > Network Connections

Then edit the connection that you want to fuel with Internet and go the the IPv4 tab and set the dropdown menu Method from Automatic (DHCP) to "Shared to other computers". Now any pc that you plugin to that connection will have internet connection.

---

### Post by Slug71 on 2009-10-31
> **vishalrao said:**
> @OP (zekopeko) - yep, zsync/rsync/delta-debs is the one im looking forward to too! perhaps it could be updated for karmic as well lets see...

that and also:



This,

Pulseaudio, which we now know is coming and

Plymouth and 

Packagekit as the backend to USC.

---

### Post by LKjell on 2009-10-31
> **Slug71 said:**
> This,

Pulseaudio, which we now know is coming and

Plymouth and 

Packagekit as the backend to USC.

Do not think we are going to use packagekit.

---

### Post by phenest on 2009-10-31
As LL will be LTS, I don't think we should be thinking about adding anything new. Time would be wisely spent polishing off what we already have.

---

### Post by qwerty2009 on 2009-10-31
to get more people to use linux instead of windows i think ubuntu should lose the windows 2000 flat style panels and the grey, brown colors , i no Linux is fully customizable but if u were coming straight from windows xp,vista,windows 7, Ubuntu's default theme would be enough to turn you off linux forever it looks like it is stepping back a generation in operating systems

---

### Post by hellion0 on 2009-10-31
Fix Bug #1
Get PulseAudio on track with upstream
Finish fixing up the boot experience
Push out the *new theme* we've been promised since Biblical days

That's about all I can suggest. :P

---

### Post by k3lt01 on 2009-11-01
Simple things like Evolution being able to be minimised to the notification applet and Empathy actually working without compromising privacy (meaning when you are hidden you are actually hidden) would be nice.

Ubuntu Software Center needs work. Instead of having to double click each item to see what it is and does there should be a small synopsis on the first page you see the item, much like Synaptic already does. Add/Remove was much easier to use.

Banshee instead of Rhythymbox.

Maybe a Business Edition (or Metapackage) that takes out alot of the material a business wouldn't want or need and replaces it with something more suited to business use. For example remove the games or some of them and replace them with the full OpenOffice suite.

A LiveCD, even the AlternativeCD, that offers options on software choices.

Please put ndiswrapper etc. back on the install CD. When you have no internet connection it would be nice to be able to get one just by using the LiveCD/AlternativeCD.

---

### Post by vishalrao on 2009-11-01
> **phenest said:**
> As LL will be LTS, I don't think we should be thinking about adding anything new. Time would be wisely spent polishing off what we already have.

A wholehearted +1 from me.

I too hope the developers/planners focus on tracking existing issues (with Karmic users) and fix them to make LL super stable for as many people/hardware combinations as possible. They can of course refine the bling and improve boot speed etc - I wont complain if LL is considered "conservative" and not brimming with new features! :lolflag:

I didn't spend too much time testing KK but will make an effort to do what I can for LL for my home machines (desktop and tablet PC) and also because I hope to have my office's sysadmin replace HH with LL in all our office PCs - so I will get them to test early alphas (networking/enterprise issues etc) there too! :D

---

### Post by k3lt01 on 2009-11-01
The option of creating a recovery partition that will recover / but leave /home untouched. Similar to Acer's System Restore for Windows machines or even Dell's own Ubuntu recovery partition supplied on its Ubuntu delivered machines.

---

### Post by vishalrao on 2009-11-01
Just saw an email to ubuntu-devel@ that LL is auto syncing with "Debian testing" instead of "Debian unstable", what does that signify? Is LL going to be more conservative or more cutting edge?

---

### Post by eyelessfade on 2009-11-01
If they aren't going to sync with unstable, then they will be much much more conservative. Debian testing is what we call super stable in ubuntu :P

---

### Post by vishalrao on 2009-11-01
Oh I see, so

Debian Stable == Ubuntu Hyper Stable
Debian Testing == Ubuntu Super Stable
Debian Unstable == Ubuntu Stable 

:lolflag:

I was confused about which was more or less stable "debian unstable" or "debian testing", now I got my answer...

---

### Post by Trezker on 2009-11-01
I wanna complain about pulseaudio, which went from bad to worse in 9.10.
Now it's required for the ubuntu-desktop package and removing pulseaudio removes sound mixer and sound conf tools.
In the next release I hope that I will be able to just remove pulseaudio without it messing up those things so I can just be happy with a sound system that works.

I also want the close notification option back, I suspect that some day one of those notification popups will forget to close and just show indefinitely.

Empathy runs to many processes IMHO. And I think it's responsible for a process without name that pops up over and over really fast and thereby messes up the process listing in system monitor.

---

### Post by vishalrao on 2009-11-01
> **vishalrao said:**
> Just saw an email to ubuntu-devel@ that LL is auto **syncing with "Debian testing" instead of "Debian unstable"**, what does that signify? Is LL going to be more conservative or more cutting edge?

So this is a good thing as far as earlier posts go: [http://ubuntuforums.org/showpost.php?p=8211175&postcount=80](http://ubuntuforums.org/showpost.php?p=8211175&postcount=80)

---

### Post by NCLI on 2009-11-01
Wow, I guess Lucid is going to be VERY stable O.O

I mean, if syncing with Debian unstable is like syncing with a kinda shifty hill, syncing with Testing is like Mount Everest(Of course, syncing with Debian Stable would be like a titanium version of the moon.)

Maybe this will finally silence the people who complain about it being released too early every year(as if).

---

### Post by gnomeuser on 2009-11-01
> **vishalrao said:**
> Just saw an email to ubuntu-devel@ that LL is auto syncing with "Debian testing" instead of "Debian unstable", what does that signify? Is LL going to be more conservative or more cutting edge?

I've often found over the years that unstable was in fact more stable than testing. the delay in pushing a build because of bugs often leads to shipping versions with known problems as well as having an unneededly long delay between bug and bugfix being available.

The only thing you truly avoid using testing is the ugly mistakes that cause dataloss or corruption of important critical packages, this however happens very rarely for most distros in any case.

---

### Post by lykwydchykyn on 2009-11-01
> **Slug71 said:**
> This,

Pulseaudio, which we now know is coming and

Plymouth and 

Packagekit as the backend to USC.

Ok, I don't want to derail this thread, but I keep hearing people say they want packagekit.  Having suffered through KPackageKit for a while now, I really have to ask -- why?  What is so compelling about it?  From my POV, it doesn't support a large number of the features of APT/DPKG (see [here](http://ubuntuforums.org/showpost.php?p=8199979&postcount=15) for my list).  Granted, work is being done to make it a better interface, but until then what's the advantage?

---

### Post by meeples on 2009-11-01
> **sim-value said:**
> Better Bluetooth Functionality!
After Pairing services should be discovered and made ready for use. For example for connection over network manager!

There is nothing more Painful(big expection ATI drivers) ive ever done in Ubuntu than trying Bluetooth dialup ...

i replaced gnome-bluetooth with Blueman for that, it does bluetooth internet and stuff easily, far more features, i like it.

as for what improvements i'd like to see in Lucid:
[LIST]
[*]Banshee as default music player, especially on netbooks once it gets its new clutter-based UI
[*]Blueman replacing gnome-bluetooth for the reasons above
[*]the whole operating systems look and feel to be consistent, i have a beautiful startup and login, and then i get grey and brown on my desktop, bit of an anticlimax.
[*]my ralink wifi adapter to work out of the box again, (internet dodgy so havent updated to final karmic so this may not be a problem anymore)
[*]Earcandy in default install would be amazing.
[*]A much more easy on the eyes Ubuntu Software Centre. PLEASE.
[*]and as always less need for the terminal
[/LIST]

i'll probably think of more laterz

---

### Post by zika on 2009-11-01
> **Trezker said:**
> I wanna complain about pulseaudio, which went from bad to worse in 9.10.
Now it's required for the ubuntu-desktop package and removing pulseaudio removes sound mixer and sound conf tools.
In the next release I hope that I will be able to just remove pulseaudio without it messing up those things so I can just be happy with a sound system that works.

I also want the close notification option back, I suspect that some day one of those notification popups will forget to close and just show indefinitely.

Empathy runs to many processes IMHO. And I think it's responsible for a process without name that pops up over and over really fast and thereby messes up the process listing in system monitor.

What is the real alternative to PulseAudio?

---

### Post by mc4man on 2009-11-01
> What is the real alternative to PulseAudio? 

A well implemented pulseaudio

[http://0pointer.de/blog](http://0pointer.de/blog)

---

### Post by amano on 2009-11-01
1) Please work on proper DVD playback. I know it is upstream which is lacking here, but I hope that they can work it out soon. Now I have mostly working menus but many DVDs are still missing sound. thus please keep updating the gst-bad plugins. Every fix there makes the situation better (it can't get much more unusable as it is currently)

2) proper Pulseaudio implementation (kernel modules patched and the new rt stuff being in place)

3) A switch to banshee IF raof upstream manages to finally get gapless playback in place: [http://gitorious.com/~raof/banshee/gapless-work](http://gitorious.com/~raof/banshee/gapless-work) If they don't merge the gapless branch, banshee is completely unusable for all people listening to live stuff or classical stuff 

4) review some printer/scanner models. Installing eg. the (closed source) brother scanner drivers from upstream is still a mess (including manually adding udev rules to system files). Make those things available from the Canonical partner repo and let a deb file do this stuff.

---

### Post by umberstark on 2009-11-02
"English UK" (and all other variants, for that matter) as a language option during installation. It's annoying to have to change my locale from US to UK when it should be done at install time.

Out-of-the-box-experience. Say it.

---

### Post by irishbreakfast on 2009-11-02
I agree jrothwell97

> Documentation, documentation and documentation.

Not everyone can/will surf the forums for an answer. Personally, I do try the doc first, but usually find myself here seeking support.

---

### Post by mrsurb on 2009-11-02
> **umberstark said:**
> "English UK" (and all other variants, for that matter) as a language option during installation. It's annoying to have to change my locale from US to UK when it should be done at install time.

Out-of-the-box-experience. Say it.

My locale is set to English (Australian) out-of-the-box. Can't remember if it's an explicit option, or as a result of setting my timezone to Sydney, Australia.

---

### Post by blazemore on 2009-11-02
I'd like to see a lot more done from the usability point of view.

I think when a user tries to open a file of an unsupported type in Naulilus (such as .exe) they should get a prompt saying something like:

> 
The file you have tried to open (.exe) requires the program "Wine" to run. Would you like to install Wine now? [ Yes ]  [ No ]  [ Learn More ]


As well as for any file, I would like to see a lot more emphasis put on getting Windows migrants up and running with .exe programs. This was actually proposed for Karmic, but never made it.

---

### Post by umberstark on 2009-11-02
> **mrsurb said:**
> My locale is set to English (Australian) out-of-the-box. Can't remember if it's an explicit option, or as a result of setting my timezone to Sydney, Australia.

Hmm, that's the problem then. I set my language to "English", but my time zone and keyboard to Norwegian (I'm English but live in Norway) so the installation is presuming I want US English I suppose.

In fact, after choosing English language and then Norway as time zone, it defaults to USA keyboard as "suggested".

All could be solved by being able to choose the specific English I want to begin with. :)

---

### Post by whoop on 2009-11-02
> **amano said:**
> 
4) review some printer/scanner models. Installing eg. the (closed source) brother scanner drivers from upstream is still a mess (including manually adding udev rules to system files). Make those things available from the Canonical partner repo and let a deb file do this stuff.

Yep, don't forget the Canon Selphy models, which are supposed to be supported, but they don't work.
I'm don't think ubuntu is to blame here, as it seems the bug is caused by the driver itself.
Posting a bug to the driver developers has not been helpful (yet):
[http://sourceforge.net/tracker/?func=detail&aid=2796178&group_id=1537&atid=101537](http://sourceforge.net/tracker/?func=detail&aid=2796178&group_id=1537&atid=101537)

---

### Post by Slug71 on 2009-11-02
> **lykwydchykyn said:**
> Ok, I don't want to derail this thread, but I keep hearing people say they want packagekit.  Having suffered through KPackageKit for a while now, I really have to ask -- why?  What is so compelling about it?  From my POV, it doesn't support a large number of the features of APT/DPKG (see [here](http://ubuntuforums.org/showpost.php?p=8199979&postcount=15) for my list).  Granted, work is being done to make it a better interface, but until then what's the advantage?

A new PK version is out sometime today. Compile it and install the aptcc backend.

Go to /etc/PackageKit/PackageKit.conf and change the default backend to 'aptcc'.

You should see a HUGE improvement. ;)

Or you could install packagekit-backend-smart and set the default to smart.
That works pretty good too.

The 0.6.x series will be forked soon too. Im guessing next release(after today) will be 0.6.0. That series will be getting interactive debconf and conffile handling which will bring PK to Debian/Ubuntu standards.

---

### Post by Slug71 on 2009-11-02
Would be nice to have 64bit Flash in the repos too.

---

### Post by ibizatunes on 2009-11-02
better hardware testing early one in the devlopment, ie printer, wireless etc
[http://brainstorm.ubuntu.com/ideatorrent/idea/22060](http://brainstorm.ubuntu.com/ideatorrent/idea/22060)

---

### Post by inportb on 2009-11-02
> **PilotPaul said:**
> I'd like to see improved mobile phone integration and synchronisation...its the only thing Windows does better any more, and that's largely down to the application software supplied by the manufacturers...be nice if ubuntu coped with at least the mainstream mobile phones out of the box...

Right... like Android works just fine out of the box with Ubuntu. w00t @ open platforms.

---

### Post by lykwydchykyn on 2009-11-02
> **Slug71 said:**
> A new PK version is out sometime today. Compile it and install the aptcc backend.

Go to /etc/PackageKit/PackageKit.conf and change the default backend to 'aptcc'.

You should see a HUGE improvement. ;)

Or you could install packagekit-backend-smart and set the default to smart.
That works pretty good too.

The 0.6.x series will be forked soon too. Im guessing next release(after today) will be 0.6.0. That series will be getting interactive debconf and conffile handling which will bring PK to Debian/Ubuntu standards.

I may try that when I have time, but none of that tells me why PackageKit is actually BETTER than existing, feature-complete APT applications.

---

### Post by zekopeko on 2009-11-02
> **lykwydchykyn said:**
> I may try that when I have time, but none of that tells me why PackageKit is actually BETTER than existing, feature-complete APT applications.

Not even slug71 knows why PK is better then apt/dpkg/whatever.
The author of PK taunts the unified package management interface as the main reason for adopting PK (the interface being pk-gnome or pk-kde/KPackagekit).
USC is already better then pk-gnome interface ever was, and the question remains why would we want the same interface for every distro out there since the whole point of distros is to "do your thing".

---

### Post by k3lt01 on 2009-11-02
> **mrsurb said:**
> My locale is set to English (Australian) out-of-the-box. Can't remember if it's an explicit option, or as a result of setting my timezone to Sydney, Australia.
Your locale is but your language option will be English US unless you change it after install.

---

### Post by slumbergod on 2009-11-02
1. a working Firefox that doesn't spike my CPU and hang;
2. a less hyperactive system fan (it was bad in Jaunty but Karmic takes it to a whole new level);
3. volume that is equal in loudness to what it is in Windows

---

### Post by umberstark on 2009-11-02
> **k3lt01 said:**
> Your locale is but your language option will be English US unless you change it after install.

Exactly, and it's wrong in my opinion. It shouldn't just shrug and pick one type of English.

To be honest, the language, time zone and keyboard settings all need to be combined in to one page of the installation wizard, with more language choices ofc ;)

---

### Post by mesmith on 2009-11-02
Quality!  Just hammer the bugs into the ground.  Forget new apps.  Make it the cleanest, most bug free release in Ubuntu's history.  Put an end to the "never do an upgrade, always fresh install", "never upgrade until 3 months have passed", etc. etc.

End it.  Kill every bug you can find.

---

### Post by Triggerhapp on 2009-11-02
> **mesmith said:**
> ..."never upgrade until 3 months have passed"...

Where did you get THAT advise!?

My personal wishlist is simple. I want it to work. Ubuntu hasnt let me down before :D

---

### Post by mesmith on 2009-11-02
Don't tell me you haven't seen that advice.  The interval may vary, but the message is the same - "let things settle down", "let them find all the important post release bugs", etc.

End it.

---

### Post by Triggerhapp on 2009-11-02
Nope never seen that advise...

The only time I've seen a "wait 3 months" is half way through making a new version of Ubuntu where you get the obligatory "Should I upgrade to alpha now? I just want XYZ"

---

### Post by Slug71 on 2009-11-02
> **zekopeko said:**
> Not even slug71 knows why PK is better then apt/dpkg/whatever.
The author of PK taunts the unified package management interface as the main reason for adopting PK (the interface being pk-gnome or pk-kde/KPackagekit).
USC is already better then pk-gnome interface ever was, and the question remains why would we want the same interface for every distro out there since the whole point of distros is to "do your thing".

Ok, first of all, PK does NOT replace apt/dpkg. It uses them. Hence why you go into Synaptic and see packagekit-backend-apt, packagekit-backend-smart, packagekit-backend-aptcc etc etc.

The main reason for adopting PK is absolutely not for the GUI, but, having a GUI which any Distro can use immediately certainly cannot do any harm. Especially considering most Distros use KDE or Gnome hence why there are GUIs for those DEs and PK is a cross Distro package management system. Distros are by no means forced to use those GUIs though and can easily create their own. openSUSE doesnt use packagekit-gnome.

USC currently uses aptdaemon as a backend which can easily be replaced by PK. Aptdaemon is based on and uses PK code. USC will therefore replace packagekit-gnome. The only reason PK was not chosen was because of debconf and conffile handling. Since Richard Hughes(PK author) is now satisfied with the way this can be integrated, it has been accepted for the 0.6.x series.

Packagekit has also been flawed by limitations of the apt(python) backend(default in Kubuntu) though. Which is why aptcc came along. Last i heard though, the apt python backend is being fixed for the 0.6.x series too.

To answer lykwydchykyn's question and zeko's first remark about PK being better than the others, well its not really a valid question since PK is the first/only(that i know of) cross Distro/Architecture package manager(which is actually just a daemon).

What makes it good though is that its just a single API that devs from any Distro can write to, to make a package that can be used by any Distro using it and it works well with Policykit. And it can do this because of how well it can handle those package files and its dependencies. Currently there are so many different backends and package managers(and therefore APIs) especially between Distros that essentially each package being made by devs need to be 'ported'(different APIs) to be used by those package managers so they actually know how to handle the files and dependencies. 

What makes it better, or rather will make it better is that many Distros are switching to it and the rapid development it is in but also the support it has for the very many Distros. What this will eventually lead to if all Distros or least the major ones switched to it, is most of the work being pushed to the backend(in our case APT) to handle those files, which means the backends will eventually have to resolve this and pretty much work the same way as PK with the dependencies and files which is why correct conffile and debconf support is needed or preferred by Debian/Ubuntu. That does mean packages will become smaller too though and more dependencies being dragged in, even downloaded and eventually downloaded and installed at the same time.

And on a side note: That backend that would be needed to resolve that issue and work like PK does already exists and is called Smart Package Manager(and is also cross-distro, bringing the downloaded and installed at the same time even closer to reality and means and already can to some extent(if the package is small enough) handle rpm and deb packages). packagekit-backend-smart or smartpm in Synaptic. Its in fact even funded by Canonical but is still pretty much in development so doesnt yet work like it should but it works. Development is also very slow at the moment.

Backends currently supported by PK:

apt, aptcc, alpm, box, conary, opkg, pisi, poldek, portage, ports, slapt, smart, urpmi, yum and zypp.

KDE is also dropping Kpackage in favour of Kpackagekit for 4.4 last i heard. And with talk of that and Adept not being maintained anymore , it really didnt leave Kubuntu with much choice anyway also taking into account that PK was suppose to be in Ubuntu since Intrepid anyway.

---

### Post by Squonk07 on 2009-11-03
> **Merk42 said:**
> Not rendering correctly though? Considering it uses Webkit, which is what non-beta Chrome, Safari, and optionally Epiphany use, I'd love to see some examples.

You mean like this one? ;)

1. Firefox
2. Chromium

[ATTACH]134460[/ATTACH][ATTACH]134459[/ATTACH]

Granted, mostly it's not terrible, but (subjectively) the fonts look better in Firefox. The too-dark lines in Chromium are a more noticeable issue--I'm not sure if that's the site's fault or WebKit's. Scattered sites that render incorrectly definitely exist, though it might be the fault of the developers of the site and not Chromium. Either way, I'm sticking with Firefox and couldn't see making Chrome/Chromium the default anytime soon.

---

### Post by Merk42 on 2009-11-03
> **Squonk07 said:**
> You mean like this one? ;)

1. Firefox
2. Chromium

[ATTACH]134460[/ATTACH][ATTACH]134459[/ATTACH]

Granted, mostly it's not terrible, but (subjectively) the fonts look better in Firefox. The too-dark lines in Chromium are a more noticeable issue--I'm not sure if that's the site's fault or WebKit's. Scattered sites that render incorrectly definitely exist, though it might be the fault of the developers of the site and not Chromium. Either way, I'm sticking with Firefox and couldn't see making Chrome/Chromium the default anytime soon.

Oh that, I don't have that issue, but I've seen it before. I thought maybe you meant where things wouldn't show up or were misaligned.

---

### Post by k3lt01 on 2009-11-03
> **umberstark said:**
> Exactly, and it's wrong in my opinion. It shouldn't just shrug and pick one type of English.

To be honest, the language, time zone and keyboard settings all need to be combined in to one page of the installation wizard, with more language choices ofc ;)
One of the reasons I got into Linux was a RedHat8 CD pack I have, it gave so much choice. Admittedly it is 3 cds and thats a big ask for a new user to download but choice is what using Ubuntu is about for me and I would like the choice of what version of English I want to install and also what programs. This is why alot of people are moving towards a "Minimal CD install", it is the only way so far with Ubuntu to have a choice of what your fresh install uses.

Maybe a regional LiveCD option is a good idea. For example Australian downloads automatically come with Australian English, British downloads automatically come with British English etc. It would encourage regional participation during the development phase and I for one would love to be involved in that part of Ubuntu development.

---

### Post by Nightstrike2009 on 2009-11-03
I'd like to see networkmanager allowing me to connect to the internet again on a 3G modem usb stick, jaunty managed it perfectly but apparently its to much to ask this of karmic. :(

---

### Post by sameer.india on 2009-11-03
a snipping tool
i mean i want to be able to select a portion of the screen and save it as an image.
currently i have to take a screenshot then edit the image with gimp
also the selection features similar to adobe acrobat in evince
better support for real media

---

### Post by zekopeko on 2009-11-03
> **Slug71 said:**
> Ok, first of all, PK does NOT replace apt/dpkg. It uses them. Hence why you go into Synaptic and see packagekit-backend-apt, packagekit-backend-smart, packagekit-backend-aptcc etc etc.

I didn't say that it replaces them.

> The main reason for adopting PK is absolutely not for the GUI, but, having a GUI which any Distro can use immediately certainly cannot do any harm. Especially considering most Distros use KDE or Gnome hence why there are GUIs for those DEs and PK is a cross Distro package management system. Distros are by no means forced to use those GUIs though and can easily create their own. openSUSE doesnt use packagekit-gnome.

USC currently uses aptdaemon as a backend which can easily be replaced by PK. Aptdaemon is based on and uses PK code. USC will therefore replace packagekit-gnome. The only reason PK was not chosen was because of debconf and conffile handling. Since Richard Hughes(PK author) is now satisfied with the way this can be integrated, it has been accepted for the 0.6.x series.

Packagekit has also been flawed by limitations of the apt(python) backend(default in Kubuntu) though. Which is why aptcc came along. Last i heard though, the apt python backend is being fixed for the 0.6.x series too.

To answer lykwydchykyn's question and zeko's first remark about PK being better than the others, well its not really a valid question since PK is the first/only(that i know of) cross Distro/Architecture package manager(which is actually just a daemon).

What makes it good though is that its just a single API that devs from any Distro can write to, to make a package that can be used by any Distro using it and it works well with Policykit. And it can do this because of how well it can handle those package files and its dependencies. Currently there are so many different backends and package managers(and therefore APIs) especially between Distros that essentially each package being made by devs need to be 'ported'(different APIs) to be used by those package managers so they actually know how to handle the files and dependencies. 

What makes it better, or rather will make it better is that many Distros are switching to it and the rapid development it is in but also the support it has for the very many Distros. What this will eventually lead to if all Distros or least the major ones switched to it, is most of the work being pushed to the backend(in our case APT) to handle those files, which means the backends will eventually have to resolve this and pretty much work the same way as PK with the dependencies and files which is why correct conffile and debconf support is needed or preferred by Debian/Ubuntu. That does mean packages will become smaller too though and more dependencies being dragged in, even downloaded and eventually downloaded and installed at the same time.

And on a side note: That backend that would be needed to resolve that issue and work like PK does already exists and is called Smart Package Manager(and is also cross-distro, bringing the downloaded and installed at the same time even closer to reality and means and already can to some extent(if the package is small enough) handle rpm and deb packages). packagekit-backend-smart or smartpm in Synaptic. Its in fact even funded by Canonical but is still pretty much in development so doesnt yet work like it should but it works. Development is also very slow at the moment.

Backends currently supported by PK:

apt, aptcc, alpm, box, conary, opkg, pisi, poldek, portage, ports, slapt, smart, urpmi, yum and zypp.

KDE is also dropping Kpackage in favour of Kpackagekit for 4.4 last i heard. And with talk of that and Adept not being maintained anymore , it really didnt leave Kubuntu with much choice anyway also taking into account that PK was suppose to be in Ubuntu since Intrepid anyway.

I still see no compelling reason why we should use PK. PK is essentially another abstraction layer on top of one interface to dpkg. So you have dpkg->apt-get/aptitude->PK->PK GUI.
I really don't see what is so great here.
And this API thing you are mentioning. You still didn't explain it to me what is so great about it.
You still have to create debs/rpm/whatever for specific distro. I don't see how this will unify package management or be beneficial to Ubuntu.

EDIT: On further deliberation is still don't see what are you talking about. 

Let's take for example since this bugs me:

> Currently there are so many different backends and package managers(and therefore APIs) especially between Distros that essentially each package being made by devs need to be 'ported'(different APIs) to be used by those package managers so they actually know how to handle the files and dependencies.

Please do tell how are you going to install packages between PK 0.4 and let's say 0.6.
The apt backend might have changed between 0.4 and 0.6 so you still have to do "porting". Not to mention that you still have to do distro specific packages since distros might work differently with your package. I don't get this API argument.

EDIT2: After a little research is found the only compelling reason to switch to PK. Installing plugins from applications. But then the question is how will the app know what is the package name? Guess that will have to be resolved by package maintainers.

---

### Post by epsolon77 on 2009-11-03
+1 for domain integration.  Being able to *easily *integrate an ubuntu server with an AD or create it's own domain would be a huge boost for the popularity of ubuntu.  I would also like to see a business oriented desktop install.  

It would be killer if there was an installable mail system compleate with shared calenders.  Something along the lines of zimbra, built in with ubuntu server and business desktop.  Make it a no brainer to roll out a whole corporate network on ubuntu.  I know all the parts are there, but they can be time consuming to piece together.

On the install, I don't mind the current CLI install on the server, but if the live CD can run an xserver, why couldn't the install CD for server run an Xserver just to grab install and config info?  I don't think this is needed though.  My 5 year old who can barely read can install Ubuntu server, and so can my friends who are not computer literate.  It's the details after the config that get them.

Of course if you make the install too easy I might be out of a job :-$

---

### Post by Rallg on 2009-11-03
I have an Asus EEE-PC which, like many netbooks, has a 1024x600 screen. When I use XP, the graphics card software allows me to quickly switch to a 1024x768 desktop, using a tray icon. The larger desktop is accessed by moving the mouse to screen edge, causing the viewport to shift (that is, the viewport is a 1024x600 window onto a larger 1024x768 desktop). The size of objects is NOT shrunk.

This is very helpful for some applications, such as Google maps, where the various controls take up a lot of space on the desktop, leaving only a small space for the useful information.

I'd like to see that in Ubuntu (for supported graphics cards), also accessible via a Gnome panel icon.

---

### Post by QwUo173Hy on 2009-11-03
I'd like to see a revamped theme for the desktop. The new one is nice, but I'd like to see a little more schazzzaaaam! At the moment, it's a little bit 'oooh, that's nice' but not very 'wow! I think I need to change my pants!' Also, I like green so if there could be lots of green that would be great too.

I'd like to see canonical hire a lot more developers so we don't have to rely on the pace of individual open-source projects. I'm 30 now and I don't want to have to wait until I'm 30 and a half to see Banshee as the default media app in Ubuntu. Let's just get in there and nail it with loads of developers and make the next release perfect!

I also think canonical should do a user interaction survey with users of Thunderbird and Evolution. The results can be used to make a new application called ThunderLution, which will satisfy both sets of users.

Finally, I'd like launchpad to do a bit more on the processing side of things. I don't want to have to send in bug reports with 'this didn't work' or 'that was wierd' details. I just want to send in a 'tut tut tut' and have launchpad figure out what the problem is. I know it's radical thinking, but it would be really cool and save me loads of time so that I can... have more time.

Also, now that we're going with cloud based services, do you think we could get a plugin for Ubuntu One that would make it a dating service also? I haven't had a girlfriend in ages and the girls here don't like the way I flirt with them... or maybe they're just playing hard to get but if you're hot and your in the phone book then it's only natural that I'm going to turn up on your doorstep with an Ubuntu CD and some flowers right?

I'll be back in April to check how things are going so stay motivated everyone - at least until these issues are dealt with. After that I don't mind too much if people have personal issues or anything making them feel a little under the weather or whatnot. That's understandable.

---

### Post by Slug71 on 2009-11-03
> **zekopeko said:**
> Not even slug71 knows why PK is better then apt/dpkg/whatever.


> **zekopeko said:**
> I didn't say that it replaces them.

Sorry, the first quote about PK being better than apt/dpkg led me to believe that you thought it replaces them. But it cant be better than them because it uses them.


> **zekopeko said:**
> I still see no compelling reason why we should use PK. PK is essentially another abstraction layer on top of one interface to dpkg. So you have dpkg->apt-get/aptitude->PK->PK GUI.
I really don't see what is so great here.

And this API thing you are mentioning. You still didn't explain it to me what is so great about it.
You still have to create debs/rpm/whatever for specific distro. I don't see how this will unify package management or be beneficial to Ubuntu.

Correct, unless Smart was used. Then it would be .deb/.rpm->smartpm->PK->GUI.

At the moment every package manager has its own API which tells the package manager how to handle the files and its dependencies for installation of x package on that distro. Packages therefore have to be 'ported' for use by those APIs so that correct file handling and dependencies are done for that Distro. 

PK brings a single API to do this regardless of what distro it is being used on.

But yes debs/rpms will still have to be created but thats the job of the backend to handle and not PK. PK just makes sure the conffiles and dependencies are satisfied.

> **zekopeko said:**
> EDIT: On further deliberation is still don't see what are you talking about. 

Let's take for example since this bugs me:

Please do tell how are you going to install packages between PK 0.4 and let's say 0.6.
The apt backend might have changed between 0.4 and 0.6 so you still have to do "porting". Not to mention that you still have to do distro specific packages since distros might work differently with your package. I don't get this API argument.

The backends to PK only change so that they can relay better information to the PK API for the better handling of packages. Thus theyre only improved on or fixed. They dont have to be 'ported' between versions simply because 0.6 in your eg. would just handle the packages better than 0.4 did. Giving better usability to the end user in the end.

See [http://www.packagekit.org/pk-matrix.html](http://www.packagekit.org/pk-matrix.html)

But again, yes youd still have to have distro specific packages like rpm/debs but those are handled by the backends not PK. PK just handles the files and dependencies of them and since PK has its own backends to all the many Distros, only a single API needs to be written to for a package to be handled and satisfied by PK. 

> **zekopeko said:**
> EDIT2: After a little research is found the only compelling reason to switch to PK. Installing plugins from applications. But then the question is how will the app know what is the package name? Guess that will have to be resolved by package maintainers.

Yes that is a very cool feature and probably my fav. at the moment.
It does so by PK plugins to that app. Type packagekit in Synaptic and you will see mozilla-packagekit, gstreamer-packagekit. Thats how it knows what application is asking for what.

---

### Post by phenest on 2009-11-03
> **Ellipsis said:**
> Also more Ubuntu One integration
+ source release for server side code.

-1 for Ubuntu One integration. Ubuntu One should not be in the default install at all. There are users who don't want or need it, therefore it should be installable for those who do.

Restore the way the hardware volume control works. The LFE channel on my laptop is unusable since it was made more 'intuitive' in Karmic. I can't use Karmic because of it.

Thunderbird as default instead of Evolution. It is a superior mail/news client that would complement Firefox.

Ditch xsplash in favour of Plymouth. It doesn't hurt to support 3rd party projects instead of creating your own.

There is a lot of hype surrounding PA. Even if the devs get it working in Lucid, there should be a means to remove it (from Software Center?) easily for those with no need for it. Same applies to Compiz as far as removing it is concerned.

Ubuntu should not have "killer apps" in order to 'sell' itself.

---

### Post by Merk42 on 2009-11-03
> **phenest said:**
> Ubuntu should not have "killer apps" in order to 'sell' itself.

What is Ubuntu (or any other distro), other than a collection of apps?

---

### Post by zekopeko on 2009-11-03
> **phenest said:**
> -1 for Ubuntu One integration. Ubuntu One should not be in the default install at all. There are users who don't want or need it, therefore it should be installable for those who do.

I like it. And you don't have to use it. Following that logic you might as well build your own custom CD.

> Restore the way the hardware volume control works. The LFE channel on my laptop is unusable since it was made more 'intuitive' in Karmic. I can't use Karmic because of it.

Could you elaborate on this. Not sure whats wrong here.

> Thunderbird as default instead of Evolution. It is a superior mail/news client that would complement Firefox.

Not really an option. Evolution is an enterprise level app. Can really compare apples and oranges.

> Ditch xsplash in favour of Plymouth. It doesn't hurt to support 3rd party projects instead of creating your own.

And why shouldn't the 3rd party support xsplash instead? Perhaps it's better then 3rd parties offering? I know that it's at least easier to create themes for it.

> There is a lot of hype surrounding PA. Even if the devs get it working in Lucid, there should be a means to remove it (from Software Center?) easily for those with no need for it. Same applies to Compiz as far as removing it is concerned.

Sorry to tell you, but pulseaudio is the future of dekstop linux sound. And most PA bugs in Ubuntu are either because of poor audio drivers or poor integration.

---

### Post by meeples on 2009-11-03
> **jarlath said:**
> 
I'd like to see canonical hire a lot more developers so we don't have to rely on the pace of individual open-source projects. I'm 30 now and I don't want to have to wait until I'm 30 and a half to see Banshee as the default media app in Ubuntu. Let's just get in there and nail it with loads of developers and make the next release perfect!

+1 on that

i really think ubuntu would do so much better if it started doing its own thing a little more than it is already. If we have a problem with an app why rely on upstream maybe dealing with it if they feel like it?

If you want a job done, do it yourself. 

I think ubuntu also needs alot more of its own apps to stand out a bit more, i know we already have ubuntu one and xsplash and USC(which btw needs alot of improvements before it will be good in my book), but a decent uhh let's say email client would be quite nice...

---

### Post by TheForumTroll on 2009-11-03
> **qamelian said:**
> Nope. T&L may have the feature set for home use and SOHO/small business, but it doesn't cut it in my work place.
 

Then install it? Would you change to Windows if gedit was removed as default and you "needed" it too? I can see where the avatar is coming from :KS


Only thing i think there should be is bug fixes so Ubuntu could get out of beta again ):P

---

### Post by phenest on 2009-11-03
> **zekopeko said:**
> Could you elaborate on this. Not sure whats wrong here.
Open alsamixer in a terminal and turn your volume up and down via the hardware volume buttons and tell me what you see. Then compare this between Karmic and Jaunty. In Jaunty you can have multiple channels moving synchronously. In Karmic, they are preset to move asynchronously.
> **zekopeko said:**
> Not really an option. Evolution is an enterprise level app. Can really compare apples and oranges.
Enterprise level app? Not sure what you mean but Evolution sucks. It doesn't display html emails as well as TB, and no inline attachments. Newsgroups are a nightmare and even causes it to crash. It's very lacking compared to TB.
> **zekopeko said:**
> Sorry to tell you, but pulseaudio is the future of dekstop linux sound. And most PA bugs in Ubuntu are either because of poor audio drivers or poor integration.
The future of what? PA is all about mixing. Who the hell needs to hear audio from many apps at once? I only want to hear one at a time.

---

### Post by phenest on 2009-11-03
> **jarlath said:**
> I'd like to see a revamped theme for the desktop.
Not that old chestnut again!
> **jarlath said:**
> I'd like to see canonical hire a lot more developers so we don't have to rely on the pace of individual open-source projects. I'm 30 now and I don't want to have to wait until I'm 30 and a half to see Banshee as the default media app in Ubuntu.
I think Mark has only so much money. And 6 months is such a long time to wait.
> **jarlath said:**
> I also think canonical should do a user interaction survey with users of Thunderbird and Evolution.
Ubuntu already has a package survey mechanism built-in. All you need to do is turn it on.
> **jarlath said:**
> Finally, I'd like launchpad to do a bit more on the processing side of things. I don't want to have to send in bug reports with 'this didn't work' or 'that was wierd' details. I just want to send in a 'tut tut tut' and have launchpad figure out what the problem is. I know it's radical thinking, but it would be really cool and save me loads of time so that I can... have more time.
What!? How are the devs supposed to work it out from nothing more than a "tut, tut, tut"? They can't do anything without details.
> **jarlath said:**
> Also, now that we're going with cloud based services...
And who is "we"?
> **jarlath said:**
> I'll be back in April to check how things are going so stay motivated everyone - at least until these issues are dealt with. After that I don't mind too much if people have personal issues or anything making them feel a little under the weather or whatnot. That's understandable.
That's it. You just put in your gripes and go away and relax until April when everything will be ready for you. Thanks for your help. Not!

Have I just replied to a troll?

---

### Post by ranch hand on 2009-11-03
> **lykwydchykyn said:**
> Ok, I don't want to derail this thread, but I keep hearing people say they want packagekit.  Having suffered through KPackageKit for a while now, I really have to ask -- why?  What is so compelling about it?  From my POV, it doesn't support a large number of the features of APT/DPKG (see [here]("http://ubuntuforums.org/showpost.php?p=8199979&postcount=15") for my list).  Granted, work is being done to make it a better interface, but until then what's the advantage?
You get to spend more time looking for what you want and then it makes sure that you have a "healthy" heart rate by screwing up.  That is the main advantage.

---

### Post by qamelian on 2009-11-03
> **phenest said:**
> Enterprise level app? Not sure what you mean but Evolution sucks. It doesn't display html emails as well as TB, and no inline attachments. Newsgroups are a nightmare and even causes it to crash. It's very lacking compared to TB.

I'm not sure why you have a problem with HTML mails in Evolution, as I've always found it flawless. And maybe it's just a personal thing, but I'm more ready to apply the term "sucks" to TB because it just doesn't have the features I need. Don't even get me started on newsgroups. Last time I tried to use TB as a newsreader it was a very poor joke at best. In my opinion, it is the other way around: TB is very lacking compared to Evolution.

---

### Post by Merk42 on 2009-11-03
> **phenest said:**
> Who the hell needs to hear audio from many apps at once? I only want to hear one at a time.

This, this is a joke right? 
Not being able to play two sounds at once is a really basic thing. And while you may not want to listen at both, the problem is you can't hear audio in Foo because Bar is running.

---

### Post by ranch hand on 2009-11-03
> **Merk42 said:**
> This, this is a joke right? 
Not being able to play two sounds at once is a really basic thing. And while you may not want to listen at both, the problem is you can't hear audio in Foo because Bar is running.
My, you must be really used to way too much noise.

---

### Post by flipper9 on 2009-11-03
What do I want to see? Be able to support all modern video cards, stock sound cards, network cards, and widely-used hardware.  It's time for Linux to support modern hardware out of the box without major issues.

Have an upgrade advisor piece of software that runs under Windows/Linux/MacOsx or a tiny downloadable cd-rom that can tell the user if their hardware is supported.

---

### Post by ranch hand on 2009-11-03
We have that.  It is called a Live CD.

---

### Post by Merk42 on 2009-11-03
> **ranch hand said:**
> My, you must be really used to way too much noise.

I'm not sure what you mean by this.

---

### Post by ranch hand on 2009-11-03
> **Merk42 said:**
> I'm not sure what you mean by this.
No, I suppose you don't.

What I mean is "What in flinderation do you want noise from more than one of the buggers for?  My god, it would drive me mad  Mad You Hear  MAD!!!!"

I hope that cleared up my meaning somewhat in a quiet and dignified way.

I am one of those folks that have every noise the box can make turned off if I can figure a way to do it.

---

### Post by flipper9 on 2009-11-03
> **ranch hand said:**
> We have that.  It is called a Live CD.

Oh sorry, guess I was confused when the Live CD worked and then booted to a black screen on install.  Silly me.

---

### Post by ranch hand on 2009-11-03
I take it that you do not do much building in your job.

What you are saying, I take it, is that someone should design and build a program, to run on tree different architectures, that will test the hardware on your box better than an operating system that is designed to just boot from that hardware.

I am also guessing that you have never had the pleasure of installing an MS product.  Now there is where you start having some problems with hardware and drivers.

---

### Post by murderslastcrow on 2009-11-03
Multimedia types, like the ones who use Ubuntu Studio, needs multiple apps to have audio enabled at once. If PulseAudio works perfectly soon, I don't see why we shouldn't use it.

I think iPod Touch and iPhone support would get more average users (that is, over 90 percent of computer users), and luckily it seems we will have this in Lynx! [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

I love how much we ask for. It just shows how much everything will continually improve. And with great native apps and services like Ubuntu One, I think we can leverage more than simply feature-parity, but in many ways Lynx could show just how superior a Linux OS can be.

I look forward to the Boot Experience being finished up so we can start skinning all those cool utilities (including xsplash), along with the Software Center becoming more complete and integrated. As long as it's not cluttered or confusing, it would be brilliant to have all the software-centric tasks managed by one utility.

I just love how I can close the Software Center while it's installing and it'll still complete everything. Brilliant!

But, although we have come very far, there is still a far way to go to reach a more perfect user experience. This is a very good thing. I'm afraid that a lot of our requests will be waiting for 10.10 to get included, however, since Lynx is an LTS after all.

---

### Post by epsolon77 on 2009-11-03
> **flipper9 said:**
> What do I want to see? Be able to support all modern video cards, stock sound cards, network cards, and widely-used hardware.  It's time for Linux to support modern hardware out of the box without major issues.

Have an upgrade advisor piece of software that runs under Windows/Linux/MacOsx or a tiny downloadable cd-rom that can tell the user if their hardware is supported.

I think the problem with hardware is a driver issue that is normally supported on the hardware vendor's side, not the OS side.  Though having all video cards working would be great.

I think having a MS app that would tell you what components you might have trouble with would be a good idea, but then again the live CD does a good job too.

---

### Post by Glenn nl on 2009-11-04
> **jarlath said:**
> 
I'd like to see canonical hire a lot more developers so we don't have to rely on the pace of individual open-source projects. I'm 30 now and I don't want to have to wait until I'm 30 and a half to see Banshee as the default media app in Ubuntu. Let's just get in there and nail it with loads of developers and make the next release perfect!

I also think canonical should do a user interaction survey with users of Thunderbird and Evolution. The results can be used to make a new application called ThunderLution, which will satisfy both sets of users.


+1
More developers and thunderbird

---

### Post by tga24 on 2009-11-04
> **ranch hand said:**
> 
I am also guessing that you have never had the pleasure of installing an MS product.  Now there is where you start having some problems with hardware and drivers.

I agree entirely.
I had to reinstall windows xp on my laptop a year ago. The sound didn't work, neither did the bluetooth, wifi or the multimedia buttons. All of these have always worked straight out of the box in ubuntu.

---

### Post by k3lt01 on 2009-11-04
> **jarlath said:**
> I'd like to see a revamped theme for the desktop. The new one is nice, but I'd like to see a little more schazzzaaaam! At the moment, it's a little bit 'oooh, that's nice' but not very 'wow! I think I need to change my pants!' Also, I like green so if there could be lots of green that would be great too.

I'd like to see canonical hire a lot more developers so we don't have to rely on the pace of individual open-source projects. I'm 30 now and I don't want to have to wait until I'm 30 and a half to see Banshee as the default media app in Ubuntu. Let's just get in there and nail it with loads of developers and make the next release perfect!

I also think canonical should do a user interaction survey with users of Thunderbird and Evolution. The results can be used to make a new application called ThunderLution, which will satisfy both sets of users.

Finally, I'd like launchpad to do a bit more on the processing side of things. I don't want to have to send in bug reports with 'this didn't work' or 'that was wierd' details. I just want to send in a 'tut tut tut' and have launchpad figure out what the problem is. I know it's radical thinking, but it would be really cool and save me loads of time so that I can... have more time.

Also, now that we're going with cloud based services, do you think we could get a plugin for Ubuntu One that would make it a dating service also? I haven't had a girlfriend in ages and the girls here don't like the way I flirt with them... or maybe they're just playing hard to get but if you're hot and your in the phone book then it's only natural that I'm going to turn up on your doorstep with an Ubuntu CD and some flowers right?

I'll be back in April to check how things are going so stay motivated everyone - at least until these issues are dealt with. After that I don't mind too much if people have personal issues or anything making them feel a little under the weather or whatnot. That's understandable.Methinks you need a little bit of a lay down if your only 30 and can't wait 6 months for Banshee to be default. What will happen if it doesn't make it?

Microsoft tried the green field idea with XP remember, it looked to perfect and XP was far from that.

As for the rest of your post, well its hard to take it seriously, so please feel free to ignore my astral contempt.

---

### Post by k3lt01 on 2009-11-04
> **ranch hand said:**
> I am also guessing that you have never had the pleasure of installing an MS product.  Now there is where you start having some problems with hardware and drivers.I had the pleasure of saving all of my Bosses business info yesterday after a trojan got into Vista. Ah the good old days of searching, downloading, rebuilding, searching some more, even more downloading and more rebuilding just to get Vista to boot long enough to get SpyBot to do what Nortons couldn't.

God I love Ubuntu, if it wasn't for my laptop I would have had to wipe the Vista box clean and start all over again even manually typing in the lost data cause someone forgot to do a backup. Wasn't me either btw and there are only two of us where I work :lolflag:

---

### Post by phenest on 2009-11-04
> **Merk42 said:**
> This, this is a joke right? 
Not being able to play two sounds at once is a really basic thing. And while you may not want to listen at both, the problem is you can't hear audio in Foo because Bar is running.

No joke. If I'm listening to Bar in Rhythmbox, why do I want to hear something from Foo. After all, if Foo is important, then there is all those visual notifications that could inform me instead.

---

### Post by Merk42 on 2009-11-04
> **phenest said:**
> No joke. If I'm listening to Bar in Rhythmbox, why do I want to hear something from Foo. After all, if Foo is important, then there is all those visual notifications that could inform me instead.

You misunderstood my clarification.

I'll give an example where audio from multiple devices doesn't neccesarily mean listening to two overlaping audio sources:
I'm listening to music in Rhythmbox while working. I have trouble with something so I go look up a tutorial on Youtube in Firefox, even if I pause Rhythmbox I still can't hear the audio in Youtube because Rhythmbox is still 'playing'.  I have to shut down Rhythmbox, and Firefox, then reopen Firefox.

I used to have that problem a LOT I think in either Hardy or Intrepid.

---

### Post by Veinor on 2009-11-04
> **phenest said:**
> No joke. If I'm listening to Bar in Rhythmbox, why do I want to hear something from Foo. After all, if Foo is important, then there is all those visual notifications that could inform me instead.

Not to mention if I'm playing a flash game or a game in WINE, I might want to mute the soundtrack and then play my own via Rhythmbox or whatever.

---

### Post by phenest on 2009-11-04
> **Merk42 said:**
> You misunderstood my clarification.
Correct. I misunderstood.
> **Veinor said:**
> Not to mention if I'm playing a flash game or a game in WINE, I might want to mute the soundtrack and then play my own via Rhythmbox or whatever.
I guess I'm not using the sound on my machine as much as the rest of you guys, or as much as I could be.

---

### Post by phenest on 2009-11-04
> **qamelian said:**
> I'm not sure why you have a problem with HTML mails in Evolution, as I've always found it flawless. And maybe it's just a personal thing, but I'm more ready to apply the term "sucks" to TB because it just doesn't have the features I need. Don't even get me started on newsgroups. Last time I tried to use TB as a newsreader it was a very poor joke at best. In my opinion, it is the other way around: TB is very lacking compared to Evolution.

Really? It's not like we're going to have different setups. Seriously, I tried to use NG's on Evo to find browsing the groups time consuming. No search feature like TB has. Also, there is no way to disable asking me for a password, when I didn't need one (ISP supplied NG's). And then, during switching between one group and another, Evo would lock up claiming it was retrieving messages. Not to mention I could only retrieve the first few posts (and I mean a few) out of the possible 1000's that TB offered. Ok, maybe this is OT now, but that was my experience of Evo.

---

### Post by wxnker on 2009-11-04
- Synaptic/apt-get

One of the biggest annoyances for me when using Ubuntu is the fact that I need to close Synaptic if I want to use apt-get in a terminal. I would like this to change so that synaptic only locks the database while installing.
[http://brainstorm.ubuntu.com/idea/7108/](http://brainstorm.ubuntu.com/idea/7108/) 

- Notifications
Being able to customize notifications. Also I would prefer if notifications would offer user interaction. Otherwise they tend to be eye candy only. If the notification is there, why not allow users to click for a common task.

- Gnome defaults
I don't want Banshee instead of Rhythmbox by default and I don't want Thunderbird instead of Evolution by default. If users prefer these application, then they can easily install them. I very much like the defaults.

---

### Post by seeker5528 on 2009-11-04
> **ranch hand said:**
> No, I suppose you don't.

What I mean is "What in flinderation do you want noise from more than one of the buggers for?  My god, it would drive me mad  Mad You Hear  MAD!!!!"

Well, some people might not want their music player, video player, etc... to fail just because a system sound happened to start playing just as they opened the player.

Some people might want to listen to music and still be able to hear audio alerts when they get new email, somebody pings them in their IM, etc...

Might want to listen to music while playing a game, but still hear the audio from the game.

I'm sure there are plenty of other examples.

Later, Seeker

---

### Post by flipper9 on 2009-11-04
> **tga24 said:**
> I agree entirely.
I had to reinstall windows xp on my laptop a year ago. The sound didn't work, neither did the bluetooth, wifi or the multimedia buttons. All of these have always worked straight out of the box in ubuntu.

Yeah; but Windows XP and later versions didn't give you blank screens or refuse to boot generally.  There should be better "safe modes" built-in to allow a user to be able to boot into their system (no required need for a CDROM or USB Key with a rescue Live CD) and fix the problem.  You could always boot into some low video mode and at least get into the system to do something.  Some people can boot, but they can't do anything.  In fact, I would think that we could do better than Windows.  Where is the extensive testing on lots of different moderately older and new hardware?  It should just work.  If not, there should be a better solution than having to spend hours diving through forums to find complex fixes and workarounds.  Things should be more automated.

---

### Post by Dayofswords on 2009-11-04
well, i'd like the inclusion of seahorse-plugins, which was oddly missing from 9.10

---

### Post by seeker5528 on 2009-11-04
There is a package kit FAQ:

[http://www.packagekit.org/pk-faq.html](http://www.packagekit.org/pk-faq.html)

The interesting things to me:

> How does PackageKit handle dependencies?

PackageKit does not do dependency resolution. This problem has already been solved by the backend systems and we don't really want to re-invent the wheel.

PackageKit does not have the fine-grained API to do everything. For instance, synaptic should still use libapt as can do much more than can be provided by PackageKit. 


How does PackageKit work with multiple users?

PackageKit is designed from the ground up to work with fast user switching and logging in and out of sessions during upgrades. You can start a system upgrade, log out, log in as another user, and be notified when the upgrade is complete, all without risking your rpmdb. 

So none of the PackageKit front ends are going to be able to compete with Synaptic based on advanced features, but it is great for a more simplified front end or utilities that provide specific functions like the 'command not found' utility, the codec installer, looking for browser extensions/plug-ins, etc... like has already been mentioned.


> **Slug71 said:**
> 
Yes that is a very cool feature and probably my fav. at the moment.
It does so by PK plugins to that app. Type packagekit in Synaptic and you will see mozilla-packagekit, gstreamer-packagekit. Thats how it knows what application is asking for what.

I'm not seeing anything about it at the moment, but I could swear that somewhere there was an indication that since package kit is a daemon you could do something like open a package manager front end and install some stuff, meanwhile you could find out you need a plug-in in Firefox and the browser helper could identify that it is available in the repositories and queue the installation without having to wait for the other installations to be complete.

Not completely sure on this, there is a queue, but this might only mean that in the above scenario the search for the plug-in, instead of failing, would be queued to start after the current installation was completed.

Either way it's still better than having it fail because there is a lock on the apt database.

Later, Seeker

---

### Post by seeker5528 on 2009-11-04
> **flipper9 said:**
> Yeah; but Windows XP and later versions didn't give you blank screens or refuse to boot generally.

Safe mode in XP was not all that reliable. 

Many is the case where I had to deal with a system constantly reboots without showing you anything, or shows a blue screen with an error code, but reboots before you can read it. Then when you choose the option not to reboot automatically, copy down the error code, look it up on google from another system, often the error codes don't help you much. And if you can't get into safe mode you are much more limited in what you can do than you are with a Linux system. 

Vista included something that can at try to recover from some types of errors, roll back updates, etc... but it is still more reliable to use these things from the Vista installation disk.

What Ubuntu provides for this could and should be improved upon, but the recovery options provided are decent and there are a lot of other things that personally I would place at a higher priority.

Later, Seeker

---

### Post by williejones on 2009-11-04
I would like to see better internet wireless support.  Ndiswrapper works better than the provided kernel Artheos 9 driver.  I would also like to see support for wireless N connection.

New users would expect their connections to work if they are going to switch to a new operating system.  If their connection does not work (and work good) they are not going to give Ubuntu a chance.  

Most people are not like the regulars in this forum.  They will not spent the time to research and fix anything not working.

---

### Post by ranch hand on 2009-11-04
> **williejones said:**
> I would like to see better internet wireless support.  Ndiswrapper works better than the provided kernel Artheos 9 driver.  I would also like to see support for wireless N connection.

New users would expect their connections to work if they are going to switch to a new operating system.  If their connection does not work (and work good) they are not going to give Ubuntu a chance.  

Most people are not like the regulars in this forum.  They will not spent the time to research and fix anything not working.
You know, I have come to loath posts that talk about how the average guy coming to Ubuntu is going to freak if we don't do this or that.

The post, I am happy to admit, makes sense.  Bells and silly whistles are alright in their place, but what folks really want is a box that works.

---

### Post by flipper9 on 2009-11-04
> **seeker5528 said:**
> Safe mode in XP was not all that reliable. 

Many is the case where I had to deal with a system constantly reboots without showing you anything, or shows a blue screen with an error code, but reboots before you can read it. Then when you choose the option not to reboot automatically, copy down the error code, look it up on google from another system, often the error codes don't help you much. And if you can't get into safe mode you are much more limited in what you can do than you are with a Linux system. 

Vista included something that can at try to recover from some types of errors, roll back updates, etc... but it is still more reliable to use these things from the Vista installation disk.

What Ubuntu provides for this could and should be improved upon, but the recovery options provided are decent and there are a lot of other things that personally I would place at a higher priority.

Later, Seeker

Granted, the auto-recover tools sucked in Windows.  But, working on many systems, I was always able to boot into the system to fix problems or even startup in non-safe mode with a working video mode.  Stop codes were generally from faulty hardware.  On Linux, sometimes the configuration gets screwed up or some update keeps you from booting entirely, and forces you to a command line where you have no GUI tools to work with.  

I'm suggesting we do better.  We have a rescue video mode where you can ALWAYS (barring hardware issues) get to a GUI tool.  We have rescue access to at least a wired network connection to download updates.  We have all drivers available, at least at some level, so people's systems will work at a minimal level (network works, video works, sound works, printers print).  It's time to bring Linux to that level where things just work.  Or at a minimum, a user can get to GUI tools to fix problems...hopefully from automated wizards that can pull in HOWTO info from the net, or better yet fix the problem.  Tall order, but it's just a suggestion thread. :P

---

### Post by ranch hand on 2009-11-04
Ah, now I see.  We need more, not less, bloat.

---

### Post by lykwydchykyn on 2009-11-04
How about an easy point-n-click way to chroot into a borked system from the LiveCD, so you can make repairs to an unbootable system?  Someone could probably whip something together in an afternoon in python; the hardest part would be explaining what the software is actually doing in layman's terms.

I could wish for a KDE user manual that wasn't 5 years and one major version out of date, but that's an upstream issue I guess.

---

### Post by ranch hand on 2009-11-04
> **lykwydchykyn said:**
> How about an easy point-n-click way to chroot into a borked system from the LiveCD, so you can make repairs to an unbootable system?  Someone could probably whip something together in an afternoon in python; the hardest part would be explaining what the software is actually doing in layman's terms.

I could wish for a KDE user manual that wasn't 5 years and one major version out of date, but that's an upstream issue I guess.
WOW, I really like that idea.  It is, probably not a real good one, but boy, I would love it.

Can you imagine the amount of damage some folks would do to their their system? 

If someone came up with it I would use it and use remastersys (after update for grub2) to make a disk.  Just click, enter the partition and hit enter.  Destroy your system, or fix it if you are smarter than the chair you are sitting on.

That would be sweet.

---

### Post by absolutezero1287 on 2009-11-05
I'd like to see a cli-only runlevel included by default. This is a very simple request and its stems from my experience with another Linux distro, ArchLinux.

With Archlinux I would start off in runlevel 3 and had my .xinitrc set up to accept arguments so "xinit $WM" would start whatever window/desktop manager I specified. I like NOT having a login manager because I feel that its just a waste of resources. Therefore having the option to start off at cli-only runlevel would be nice.

Another thing that bugs me are the metapackages. I've tried to make a minimal version of Ubuntu using debootstrap but I find that installing certain things causes a lot of unwanted things to be installed along with it. If I were to have my own custom *buntu I'd install the ubuntu base with fluxbox, xmonad, and a few of my favorite apps.

Last suggestion would be the support for BSD partitioning schemes. I dualboot with FreeBSD and I can't see my FreeBSD partitions.

---

### Post by gnomeuser on 2009-11-05
> **ranch hand said:**
> Ah, now I see.  We need more, not less, bloat.

One mans bloat is another mans vital feature. E.g. there was similar debate going when people wanted to build a windowing system, when internationalization was implemented, when we got anti aliased text.. 

We are not to bloated, we are approaching feature completeness for all mankind, for all use cases.

---

### Post by k3lt01 on 2009-11-05
> **gnomeuser said:**
> We are not to bloated, we are approaching feature completeness for all mankind, for all use cases.So all the games that come as standard aren't bloat?

I wonder what a "One Laptop per Child" user thinks when they are confronted with 16 games, some of which have just as many types in one game, and only 5 "Office" applications. How is that feature rich for all mankind? are we trying to teach kids to play computer games when they would be much better off playing a physical game or are we trying to help them get an education? What about Business users? why do they need all these games instead of good open source (i.e. FREE) business software.

I think we have a very different idea of what feature completeness means.

btw this isn't an argument with you personally, just a very different way of looking at things.

---

### Post by slakkie on 2009-11-05
> **absolutezero1287 said:**
> I'd like to see a cli-only runlevel included by default. This is a very simple request and its stems from my experience with another Linux distro, ArchLinux.


Install a cli only system via the alternate CD/minimal install CD, install xinit, install whatever window manager you want, disable [xgk]dm (or remove the packages) and you should have a cli only system with X at your finger tips.

---

### Post by zika on 2009-11-05
> **slakkie said:**
> Install a cli only system via the alternate CD/minimal install CD, install xinit, install whatever window manager you want, disable [xgk]dm (or remove the packages) and you should have a cli only system with X at your finger tips.That looks nice. It reminds me of DesqView (thirty years ago) ...

---

### Post by UKBB on 2009-11-05
A menu option when you right click the desktop to shutdown like they have in KDE. Also an option when installing to disable the 60 second shutdown counter.

---

### Post by jerrylamos on 2009-11-05
Lucid - please, don't break video!  Can't test with a broken desktop!

Karmic video did not work! as updated for weeks or months on intel and/or ati.  It's a pain trying to look for bugs in new features if the screen won't work.  Thru the karmic forum I was able to get the screens to work with various tricks.

Video performance even now with the karmic intel drivers is slower than vesa!   Example on intel i845 video the benchmark GtkPerf is 28% slower with ubuntu intel 2.9.0 driver than with vesa.  

Could be Intrepid is the peak video performance on intel, even though Compiz is busted with that configuration.  My opinion, Compiz is window dressing not application function.

Rule #1: early Lucid should boot and run the screen.  I hope....

Jerry

---

### Post by slakkie on 2009-11-05
Actually, I would like to see debdiffs, but it would not be feasible in an LTS. If they would start with it in Lucid, but deliver it in 10.10 that would be nice too. Then backport it maybe to Lucid when it's done..

---

### Post by akand074 on 2009-11-05
Boot speed! Most important thing. In jaunty I could boot and fully log in within 25 seconds at most, with Karmic its up to about 50 seconds to a minute. Thats no good! Built in touch drivers for tablet PCs! Other than that, I'm quite content with ubuntu it may have the odd bugs here and there but theres always a reason for what happened and there is always a way to fix it. Best OS in the world! I can't wait to see what Lucid is like, I've seen some neat ideas from some people but with linux performance comes first! Looks comes second, like the nicer boot in Karmic = slower boot. Thats no good. I believe focus should be left on performance and the extras only added if it can be done without sacrificing any or too much performance

---

### Post by slakkie on 2009-11-05
personally, I don't care about boot speeds. My servers run 24/7 and my laptop booting allows me to go for coffee..

---

### Post by akand074 on 2009-11-05
> **slakkie said:**
> personally, I don't care about boot speeds. My servers run 24/7 and my laptop booting allows me to go for coffee..
 
Hahahaha thats a nice way to take advantage of it! But I mean theres many times when you just want to quickly check a website, boot speed is essential there. For servers its hardly an essential feature but for everyday use, when I'm rushing to get my laptop booted for class, you want a fast boot speed and great performance while logged in. Several friends of mine told me that they dual boot ubuntu now just for the boot speed. 
 
I should deffinately get into the whole coffee in the morning, so that I'm not sleeping through all my morning classes haha.

---

### Post by slakkie on 2009-11-05
Get to work, plug in all devices to laptop, boot laptop, get coffee, talk to others while drinking coffee, get back to desk, start slacking^Wworking ;)

---

### Post by absolutezero1287 on 2009-11-05
> **slakkie said:**
> Install a cli only system via the alternate CD/minimal install CD, install xinit, install whatever window manager you want, disable [xgk]dm (or remove the packages) and you should have a cli only system with X at your finger tips.

Its not the same as having a cli-only runlevel. For example, you could have different entries in Grub. One that boots the system into runlevel 5, which starts the login manager and all that fun GUI stuff, and one that starts at runlevel 3 which boots you into the cli-only system. Simply installing a "cli-only" system isn't enough. Read up a bit on runlevels.

---

### Post by absolutezero1287 on 2009-11-05
> **k3lt01 said:**
> So all the games that come as standard aren't bloat?

I wonder what a "One Laptop per Child" user thinks when they are confronted with 16 games, some of which have just as many types in one game, and only 5 "Office" applications. How is that feature rich for all mankind? are we trying to teach kids to play computer games when they would be much better off playing a physical game or are we trying to help them get an education? What about Business users? why do they need all these games instead of good open source (i.e. FREE) business software.

I think we have a very different idea of what feature completeness means.

btw this isn't an argument with you personally, just a very different way of looking at things.

sudo apt-get remove gnome-games

problem solved

When people refer to bloat they usually mean about processes that are constantly running. Some may say that Firefox is bloat because it uses more resources than another web browser. Games aren't really bloat when there are 1 TB HDD available.

However, lets say that there were only a few games installed by default. You would be happy. You would say, now THIS is a serious business OS. I don't need all those sundry amusements. However, when a more casual user installs it they say: where's solitaire, checkers, and all the games?

If you want more business software take a look at IBM's Lotus. If the games annoy you that much then simply remove them. Its not bloat if you can remove them so I really don't see what the complaining is about.

---

### Post by slakkie on 2009-11-05
> **absolutezero1287 said:**
> Its not the same as having a cli-only runlevel. For example, you could have different entries in Grub. One that boots the system into runlevel 5, which starts the login manager and all that fun GUI stuff, and one that starts at runlevel 3 which boots you into the cli-only system. Simply installing a "cli-only" system isn't enough. Read up a bit on runlevels.

Have a look here: [http://www.debian-administration.org/article/An_introduction_to_run-levels](http://www.debian-administration.org/article/An_introduction_to_run-levels)

> 
Run levels 2 through 5 are full multi-user mode and are the same in a default UserLinux (Debian) system. It is a common practise in other Linux distributions to use run level 3 for a text console login and run level 5 for a graphical login.


See also some useful comments here: 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

I think such a change is pretty drastic for Ubuntu to do on its own. A change like this would need to be made into Debian.

---

### Post by Lieter on 2009-11-05
**radeonhd xorg driver as an alternative to fglrx.**
Groundwork for kms is in 2.6.32 and i have (as far as i've tested) full compositing and 3d support on fedora 12 beta using that driver. I can play alien arena and other games. And compiz appears to run smoother on radeonhd than on fglrx.

**Opensource 3d videodrivers (if mature enough, otherwise lucid+1)**
As the former, use nouveau and radeonhd to supply user with an instant composited(metacity or compiz) desktop. The lack thereof is a turnof for first-timers(see also next idea)

**New default theme**
Karmic was a great improvement over the previous versions(especially the wallpapers). However it still is not as pretty as a clean install of (forgive me) windows 7 or fedora. The brown color isn't what i want to see, its not "fresh".

**Blueman as replacement for bluetooth-applet**
Blueman if full featured and allows easy creation of pan's and rfcomm(3g modem over bluetooth :D). 

the first and the last are my personal requests, the other two are more for first timers.

---

### Post by absolutezero1287 on 2009-11-05
> **slakkie said:**
> Have a look here: [http://www.debian-administration.org/article/An_introduction_to_run-levels](http://www.debian-administration.org/article/An_introduction_to_run-levels)



See also some useful comments here: 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

I think such a change is pretty drastic for Ubuntu to do on its own. A change like this would need to be made into Debian.

True, but what is the point of having runlevels 2-5 do the same thing?
I think this makes more sense:
 * 0		System Halt
 * 1		Single user
 * 2		Full multi-user mode (Default)
 * 3		Console login
 * 4            Not used
 * 5            Graphical Login
 * 6		System Reboot

---

### Post by absolutezero1287 on 2009-11-05
True, but what is the point of having runlevels 2-5 do the same thing?
I think this makes more sense:
 * 0		System Halt
 * 1		Single user
 * 2		Full multi-user mode (Default)
 * 3		Console login
 * 4            Not used (or user defined)
 * 5            Graphical Login
 * 6		System Reboot

---

### Post by absolutezero1287 on 2009-11-05
> **absolutezero1287 said:**
> 
Another thing that bugs me are the metapackages. I've tried to make a minimal version of Ubuntu using debootstrap but I find that installing certain things causes a lot of unwanted things to be installed along with it. If I were to have my own custom *buntu I'd install the ubuntu base with fluxbox, xmonad, and a few of my favorite apps.

I'd just like to elaborate on this post.
I've noticed that with every version of Ubuntu that I've used that uninstalling certain things renders my system unusable. Why is it that removing one thing causes some insane chain reaction?

For example, removing certain packages related to evolution causes the ubuntu-desktop package to be removed. I personally don't use evolution at all. I should be able to remove it without making my system unstable.

I observed the bane of metapackages again when I tried to make a custom Ubuntu install using debootstrap and a chroot. I installed the intel driver for xorg and it made me install many other drivers that I don't need. Now, I know the drivers are small but the point is that I shouldn't have to install crap that I don't need for the sake of it being convenient. It should be easier for the end-user to install and remove what packages they want without breaking the system.

> **absolutezero1287 said:**
> 
Last suggestion would be the support for BSD partitioning schemes. I dualboot with FreeBSD and I can't see my FreeBSD slices.

In retrospect, this is probably a kernel issue.

---

### Post by seeker5528 on 2009-11-05
> **flipper9 said:**
> Granted, the auto-recover tools sucked in Windows.  But, working on many systems, I was always able to boot into the system to fix problems or even startup in non-safe mode with a working video mode.

Maybe in a controlled environment where updates are managed, users are limited in the software they can install, or at least have a healthy level of paranoia about installing random stuff from the net.

And I do see enough memory and hard drive failures to want to check those things sooner rather than later.

I most commonly deal with home users or small business people where they or their employees install all kinds of crap. I've seen way too many times where these were caused by a bad download from Windows update, bad driver, corruption resulting from a power failure while the system was running, problems with a whole range of software that integrates with explorer or internet explorer, problems with security software, problems with burning software, etc...

It's fairly common, especially with the badware situation being what it is, I have to resort to [System Rescue CD](http://www.sysresccd.org/Main_Page), [RIP](http://rip.7bf.de/current/), boot from the Windows installation disk to get to the recovery console, or stick the hard drive on another machine with Windows and Linux on it to check things out, rename/delete things, nuke the Windows password on the odd occasion, set some service or another not to start, have some registry editing capabilities.  


> On Linux, sometimes the configuration gets screwed up or some update keeps you from booting entirely, and forces you to a command line where you have no GUI tools to work with.  

If the problems are that extreme, expecting to always have a GUI is asking a bit much without having a CD to boot from, having a menu driven, curses/ncurses based recovery interface with some automated processes and option to boot into single-user mode is much more reliable, in particular if the problem is with a video driver, X.org, or the kernel. Options to deal with X.org should be a part of that and network configuration for those who don't have a system wide configuration that is enabled during boot up. If it's a kernel related issue and you can get the the recovery options, then there is a reasonable chance that you can choose to continue on into the normal run level and have all the GUI stuff available.

If the problem is with KDE, Gnome, etc... they should be providing their own safe type of option that can bypass the normal session configurations and allow you to log in with minimal stuff enabled.

I do think there should be some ongoing effort to improve and extend the recovery options, but I think the bigger pay off in the long run is to identify problem areas and find more robust ways of handling error conditions that might result from those without having to resort to the recovery options in the first place.

Later, Seeker

---

### Post by uBeer on 2009-11-05
> **absolutezero1287 said:**
> I'd just like to elaborate on this post.
I've noticed that with every version of Ubuntu that I've used that uninstalling certain things renders my system unusable. Why is it that removing one thing causes some insane chain reaction?

For example, removing certain packages related to evolution causes the ubuntu-desktop package to be removed. I personally don't use evolution at all. I should be able to remove it without making my system unstable.

I observed the bane of metapackages again when I tried to make a custom Ubuntu install using debootstrap and a chroot. I installed the intel driver for xorg and it made me install many other drivers that I don't need. Now, I know the drivers are small but the point is that I shouldn't have to install crap that I don't need for the sake of it being convenient. It should be easier for the end-user to install and remove what packages they want without breaking the system.


In retrospect, this is probably a kernel issue.

Actually, if you first reinstall the ubuntu-desktop package and then try to remove Evolution: tada!! No removal of ubuntu-desktop. Someone told this in the forums a few weeks back. Weird kind of bug, no idea if there is already a bug report for this...

---

### Post by Jordanwb on 2009-11-05
I would like to see MTP support working for my Creative ZEN. I plugged it in, the icon **did** show up on the desktop, I dragged a song to the /Music folder of the ZEN, unplugged it and it didn't show up. I tried to play another song and the album name or song name of some of the songs were truncated. For example Jerry Reed's song "East Bound and Down" was truncated to "East Bo". Gnomad2 does work but it's kinda messy in my opinion.

I would like to see the "ata[Number]: softreset failed (device not ready)" errors gone. The problem is that Port Multiplier Support may be needed on some machines. This isn't a critical problem for me (it is for some), but it doesn't reflect well on Linux.

"[    0.564002] ..MP-BIOS bug: 8254 timer not connected to IO-APIC" But that's a known kernel bug.

I'd like to see less crazy dependencies. I was playing around with openbox in a Vbox vm, to install xorg I had to install about 30 video drivers, of which I'd use only one. absolutezero1287 already touched on this but it still applies.

I'd like to see less foreign fonts installed. I only speak English, so I don't need Korean, Japaneese, Arabic or such fonts installed. There are easy to find and remove but still.

I'd like to see an RSS feed for the lucid release schedule. I sent an email to Canocal (I hope I spelt that right) asking for one and my response pretty much said "Use google calendar".

There was something else I'd like to see changed but I can't remember what it was.:-?

---

### Post by slakkie on 2009-11-05
> **absolutezero1287 said:**
> True, but what is the point of having runlevels 2-5 do the same thing?
I think this makes more sense:
 * 0		System Halt
 * 1		Single user
 * 2		Full multi-user mode (Default)
 * 3		Console login
 * 4            Not used
 * 5            Graphical Login
 * 6		System Reboot

I like the Solaris init levels: [http://www.princeton.edu/~unix/Solaris/troubleshoot/initstate.html](http://www.princeton.edu/~unix/Solaris/troubleshoot/initstate.html)

But you are right, it doesn't make real sense to have 2-5 doing the same thing.

---

### Post by absolutezero1287 on 2009-11-05
> **uBeer said:**
> Actually, if you first reinstall the ubuntu-desktop package and then try to remove Evolution: tada!! No removal of ubuntu-desktop. Someone told this in the forums a few weeks back. Weird kind of bug, no idea if there is already a bug report for this...

I was actually able to remove evolution but evolution-data-server or other evolution related packages. However, you seem to be missing the point. It not JUST evolution. The problem occurs with many packages. Try using debootstrap to build your own custom *buntu or get the minimal install CD to install ONLY the packages you want. Then tell me if you're not thoroughly frustrated. I was less frustrated when I was using Linux from Scratch and had to compile everything from source.

---

### Post by Lieter on 2009-11-05
> **slakkie said:**
> I like the Solaris init levels: [http://www.princeton.edu/~unix/Solaris/troubleshoot/initstate.html](http://www.princeton.edu/~unix/Solaris/troubleshoot/initstate.html)

But you are right, it doesn't make real sense to have 2-5 doing the same thing.

Aren't runlevels kinda depricated with upstart. The System V style of runlevels is quite old. Windows XP has a better "Services" management. I'd love for ubuntu to fully implement(there by depricating init scripts) upstart, but with the possibility to boot or switch to a minimal system(stopping all services except kerneloops and switching to a tty)

---

### Post by absolutezero1287 on 2009-11-05
> **Lieter said:**
> Aren't runlevels kinda deprecated with upstart. The System V style of runlevels is quite old. Windows XP has a better "Services" management. I'd love for ubuntu to fully implement(there by depricating init scripts) upstart, but with the possibility to boot or switch to a minimal system(stopping all services except kerneloops and switching to a tty)

Exactly how are they deprecated when many Linux distributions still use runlevels? There's really nothing wrong with runlevels in my opinion. If it ain't broke don't fix it.

Upstart is simply an alternative to System V init. It does seem to have advantages over init but it also seems like it has a long way to go. If anything there needs to be more documentation on customizing runlevels with upstart.

So if upstart is here to stay at least give the option to customize runlevels because I (and many other users) like the text-only login. I personally feel that gdm is bloat.

[Adding a text only runlevel to Ubuntu 7.10]("http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html")
See the above link for this workaround. Its a pretty crazy hack that is very unnecessary when all users want is a simple text only runlevel. Upstart, if I'm not mistaken, is a project that was started by Canonical, therefore, they can (and SHOULD) fix it.

---

### Post by xebian on 2009-11-05
I could see equalizer coming very soon for Amarok.  :=)

---

### Post by Chrisn02 on 2009-11-06
Mostly happy with Ubuntu as it is excluding a few minor niggles.

What I'd like to see...
1. On running VICE (C64/+4/etc emulator) checking that the roms are available instead of just doing nothing.  Even if its just a pop up message with instructions.

2. Some indication of what to do after installing certain thing.  e.g. I tried to installed bugzilla for use at work but it appear to do nothing, just didn't know enough to continue with it.  

3. Ensuring that sound volumes are set to the same level there were before upgrade and not totally muted after clean install.

4. Inform user that some hardware has no driver available. 
 
5. The return of the old volume control or something like it.  

6. Ensure that there's no way any application can block another application from playing sound.  This happened to me last night on my netbook with VICE blocking flash audio, not investigated why yet.  Still using 9.10RC on it, upgrading soon.

7. I don't know if this is still the case but it use to be that when installing the nvidia driver from the website you had to fight ubuntu for control of which ones to use.  Probably my fault.  Long since given up trying to do this, now using a ppa which is almost always up to date.

8. Probably seen this already but if there is any way to match the these benchmarks ;)
[Fedora 12 vs. Ubuntu 9.10 Benchmarks on Phoronix]("http://www.phoronix.com/scan.php?page=article&item=fedora12_ubuntu910&num=2")

Thank you for all your hard work with Ubuntu so far and I look forward to testing Lucid in the near future.

---

### Post by k3lt01 on 2009-11-06
> **absolutezero1287 said:**
> sudo apt-get remove gnome-games

problem solved

When people refer to bloat they usually mean about processes that are constantly running. Some may say that Firefox is bloat because it uses more resources than another web browser. Games aren't really bloat when there are 1 TB HDD available.

However, lets say that there were only a few games installed by default. You would be happy. You would say, now THIS is a serious business OS. I don't need all those sundry amusements. However, when a more casual user installs it they say: where's solitaire, checkers, and all the games?

If you want more business software take a look at IBM's Lotus. If the games annoy you that much then simply remove them. Its not bloat if you can remove them so I really don't see what the complaining is about.

You missed the point entirely, it wasn't a complaint it was another way to look at things.

I already remove the games, most of the time I do a mini install and don't install them anyway butthink about it this way. Your an admin and you dont want to sudo apt-get remove gnome-games on 500 PCs yet you have to because there are so many of them. Furthermore you have to go and search around for Business Software so you can run your business. Sorry to say this but Ubuntu, which I personally prefer for everything I do except for dealing with my iPod, is not really Business oriented in its current format.

It is also not very educationally oriented either. Yes there is Edubuntu but its not easy to find if your new to Ubuntu. So Ubuntu needs to change a few things to be able to be taken seriously in the Open Market even though it is free. OSs like Windows and Mac are easily available with Windows having a Business variant, I honestly don't know what Mac has and I don't care either.

So instead of telling me I'm complaining, think a little differently and try to understand I am presenting a different POV. Being a Small Business owner, a School Teacher, and a Motor Mechanic, I get to see what others like me are wanting in an OS not something with superfluous extras that have to be removed of up to 200 machines and then more things added after that.

The major difference John and Jane Doe see between Windows and other OSs is because of marketing and the different variants that are available. Bug #1 will never be taken car of until Ubuntu is taken seriously as an option for mor than your average family PC.

In the case of IBM and Lotus, I never liked IBMs (Lenovo now) and never liked Lotus either. I'd prefer to use Novell with Windows running on top like most education systems in Australia already do, and run MYOB or some other propriety Business Software like AutoSoft than run Lotus.

---

### Post by RaptorJesus on 2009-11-06
I have a strong belief that Synaptic has become deprecated, and we should all join hands and make our own. Also a new GUI theme would be nice.

---

### Post by absolutezero1287 on 2009-11-06
> **k3lt01 said:**
> You missed the point entirely, it wasn't a complaint it was another way to look at things.

I already remove the games, most of the time I do a mini install and don't install them anyway butthink about it this way. Your an admin and you dont want to sudo apt-get remove gnome-games on 500 PCs yet you have to because there are so many of them. Furthermore you have to go and search around for Business Software so you can run your business. Sorry to say this but Ubuntu, which I personally prefer for everything I do except for dealing with my iPod, is not really Business oriented in its current format.

It is also not very educationally oriented either. Yes there is Edubuntu but its not easy to find if your new to Ubuntu. So Ubuntu needs to change a few things to be able to be taken seriously in the Open Market even though it is free. OSs like Windows and Mac are easily available with Windows having a Business variant, I honestly don't know what Mac has and I don't care either.

So instead of telling me I'm complaining, think a little differently and try to understand I am presenting a different POV. Being a Small Business owner, a School Teacher, and a Motor Mechanic, I get to see what others like me are wanting in an OS not something with superfluous extras that have to be removed of up to 200 machines and then more things added after that.

You could always use a program like apt-on-cd to only install the packages you want. I'm still not seeing how a few games disqualifies Ubuntu from being a serious business OS. I recommend Ubuntu to a lot of my clients (who are small business owners) and the ones that do switch are very satisfied despite the "superfluous extras" which don't take up that much extra space or system resources.

The fact is that there are solutions for your issue. You CAN make a custom Ubuntu install CD. There are lots of howtos.

---

### Post by absolutezero1287 on 2009-11-06
> **RaptorJesus said:**
> I have a strong belief that Synaptic has become deprecated, and we should all join hands and make our own. Also a new GUI theme would be nice.

What do you base your claims on?

---

### Post by ranch hand on 2009-11-06
I have always thought that folks that play solitaire on a computer really need to get a life.  And learn to shuffle.

That is a good use of technology, replace a 2.00 (or whatever they are now) deck of cards with several 100s of dollars worth of computer.

The only benefit here can only be to Dr.s that fix carpal tunnel.

---

### Post by k3lt01 on 2009-11-06
> **absolutezero1287 said:**
> The fact is that there are solutions for your issue. You CAN make a custom Ubuntu install CD. There are lots of howtos.I am very well aware of that, but as a Business owner looking for an alternative I may not want to use someone outside to do something like this for me and I may not have enough PC skills to do it either. It would make sense for a "Business Edition" to be available that can at least have the basics there and can be easily built upon by John and Jane Doe.

---

### Post by absolutezero1287 on 2009-11-06
> **ranch hand said:**
> I have always thought that folks that play solitaire on a computer really need to get a life.  And learn to shuffle.

That is a good use of technology, replace a 2.00 (or whatever they are now) deck of cards with several 100s of dollars worth of computer.

The only benefit here can only be to Dr.s that fix carpal tunnel.

You are obviously unaware of World of Warcraft which people actually become addicted to. What's wrong with playing solitaire on your coffee break?

---

### Post by absolutezero1287 on 2009-11-06
> **k3lt01 said:**
> I am very well aware of that, but as a Business owner looking for an alternative I may not want to use someone outside to do something like this for me and I may not have enough PC skills to do it either. It would make sense for a "Business Edition" to be available that can at least have the basics there and can be easily built upon by John and Jane Doe.

Then learn how to make a live CD and install more business-oriented software. Give back to the community. Remember that Ubuntu is provided to you free of charge with no strings attached. Canonical is a non-profit organization. Unless the devs see a need for an Ubuntu business edition it won't really happen. So give back to the community and start working on a prototype. GO GO GO!!!!

---

### Post by Merk42 on 2009-11-06
> **absolutezero1287 said:**
> I'm still not seeing how a few games disqualifies Ubuntu from being a serious business OS.

Nor I.
As far as I know, the Windows XP, Vista and 7 Professional versions still come with games.

---

### Post by absolutezero1287 on 2009-11-06
> **Merk42 said:**
> Nor I.
As far as I know, the Windows XP, Vista and 7 Professional versions still come with games.

Exactly. Windows Server is probably the only Windows that doesn't come with games. I think k3lt01's request is more of a personal thing. He doesn't like games on his machines. That's completely fine. However, making "distro-wide" changes based on "I don't like games" is a bit much.

If there were to ever be an Ubuntu business OS it would probably still have the same games but would come with more business-oriented software. It would probably be more secure by default. When I think of Ubuntu Business Edition the last thing that comes to mind is no games.

---

### Post by ranch hand on 2009-11-06
> **Merk42 said:**
> Nor I.
As far as I know, the Windows XP, Vista and 7 Professional versions still come with games.
Yup, they all have them.

It must be a "must have item".

They are easy to remove.

---

### Post by seeker5528 on 2009-11-06
> **k3lt01 said:**
> You missed the point entirely, it wasn't a complaint it was another way to look at things.

I already remove the games, most of the time I do a mini install and don't install them anyway butthink about it this way. Your an admin and you dont want to sudo apt-get remove gnome-games on 500 PCs yet you have to because there are so many of them. Furthermore you have to go and search around for Business Software so you can run your business. Sorry to say this but Ubuntu, which I personally prefer for everything I do except for dealing with my iPod, is not really Business oriented in its current format.

From the dpkg man page

```

  --get-selections [package-name-pattern...]
              Get  list of package selections, and write it to stdout. Without
              a pattern, non-installed packages (i.e. those  which  have  been
              previously purged) will not be shown.

       --set-selections
              Set  package  selections  using  file read from stdin. This file
              should be in the format '<package> <state>', where state is  one
              of  install,  hold,  deinstall or purge. Blank lines and comment
              lines beginning with '#' are also permitted.

       --clear-selections
              Set the requested state of every non-essential package to  dein&#8208;
              stall.    This   is  intended  to  be  used  immediately  before
              --set-selections, to deinstall any packages not in list given to
              --set-selections.

```

From the apt-get man page

```

dselect-upgrade
           dselect-upgrade is used in conjunction with the traditional Debian packaging front-end, dselect(8).
           dselect-upgrade follows the changes made by dselect(8) to the Status field of available packages, and performs
           the actions necessary to realize that state (for instance, the removal of old and the installation of new
           packages).

```

So on your first machine you remove the stuff you don't want, install the stuff you do, then do:

```
dpkg get-selections > selections.txt
```

Put the selections file on a thumbdrive or somewhere on your network you can access from your other machines.

On the other machines do:

```
dpkg clear-selections
dpkg set-selections < selections.txt
apt-get dselect-upgrade
```

Later, Seeker

---

### Post by k3lt01 on 2009-11-06
Seeker, I already now how to do that but choose instead to do a minimum install. So I only select what I want in the first place.

AbsoluteZero, my request is not a personal thing. It is something I hear about often. Business owners complaining of workers playing games during work time is a common thing.

> **absolutezero1287 said:**
> **You are obviously unaware of World of Warcraft which people actually become addicted to.** What's wrong with playing solitaire on your coffee break?My point exactly. When we are discussing a business environment playing a game during a coffee break is not a problem, downloading and installing WOW, or playing Solitaire outside of Coffee Breaks is plain wrong, and it happens alot.

Teachers with 30 kids on PCs cannot watch every kid all the time, especially when you are trying to assist a kid who is actually trying to get some legitimate work done for a major project. You turn around and if the kid isn't quick enough, or smart enough because all they do is play PC games, you then have to deal with them. These things in certain circumstances decrease productivity, nobody can deny that. The only link to this being personal is the fact I have had to deal with both these situations. I know many more people who feel the same way.

I also know how to make a custom LiveCD. However, I have seen people get on this forum before for something like this trying to get support and get bagged for their efforts. Maybe if Canonical and the Devs helped to legitimise this type of effort in some way it would happen.

---

### Post by seeker5528 on 2009-11-06
> **k3lt01 said:**
> Seeker, I already now how to do that but choose instead to do a minimum install. So I only select what I want in the first place.

It's about the same either way, just leave out the 'dpkg clear-selections' part.

I have not actually used this so I don't know the exact process, but if you are only worried about installing, Synaptic has the option  on the file menu to create a download script which could be run on same machine or a different machine to download the desired packages, burn the downloaded packages to a CD, DVD, or thumbdrive, then you could take the CD, DVD, or thumbdrive around to your other machines and use Synaptic to install the downloaded packages.

If you really want to keep it to the minimum then in Synaptic 'settings --> preferences --> general' uncheck the option to treat recommends as dependencies.

Later, Seeker

---

### Post by k3lt01 on 2009-11-06
Seeker, you are trying to teach me things I already know.

My point in this thread, "What improvements would you like to see in Lucid?" is that I think, yes from my own experience but also from people talking to me about theirs, is that a Business version would be a good idea. It could improve Ubuntu's circulation. It's obvious that a few of you don't think so but I do and that is what this thread is about.

Now I have people giving me pointers about how to do it for my own situation, which I already do anyway. Wouldn't it be nice for other businesses not to have to go through alot of rigmarole and still be able to have a viable Business alternative OS?

---

### Post by RaptorJesus on 2009-11-06
> **absolutezero1287 said:**
> What do you base your claims on?
The very large amount of trouble I had to go through when updating to 9.10.

---

### Post by absolutezero1287 on 2009-11-06
> **RaptorJesus said:**
> The very large amount of trouble I had to go through when updating to 9.10.

That doesn't necessarily indicate a fault with synaptic. Upgrading your entire system is much more complex than installing a few packages. It would be wiser to ask for smoother upgrades.

---

### Post by k3lt01 on 2009-11-07
> **absolutezero1287 said:**
> It would be wiser to ask for smoother upgrades.Wisdom is a wonderful thing. I only wish people who make statements such as this would at least try to understand a thread by its title. Not everyone has the time and/or ability you seem to have, instead of sprouting wisdom try understanding where others are coming from.

---

### Post by Ellipsis on 2009-11-07
Two things both revolve around software center:

1) Allow Software Center to install non-repository programs. Including sh etc. programs graphically. I know that Ubuntu stays away from supporting this path but it would be better to A) warn people about the non-repo software they are installing B) get rid of some of the frustration they may feel when trying to install such programs via command line. 

2) A sort of "collections" system for programs. Because Ubuntu at the base will try and should try to stay as small as possible but people may need additional functionality quickly, are not familiar with programs that run on Ubuntu and as a way to simplify the multi-distro system. 

Firstly such a system should include a "Ubuntu +" collection featuring things like the community themes package, additional wallpapers, programs that are "sorta expected" (video editing) etc. 

Secondly it should allow people to put together collections of programs and share them via a site. (They could create personal collections which would instantly install many of the programs they previously had on a new or additional install). 

Lastly such a system could be used by distributions based on Ubuntu to quickly/visibly install their additions/modifications on Ubuntu.

---

### Post by MacUntu on 2009-11-07
> **gotsanity said:**
> I figured this one out the other day along with the help of a couple of others on the forums. Howto is here: [http://ubuntuforums.org/showpost.php?p=8185993&postcount=9](http://ubuntuforums.org/showpost.php?p=8185993&postcount=9)

Thanks for the link, I'm already using something similar for WIN+Left and WIN+Right. The problem is that AeroSnap feels and looks professional whereas these workarounds don't (gaps, overlapping, problematic edge triggering, etc.).

---

### Post by Slug71 on 2009-11-07
> **absolutezero1287 said:**
> I'd just like to elaborate on this post.
I've noticed that with every version of Ubuntu that I've used that uninstalling certain things renders my system unusable. Why is it that removing one thing causes some insane chain reaction?

For example, removing certain packages related to evolution causes the ubuntu-desktop package to be removed. I personally don't use evolution at all. I should be able to remove it without making my system unstable.

I observed the bane of metapackages again when I tried to make a custom Ubuntu install using debootstrap and a chroot. I installed the intel driver for xorg and it made me install many other drivers that I don't need. Now, I know the drivers are small but the point is that I shouldn't have to install crap that I don't need for the sake of it being convenient. It should be easier for the end-user to install and remove what packages they want without breaking the system.


In retrospect, this is probably a kernel issue.

Yeh id definitely like to see improvement here too. You cant even remove gnome-icon-themes without a bunch of other stuff being removed with it. I have a install of crunchbang running the xfce DE and i tried removing a bunch of Gnome stuff(which shouldnt be needed) and customizing some of the programs installed and the amount of dependencies involved for both installing and removing is quite ridiculous. I broke the install and had to do a reinstall and the space used before format was more than any of the other 11 installs i have and they pretty much all have the same stuff installed.

---

### Post by absolutezero1287 on 2009-11-07
> **Slug71 said:**
> Yeh id definitely like to see improvement here too. You cant even remove gnome-icon-themes without a bunch of other stuff being removed with it. I have a install of crunchbang running the xfce DE and i tried removing a bunch of Gnome stuff(which shouldnt be needed) and customizing some of the programs installed and the amount of dependencies involved for both installing and removing is quite ridiculous. I broke the install and had to do a reinstall and the space used before format was more than any of the other 11 installs i have and they pretty much all have the same stuff installed.

I've broken two installs in the past when I tried to customize Ubuntu. The dependency hell users are put through is definitely a problem that needs to be addressed. As well as having a cli-only runlevel. These are both problems that can be fixed.

Also: when I said "in retrospect this is probably a kernel issue" I was referring to being able to recognize FreeBSD slices and partitions.

---

### Post by yaztromo on 2009-11-07
Samba browsing in thunar.

A network manager applet thats bug free. It's still a sod to use.

The death of pulseaudio.

---

### Post by seeker5528 on 2009-11-07
> **k3lt01 said:**
> My point in this thread, "What improvements would you like to see in Lucid?" is that I think, yes from my own experience but also from people talking to me about theirs, is that a Business version would be a good idea. It could improve Ubuntu's circulation. It's obvious that a few of you don't think so but I do and that is what this thread is about.

The problem with these 'everybody chime in' threads is it is sometimes hard to follow a sub string of messages within the larger thread.

The main thrust of this sub topic seemed to be addition and removal of things and doing that for multiple machines in a workplace.

The Ubuntu desktop is a fairly basic set of things, and from that perspective I don't hold to the view that there should be anything different for home versus business. The basics are the same for both cases, good networking, IM, Email, good basic audio and video capabilities and an office suite and backup capabilities. In some businesses admins want some control over what the employees can or can't do on the computer. At home, some parents want some control over what the kids can or can't do on the computer.

If you have more than a handful of machines, then what is or isn't included in the installation seems like a pretty marginal concern compared to the question of how you are going to roll out the installation to those machines. 

Later, Seeker

---

### Post by munky99999 on 2009-11-07
My personal big wish for ubuntu would be an actual working domain - active directory - group policy mechanism.

Currently sure you can join a domain to share login details and such... but that's a small factor. Group policy and the numerous other tools that are part of active directory is what really makes it work.


Another feature I would like to see is a power user customization installation. Give us the power to customize what packages we want installed.

---

### Post by Jordanwb on 2009-11-07
> **munky99999 said:**
> Give us the power to customize what packages we want installed.

I forsee a "Go install Gentoo" post coming up.

I remember what it was I wanted to add. The Update manager. I don't know if it's like this in Karmic but on Jaunty it opens about 5 minutes after booting, telling you there's updates. It proceeds to do this every few minutes till you install the update(s). I am aware that you can disable that (which I have done), but now I'm not notified at all. No taskbar icon or something. If there were any updates I like it to say "There are updates available" using a little icon in the notification bar and shut up and leave me alone. Perhaps there is an alternate update-manager?

---

### Post by munky99999 on 2009-11-07
> **Jordanwb said:**
> I forsee a "Go install Gentoo" post coming up.

No that's usually me who posts that. Hell my name/trip on /g/ is Install!the3gentoo

Seriously though. Why not have this option in ubuntu also. It's a powerful and useful feature.

---

### Post by Merk42 on 2009-11-08
> **Jordanwb said:**
> I forsee a "Go install Gentoo" post coming up.

I remember what it was I wanted to add. The Update manager. I don't know if it's like this in Karmic but on Jaunty it opens about 5 minutes after booting, telling you there's updates. It proceeds to do this every few minutes till you install the update(s). I am aware that you can disable that (which I have done), but now I'm not notified at all. No taskbar icon or something. If there were any updates I like it to say "There are updates available" using a little icon in the notification bar and shut up and leave me alone. Perhaps there is an alternate update-manager?
While I understand your idea, I'm just curious.  If there are updates, why don't you install them? Unless it's a kernel update you most likely won't have to restart.

---

### Post by castrojo on 2009-11-08
> **munky99999 said:**
> Another feature I would like to see is a power user customization installation. Give us the power to customize what packages we want installed.

Have you tried the expert mode installation? (I think it's F6 or something on boot)

---

### Post by jeb800e on 2009-11-08
Bring back the animal-based main wallpapers! :D

---

### Post by jeb800e on 2009-11-08
NETWORKING, also!

---

### Post by Jordanwb on 2009-11-08
> **Merk42 said:**
> While I understand your idea, I'm just curious.  If there are updates, why don't you install them? Unless it's a kernel update you most likely won't have to restart.

I do install them, but not when I'm doing something else. Unless they're super critical updates then they can wait an hour or two, and so can the update manager. My point is is that the update manager is a pain in the *** and keeps telling me what I already have been told: that there's updates available.

> **jeb800e said:**
> NETWORKING, also!

Um, huh? Plus, there's an edit button.

---

### Post by woodbj on 2009-11-09
> **jeb800e said:**
> Bring back the animal-based main wallpapers! :D

+1, I loved the old wallpapers especially Hardy's one

---

### Post by nanog on 2009-11-09
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

no meta packages

---

### Post by Jordanwb on 2009-11-09
> **nanog said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

no meta packages

Care to explain? Personally I'd like to see better naming of metapackages. For example: "xserver-xorg" and "xserver-xorg-core", they both install the same packages. The later should be removed and the former should be simply "xorg".

---

### Post by nanog on 2009-11-09
+1 on dumping evolution and adding tb3. 

evolution does a terrible job at handling imap  -- every release i give evolution another spin only to purge it in *bangs head on wall* frustration.  i also have rendering problems with embedded html in evolution -- especially macmail and entourage. tb3 (especially the dailies) is a vast improvement from buggy linux tb2. the new search and tab features are invaluable. i may finally be able to get rid of google desktop search which is my current email indexer...

i also think that ubuntu should bite the bullet and seriously fund wine.  while i use open office for all *my* run of the mill stuff, it completely fails when i am collaboratively editing docs with ms office users. there have been incredible regressions in compatibility filters. imo, the ms office 2007 open office document conversion filter is superior to the open office ms office filter. and that is seriously ironic...

---

### Post by nanog on 2009-11-09
sorry i was replying to the user who wanted an advanced install option. but i am definitely anti-meta package. in my experience they limit choice by making it difficult to remove default applications without causing problems in future upgrades. i think they also cause some developers to just assume that ceratain application will be installed (e.g. evolution and gnome-do plugins dependency). i remove empathy, evolution, all games, tomboy, pidgin, and default firefox for all my ubuntu installs. i used to remove open-office and totem too but i've been very happy with recent ubuntu builds.

---

### Post by seeker5528 on 2009-11-09
> **Jordanwb said:**
> Care to explain? Personally I'd like to see better naming of metapackages. For example: "xserver-xorg" and "xserver-xorg-core", they both install the same packages. The later should be removed and the former should be simply "xorg".

Xserver-xorg-core is not a metapackage, it is the minimal amount of xserver stuff, then you still have to install the xserver-xorg-input-* and xserver-xorg-video-* packages you need for the input and video hardware you have. 

Xserver-xorg is not a metapackage, but I think not required to have a functional Xorg environment either, it includes dexconf, some hal policy stuff and pulls in almost all of the xserver-xorg-input-* and xserver-xorg-video-* packages by depending on the xserver-xorg-*-all metapackages for each of these.

There *is* a metapackage that is simply call "xorg", which typically would be what you want to select to pull in all the packages necessary to provide a working Xorg environment on a single machine. The server stuff only only provides what you need to connect to, show, and control what is running on the client. The client stuff only provides the environment for running the programs. You need both to have a fully functioning X environment on a single machine.

Any better examples of metapackages you have a problem with? :p

Later, Seeker

---

### Post by Jordanwb on 2009-11-09
> **seeker5528 said:**
> Xserver-xorg-core is not a metapackage, it is the minimal amount of xserver stuff, then you still have to install the xserver-xorg-input-* and xserver-xorg-video-* packages you need for the input and video hardware you have.

When I ran "apt-get install xserver-xorg-core" it wanted to install a bunch of video drivers. It wanted to install 66 packages, installing xserver-xorg wanted to install the same 66 packages.

But anyways. :-)

---

### Post by sfreed on 2009-11-09
> **nanog said:**
> +1 on dumping evolution and adding tb3. 

i also think that ubuntu should bite the bullet and seriously fund wine.  while i use open office for all *my* run of the mill stuff, it completely fails when i am collaboratively editing docs with ms office users. there have been incredible regressions in compatibility filters. imo, the ms office 2007 open office document conversion filter is superior to the open office ms office filter. and that is seriously ironic...

Nothing ironic about it at all. MS has the complete ODF specification to work from. OO.o on the other hand, has to work from their analysis of the closed MS Office binary formats. A lot of guess work there.


--
steve.

---

### Post by williejones on 2009-11-09
Ath9k working.

---

### Post by zekopeko on 2009-11-10
> **sfreed said:**
> Nothing ironic about it at all. MS has the complete ODF specification to work from. OO.o on the other hand, has to work from their analysis of the closed MS Office binary formats. A lot of guess work there.


--
steve.

Wrong. MS Office specs are open. Including OOXML and the old binary formats.

---

### Post by lykwydchykyn on 2009-11-10
> **zekopeko said:**
> Wrong. MS Office specs are open. Including OOXML and the old binary formats.

Of course, this glosses over the fact that MS office specs have only been open for about a year, whereas ODF was developed in the open and has been completed since 2005.  Yet, ironically, OOo has had some level of support for MSO documents since it first appeared, while MSO has only just gotten around to supporting ODF.

---

### Post by zekopeko on 2009-11-10
> **lykwydchykyn said:**
> Of course, this glosses over the fact that MS office specs have only been open for about a year, whereas ODF was developed in the open and has been completed since 2005.  Yet, ironically, OOo has had some level of support for MSO documents since it first appeared, while MSO has only just gotten around to supporting ODF.

I'm guessing that is because OOXML is a rather complete spec compared to ODF (AFAIK this was true at least a year ago).
I heard that the MS Office ODF plugin isn't playing nicely with document presentation. Would love to have MS and Sun work together on this.

---

### Post by slumbergod on 2009-11-10
Agreed totally. FIX THE BUGS before it is released. Like it or not Ubuntu has kind of become the distro everyone looks at when they think about Linux. But it is being released before the majority of bugs are released. The number of issues after the latest release certainly wasn't a good thing for linux in general.

---

### Post by lykwydchykyn on 2009-11-10
> **zekopeko said:**
> I'm guessing that is because OOXML is a rather complete spec compared to ODF (AFAIK this was true at least a year ago).
I heard that the MS Office ODF plugin isn't playing nicely with document presentation. Would love to have MS and Sun work together on this.

I wasn't even referring to OOXML, but the older binary formats, which have only recently been opened by order of the EU antitrust authorities.  

Frankly I don't think we'll ever have office programs from different authors where each perfectly renders documents created or edited in the other program.  Even with perfectly open specs like HTML and CSS, we can't get web browsers to render pages 100% correctly -- and that's strictly viewing. 

The problem is worse when you're editing and creating documents, and even worse when you're operating with software that originated with creating closed binary formats (true of both OOo and MSO).

---

### Post by irishbreakfast on 2009-11-10
Software Centre and Packet Manager

It would help new users if both of these included clear information such as 1) how to start the app via the menu 2) how to start the app via the cli 3) how to read the man pages 4) link to the app's website

---

### Post by jeb800e on 2009-11-11
A shortcut to Forcequit - both a hotkey on the keyboard and in the top panel!

---

### Post by jeb800e on 2009-11-11
Even better wireless support - PCI AND USB!

---

### Post by seeker5528 on 2009-11-11
> **Jordanwb said:**
> When I ran "apt-get install xserver-xorg-core" it wanted to install a bunch of video drivers. It wanted to install 66 packages, installing xserver-xorg wanted to install the same 66 packages.

From these lists of depends/recommends there is no obvious reason that should be the case:

xserver-xorg

> Depends: xserver-xorg-core (>= 2:1.5.99.901), xserver-xorg-video-all | xserver-xorg-video-5, xserver-xorg-input-all | xserver-xorg-input-4, xserver-xorg-input-evdev, hal (>= 0.5.12~git20090406), console-setup (>= 1.29) | console-setup-mini (>= 1.29), libc6 (>= 2.7), xkb-data (>= 1.4), x11-xkb-utils
Recommends: libgl1-mesa-dri, udev


xserver-xorg-core

> Depends: xserver-common (>> 7), libc6 (>= 2.7), libdbus-1-3 (>= 1.0.2), libdrm2 (>= 2.3.1), libfontenc1, libgcc1 (>= 1:4.1.1), libgcrypt11 (>= 1.4.2), libhal1 (>= 0.5.8.1), libpciaccess0, libpixman-1-0 (>= 0.13.2), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9), xserver-xorg
Recommends: xkb-data, libgl1-mesa-dri (>= 7.1~rc1)

So that is not a package/metapackage issue. Could be something in the pile of packages that get pulled in that specifically recommends the xserver-xorg-video-all in which case opting not to treat the recommends as dependencies would stop it, or somethig has a dependency like:

```
xserver-xorg-video-all | xserver-xorg-video-5
```

In which case if you don't already have something that provides xserver-xorg-video-5 and have not specifically selected something that provides xserver-xorg-video-5 then xserver-xorg-video-all would be installed by default, otherwise the installation would have to fail with the indication that there are multiple packages that provide xserver-xorg-video-5 and you have to choose one, which can be preferred, but I think not so much in this case. The xserver-xorg has this type of dependency so theoreticall if you specify the input and video packages you want then the xserver-xorg-*-all packages should not get pulled in, but there may be other variables depending on what else you have installed or selected for installation. 

When using apt front ends where you go through the list of available packages and individually mark packages for installation, the order you choose them in does make a difference. When using front ends where you specify packages for installation on the command line, the order shouldn't make a difference, but which ones you specify and which ones you let get pulled in automatically does.

Later, Seeker

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
I'll show my noobishness, but how about resurrecting the screens and graphics tool, or something like it? I spent 2 days trying every command I could find to correctly configure the screen resolution on my legacy machine, and everything either failed to create a change or else broke the xserver. 
The low system requirements combined with the cost (no more than the cost of a CD) drives many people to put Ubuntu on older machines. This legacy equipment appears (from the number of posts on the forum) to not be auto detected properly. As such, I'd like to see an easy to use program that spits out a working config file and backs up the present one automatically. 
The tool should be in the administration menu, require admin authentication, and could be hidden by default the way it was in Hardy.
As much as I'd like to see the default setup look more modern, and networking to be a little easier, a lot of people won't get past a 640x480(yes, I had that low of a resolution with "auto-detect") or 800x600 that can't just be easily changed in the display dialog.

---

### Post by Krause on 2009-11-12
I would like to see advanced options added to the Network Manager program. Right now If you want to do any kind of teaming what so ever you need to uninstall it and configure it manually.

It needs to be updated anyways to fix the pretty large hanging issues people are having with it over the version in Jaunty.

---

### Post by natrixgli on 2009-11-13
[LIST]
[*]Support for remote folders in Firefox's browse dialog
[*]Ability to dismiss notifications
[*]Ditch Empathy and go back to Pidgin
[*]Include OpenOffice.org Base by default
[/LIST]

---

### Post by jeb800e on 2009-11-14
The ability to get your free 2 GB of storage in the Ubuntu One cloud without signing up with a Launchpad account... to have it working from the moment Ubuntu starts up.

---

### Post by Digikid on 2009-11-14
Out of the box support for Ntrig and wacom Multitouch Tablets/Laptops ( HP Touchsmart Series )

---

### Post by falconindy on 2009-11-14
Fewer meaningless dependencies. I think it's ridiculous that you can't remove, for example, touchscreen utilties without removing the entire ubuntu-desktop package and about 15 other things.

---

### Post by DeMus on 2009-11-15
Re-install all the good things from Jaunty (and Hardy) which have been taken away in Karmic:
[LIST=1]
[*]Grub 1 instead of the dreadful Grub2
[*]Volume control in the pulldown menu when clicking on the loudspeaker icon in the upper panel
[*]Preferences in the pulldown menu when right-clicking on the Shutdown button in the upper panel
[*]Reading of sensors and using fancontrol to control fans and thus the temperature in the computer
[/LIST]

Then:
[LIST=1]
[*]Don't install Compiz automatically when installing the OS. If people want to destroy their computer let them do it by installing it themselves
[*]Remove Evolution from the standard install
[*]Better (easier) way to install (new) hardware drivers (nVidia, Ati,for example) so a reboot does not end in the command line
[*]Test Lucid intensively before releasing it. I've got a strong feeling this did not happen with Karmic, so I am back to Jaunty.
[/LIST]

---

### Post by Digikid on 2009-11-15
> Don't install Compiz automatically when installing the OS. If people want to destroy their computer let them do it by installing it themselves

What nonsense.  State your proof of this.

---

### Post by DeMus on 2009-11-15
> **Digikid said:**
> What nonsense.  State your proof of this.

Just read the forums. When people have an unstable system, Compiz is always involved. When they disable it the problems are gone. I experienced it myself and un-install it completely (?) when installing Ubuntu.
This should not be a part of the OS when installed. When you want it, install it yourself, but don't let those who want a stable system be stuck with it.

---

### Post by k3lt01 on 2009-11-15
> **Digikid said:**
> What nonsense.  State your proof of this.Google Earth won't work with it and as a Geography teacher Google Earth is an invaluable resource.

---

### Post by woodbj on 2009-11-15
> **DeMus said:**
> Re-install all the good things from Jaunty (and Hardy) which have been taken away in Karmic:
[LIST=1]
[*]Grub 1 instead of the dreadful Grub2
[/LIST]

Then:
[LIST=1]
[*]Remove Evolution from the standard install
[*]Better (easier) way to install (new) hardware drivers (nVidia, Ati,for example) so a reboot does not end in the command line
[/LIST]

*Grub2 I have found that it is much better than Grub1 (even though it is still under development)
*Would like to see evolution removed in favour of Thunderbird
*I have install many graphic drivers via Jockey and it has never ended up having manually configure anything in command line

---

### Post by gnomeuser on 2009-11-15
> **k3lt01 said:**
> Google Earth won't work with it and as a Geography teacher Google Earth is an invaluable resource.

It should work fine provided your driver supports DRI2. 

Though I do agree that turning on compiz by default was premature and also a decision that forced Ubuntu to ship proprietary drivers which cause a lot of related and unrelated problems including opening users to security and latency problems.

---

### Post by zika on 2009-11-15
> **gnomeuser said:**
> It should work fine provided your driver supports DRI2. 

Though I do agree that turning on compiz by default was premature and also a decision that forced Ubuntu to ship proprietary drivers which cause a lot of related and unrelated problems including opening users to security and latency problems.I'm not sure that compiz is turned on by default, at least in my case, I did not encounter it turned on by default on many of my installations. Not upgrades, clean installations. (ATI card). It is installed by default but not turned on.

---

### Post by k3lt01 on 2009-11-15
> **gnomeuser said:**
> It should work fine provided your driver supports DRI2.It doesn't work at all, screen flickers, cannot make anything in GE work with it, so uninstall it and leave MetaCity and Google Earth works a treat. Uninstalling it also helps to create a cleaner system which is a plus for me.

I can see how some would want it but I think it shows another case where Ubuntu needs to consider giving the end user some basic options during the install phase.

---

### Post by woodbj on 2009-11-15
> **k3lt01 said:**
> 
I can see how some would want it but I think it shows another case where Ubuntu needs to consider **giving the end user some basic options during the install phase.**

+1 on that

---

### Post by gnomeuser on 2009-11-15
> **zika said:**
> I'm not sure that compiz is turned on by default, at least in my case, I did not encounter it turned on by default on many of my installations. Not upgrades, clean installations. (ATI card). It is installed by default but not turned on.

Compiz is enabled by default on any setup that supports it. E.g. my netbook with an intel chip has it, my desktop (the wonderful Acer Aspire Revo r3610) has it enabled provided the nvidia driver is installed.

---

### Post by DeMus on 2009-11-15
> **k3lt01 said:**
> It doesn't work at all, screen flickers, cannot make anything in GE work with it, so uninstall it and leave MetaCity and Google Earth works a treat. Uninstalling it also helps to create a cleaner system which is a plus for me.

I can see how some would want it but I think it shows another case where Ubuntu needs to consider giving the end user some basic options during the install phase.

+1
If people want it, let them install it, but don't install and enable it by default. It just makes the whole system unstable, programs don't want to run well on it (like GE). Is this what Ubuntu wants: an unstable system? Can not imagine it.

@woodbj:
> *Grub2 I have found that it is much better than Grub1 (even though it is still under development)
What is so great about Grub? It's something you don't even want to see. When I put on my computer I want to see the desktop come alive asap. All these BIOS texts, the Grub menu, the splash screen: skip it. Put the desktop on screen and let's use the computer.

---

### Post by ranch hand on 2009-11-15
> **gnomeuser said:**
> Compiz is enabled by default on any setup that supports it. E.g. my netbook with an intel chip has it, my desktop (the wonderful Acer Aspire Revo r3610) has it enabled provided the nvidia driver is installed.
Well, that sucks.  I am VERY glad that it is not supported by my box.  Can't see the point, at all, of that crap.

---

### Post by zekopeko on 2009-11-15
> **k3lt01 said:**
> It doesn't work at all, screen flickers, cannot make anything in GE work with it, so uninstall it and leave MetaCity and Google Earth works a treat. Uninstalling it also helps to create a cleaner system which is a plus for me.

I can see how some would want it but I think it shows another case where Ubuntu needs to consider giving the end user some basic options during the install phase.

The more options you give the more code you have to support.
Plus, the installer should be minimal. If you want to fiddle with your system do it post install. Or install another distro that offers customization in the install phase.

---

### Post by tiggsy on 2009-11-15
1. Ability to print to a lexmark (worked in hardy, won't now)

2. Ability to burn disks (worked in hardy, won't now)

3. MOST IMPORTANT: Being secure in the knowledge that something you spent hours getting to work in a previous release will stay fixed when you upgrade (eg, printer, also sound, which I had to spend an hour or so AGAIN to get working)

---

### Post by k3lt01 on 2009-11-15
> **zekopeko said:**
> The more options you give the more code you have to support.I am very well aware of that.
> **zekopeko said:**
> Plus, the installer should be minimal.There is a minimum installer available and I use it to so that I have only what I want to have but not everyone has that luxury.
> **zekopeko said:**
> If you want to fiddle with your system do it post install. Or install another distro that offers customization in the install phase. This is one of the reasons I got into Linux but I'm not going to pay to use RedHat which is the distro I first come across and is still seen by many as the distro of choice for the serious user.

---

### Post by zekopeko on 2009-11-15
> **k3lt01 said:**
> There is a minimum installer available and I use it to so that I have only what I want to have but not everyone has that luxury.

I was talking about the graphical installer not the command line/ncurses one.


> This is one of the reasons I got into Linux but I'm not going to pay to use RedHat which is the distro I first come across and is still seen by many as the distro of choice for the serious user.

Redhat is for enterprise deployment. They don't target consumer desktop. If you want Redhat you can use CentOS as a free replacement.
Your whole argument is moot since there are other distros that fit your demands. Trying to make Ubuntu into Arch or Gentoo isn't going to work since Ubuntu isn't targeting you.

---

### Post by woodbj on 2009-11-15
> **DeMus said:**
> 
@woodbj:

What is so great about Grub? It's something you don't even want to see. When I put on my computer I want to see the desktop come alive asap. All these BIOS texts, the Grub menu, the splash screen: skip it. Put the desktop on screen and let's use the computer.

Well considering at the moment I have 9 different distro's dual booting I need to "see" it, and the fact that grub2 makes it soo easy to add custom entries.. And will support theming in the future which some of the early themes/mock-ups look great

---

### Post by ranch hand on 2009-11-15
I usually have more than the 10 OS' on board at this time.

I certainly agree that grub2 is the cats meow.

---

### Post by bluelamp999 on 2009-11-15
Karmic is, for me, fantastic. The best yet...

However, please please please upwards and onwards for the open source ATI graphics driver is my main wish...

---

### Post by k3lt01 on 2009-11-16
> **zekopeko said:**
> Redhat is for enterprise deployment. They don't target consumer desktop. If you want Redhat you can use CentOS as a free replacement.Fedora is the direct replacement if my memory is correct. RedHat use to be a consumer desktop system, obviously you missed that era.

> **zekopeko said:**
> Your whole argument is moot since there are other distros that fit your demands. Trying to make Ubuntu into Arch or Gentoo isn't going to work since Ubuntu isn't targeting you.I'll advise you to remember your manners, don't go telling me what to use or what targets me and what doesn't target me.

This thread is a WISH LIST thread, other have already stated they agree with me yet you haven't singled them out for that, no one has demanded anything yet a small group of people like yourself keep making yourselves out like your bigger than everyone else.

If you don't like what we wish for then so be it but don't be rude and high and mighty about it.

---

### Post by drumour on 2009-11-16
[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

+1 for this
+1 for bug fixing

I have 20+years in the business dealing with end users in the SoHo, Corp and Academic sectors, working with newbies and pro's, rich and poor. I strongly believe these should be the focus of Lucid especially as it has LTS status and these will have a daily impact on every user and every other feature mentioned in this long thread.

---

### Post by zekopeko on 2009-11-16
> **k3lt01 said:**
> Fedora is the direct replacement if my memory is correct. RedHat use to be a consumer desktop system, obviously you missed that era.

And your memory isn't correct.
[http://en.wikipedia.org/wiki/CentOS](http://en.wikipedia.org/wiki/CentOS)

Fedora is more like RedHat's playground to see how is the next RedHat Enterprise Desktop going to shape up. That's why they push bleeding edge in it.

> I'll advise you to remember your manners, don't go telling me what to use or what targets me and what doesn't target me.

This thread is a WISH LIST thread, other have already stated they agree with me yet you haven't singled them out for that, no one has demanded anything yet a small group of people like yourself keep making yourselves out like your bigger than everyone else.

If you don't like what we wish for then so be it but don't be rude and high and mighty about it.

Didn't mean to ruffle your feathers. I was merely correcting you. And wishes expressed here should be implementable in the Lucid time-frame. That is the point of this thread. Brainstorm is for the long term ones(or at least should be).

---

### Post by TDK800 on 2009-11-16
Inclusion of Gnome Commander twin-panel file manager.


Apps below are all I use to do everyday tasks on Ubuntu and only Gnome Commander and Skype are not included in default install, Skype because of being closed source, but why not Gnome Commander?:

Firefox, Empathy, Terminal, Gnome Commander, VLC Player, Skype.

---

### Post by Starks on 2009-11-16
> **drumour said:**
> [https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)
Wouldn't zsync be more ideal for this?

---

### Post by DeMus on 2009-11-16
> **woodbj said:**
> *Grub2 I have found that it is much better than Grub1 (even though it is still under development)
*Would like to see evolution removed in favour of Thunderbird
*I have install many graphic drivers via Jockey and it has never ended up having manually configure anything in command line

What is so much better about Grub2 compared to Grub1? What is it doing better? Choose the OS you want to boot? Grub1 does an excellent job there and isn't that all it is supposed to do?

I have a raid system in my PC. Grub can not reside inside a Raid. So, in Jaunty with Grub1, I made a separate partition for /boot, thus keeping it outside the two Raids for / and /home.
With Grub2 files are everywhere, /boot, /etc and God knows where else. Do I have to keep all these folders in separate partitions outside the Raid? Meaning no Raid at all? No thank you.

---

### Post by Starks on 2009-11-16
Meh. I've never had any problems with grub2.

---

### Post by doas777 on 2009-11-16
better samba integration, both for system and user-space sharing (at the same time, on the same machine). ACL interface for more complex permission sets (> 1 groups).

stable ttys on my laptop.

---

### Post by lykwydchykyn on 2009-11-16
> **DeMus said:**
> What is so much better about Grub2 compared to Grub1? What is it doing better? Choose the OS you want to boot? Grub1 does an excellent job there and isn't that all it is supposed to do?


Apparently, Grub 1 was a mess to maintain.  See [http://www.gnu.org/software/grub/grub-2-faq.en.html](http://www.gnu.org/software/grub/grub-2-faq.en.html)
 
> 
I have a raid system in my PC. Grub can not reside inside a Raid. So, in Jaunty with Grub1, I made a separate partition for /boot, thus keeping it outside the two Raids for / and /home.
With Grub2 files are everywhere, /boot, /etc and God knows where else. Do I have to keep all these folders in separate partitions outside the Raid? Meaning no Raid at all? No thank you.

According to documentation (haven't tried it myself) Grub2 won't require you to keep a separate /boot.  It supports RAID and LVM:

[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

---

### Post by b3n87 on 2009-11-16
> **gnomeuser said:**
> 

Removal of Ubuntu One from the default install or a release of the server side code - sorry I still don't trust my data to source I can't see and I do expect better from a Linux company.



So you have a problem with people handling your data, but your OK with using Google products that track you?

---

### Post by k3lt01 on 2009-11-17
> **zekopeko said:**
> And your memory isn't correct.
[http://en.wikipedia.org/wiki/CentOS](http://en.wikipedia.org/wiki/CentOS) I beg to differ with you, Two can play the [wikipedia]("http://en.wikipedia.org/wiki/Fedora_(operating_system)") game. The first paragraph clearly agrees with my thoughts.

> **wikipedia]Fedora (pronounced /f&#601 said:**
> 

[QUOTE=zekopeko;8329682]Didn't mean to ruffle your feathers. I was merely correcting you. And wishes expressed here should be implementable in the Lucid time-frame. That is the point of this thread. Brainstorm is for the long term ones(or at least should be).It's not a matter of ruffling feathers it's a matter of showing respect, something which is sadly lacking of late.

I don't see how any of the wishes expressed here are not implementable by Lucid, RedHat did it 10 years ago. If Canonical is listening to Ubuntu users there should be some level of advance planning.

---

### Post by bluenova on 2009-11-17
Regression to a magical time when the user had control over GDM.

---

### Post by gnomeuser on 2009-11-17
> **k3lt01 said:**
> Fedora is the direct replacement if my memory is correct. RedHat use to be a consumer desktop system, obviously you missed that era.

As a former Fedora developer let me say this. 

Fedora is not the direct replacement for any previous Red Hat product. There isn't really something to pick up from the old Red Hat Linux products of the past and Fedora certainly isn't billed as such. 

CentOS is a recompile of the Red Hat Enterprise Linux product and is what is recommended as the replacement for RHEL in situations where you cannot afford or do not need the RHEL support contract.

As for what Fedora is in all of this, it is a rapidly moving project with a focus on new technology. There is a predictable release schedule and limited life time for every release. It is the base for amongst other things Red Hats enterprise products but also things like the OLPC OS. 

Fedora isn't really suitable for a consumer desktop as that would require actual support (Fedora is merely maintained, not supported and nobody sells support for Fedora in any official capacity). One could build a consumer desktop based on it but it would rapidly need to start looking like RHEL/CentOS for any successful deployment.

RHEL's release come out every 2 years or so, a release is supported for 7 years (optionally one can buy support for special deployments up to 10 years). In the first half of a releases lifetime you get technology updates (new drivers, new versions of software e.g.) issued as well as have new install cds made available (for those new setups that require the new support to even install). After that a release goes into maintance mode and only gets security updates.

---

### Post by k3lt01 on 2009-11-17
> **gnomeuser said:**
> As a former Fedora developer let me say this.As a very brief former RedHat user, not RHEL btw, Fedora was touted as its replacement. That is regardless of its so called "support" status. It was and still is RedHat's community maintained version. Fedora was allowed to use part of the RedHat logo (Fedora being the RedHat) yet CentOS has never been allowed to use anything but RedHat's code. I made no claims about support or enterprise usage.

I find it interesting that you have had your hands in so many baskets, you are clearly very good at your work, I bet some people wish you would answer their questions though.

> **b3n87 said:**
> So you have a problem with people handling your data, but your OK with using Google products that track you?

Now back to our regular programming.

---

### Post by ranch hand on 2009-11-17
I don't want anything fancy, I just want the option of turning off that DAMNED slide show during installation.

---

### Post by Merk42 on 2009-11-17
> **ranch hand said:**
> I don't want anything fancy, I just want the option of turning off that DAMNED slide show during installation.

Walk away;)

Seriously though, can't it just be minimized in a LiveCD situation?

---

### Post by lykwydchykyn on 2009-11-17
> **ranch hand said:**
> I don't want anything fancy, I just want the option of turning off that DAMNED slide show during installation.

There's always the alternate install.  I think it'd be right up your alley.  100% no-eye-candy guarantee.

---

### Post by LKjell on 2009-11-17
> **Merk42 said:**
> Walk away;)

Seriously though, can't it just be minimized in a LiveCD situation?
I think you can use ctrl + alt + d to minimise and not show it.

************************

Anyway a question to those who want to do drastic changes to Ubuntu. Have you ever thought of why you pick Ubuntu and not other distro that might have done what you already want for your Ultimate system? Like if you like have take controll of your system we have Gentoo and Arch which let you mess your system to the beyond. Just free software we have Fedora and Debian; and many others.

But you have your freedom to pick the one you like. That is one of the reason why there are so many different distribution. They target different audience. One may be perfect for one person while it may feel like crap to another. You can even create your own!

For all Ubuntu users we all have a common ground. And we should embrace us in it and develop together and not deviate from each other. Good ideas are to be shared.

---

### Post by ranch hand on 2009-11-17
> **lykwydchykyn said:**
> There's always the alternate install.  I think it'd be right up your alley.  100% no-eye-candy guarantee.
I really do not use the AltCD because the LiveCD is so handy to have for so many little things (partitioning and grub recovery for example.

Seeing the problems some folks have had with the LiveCD installation, I may have to try it again though.

The slide show doesn't even count as eye candy to me.  Once you have seen it you have seen it, so what.  Every time you are put through it again it just qualifies as a large irritant on your screen.

I installed 9.04 the other day to run the upgrade 9.04>9.10>10.04 and the installation progress bar is small and unintrusive and can be parked in the corner, marked "always on top" and you can do other things and keep an eye on it.

With the slide show it takes up a good 1/3 of the screen.  This just sucks.

---

### Post by issih on 2009-11-17
> **ranch hand said:**
> I really do not use the AltCD because the LiveCD is so handy to have for so many little things (partitioning and grub recovery for example.

Seeing the problems some folks have had with the LiveCD installation, I may have to try it again though.

The slide show doesn't even count as eye candy to me.  Once you have seen it you have seen it, so what.  Every time you are put through it again it just qualifies as a large irritant on your screen.

I installed 9.04 the other day to run the upgrade 9.04>9.10>10.04 and the installation progress bar is small and unintrusive and can be parked in the corner, marked "always on top" and you can do other things and keep an eye on it.

With the slide show it takes up a good 1/3 of the screen.  This just sucks.

The slide show does not exist for you though...It exists for people who are new to Ubuntu, to familiarise them with a few concepts that might help them get around in a slightly alien environment.

Why would you want to get rid of something you will only ever see anything of every 6 months or so, and which only appears during a period of time when your computer is busy installing the OS and needs precisely zero input from you? Just go away, make a cup of tea and watch some television for 30 minutes, or if even a fleeting glimpse will make you violently ill, and you live in an open plan loft where you can't shut the door on it...turn the monitor off!

It may be patronising and irritating for you...but once again it is not meant to turn you from highly experienced user to linux god, it is meant to help a confused and unsure newbie feel more comfortable with their system..

It is a fine addition to the installer, and is making some use of what was previously wasted time and space.

Now, if you install the OS a million times a week as part of a job and you for some reason continue to use the live cd to do something whilst the install is proceeding, I can understand the frustration somewhat, but that is hardly a typical scenario, and catering specifically for non-typical scenarios is idiotic.

All in all, the slide show should 100% stay.

P.S. An option to minimise or close it would be fine though - no problems there whatsoever..

---

### Post by tulchan on 2009-11-17
My Karmic was hanging - all procs stopped - no logging - nothing - at random times.

At each reboot, I was having to run an fsck manually because the system had to be hard booted.

Uninstalled Compiz - now the system isn't hanging.

Personally if it wasn't for the far better (faster) network printserver in Karmic, I would go back to Jaunty. 

My package db is corrput because the system froze when doing a regular update in Update Manager - now I can't get rid of some python packages or reinstall them.

If I knew how to (or there was an uninstall option for Karmic that I could find in less than an hour of web searching), I would get rid of Karmic.

---

### Post by ranch hand on 2009-11-17
> 
P.S. An option to minimise or close it would be fine though - no problems there whatsoever..

That is what I want.

I actually play with my box quite a bit, particularly a single drive external enclosure that I loan to people to try Linux on their box with.  I see the installation program quite a bit.

It could be that in testing we may see it quite a bit too, for one reason or an other.

I went from MSdos to 98.  The very first time that rediculous crap MS put on came up it irritated me.

When I went from MS to Ubuntu, I did not have the joy of a slide show.  I had been a member of these forums for about 3 weeks and had found most of the documentation.  Anyone coming in cold, with no knowledge, is not goiing to be helped by a slide show.

It may, very well, make them feel better.  This, of course, is a good thing as it may give them the incentive to not panic, slow down and work things out.

I just wantto be able to turn it off.

---

### Post by ST3ALTHPSYCH0 on 2009-11-18
Speaking of people who migrate from MS... how about a little more polish for the default theme? Just for giggles I popped in a two year old Knoppix disc that I found near the bottom of a spindle the other day.... I hate to say it, but it looks way more modern than the default Ubuntu setup. I realize that the sky is the limit for customization, but why does it have to look so mid 90's out of the box?

---

### Post by k3lt01 on 2009-11-18
> **LKjell said:**
> Anyway a question to those who want to do drastic changes to Ubuntu. Have you ever thought of why you pick Ubuntu and not other distro that might have done what you already want for your Ultimate system? Like if you like have take controll of your system we have Gentoo and Arch which let you mess your system to the beyond. Just free software we have Fedora and Debian; and many others.

But you have your freedom to pick the one you like. That is one of the reason why there are so many different distribution. They target different audience. One may be perfect for one person while it may feel like crap to another. You can even create your own!

For all Ubuntu users we all have a common ground. And we should embrace us in it and develop together and not deviate from each other. Good ideas are to be shared.Ubuntu is one of the few distros that works well on every machine I have. Fedora is crap on some while on others its ok. Ubuntu works the majority of the time and I like most of what it offers. Do you think thats a good enough reason to prefer it but also to want to help make it better?

---

### Post by grashdur on 2009-11-18
I think everything in Karmic Koala is wonderful except for sound. And that part really, really sucks (at least with my soundcard and computer).

So what I'd like most is a major, fundamental overhaul of the whole sound system so that Ubuntu can work well with Skype, and so that sound options are simple and easy to change around (such as switching a program's audio output to different devices on the fly).

---

### Post by KiLaHuRtZ on 2009-11-19
Don't need anything new, just fix all the problems the last three releases caused and I will be happy. :D

---

### Post by Slug71 on 2009-11-19
> **Slug71 said:**
> This,

Pulseaudio, which we now know is coming and

Plymouth and 

Packagekit as the backend to USC.

> **LKjell said:**
> Do not think we are going to use packagekit.

[https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend](https://blueprints.edge.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend) :p

---

### Post by Toadinator on 2009-11-19
> **gnomeuser said:**
> Removal of Ubuntu One from the default install or a release of the server side code - sorry I still don't trust my data to source I can't see and I do expect better from a Linux company.

Banshee as the new default mediaplayer.

No no no. First of all, Ubuntu One is a service provided by canonical to get some money out of this (more than usual). Is that so wrong? Releasing the code for it would of course be a great idea, but you're not forced to use it (Dropbox is a wonderful alternative if you like cross-platform syncing; not sure if the server's open source though).

Second and lastly, Banshee is bloated. The last thing Canonical wants to do is make Ubuntu unnecessarily bloated. I, like you, use(d) Banshee, and for a while I loved it, but it seemed rather slow/memory inefficient to me. So I tried out Rhythmbox (the latest release is great) and I love it! Does everything I need it to do and does it fast. Asking Banshee to replace Rhythmbox is like asking them to replace Firefox with Epiphany; it makes more sense to stick to what we're currently using.

---

### Post by gnomeuser on 2009-11-19
> **Toadinator said:**
> No no no. First of all, Ubuntu One is a service provided by canonical to get some money out of this (more than usual). Is that so wrong? Releasing the code for it would of course be a great idea, but you're not forced to use it (Dropbox is a wonderful alternative if you like cross-platform syncing; not sure if the server's open source though).


I have no problem with them making money, I really wish people would stop hiding behind this excuse. There is no reason they could not make money while also releasing the code. No average user is going to build his own U-one server just to get out of a 10$ a month expense and any competitor using the open code will have to contribute their changes back, they will also have to have the same support costs and challenges as Canonical have.  Even at that would you pick the original strong flavor or "new coke" where you couldn't count on the support coming from the actual developers? No I didn't think so. 

There is no reason why they couldn't make money with open source, other people do so, happily. 

There is however without a code release no telling what they do with your data, no assurance as to how they store it. You can't look at it to see if there are security issues. You can't fix it and extend it.. 

> 
Second and lastly, Banshee is bloated. The last thing Canonical wants to do is make Ubuntu unnecessarily bloated. I, like you, use(d) Banshee, and for a while I loved it, but it seemed rather slow/memory inefficient to me. So I tried out Rhythmbox (the latest release is great) and I love it! Does everything I need it to do and does it fast. Asking Banshee to replace Rhythmbox is like asking them to replace Firefox with Epiphany; it makes more sense to stick to what we're currently using.

Banshee uses less memory than rhythmbox for large collections by design. Even at that with a small collection at the default settings for both apps (hardly a fair comparison as they do not have the same support loaded by default but hey). 

[http://www2.apebox.org/wordpress/linux/113/](http://www2.apebox.org/wordpress/linux/113/)

Wow, 12 megs of memory more.. that is hardly obscene given the advantages it gains us such as proper library management

As for replacing Firefox with Epiphany that is hardly a fair comparison, to rb -> banshee. Banshee is more featureful, has a more active development community and is better designed underneath. This is sadly not the case for Epiphany, what it has going for it is being a native GNOME app and in the past I would have been a proponent of looking at it for replacement for this reason. Sadly a lack of interest from distributions amongst other things have caused development of Epiphany to slip into nothingness. 

A more fair comparison would be replacing firefox with chromium, a faster, more secure alternative - something I most certainly would advocate for serious consideration in the future.

---

### Post by BbICEP on 2009-11-20
> **gnomeuser said:**
> I have no problem with them making money, I really wish people would stop hiding behind this excuse. There is no reason they could not make money while also releasing the code. No average user is going to build his own U-one server just to get out of a 10$ a month expense and any competitor using the open code will have to contribute their changes back, they will also have to have the same support costs and challenges as Canonical have.  Even at that would you pick the original strong flavor or "new coke" where you couldn't count on the support coming from the actual developers? No I didn't think so. 

There is no reason why they couldn't make money with open source, other people do so, happily. 

There is however without a code release no telling what they do with your data, no assurance as to how they store it. You can't look at it to see if there are security issues. You can't fix it and extend it.. 



Banshee uses less memory than rhythmbox for large collections by design. Even at that with a small collection at the default settings for both apps (hardly a fair comparison as they do not have the same support loaded by default but hey). 

[http://www2.apebox.org/wordpress/linux/113/](http://www2.apebox.org/wordpress/linux/113/)

Wow, 12 megs of memory more.. that is hardly obscene given the advantages it gains us such as proper library management

As for replacing Firefox with Epiphany that is hardly a fair comparison, to rb -> banshee. Banshee is more featureful, has a more active development community and is better designed underneath. This is sadly not the case for Epiphany, what it has going for it is being a native GNOME app and in the past I would have been a proponent of looking at it for replacement for this reason. Sadly a lack of interest from distributions amongst other things have caused development of Epiphany to slip into nothingness. 

A more fair comparison would be replacing firefox with chromium, a faster, more secure alternative - something I most certainly would advocate for serious consideration in the future.
Outdated: my RB takes less memory with larger database (about 11 days) - 28Mb on 64-bit system. BTW, RB with 30-days long collection still eats less memory than banshee. And it launches much faster and its response is quicker. And yes, banshee has some vacuous features, but it's lack of most essential feature each music management software must have: realtime library watching. Banshee also has some very old and annoying bugs, like this one: [http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_2a1b9_e9406456_orig](http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_2a1b9_e9406456_orig) The dev insist it's my wrong tags. Actually, other players show this as one album. IMO, banshee is a toy of crazy C# phanatics. It's just stupid to switch to it, it would be the same mistake that have been done with pulseaudio, where gnome maintainers trusted to unskilled guy with fertile imagination.

---

### Post by longlegs on 2009-11-20
THIS IS A RANT! It would be nice if the bootloader (grub1) was made to work before coming out with a new one(grub2). It seems as if some of the ubuntu programmers (not just grubbers) have decided to work for ms in placing feature before function.*&^%$!~!!
I generally try ubuntu once a year, and this year looked like I might be able to switch from windows. No such luck. I've been working 3-5 hours an evening for 2 weeks now, trying to get Win2k/Ubuntu9.04 -9.10 to dual boot.
Have wiped MBR's and PBR's numerous times. Can make it boot only linux or only win but not both. Most of the how-to posts have built in failure modes.

I know that some bugs are more important than others, but the programmers involved with grub should realise that (for most potential new users) if it can't dual boot with win, the user won't switch. And if the progammers can't make grub1 work, WTH makes them think they can make grub2 work?
 BTW 
Get rid of that crap about hd0 being the first hd. This one single wrong headed idea probably causes more than 3/4 of the install failures. Use (for example) sdb3 for second (b)drive and third (3) partition.
Get rid of "error xx" messages and give some useful info. Instead of "error 15", say "File <filename> could not be found."
DOES ANYBODY HAVE A SET OF INSTRUCTIONS FOR DUAL BOOTING Win2k AND Ubuntu IN A SYSTEM WITH AN ORIGINAL SCSI DRIVE CONTAINING NT4, AN ADDED IDE WITH Win2k AND Win98SE, AND A SECOND SCSI CONTAINING Ubuntu9.10 WITHOUT RUINING THE MBR OF FIRST SCSI ??? Please try the instructions before pointing to them.
Oh, one other thing. Having the bootloader hidden behind an "Advanced" button and defaulting to no bootloader was really ... well u no wher his head was.
Any help appreciated. If this post moved, say where to? Thanks
H.M.Jones

---

### Post by VMC on 2009-11-20
> **longlegs said:**
> ...Get rid of "error xx" messages and give some useful info. Instead of "error 15", say "File <filename> could not be found."
DOES ANYBODY HAVE A SET OF INSTRUCTIONS FOR DUAL BOOTING Win2k AND Ubuntu IN A SYSTEM WITH AN ORIGINAL SCSI DRIVE CONTAINING NT4, AN ADDED IDE WITH Win2k AND Win98SE, AND A SECOND SCSI CONTAINING Ubuntu9.10 WITHOUT RUINING THE MBR OF FIRST SCSI ??? Please try the instructions before pointing to them.
Oh, one other thing. Having the bootloader hidden behind an "Advanced" button and defaulting to no bootloader was really ... well u no wher his head was.
Any help appreciated. If this post moved, say where to? Thanks
H.M.Jones

We really need a Boot-loader forum, separate from all the rest. This is the single most ask and troubled area of all.

 It surprises me most that the moderators haven't realized this yet?! It would save having to search all over tarnation to find someone with similar errors.

At least we need a sticky on this issue. We have one for Sound & Multimedia. We did have a sticky for a short wile during Karmic testing.

Maybe, and I hate to suggest this but, search for grub issues. 
I'm not being funny here - **We Need A Boot-loader forum or Sticky**.

---

### Post by Roasted on 2009-11-20
Dear Lucid Developers:

I would really, really like to have the next distribution release to actually support multiple hard drives, seeing as though Karmic cannot handle this task. Anything you can do in this regard would be appreciated beyond belief. Thank you for your hard work.

Your's Truly,
Roasted

---

### Post by Merk42 on 2009-11-20
> **Roasted said:**
> Dear Lucid Developers:

I would really, really like to have the next distribution release to actually support multiple hard drives, seeing as though Karmic cannot handle this task. Anything you can do in this regard would be appreciated beyond belief. Thank you for your hard work.

Your's Truly,
Roasted
 I personally have multiple hard drives, and I think others have SATA RAID set up fine.  What exactly are you talking about?

---

### Post by Gina on 2009-11-20
I have three independent drives in my P4 machine.  One IDE 250GB and two SATA 160GB.  On those I have a whole dose of operating systems including Windows XP.  Installing Karmic (9.10) using the Alternate CD and leaving boot loader (grub2) install at default - MBR of first drive (the IDE), it installed fine and detected ALL my OSs and they would ALL BOOT and work from the boot menu.  The Live CD refused to install the boot loader - anywhere!

Now I have installed Lucid using the daily live Alternate CD ISO and that did the same - all OK.

I'm now using grub2 on both AMD64 and P4 desktops.  Not tried yet on the >10yr old AMD.  Have problems with my laptop (one HD and 3 OSs - 2 U & XP) - installs but wont boot.

---

### Post by Noo 2 Ubuntoo on 2009-11-20
> **TrueTom said:**
> Fixing bugs while not breaking things that already worked would be a start...

Seconded, in fact, don't bother with further development, just make Karmic into an OS that "Just works" and rename it Lucid

---

### Post by DeMus on 2009-11-20
[LIST=1]
[*]Use Thunderbird as standard e-mail client and get rid of Evolution. Simply because, as I understand it, it is woven deep in the heart of Gnome. Just as IE is part of the Windows OS. Why does Linux (gnome in this case) imitate Windows?
[*]Get rid of Grub2. Let Karmic be the only OS in which the Ubuntu made this mistake of using it. Again this is an imitation of Windows. Windows used to have the boot.ini file, a simple text file, easy to be changed if necessary, now they have a system which is not so easy to configure. Same happened here with Grub. Why? Don't tell me Grub2 is much better. Grub1 boots my pc as it should, that's all I ask of it. I don't need a complicated menu on a shining background because I don't even want to see it. The computer has to boot and boot fast, without showing me the menu at all. So why waste so much time and effort on it?
[*]Loose Compiz in the standard installation. When people want to have it let them install it and ruin their computers, don't make those people who do not want to have Compiz do the same.
[*]Easier ways to connect computers together, using Samba, NFS, Remote desktop, etc.
[*]A stable Conky which does not crash all the time like the one which is in Jaunty.
[*]Easier and more functional way to install drivers, especially the graphic drivers. Just look in the forums to see how many times this subject comes up.
[*]Put back the things which are in Hardy and Jaunty, but were taken out or were hidden somewhere, in Karmic: Preferences of the loudspeaker, getting rid of the 60 seconds delay when shutting down, etc.
[*]A video-editing program which can stand the competition of let's say Adobe Premiere and Ulead's Media Studio Pro.
[*]Let the user choose from a giant list during installing the OS which programs (s)he wants to install and use. That way everyone can get what (s)he wants to have and is not being stuck with something which is never used.
[/LIST]
There is enough to be done. Since Lucid will be an LTS version, I think these things really should be a part of it to make Lucid the best Ubuntu ever, and that for a long time.

---

### Post by Gina on 2009-11-20
I'd like to see a Custom Install but also a Standard (or Normal, or Everything) install option.  That way new users can choose the Standard Install and get what we have now.  Those wanting a cut down version would have the option.  The Minimal-Install-CD (mini.iso) doesn't do this - it installs the system but downloads the apps you've ticked from the net.  What I mean is to have everything on the CD as now but optionally prevent installing the apps you don't want.  This applies particularly to CDs obtained by other means than downloaded as ISO files - the mini-iso covers the download method (well almost).

I wonder how much space such an extra option would take up on the CD.  I wouldn't have thought it was very much - just an installation script to read as installation progresses.

---

### Post by Gina on 2009-11-20
Addendum to above :- It would be impractical to have options for every app on the CD - there are dozens - but maybe in groups, such as Games.

---

### Post by Slug71 on 2009-11-20
> **DeMus said:**
> [LIST=1]
[*]Use Thunderbird as standard e-mail client and get rid of Evolution. Simply because, as I understand it, it is woven deep in the heart of Gnome. Just as IE is part of the Windows OS. Why does Linux (gnome in this case) imitate Windows?
[*]Get rid of Grub2. Let Karmic be the only OS in which the Ubuntu made this mistake of using it. Again this is an imitation of Windows. Windows used to have the boot.ini file, a simple text file, easy to be changed if necessary, now they have a system which is not so easy to configure. Same happened here with Grub. Why? Don't tell me Grub2 is much better. Grub1 boots my pc as it should, that's all I ask of it. I don't need a complicated menu on a shining background because I don't even want to see it. The computer has to boot and boot fast, without showing me the menu at all. So why waste so much time and effort on it?
[*]Loose Compiz in the standard installation. When people want to have it let them install it and ruin their computers, don't make those people who do not want to have Compiz do the same.
[*]Easier ways to connect computers together, using Samba, NFS, Remote desktop, etc.
[*]A stable Conky which does not crash all the time like the one which is in Jaunty.
[*]Easier and more functional way to install drivers, especially the graphic drivers. Just look in the forums to see how many times this subject comes up.
[*]Put back the things which are in Hardy and Jaunty, but were taken out or were hidden somewhere, in Karmic: Preferences of the loudspeaker, getting rid of the 60 seconds delay when shutting down, etc.
[*]A video-editing program which can stand the competition of let's say Adobe Premiere and Ulead's Media Studio Pro.
[*]Let the user choose from a giant list during installing the OS which programs (s)he wants to install and use. That way everyone can get what (s)he wants to have and is not being stuck with something which is never used.
[/LIST]
There is enough to be done. Since Lucid will be an LTS version, I think these things really should be a part of it to make Lucid the best Ubuntu ever, and that for a long time.

Its very unlikely that Compiz will get dropped.

Grub2 will NOT get dropped either. I run a multiboot machine with 12 OSs on and i can honestly tell you that Grub2 is better. Sure it is still rough around the edges but it is better. 
Fedora is using Grub2 for F-13 and my guess is that Mandriva and openSUSE among others will be using it too for their next release. I know Mint 8 will be.
Expect a lot of improvement by Lucid release.

---

### Post by seeker5528 on 2009-11-20
> **longlegs said:**
> THIS IS A RANT! It would be nice if the bootloader (grub1) was made to work before coming out with a new one(grub2).

It was the limitations and lack of flexibility that led the developers to rewrite grub from scratch.

> I know that some bugs are more important than others, but the programmers involved with grub should realise that (for most potential new users) if it can't dual boot with win, the user won't switch.

Granted it happens more than it should, but percentage wise I think it's not *that* huge of a problem.

> And if the progammers can't make grub1 work, WTH makes them think they can make grub2 work?

Because they have the experience from Grub 1 to look back on and not make some of the same mistakes again.

> Get rid of that crap about hd0 being the first hd. This one single wrong headed idea probably causes more than 3/4 of the install failures.

I would guess, of the people who have had installation failures, significantly less than half choose where to install grub. 

> Use (for example) sdb3 for second (b)drive and third (3) partition.
Get rid of "error xx" messages and give some useful info.

Your third drive, second parition might not be sdb3. Would have been better to use (hd2,3). For distributions that still represent some or all of the PATA drives as hda, hdb, etc... your second hard drive could be hdd, and your third drive sda if you also have SATA, but rather than change that now it should be up to the installer to indicate to the user that numbering starts at 0. Then there is the potential that people are installing grub from a different OS that using a completely different identifacation scheme. If you have SATA and/or PATA in addition to SCSI there is additional potential for things to be screwed if the installer recognizes the different subsystems in a different order than the installed system, then your SCSI drives may be viewed as the first and second drive during installation, but as the second and third drive by the installed system or vice versa. It's not grubs fault if the system map created at the time of installation, doesn't match the order of the drives in the actual installation.

> Oh, one other thing. Having the bootloader hidden behind an "Advanced" button and defaulting to no bootloader was really ... well u no wher his head was.

I have seen where you could choose not to install the boot loader, but I have not seen where that is the default. What version was this?????

Later, Seeker

---

### Post by DeMus on 2009-11-20
> **Slug71 said:**
> Its very unlikely that Compiz will get dropped.

Grub2 will NOT get dropped either. I run a multiboot machine with 12 OSs on and i can honestly tell you that Grub2 is better. Sure it is still rough around the edges but it is better. 
Fedora is using Grub2 for F-13 and my guess is that Mandriva and openSUSE among others will be using it too for their next release. I know Mint 8 will be.
Expect a lot of improvement by Lucid release.

Grub 2 is NOT an improvement for me.
I have a RAID0 configuration. On Jaunty I made a partition for /boot on sda (outside the RAID because it can/may not be inside), a MD0 RAID0 for / and an MD1 RAID0 for /home. How to do that in Grub2 where the files are scattered all over the place? Just doesn't work.

Read the forum here and day by day you see that Compiz is destructing systems, making them unstable. Once more, if people want to use Compiz please do so, but don't install it in the standard install.

---

### Post by longlegs on 2009-11-21
Hi Seeker,

It was the limitations and lack of flexibility that led the developers to rewrite grub from scratch.
All a bootloader needs to do is get the location/s of the OS/s, list for choice if more than one, get choice, boot it. Where is flexibility needed?

I know that some bugs are more important than others, but the programmers involved with grub should realise that (for most potential new users) if it can't dual boot with win, the user won't switch.
Granted it happens more than it should, but percentage wise I think it's not *that* huge of a problem.
It isn't a problem for the potential new user. He/she just skips linux and stays with windows. Is that what you want?

Because they have the experience from Grub 1 to look back on and not make some of the same mistakes again.
If they did not make it work, then they did not learn from their mistakes so I repeat WTH makes them think they can "do it right the second time"

I would guess, of the people who have had installation failures, significantly less than half choose where to install grub. 
You cannot get thru the process of installing the latest distro of ubuntu without making a choice unless you fail to click the 'Advanced' button, in which case no bootloader is installed.

Your third drive, second partition might not be sdb3. Would have been better to use (hd2,3).
Say I have three drives named Abigail, Monica and Penelope and that they are respectively reported to the user as the FIRST drive, SECOND drive, and THIRD drive. If I understand your 'better to use (hd2,3) your hd2 would represent the THIRD DRIVE and  HD1 would represent the SECOND drive, so that hd0 would represent the FIRST drive, and it's ok to spout confusion like this to beginners. BS. If you use hd0 to represent a drive, it must be the Zeroth drive which is non-existent, then hd1 would represent the FIRST drive, hd2 the SECOND drive, and hd3 the THIRD drive. Again, hd0 representing a real drive is non-sense.
Now, if you find some thing magical about hd instead of sd, sr, .... From the viewpoint of a new user, a drive is a drive is a drive and who cares whether it is ide, scsi, sata, pata, juju, cd, fd or whatever. Something as simple as abbreviation would work just fine. eg Drive1,Drive2... Partition1, Partition2.. could be written as D1P1,D1P2,D1P3... D2P1,D2P2 and there would be no confusion. But now we run into the problem caused by adding an external drive. It sometimes causes the pre-existing drives to be renumbered, thus breaking your numbering system (and GRUB) AND WINDOWS. SO lets call the drives by name and partition number, eg AbigailP1, AbigailP2...And adding a drive causes no changes. Do you STILL like hd0 ??? 
BTW is a 32char DID# any better that say a 4 charDID? (DriveID)

I have seen where you could choose not to install the boot loader, but I have not seen where that is the default. What version was this?????
You cannot get thru the process of installing the 9.04/9.10 ??? distro of ubuntu without making a choice unless you fail to click the 'Advanced' button, in which case no bootloader is installed. Not knowing whats behind that button, it's likely that a new user would not choose that button, would wind up with no bootloader. That seems like a default (what you get by NOT doing something) to me.

I'm still trying to get a working dual boot. Just installed 9.04 the did an upgrade to 9.10. Will see if can get grub working that way....but it's late so

As you say, Later.
H.M.Jones

---

### Post by bcschmerker on 2009-11-21
Having one year's experience with 8.04-LTS Hardy, I see a lot of potential in software components introduced in later releases.  Most urgent for 10.04-LTS Lucid from my perspective are:

1.  A revised Startup Manager for, in addition to fixing the known serious bugs in, GrUB 1.9-up.  The version that came with Ubuntu 8.04 works only with GrUB 0.96, and the new version will need a comparable X/GNOME/KDE frontend.

2.  Improved JACK, FFADO and GStreamer.  Currently, my Everex with 8.04 is unable to use Userplane Chat due to a serious bug in the GStreamer-FFMPEG component (still triaged as of 21 November 2009), and we know about the failure to re-set USB cameras (likewise still triaged).

3.  Bug fixes in X/GNOME/KDE components related to display configuration.  Testing an eMachines/Acer T19W6 LCD display unit on my Everex under 8.04-LTS, I discovered that GTK defaults to not larger than 1366x768 (on a 1440x900 display) for DVI-D.

I have had no problems to date with multiple hard drives for a custom installation (my Everex uses one HDA, /dev/hd0, for System and User programs partitions plus swap; a second, /dev/hd1, for Home and Variable data partitions); reliable handling of SATA will be helpful for users of newer systems.

---

### Post by k3lt01 on 2009-11-21
> **Roasted said:**
> Dear Lucid Developers:

I would really, really like to have the next distribution release to actually support multiple hard drives, seeing as though Karmic cannot handle this task. Anything you can do in this regard would be appreciated beyond belief. Thank you for your hard work.

Your's Truly,
RoastedMy server runs quite well with 3 hdds so I think your not doing something properly.

---

### Post by Tompalaz on 2009-11-21
In the Fedora installer you can easily set up a software RAID, I'd like to see that in the Ubuntu installer as well.

In Ubuntu, if i'd like to raid my drives i'd need an alternate cd.

second: More of a bug fix, but if rhythmbox scanning my Music folder it asks for codecs for wmv files. However, it won't find any because they are already installed.   
This bug is reported [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566) but I'd still liked it to be fixed for next release :)

Otherwise, I'm really satisfied with Ubuntu.

---

### Post by k3lt01 on 2009-11-21
> **Gina said:**
> I'd like to see a Custom Install but also a Standard (or Normal, or Everything) install option.  That way new users can choose the Standard Install and get what we have now.  Those wanting a cut down version would have the option.  The Minimal-Install-CD (mini.iso) doesn't do this - it installs the system but downloads the apps you've ticked from the net.  What I mean is to have everything on the CD as now but optionally prevent installing the apps you don't want.  This applies particularly to CDs obtained by other means than downloaded as ISO files - the mini-iso covers the download method (well almost).Maybe an online program selection that allows an experienced user to choose what they want in their new system, e.g. Thunderbird instead of Evolution, or Banshee instead of Rhythmbox etc. and then be able to download the cd/dvd of that install.

> **Gina said:**
> I wonder how much space such an extra option would take up on the CD.  I wouldn't have thought it was very much - just an installation script to read as installation progresses.My old RedHat is 3 cds so it does take up alot of space and that is the only reason I can see Ubuntu not adopting such a process unless the demand is there.

With Vista Windows went to dvds and not all machines that could use Vista otherwise had dvd capable drives (big mistake) so to get Vista people were required to either purchase a new dvd drive that was not guaranteed to work with Vista anyway (another big mistake) or order it on cds and wait for ages for it to come (huge mistake). So there are drawbacks to this idea even though I like it myself.

---

### Post by k3lt01 on 2009-11-21
> **DeMus said:**
> Use Thunderbird as standard e-mail client and get rid of Evolution. Simply because, as I understand it, it is woven deep in the heart of Gnome. Just as IE is part of the Windows OS. Why does Linux (gnome in this case) imitate Windows?Evolution is actually a decent program now. My only problem with it is that it is a required component for an Ubuntu install.
> **DeMus said:**
> Get rid of Grub2. Let Karmic be the only OS in which the Ubuntu made this mistake of using it. Again this is an imitation of Windows. Windows used to have the boot.ini file, a simple text file, easy to be changed if necessary, now they have a system which is not so easy to configure. Same happened here with Grub. Why? Don't tell me Grub2 is much better. Grub1 boots my pc as it should, that's all I ask of it. I don't need a complicated menu on a shining background because I don't even want to see it. The computer has to boot and boot fast, without showing me the menu at all. So why waste so much time and effort on it?I find GRUB2 easier and so to do many others.
> **DeMus said:**
> Loose Compiz in the standard installation. When people want to have it let them install it and ruin their computers, don't make those people who do not want to have Compiz do the same.I agree but this is personal choice for many to have it
> **DeMus said:**
> Easier ways to connect computers together, using Samba, NFS, Remote desktop, etc.This isn't hard anyway
> **DeMus said:**
> A stable Conky which does not crash all the time like the one which is in Jaunty.Never had a problem with this
> **DeMus said:**
> Easier and more functional way to install drivers, especially the graphic drivers. ***_Just look in the forums to see how many times this subject comes up._***The bit highlighted is the important phrase, for some reason people aren't looking in the forums anymore they just post their problem without searching. It seems using ones own brain is becoming increasingly difficult, so much so every second Tom, Dick, and Harry has to post a new thread because they can't use a search function. Sorry but sometimes you cannot save people from themselves.
> **DeMus said:**
> Put back the things which are in Hardy and Jaunty, but were taken out or were hidden somewhere, in Karmic: Preferences of the loudspeaker, getting rid of the 60 seconds delay when shutting down, etc.The 60 second delay is a great thing, it has saved me alot of effort with my father especially when he accidentally hits the wrong button. Methinks your just having a rant here.
> **DeMus said:**
> A video-editing program which can stand the competition of let's say Adobe Premiere and Ulead's Media Studio Pro.I agree choose one from UbuntuStudio and let the devs know you want it in the standard install.
> **DeMus said:**
> Let the user choose from a giant list during installing the OS which programs (s)he wants to install and use. That way everyone can get what (s)he wants to have and is not being stuck with something which is never used.Again I agree, see my previous post for a possible idea on how to make this work.

---

### Post by goldsniper on 2009-11-21
> **pressureman said:**
> Drop Evolution, since it has done anything but what its name implies for about the last four years. Replace with Thunderbird 3. I know it's still in beta, but it's probably more stable and faster than Evolution, and the Lightning calendar addon with Google Calendar connectivity is already much nicer than Evolution's calendar.

Thunderbird also has a way better IMAP implementation that actually supports IDLE. The only thing that Evolution _might_ have over TBird is libmapi, for Exchange connectivity... and which is due any decade now.


Hmm.. I used evolution back in 7.10, dont like it, change to Thunderbird since.

> **froggyswamp said:**
> No no no, while the majority of users would prefer Thunderbird 3 cause it's clearly better than Evolution, Canonical wouldn't move over cause their (Ubuntu) devs are already comfortable with Evolution and will throw at you any reason not to move over, just throw a few (half-truth) reasons like "better integration", "users are accustomed with Evolution", "it's the default in Gnome so less work", etc.
But if you touch an even more important subject (which Evolution leads to) I'm pretty sure you'll be banned (as troll or whatever). I don't need troubles.

Just remove evolution and install what ever we want! Hehe..

> **qamelian said:**
> Um, no. Evolution is simply a better solution for a PIM. If the only option I had was Thunderbird and Lightning, I would have no choice but to go back to Windows and Outlook, because T&L simply doesn't provide the functioanlity I need in my work environment, while Evolution does. T&L has maybe 70% of the features I require in a PIM solution for work. The combo just isn't good enough to be the default solution yet.

So, make Thunderbird more PIM friendly or even better make Evolution UI more friendly/useful.

------ just my 2.5 cnts.

---

### Post by goldsniper on 2009-11-21
> **omarly said:**
> I just tried to get a friend of mine to convert. He is a gamer and has a brand new mashine, 8 kernels and so on...., Earlier he has tried to install ubuntu, but when he came 2 the partitioning part, it had stopped him when he tried to cope on his own. I got him going up on the beta 9.10, but he just got the win7 in the mail, so he had lots of hours to play.

He is interested in getting his big-screen and all the things on his home going on Myth, and he is a RALLY big tech-freak, but if the part about partitioning in the install prosess could be made a bit more accessible for previous windows users I think a lot of new users could be won.

Seems like its quite a gap in understanding that part. I can remember i had 2 read a bit about it too.

We did an install on a split ssd and we had to format the part of the disk 2 ext3 before i could guide him to complete.

I still don't understand why he didn't follow my adwise to convert completely, but his loss.

Just love the new 9.10 64 install on my laptop!!!! WWWOOOOWWW

Yes, I know what you mean... for the average users, making decisions on what to partition is like that old matrix movie script:

"Take the blue pills, you'll see the truth!"

When even they don't know what is "partition" and never did a partitioning process!

Hmm.. I think.. easier documentation and examples should help.

---

### Post by goldsniper on 2009-11-21
> **Merk42 said:**
> 
The difference usually with installing Ubuntu vs Windows is that for the majority of users, Windows is **already installed**

I agreed! But now and then, when those majority of users become quite comfortable with Ubuntu, usually they will try to install Ubuntu by themselves. :popcorn:

---

### Post by Gina on 2009-11-21
There is a simple and reliable way of installing Ubuntu on a Windows machine and that's WUBI the Windows Ubuntu Installer.  This works like installing any extra software in Windows but results in a dual-boot system with a boot menu when starting up that has Windows and Ubuntu boot choices. No worrying about partitions, WUBI sets up a filing system inside Windows.  In spite of this the Ubuntu system performs very nearly as well as it would in a separate partition.  (Unlike using a VM.)

In the unlikely event that the user doesn't like Ubuntu, it can easily be removed the same way as any Windows application and everything is restored to what it was before.

---

### Post by Gina on 2009-11-21
Continuing from my post above...  But using the standard Desktop CD to install Ubuntu...

The problem with installing Ubuntu (or any other separate OS) into a separate partition is that a Windows machine is usually supplied with one partition containing Windows.  Or it might have another partition (often hidden) providing a recovery option whereby the HD is wiped and the system restored to the factory default.  In any case the user will probably need to resize the Windows partition to make space for  the Ubuntu partitions.

On a new machine there will be plenty of HD space at the top of the Windows partition and little problem other than the user being frightened of touching partitions - which I find quite understandable.  The automatic installation option of letting the installer resize and do all the necessary steps should be perfectly safe.  However, after using the PC for some time the HD is likely to have files scattered all over it and will need de-fragmenting within Windows before any attempt to set up extra partitions for Ubuntu.  I've known people even frightened of doing this - it's not that uncommon.

I don't know about later versions but I found Windows XP needed defragging several times to move files to the beginning of the partition.  Furthermore, it needed hibernate and swap systems turned off to avoid immoveable files interfering with the process.

We, in this forum, are quite familiar with all of this but the general Windows user may not be and I think the installer could do with improving, particularly in the partitioning phase.  More instructions would help.  And although the Desktop (Live) CD installer is very pretty and informative to experienced users, I'm far from sure new users would see it like that.

---

### Post by Merk42 on 2009-11-21
> **goldsniper said:**
> I agreed! But now and then, when those majority of users become quite comfortable with Ubuntu, usually they will try to install Ubuntu by themselves. :popcorn:

My point was partitioning is done in either OS.
No matter how easy Ubuntu is to install or hard Windows is to install it won't matter to most Windows users because they never had to install Windows.

---

### Post by seeker5528 on 2009-11-21
> **longlegs said:**
> Now, if you find some thing magical about hd instead of sd, sr, .... From the viewpoint of a new user, a drive is a drive is a drive and who cares whether it is ide, scsi, sata, pata, juju, cd, fd or whatever.

Floppy drives are 'fd', Hard drives are 'hd', optical devices are 'cd', seems pretty logical to me, I don't think there is a lot of confusion over that point.

Which only leaves confusion over the numbering, which could be dealt with by indicating to people that numbering starts at 0 at the time they are given the option to specify the location.

If you look in the disk manager in Windows the first hard disk is 0. If you look in the boot.ini file, the identification of the hard drives and partitions there is more cryptic resembling something more like the way the linux kernel identifies them. Grub doesn't care how the OS represents the drive, it just needs to be kept up to date about which drive should be represented by what number.

> BTW is a 32char DID# any better that say a 4 charDID? (DriveID)

The UUID thing has it's advantages and disadvantages, but that's an OS thing, grub doesn't care that. I did see some references about being able to use a UUID with the find command, but I did not follow up to see how you would actually use that.

> Not knowing whats behind that button, it's likely that a new user would not choose that button, would wind up with no bootloader. That seems like a default (what you get by NOT doing something) to me.

My expectation is a new user would accept the default, not click on the advanced button, and ends up with grub installed in the MBR of the first HD or if they do click on advanced and don't understand what they are looking at, they don't change anything and they end up with grub in the MBR of the first HD.

There are three things that come into play. 

[list]1. In what order does your motherboard recognize the drives?[/list]

[list]2. In what order does the OS recognize the drives?[/list] 

[list]3. How are the drives mapped in the device.map file?[/list]

Say you have a SCSI HD an IDE HD and an IDE CD/DVD, the IDE stuff could be SATA or PATA, it doesn't really matter. 

I don't think it's typical, but on some computers if you boot from the SCSI your SCSI HD will be seen as the first HD, if you boot from your IDE CD to install the OS then your IDE HD will be seen as the first HD. I don't know what drivers are available at boot time when you boot off of the Ubuntu CD, but if that doesn't include the SCSI drivers your IDE stuff will always be recognized at boot time and the SCSI won't be recognized until the boot process is far enough along for modules to start being loaded, so the IDE stuff will always be first.

If you change the boot order in the bios, that may also change the order in which the different types of drives are recognized.

The device.map is created based on the way things are recognized at the time of installation, if that is different than it is when you boot normally, you have some problems.

[list]1. If you don't choose where to install grub it will most likely be installed to the MBR of the wrong drive.[/list]

[list]2. If you do choose where to install grub, but don't verify that the drives show up in the order you expect, you might choose the wrong place to install grub.[/list]

[list]3. If you verify that the drives show in a different order and made the necessary adjustment to get grub installed in the correct location, you have to make corrections after the fact. Either edit the device.map file (it's a text file) to remap the order of the drives based on what is in the grub boot entries or edit the grub boot entries based on the order the drives are actually detected in. Either way it's a PITA.[/list]

Theoretically if you bios lets you choose which hard drive should be first in the boot order, that should always be hd0, if I am reading things correctly. If you can only choose which type of drive should be booted first (SCSI, IDE, etc...) then there is the added potential for something to go wrong and with SCSI I believe there are extra variables in the way different motherboards may handle things.

Looks like there was some discussion ([Link](http://www.mail-archive.com/grub-devel@gnu.org/msg05907.html)) about possibly retiring device.map with grub2, but it sounds to me like we are not there yet. 

Later, Seeker

---

### Post by seeker5528 on 2009-11-21
This talk about boot up stuff does bring to mind a couple of things I would like to see changed.

First....

With all the partitioning utilities, if you are formatting an existing partition with the same type of format that was previously used, use the same UUID instead of generating a new one. Or at least provide a function to save the UUID before hand and restore the saved UUID later. I know this could be done from the command line, but most people are not going to want to figure out what is required or think it is more hassle than it is worth.

Second....

It seems insane to me to expect the distribution that is managing grub in the MBR to recognize all your other linux installations and magically keep grub entries up to date that directly load their kernels.

It is sane to expect each distribution to handle it's own boot stuff correctly so I would like to see the OS-prober first look at the partition BRs and add chainloader entries for the ones where a boot loader is found and then only probe for additional stuff on partitions where no boot loader was found.

Later, Seeker

---

### Post by Paul D on 2009-11-21
Someone may have already stated; Relevant "detailed" documentation pertaining to current version. I can hardly find any useful info out there on 9.10, just other people with problems, hunting for answers.

Driver installation tools, + GUI to show what version drivers are installed with what hardware, and the status. Instead of me knowing what directories things are stored in, and what command line commands to use. I am uncertain of the status of Envyng for 9.10+. But that was the right idea. By the way, Envyng doesn't seem to work on 9.10 for me.

Similar GUI tools for networking setup. It is not obvious to everyone that you have to uncomment and move text around in some file somewhere to get a windows network to function.

Standard sound tool, it is confusing having Pulse, Jack, Gnome etc. I don't know the difference, or which one I need. More informative test tools for these kinds of things might also help.

---

### Post by longlegs on 2009-11-22
Hi seeker,
It is sane to expect each distribution to handle it's own boot stuff correctly so I would like to see the OS-prober first look at the partition BRs and add chainloader entries for the ones where a boot loader is found and then only probe for additional stuff on partitions where no boot loader was found.

On my machine i have scsi#1 (5 parts) with dos5 on first part, NT4 on third part, then an EIDE (3 parts) with Win98SE on first part, Win2k on second part, then a scsi#2 with 2g fat32 on first part, 4g ubuntu swap part, 30g ext2 with ubuntu 9.10 installed on third part, 30g empty ext2 and 40g fat32 on parts fourth and fifth. I can reliably boot all but ubuntu with NT's loader, and can boot ubuntu with 'Super grub disk'. I'm just about ready to throw in the towel on the dual boot problem. BUT one thing I have found is that the ubuntu disk# depends on whether or not I have a usb drive plugged in.
If I run os-prober it only finds 
/dev/sdb1:Windows NT/2000/XP (loader):Windows:chain
sdb1 is scsi#1, so your idea above sounds good to me.
Have a good day!
H.M.Jones

---

### Post by Gina on 2009-11-22
I have a boot problem on my laptop.  The boot loader finds all the OSs but nothing will boot from the grub2 menu - system just freezes.  If I reinstall the grub legacy driver top the MBR, again all OSs are listed and XP and earlier Ubuntu versions work fine, but the boot2 systems (Lucid and Karmic) won't boot.  Same thing happens as with grub2 on the MBR.  I edited the menu list in grub legacy to chainload to the two grub2 systems but get the dreaded Error 13 :(  There is only one HD on the laptop so it isn't due to wrong HD identification.

I remember seeing a possible solution for this but a search brings up dozens of results but so far not what I'm looking for.  I know I've read that several members have been having this sort of problem so I think we could do with a sticky thread with suggestions for solving it.

---

### Post by Seamyst on 2009-11-22
An out of the box way to completely disable the touchpad on a laptop.  Preferably just by having this option on System >> Preferences >> Mouse >> Touchpad.  It's very irritating to have to follow several steps in order to do this, especially when the steps change between versions.

I agree that a faster boot time would also be very nice.

Other than that, I like how Karmic is working!  And after going into alsamixer, let me say that it's a delight to finally have a GOOD volume range on my MacBook, instead of having to max out the volume.

---

### Post by Manyette on 2009-11-23
I'm a newbie, so my input is possibly/probably questionable, but I have been very impressed with Karmic, and to be honest, I would put a priority on consolidation of the present features of Ubuntu ahead of new features.  I'm not against the suggestions made, but it seems every release comes out, and the follow the flood of fixes for the base release.  I admit that my experience is limited to 8.10, 9.04, and 9.10, but I have seen many posts that complain of faults in the base release, many of which are fixed very shortly after the release, but that puts off a lot of folks who download the base release, find problems, and don't realize how quickly they will be fixed.  Just my thoughts.

---

### Post by ranch hand on 2009-11-23
Hopefully this is what will happen with this release.  You missed the last LTS (Long Term Service) release (8.04).

10.04 should be very like 9.10 and much more stable.  Here in testing we will be the first with a clue.

---

### Post by irishbreakfast on 2009-11-24
I would like the return of the functionality in 9.04 sound preferences! Specifically, I used to be able to change the output device independently for system sounds, tv/movies and something else. I enjoyed this!

Now, while watching a film I get system notifications over the TV, YUCK! 

Please bring back the flexibility. (And if you can tell me how I can revert to the 9.04 sound pref, please send me a message. I haven't figured it out yet)

---

### Post by irishbreakfast on 2009-11-24
after thought:
Cleanup guis used for NFS.  I just setup NFS between two home 9.10 machines and was disappointed in the entire experience (my changes to /etc/exports kept getting overwritten, can't share the folder I want to (don't know why), always defaulted to assuming I wanted a windows share)

And don't get me started on all the coasters Brasero and Xfburn are making for me - simply when I blank the disk.

Or the fact that the Ubuntu Help centre keeps crashing.

Breathe. 
Improvement I want are quality documentation where I can find it and skip the bells and whistles - clean up (what should be) the simple stuff.

---

### Post by Jordanwb on 2009-11-25
I'd like to see Ubuntu make up their minds about how to grant privileges. In some of the porgrams - like Synaptic - it asks for your password right away, but for "Login Screen" you have to unlock it by clicking a button then typing your password. Did Canonical forget about gksudo?

---

### Post by gnomeuser on 2009-11-25
> **Jordanwb said:**
> I'd like to see Ubuntu make up their minds about how to grant privileges. In some of the porgrams - like Synaptic - it asks for your password right away, but for "Login Screen" you have to unlock it by clicking a button then typing your password. Did Canonical forget about gksudo?

This is largely down to migrating all applications to PolicyKit. The screen saver sounds like a papercut though you could file it.

---

### Post by e-Gee on 2009-11-26
Great improvement would be to have Pidgin instead of Empathy in Lucid :KS

---

### Post by k3lt01 on 2009-11-26
> **e-Gee said:**
> Great improvement would be to have Pidgin instead of Empathy in Lucid :KS
I don't necessarily agree with this, even though I personally use Pidgin I have found some very serious security flaws in it and have had to constantly battle with it in Karmic. I have posted about it on this forum and also on the Pidgin site itself. 

My issue with Empathy is also security related so I guess, for me at least, it's a choice between the lesser of 2 evils. The jury, me that is, is still out and deliberating on the question of what one is less evil ;)

---

### Post by zoggerman on 2009-11-26
> **sim-value said:**
> Better Bluetooth Functionality!
After Pairing services should be discovered and made ready for use. For example for connection over network manager!

There is nothing more Painful(big expection ATI drivers) ive ever done in Ubuntu than trying Bluetooth dialup ...

  ----what you said. I am trying like crazy to get this install to even *see* the USB bluetooth dongle. The kids call it &quot;epic fail&quot;.   The future, a big part, of computing is wireless connections. So wifi and bluetooth *have* to work, and work well. Pretty soon now we'll have smartphones with enough computing power to be the main computer people have,(cellphones already *are* the main &quot;computer&quot; people have in the devloping world) then they will only need a paired keyboard and monitor and printer, etc when they get home. Plop the phone down, sit down to your desk and keep on doing whatever you were doing using your phone, just this time with a normal sized set of keyboard/mouse/monitor, etc.    The interim stage is netbooks, but really, the &quot;powerful enough&quot; cellphone is only a year or two away at this point, because of the ARM processor and tons of cheap solid state memory and storage goodness.

---

### Post by buzzmandt on 2009-11-27
I would like to see medibuntu repo as a check option in sources gui

---

### Post by gnomeuser on 2009-11-27
> **buzzmandt said:**
> I would like to see medibuntu repo as a check option in sources gui

Why? I mean I never heard of this repo before. If it brings packages that we desire I would argue the correct path would be to move them into debian then into the correct ubuntu repos to make them available. If it is commercial software then it should go into the commercial ISV repo.

---

### Post by t.rei on 2009-11-27
I still want a properly working **Groupware Backend**. If this is ubuntu one - please support encryption. Thank you. ;)

---

### Post by k3lt01 on 2009-11-27
> **gnomeuser said:**
> Why? I mean I never heard of this repo before.Your kidding right? Your saying you have never heard of [MediBuntu]("http://www.medibuntu.org/")?

---

### Post by seeker5528 on 2009-11-28
Thought of an additional UUID related wish to go along with my earlier wish that partitioning utilities provide a function to save and restore UUIDs, they should also give you the option to generate a new UUID.

Take the hypothetical situation. Since many people are not re-partitiong drives all the time and may not think of it, say you just got a nice new large drive, so you use Gparted, dd, ddrescue, or whatever to copy a partition to the bigger drive, but you are leaving the original disk with the original parition in there. Now you have 2 partitions with the same UUID, so what happens? Your fstab entry that uses the UUID to mount the partition causes them both to be mounted at the same mount point.

Yeah.... ummmmm.... don't ask me how I know that, I'm sure you can guess. :redface: :P

Later, Seeker

---

### Post by LoREZ on 2009-11-28
I use a dual-monitor system, and this has led me to the conclusion that the new gdm is junk (for me, anyway).  Frankly, I'm not the only one with this problem: [dual-monitor problems]("http://ubuntuforums.org/showthread.php?t=1315500").  Even though gnome recognizes my preferred display (because I told it in my xorg.conf), gdm doesn't at the login screen.  This also causes problems with my e17 install, since e17 thinks gdm's decision is somehow correct, so my launchbar is relegated to my secondary screen in that desktop environment too.  It's stupid, and apparently impossible to fix without hacking the code.  There are no settings worth a damn to manipulate, except 'pick your theme' stuff, the execution of which is needlessly obscure for a graphical program.  Seriously, who got the bright idea to make gdm so opaque and lame?

---

### Post by expxe on 2009-11-28
i would like to see less emphasis on the command line. seriously. work on this issue before fixing up other less important problems or adding additional (useless) features. 

this is the big one, you know it will keep coming back and biting you in the behind until you take care of it.

---

### Post by zaphod777 on 2009-11-29
I would like to see network manager fixed. The forums are riddled with users having to uninstall it and install wicd me being one of them.

Also I even had to install the backports to get wireless to work somthing I never had to do before.

Also 802.11n wireless seams to be broken. with all of the 802.11n devices out there we should make sure we support them.

---

### Post by Gina on 2009-11-29
> **LoREZ said:**
> I use a dual-monitor system, and this has led me to the conclusion that the new gdm is junk (for me, anyway).  Frankly, I'm not the only one with this problem: [dual-monitor problems]("http://ubuntuforums.org/showthread.php?t=1315500").  Even though gnome recognizes my preferred display (because I told it in my xorg.conf), gdm doesn't at the login screen.  This also causes problems with my e17 install, since e17 thinks gdm's decision is somehow correct, so my launchbar is relegated to my secondary screen in that desktop environment too.  It's stupid, and apparently impossible to fix without hacking the code.  There are no settings worth a damn to manipulate, except 'pick your theme' stuff, the execution of which is needlessly obscure for a graphical program.  Seriously, who got the bright idea to make gdm so opaque and lame?I have the same problem.  We have an HD TV and one graphics output is (sometimes) connected to the TV via a DVI to HDMI cable.  The other output is connected via a KVM switch to my 22" monitor.  (I use this for two machines.)  

The problem is that if the DVI-HDMI cable is connected the system sends it's display to that.  This is obviously not acceptable so I have to unplug the cable from the computer whenever I don't want a computer home cinema working!  And I don't like crawling around on the floor any more!!!

---

### Post by gnomeuser on 2009-11-29
I would love to see VDPAU be easy to use on setups that support it. However I acknowledge that the various acceleration technologies such as VDPAU aren't flexible nor easy to integrate into GStreamer. I would be perfectly happy to see it work in Lucid+1.

The reason I think getting VDPAU and similar technologies supported is that there is a growing market for smaller machines used for lighter desktops or media centers that depend on this technology to do HD playback. 

The end goal would naturally be to ship an Ubuntu Media Center and let vendors package known good hardware that will work out of the box (a little like Google does for ChromeOS really).

---

### Post by arvevans on 2009-11-29
Ubuntu-Gnome interface uses the same default directory (/$HOME/[username]/Desktop) for all "desktops", with no obvious way to customize which directory is related to which desktop.  We need a GUI tool with ability to make different desktops focus on different directories, so that desktop content and tools will reflect specific work tasks.  "Defaults" are nice, but we could really use some Gui's to help changing them when needed.  Such a tool could also control which top-bar application launchers are present on which desktop.

Thanks,

---

### Post by expxe on 2009-11-29
more support for logitech mice, perhaps a configuration program with a GUI

---

### Post by t.rei on 2009-11-29
Sound working PERFECTLY! And I mean perfectly. Booting/Waking up with speakers plugged in, Subwoofer, Speakers muting as they should... and so on... just WORKING.

---

### Post by gnomeuser on 2009-11-29
> **t.rei said:**
> Sound working PERFECTLY! And I mean perfectly. Booting/Waking up with speakers plugged in, Subwoofer, Speakers muting as they should... and so on... just WORKING.

I would encourage filing bugs, we do actually work on making this better and often to fix your setup all we need is a quirk for your specific hardware which is easily to deploy. 

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by Reiger on 2009-11-29
> **arvevans said:**
> Ubuntu-Gnome interface uses the same default directory (/$HOME/[username]/Desktop) for all "desktops", with no obvious way to customize which directory is related to which desktop.  We need a GUI tool with ability to make different desktops focus on different directories, so that desktop content and tools will reflect specific work tasks.  "Defaults" are nice, but we could really use some Gui's to help changing them when needed.  Such a tool could also control which top-bar application launchers are present on which desktop.

Thanks,

You may want to read up on the xdg-user-dirs spec which is an interoperability standard so xdg &#8216;aware&#8217; applications such as many KDE and GNOME apps can do basic integration (e.g. know where to expect/store what things by default). These settings can in fact be customized to your taste -- if not for individual desktop/workspaces.

---

### Post by expxe on 2009-11-29
how about double click install for ALL programs, just like how windows does it! you know they had a good thing going with that, now ubuntu don't be jealous, just implement this upgrade and make everybody happy. because the current way of installing "packages" on ubuntu is just insane, there should be NO reason for users to be commandlining.

---

### Post by Merk42 on 2009-11-29
> **expxe said:**
> how about double click install for ALL programs, just like how windows does it! you know they had a good thing going with that, now ubuntu don't be jealous, just implement this upgrade and make everybody happy. because the current way of installing "packages" on ubuntu is just insane, there should be NO reason for users to be commandlining.

You mean like Add/Remove Programs or Ubuntu Software Center?
Or double clicking a .deb file?


It's not Ubuntu's fault if the creator of the program doesn't make it available in one of those two ways.

---

### Post by impert on 2009-11-29
I'd like to see a version of Grub 1 that could handle ext4 partitions.
> Maybe, and I hate to suggest this but, search for grub issues.
I'm not being funny here - We Need A Boot-loader forum or Sticky.
 **+1**, and the reason is that lots of people are having issues with Grub2, myself included. Oh, it's booting Ubuntu Karmic and Jaunty on this box, but it won't do lots of things it's supposed to.
  Having grub.cfg written only by **update-grub**/**grub-mkconfig** and not editable is a big mistake, I think, as it takes control away from the user. Grub1's menu.lst is easy and quick to configure, and you get what you want. With Grub2 I get  a list of  63 entries, 42 of which I don't want,  several with "Unknown linux on  . . ." - and one at least missing. (I know you can modify the grub.d files, but should you really have to hack the code?) What happened to the **hide** command? What happened to **geometry**? **configfile**? **chainloader**? And so on.
The only improvement is that it can deal with ext4, which is why I'm persevering; otherwise I'd just go back to Grub 1.

---

### Post by ranch hand on 2009-11-29
I happen to like and use grub2.  That said, I do not understand where this ext4 is a problem with grub-legacy comes from.

I have used grub-legacy with 9.04 and a couple of respins of 9.04, all installed on ext4, and never had any trouble with grub-legacy at all.

I think that this is from the same type of source that seems to be supplying most of the info on grub2.  Nice graphics, little knowledge.  Grub2 does have a number of problems, it does not need these compounded by people that are talking through their hats.

Grub-legacy does not need this either.

---

### Post by Slug71 on 2009-11-30
> **impert said:**
> I'd like to see a version of Grub 1 that could handle ext4 partitions.

 **+1**, and the reason is that lots of people are having issues with Grub2, myself included. Oh, it's booting Ubuntu Karmic and Jaunty on this box, but it won't do lots of things it's supposed to.
  Having grub.cfg written only by **update-grub**/**grub-mkconfig** and not editable is a big mistake, I think, as it takes control away from the user. Grub1's menu.lst is easy and quick to configure, and you get what you want. With Grub2 I get  a list of  63 entries, 42 of which I don't want,  several with "Unknown linux on  . . ." - and one at least missing. (I know you can modify the grub.d files, but should you really have to hack the code?) What happened to the **hide** command? What happened to **geometry**? **configfile**? **chainloader**? And so on.
The only improvement is that it can deal with ext4, which is why I'm persevering; otherwise I'd just go back to Grub 1.

Ahhh, Jaunty had Ext4 and Grub1. :neutral:

---

### Post by cariboo on 2009-11-30
The Ubuntu devs modified grub-legacy to work with ext4. Most of the other distro didn't bother doing that or using Ubuntu's patch. They have gone straight to Grub2. Another problem with grub-legacy is that it is no longer maintianed.

---

### Post by User3k on 2009-11-30
My request is simple :)

I have an old computer that has a floppy drive I never use. I would like Lucid to have a program that will make tiny little pizza's come out of it. While your at it I never use my old printer port and I would love to have a program that would dispense beer from it.

Thank you :popcorn:

---

### Post by Roasted on 2009-12-01
> **expxe said:**
> how about double click install for ALL programs, just like how windows does it! you know they had a good thing going with that, now ubuntu don't be jealous, just implement this upgrade and make everybody happy. because the current way of installing "packages" on ubuntu is just insane, there should be NO reason for users to be commandlining.

Do you... know how to use Ubuntu?

I install everything in the GUI without any issues. There's this neat thing called Add/Remove Programs in Ubuntu. Yep, just like Windows. Except in Windows, have you ever been able to "add" anything through it? Didn't think so. In Ubuntu, you can. And of course there's always Synaptic. :) 

If I install from the terminal, it's because I'm doing multiple applications at once. Example:

sudo apt-get install amarok audacious exaile vlc thunderbird ktorrent ubuntu-restricted-extras xmms audacity 

Several installations in 1 command?

Now now, WINDOWS, don't be jealous...

---

### Post by Dr. Freeze on 2009-12-01
I'd like it to be able to play PC games without using wine

---

### Post by Roasted on 2009-12-01
> **Dr. Freeze said:**
> I'd like it to be able to play PC games without using wine

That's a question for Electronic Arts, Squaresoft, etc etc. Not Ubuntu, unfortunately.

---

### Post by nanog on 2009-12-01
> Upgrading your entire system is much more complex than installing a few packages.

LOL!

Upgrade -d is the african word for does not understand how to use apt/dpkg.

---

### Post by confused_user on 2009-12-01
i would like to see much better driver availability and testing.  honestly that is the biggest problem with ubuntu right now.  i dont care about swishy new features, they mean nothing to me if i cant get on the internet from my wireless card

---

### Post by ShizzlePDX503 on 2009-12-01
I wouldn't mind seeing touch functionality and maybe gestures even as well... yeah I know its a Windows 7 ripoff but I think that they would be cool features and allow ubuntu to go into the future of user interaction especially with XBMC and other media center apps.

Just my two cents

---

### Post by Blancmange on 2009-12-01
I'd like to see proper support for stuff like my 12"x12" Wacom ArtZ II serial tablet and stylus. Graphics work of any kind is infeasible without a tablet and I see no good reason to throw out a perfectly functional $1000 tablet built to last (like a Model M keyboard) and buy a new one just on the chance that Ubuntu might support it better.

As it is, Ubuntu 8.04 sort of supports my tablet, but every few seconds or so, it generates spurious clicks at maximum force and often sends the pointer to the edge of the screen. It is very, very hard even just to view or scale an image in The GIMP without marring the image.

As a consequence, I boot into Windows 2000 to perform any task that requires reliable control of the pointer. (I'm not going to use a computer mouse to do it, of course. That would be dumb.)

I'm about to do another great backup and see what 9.10 (non alpha) is like.

---

### Post by negativ on 2009-12-01
I would like to see a utopian fantasy world where editing the stupid GRUB2 boot menu is less complicated than compiling a custom kernel.

---

### Post by LiquidMeson on 2009-12-01
> **negativ said:**
> I would like to see a utopian fantasy world where editing the stupid GRUB2 boot menu is less complicated than compiling a custom kernel.

sudo nano /etc/default/grub
sudo update-grub
what were you trying to do?

---

### Post by ronacc on 2009-12-01
the improvments I would like to see have nothing to do with Ubuntu , I would like to see major companies stop ignoring us .And I am sick to death of "this site requires internet Explorer " .

---

### Post by Merk42 on 2009-12-01
> **ronacc said:**
> the improvments I would like to see have nothing to do with Ubuntu , I would like to see major companies stop ignoring us .And I am sick to death of "this site requires internet Explorer " .

You still see that?
I see some media related sites require Windows or OS X (though it works fine in Linux).

---

### Post by ronacc on 2009-12-02
yes I really do still see that , more often these days it is a you say but a couple of sites I MUST access in my business still only work with IE , thank god for wine .

---

### Post by Gina on 2009-12-02
I still see sites where the formatting is all wrong because they are using MS Extensions which only work with IE!!  Makes me SO MAD!!!  Even some died-in-the-wool Windows addicts use Firefox or other non-IE browser.

---

### Post by orbish on 2009-12-02
An intel driver that performs better than a 3dfx Voodoo3.

From the get-go.

---

### Post by confused_user on 2009-12-02
Edit: will any of these requests make it past this forum?  i mean do the developers read these? or are we all just getting excited over nothing?

The Network Proxy app in the menu does not work anymore.  In fact i configured it to use a proxy system wide on monday and it didnt work so i just set it to direct connection to the internet.  

2 days later i cant use apt-get since it cant find the proxyserver despite being configured to NOT use a proxy server, the proxy server details have now been deleted and it is still trying to use the proxy server.

ffs

GSM modem support in network wicd would be nice, then i would be able to get rid of network manager.

Better still, fix  network manager and make it start **before** gdm so that i can access my machine over ssh after a reboot without having to travel to get physical access to it and log in to gdm.

it has a wireless connection.

On that note, why does ubuntu load two drivers for myu rt2870sta  chipset?  it loads the correct driver on boot and then it loads the ath9k driver as well which takes precedence.  after each reboot i have to unload at9k to get a network connection.


driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers driver drivers drivers drivers drivers drivers drivers drivers drivers

---

### Post by jmmL on 2009-12-02
> **confused_user said:**
> On that note, why does ubuntu load two drivers for myu rt2870sta chipset? it loads the correct driver on boot and then it loads the ath9k driver as well which takes precedence. after each reboot i have to unload at9k to get a network connection.

Why not just blacklist ath9k?

---

### Post by registering on 2009-12-02
> **confused_user said:**
> Edit: will any of these requests make it past this forum?  i mean do the developers read these? or are we all just getting excited over nothing?


Good question. Based on responses and lack of responses to my bug filings, I doubt this will get past this forum. However in my naive quest for getting what I want, stop adding features and just add stability. I and others I know are seriously considering giving-up on Ubuntu and going elsewhere because Ubuntu has been such horrible quality for the past year.

---

### Post by confused_user on 2009-12-02
> **registering said:**
> Good question. Based on responses and lack of responses to my bug filings, I doubt this will get past this forum. However in my naive quest for getting what I want, stop adding features and just add stability. I and others I know are seriously considering giving-up on Ubuntu and going elsewhere because Ubuntu has been such horrible quality for the past year.

I know, this is kind of why i asked, I'm wondering if the development team are either not getting our feedback from this forum or if they even care at all.

---

### Post by Merk42 on 2009-12-02
> **confused_user said:**
> I know, this is kind of why i asked, I'm wondering if the development team are either not getting our feedback from this forum or if they even care at all.

Devs very very seldom read these forums.

---

### Post by confused_user on 2009-12-02
yes i got that impression, this is a very sad fact since this forum represents an important part of the 'community'.  

The part that is having technical difficulty.

I cant see stability and hardware support improving if they dont take notice of the issues that are being documented here.  Ok so there is bugtrack, but i have found the same problem there, people just dont seem to respond and my bugs keep being declared 'solved' when they are not.

Anyway, all a moot point seeing that nobody who can actually help is going to read this, also a waste of a lot of good ideas being posted here seeing as this poll is just for fun.

---

### Post by Jordanwb on 2009-12-02
Less file "Open With" hijacking. When I install ubuntu the first thing I install is vlc, then atunes. Since atunes requires mplayer to play mp3's I install mplayer. mplayer then hijacks the "Open With" and changes it to mplayer. The same goes with gnomad. Good thing I don't need gnomad now since I got my ZEN to work (yay!).

---

### Post by castrojo on 2009-12-02
> **Merk42 said:**
> Devs very very seldom read these forums.

Why does everyone keen saying that? I read these every day and we always look at forum threads when doing UDS sessions, etc.

Usually no one responds because we usually don't need to be reminded what sucks and what doesn't since we use Ubuntu too. :D

Brainstorm feedback is probably easier to follow than forum threads though.

---

### Post by benjamimgois on 2009-12-02
What i really like to see on Lucid:

[LIST]
[*]A simple Paint program, very easy to use.
[*]Empathy stabilization
[*]A better metacity
[*]A nice and beautiful plymouth boot.
[*]Integration of "Back in Time " as a principal backup tool.
[*]Integration of GUFW for easier setup of firewall.
[*]Removal of GIMP and Openoffice Draw
[*]Small marketing video on the first system boot. (Just like OSX)
[/LIST]

---

### Post by k3lt01 on 2009-12-02
> **whiprush said:**
> Why does everyone keen saying that? I read these every day and we always look at forum threads when doing UDS sessions, etc. Because there are alot of people on here who think they know better than everyone else. It helps to increase their post count when its outside of the Cafe.

Sorry about the negativity but this is a wish list thread and we have people asking for silly things, and others "giving helpful" advice when it hasn't been asked for. The silly things should be deleted and the advice left to absolute beginners talk etc.

---

### Post by ranch hand on 2009-12-02
> **whiprush said:**
> Why does everyone keen saying that? I read these every day and we always look at forum threads when doing UDS sessions, etc.

Usually no one responds because we usually don't need to be reminded what sucks and what doesn't since we use Ubuntu too. :D

Brainstorm feedback is probably easier to follow than forum threads though.
I have wondered about that as you do see users labeled, as you are, as being connected to Ubuntu development.  Seems like it would be a good place to see how folks respond to your work.

That is important to me anyway.

---

### Post by confused_user on 2009-12-02
> **whiprush said:**
> Why does everyone keen saying that? I read these every day and we always look at forum threads when doing UDS sessions, etc.

Usually no one responds because we usually don't need to be reminded what sucks and what doesn't since we use Ubuntu too. :D

Brainstorm feedback is probably easier to follow than forum threads though.

well i had previously assumed that developers used this site as a resource for feedback until i read a post from another developer saying the he and other developers "hardly read these forums at all" since they dont have time.

firstly i think i can speak for every one when i say that i appreciate your work - even the bits that dont work properly

secondly, operating systems are important and we all want ours to work properly.  It can be frustrating as an end users to see developer resources focused on implementing new features when the old ones dont work properly and we are still,after many years of perseverance fighting to get our peripherals working.  

i know that you cant be held responsible for manufacturers not releasing drivers that work, or just releasing any driver at all but that does not help the end user nor does it offer a solution to a very large stumbling block to ubuntu uptake.  

How about assigning a group of developers to purely work on drivers - that is but one suggestion.

I can already hear the people on here thinking "well if you dont like it go use windows", those are the people using already supported hardware no doubt.

there is not enough contact from the development team and the userbase and as a result we all post our frustrations here.  

I do hope that this post can be taken constructively and not attract trolls.

---

### Post by Merk42 on 2009-12-02
> **whiprush said:**
> Why does everyone keen saying that? I read these every day and we always look at forum threads when doing UDS sessions, etc.

Usually no one responds because we usually don't need to be reminded what sucks and what doesn't since we use Ubuntu too. :D

Brainstorm feedback is probably easier to follow than forum threads though.

Well okay if I am mistaken, then I am glad to be. I thought I had heard it often from 23meg (or maybe someone else) that it was the case that devs didn't often read these forums.

Other than perhaps yourself and mpt I haven't noticed a lot of developers posting.

I also didn't mean to say this place was just ignored, just that there are other ways the devs use for communication, like launchpad and mailing lists.

---

### Post by Amaranth on 2009-12-02
A few of us read them (somewhat irregularly) but you'll still see people telling you to file a bug instead of expecting posting here to get you a fix because a forum makes for a terrible bug tracker.

---

### Post by Gina on 2009-12-02
> **Amaranth said:**
> A few of us read them (somewhat irregularly) but you'll still see people telling you to file a bug instead of expecting posting here to get you a fix because a forum makes for a terrible bug tracker.Yes, forums contain much irrelevant chat and finding something specific is not easy if the Search doesn't bring it up.

Must say, it's lovely to see you here :)  I very much appreciate all your (collective) hard work.  I used to be a software developer, so I know the problems.  Thank you :):)

---

### Post by 23meg on 2009-12-02
> **Merk42 said:**
>  I thought I had heard it often from 23meg (or maybe someone else) that it was the case that devs didn't often read these forums.

There's a distinction between "read" and "participate in". 

And whether (m)any developers ("contributors" is the term I prefer; of the people you cited, neither whiprush, nor mpt are "developers") read or participate in the forum is a different question than whether an unstructured, noisy "wishlist" thread is a good way of listening to and keeping track of what people need or want.

---

### Post by Docaltmed on 2009-12-05
All I really want from Lucid is the ability to have my laptop suspend or hibernate without freezing up. Really. That's all.

---

### Post by pepsifx357 on 2009-12-06
For the server edition, I would like to see a well rounded, built-in exchange server that is compatible with MS Exchange.

---

### Post by Ylon on 2009-12-06
[delete]

---

### Post by longlegs on 2009-12-13
During install of 9.10 the partitioner 'scanned' the drives, asked a question, got an answer, scanned the drives, asked a question, got an answer, scanned the drives...

How about scanning drives ,asking ALL the questions, get ALL answers, scan once more IF NEEDED ( and it should not be ), partition and finish install?

How about replacing ALL 'Error xx" messages with "Cannot find file <filename>, browse for? Y/N"  or "Corrupt file <path/filename>. Replace or repair and try again." or .....
Would it really take too many bytes to do this? or are programmers in general still stuck in the days of assembly and 32k total memory?

Consider that an explanatory message would eliminate posting a lot of questions saving a kot of time.

have a good day!
Longlegs

---

### Post by smoosh on 2009-12-13
a working suspend for my Sony Vaio laptop so I can upgrade from Jaunty. It doesn't work in Karmic...

---

### Post by SonicSteve on 2009-12-13
Good Intel Drivers for the latest GMA chipsets,
Bug fixes,
General stability, Firefox has on occasion become "uninterpretable" in Karmic. This is a bad, bad thing for the default browser to do. Often a reboot is the only way to revive it.

For the server, I would like a GUI. Go ahead and through the snowballs at me. There is just a lot to learn, and learning the command line for server makes it just that much harder.

---

### Post by Taoye on 2009-12-14
Networking
Clean and unified boot experience
Look & Feel... I really like the Dust theme, and I want stuff like Aero snap in Gnome. 

Oh and most importantly... fixing bugs without causing new ones. I encountered two major bugs on Karmic's release and am not a happy camper.

---

### Post by donniezazen on 2009-12-14
Seamless integration with external display.

---

### Post by running_rabbit07 on 2009-12-14
Basically, I'd be happy with Karmic built on a better kernel, which Lucid does work better than Kamic in VBox. Anything else the devs add will be icing on the cake.

And, if it is released in time, I would like to see Thunderbird 3. It looks awesome in Windows and Fedora, so I know it would look even better in Ubuntu, the OS I call home.

---

### Post by collinp on 2009-12-14
> **running_rabbit07 said:**
> And, if it is released in time, I would like to see Thunderbird 3. It looks awesome in Windows and Fedora, so I know it would look even better in Ubuntu, the OS I call home.

Thunderbird 3 was released earlier last week. It does indeed look awesome; I pulled it from the Mozilla Daily Build PPA found at [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa") .

---

### Post by SonicSteve on 2009-12-14
> **soham_1207 said:**
> Seamless integration with external display.

Add my vote to this also. Honestly it's embarrassing, when macs and windows plug into a projector and Linux has to mess and fuss about to achieve the same thing.

---

### Post by benjamimgois on 2009-12-14
> **SonicSteve said:**
> Add my vote to this also. Honestly it's embarrassing, when macs and windows plug into a projector and Linux has to mess and fuss about to achieve the same thing.

+1 , i always get a little embarrased when using a projector...

---

### Post by klim8 on 2009-12-14
> **SonicSteve said:**
> Add my vote to this also. Honestly it's embarrassing, when macs and windows plug into a projector and Linux has to mess and fuss about to achieve the same thing.

Works flawlessly with Intel GPUs (even using the special key in the keyboard). The problem is propietary drivers for ATI and NVIDIA which do not support XRandr 1.2 or higher.

---

### Post by benjamimgois on 2009-12-14
> **klim8 said:**
> Works flawlessly with Intel GPUs (even using the special key in the keyboard). The problem is propietary drivers for ATI and NVIDIA which do not support XRandr 1.2 or higher.

Klim, i have a intel 965G and i still having some trouble. I mean, the image works right away, but the resolution is wrong in the majority of times, so i have to restart the X server with **ALT + PRT SCR + K** for it automatic detect the correct resolution.

---

### Post by Taoye on 2009-12-14
> **soham_1207 said:**
> Seamless integration with external display.

Yes! I want this, too. It is indeed embarrassing when a Windows machine can do this but my Linux machine can't.

---

### Post by phillw on 2009-12-14
RAID on behalf of those with servers, otherwise --- STOP -- it works fine :popcorn:

What some are considering is 'look and feel' - I don't give a monkeys about that - I can go get a skin. I want a bomb-proof OS that measures its up-time in months, not hours.

Just my $0.02

Phill.

---

### Post by jwssr on 2009-12-14
bluetooth working with  pulse audio......

are we going to use blueman or gnome bt?  I prefer blueman...but on past karmic topics...ubunut was down on blueman because of some tecnical questions...

I use BT and am developing BT apps for voip(asterisk & freeswitch) using sflphone (uses pulse...but right now BT is broken)

I am counting big on 10.04 and PA and BT....

Thanks to all developers for their diligent work.....

---

### Post by A_M_S on 2009-12-14
Making the wireless management more robust. 

After countless hours of experimentation i managed to put my wireless interface almost 100% functional (i still have random disconnections sometimes).  

IMO this is  a big problem that intimidates many newbies (even with the great support by the online community ) to migrate definitely to linux.

---

### Post by vishalrao on 2009-12-15
I dunno if it has already been posted in here, but one item would be "better/full support for SSDs - TRIM etc" right from the installer/partitioner to the regular filesystems (ext4/btrfs etc)... is there some place i can go file a feature request and help testing?

---

### Post by SonicSteve on 2009-12-15
> **benjamimgois said:**
> Klim, i have a intel 965G and i still having some trouble. I mean, the image works right away, but the resolution is wrong in the majority of times, so i have to restart the X server with **ALT + PRT SCR + K** for it automatic detect the correct resolution.

I didn't know the keyboard shortcut above, I'll give a try. To clarify I can get the video out going but the image resolution is wrong. It always ends up panning which looks really silly.

---

### Post by simplr on 2009-12-16
Evolution is all right for users who were happy with the limitations of Outlook Express, or perhaps corporate users who are confined to corporate policy. But anyone who relies heavily on email, hates spam, has multiple mail accounts, uses news groups and RSS feeds, and wants the freedom to install add-ons would do much better with Thunderbird. Those same power users will know how to install Thunderbird and so the default mail client can stay Evolution.

It would be nice if Evolution was easier to un-install.

---

### Post by Jordanwb on 2009-12-16
The update manager just hijacked focus while I

---

### Post by alanwalterthomas on 2009-12-16
Fix audio.

More often than not it's horribly scratchy. I have to run killall pulseaudio to run a most games then pulseaudio -D to get it back.

---

### Post by n0glu3 on 2009-12-16
ATI KMS that works on Xpress chips.

---

### Post by longlegs on 2009-12-17
Hi folks,
At present grub, when loading windows, calls the windows bootloader. This requires that I select the grub screen windows choice before the time out, then select it again on the windows loader choice screen before it's time out. It should be possible to have grub setup read the windows choices, and insert them into the grub screen so that I can make one choice to get to the right OS. 
Have a good day!
longlegs

:popcorn:

---

### Post by zengeos on 2009-12-17
On external projector issues...I guess I am not having the problems others have expressed. I have HD3200 video and am using the ATI proprietary drivers. I gave a presentation using OpenOffice just 2 weeks ago, using an external project. not a glitch or flicker.

As with ALL OS's there is bound to be some hardware that is not compatible. Linux has the onus placed upon it that the vast majority of hardware drivers are programmed by the community. Windows and MAC have the advantage that the majority of drivers are actually created by the companies releasing the hardware.

Given this fact, I am amazed at how well my various hardware works in Linux, especially Ubuntu. My network printer got picked up by Ubuntu and many other distros I tried. On Windows Vista I have to download the printer driver from the manufacturer's website, THEN install it, THEN I have to manually configure it because Windows Vista can't seem to do network printer discovery, while Linux can.

---

### Post by Chrisn02 on 2009-12-18
Got a few more for my wish list.
1. Alsa 1.0.22 released recently might be too late/new for this release.  This solves the 9800m hdmi audio problem I had.  
2. Sort of mentioned before in my previous post (see audio volumes) but keeping old setting on update and upgrade.  
e.g. from the other day. I returned to work the other day to find the setting for mounting hard disks without password had reverted back to what it was.  For me its not a big deal I can just change it back but for others it will probably be annoying.  I can't prove it was an update that did this.
3. Perhaps most importantly stability. :)

---

### Post by bronxbomberz41 on 2009-12-18
> **sameer.india said:**
> a snipping tool
i mean i want to be able to select a portion of the screen and save it as an image.
currently i have to take a screenshot then edit the image with gimp
also the selection features similar to adobe acrobat in evince
better support for real media

+1 for a snipping tool!  I recently got upgraded to Vista at work (from Win2000...kind of embarassing for a large company) and one of the few things i actually like and appreciate, and use very often, is the snipping tool

---

### Post by QwUo173Hy on 2009-12-18
This is available already. Just install compizconfig-settings-manager and check the 'screenshot' section under Extras. You might want to have a look to see what the key-binding is for it. I use it all the time and I agree, it's extremely useful.

---

### Post by k3lt01 on 2009-12-18
> **bronxbomberz41 said:**
> +1 for a snipping tool!  I recently got upgraded to Vista at work (from Win2000...kind of embarassing for a large company) and one of the few things i actually like and appreciate, and use very often, is the snipping tool :confused:

> **jarlath said:**
> This is available already. Just install compizconfig-settings-manager and check the 'screenshot' section under Extras. You might want to have a look to see what the key-binding is for it. I use it all the time and I agree, it's extremely useful. :confused:

You don't even need Compiz, Applications > Accessories > Take Screenshot > Select Area to Grab and go for it. It's not all that complicated.

---

### Post by QwUo173Hy on 2009-12-19
k3lt01 - I hadn't noticed that, you're absolutely right.

---

### Post by kaligus on 2009-12-19
** I am still reading but wanted to get my $0.02 in before I get another decade older ;)

1) !!!! SOUND !!!! the kind that works, allows me to run all of my apps and everyone can be heard.  This feature is so 1985 that it makes me sick when my monster powerhouse can not do the simple things my antique Pentium could do.  I should mention while I can that I can run windows in vbox AND regain use of actual audio... [monster tears]

2) a REAL install-uninstall system that actually functions.  I do not care what it is called but when my FIL can call up to beg for help fixing the latest infestation on his windows system and laugh at the fact that I can not just "click remove" and be done with it there is a major problem. (see #1)  An option that is locatable would be good in the event this already exists.

3) support for my web-cam in a chat/IM/etc. app (see above [sigh]) and maybe even just plain as a web cam or to record whatever I want to record.  It is a common webcam sold at electronics stores including the big box kind even with cosmetic changes and OEM names changing it does not function on Ubuntu as anything but a flash drive (I can download what ever I snapped or recorded).  I have tried with many branded cameras with the same USB ID and names people pay 10x what I paid same result.

4) an option to disable the power-down of the screen everytime I walk away to a meeting etc. (that my boss can use if you get my drift... and SEE ABOVE AGAIN)

5) a real web browser that works exactly like the same named browser on that other OS, or one with the same functionality that actually works rather than being all talk no do. (you guessed it... see above)


I am done griping for now because even with these gripes I far prefer Ubuntu to that other OS and those calls weekly from FIL remind of that fact ... just want to take away the 5 reasons he taunts me with so I can smile at him ;)

EDIT: 
+1 for networks shares both directions that don't go away and can be operated by bosses and non-tech henchpersons

---

### Post by Merk42 on 2009-12-19
> **kaligus said:**
> 
2) a REAL install-uninstall system that actually functions.
What is wrong with Add/Remove and Ubuntu Software Center?

> **kaligus said:**
> 3) support for my web-cam in a chat/IM/etc.

What is the specific model? Some of that may come from the driver thing which isn't Ubuntu's fault.

> **kaligus said:**
> 4) an option to disable the power-down of the screen everytime I walk away to a meeting etc. (that my boss can use if you get my drift... and SEE ABOVE AGAIN)
System > Preferences > Power Management

> **kaligus said:**
> 5) a real web browser that works exactly like the same named browser on that other OS, or one with the same functionality that actually works rather than being all talk no do. (you guessed it... see above)
What specifically is wrong with Firefox? How does it lack functionality?

---

### Post by running_rabbit07 on 2009-12-19
> **kaligus said:**
> ** I am still reading but wanted to get my $0.02 in before I get another decade older ;)

1) !!!! SOUND !!!! the kind that works, allows me to run all of my apps and everyone can be heard.  This feature is so 1985 that it makes me sick when my monster powerhouse can not do the simple things my antique Pentium could do.  I should mention while I can that I can run windows in vbox AND regain use of actual audio... [monster tears]

2) a REAL install-uninstall system that actually functions.  I do not care what it is called but when my FIL can call up to beg for help fixing the latest infestation on his windows system and laugh at the fact that I can not just "click remove" and be done with it there is a major problem. (see #1)  An option that is locatable would be good in the event this already exists.

3) support for my web-cam in a chat/IM/etc. app (see above [sigh]) and maybe even just plain as a web cam or to record whatever I want to record.  It is a common webcam sold at electronics stores including the big box kind even with cosmetic changes and OEM names changing it does not function on Ubuntu as anything but a flash drive (I can download what ever I snapped or recorded).  I have tried with many branded cameras with the same USB ID and names people pay 10x what I paid same result.

4) an option to disable the power-down of the screen everytime I walk away to a meeting etc. (that my boss can use if you get my drift... and SEE ABOVE AGAIN)

5) a real web browser that works exactly like the same named browser on that other OS, or one with the same functionality that actually works rather than being all talk no do. (you guessed it... see above)


I am done griping for now because even with these gripes I far prefer Ubuntu to that other OS and those calls weekly from FIL remind of that fact ... just want to take away the 5 reasons he taunts me with so I can smile at him ;)

EDIT: 
+1 for networks shares both directions that don't go away and can be operated by bosses and non-tech henchpersons

File sharing and sound are the only things I could agree with here. But the problems I am having with file sharing stem from the Vista machine, not the Ubuntu machine.

---

### Post by k3lt01 on 2009-12-19
> **kaligus said:**
> 1) !!!! SOUND !!!! the kind that works, allows me to run all of my apps and everyone can be heard.  This feature is so 1985 that it makes me sick when my monster powerhouse can not do the simple things my antique Pentium could do.  I should mention while I can that I can run windows in vbox AND regain use of actual audio... [monster tears] This isn't just an Ubuntu issue, Vista was an absolute SHOCKER when it first come out. None of my hardware would work with it yet it worked beautifully with XP. The reason I looked for another option and found Ubuntu was because of MS's apparent inability to allow my perfectly good hardware to work with the new system when it worked with the old system. So your "so 1985" comment needs to be put in its correct light.

> **kaligus said:**
> 2) a REAL install-uninstall system that actually functions.  I do not care what it is called but when my FIL can call up to beg for help fixing the latest infestation on his windows system and laugh at the fact that I can not just "click remove" and be done with it there is a major problem. (see #1)  An option that is locatable would be good in the event this already exists. Synaptic, Software Centre, Add/Remove, Command Line. How many real options do you want? Not only that with Ubuntu you can actually Uninstall the entire program not like WIndows that leaves things in the registry etc.

> **kaligus said:**
> 3) support for my web-cam in a chat/IM/etc. app (see above [sigh]) and maybe even just plain as a web cam or to record whatever I want to record.  It is a common webcam sold at electronics stores including the big box kind even with cosmetic changes and OEM names changing it does not function on Ubuntu as anything but a flash drive (I can download what ever I snapped or recorded).  I have tried with many branded cameras with the same USB ID and names people pay 10x what I paid same result. See my reply to number 1 above.

> **kaligus said:**
> 4) an option to disable the power-down of the screen everytime I walk away to a meeting etc. (that my boss can use if you get my drift... and SEE ABOVE AGAIN) Merk has answered this extremely well.

> **kaligus said:**
> 5) a real web browser that works exactly like the same named browser on that other OS, or one with the same functionality that actually works rather than being all talk no do. (you guessed it... see above) Would you like to open a thread in ABT or GH about your problems with FireFox?

---

### Post by utnubuuser on 2009-12-19
A new wallpaper?

---

### Post by running_rabbit07 on 2009-12-19
> **utnubuuser said:**
> A new wallpaper?

Gee, now your asking too much.:)

---

### Post by kaligus on 2009-12-21
answers for all.
 

 

 1) I have zero experience with Vista beyond the complaints I hear from others though on an identical piece of hardware my FIL had no problems so I can only *azz-u-me* the problem with my needing to spend hours if not days trying to get audio working EVERY time I have upgraded Ubuntu after tossing out my SB16 is probably an Ubuntu/Debian problem.  

I have not experienced the same level of frustration on similar or identical hardware with other OS choices I have experience with.  

My SB-Live was difficult, my Nvidia on board was difficult, my GigaByte onboard is still difficult, my c-media was difficult... ALL except the GigaByte have been with me since 6.04, the GigaByte since 9.04.
 
 

2) Add/Remove has in my experience so far NOT removed everything added even when I know for a fact it is no longer being used.
 
 Example: add treeline+~20 additional packages required.  Remove treeline... look still 20 additional packages, nothin installed or removed in the mean time.
 
 Synaptic is even worse as I don't think I have ever seen it remove additional packages EVER.
 
 A system which while imperfect like Windows uses even in a flat-file with 1 line per package "package name :: <count-claimed>" where package managers would add a count for each program which references this package, subtract one for each removed, and whne the count reaches 0 the additional package is removed has worked very well on other Linux family OS so it makes sense to me that it couldbe implemented on Ubuntu.
 

 
3) The camera is listed in lsusb as "Bus 001 Device 029: ID 04f2:a216 Chicony Electronics Co., Ltd" but I have seen this EXACT string returned for cameras (none of which work) with names such as Vivitar on them.
 
I am sure it is not an Ubuntu problem specifically but there is no easy way to get support added (I have personally contacted V4L with zero response of any kind so far, but regular-average-user is not going to go through that, they are going to complain to the manufacturer who will promptly blame Linux and resolve to never support their product on Linux.
 
 > side note: business-1010 (or 101 for the old school people) states that the complaint will say “your product doesn't work on Linux” the boss sees it as "well, everyone hates Linux so we should not support it"
 
 The boss of what ever company always believes their product  is perfect and any complaints must be the fault of what ever word stand out most in the complaint.   
 
 Linux already has the fudpackers against it so that word leaps off the page and the boss immediately falls on it as the obvious cause of the nasty message on his/her desk.
 
 Thus Linux is further demonized and my chances of ever seeing support are lowered
 If there were an easy way to at least get the message moving in the right direction that would be as good as getting support added :)
 

 
4) my power-management settings have been set to "never" since 8.04 yet my screen still blanks after a certain time unless I take further steps to prevent it including writing boot-time scripts.  AND with 9.10 my boot-time script throws an error “can not disable power saving” from setterm and still blanks after a while anyway (though I have not rebooted since trying my newest idea).
 

 
5) I have not been able to use firefox out of the box since 8.04 to view online media, play browser games, etc.  I can usually use epiphany for most of those things, but to get all of them I need to either run vbox+windows or firefox+wine, and sometimes only vbox+firefox solves the problem period.
 
 9.10 has made Epiphany not work on some of them but I have not played to find a solution if any yet.
  Again average users will refuse to take these steps.
 


I do not care if anyone chooses to use ANY OS or not, but I do care when they are contributing to the bad name my choice gats in a manner which may (and I have seen it do just his in the case of both software and hardware developers) affect me adversely later on.

---

### Post by jerrylamos on 2009-12-21
Improvements?

Don't break xorg!

I've got intel video graphics i845. kernel 2-6-32-9 update kills xorg!  Again!

And of course all the launchpad tools like ubuntu-bug and apport are dependent on xorg running!

lucid not much use with a black screen.

Thanks much, jerry

---

### Post by ranch hand on 2009-12-21
Jerry
That is why we are here, to have this breakage so that it can be fixed for the release that is a LONG way off.

More reporting testers mean a more stable release.

---

### Post by CJN on 2009-12-21
Obviously as an apple user I'd like the gptsync package updated to the current debian version so that every update to GRUB2 doesn't blow up.

Also I'd like sound that works without updating alsa drivers every-time I update my kernel, once should be enough I think, or not at all but I don't see that happening soon.

Further one thing that I don't *think* is currently possible is *installing* software/drivers/etc while running a live cd, and I really think this would be useful for DEMONSTRATION purposes, at least in some sort of simulated way or something, because right now I tend to have the best luck and run into a lot of computers that don't play nice with the live DVD.

---

### Post by michael37 on 2009-12-21
> **Hellow said:**
> Thunderbird 3 was released earlier last week. It does indeed look awesome; I pulled it from the Mozilla Daily Build PPA found at.

Thunderbird 3, definitely.  With all the extension support, especially Lightning (if it is released on time).

---

### Post by darkzlayer on 2009-12-22
Smaller buttons and menus. Like window$' and mac. (That'll make Ubuntu modern-looking) :)

This can attract more users(as what I've experienced).

---

### Post by cariboo on 2009-12-22
> Further one thing that I don't *think* is currently possible is *installing* software/drivers/etc while running a live cd, and I really think this would be useful for DEMONSTRATION purposes, at least in some sort of simulated way or something, because right now I tend to have the best luck and run into a lot of computers that don't play nice with the live DVD.

It's possible now, give it a try. If you install video drivers you should be able to just log out and back in again. All other drivers just restart the service. You can even reset a Windows password by installing one small program.

---

### Post by Gina on 2009-12-22
If you use a USB memory stick and put the Live CD (Desktop) version onto it you get "Persistence",  You can load apps and set them up as you like and next time you boot from it you have everything there.  You can use it as a normal system except that it's slower and you can easily run out of space.  I use one as a working system when I've "borked" my system totally in testing :lol:  Also, for recovery sometimes.

---

### Post by seeker5528 on 2009-12-22
> **CJN said:**
> 
Further one thing that I don't *think* is currently possible is *installing* software/drivers/etc while running a live cd, and I really think this would be useful for DEMONSTRATION purposes, at least in some sort of simulated way or something, because right now I tend to have the best luck and run into a lot of computers that don't play nice with the live DVD.

If you have a working internet connection, installing software is not a big deal. Drivers may take a little work possibly having to load modules and in the case of video drivers you may need to stop the X session and do some stuff so not necessarily as simple as one might like. If you have a specific use, there are tools for creating custom live CDs.

I don't remember the name of it off the top of my head, but at least for a while, there was a distribution designed completely around the live CD/DVD session, which would let you add and remove software, change configurations, and had the option to write those things and any personal data created back to the CD/DVD, but that takes a whole different kind of design philosophy. It was cool at the time and if your whole distribution is base around the live CD then the effort to maintain the management tools makes sense. 

While there are still many computers out there that don't boot from USB, there is some expectation that most new and recent computers should be able to boot from a flash drive, so that seems like the way to go these days.

With DVD you have the issue that some drives will only read DVD+ or DVD-, but any drive in the last year or two should read both and while the live session seems to be the same as the CD, you do have .deb files availaable for the stuff in main, so there is a fair amount of additional stuff available without having to have an internet connection.

Later, Seeker

---

### Post by KrazyPenguin on 2009-12-22
Smart Backups
example:
I copy a photo to my computer, my computer KNOWS this has to be backed up.
It backs it up to 2 different cloud servers automatically, i don't have to do anything, i don't have to worry about it, if one of the clouds loses my backups, the other one still has them lol  Can never have enough backups -- everything is done automatically even /home directory, so it is always there and synced , etc

And my second improvement would be "I THINK IT AND IT HAPPENS" , who wants to type all the time anyway or use a mouse???  That's old school stuff. LOL

And how about automatically connecting me to the internet and then checking my email and sorting it out for me, actions, waiting fors, archives, etc gtd?????
Do it for me, that would really be getting things done.
Need some kind of artifical intellenge hooked up into this thing,  you know!!!!
if the aliens are controlling the Obama administration, why can't they share their tech????

Faster boot, grub2 sucks so get rid of it!!!!!

Customized desktop so maybe a nice DVD ubuntu version with the choices on it, click click click and it sets everything up in one shot.

i don't use evolution, so why install it????
Go with Chrome, firefox is too bloated to be part of Ubuntu.

---

### Post by hansheijmans on 2009-12-22
I didn't have the time to read the whole thread, so I probably missed something, but here's my wish list:

1. the possibility to have digital audio output using all varieties of media players and analog audio (e.g. using internal speakers) when listening to YouTube or other flash related sites --> SIMULTANEOUSLY. Using *sound preferences* I'm only allowed to choose between either of them (I didn't have this problem in 9.04).

2. Better support for N-draft wireless adapters. I still cannot use my Netgear WN511N at full speed (see my other thread [http://ubuntuforums.org/showthread.php?t=1348884 ]("http://ubuntuforums.org/showthread.php?t=1348884"). Actually I don't understand why it's still called *draft* as it's been on the market for years now!

3. A good replacement for Skype, with the ability to contact Skype users. I know it is not in the repositories but I used the current version 2.1.0.47, retrieved from the Skype ppa, on Windoze when I was still wearing dipers! This version also lacks a great amount of stability. I also don't understand why Mr. Skype isn't able to port the latest version (4.x something, with the much nicer interface) of its application from OSX to Linux. I thought OSX is some sort of *BSD and much alike other Linux distros?

4. Just a few more themes included in the standard install, although I don't consider this a problem. This could be an advantage for the less experienced users to nicen up their desktop and make them switch easier from mickeysoft to Linux.

5. Make *hibernate *and *suspend *work on Dell Latitude laptops (like mine) :)

Greetings from Holland...

---

### Post by Shibblet on 2009-12-22
I'd like to see the kernel option for BFS.  But make it optional.  Even if it requires downloading a secondary patched kernel.

---

### Post by KrazyPenguin on 2009-12-23
Forgot to add:
Replace Tomboy with gnote.

I just tried gnote today, and was inmpressed at the speed difference.
gnote opens immediately , there is no 2 second wait!!!!!

And i copied my notes from tomboy to gnote and they all worked.

;-)

---

### Post by Gourgi on 2009-12-23
> **KrazyPenguin said:**
> 
Replace Tomboy with gnote.

does it support U1 notes sync?
if not then is a no-go to me :-D

---

### Post by zekopeko on 2009-12-23
> **KrazyPenguin said:**
> Forgot to add:
Replace Tomboy with gnote.

I just tried gnote today, and was inmpressed at the speed difference.
gnote opens immediately , there is no 2 second wait!!!!!

And i copied my notes from tomboy to gnote and they all worked.

;-)

Gnote doesn't have a Win and Mac client. So for people that are stuck on Win or Mac the only way to view notes is by having them synced with U1 and going to the website.
And 2sec isn't a big deal since it only happens on a warm start. Later it's just as fast.

---

### Post by kmh.putta on 2009-12-23
I want Lucid to turn on automatically from hibernation at a specified time and do a task. This can be done very easily in Windows. This is the only thing that is tying me to Windows. If Lucid solves this, I'll be an Ubuntu user for life!

---

### Post by Jordanwb on 2009-12-23
> **kmh.putta said:**
> I want Lucid to turn on automatically from hibernation at a specified time and do a task. This can be done very easily in Windows. This is the only thing that is tying me to Windows. If Lucid solves this, I'll be an Ubuntu user for life!

When the computer is hibernating it is turned off. Perhaps you meant sleep mode?

Update Manager just hijacked focus again.

---

### Post by running_rabbit07 on 2009-12-24
> **Jordanwb said:**
> When the computer is hibernating it is turned off. Perhaps you meant sleep mode?

Update Manager just hijacked focus again.

I don't understand the hard part about running Update Manager at any time. It takes seconds.

---

### Post by slumbergod on 2009-12-24
> **Robin Nixon said:**
> Networking - Networking - Networking!

Make it so I can connect to any network drive anywhere I'm allowed and STAY connected after a restart WITHOUT having to edit any config files. I mean, let this all happen with point and click the way other operating systems such as, well, OS X and Windows allow, for example :)

Agreed. Wireless in Karmic is terrible. 

Also, give me back a decent gdm log in window not this clunky mess we have now.

---

### Post by running_rabbit07 on 2009-12-24
> **slumbergod said:**
> Agreed. Wireless in Karmic is terrible. 

Also, give me back a decent gdm log in window not this clunky mess we have now.

Having stitch greet me at sign in would be awesome.

---

### Post by KrazyPenguin on 2009-12-24
> **zekopeko said:**
> Gnote doesn't have a Win and Mac client. So for people that are stuck on Win or Mac the only way to view notes is by having them synced with U1 and going to the website.
And 2sec isn't a big deal since it only happens on a warm start. Later it's just as fast.
1st of all I didn't ask for your opinion did I??
2nd - i don't care about mac or win
3rd - it is faster

have a nice day ;-)

---

### Post by KrazyPenguin on 2009-12-24
Oh ya, I forgot to mention U1

Well for me U1 sucks!!! There is a bug that uses 100% CPU , check launchpad, U1 is in beta still, it needs work, dropbox is better, and it is cheaper and it works.

---

### Post by Amaranth on 2009-12-24
Hostility is not a useful way to get your point across. It is, however, useful if you want everyone to ignore you completely. Please remember the Code of Conduct when posting in the future.

---

### Post by zekopeko on 2009-12-24
> **KrazyPenguin said:**
> 1st of all I didn't ask for your opinion did I??
2nd - i don't care about mac or win
3rd - it is faster

have a nice day ;-)

1. So what if you didn't? It's a public forum. I can replay to your posts all I want. Just as you can to mine.

2. I do.

3. Loads plenty fast on my netbook.

---

### Post by running_rabbit07 on 2009-12-24
Can't we all just get along. Counter productivity is not productive.

---

### Post by zekopeko on 2009-12-24
> **running_rabbit07 said:**
> Can't we all just get along. Counter productivity is not productive.

Read my replay to his "replace Tomboy with Gnote" proposition.
I would say it was pretty productive and informative.
He/she could have politely replied and refuted my arguments. Or asked further questions that I would happily replay to.

---

### Post by KrazyPenguin on 2009-12-25
> **zekopeko said:**
> Read my replay to his "replace Tomboy with Gnote" proposition.
I would say it was pretty productive and informative.
He/she could have politely replied and refuted my arguments. Or asked further questions that I would happily replay to.

The question is "Re: What improvements would you like to see in Lucid?".

Your so called opinion on the subject is irrelevant, since you can't answer that for me.
Unless your suppose to analysis what improvements people want and then either ok it or not ok it.
Maybe you are God?? I didn't know your suppose to read my mind!!!!
I thought this thread was a list of ideas, not to put down somebody elses ideas, because an improvement to me might not be one to you.  Everybody will give you different answers which is what choice is.

---

### Post by zaphod777 on 2009-12-25
Guys how about we keep this civil. state your idea / improvement and go on with your day no need to fight lets keep this constructive.

---

### Post by gnomeuser on 2009-12-25
> **running_rabbit07 said:**
> Can't we all just get along. Counter productivity is not productive.

The thing is that when someone proposes unreasonable changes based on false assumptions or bad evidence, then goes on to attack people for engaging in debate on the matter.. apeacement is not a good tactic for the community long term. Certain uninformed people are best faced with evidence and if needed ridicule (though such people seem to produce that themselves). 

Should we also "just get along" with people who claim the Earth is flat. No, of course not, we should present the evidence why they are wrong even if it hurts their feelings. If they decide to engage in ad hominem attacks rather than honest debate then they have no place posting here, it is not a soapbox, it is a forum. In a forum you debate, you don't assert, you open your ideas to criticism.  

That being said, I added KrazyPenguin to the ignore list as he has proven that he has nothing of value to contribute to the debate currently. Peace at last.

---

### Post by QwUo173Hy on 2009-12-25
> **gnomeuser said:**
> uninformed people are best faced with evidence and if needed ridicule

Evidence, certainly. Ridicule? I think not. Low-level activity such as ridicule does not lead to healthy outcomes for all involved.

---

### Post by MarkX on 2009-12-25
1) FIX THE ^*^% RESOLUTION PROBLEMS!!!!!
This is a basic horrendous flaw!
There used to be a dialog where you could set the correct monitor resolution that overrides the 25% duff wrongly detected automatic resolution settings.
Some genius (not) decided to sabotage Ubuntu and not make it possible for people to set the correct resolutions. I say "sabotage" because every release this is broken in a different way, so the longwinded console fixes keep getting obsolete. Even windows 3.11 was better on this.

2) An intelligible way to give yourself permission to access your own damn drives and files. This includes the "Lost and Found" files. I don't care what's in them but I need to be able to see any content or it's just a hiding place for spyware. Hidden stuff aint' "Open source".

3) FFS grow up and do a windows theme as an option (preferably default). Not having one isn't "different" it's just stupid. Hard enough for noobs to change over without making life even more difficult.

4) What genius put the "shut down" button in EXACTLY the wrong place???
It's where people click to shut down normal windows, it don't mean they want to shut down the puter.

5) Before you "developers" get your jollies with your own inane pet projects, sort out the simple stuff

Plenty more but that would be too much for "developers" to cope with all in one go.

---

### Post by wil on 2009-12-25
Pulseaudio that works or something in it's place that does.

---

### Post by k3lt01 on 2009-12-25
> **MarkX said:**
> 3) FFS grow up and do a windows theme as an option (preferably default). Not having one isn't "different" it's just stupid. Hard enough for noobs to change over without making life even more difficult.

4) What genius put the "shut down" button in EXACTLY the wrong place???
It's where people click to shut down normal windows, it don't mean they want to shut down the puter.So you want the Shut Down button concealed in the Start button? That's how Windows does it! What genius thought that idea up?

I think Gnome has the "Window" sorted pretty well, the only thing I think is a "problem" is the panels take up a bit of room on smaller screens so it would be nice to be able to resize them proportionately.

---

### Post by reiki on 2009-12-25
I'd like to see policykit working.... unlike the broken piece of crap in Karmic :)

---

### Post by bapoumba on 2009-12-25
Shh.. Happy times everyone :)

---

### Post by ranch hand on 2009-12-25
> **k3lt01 said:**
> So you want the Shut Down button concealed in the Start button? That's how Windows does it! What genius thought that idea up?

I think Gnome has the "Window" sorted pretty well, the only thing I think is a "problem" is the panels take up a bit of room on smaller screens so it would be nice to be able to resize them proportionately.
If you cursor onto one of your panels and right click you ca nthen click on "properties".  There you can uncheck "expand and the panel will be just the width to hold what is on it.  You can also change the height of the panel by changing the pixel count.  Auto hide is also an option.

---

### Post by hansheijmans on 2009-12-25
> **bapoumba said:**
> Shh.. Happy times everyone :)

I totally agree. Merry Christmas!!

May the Ubuntu be with you!

---

### Post by hansheijmans on 2009-12-25
In addition to one of my previous posts:

6. Somehow when playing music in Totem or Exaile, there's no way to display the bitrate of the playing file or internet radio stream. This piece of information just disappeared with the upgrade from Jaunty to Karmic. I hope the correct information will be shown in Lucid.

---

### Post by MarkX on 2009-12-25
> **hansheijmans said:**
> i totally agree. Merry christmas!!

May the ubuntu be with you!


well no! I've just wasted most of it unsuccessfully trying to get the right &%^&* undetected resolution on my monitor because nobody at Canonical thought about ways of setting them manually. And it's not the first time either

---

### Post by v1nsai on 2009-12-25
> **MarkX said:**
> well no! I've just wasted most of it unsuccessfully trying to get the right &%^&* undetected resolution on my monitor because nobody at Canonical thought about ways of setting them manually. And it's not the first time either

Okay fine, how about 'may the xrandr -s yourxresolution be with you' then?

Also, would like to see the intel graphics drivers fiasco that's been going on since Jaunty fixed.  My display is still unclaimed in Lucid :(

---

### Post by k3lt01 on 2009-12-25
> **ranch hand said:**
> If you cursor onto one of your panels and right click you ca nthen click on "properties".  There you can uncheck "expand and the panel will be just the width to hold what is on it.  You can also change the height of the panel by changing the pixel count.  Auto hide is also an option.LOL, I do know how to do that. I already have them as small as I can get them. That is why I posted what I posted.

---

### Post by ranch hand on 2009-12-25
In that case, just how small is your screen.  Must be tiny.

---

### Post by phillw on 2009-12-25
::SIGH::

Why not get a computer that works, then ? They do make them. 10.04 is a TEST system, it is NOT a 'working release'. Is your problem to do with nvidia or ati video cards ? Some of those cards a persistant problem causers - others run sweet.

[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459) Is a good place to head.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)  covers stuff on recovering from boot problems with cards.

The rage about video card support will continue until and unless the manufacturers of video cards that you pay good money for - which is HARDWARE - allow YOU to put them into the computer of YOUR choice.

But, I  guess, with the 'race' between ATI & nvidia we shouldn't expect them to allow that any time before hell freezes over. I HATE commercial politics - one of the reasons I came over to Linux in the 1st place. So, I guess those wanting video cards should take a look-see at which ones work well and, as importantly, which ones are a pain in the ***.

If you've gotten a working solution for your rig, then please post it - save some other poor soul going through the hell you've been through.

Regards,

Phill.

---

### Post by k3lt01 on 2009-12-25
> **ranch hand said:**
> In that case, just how small is your screen.  Must be tiny.It really doesn't matter how big my screen is does it? It's just something that could make the Ubuntu experience a little easier in certain situations.

Unlike many others, I don't think Ubuntu has any major problems that stop further improvement in overall look and feel. However I wouldn't class myself as a "power" user either, I'm more of an everyday John Doe who would like his PCs to be easy to use.

The point of feeling the Panels could be smaller comes from using many different PCs, even though mine are all Ubuntu, doing the same things on each PC and some things are easier on Windows simply because some programs or websites have to be scrolled so you can see the bottom of the page.

---

### Post by QwUo173Hy on 2009-12-25
I'm always told that size matters.

---

### Post by Gina on 2009-12-25
I've never found anything easier in Windows - usually harder!  And as for screen real-estate, you can always cut out one of the panels and use just one - or go full-screen in the app.

---

### Post by k3lt01 on 2009-12-25
> **Gina said:**
> I've never found anything easier in Windows - usually harder!  And as for screen real-estate, you can always cut out one of the panels and use just one - or go full-screen in the app.Firefox had a full screen problem a few distributions ago, Hardy I think it was, that stopped me from accessing Pidgin easily. I also like having both panels easily accessible so I can do other things. They call it multi-tasking.

Like I said before I think Gnome has the desktop sorted pretty well (i.e. I don't see the need to change what is actually on the screen) the only thing I would like to see is how it sits on the screen. Adjustability is the key for me. I realise not every wants it or needs it but it is a suggestion.

I remember reading threads ages ago with people saying they would like to be able to add extra folders to the Places menu without it putting things in a Bookmark menu. There were people who made comments like "you can always do this or that" and "is it to hard to make that extra click?" etc. yet what do we have now in Karmic? A places menu that is easily added to without resorting to going to Bookmarks.

The point of the last paragraph is, I like many others are making suggestions to help Ubuntu. Most of us don't need or want "help" to do things another way, if we did we would post a thread in the appropriate section asking for help.

---

### Post by BilliShere on 2009-12-28
I would absolutely love to see better battery life! 
Even windows vista lasts longer than ubuntu on my laptop's battery...*sigh*

also flashier, sexier icons would really reaaallly help the aesthetics and appeal of ubuntu. that's practically what makes osx look good too.

---

### Post by tgpraveen on 2009-12-28
> **billishere said:**
> i would absolutely love to see better battery life! 

+100000000000000000000000000

---

### Post by ezsit on 2009-12-28
MarkX wrote:
> An intelligible way to give yourself permission to access your own damn drives and files. This includes the "Lost and Found" files. I don't care what's in them but I need to be able to see any content or it's just a hiding place for spyware. Hidden stuff aint' "Open source".

This is a typical Windows user's response to Unix/Linux style permissions. Once you get over the whole user / root distinction, this complaint should explain itself away.

---

### Post by QwUo173Hy on 2009-12-28
I don't understand why those lost+found folders are even presented to non-root users. If there is a root / user distinction then why not respect it in the file browser?

---

### Post by ranch hand on 2009-12-28
> **jarlath said:**
> I don't understand why those lost+found folders are even presented to non-root users. If there is a root / user distinction then why not respect it in the file browser?
Because you need to know they are there.

I don't like the files "hidden" in the home folder.

With "nautilus-gksu" available I do not understand the problem here at all.

---

### Post by ezsit on 2009-12-28
Actually, a regular user does not need to know any folder or file exists other than their /home/user folder and the contents of that folder only as it relates to what the user "should" be able to modify or change with complete safety. 

All the hidden files and folders in a user's /home folder are not files and folders that the user "should" be messing with or deleting. 

The Linux/Unix file system hierarchy is not something the regular user needs to see or understand IF the system works properly. However, for trouble shooting purposes, its nice to see what's inside the file system.

To those who are naturally suspicious, if a folder cannot be accessed, nor its contents modified, by regular users, then it is not a place to worry about the collection of harmful software since only ROOT can write to the folder. As for the open source nature of the Linux/Unix file system hierarchy, it is always wide open to ROOT! Just use your root password and have all the access you want.

---

### Post by ranch hand on 2009-12-28
I admit to not knowing what to do with some of the files (lots actually) but I do want to be able to see them and get into them.  This was a major factor in my switching.

That, however, does not mean that I advocate running as "root".  File access is easy enough in Ubuntu, as it is, if you are smart enough to read.  If not you should probably stay out of them anyway.

I like the "sudo" system and prefer it to the root password of most other flavors of linux.

---

### Post by phillw on 2009-12-28
>  I like the "sudo" system and prefer it to the root password of most other flavors of linux.+1

I have got su *root* disabled - more of a security consideration for the server - but I don't miss it. ```
sudo !!
``` is really kewl for when a command reports back permission problems ;-)

We all like the joke, but i prefer this version

$ Go make Some Toast
<<- Go make your own
$ sudo !!
<<- Oh, okay then

:-)

Phill.

---

### Post by PsychoDevon on 2009-12-28
someone may have already suggested this, but, I have had problems with copy and pasting text in Karmic Koala.

If I copy something from say, Firefox, and I want to paste it somewhere else, if I close Firefox, the text I copied is removed from the clipboard, so I can't paste it. It's small, but still counts imo.

---

### Post by PsychoDevon on 2009-12-28
> **phillw said:**
> 
$ Go make Some Toast
<<- Go make your own
$ sudo !!
<<- Oh, okay then

:-)

Phill.

There's a joke about that on xkcd.

[IMG]http://i49.tinypic.com/2yyqequ.png[/IMG]

---

### Post by kaligus on 2009-12-29
> **psychodevon said:**
> someone may have already suggested this, but, i have had problems with copy and pasting text in karmic koala.

If i copy something from say, firefox, and i want to paste it somewhere else, if i close firefox, the text i copied is removed from the clipboard, so i can't paste it. It's small, but still counts imo.
+1

---

### Post by ranch hand on 2009-12-29
That has been a "feature" for a long time.  This is true of any app you close, not just FF.

I would not suggest holding your breath on this one.

I would suggest not closing something you are trying to copy from.

---

### Post by autark on 2009-12-29
> **ranch hand said:**
> That has been a "feature" for a long time.  This is true of any app you close, not just FF.


The gnome-clipboard-daemon is supposed to take of this issue, and it seems to work with gedit. I just tried this (on Jaunty), and it worked: the clipboard was preserved after I had closed gedit.

However, until quite recently Firefox did not use the daemon, so the Ubuntu-packaged versions do not yet benefit from it. You can expect better things of FF 3.7, though. See [https://bugzilla.mozilla.org/show_bug.cgi?id=311340](https://bugzilla.mozilla.org/show_bug.cgi?id=311340) for more details.

---

### Post by Rackstar on 2009-12-29
I would like to see (however unlikely) a new policy for config files. Instead of dropping them all in /home/user/, they should place them all in /home/user/.config/ (or better solution?). 

It would speed up loading your home directory (and improving the use for the user, as many users probably see this as a OS-directory, not a personal one, in contrast with the name)

(Yea, 200 beans!)

---

### Post by oneindelijk on 2010-01-28
Installation of multiple softwares from the software channel could go faster, if the OS would start the download from the next item when the first item finished (but is still being applied and configured)

---

### Post by Herman on 2010-01-31
Now that we can use GRUB2 to boot an .iso file in our file systems, it would be nice to be able to use that .iso file to install Ubuntu with in another disk without the need to burn it to a CD first. 
 I have an SSD drive that I sometimes plug into my Desktop computer by SATA cable and other times pop into an USB external case and boot in other computers.
My Ubuntu .iso files are also inside that disk where I can keep sharing them with transmission bittorrent client when my regular Ubuntu operating system is running.
 
 With the SSD disk in a USB enclosure plugged into another computer I tried booting an .iso file to install Ubuntu in an internal hard disk but I couldn't complete the installation. 
 I tried several times but every time the installer proceeded nicely all the way to the part where it offers the documents and settings migration assistant, which was very good and I was really happy. 
 But then the installation fails because the migration assistant can't mount the loop mounted file system, (or something like that). I didn't want to use the migration assistant anyway on that particular occasion. I have no objections against the migration assistant, but I would have been happy if I had a choice to be able to proceed with the installation without it. 
It would be even better if the migration or whatever it uses to mount the other file systems could be improved so it will to work or decide by itself not to work in that kind of situation and allow the installation to complete.
 
 I have no idea if it's an easy thing to achieve or not, but I hope it's something small and easy to fix.

---

### Post by vishalrao on 2010-01-31
I was hoping KDE progress bars would have smooth animations but sadly looks like it may be only for 4.5 at the earliest: [http://lists.kde.org/?l=kwin&m=126493325916099](http://lists.kde.org/?l=kwin&m=126493325916099)

Also see my attempts at a patch here: [http://www.youtube.com/watch?v=zrvCprVHqag](http://www.youtube.com/watch?v=zrvCprVHqag) :)

---

### Post by sleepee on 2010-02-10
speaking as somebody very new to ubuntu and linux in general, i would love to see bugs fixed..
especially sound bugs.. i don't want to fix one sound problem, only to have another one replace it.
more than any new features, i just want my setup to work.  that's all i ask for..

---

### Post by ranch hand on 2010-02-10
> **sleepee said:**
> speaking as somebody very new to ubuntu and linux in general, i would love to see bugs fixed..
especially sound bugs.. i don't want to fix one sound problem, only to have another one replace it.
more than any new features, i just want my setup to work.  that's all i ask for..
Are you testing 10.04?

I ask because when 9.10 came out a majority of folks having real problems were on hardware that I do not believe was represented in testing.  It is not possible to have things work in the final release on all hardware if all hardware was not tested and bugs filed.

---

### Post by sleepee on 2010-02-10
> **ranch hand said:**
> Are you testing 10.04?

I ask because when 9.10 came out a majority of folks having real problems were on hardware that I do not believe was represented in testing.  It is not possible to have things work in the final release on all hardware if all hardware was not tested and bugs filed.

well, i guess that might be the problem then.. i'm using 9.10 on a relatively new laptop.
but i'm guessing since 10.04 will be LTS, that there should be a focus on more extensive testing and bug fixing.  i'll definitely be upgrading, but i'm not sure i have the time to do much testing and troubleshooting.  i would definitely help in what i can though, since i really like ubuntu and definitely plan on sticking with it.  i just want to see it work.

---

### Post by ranch hand on 2010-02-10
If you read the wiki on the LTS releases you will see that stability is the number one idea.

They do not have all the possible combinations of hardware, however, and if it is not tested they can't fix bugs they do not know about.  That is the short and the long of it.

So far I would say this is going pretty well.  It is kind of boring compared to the last one but that is a good thing.

---

### Post by zika on 2010-02-10
> **ranch hand said:**
> If you read the wiki on the LTS releases you will see that stability is the number one idea.The pure fact that on my machine I'm unable to use KMS for weeks and have to use "nomodeset" to get stable machine is a bit off that goal... With KMS it crushes in minutes or after several hours, but it surely does. Total freeze... Without KMS I'm unable to get it on its knees...  (there is a [thread](http://ubuntuforums.org/showthread.php?t=1347430) about that...)

---

### Post by Merk42 on 2010-02-10
> **zika said:**
> The pure fact that on my machine I'm unable to use KMS for weeks and have to use "nomodeset" to get stable machine is a bit off that goal... With KMS it crushes in minutes or after several hours, but it surely does. Total freeze... Without KMS I'm unable to get it on its knees...  (there is a [thread](http://ubuntuforums.org/showthread.php?t=1347430) about that...)

and Lucid as of this writing, is still an Alpha. What is the state of the filed bug?

---

### Post by ranch hand on 2010-02-10
> **zika said:**
> The pure fact that on my machine I'm unable to use KMS for weeks and have to use "nomodeset" to get stable machine is a bit off that goal... With KMS it crushes in minutes or after several hours, but it surely does. Total freeze... Without KMS I'm unable to get it on its knees...  (there is a [thread]("http://ubuntuforums.org/showthread.php?t=1347430") about that...)
I will admit the it is still rough.

On the other hand you were here for the last round.  About this time (A2) we were trying to figure out, without documentation, how to run the Ubuntu version of grub1.96.  It was not going all that well.

---

### Post by zika on 2010-02-10
> **ranch hand said:**
> I will admit the it is still rough.

On the other hand you were here for the last round.  About this time (A2) we were trying to figure out, without documentation, how to run the Ubuntu version of grub1.96.  It was not going all that well.You remember well... I'm not complaining, just noting where we are... Compared to the same moment in KK testing, we are doing rather well... What buggs me is that this freezeing is, probably, very small, bug somewhere...

---

### Post by ranch hand on 2010-02-10
And plymouth and this mornings fun with the "missing file".

My hardware is not having the freezing problem, never notice KMS.  Firefox seems to me to be the freezing problem here and that, I think is only because of how I keep boinc cranking the cpu's to 99 to 100% all the time.

On my other installs I can open 4 windows of FF with several tabs of animated stuff at once and have it hod up.  Here if I have 7 weather tabs (3 animated radar) on a window and then 2 other windows with static tabs it will freeze at least once a day sometimes several.  I keep doing it though.

Just for the FUN.

---

### Post by goldsniper on 2010-02-12
I hope this is in right category,

My Ubuntu Lucid Lynx 10.04 WISH LIST !

Dear Ubuntu Developer and Ubuntu Community,:popcorn:

This is what I want in my Lucid Lynx 10.04.

1. Native and built-in driver to fully support my Lexmark Z615 inkjet printers.
2. Native and built-in driver to fully support Canon LBP 3050 Laser printer at work!
3. My wife Broadcom wireless adapter worked out of the box- and yes, the current setup in Karmic is problematic.
4. The vboxusers PID problems are fixed!
5. Copy-paste after closing the application worked!
6. Perhaps a free pizza with every Lucid CD's ordered! :D 

Well, I would rant some more, but this would be enough for Lucid! And NO! I don't care about booting in 10 seconds, as long as all my wishes are granted!

---

### Post by ElSlunko on 2010-02-12
Perhaps they could print a pizza over the CD label :P.

I really think they should include parcellite by default for the copy paste issue. What does gnome use by default for copy + paste ?

---

### Post by HomoGleek on 2010-02-12
Its a little bit late for wishlists lol...

But I agree copy + paste has always been a pain in the *****

---

### Post by goldsniper on 2010-02-12
A pizza is superb, but if we have support for those printers is enough for me...:D

I'm just saying they should be a fix for those things..

---

### Post by goldsniper on 2010-02-12
more printers support anyone?

---

### Post by HomoGleek on 2010-02-12
99% of the time its not Canonicals place to fix them, its the companies should provide the drivers. I know there are some workarounds, but usually they're never truly fixed.

---

### Post by goldsniper on 2010-02-12
Homegleek, I know that. And I did using the workaround. You can check on [my blog here]("http://mindaict.blogspot.com/2010/02/my-ubuntu-lucid-lynx-1004-wish-list.html"):KS 

I just think it is wonderful if the workaround are implemented in Lucid.. maybe not all but surely the vboxusers PID can be fixed by us.:P

---

### Post by Kenny_Strawn on 2010-02-12
For the record: I currently have Lucid A2, and Copy/Paste works absolutely fine for me. There is evidence of this on these forums: When I post links to other posts of mine or other threads, I always use Copy/Paste in Lucid, and it works perfectly. So, problem solved.

---

### Post by goldsniper on 2010-02-12
> **Kenny_Strawn said:**
> For the record: I currently have Lucid A2, and Copy/Paste works absolutely fine for me. There is evidence of this on these forums: When I post links to other posts of mine or other threads, I always use Copy/Paste in Lucid, and it works perfectly. So, problem solved.

1. Native and built-in driver to fully support my Lexmark Z615 inkjet printers.
2. Native and built-in driver to fully support Canon LBP 3050 Laser printer at work!
3. My wife Broadcom wireless adapter worked out of the box- and yes, the current setup in Karmic is problematic.
4. The vboxusers PID problems are fixed!
[S]5. Copy-paste after closing the application worked![/S]
6. Perhaps a free pizza with every Lucid CD's ordered!

Thats +1 for you ! I just try it and i'm confirming that copy-paste is superbly functioning in Alpha 2!

Thanks.. now, printers, printers.

---

### Post by vrkalak on 2010-02-12
It's not delivery ... it's Pizza*buntu  \\:D/

Except, of course ... that the Lucid _Lynx_ ate it.

---

### Post by kahumba on 2010-02-12
> 5. Copy-paste after closing the application worked!
```

sudo aptitude install parcellite

```
reboot

---

### Post by Desolathor on 2010-02-12
If they fix the problem with proprietary nvidia/ati drivers would be awesome. Cause currently its the only major flaw in my set up. 

Other than that, GNOME has space for improvement too. A bit more consistency, maybe... they could easily drop multiple tools and replace them with a single one like Ubuntu Tweak.

-des

---

### Post by ezsit on 2010-02-12
Never mind :-)

---

### Post by cariboo on 2010-02-12
> 1. Native and built-in driver to fully support my Lexmark Z615 inkjet printers.
2. Native and built-in driver to fully support Canon LBP 3050 Laser printer at work!
3. My wife Broadcom wireless adapter worked out of the box- and yes, the current setup in Karmic is problematic.

Lexmark does have Linux drivers for their commercial grade printers, I have a C520, that is automagically detected and setup. From the looks of it, they don't care about the consumer grade printers, as it seems they have set the price of ink to be just a little more than the cost of a new printer.

I've emailed Canon a couple of times about Linux support for their printers and scanners, the answer is has been they don't plan on ever supporting Linux.

Depending on what Broadcom chipset you wife's system has, it could be the wrong driver was installed. I just installed Karmic on my netbook with a Broadcom 4312 chipset, it installed the B43 driver by default, I had to black list it, and install the ST driver, and so far I've had a good solid connection, in the three days since I've installed Karmic, I haven't seen signal strength drop below 90%.

---

### Post by Kenny_Strawn on 2010-02-12
> **cariboo907 said:**
> Lexmark does have Linux drivers for their commercial grade printers, I have a C520, that is automagically detected and setup. From the looks of it, they don't care about the consumer grade printers, as it seems they have set the price of ink to be just a little more than the cost of a new printer.

I've emailed Canon a couple of times about Linux support for their printers and scanners, the answer is has been they don't plan on ever supporting Linux.

Depending on what Broadcom chipset you wife's system has, it could be the wrong driver was installed. I just installed Karmic on my netbook with a Broadcom 4312 chipset, it installed the B43 driver by default, I had to black list it, and install the ST driver, and so far I've had a good solid connection, in the three days since I've installed Karmic, I haven't seen signal strength drop below 90%.

That sucks, because my HP printer is perfectly recognized, even over a wireless network.

Edit: Oh, and my Linksys WMP600N PCI adapter is also recognized right out of the box.

---

### Post by crysis on 2010-02-13
ok people put your wishlist for lucid in my thread. ( no complain or problem solving, just wishlist). keep it focused and simple.

so here goes mine.

1. Inclusion of a optional iso image with built-in multimedia codecs,java,flash (like linux Mint). not every-body lives in a crazy country you know :)

2. multiple undo/redo function in default file manager.

3. automatic file icon & icon association with software installation for all possible methods of software installation. and also automatic file icon association change with changing program association. (like OS X, Windows)

4. ability to open file manager with preselected files. (like when using "open file location" in media players, etc)

5. ability to create & delete file/folder in "open file" dialog box.

6. K3b as default optical disk burner optimized for genome (or which ever default windows manager), or any other burner that can create iso/udf bridge discs.

7. a customized IM client that supports voice and video chat over msn and yahoo.

8. free roaming gadget support out-of-the-box like windows 7 in desktop.

9. easy Internet connection sharing option like OS X.

10. out-of-the-box file sharing support with windows/mac pcs (without additional downloads).

11. centralized network and sharing center like vista/win7.

12. out-of-the-box ability to record sound using sound mixer. (record/capture sound that are playing in the same pc)

13. option to have thumbnail grid view in images/videos in "open file" dialog box.

14. abilty to color folders like icolorfolder in winxp.

15. file manager modified to show "computer:///: as the top most location instead of "root, /" so that if u keep doing up u end up in hard drive partitions and liks (dvd etc). this makes single window file browsing more productive & intuitive i guess.

---

### Post by kklimonda on 2010-02-13
But it's pointless at this time - Lucid reaches Feature Freeze in just 5 days so implementing almost anything from this list isn't possible.

---

### Post by emarkay on 2010-02-13
1. Yea, or at least a way to make an ISO from the post-release build (all updates included) and then optionally, with the apps and configs as installed.
2. Yea, is this 1990 or what?
3. Or at least a way to manually config app and file.
4 & 5. I guess, OK by me.
6. YES YES YES, and maybe get it without some of the KDE libs and apps and things that aren't necessary - How about a Gnome default version!
7. Yea whatever - doesn't Skype do that? 
8. What's a "roaming gadget"???
9. See 11.
10. You mean like networking?  Don't get me started - I have been using Ubuntu for 5 years ans I STILL can't get Samba or Samba4 to work ...  And I sort of got flamed for complaining!  I even had a legit Launchpad bug changed to "question/request" - um it does not work!
11. Isn't  that the same thing as 9?
12  I know there are a few apps that can do thins to some extent.  Do you mean like "XVidCap"?  
13. Dunno - got a screen cap or drawing? 
14. Eh, "Dog and pony show", but yea, whatever - should be easy.
15. Yea, OK, that should be an easy app to do, but only if networking is bulletproof in Ubuntu and then across other OS's.

But yea, these and many other good ideas will have to wait.

I still thing usability and functionality and stability should be taken as priority before any "fluff".  There are a bunch of bugs that affect genuine productivity that have been around for a few years that need to be attended to before all the pretty things, IMHO.

---

### Post by k3lt01 on 2010-02-13
> **crysis said:**
> ok people put your wishlist for lucid in my thread. ( no complain or problem solving, just wishlist). keep it focused and simple.Focused and simple? There is already another thread on this, is that focused and simple enough?

Maybe after the feature freeze you should start a thread for the next version (10.10) that way you get the jump on things instead of trying to get stuff a few days before new additions can be made.

---

### Post by Yellow Pasque on 2010-02-13
GTK version of K3B probably isn't going to happen, but it's a nice thought.

About the UDF thing, see: [https://bugs.launchpad.net/brasero/+bug/205919](https://bugs.launchpad.net/brasero/+bug/205919)

---

### Post by 23meg on 2010-02-14
Merged with the larger wishlist thread.

---

### Post by IanW on 2010-02-14
From Crysis' list

1: Have the standard installer offer "ubuntu-restricted-extras" as an option if the user chooses a location that isn't USA.
(Or at least tell the user about it!)
4: Right click on the file. Select "Open with other application". Select "Open Folder" from the list offered.
6: K3B is a KDE app, and is unlikely to be included in a Gnome desktop by default.
7: Pidgin is working towards this

---

### Post by goldsniper on 2010-02-14
> **cariboo907 said:**
> Lexmark does have Linux drivers for their commercial grade printers, I have a C520, that is automagically detected and setup. From the looks of it, they don't care about the consumer grade printers, as it seems they have set the price of ink to be just a little more than the cost of a new printer.

I've emailed Canon a couple of times about Linux support for their printers and scanners, the answer is has been they don't plan on ever supporting Linux.

Depending on what Broadcom chipset you wife's system has, it could be the wrong driver was installed. I just installed Karmic on my netbook with a Broadcom 4312 chipset, it installed the B43 driver by default, I had to black list it, and install the ST driver, and so far I've had a good solid connection, in the three days since I've installed Karmic, I haven't seen signal strength drop below 90%.

Thanks.

I know there are many workarounds to make the printers to function. And I had tried it with success... I just wondering if those workarounds could be implemented by default in Ubuntu installations.

---

### Post by emarkay on 2010-02-14
> **IanW said:**
> From Crysis' list
6: K3B is a KDE app, and is unlikely to be included in a Gnome desktop by default.



That sux when the best app is from "the competition"  Sort of like when the Tucker had the third headlamp...

Come on Gnome folks, get your (Brasero I think?) disfunctional and unintuitive app (something about checksum errors, and 1990 interfaces are so 1990...) to work like K3b! :)

---

### Post by 2hot6ft2 on 2010-02-14
I don't know if there's even such an animal yet but a GUI firewall for managing the ip6tables. Not the iptables but the ip6tables in case you're reading too fast to catch that.
Better networking, frequent disconnects are a pain in the rear.

Other than that just fixing existing bugs since the OS is already killer.

A network manager that supports for multiple simultaneous connections like is supposed to be supported when WICD 2.0 comes it. They already claimed it would be supported in 1.6 back before it came out but it didn't happen. (Not really a ubuntu issue per say but I would like it)

---

### Post by emarkay on 2010-02-15
Wow, a lot of chatter, as well as some good ideas and a few bad apples spoling the thread.

This really needs to be pared - maybe one of the mods can take a bit of time and edit the chit-chat and nastiness and **make this a Sticky**?

---

### Post by HomoGleek on 2010-02-15
> **emarkay said:**
> 
......
This really needs to be pared - maybe one of the mods can take a bit of time and edit the chit-chat and nastiness and **make this a Sticky**?

To late in the release cycle for most of this even to be considered.

---

### Post by jsmanian on 2010-02-16
I would like to have some support in lucid for installing linux version engineering softwares (ansys, pro-E etc..).  As some of these software providers are not supporting Ubuntu, it is hard to find the installing procedure. So if there is any procedure to install these packages (like dependent libraries in synaptic package manager), it will be great.:p

---

### Post by cygnus-X1 on 2010-02-16
**-1 on Chrome.** Google, corporate owned, Microsoft, power-hungry, gobble up the competition mindset. Firefox, like Linux, is independent. That's a plus in and of itself. 

Being able to find apps easier. I'm currently running a 8.04(32)/9.10(64) dual boot, and I find the 8.04 app center **much** easier to customize and navigate. The 9.10 app center is clunky, for lack of a better term. If you don't KNOW what you're looking for. Lotsa luck! 

That's my take as I'm still rather green with Linux as a whole. (BTW - I hope to be rid of ALL win-doh's based OS by summers end. Trying to get winders to play nice in a dual boot system for 5 days was the straw that broke this camel's back!)

*[SIZE="1"]Gigabyte MA78GM-S2HP/X4 945 Phenom II/2GB DDR2/8.04(32) & 9.10(64)[/SIZE]*

[COLOR="White"]-[/COLOR]

---

### Post by HomoGleek on 2010-02-16
> **cygnus-X1 said:**
> **-1 on Chrome.** Google, corporate owned, Microsoft, power-hungry, gobble up the competition mindset. Firefox, like Linux, is independent. That's a plus in and of itself. 



aye ok my son ........

---

### Post by jezza1972 on 2010-02-16
Probably too late now, but pulseaudio does not work on all 4 computers i have in my house. I have to remove it on every one and it has become an unnecessary chore, so please go back to alsa or move onto something else.

Oh and screens and graphics back please. I don't want to be faffing about editing xorg config. Everyting worked in 8.04, and went t*ts up from 8.10.

---

