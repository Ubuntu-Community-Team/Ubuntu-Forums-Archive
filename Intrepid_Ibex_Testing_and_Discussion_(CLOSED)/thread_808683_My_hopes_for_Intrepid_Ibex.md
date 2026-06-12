---
title: "My hopes for Intrepid Ibex"
date: 2008-05-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danbuter on 2008-05-26
What I'd like to see:

Abiword 2.6.3 (Should have been in HH)
Perl 5.10 (should have been in HH)
Compiz OFF by default (buggy as hell)
NO Tracker/Beagle program (waste of memory)
Updated graphics (compare Ubuntu to OpenSUSE and see what I mean, esp. regarding font rendering)
NO Ubuntu-desktop (Makes me feel like I HAVE to use the included programs, and is a PITA when I upgrade)
More bug-hunting (because there can never be enough)

In general, I'm very happy with HH, but I hope II blows my socks off.

---

### Post by KhaaL on 2008-05-26
I agree with most except for compiz. I'd like to see the crazier plugins there too, such as cylinder view!

In addition to that, I hope to...
* Better support for Bluetooth headsets (this is a really lacking area!)
* AcetoneISO included by default 
* screensaver-settings included by default
* MUCH better pulseaudio support - it works worse than ALSA in some cases for me... I can't play ET:QW and listen to music anymore :(
* better support for 64 bit users (install Firefox 32bit with flash and java by default, instead of relying on flashwrapper and openJDK)
* cairo dock present in the repository

---

### Post by gnomeuser on 2008-05-26
> **danbuter said:**
> 
NO Tracker/Beagle program (waste of memory)


Another option for this would be making Tracker useful, let it do virtual folders in nautilus, populate the library in your media player.. integrate it's functionality beyond being a neat way to search your stuff. Xesam promises to help us do this, I'm thinking we need that stuff to see the true power of Tracker.

It's a powerful tool but we just don't use it right now and there has been no concerted effort to use it before we had Xesam as a standard interface to query the indexers.

---

### Post by smartboyathome on 2008-05-26
> **danbuter said:**
> What I'd like to see:

[LIST=1]
[*]Abiword 2.6.3 (Should have been in HH)
[*]Perl 5.10 (should have been in HH)
[*]Compiz OFF by default (buggy as hell)
[*]NO Tracker/Beagle program (waste of memory)
[*]Updated graphics (compare Ubuntu to OpenSUSE and see what I mean, esp. regarding font rendering)
[*]NO Ubuntu-desktop (Makes me feel like I HAVE to use the included programs, and is a PITA when I upgrade)
[*]More bug-hunting (because there can never be enough)
[/LIST]

In general, I'm very happy with HH, but I hope II blows my socks off.

[LIST=1]
[*]I don't like Abiword, I use Ubuntu for school and it just doesn't have enough functionality to be able to work with everything.
[*]If someone packages it before the freeze, it should be accepted.
[*]I like Compiz, and it attracts the bulk of users. I think we should keep it on by default.
[*]I wouldn't care either way, because I don't use it. I just keep my files well organized.
[*]No comment, as I am fine with the font rendering as it is and have never used opensuse.
[*]This is how Ubuntu manages the upgrade. If there are upgrades where it installs a new package, people wouldn't get this upgrade. If it uninstalls a package because a newer one is available, this also wouldn't happen.
[*]Care to help hunt those bugs? :D
[/LIST]

Smartboy

---

### Post by Quikee on 2008-05-27
Perl 5.10 is already in II.

---

### Post by irrdev on 2008-05-27
> **smartboyathome said:**
> [LIST=1]
[*]I don't like Abiword, I use Ubuntu for school and it just doesn't have enough functionality to be able to work with everything.
[*]If someone packages it before the freeze, it should be accepted.
[*]I like Compiz, and it attracts the bulk of users. I think we should keep it on by default.
[*]I wouldn't care either way, because I don't use it. I just keep my files well organized.
[*]No comment, as I am fine with the font rendering as it is and have never used opensuse.
[*]This is how Ubuntu manages the upgrade. If there are upgrades where it installs a new package, people wouldn't get this upgrade. If it uninstalls a package because a newer one is available, this also wouldn't happen.
[*]Care to help hunt those bugs? :D
[/LIST]

Smartboy
I totally agree with you, Smartboy. OpenOffice handles everything, whereis Abiword handles only a few select word processing tasks. In today's world of Aero and Aqua, Compiz is also a must for attracting new users. It's also tons of fun to play with. :) As for the ubuntu-desktop package, this is an essential part of the distro which cannot be eliminated. The alternative is to simply install gnome, without the extra programs, without any integration, and without any extra features. If that's what you want, you would be better off to get the [GNOME LiveCD]("http://torrent.gnome.org/") directly. 

Just my two cents.:)

---

### Post by Quikee on 2008-05-27
Well for my writing needs AbiWord is more then enough, however it is faster, cleaner and handles some Word files better than OO in my experience. The only thing missing for me currently is to show 2 pages side by side, which is useful on large wide-screen monitors.

Out of curiosity what OO features do you use that is not available in AbiWord?

For spreadsheets Gnumeric is also more suited for my needs than OO Calc.

---

### Post by gnomeuser on 2008-05-27
> **irrdev said:**
> I totally agree with you, Smartboy. OpenOffice handles everything, whereis Abiword handles only a few select word processing tasks. In today's world of Aero and Aqua, Compiz is also a must for attracting new users. It's also tons of fun to play with. :) As for the ubuntu-desktop package, this is an essential part of the distro which cannot be eliminated. The alternative is to simply install gnome, without the extra programs, without any integration, and without any extra features. If that's what you want, you would be better off to get the [GNOME LiveCD]("http://torrent.gnome.org/") directly. 

Just my two cents.:)

So those of us who actually like Abiword don't deserve the latest version being available - which was the request not making it the default. Why thank you, we love you to OpenOffice fans. Hardy is stuck with a version of abiword that is outdated by at least a few years due to the unwillingness of the team to grant a freeze exception. Abiword users are noticably upset especially since this is the only supported version upstream now and it has many bugfixes.. oh and every other distro shipped in the Hardy timeframe managed to get the 2.6.x series in.

The Abiword developers had to spend their time doing Ubuntu' job to even let Ubuntu users have the option to get a supportable version of Abiword:
[http://msevior.livejournal.com/22172.html](http://msevior.livejournal.com/22172.html)

I share his opinion that compiz isn't ready, well not so much compiz but the underlying X stack. One major lacking feature is DRI2 which is needed to do things like making OpenGL apps like glxgears work or xv video. Enabling it by default was premature as a technical decision. From a marketing point of view it was probably a so and so decision, people seem to like it but they also hate it when it crashes or makes things not work, something that happens to damn often. I would favor disabling it till the underlying stack is ready for real deployment. People can still enable it if they want.

---

### Post by hartl_vienna on 2008-05-27
I hope that we´ll get a working Synchronisation between Evolution and my Palm Treo 680.  [-o<

---

### Post by smartboyathome on 2008-05-27
> **Quikee said:**
> Well for my writing needs AbiWord is more then enough, however it is faster, cleaner and handles some Word files better than OO in my experience. The only thing missing for me currently is to show 2 pages side by side, which is useful on large wide-screen monitors.

Out of curiosity what OO features do you use that is not available in AbiWord?

For spreadsheets Gnumeric is also more suited for my needs than OO Calc.

Tables within tables. My English class strangely uses this. Abiword has not been able to render my documents with those correctly, whereas OpenOffice has.

> **gnomeuser said:**
> So those of us who actually like Abiword don't deserve the latest version being available - which was the request not making it the default. Why thank you, we love you to OpenOffice fans. Hardy is stuck with a version of abiword that is outdated by at least a few years due to the unwillingness of the team to grant a freeze exception. Abiword users are noticably upset especially since this is the only supported version upstream now and it has many bugfixes.. oh and every other distro shipped in the Hardy timeframe managed to get the 2.6.x series in.

The Abiword developers had to spend their time doing Ubuntu' job to even let Ubuntu users have the option to get a supportable version of Abiword:
[http://msevior.livejournal.com/22172.html](http://msevior.livejournal.com/22172.html)

I share his opinion that compiz isn't ready, well not so much compiz but the underlying X stack. One major lacking feature is DRI2 which is needed to do things like making OpenGL apps like glxgears work or xv video. Enabling it by default was premature as a technical decision. From a marketing point of view it was probably a so and so decision, people seem to like it but they also hate it when it crashes or makes things not work, something that happens to damn often. I would favor disabling it till the underlying stack is ready for real deployment. People can still enable it if they want.

I am sorry I misunderstood. I thought the op was asking for Abiword being the default.

About Compiz, I think that if you disable it, we will see a huge flux in new people saying "How do I turn those cool things on?". There will be way to many with it off. As it is, Ubuntu just uses stable effects, and the users have to install extra software from the repos to get other effects, a wise decision imo.

---

### Post by Game_boy on 2008-05-27
1. Improve boot speed and slickness

2. Maintain a hardware database indicating the level of support in past, current and development versions of Ubuntu, and also the locaton of relevant third-party drivers.

3. Provide clear links to Canonical paid support, and some tutorial screencasts, on first boot.

4. Suggest Wine to be installed for EXE, MSI and BAT files.

5. Suggest suitable software or hardware MIDI stack to be installed and integrated with Movie Player when MIDI file is opened.

6. Provide a unique GRUB theme to make it appear friendlier.

7. Provide whatever does the partitioning in Ubiquity as a desktop application.

8. Offer a USB key version of Ubuntu, or even better make a Revisor clone that offers to do so.

9. Offer mobile and/or iPod syncing by default or a prepackaged "just work" setup in the repositories

10. Offer a recovery mode that is graphical and offers to repair damaged critical files or back up your /home.

11. Offer a fully graphical process (no bridging or networking or something like that) for virtualisation. I want to click to install virtualistaion support and it asks me immediately if I have an ISO to boot from.

12. Offer more user-friendly info in Hardware Information, tied to the online hardware database.

13. Include R500 3D support whether it has been officially released by xf86-video-ati or not.

14. Consolidate and reduce the number of items in System->Preferences and System->Administration

15. Make Kubuntu catch up to Ubuntu in all areas.

16. Fix wireless drivers. Even if it is not Ubuntu's fault that they are broken, surely Ibex's focus on networking demands that developers put some effort into patching the most common or most broken ones?

---

### Post by syxbit on 2008-05-27
I must say, I agree with pretty much everything Game_boy said
taking advantage of upstart should really be a high priority, especially in the first os a series of Non LTS releases.
Surely the goal should be to have it perfect for the next LTS, which would mean at least some small strides in between.

As for grub, what are those guys doing?
we've been on grub legacy for years, with the promise that soon we'll be on grub2.
hm.....

As for wireless, a lot of those problems can be fixed by just using the latest kernel (which Ubuntu rarely does) and using an svn of network manager (something Fedora always does)
I want 2.6.27. It'll be out in time!!!

---

### Post by meborc on 2008-05-27
> **syxbit said:**
> 
I want 2.6.27. It'll be out in time!!!

ubuntu kernel guy said in II 26 will be used... interview in the ubuntudevelopers youtube channel

---

### Post by Sockerdrickan on 2008-05-27
I don't think compiz fusion should be disabled by default.

I think it should be [SIZE=7]friggin FIXED [SIZE=1]by default.[/SIZE][/SIZE] And work on auto turn off when gaming!

---

### Post by Game_boy on 2008-05-27
> **Tux0r said:**
> I don't think compiz fusion should be disabled by default.

I think it should be [SIZE=7]friggin FIXED [SIZE=1]by default.[/SIZE][/SIZE] And work on auto turn off when gaming!

Ah. You want Redirected Direct Rendering and Input Transformation. They're in development for X.Org, and between them stops all of the random flickering, crashing and applications behaving stupidly while Compiz is enabled. Also, X.Org is really, really behind schedule with entrenched bugs and dropped features, so you won't have much luck for quite some time.

---

### Post by Jeffery Mewtamer on 2008-05-27
Things I would like to see:

*buntu-desktop-minimal meta-packages to make it easy to install a bare bone desktop environment and add a custom software combination. This gives me and the thread creator our desire for an easy to customize GUI based system while still giving less experienced users the ease of a fully functioning system out of the box.

For KDE4 apps to regain functionality that they lost compared to their KDE3 counterparts. Gwenview and Ark in particular seem to have been gutted in the transfer.

A single meta-package to install all of the software needed to execute music transfers from a hard drive to a Rio Karma. The omfs drivers are already in the Hardy repositories, but I had to compile from source to get them working, and I can install libkarma from the repositories. Fixing the omfs drivers in the repositories, adding lkarmafs, and creating a meta-package that install all three and their dependencies is all the seems necessary.

I also support the idea of developing an easy method for creating LiveUSB installations.

---

### Post by Luke has no name on 2008-05-27
On the issue of Compiz by default: There should at least be a warning for users that have it enabled that it is alpha software, and that it should be the first place to look (next to proper xorg.conf) when debugging video problems.

---

### Post by smartboyathome on 2008-05-27
It isn't alpha software to me, more like beta, as I personally haven't had problems with it with my X3100, and there aren't nearly as many bugs with it as before.

---

### Post by Gina on 2008-05-27
Compiz won't work for me om any of my computers.  But I'm planning to make myself a new one so maybe that'll work!

---

### Post by ccw on 2008-05-28
> **danbuter said:**
> What I'd like to see:

Abiword 2.6.3 (Should have been in HH)
Perl 5.10 (should have been in HH)
Compiz OFF by default (buggy as hell)
NO Tracker/Beagle program (waste of memory)
Updated graphics (compare Ubuntu to OpenSUSE and see what I mean, esp. regarding font rendering)
NO Ubuntu-desktop (Makes me feel like I HAVE to use the included programs, and is a PITA when I upgrade)
More bug-hunting (because there can never be enough)

In general, I'm very happy with HH, but I hope II blows my socks off.

Perl 5.10 is on its way in now.

If you're savvy enough to understand what the ubuntu-desktop package is, you should be comfortable enough to remove it if it disagrees with you.

---

### Post by meborc on 2008-05-28
> **ccw said:**
> Perl 5.10 is on its way in now.

If you're savvy enough to understand what the ubuntu-desktop package is, you should be comfortable enough to remove it if it disagrees with you.

true... ubuntu-desktop is a must have metapackage

---

### Post by danbuter on 2008-05-28
I always end up deleting ubuntu-desktop. But then 6 months later I get to reinstall it so I can upgrade, then go about removing it again (along with a bunch of other stuff that is tied to it).

---

### Post by 23meg on 2008-05-28
You don't have to reinstall ubuntu-desktop; the dist-upgrade tool will take care of it for you.

---

### Post by Gina on 2008-05-29
Also, you don't have to install a desktop if you use the Minimal Install CD (mini.iso).

---

### Post by ayllu on 2008-05-29
Well... 

1st Soppourt for IPAQ PDA if is possible by default. 
2 Amarok by default 

For those gyus that dosent like compiz.

Just if you dont have a Nvidia Card have the option to shut down compiz.

---

### Post by durand on 2008-05-30
I didn't know compiz was turned on by default? I'm not sure I fully understand this argument, does compiz cause problems with ATI cards? With Intel and Nvidia that I have, its very stable. It's really easy to disable compiz anyway so I dunno what the problem is here...

> Also, you don't have to install a desktop if you use the Minimal Install CD (mini.iso).

 I think he wants a desktop, just not the default set of applications?

> I can't play ET:QW and listen to music anymore

Lol, same here. I sometimes just change amarok's sound driver to alsa for this.

> 2 Amarok by default
Amarok can't be a default because its a QT app, not GTK. Ubuntu doesn't ship with any QT widgets because that's what kubuntu is for.

---

### Post by meborc on 2008-05-30
> **ayllu said:**
> 
2 Amarok by default 


i never really used amarok... **qt->gtk** but wouldn't exile be as good? it is supposed to be amarok clone for gnome [http://exaile.org/](http://exaile.org/)

---

### Post by plun on 2008-05-30
> **meborc said:**
> i never really used amarok... **qt->gtk** but wouldn't exile be as good? it is supposed to be amarok clone for gnome [http://exaile.org/](http://exaile.org/)

Well, Exaile is just great.....:guitar:

LastFM is fixed and is just great.  (bzr version)


(Amarok and KDE4 is maybe a problem because Gnome stands still and discuss
with Debian/Gentoo if the earth is round or flat.... can take a couple of years to solve that the earth IS round.  ....   :)  )

---

### Post by UbuWu on 2008-05-30
> **danbuter said:**
> What I'd like to see:

Abiword 2.6.3 (Should have been in HH)


Has been uploaded to intrepid.

---

### Post by meborc on 2008-05-31
> **plun said:**
> (Amarok and KDE4 is maybe a problem because Gnome stands still and discuss
with Debian/Gentoo if the earth is round or flat.... can take a couple of years to solve that the earth IS round.  ....   :)  )

that is true, but i think we should keep one DE stable (and standing still) as rock until the other one has gone through it's changes... it will take another year or so until when KDE4 starts to actually be usable (as in usable for all 3.5.9 was)

---

### Post by Exsecrabilus on 2008-06-01
> **danbuter said:**
> More bug-hunting (because there can never be enough)
Isn't Intrepid Ibex supposed to try out like all-new features?

Doesn't that mean there will be way more bugs than bug fixes?

---

### Post by 23meg on 2008-06-01
No and no.

---

### Post by durand on 2008-06-01
It's supposed to try out some new stuff but it is not a bleeding edge release. II still aims to be stable and bug free.

---

### Post by Exsecrabilus on 2008-06-01
> **23meg said:**
> No and no.
Fail, you = wrong.

I didn't mean bleeding-edge never-before-seen stuff.
I just meant that it will have more features and more bugs than Hardy.

---

### Post by 23meg on 2008-06-01
How do you know?

---

### Post by grem91 on 2008-06-01
Just wondering, Is there a compiled list of features and additions that Intrepid Ibex is likely to include? And where could I find it?

---

### Post by Dojan5 on 2008-06-01
Now, i am a weird person, but im just happy that it is called Intrepid **Ibex**.
Mainly because if you translate Ibex to Swedish it becomes Stenbock, if you then translates that back to English it can become either Ibex or Capricorn (And since i am a Capricorn, :lolflag:)
Although i think they could include more GTK transparency, they cant make the window border transparent in metacity can they (Like in fvwm-crystal)?
I would also like to see an update of GNOME, but that might be too much too ask...

---

### Post by 23meg on 2008-06-01
> **grem91 said:**
> Just wondering, Is there a compiled list of features and additions that Intrepid Ibex is likely to include? And where could I find it?

No. The [blueprints]("https://blueprints.launchpad.net/ubuntu/intrepid") are being written yet (yes, that's why you only see four yet). Since the UDS sessions will form the basis of most blueprints, the [UDS schedule]("http://people.ubuntu.com/~scott/uds-intrepid/") may give you a rough idea.

---

### Post by durand on 2008-06-01
> **Exsecrabilus said:**
> Fail, you = wrong.

I didn't mean bleeding-edge never-before-seen stuff.
I just meant that it will have more features and more bugs than Hardy.

But every new version will have more features...possibly more bugs, but many will be fixed.

---

### Post by Exsecrabilus on 2008-06-01
> **23meg said:**
> How do you know?
I don't know if I'm right or wrong, I'm just guessing.

Sorry about the kind-of-bashing, looks like you're more advanced on Ubuntu knowledge than me. :D

---

### Post by hugmenot on 2008-06-01
How is OpenSuSe font rendering even slightly better than Ubuntu's?
OpenSuSe's font rendering modes are a /subset/ of the modes available in Ubuntu, i.e., you can replicate all render settings in Hardy.

---

### Post by tw3k on 2008-06-01
> **danbuter said:**
> What I'd like to see:
Compiz OFF by default (buggy as hell)



No way! works great. luv it.

---

### Post by tw3k on 2008-06-01
> **tw3k said:**
> No way! works great. luv it.

I guess I should say, to stick with the posters point, that I don't use gdm. I just use startx with an xterm in .xinitrc and start compiz from there.

---

### Post by danbuter on 2008-06-03
> **hugmenot said:**
> How is OpenSuSe font rendering even slightly better than Ubuntu's?
OpenSuSe's font rendering modes are a /subset/ of the modes available in Ubuntu, i.e., you can replicate all render settings in Hardy.

I have no idea. All's I know is that the fonts in OpenSUSE are MUCH more readable than the fonts in Ubuntu. Maybe it's a KDE/Gnome thing.

---

### Post by syko21 on 2008-06-04
1. Get the restore from trash function that was ambiguously referred to in the HH documents. ([http://ubuntuforums.org/showthread.php?t=731537](http://ubuntuforums.org/showthread.php?t=731537))
2. Pulseaudio gui integration. hate to say it but this is one thing that Vista does very well as far as individual application sound is concerned.
3. ext4 support? (even if its not for the /boot partition)
4. Prettier bootloader screen, I tried Linux mint and it is very easy on the eyes during the grub phase.
5. ndisgtk included in the livecd (very annoying to download the .debs from a windows machine)
6. New artwork/look that I was hoping to get, that was promoted early on with HH but gutted.

---

### Post by cariboo on 2008-06-04
Safe mode with networking. Should be pretty easy to implement.

Jim

---

### Post by caryb on 2008-06-04
Unless my computer is a freak my Kubuntu in recovery mode has full wireless & Ethernet networking. Whenever I break X I use recovery mode to do updates & wget rouge packages.


Cary

---

### Post by cariboo on 2008-06-05
Truthfully I think safe mode does have networking, it probably had something to do with my Sysvutils debacle. I think I was really thinking of networking at an initramfs prompt.

Jim

---

### Post by davbren on 2008-06-15
These are my hopes: -

1. Uber graphics update, this OS needs that 'Wow' factor that vista didn't deliver.
2. Cheese installed my default. Mac has it, why can't we?
3. Multipoint trackpadiness
4. Wine installed my default.
5. Compiz advanced options installed.
6. Desktop drapes installed by default.
7. Better WebDav support.

I'll probably come up with some more at a later date but I can't think of anything else right now.

P.S. I'm not really seeing what opensuse has that ubuntu doesn't...

---

### Post by Exsecrabilus on 2008-06-15
> **davbren said:**
> These are my hopes: -

1. Uber graphics update, this OS needs that 'Wow' factor that vista didn't deliver.
2. Cheese installed my default. Mac has it, why can't we?
3. Multipoint trackpadiness
4. Wine installed my default.
5. Compiz advanced options installed.
6. Desktop drapes installed by default.
7. Better WebDav support.

I'll probably come up with some more at a later date but I can't think of anything else right now.

P.S. I'm not really seeing what opensuse has that ubuntu doesn't...
You have to keep in mind that the CD has to have a limit.
If it adds certain "extra" packages, it will add another one. And another one. And another one. It goes on.

Cheese wasn't installed because not all people have webcams and it was unnecessary. It's in the repos if you need it.

Not everyone installs Ubuntu on a laptop so trackpad-specific support can't be enabled by default.

Wine is a big program, but like I said, not everyone needs it. If they do, however, it will always be in the repos.

Also, I agree with your idea that either CompizConfig Settings Manager or Simple CCSM needs to be installed by default.

---

### Post by caryb on 2008-06-15
My worry is that we are 2 months in & all resources are to 8.04.1 & not 8.10 with 4 months out (really 3 months as we have freeze 1 month before) we have no new kernel Kubuntu is barely working, there really has been nothing to test. You only have to look at the posts in this area (dev) & the same posts are there day after day with no new packages if things are going to happen it will be at the 12th hour. I read a post early on & it said "will Intrepid be a dud" I thought that was very harsh so early on, I now feel that there might be some credence in the post.


Cary

---

### Post by msrinath80 on 2008-06-15
I second your thoughts. I think the only thing that really stands out in any 6-month release (of any distro) is a new version of GNOME. Sometimes, I wonder what GNOME is really trying to do in the name of simplicity. Just how much more simpler can it get? Why does GNOME try so hard to be so user-friendly to a two-year old?

---

### Post by caryb on 2008-06-15
To reinforce my thoughts this is the list of apps to be built for Intrepid.

[https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending]("https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending")


Cary

---

### Post by Exsecrabilus on 2008-06-15
> **caryb said:**
> To reinforce my thoughts this is the list of apps to be built for Intrepid.

[https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending]("https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending")


Cary
Augh, I really think the quality of development in Ubuntu is going down with every release.

I can't even find the Alpha1 release, is it even released?

---

### Post by caryb on 2008-06-15
Alpha 1 delayed for a few days! Why not rebrand 8.04.1 as Intrepid alpha 1:confused:


Cary

---

### Post by ShirishAg75 on 2008-06-15
> **caryb said:**
> To reinforce my thoughts this is the list of apps to be built for Intrepid.

[https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending](https://launchpad.net/ubuntu/intrepid/+builds?build_text=&build_state=pending)


Cary

Hi Cary, I don't know whether you were being sarcastic or not but horrors of horrors there is no such list of packages waiting to be merged. There is also possibility that these guys may be waiting to do the merges when GNOME 2.24 is out in September. Of course that doesn't give us as well as them much time to test GNOME, the kernel and few assorted packages here and there :(

---

### Post by autocrosser on 2008-06-15
I just looked at the current build set for X86 & it has 9269 results----

[https://launchpad.net/ubuntu/intrepid/i386/+builds?build_text=&build_state=all](https://launchpad.net/ubuntu/intrepid/i386/+builds?build_text=&build_state=all)

I also know that the next version of X is coming very soon--You might ask 23meg what he knows............

---

### Post by ladr0n on 2008-06-16
> **msrinath80 said:**
> Sometimes, I wonder what GNOME is really trying to do in the name of simplicity. Just how much more simpler can it get? Why does GNOME try so hard to be so user-friendly to a two-year old?

It seems to me that GNOME is considered more or less "finished" from a technical standpoint, and the GNOME devs are just trying to polish it up as much as they can.  If we can have a GUI that even a two-year old can sit down and use, without extraneous bloat or any hindrance to productivity, why not?

---

### Post by aamukahvi on 2008-06-16
> **caryb said:**
> we have no new kernel
Do you want newer than 2.6.26? Because that's in the repos.

---

### Post by msrinath80 on 2008-06-16
A two-year old would find playing with plastic toys to be an interesting recreational activity. Will you? No. Everything needs to be age-appropriate. Same with Computers. Two-year olds don't need to use the computer. They don't have the maturity to understand the whys and hows of computers in the first place. The point I'm trying to make is that GNOME has lost sight of its "simplicity" aim. They overshot the landing site a long time ago. You are absolutely correct when you say that technically GNOME is done. All I'm wondering is how much more polishing is necessary? Over simplification can also lead to a *loss* of productivity. One needs to be very careful in this respect.

---

### Post by Raptor45 on 2008-06-16
> **msrinath80 said:**
> A two-year old would find playing with plastic toys to be an interesting recreational activity. Will you? No. Everything needs to be age-appropriate. Same with Computers. Two-year olds don't need to use the computer. They don't have the maturity to understand the whys and hows of computers in the first place. The point I'm trying to make is that GNOME has lost sight of its "simplicity" aim. They overshot the landing site a long time ago. You are absolutely correct when you say that technically GNOME is done. All I'm wondering is how much more polishing is necessary? Over simplification can also lead to a *loss* of productivity. One needs to be very careful in this respect.

Do you have any specific complaints? Criticisms are one thing, aimless rants another.

---

### Post by msrinath80 on 2008-06-16
That's just my 0.02$ And no, I don't complain. That is a line I draw between being a free software advocate and an end user of proprietary code; one that I try not to cross.

All I'm trying to say is that GNOME is merely goofing around with unnecessary simplification much like Vista is today. Windows 2000 if you ask me is still the most stable Windows flavor I know of. KDE isn't doing much good either. Even if I pretend that the focus isn't shifting on enhancing eye candy in today's desktops (read:compiz and emerald), there's always the increasing "The user is an idiot" mentality among the GNOME devs. Pretty soon, we'll reach a point where they will start insisting that the end user should not have to access a terminal emulator at any point. Everything should be done only using the GUI and so on. Don't get me wrong. This is all nice and good in the interest of new and existing non-technical users. All I'm worried about is that this GNOME mentality will ultimately turn GNU/Linux into another Windows XP, ushering in a new breed of "converted idiots", if you will (No offense). One that will not know how to solve any problem without access to a user-friendly interface.

The thing that needs most attention in my opinion is keeping small memory footprints, increased responsiveness and I can't emphasize this any more, *stability*. Feature wise, GNOME has more than everything a basic DE should have. "Enlightenment" is a very good example of a nice and perfect DE.

What GNOME is trying to do is pull in all other kinds of esoteric software in an attempt to be a one-size-fits-all DE. This, we know from experience (read: the Windoze series) is no easy task and plus, it goes against the *nix philosophy - bunch of small programs working together to achieve a very stable yet productive system. For instance, Gnumeric is an excellent spreadsheet application in its own right. Back in my day (read: 1997-98), Gnumeric used to be a standalone GTK application that could be built independently. It still can be if you build from source with specific switches. However GNOME's popularity has biased GNU/Linux distributions into building it with libGNOME support thus making it more vulnerable. Bugs in the GNOME library can now affect Gnumeric thus potentially compromising stability.

To conclude, all I'm saying is that there is no shame in being just a very good DE and stopping it at that. Look at FVWM, Window Maker etc. There's not much development going on. Yet those are the most stable Window Managers. Why? Because they are focused projects that concentrate on specific and limited goals and they do a good job at that. This is what keeps *nix stable. A group of well focused and well written programs that work together. The emphasis being on *group*.

---

### Post by durand on 2008-06-17
Just my opinion - FVWM and Window Maker don't seem to have any interesting features...I'd rather have a featureful and interesting(/fun) desktop than one which is just stable and nothing else.

I like enlightenment a lot but I can never use a environment that doesn't have proper icons on the desktop, ties programs together nicely and is simple but also feature full. Maybe it is just me but I really like the way GNOME is heading.

---

### Post by cariboo on 2008-06-17
I see on slashdot this morning that Wine 1.0 was released are we going to see this in intrepid?

Jim

---

### Post by Raptor45 on 2008-06-17
> **cariboo907 said:**
> I see on slashdot this morning that Wine 1.0 was released are we going to see this in intrepid?

Jim

I can't see any reason why not. We're not anywhere close to a freeze.

---

### Post by Stochastic on 2008-06-17
What do you guys think about modularizing the default installation a bit more?  Kinda like the way Debian used ?tasksel? (I think that's how it's spelled) back when I tried it.  For instance give the user an option to check/uncheck certain blocks of programs at installation time (webcam tools, multimedia production suite, programming suite, gaming suite, educational tools, scientific tools, etc..)?  I think there should still be a base default, but giving these extra options in the installer would be nice (probably most feasible to utilize an internet connection and download these via the repos).

Also, is there any consideration being made to providing a suite of CDs or DVDs for those who don't have a (high-speed) internet connection to still access the repositories?

---

### Post by cariboo on 2008-06-17
I personally like tasksel but for new users it would have to be the only way for them to do an initial installation, because if you check the newbie section most of them are confused with the many different ways of install programs.

Actually that's another thing I've been thinking about, if there was a way to run a video tutorial on first run after installation and give the newbies a leg up on using their shiny new Ubuntu distibution.

Jim

---

### Post by Gina on 2008-06-17
The Minimal Install (mini.iso) gives you a choice of software to install and downloads your selection from the repos at install time.  The Hardy mini.iso is just 9.5MB and installs just the base system and the software selector app.

---

### Post by psyke83 on 2008-06-17
> **Gina said:**
> The Minimal Install (mini.iso) gives you a choice of software to install and downloads your selection from the repos at install time.  The Hardy mini.iso is just 9.5MB and installs just the base system and the software selector app.

That's interesting, I thought it just installed core packages.

This idea is much better suited to the alternate cd, as it contains the actual deb packages and not a preinstalled filesystem image (the live cd). In fact, I don't think it's possible for the live install without a lot of hacking (profiling deb package contents and deliberately including/excluding what gets copied during install).

---

### Post by Gina on 2008-06-17
More info [HERE]("https://help.ubuntu.com/community/Installation/MinimalCD")  (Forgot to add the link)

---

### Post by DeliriousNor on 2008-06-18
What about adding an option in the installation prosess where you can choose not to install the ubuntu-desktop, but only pure gnome, then everybody would be happy!

---

### Post by YaroMan86 on 2008-06-18
> **DeliriousNor said:**
> What about adding an option in the installation prosess where you can choose not to install the ubuntu-desktop, but only pure gnome, then everybody would be happy!

That strikes me as a rather difficult thing to do. I believe the GNOME packages have ubuntu-desktop set as a dependency as far as Ubuntu is concerned. So, in theory, that would require a considerable amount of space just for an identical GNOME package set that doesn't have ubuntu-desktop as a dependency. That's probably too much space for comfort.

You could always get ahold of a distro that doesn't install a GUI by default and then install GNOME on top of that, perhaps? I'm not sure.

---

### Post by Exsecrabilus on 2008-06-18
This has been an idea existing at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) for a long time, but I'll mention it here anyway.

When you install Windows, it completely wipes out all traces of other operating systems in the GRUB menu.

What the Live CD needs to come with is a feature that just establishes a new GRUB for Ubuntu, no?

There are ways to fix it, but some people find them complicated and many don't know it's possible.

---

### Post by YaroMan86 on 2008-06-18
> **Exsecrabilus said:**
> This has been an idea existing at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) for a long time, but I'll mention it here anyway.

When you install Windows, it completely wipes out all traces of other operating systems in the GRUB menu.

What the Live CD needs to come with is a feature that just establishes a new GRUB for Ubuntu, no?

There are ways to fix it, but some people find them complicated and many don't know it's possible.

I agree, although repairing the MBR using GRUB isn't too difficult provided one follows [this HOWTO right here.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by stereo_steve on 2008-06-19
> **davbren said:**
> 

P.S. I'm not really seeing what opensuse has that ubuntu doesn't...

A deal with Microsoft? ie we should avoid it like the plague!

---

### Post by amano on 2008-06-19
> **Exsecrabilus said:**
> This has been an idea existing at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) for a long time, but I'll mention it here anyway.

When you install Windows, it completely wipes out all traces of other operating systems in the GRUB menu.

What the Live CD needs to come with is a feature that just establishes a new GRUB for Ubuntu, no?

There are ways to fix it, but some people find them complicated and many don't know it's possible.

Yes. They should add a shortcut/starter to the LiveCD desktop that calls a script which fixes the MBR. That should be easy to do and is certainly worth the effort.

And you do not have to find a how-to first, which could be problematic beacuse you rely to a working windows internet connection then.

---

### Post by chrisccoulson on 2008-06-19
> **DeliriousNor said:**
> What about adding an option in the installation prosess where you can choose not to install the ubuntu-desktop, but only pure gnome, then everybody would be happy!
Can't happen with the existing installer, as it basically extracts an image of a default system on to your hard disk (complete with ubuntu-desktop) and then does some post-install configuration, as opposed to installing a list of deb packages (which would be configurable)

The alternate install CD installs a list of packages instead of extracting a generic image, so it would be theoretically possible with that.

---

