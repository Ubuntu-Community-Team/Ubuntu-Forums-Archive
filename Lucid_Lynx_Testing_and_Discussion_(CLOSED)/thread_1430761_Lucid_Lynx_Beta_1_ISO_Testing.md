---
title: "Lucid Lynx Beta 1 ISO Testing"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-03-15
Beta 1, which will be the fourth milestone release of the Lucid Lynx development cycle, will be out this Thursday. Like every milestone release, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the release candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

We are in Beta 1 Freeze, and candidate images for Lucid Lynx Beta 1 are now available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by Cam! on 2010-03-15
Nice! I think I'll wait until thursday to download to the Beta, though.

---

### Post by ViperScull on 2010-03-15
Any difference between a fresh install of Beta 1 and a daily aptitude update from alpha 3 ???

---

### Post by 23meg on 2010-03-15
> **ViperScull said:**
> Any difference between a fresh install of Beta 1 and a daily aptitude update from alpha 3 ???

No.

---

### Post by kansasnoob on 2010-03-15
It looks to me like they're into a rebuild. I don't know why, I did report three tiny bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

[https://bugs.launchpad.net/ubuntu/lucid/+source/casper/+bug/539182](https://bugs.launchpad.net/ubuntu/lucid/+source/casper/+bug/539182)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204)

We'll see. Oh Plymouth is still a mess I guess. I boot fine but see no splash.

---

### Post by Speed_arg on 2010-03-15
Now there won't be any new features, just bufixes right?

And there won't be any boot-time imprevements right?

---

### Post by ndefontenay on 2010-03-15
Most likely yes. But you never know. A bug fix could improve the booting time.

---

### Post by ranch hand on 2010-03-16
Every thing just went great for me except for the failure to reboot.  Quite a lot of change in the way the CD works since last time.

---

### Post by ranch hand on 2010-03-16
> **kansasnoob said:**
> It looks to me like they're into a rebuild. I don't know why, I did report three tiny bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

[https://bugs.launchpad.net/ubuntu/lucid/+source/casper/+bug/539182](https://bugs.launchpad.net/ubuntu/lucid/+source/casper/+bug/539182)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204)

We'll see. Oh Plymouth is still a mess I guess. I boot fine but see no splash.
How in flinderation do we know if we need to retest?

I thought the bugger worked pretty well.  CD did not shut down.  I did have to hit Ctrl-Alt-F7 to get to the login.

Other than that it worked very well and even almost booted right.

---

### Post by cookiecruncher on 2010-03-16
> **kansasnoob said:**
> Oh Plymouth is still a mess I guess. I boot fine but see no splash.
Ditto here.

---

### Post by teh603 on 2010-03-16
From looking at some of the bugs I've seen related to Plymouth, its going to be a mess until Beta 2, if not later. The devs are still having trouble tracking down every bug.

---

### Post by katie-xx on 2010-03-16
Im waiting until Thursday before a fresh install.
Re: Plymouth ..you shouldnt expect it ever to be ok. 

Kate

---

### Post by Mawoon on 2010-03-16
The beta should be pretty stable, maybe even plymouth, after all, it is an LTS release, I'm just going to make a 20gb partition for testing purposes. You should wait till at least the release candidate before making 10.04 your primary operating system.

---

### Post by Stason on 2010-03-16
I had no choice due to some hardware upgrade and jumped into Alpha2 straight from Gutsy, so 10.04 is my primary system. Fortunately, only the bootup/plymouth issue is of serious concern to me. Pretty much everything else work great. I am going to check on that recent plymouth update hanging up pc completely during boot before updating to beta though.

---

### Post by ranch hand on 2010-03-16
> **katie-xx said:**
> Im waiting until Thursday before a fresh install.
Re: Plymouth ..you shouldnt expect it ever to be ok. 

Kate
Now now, you shouldn't be so harsh.  They want to put packagekit on here too sometime.

That will make plymouth look a lot better by comparison.

Just think, not able to boot and then not able to get packages in a decent manner.  Good combination.

---

### Post by Irihapeti on 2010-03-16
If I can get the beta to boot at all on my desktop, I shall be happy.

Stuff like what side the buttons are on, pulseaudio, theme colours etc are irrelevant to me until I can boot.

I feel like a starving man wondering why people are fussing about how long the egg has been boiled. :)

---

### Post by VMC on 2010-03-16
> **ranch hand said:**
> Now now, you shouldn't be so harsh.  They want to put packagekit on here too sometime.

That will make plymouth look a lot better by comparison.

Just think, not able to boot and then not able to get packages in a decent manner.  Good combination.

Combine those two and the button, button whose got the button, and we have the making of a Three-Ring-Circus :)

I don't know about packagekit, but I do know about **plymouth**, and hope it will get fixed.

---

### Post by ranch hand on 2010-03-16
Booting, while spotty, is much better than 9.10 at this stage of the game.

I suspect that your install would boot if you removed plymouth.  Whether this is a good testing practice is debatable.

The rest of the bugger seems to work real well compared to 9.10 at RC.

---

### Post by Wa1k3rTXRang3r on 2010-03-16
> **ranch hand said:**
> Booting, while spotty, is much better than 9.10 at this stage of the game.

I suspect that your install would boot if you removed plymouth.  Whether this is a good testing practice is debatable.

The rest of the bugger seems to work real well compared to 9.10 at RC.

I totally agree. Booting was a disaster in 9.10 testing releases. I distinctly remember you personally attempting to help me with my problems ranch hand! Haha. Thankfully, both Ubuntu and I have come a long way since then!

I haven't experienced any serious issues with plymouth so far. Only that the splash screen doesn't display correctly with the current NVIDIA driver active.

---

### Post by VMC on 2010-03-16
> **Irihapeti said:**
> If I can get the beta to boot at all on my desktop, I shall be happy.

Stuff like what side the buttons are on, pulseaudio, theme colours etc are irrelevant to me until I can boot.

I feel like a starving man wondering why people are fussing about how long the egg has been boiled. :)

I remember your topic. Why don't you bump it, so we can work on it some more. There must be someway we can get you booted up.

---

### Post by Irihapeti on 2010-03-16
> **VMC said:**
> I remember your topic. Why don't you bump it, so we can work on it some more. There must be someway we can get you booted up.

I was going to wait until beta1 was out before bumping it. That's only a couple of days away now.

But maybe I should do it now....

---

### Post by qwerty2009 on 2010-03-17
i doubt there even going to fix this startup bug as its been around months now. i want to be able to use lucid and upgrading from karmic isnt an option as i have a slow connection. i dont know what could be causing it as my machine doesn't use nvidia so it cant be plymouth causing the problems

---

### Post by qwerty2009 on 2010-03-17
filled a bug report[https://bugs.launchpad.net/ubuntu/+bug/540100](https://bugs.launchpad.net/ubuntu/+bug/540100)

---

### Post by ranch hand on 2010-03-17
They certainly seem to be pretty serious about getting this bugger to run.   I have to go and do some things but will see about this later when, hopefully, they have the bugger rebuilt - again.

I guess I will not do anymore tweeking on my install.  Get to do it again.  Oh Boy.

Are we having FUN or what?

---

### Post by Irihapeti on 2010-03-17
> **qwerty2009 said:**
> upgrading from karmic isnt an option as i have a slow connection.

If you can get a copy of the Lucid alternate CD, you can upgrade from that.

---

### Post by ranch hand on 2010-03-17
Wow, no rebuild yet.

Anyone got an idea when it may become available?

---

### Post by kansasnoob on 2010-03-17
> **ranch hand said:**
> Wow, no rebuild yet.

Anyone got an idea when it may become available?

I'm thinking we're done. Based on previous experience the actual Beta 1 will show up in about 24 to 32 hours (different sides of the pond) so it's doubtful they'll release another test candidate this close.

I remember one time in Karmic development we had 3 rebuilds in one day, since I zsync or rsync I don't mind, but nine or more "attentive" installs in one day does get tiresome :D

Note: When I say "attentive" I mean just that. I sit here and watch! I normally do installs while multi-tasking, that is I just walk away, but with iso testing I try to watch everything.

I must say that I've seen one heck of an effort from the devs to fix every valid bug possible before this Beta.

I'm impressed.

---

### Post by ranch hand on 2010-03-17
I just checked and they still have most of the stuff crossed off so you must be right.

Guess this means I had better finish setting that bugger up so I can put GS back on it one of these days when I have a moment (I am running QA checks with the Censless).

Yes I think they want the CD to work as well as possible for this release.  Maybe the ones at the end, like B3, RC, Final will work for more folks than last time too.  That would be nice.  You still see some folks having trouble with the 9.10CD.

---

### Post by wjm on 2010-03-17
I found a bug just now in the Live installer from todays build.  Should I wait till tomorrow to bug it seeing as it may be addressed (I haven't looked in launchpad yet)

---

### Post by ranch hand on 2010-03-17
I think I would wait.  They seem to be taking this real seriously.

---

### Post by andrew5859 on 2010-03-18
*[FONT=Book Antiqua][SIZE=3]:D           I'm wondering if there is going to be some kind of coding put into the Lucid Lynx that would allow for the aero glass look...I think this would be a great plus for Ubuntu and would attract more people from other OS's[/SIZE][/FONT]*
*[FONT=Book Antiqua][SIZE=3][/SIZE][/FONT]* 
*[FONT=Book Antiqua][SIZE=3][/SIZE][/FONT]* 
*[FONT=Book Antiqua][SIZE=3][/SIZE][/FONT]* 
*[FONT=Book Antiqua][SIZE=3]Andrew      :D[/SIZE][/FONT]*

---

### Post by Orographic on 2010-03-18
I'm not into that Aero Glass look at all and was with Windows for twenty years before 2008. Each to their own though. Just looking forward to a solid release that will hopefully work well on the new i3 I purchase later this year.

Plan to install the Beta 1 for a looky as well.

---

### Post by Keyper7 on 2010-03-18
> **andrew5859 said:**
> I'm wondering if there is going to be some kind of coding put into the Lucid Lynx that would allow for the aero glass look...I think this would be a great plus for Ubuntu and would attract more people from other OS's

There is technology to allow transparency, but it was considered too unstable for Lucid.

There is a high possibility that it will be included in Lucid+1.

---

### Post by petex on 2010-03-18
so where can I download the beta?

---

### Post by Uncle Spellbinder on 2010-03-18
The official beta is not released yet.

---

### Post by petex on 2010-03-18
will it be released today or do they have a delay?

---

### Post by andrewabc on 2010-03-18
> **petex said:**
> will it be released today or do they have a delay?

Probably today.
Wait until official announcement before downloading even when people start posting download links or say to get daily build. A thread will get stickied showing release info.

Usually doesn't happen for another 6 hours or so

---

### Post by kansasnoob on 2010-03-18
> **wjm said:**
> I found a bug just now in the Live installer from todays build.  Should I wait till tomorrow to bug it seeing as it may be addressed (I haven't looked in launchpad yet)

What was the bug?

---

### Post by kansasnoob on 2010-03-18
> **ranch hand said:**
> I just checked and they still have most of the stuff crossed off so you must be right.

Guess this means I had better finish setting that bugger up so I can put GS back on it one of these days when I have a moment (I am running QA checks with the Censless).

Yes I think they want the CD to work as well as possible for this release.  Maybe the ones at the end, like B3, RC, Final will work for more folks than last time too.  That would be nice.  You still see some folks having trouble with the 9.10CD.

Turns out I was wrong, they did push out a fourth test candidate and the only bug I personally encountered was this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539204)

And I see a fix was just committed on that one so I bet it'll be fixed in the actual Beta 1.

I think the devs deserve a lot of credit for this one. With six weeks until final this should be really great :D

Of course we'll still hear a lot of griping about default this, and default that, but as long as I'm able to configure things the way I like I'm a happy camper.

ATM my post-install mumbo-jumbo:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get install abiword gnome-alsamixer gparted gphoto2 gthumb gtkam gtkam-gimp gufw hplip-gui mozilla-plugin-vlc  vlc-plugin-pulse startupmanager totem-plugins-extra totem-xine ubuntu-restricted-extras gnome-themes-more gnome-themes-extras shiki-colors-metacity-theme gnome-backgrounds nautilus-gksu sensors-applet ntfsprogs libdvdcss2 w32codecs zsync
```

Then a few leisurely mouse clicks to get my default settings the way I like and I'm rockin' :guitar:

---

### Post by ranch hand on 2010-03-18
One of these days I really ought to do that type of automation for my installs.  The problem is that I keep changing things around.  I think, just recently, that I may, finally, have gotten the look and feel the way I really want it.

Then they come up with GS.

---

### Post by anselm on 2010-03-18
Downloaded beta last night, couldn't get it to boot the splash screen would come up than a blank screen with a blinking cursor.

I usually start testing LTS releases during the beta cycle as I only use LTS.

I was wondering should I go ahead and do a clean install as I have seperate home and root partition's.

---

### Post by wjm on 2010-03-18
The blinking cursor you're talking about may just be it booting.  I noticed when I first started using Lucid that this happens during the installer - takes about three minutes IIRC.

---

### Post by zoomy942 on 2010-03-18
does ALT + F7 do anything?

---

### Post by anselm on 2010-03-18
Ok I didn't wait long enough to see if it was going boot to a desktop, it took about 3 min to boot off of the live cd.

Posting this from the live cd.

---

### Post by entangled on 2010-03-18
Just saw that the beta 1 is delayed til Friday now. Sounds like 'Boot time issues'

---

### Post by ranch hand on 2010-03-18
> **anselm said:**
> Downloaded beta last night, couldn't get it to boot the splash screen would come up than a blank screen with a blinking cursor.

I usually start testing LTS releases during the beta cycle as I only use LTS.

I was wondering should I go ahead and do a clean install as I have seperate home and root partition's.
You did not download the beta last night.  The beta1 CD will not be released until tomorrow.

I would wait until then and you may get a very different CD.

---

### Post by ranch hand on 2010-03-18
This ISO is a definite improvement, at least on my hardware.   The only thing weird was the detection of the "package disk" 3 times.

I filed no bug as I am thinking this is connected with my use of an external enclosure (USB) and an external DVDrom.

The boot seemed real slow too but booted fine with only a little flicker.

OS seemed to work well.  Booted very nicely.  Didn't mess with it too much as 10.04 has become too stable to be any FUN.  It is, on this box, almost up with 9.04 which is rock solid.

---

### Post by jeremy1138 on 2010-03-18
Just downloaded and tried the lucid i386 iso.  I booted into a live session without any trouble and installed alongside the existing 9.10 installation without a hitch.  Everything seems to be working perfectly.  I haven't had any problems at all so far.  The only little blemish that I see is that a bunch of text flashes across the screen when I boot up or shut down.  It only happens for a second and I do get to see the new boot splash.  I'm just chalking that up to this being a beta release and leaving it at that.  Other than that everything seems to be working really well.  This is shaping up to be the most visually appealing Ubuntu so far!  The folks working on development of this deserve a pat on the back.  Great job!

(edit)
Oh and I got the same detection of a package disk as the commenter above while the installation routine was running in a live session.  I'm not sure what that was about...

---

### Post by OrangeCrate on 2010-03-18
> **ranch hand said:**
> This ISO is a definite improvement, at least on my hardware.   The only thing weird was the detection of the "package disk" 3 times.

I filed no bug as I am thinking this is connected with my use of an external enclosure (USB) and an external DVDrom.

The boot seemed real slow too but booted fine with only a little flicker.

OS seemed to work well.  Booted very nicely.  Didn't mess with it too much as 10.04 has become too stable to be any FUN.  It is, on this box, **almost up with 9.04 which is rock solid.**

Agreed. I'm running Jaunty in the office (IMO, the best version to date), and Lucid at home, and Lucid feels very solid indeed. For right, or for wrong, I think the devs feel a bit blistered over the response to Karmic, and I personally think that Lucid may very well be the best release ever. We'll see...

---

### Post by ranch hand on 2010-03-18
While I am not real fond of 9.10 I do not think the devs have anything to be really be bothered about it.  They threw the kitchen sink in there so that things would be ready for 10.04.

I think it is paying off.

I wondered at the time about it as they said they did not want to put in much on an LTS.  If they had not done what they did we would be getting much less of an OS this time and still had to put up with plymouth that they may get straight yet too.

Even with plymouth this is a very boring, so far, testing cycle compared to 9.10.  I am always surprised, really, by how good 9.10 is.  Testing was a tough, rough ride on that one.

---

### Post by uRock on 2010-03-18
I love Karmic so much I am not sure I will upgrade all of my machines to Lucid for a while. My wife doesn't like me tinkering with hers since I got it tweaked, if I can prove the Lucid works well with the iPhone she will let me upgrade it. 

I think I was one of the lucky ones testing Karmic, because it worked well on my machine during Beta testing.:D

---

### Post by ticknubbs on 2010-03-19
Anybody have any word or links to the official beta release? I have clicked around through the previous postings in this thread and cant find the iso....

---

### Post by uRock on 2010-03-19
> **ticknubbs said:**
> Anybody have any word or links to the official beta release? I have clicked around through the previous postings in this thread and cant find the iso....

I don't think they have it on the servers yet. Beta1 was delayed and is supposed to be ready later today.

---

### Post by ticknubbs on 2010-03-19
[http://www.ubuntu.com/testing/lucid/beta1]("http://www.ubuntu.com/testing/lucid/beta1")

The iso is up now, I am assuming this is official!

---

### Post by ranch hand on 2010-03-19
All that means is that the page is up.  Wait for the notification.  They need to sync the mirrors and check things out.

Don't get your knickers in a knot.  It is coming.

---

### Post by commonplace on 2010-03-19
I keep seeing people post things like "omg it's out!!!1" and then it gets deleted. From the official sticky:

*Please do not attempt to download Beta 1 before the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/date.html"). The release will also be announced on the forum.*

/Kevin

---

### Post by teh603 on 2010-03-19
They've got things up early. I vaguely remember having to wait until close to midnight for the RC of Jaunty.

---

### Post by grubdude on 2010-03-19
I am downloading Beta 1 right now, so it must be up :-)

---

### Post by commonplace on 2010-03-19
> **grubdude said:**
> I am downloading Beta 1 right now, so it must be up :-)

Okay, right, but are you not reading? Seriously?

**Please do not attempt to download Beta 1 before the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/date.html"). The release will also be announced on the forum.**

---

### Post by uRock on 2010-03-19
> **commonplace said:**
> Okay, right, but are you not reading? Seriously?

**Please do not attempt to download Beta 1 before the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/date.html"). The release will also be announced on the forum.**

They should put that at the top of the UF home page.

---

### Post by grubdude on 2010-03-19
Thats what I get for waking up doing a quick scan without my first coffee. :-). Just realized that after my post..thanks!

---

### Post by commonplace on 2010-03-19
> **iRock said:**
> They should put that at the top of the UF home page.

Oh, definitely.

On the flip side, once the page goes live, what does Canonical expect, really? I don't know how big of a deal it is if people download it "early" or whatever, but I'm holding off to be courteous... but I'm sure plenty of others have already grabbed it, for better or worse.

/Kevin

---

### Post by commonplace on 2010-03-19
> **grubdude said:**
> Thats what I get for waking up doing a quick scan without my first coffee. :-). Just realized that after my post..thanks!

haha, it's all good. It was just that I'd just posted that, and then you posted what you posted.. and I was almost rubbing my eyes in disbelief. But I understand, too. And there's nothing on that download page that says otherwise, which is Canonical's fault/problem.

/Kevin

---

### Post by commonplace on 2010-03-19
The main Ubuntu.com page is inviting everyone to download the beta now, so I guess it's all clear now? So much for waiting on the dev list announcement. Heh.

/Kevin

---

### Post by grubdude on 2010-03-19
yes that is what I saw too....and I discontinued the download darn :-)

---

### Post by commonplace on 2010-03-19
> **grubdude said:**
> yes that is what I saw too....and I discontinued the download darn :-)

Sorry about that. :(  I didn't realize they'd posted that announcement. It really stinks that there is conflicting information being disseminated.

I say to heck with it. If Ubuntu.com says download it, I say download it. I'm starting my download now. :D

/Kevin

---

### Post by uRock on 2010-03-19
I added to my torrents.

---

### Post by grubdude on 2010-03-19
I don't really care because I am running in a virtual machine anyway. If it is hosed I will just install another. :-)

---

### Post by xubin on 2010-03-20
Hi, I have a severe problem here: since alpha2, I can't install Lucid to my Toshiba. I have Kamic working properly right now. And when I try to install from live usb, it fails every time when I see the desktop. By fails, I mean the OS freezes at the desktop, I can't do any operation. I also try to install within WINDOWS 7 by WUBI, but can't even start installation, it stucks at the grub entry. I would really be thankful if someone help me out here, I have been using Ubuntu since 8.04, I don't want to stay in 9.10 forever. Thank you!

---

### Post by 23meg on 2010-03-20
Please start separate threads for your problems. I'm closing this thread, since Beta 1 is released, and ISO testing is thus over. Thanks to all who participated.

---

