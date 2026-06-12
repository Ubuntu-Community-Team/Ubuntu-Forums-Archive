---
title: "Alpha 5 Released"
date: 2008-09-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2008-09-05
[http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)
[http://cdimage.ubuntu.com/releases/intrepid/alpha-5/](http://cdimage.ubuntu.com/releases/intrepid/alpha-5/)


Finally :)

Lee

---

### Post by v1cho on 2008-09-05
Great! :) :popcorn:

---

### Post by v1cho on 2008-09-05
What the ... ?!?! Why are you using the daily builds form the day before yesterday? :confused:
Does it REALLY include kernel 2.6.27?

---

### Post by chris062689 on 2008-09-05
No offense to Ubuntu, but it feels like this release (8.10) isn't as "groundbreaking" as all of the other releases...  :(

---

### Post by dudude on 2008-09-05
I hope the theme for alpha 5 is just a temporary one, because is falls WAY short of some of the other proposed themes. 
For those who care...
[[IMG]http://img529.imageshack.us/img529/1124/ubuntu64bit200809051645lp5.th.png[/IMG]](http://img529.imageshack.us/my.php?image=ubuntu64bit200809051645lp5.png)

---

### Post by perlluver on 2008-09-05
Anyone still confirm the bug of slave drives not mounting?  I will wait till they get that worked out, as all my music and pictures are on the slave drive.

---

### Post by plun on 2008-09-05
> **perlluver said:**
> Anyone still confirm the bug of slave drives not mounting?  I will wait till they get that worked out, as all my music and pictures are on the slave drive.

Well... please read these bugs and maybe add your point....

[https://bugs.launchpad.net/ubuntu/+bug/254098](https://bugs.launchpad.net/ubuntu/+bug/254098)

[http://bugzilla.gnome.org/show_bug.cgi?id=520736](http://bugzilla.gnome.org/show_bug.cgi?id=520736)


This is not a bug today !


Change  [B]Menu System > Administration> > Authorisations  > hal > storage > "Mount file systems from internal drives" > add yourself to the right. 
[/B]

:-k

---

### Post by nanog on 2008-09-05
If you read the announcement (which you always should) its clear that the theme problem is a known bug. 

>  On Ubuntu systems, the default desktop theme is wrong. As a workaround, please select "Human-Murrine" (or another theme of your choice) in System &#8594; Preferences &#8594; Appearance. [https://bugs.launchpad.net/bugs/256972](https://bugs.launchpad.net/bugs/256972)


[http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)

---

### Post by Nullack on 2008-09-05
> **chris062689 said:**
> No offense to Ubuntu, but it feels like this release (8.10) isn't as "groundbreaking" as all of the other releases...  :(

Theres quite a bit of progress you'd find with a more detailed look, such as:

Benefits of linux .26 and .27
Changes with gnome 2.23.x
Upgrades to gstreamer, openjdk and so on

---

### Post by rocknrolf77 on 2008-09-05
Man that theme was ugly [-X

Hoping this alpha will work. None of the others have worked on my 3 computers. This has never happened with earlier releases.

---

### Post by perlluver on 2008-09-05
> **plun said:**
> Well... please read these bugs and maybe add your point....

[https://bugs.launchpad.net/ubuntu/+bug/254098](https://bugs.launchpad.net/ubuntu/+bug/254098)

[http://bugzilla.gnome.org/show_bug.cgi?id=520736](http://bugzilla.gnome.org/show_bug.cgi?id=520736)


This is not a bug today !


Change  [B]Menu System > Administration> > Authorisations  > hal > storage > "Mount file systems from internal drives" > add yourself to the right. 
[/B]

:-k

Ok, but the problem is, I added it to, /etc/fstab, to mount on /media/disk.  It is a jfs volume, which has mounted all the way up to Hardy.  Now it says /dev/sda1, special device does not exist.  It shows up in fdisk -l, but will not mount, and does not get recognized.  So it seems to be a pretty big bug, or a mess up.

---

### Post by Nullack on 2008-09-05
> **perlluver said:**
> Ok, but the problem is, I added it to, /etc/fstab, to mount on /media/disk.  It is a jfs volume, which has mounted all the way up to Hardy.  Now it says /dev/sda1, special device does not exist.  It shows up in fdisk -l, but will not mount, and does not get recognized.  So it seems to be a pretty big bug, or a mess up.

Assuming you created the disk directory ok its probably a bug. Have a look here on how to contribute to Intrepid:

[http://ubuntuforums.org/showthread.php?t=896777](http://ubuntuforums.org/showthread.php?t=896777)

---

### Post by chris062689 on 2008-09-05
> **Nullack said:**
> 
Benefits of linux .26 and .27

Hm?  I tried searching, but I couldn't find any logs, what are some of the new fancy features?

---

### Post by andrewabc on 2008-09-05
Alpha 5 work with virtualbox? I know alpha 4 didn't (so I read)

---

### Post by dudude on 2008-09-05
This probably does not help any, but it works flawlessly (as far as I can tell) with VMware.


Edit: Installing VMware tools seems to keep freezing on me, so I'm having some doubts.

---

### Post by rockin_goliath on 2008-09-06
does anyone know if pulseaudio is set up properly in this release?

---

### Post by Saint Angeles on 2008-09-06
ok so i'm doing an upgrade right this minute!

i'm excited for some new software! i was getting bored with the way everything on hardy worked all the time.

---

### Post by shafin on 2008-09-06
Has MySQL started working again?

---

### Post by Nullack on 2008-09-06
> **chris062689 said:**
> Hm?  I tried searching, but I couldn't find any logs, what are some of the new fancy features?

Google is your friend :)

Also this url

[http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by dino99 on 2008-09-06
> **andrewabc said:**
> Alpha 5 work with virtualbox? I know alpha 4 didn't (so I read)

hi,
i can work with virtualbox 2.0 (and before too) if:
- i remove "quiet" & "splash" from the boot line (grub)
- and add "noreplace-paravirt" at the end of this line

some others have played with "nozl=off" or acpi_timer (for 32 bits) / acpitimer (for 64 bits)

hope that can help !!!

---

### Post by Saint Angeles on 2008-09-06
ok so i upgraded to intrepid and man... im pissed.

i cant use fglrx and it wont let me install pidgin (dependency hell)... also, it gives me an error about being unable to upgrade fusion icon everytime i try to do a dist-upgrade.


i have to use butt ugly kopete.

but nautilus' tabs and restore from trash rock hard

---

### Post by rocknrolf77 on 2008-09-06
> **dino99 said:**
> hi,
i can work with virtualbox 2.0 (and before too) if:
- i remove "quiet" & "splash" from the boot line (grub)
- and add "noreplace-paravirt" at the end of this line

some others have played with "nozl=off" or acpi_timer (for 32 bits) / acpitimer (for 64 bits)

hope that can help !!!

What the **** is going on? Never had problems like this in any alpha version, just 8.10 gives me this ****. Tried all of them. It will not work in Virtualbox.

---

### Post by KrazyPenguin on 2008-09-06
> **chris062689 said:**
> Hm?  I tried searching, but I couldn't find any logs, what are some of the new fancy features?

Here is a list a member made:
[http://ubuntuforums.org/showthread.php?t=886980](http://ubuntuforums.org/showthread.php?t=886980)


Also read the release notes:
[http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)

For me each release gets a little better than the previous release.
I think a lot of people expect BIG things, but with 6 month releases we see small changes happen at a time, while maintaining stability.

Ubuntu always does a lot of "under-the-hood" work, and sometimes the changes aren't apparent. 

:popcorn:

---

### Post by meborc on 2008-09-06
> **Saint Angeles said:**
> ok so i upgraded to intrepid and man... im pissed.

i cant use fglrx and it wont let me install pidgin (dependency hell)... also, it gives me an error about being unable to upgrade fusion icon everytime i try to do a dist-upgrade.


i have to use butt ugly kopete.

but nautilus' tabs and restore from trash rock hard

why are you pissed at an alpha OS release, which you upgraded yourself? why? ... i just have to ask (read my sig for explanation) ;)

---

### Post by Sand &amp; Mercury on 2008-09-06
> **meborc said:**
> why are you pissed at an alpha OS release, which you upgraded yourself? why? ... i just have to ask (read my sig for explanation) ;)
I'm sure he knew the risks, but that doesn't necessarily make it not annoying when things don't work, I guess...

---

### Post by Changturkey on 2008-09-06
So Alpha 6 will have the "revolutionary desktop"?

---

### Post by olskar on 2008-09-06
> **Changturkey said:**
> So Alpha 6 will have the "revolutionary desktop"?


Haha, yeah.

UserInterfaceFreeze is on 11 September:
> After the user interface freeze (UIF), the following things must not change any more without approval of the release team and notification to the documentation team:

    * the user interface of individual applications which are installed by default,
    * the appearance of the desktop,
    * the distribution specific artwork,
    * all user-visible strings in applications and the desktop. 


And Alpha 6 is 18 September

---

### Post by doorknob60 on 2008-09-06
I don't know what it is, but Alpha 5 hates me! I'm using Kubuntu if it matters, but I simply can't get my wifi to work! It works out of the box in alpha 4, hardy, gusty, feisty, and debian, but I can't get it to work at all with Alpha 5. I tried ath5k (works in debian lenny), madwifi (works in debian lenny and all previous versions of Ubuntu) and ndiswrapper (worked ever time I tried it in the past), but nothing works. It's not a hardware problem because it works fine in my Debian partition with ath5k...also I plugged in an ethernet cable and k network manager still wouldn't work with it ??? I had to use dhclient to connect in the terminal. Oh yeah I tried connecting with iwconfig and dhclient too which always works for me but not this time...any ideas? I'm probably just gonna install the older kernel and use that :( EDIT: Holy crap, after all this time troubleshooting, it's as simple as installing Wicd :P Works fine with latest kernel and madwifi (too scared to mess with it enough to try ath5k lol).

---

### Post by yoghurt-feen on 2008-09-06
I have problems with the guest-account... im login to my normal account, switches to guest, switch back to normal, but when i tries to switch to guest again, im prompted for a password, but there shouldnt be a password?

---

### Post by meborc on 2008-09-06
> **Sand & Mercury said:**
> I'm sure he knew the risks, but that doesn't necessarily make it not annoying when things don't work, I guess...

i understand... but it is like slicing your throat and being angry that you die :D ... if you get my analogy

---

### Post by MadsRH on 2008-09-06
No need to worry, Ubuntu will be beatuiful by the final release :)

Check out the artwork mailinglist to follow the progress.

[B]
//MadsRH[/B]

---

### Post by MaX on 2008-09-06
Ok, so today I updated my packages... again...
[LIST]
[*]Nvidia refuses to work
[*]The damn X-auto-configure stuff, detects my CRT as a 800x600 CRT (when it's a 1600x1200 CRT), it doesn't detect my 1280x1024 LCD at all...
[*]Private folder is nowhere to be found
[*]That's about it... mostly bummed about nvidia crashing though, haven't seen any other posts on that so I didn't expect it.
[/LIST]

---

### Post by Gina on 2008-09-06
Intrepid Alpha 5 boots on my laptop but the firmware for my wireless (bcm4306) won't load and network manager has crashed several times.  Back in Hardy, everything fine.

---

### Post by xlinuks on 2008-09-06
> **Saint Angeles said:**
> ... i'm not irritated enough to use another OS
hahahahaha  :)

---

### Post by Nullack on 2008-09-06
Being unhappy about particular items of Ubuntu is an excellent source of motivation to get involved, to contribute to make it better. You could look at reporting bugs, doing some debugging and generally helping on the issues.

---

### Post by danbuter on 2008-09-06
Sometimes I get the feeling that all the good programmers at Canonical went on vacation and got replaced by pissed-off monkeys. Then the programmers come back at RC, and try to fix everything all at once. Or at least, the last 2 releases have been like that. (I've submitted a number of bug reports since Alpha 3. Guess how many have been fixed).

---

### Post by hvac3901 on 2008-09-06
> **v1cho said:**
> What the ... ?!?! Why are you using the daily builds form the day before yesterday? :confused:
Does it REALLY include kernel 2.6.27?
yes

---

### Post by Sef on 2008-09-06
> I have problems with the guest-account... im login to my normal account, switches to guest, switch back to normal, but when i tries to switch to guest again, im prompted for a password, but there shouldnt be a password?

That's a bug.  Report it to launchpad, please.

---

### Post by Nullack on 2008-09-06
> **danbuter said:**
> Sometimes I get the feeling that all the good programmers at Canonical went on vacation and got replaced by pissed-off monkeys. Then the programmers come back at RC, and try to fix everything all at once. Or at least, the last 2 releases have been like that. (I've submitted a number of bug reports since Alpha 3. Guess how many have been fixed).

Most of it is upstream issues. To help further your could setup a bugwatch on LP for an upstream bug. Also, conduct further debugging to isolate the issue and give lower hanging fruit to the devs.

---

### Post by robzon on 2008-09-06
Just booted Alpha5. My experience so far:
- touchpad is painfully slow
- sound deosn't work out-of-box
- bluetooth doesn't work after suspend
- compiz doesn't work out-of-box (it does in hardy)
- network manager is much worse than before
- bluetooth input services don't even show up (can't use my bt mouse)
- no new theme? where did it go?
- restart button doesn't work

Now, WTF?? So far my experience with Ubuntu was that late alphas were actually pretty stable. Now it's crap. So many regressions I'm starting to worry that they won't get fixed for the release :/

---

### Post by IanW on 2008-09-07
> **doorknob60 said:**
> I don't know what it is, but Alpha 5 hates me! I'm using Kubuntu if it matters, but I simply can't get my wifi to work! It works out of the box in alpha 4, hardy, gusty, feisty, and debian, but I can't get it to work at all with Alpha 5. I tried ath5k (works in debian lenny), madwifi (works in debian lenny and all previous versions of Ubuntu) and ndiswrapper (worked ever time I tried it in the past), but nothing works. It's not a hardware problem because it works fine in my Debian partition with ath5k...also I plugged in an ethernet cable and k network manager still wouldn't work with it ??? I had to use dhclient to connect in the terminal. Oh yeah I tried connecting with iwconfig and dhclient too which always works for me but not this time...any ideas? I'm probably just gonna install the older kernel and use that :( EDIT: Holy crap, after all this time troubleshooting, it's as simple as installing Wicd :P Works fine with latest kernel and madwifi (too scared to mess with it enough to try ath5k lol).

I found (with an EeePC701) that to get wifi I had to _disable_ ath5k in System/Administration/Hardware Drivers.:confused:

---

### Post by awakatanka on 2008-09-07
> **doorknob60 said:**
> I don't know what it is, but Alpha 5 hates me! I'm using Kubuntu if it matters, but I simply can't get my wifi to work! It works out of the box in alpha 4, hardy, gusty, feisty, and debian, but I can't get it to work at all with Alpha 5. I tried ath5k (works in debian lenny), madwifi (works in debian lenny and all previous versions of Ubuntu) and ndiswrapper (worked ever time I tried it in the past), but nothing works. It's not a hardware problem because it works fine in my Debian partition with ath5k...also I plugged in an ethernet cable and k network manager still wouldn't work with it ??? I had to use dhclient to connect in the terminal. Oh yeah I tried connecting with iwconfig and dhclient too which always works for me but not this time...any ideas? I'm probably just gonna install the older kernel and use that :( EDIT: Holy crap, after all this time troubleshooting, it's as simple as installing Wicd :P Works fine with latest kernel and madwifi (too scared to mess with it enough to try ath5k lol).Known bug : > [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/259278](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/259278)
 
 Workaround: install network-manager-gnome and launch nm-applet

---

### Post by stijngysemans on 2008-09-07
> **robzon said:**
> Just booted Alpha5. My experience so far:
- touchpad is painfully slow

is there already a bug report about this.

---

### Post by gmclachl on 2008-09-07
I am a bit confused by a couple of things Alpha5 is supposed to have Gnome 2.2.24 Beta 2 but my Gnome seems to be 2.2.23.91 

Also ath9k is now built into the kernel but I can't seem to use it. As soon as I enable the module and disable ath5k my wireless breaks. 

I had it working fine with the torvalds git tree. 

George

---

### Post by Sand &amp; Mercury on 2008-09-07
> **meborc said:**
> i understand... but it is like slicing your throat and being angry that you die :D ... if you get my analogy
Ok, very true :lol:

I may end up trying this just as a livecd, it seems like this particular release in its alpha state has given people a lot of grief.

---

### Post by IanW on 2008-09-07
> **gmclachl said:**
> I am a bit confused by a couple of things Alpha5 is supposed to have Gnome 2.2.24 Beta 2 but my Gnome seems to be 2.2.23.91  

George

AFAIK 2.23.91=2.24b2

---

### Post by mejy on 2008-09-07
> **IanW said:**
> AFAIK 2.23.91=2.24b2

Yup, development releases are odd numbers leading up to a stable release of the succeeding number (2.23 development leads to 2.24 stable), and the beta's start with 2.*.90 (making that beta 1).

I think everybody's being a bit overly-critical over this release - it's an alpha months away from release and despite comparatively few UI changes as yet, pulse audio, the kernel and network manager (so sound, drivers and network) have been upgraded and changed substantially.  It's not surprising that there's instability and bugs, but you'd do much better to report these issues to the devs (or confirm existing bug reports if there are any) than to moan about them on a forum.

As suggested in the name, Intrepid is an ambitious release that plans to move Ubuntu forward - it may well lack the polish and stability that Hardy has after months of post-release updates.

---

### Post by meborc on 2008-09-07
> **mejy said:**
> i think everybody's being a bit overly-critical over this release

+1

---

### Post by MadsRH on 2008-09-07
> **meborc said:**
> +1

+1

I'm really looking forward to Ibex. I think it will be a step up for Linux on many fronts

---

### Post by Exsecrabilus on 2008-09-07
It's strange how Ubuntu spends 3 months over each release. For a complete and fully-working operating system and with their reputation as the most popular Linux distribution, you'd think they'd at least work for 5 months and have something innovative every release to meet public demands.

---

### Post by Progressive on 2008-09-07
Ubuntu releases do not come out every 3 months. Releases only come out once every 6 months.

---

### Post by Changturkey on 2008-09-07
Are the Kith/Dust themes ever going to be used?

---

### Post by IanW on 2008-09-07
> **Exsecrabilus said:**
> It's strange how Ubuntu spends 3 months over each release. For a complete and fully-working operating system and with their reputation as the most popular Linux distribution, you'd think they'd at least work for 5 months and have something innovative every release to meet public demands.

Not quite.
8.10 "Intrepid Ibex" is currently due for release around 30th Oct 2008.
This means that "Jesting Jackalope" (or whatever development codename 9.04 gets) will start being worked on around 1st Nov 2008 (if not sooner).

---

### Post by Kevbert on 2008-09-07
> **plun said:**
> Well... please read these bugs and maybe add your point....

[https://bugs.launchpad.net/ubuntu/+bug/254098](https://bugs.launchpad.net/ubuntu/+bug/254098)

[http://bugzilla.gnome.org/show_bug.cgi?id=520736](http://bugzilla.gnome.org/show_bug.cgi?id=520736)


This is not a bug today !


Change  [B]Menu System > Administration> > Authorisations  > hal > storage > "Mount file systems from internal drives" > add yourself to the right. 
[/B]

:-k
How do I do this in Kubuntu ?

---

### Post by Exsecrabilus on 2008-09-07
> **Progressive said:**
> Ubuntu releases do not come out every 3 months. Releases only come out once every 6 months.
No. Don't you think that I, being the maintainer of a list of new features in Intrepid, know Ubuntu? True, the developers did their usual "massive merge from Debian" in June and July, but what else did they do but *plan* features for 8.10? Nothing. They were all hyped up and focused on 8.04.1, so in effect, only three and a half months were left for Intrepid's development.

> **IanW said:**
> Not quite.
8.10 "Intrepid Ibex" is currently due for release around 30th Oct 2008.
This means that "Jesting Jackalope" (or whatever development codename 9.04 gets) will start being worked on around 1st Nov 2008 (if not sooner).
As you have said yourself, "not quite."

The UDS developer conference is a few weeks AFTER an official release. So will it make sense to start on November like you have said? No. For the first three months, this is what Ubuntu typically does:
[list][*]Sync with Debian, get new packages and new versions.
[*]Plan new features.
[*]Prepare 8.04.x (8.04.2).[/list]
So in true sense, with 8.04.2, they'll probably have only three months for 9.04 also.

---

### Post by mejy on 2008-09-07
> **Exsecrabilus said:**
> No. Don't you think that I, being the maintainer of a list of new features in Intrepid, know Ubuntu?
Your list is a useful starting point for understanding the major changes from previous Ubuntu versions, but is ultimately a compilation of clips from other webpages and, as far as I can tell, not even the result of your own testing of Intrepid.  I don't think this really justifies that kind of arrogant retort.

> **Exsecrabilus said:**
> True, the developers did their usual "massive merge from Debian" in June and July, but what else did they do but *plan* features for 8.10? Nothing. They were all hyped up and focused on 8.04.1, so in effect, only three and a half months were left for Intrepid's development.

Hardy is an LTS and so obviously required a small amount of developer time, but adding minor patches doesn't take nearly as many developer-hours as does making massive over-hauls to the architecture and executing repositry-wide rebuilds.

Merging from Debian is a huge task, and requires effort to account for differences between the distributions and ensure clean builds throughout - as well as making sure Ubuntu-specific patches still have the desired effect.  Unless you have experience in this area (I've managed some simple packaging, developed a few apps and contributed some up-stream patches as a hobby - and I accept that what the developers do is on an entirely different scale) I don't think you can really criticise their work.

Not to mention there is a significant amount of time spent assessing the feasibility of future plans and blueprints, as well as beginning attempts to develop or implement these plans before they're made public.  Admittedly, when applications aren't yet public (generally because they're not usable or Canonical wants the PR) it's difficult to asses the progress made, but equally since you don't have the full picture you can hardly criticise what's done.

Also consider that Ubuntu developers may hack on upstream applications, which benefits the entire community rather than just Ubuntu users.


> **Exsecrabilus said:**
> As you have said yourself, "not quite."

The UDS developer conference is a few weeks AFTER an official release. So will it make sense to start on November like you have said? No. For the first three months, this is what Ubuntu typically does:
[list][*]Sync with Debian, get new packages and new versions.
[*]Plan new features.
[*]Prepare 8.04.x (8.04.2).[/list]
So in true sense, with 8.04.2, they'll probably have only three months for 9.04 also.

Developers don't just take a holiday before UDS, they'll be preparing and drafting blueprints and other ideas - actually writing code isn't the only job of a decent developer.  As I said before, preparing point releases is a comparatively minor task and the other two are perfectly valid (and not exclusive) uses of developer time which help to move the next release forward and ensure its quality.

Ubuntu has a comparatively minor but dedicated core of paid developers - much of the rest is implemented by the community (such as WUBI in the last release).  May I suggest that before you criticise the developers' use of their time - many of whom are doing so in their free-time anyway - you get involved in the process and contribute something yourself?

---

### Post by avb on 2008-09-07
for sure this release have a lot of bugs now. the reason is easy. New x.org and 2.6.27 kernel. x.org is moving to evdev driver for all input devices. Thats the case of problems why touchpads and trackpoints lost a part of it functional. evdev driver should be fixed until intrepid release. 
Second issue is 2.6.27 kernel made a bunch of merges of out-of-tree drivers. And this procedure have a couple issues. Like some wireless cards stopped working. Mine webcams stop working because of merge of a gspca driver. 

So guys, lets be calm until release. Its an alpha software, so all we should do is feed bugtrack with our bug reports. Lets do this :)

---

### Post by Nullack on 2008-09-07
Id like to add a point to avb's post.

Best practice in contributing to bugs is to manage the bug throughout its lifecycle and not simply report it and leave it. If you learn something new about the bug thats relevant, post a comment. Retest it to see if it still occurs on new revisions of dependent packages. If you learn how to fix it via debugging, post that into the bug too and move the status.

Basically, please keep the bug updated as you move forward :)

---

### Post by Exsecrabilus on 2008-09-08
> **mejy said:**
> Your list is a useful starting point for understanding the major changes from previous Ubuntu versions, but is ultimately a compilation of clips from other webpages and, as far as I can tell, not even the result of your own testing of Intrepid.  I don't think this really justifies that kind of arrogant retort.
And doesn't it take work to compile all the separate links and screenshots, compile them into one place, and summarize each point? After browsing through a bunch of webpages?



> **mejy said:**
> Hardy is an LTS and so obviously required a small amount of developer time, but adding minor patches doesn't take nearly as many developer-hours as does making massive over-hauls to the architecture and executing repositry-wide rebuilds.
LTS doesn't mean extra stability, it means longer support. :D

> **mejy said:**
> Merging from Debian is a huge task, and requires effort to account for differences between the distributions and ensure clean builds throughout - as well as making sure Ubuntu-specific patches still have the desired effect.  Unless you have experience in this area (I've managed some simple packaging, developed a few apps and contributed some up-stream patches as a hobby - and I accept that what the developers do is on an entirely different scale) I don't think you can really criticise their work.
I didn't realize that. I know nothing of how to merge from Debian, so that shouldn't have been said. Sorry. :P

> **mejy said:**
> Not to mention there is a significant amount of time spent assessing the feasibility of future plans and blueprints, as well as beginning attempts to develop or implement these plans before they're made public.  Admittedly, when applications aren't yet public (generally because they're not usable or Canonical wants the PR) it's difficult to asses the progress made, but equally since you don't have the full picture you can hardly criticise what's done.
True. I agree.

> **mejy said:**
> Also consider that Ubuntu developers may hack on upstream applications, which benefits the entire community rather than just Ubuntu users.
What Ubuntu modifies, Ubuntu uses. Typically Ubuntu changes its default applications for language fit, for system integration, and some others (such as disabling "Check for Updates...",) but none significant that I know of.




> **mejy said:**
> Developers don't just take a holiday before UDS, they'll be preparing and drafting blueprints and other ideas - actually writing code isn't the only job of a decent developer.  As I said before, preparing point releases is a comparatively minor task and the other two are perfectly valid (and not exclusive) uses of developer time which help to move the next release forward and ensure its quality.
Yes, planning new features = making blueprints. >_>

> **mejy said:**
> Ubuntu has a comparatively minor but dedicated core of paid developers - much of the rest is implemented by the community (such as WUBI in the last release).  May I suggest that before you criticise the developers' use of their time - many of whom are doing so in their free-time anyway - you get involved in the process and contribute something yourself?
Criticsm doesn't come from the experienced. It comes from the public. If it didn't come from the public, it wouldn't be called "criticism," but rather a "mistake pointed out" from an experienced and just forgotten about.

---

### Post by MALEADt on 2008-09-10
I think I'm going crazy... in a positive way :)

Got a new ATI GPU last month, but couldn't get it working at any linux distro. Fedora 9 refused fglrx, Ubuntu Hardy nor Intrepid didn't either. Default readon(hd) didn't work on Fedora 9 and Hardy, and I couldn't manage to install the newest ones on Hardy. No matter how hard I tried, I couldn't get this ATI (x1650 Pro) GPU working at linux :'( I was so desperately I even had to revert back to XP for some weeks.

Until now :) This morning I downloaded Alpha 5, just to see how things were working out. just booted up, everything worked very smooth... suspiciously smooth...

So I did an ''glxinfo'', which turned up:
```
ubuntu@ubuntu:/media/Boot$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

Omg I'm going crazy :D

---

### Post by sleepingdragon on 2008-09-10
Here's my run at Alpha 5 with KDE 4.1... (yeah, I know, I'm a masochist).

Smooth... pure and simple. I've only had one error from FF3, probably from me pushing 40 tabs at once.

Here's the specs:

2.4 Celeron
1GB RAM
256 Mb nVidia 6200
2x160Gb IDE drives.

Nothing fancy, but it all worked beautifully.  Here's a screenshot...

---

### Post by inportb on 2008-09-10
A masochist for running Ubuntu 8.10 Alpha5 or a masochist for running KDE 4.1? :)

Because I have both and I consider myself a connoisseur of fine software ;p

---

### Post by inportb on 2008-09-10
Please note that Ubuntu is currently experiencing the same fglrx issues that Fedora's been experiencing. Until AMD releases a driver compatible with the new Xorg, we'll be using the opensource ati, radeon, and radeonhd drivers.

The good news is that they have pretty good 2D support, and I'm getting passable 3D using the radeon driver.

Your glxinfo quote may be slightly misleading, as Mesa supports direct rendering now ;p

> **MALEADt said:**
> I think I'm going crazy... in a positive way :)

Got a new ATI GPU last month, but couldn't get it working at any linux distro. Fedora 9 refused fglrx, Ubuntu Hardy nor Intrepid didn't either. Default readon(hd) didn't work on Fedora 9 and Hardy, and I couldn't manage to install the newest ones on Hardy. No matter how hard I tried, I couldn't get this ATI (x1650 Pro) GPU working at linux :'( I was so desperately I even had to revert back to XP for some weeks.

Until now :) This morning I downloaded Alpha 5, just to see how things were working out. just booted up, everything worked very smooth... suspiciously smooth...

So I did an ''glxinfo'', which turned up:
```
ubuntu@ubuntu:/media/Boot$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

Omg I'm going crazy :D

---

