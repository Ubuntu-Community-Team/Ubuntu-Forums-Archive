---
title: "Lucid Lynx Alpha 2 Released"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-01-15
Alpha 2, the second milestone of the Lucid Lynx development cycle leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-January/000665.html") on the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce")
[*] [Technical Overview]("http://www.ubuntu.com/testing/lucid/alpha2")[/list]

---

### Post by kahumba on 2010-01-15
I think someone should update (fix typo) the Alpha 2 page at:
[http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues]("http://www.ubuntu.com/testing/lucid/alpha2#Known%20issues")

the line "sudo nvidia-config"
with "sudo nvidia-xconfig"

Only non-newbies will figure out that that's just a typo, and not a Ubuntu issue.

---

### Post by Psumi on 2010-01-15
I see they really are planning full removal of hal. A bunch of programs (like xfburn) will not work because of this.

---

### Post by xebian on 2010-01-15
> **Psumi said:**
> I see they really are planning full removal of hal. A bunch of programs (like xfburn) will not work because of this.

They said A2 has full removal of hal but I still see hal processes.  So not sure which is true or not.

---

### Post by rubenverweij on 2010-01-17
Is it already possible to have nouveau working on lucid? I couldn't install it in alpha1, it's the only thing that is keeping me back now.

---

### Post by jerrylamos on 2010-01-17
Progress....

A2 CD live won't boot, initial boot screen freezes no matter what is tried on the linux boot line or what keystrokes are used.

A1 updated to A2 level won't run any time at all unless "nomodeset" and "vesa" are used.

A2 Alternate installed O.K., has been running! (careful! Don't update it, it's running!  "If it ain't broke, don't fix it!")

Linux version 2.6.32-10-generic (buildd@palmer) (gcc version 4.4.3 20100105 (prerelease) (Ubuntu 4.4.2-8ubuntu2) ) #14-Ubuntu SMP Thu Jan 7 17:38:40 UTC 2010

So on this machine the fix is the A2 alternate install.

Jerry

---

### Post by Digikid on 2010-01-17
I was told that the removal of HAL means that there is no more automount.

Please tell me that this is not so.  :(

---

### Post by andrewabc on 2010-01-17
> **Digikid said:**
> I was told that the removal of HAL means that there is no more automount.

Please tell me that this is not so.  :(

If that's true then there better be a good tutorial on how to make that happen. Otherwise can't use ubuntu. SSD + hard drive having hard drive partitions mount on boot makes life easy as it's where all my data goes.

I've messed with fstab many times and it is a big clusterfark.

---

### Post by PaulInBHC on 2010-01-17
Now I've wasted 2 CDs and a few hours of time. A2 386 Live does nothing, A2 386 alt gives me the install, boots to black screen, hear bongos, type name return, type password return, get music, black screen.

---

### Post by Ibidem on 2010-01-18
That's USB automount.  You would need to manually mount flash drives OR install "usbmount" (universe).
Hard drive automount is kernel/init stuff, with fstab to control it. But that has gotten maybe a little bit better in Lucid.

Ibidem

---

### Post by Psumi on 2010-01-18
> **Ibidem said:**
> That's USB automount.  You would need to manually mount flash drives OR install "usbmount" (universe).
Hard drive automount is kernel/init stuff, with fstab to control it. But that has gotten maybe a little bit better in Lucid.

Ibidem

That sucks, I need my USB to automount for me.

---

### Post by Ibidem on 2010-01-18
As stated: install usbmount.
It's a tiny download, with no dependencies to speak of.
It works even if your GUI doesn't.

sudo apt-get install usbmount

---

### Post by andrewabc on 2010-01-18
> **Ibidem said:**
> As stated: install usbmount.
It's a tiny download, with no dependencies to speak of.
It works even if your GUI doesn't.

sudo apt-get install usbmount

"Dumb" users won't know to do that. They'll just think they're usb won't show up and hate ubuntu. Yet another program I'll have to remember to install after installing.

It's something that should be installed by default. Especially if small program, there is currently lots of space on cd. Someone file a bug?

---

### Post by VMC on 2010-01-18
> **Digikid said:**
> I was told that the removal of HAL means that there is no more automount.

Please tell me that this is not so.  :(

Mine is still installed:
```
$ aptitude show hal
Package: hal
State: installed
Automatically installed: no
Version: 0.5.14-0ubuntu2
```

When does the removal take place. Running A2 and updated.

---

### Post by Psumi on 2010-01-18
> **andrewabc said:**
> Someone file a bug?

All the launchpad people will do is tell you to go on the mailing list.

I hate mailing lists. And the brainstorm people will just make sure that your idea is not an idea regardless if it isn't a bug or not.

---

### Post by 23meg on 2010-01-18
> **VMC said:**
> Mine is still installed:
```
$ aptitude show hal
Package: hal
State: installed
Automatically installed: no
Version: 0.5.14-0ubuntu2
```

When does the removal take place. Running A2 and updated.

[http://ubuntuforums.org/showpost.php?p=8671630&postcount=16](http://ubuntuforums.org/showpost.php?p=8671630&postcount=16)

---

### Post by 23meg on 2010-01-18
[QUOTE=Psumi]All the launchpad people will do is tell you to go on the mailing list.[/QUOTE]

That's what (correctly) happens only in [cases]("https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug") where the issue at hand is fit for discussing on a mailing list, rather than a bug tracker.

---

### Post by VMC on 2010-01-18
> **23meg said:**
> [http://ubuntuforums.org/showpost.php?p=8671630&postcount=16](http://ubuntuforums.org/showpost.php?p=8671630&postcount=16)

I've already read that link and it doesn't answer my question as to when Ubuntu will remove hal. This imply's that I have to do this on my own. Will future releases keep hal or not?

---

### Post by 23meg on 2010-01-18
> **VMC said:**
> I've already read that link and it doesn't answer my question as to when Ubuntu will remove hal. This imply's that I have to do this on my own. Will future releases keep hal or not?

HAL will not be part of the default installation in future releases, and AFAIK is only pulled in as a "Recommends" of PiTiVi in Lucid for now. It may also have been pulled in as the dependency for a non-default application you installed.

---

### Post by VMC on 2010-01-18
> **23meg said:**
> HAL will not be part of the default installation in future releases, and AFAIK is only pulled in as a "Recommends" of PiTiVi in Lucid for now. It may also have been pulled in as the dependency for a non-default application you installed.

Thanks for the answer. I didn't install anything except a fresh install of ubuntu alpha 2. I wonder why aptitude shows it installed?

At any rate I backed my partition and will try the removal as see what happens.
Thanks.

---

### Post by Tatty on 2010-01-20
> **Digikid said:**
> I was told that the removal of HAL means that there is no more automount.

Please tell me that this is not so.  :(

HAL is being replaced by devicekit.  [http://en.wikipedia.org/wiki/DeviceKit](http://en.wikipedia.org/wiki/DeviceKit)

Things will still automount, it is just that HAL has been largely superseded by other packages, and the last functions which HAL was still needed for have been rewritten as devicekit.

---

### Post by PaulInBHC on 2010-01-20
> **PaulInBHC said:**
> Now I've wasted 2 CDs and a few hours of time. A2 386 Live does nothing, A2 386 alt gives me the install, boots to black screen, hear bongos, type name return, type password return, get music, black screen.

Noone has commented on my problem. Should I just wait for the RC and see if I waste another CD?

---

### Post by andrewabc on 2010-01-20
> **PaulInBHC said:**
> Noone has commented on my problem. Should I just wait for the RC and see if I waste another CD?

Purchase cd-rw
No more wasted cd. It works good for me. Every new release I update all my CDs with different versions.

---

### Post by espen77 on 2010-01-20
> **andrewabc said:**
> Purchase cd-rw
No more wasted cd. It works good for me. Every new release I update all my CDs with different versions.

Havent used CD's in ages. Found this guide [(http://www.panticz.de/MultiBootUSB)]("http://www.panticz.de/MultiBootUSB") on how to make a USB-Pen where you can just store the iso's and update grub.cfg to make them bootable.

---

### Post by balduin on 2010-01-27
I'm surprised how stable the current alpha versions are compared to 9.10's alphas. Keep up the good work!

---

### Post by Siljrath on 2010-01-27
i was poking around looking at [http://cdimage.ubuntu.com/releases/lucid/alpha-2/](http://cdimage.ubuntu.com/releases/lucid/alpha-2/) and other pages, trying to find the minimal.   is there no minimal in alpha and beta stages?   when does the minimal usually show up?   or did i overlook it?
what'd be the nearest to what i'm looking for?  alternative cd?

---

### Post by VMC on 2010-01-28
> **Siljrath said:**
> i was poking around looking at [http://cdimage.ubuntu.com/releases/lucid/alpha-2/](http://cdimage.ubuntu.com/releases/lucid/alpha-2/) and other pages, trying to find the minimal.   is there no minimal in alpha and beta stages?   when does the minimal usually show up?   or did i overlook it?
what'd be the nearest to what i'm looking for?  alternative cd?

It looks like only releases have mini.iso. Try looking around [here]("https://help.ubuntu.com/community/Installation/MinimalCD").

---

### Post by jerrylamos on 2010-01-28
> **balduin said:**
> I'm surprised how stable the current alpha versions are compared to 9.10's alphas. Keep up the good work!

Maybe for you.

This one just hung again today, all updated to the latest.

It uses intel (ever hear of Intel? must be some small unknown company with few products out ...) video graphics, the only way it runs at all is with "nomodeset" on the boot linux line, and with xorg.conf "vesa".

Between Compiz changes for Intrepid and KMS things have been pretty "unstable" for my various intel and ati pc's.

Jerry

---

### Post by Siljrath on 2010-01-28
@VMC,
cheers, i have, and will again be looking there often.  only looking for whats happnin with 10.04 tho.
it's just the core i'm after at the moment.  not fussed on the fluff.


> **jerrylamos said:**
> Maybe for you.

This one just hung again today, all updated to the latest.

It uses intel (ever hear of Intel? must be some small unknown company with few products out ...) video graphics, the only way it runs at all is with "nomodeset" on the boot linux line, and with xorg.conf "vesa".

Between Compiz changes for Intrepid and KMS things have been pretty "unstable" for my various intel and ati pc's.

Jerry

oh great.  :/   just one more thing pushing me archward.  thnx alot ubloatu.  ;p   doesnt look good for my poor intel graphics laptop.

---

### Post by thelostgraviton on 2010-01-31
[http://cdimages.ubuntu.com/netboot/lucid/](http://cdimages.ubuntu.com/netboot/lucid/)

---

### Post by R33D3M33R on 2010-01-31
Who must I contact to get a newer package into Lucid Lynx? Currently I'm talking about the game hex-a-hop. The version in the repository is really old (year 2007), there is a much improved version with sound and music available on sourceforge: [http://hexahop.sourceforge.net/](http://hexahop.sourceforge.net/)

---

### Post by andrewabc on 2010-01-31
> **R33D3M33R said:**
> Who must I contact to get a newer package into Lucid Lynx? Currently I'm talking about the game hex-a-hop. The version in the repository is really old (year 2007), there is a much improved version with sound and music available on sourceforge: [http://hexahop.sourceforge.net/](http://hexahop.sourceforge.net/)

Usually filing a bug works.

[http://packages.ubuntu.com/lucid/hex-a-hop](http://packages.ubuntu.com/lucid/hex-a-hop)
[https://launchpad.net/ubuntu/+source/hex-a-hop/+bugs](https://launchpad.net/ubuntu/+source/hex-a-hop/+bugs)

Make sure to be descriptive and provide link to the website.
They sometimes want a diff(?) but ubuntu 10.04 is early in development build, so hopefully they just put in new version.
Have you gotten new version to work in lucid? Usually a plus if you've got it working.

---

### Post by R33D3M33R on 2010-02-01
Thank you for your reply. I have submitted the bug and I sure hope they will upgrade it.

---

### Post by bigal50 on 2010-02-01
[B]FYI:
64 bit[/B]

I have a dual cpu Xeon 2.80 GHz server and I tried to boot with the 64 bit LiveCD and was told that I had the wrong architecture. I can install off the Lucid 64 bit server CD

2-3-10
I am not real sure that the Xeon's are 32 bit. After installing the server did not act just right and when I use 32 bit anything all seems to work okay. At 1st I thought it was a bug but now I don't believe the problem was/is Lucid but the  system itself. Anyway sorry for jumping the gun here. If I could I would just delete this post as to not confuse someone else.

---

### Post by mdshaver on 2010-02-09
I just downloaded the 64-bit Alpha 2 and ran all the updates (including the partial upgrade) and I have to say I am very happy! I am using a cheap eMachines laptop which has an Atheros AR9285 wifi chip and an ATI Radeon HD 3200 video card. These are the two biggest problems for many distros. Although I could previously get wifi with jaunty (when installing the wifi backports), it did not work as well as Mandriva. Although I could install the proprietary ATI driver on Ubuntu, I could not on Mandriva. The proprietary driver had a lot of problems anyways. Now I am using the open source ATI with 3D acceleration! I've got my newer programs from the repos (e.g., Qtiplot) and wifi works better than in Jaunty. No problems yet (fingers crossed). I'm using this alpha release for my day-to-day operations with any important files synced to Dropbox in case of a crash! Again, very pleased so far!

---

### Post by Kenny_Strawn on 2010-02-09
I am having a little bit of trouble with clean installs, as on the CD/USB-FD, 566 packages are obsolete.

---

### Post by VMC on 2010-02-09
> **Kenny_Strawn said:**
> I am having a little bit of trouble with clean installs, as on the CD/USB-FD, 566 packages are obsolete.

Not sure what CD's, Floppies, and USB has to do with obsolete packages.
When you say clean install. Is this using either alpha2 or one of the daily-lives?

How are you installing Ubuntu Lucid? What steps.

---

### Post by gibbylinks on 2010-02-10
> **PaulInBHC said:**
> Noone has commented on my problem. Should I just wait for the RC and see if I waste another CD?

Try using "nomodeset" on the grub command line. I'm having to use this currently otherwise I get the same thing.

I still can't use the "alternative" logins (alt+f1 etc) as I just get a black screen.

---

### Post by Kenny_Strawn on 2010-02-11
> **VMC said:**
> Not sure what CD's, Floppies, and USB has to do with obsolete packages.
When you say clean install. Is this using either alpha2 or one of the daily-lives?

How are you installing Ubuntu Lucid? What steps.

Using Alpha 2. Do you mean that there are weekly builds of Ubuntu, and especially Lucid? Please give me a link to the latest weekly build.

---

### Post by sparker256 on 2010-02-11
> **Kenny_Strawn said:**
> Using Alpha 2. Do you mean that there are weekly builds of Ubuntu, and especially Lucid? Please give me a link to the latest weekly build.

[http://cdimage.ubuntu.com/daily-live/current/?C=N;O=A](http://cdimage.ubuntu.com/daily-live/current/?C=N;O=A)

Bill

---

### Post by VMC on 2010-02-11
> **Kenny_Strawn said:**
> Using Alpha 2. Do you mean that there are weekly builds of Ubuntu, and especially Lucid? Please give me a link to the latest weekly build.

The're not weekly builds, the're daily builds, and the link that sparker gave you is good.

---

### Post by cookiecruncher on 2010-02-12
...and here is a link to Kubuntu (daily build)

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

### Post by degarb on 2010-02-15
> **andrewabc said:**
> "Dumb" users won't know to do that. They'll just think they're usb won't show up and hate ubuntu. Yet another program I'll have to remember to install after installing.

It's something that should be installed by default. Especially if small program, there is currently lots of space on cd. Someone file a bug?

+1  

These aren't dumb users, rather users that know that a good OS should just install itself (They don't care if it is on 2 cds.), and then, get out of the way to making the machine pay for itself.

An advanced Linux user, or anyone that has gone native, just gets numb to jimmies and workarounds that keep Ubuntu from over taking Windows.   My first impression was Ubuntu--the install, the interface, the group-- is just about 4 road blocks away from being the OS anyone would love  (a few things not made obvious to new users).   Heck, even a single oversight of something that an experience user would take for granted--even defend--, could mean the difference between .1 percent of world user-base and %66 of world user-ship of the OS.

Auto mounting is a non negotiable part of getting an OS to become successful.  Marketsharewise, that is.

I also have to mention that, without domination, the OS has diminished usefulness.  Take voice recognition, for example.  I can point to about a dozen aps, where there are no good alternatives on Linux + Wine.  To me, Ubuntu is ideal for the additional computers in a business or home of an advanced computer user, or ideal for a light to moderate computer user.  I would like to see Ubuntu replace the Microsoft altogether, and every commercial program have a deb port. 

As I said before, you cannot build a house and have doors and windows that are hard to open and shut, floors that squeak, outlets that constantly trip.  I don't care if you give the house away for free.  This isn't the mindset of the consumer. If on first entry of the house (if they get the over their skepticism), they cannot get the front door key to work, they will move on to a real-estate agent.

---

### Post by jerrylamos on 2010-02-15
> The Linux directory system is a messy desk of a genius-- designed in a time where the system ruled the user, and not the user ruling the system. Seriously, consult your elders on this one. 

I don't know about the rest of you, but the Windows "Registry" system is such a mess that the "experts" say the only way to get it going as new is to install periodically.  Of course, with the $$$$$$ Microsoft and $$$$$$ applications that's a mess for me.

Jerry

---

### Post by putxi on 2010-02-16
Hi!

I can't find a LAPTOP version for Lucid alpha, does it exist?

I've just acquired a dell laptop (Core i5-520M) and have read on an other thread that 10.04 version was the one that suits best for that box, after some trials (see [post]("http://ubuntuforums.org/showthread.php?p=8828880&posted=1#post8828880")).

Is it the desktop version which i shoud install?

Thanks in advance!

Regards,
jordi

---

### Post by andrewabc on 2010-02-16
There is no such thing as laptop version.

If you've got a high end laptop with intel corei5 you want 64bit desktop.

Also don't get alpha 2, get a daily.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Hmm, they are oversized so won't fit on CD if that's how you normally do it. You can always make liveusb or burn to a dvd if needed. To test and see what works before installing.
Or wait a day or so until they fix that problem.

---

### Post by VMC on 2010-02-16
> **andrewabc said:**
> There is no such thing as laptop version.

If you've got a high end laptop with intel corei7 you want 64bit desktop.

Also don't get alpha 2, get a daily.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Hmm, they are oversized so won't fit on CD if that's how you normally do it. You can always make liveusb or burn to a dvd if needed. To test and see what works before installing.
Or wait a day or so until they fix that problem.

Yea, your right. Now all the dailies(daily-live & daily) have past CD size limit. See the red warning messages. I have always used DVD/RW's so it doesn't effect me. Now though, I use USB flash so its a non issue, but others need to be warned.

Edit: I just read carfully the warning regarding oversize. Says there's a bug?! Bug where? See below printout.

[COLOR="Red"]Warning: This image is oversized (**which is a bug**) and will not fit onto a standard 700MB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.[/COLOR]

---

### Post by ratcheer on 2010-02-16
> **VMC said:**
> Yea, your right. Now all the dailies(daily-live & daily) have past CD size. See the read warning messages. I have always used DVD/RW's so it doesn't effect me. Now though, I use USB flash so its a non issue, but others need to be warned.

I have been formatting my DVD+RW disk each time before copying the new daily iso image to it. Is this necessary, or can I just overwrite it?

Thanks,
Tim

---

### Post by ranch hand on 2010-02-16
I think that the idea of a company telling you that you need to install an alpha version is not a good thing.

I would call them and ask if they are serious.

Install 9.10 unless you are really up to testing an alpha release.  Expect breakage in the OS at this point.  Perhaps problems installing.

This really is the stupidist suggestion from a company that I have heard in some time.

---

### Post by IanW on 2010-02-16
I've found a good way to keep an up-to-date install disk is as follows:-

1: Download Latest daily image from [http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")
2: Install "zsync" using your package manager of choice
3: Run "zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync"
4: Run USB creator against resulting image, using a USB stick of >1GB.
5: 24 Hrs later, go to 3.

Using zsync instead of getting a fresh image greatly reduces the amount of bandwidth both you & Canonical pay to use.

---

### Post by putxi on 2010-02-16
Hi! Thanks for the info ...

>> I had already burn a current image of 10.04 on a dvd, this morning, no need to wait for cd sized. But thanks anyway.

>> It's really risky installing an alpha on a laptop i'll use professionally ... TRUE
The temptation is becasue of this information:
[Ubuntu 9.10 64 bit install problems on Dell Studio 1558]("http://ubuntuforums.org/showthread.php?p=8828880&posted=1#post8828880") 

>> I'll try both of them and see ...
The thing is **9.10** (estability but some hw incompatibilities) against** 10.04** (non-stable but better hw compatibility) ???
It depends on the "size" of this (in)estability and the (in)compatibility :D

Luckily, **ranch hand**, i finally have the desktop (it comes from [that post]("http://ubuntuforums.org/showthread.php?p=8812225#post8812225")) running quite nicely with the 9.10. Thanks!
So, it's time to change the patient, now the laptop. 

I'll keep you updated.

Salut,
jordi

---

### Post by ratcheer on 2010-02-16
> **IanW said:**
> 

Using zsync instead of getting a fresh image greatly reduces the amount of bandwidth both you & Canonical pay to use.

Well, I would hope we all are doing that. I am.

Tim

---

### Post by putxi on 2010-02-16
> **ratcheer said:**
> Well, I would hope we all are doing that. I am.

Tim

Is it enough a 2GB usb to work with zsync?
It could be the fist time i use an alpha release...

Salut,
jordi

---

### Post by ratcheer on 2010-02-16
> **putxi said:**
> Is it enough a 2GB usb to work with zsync?
It could be the fist time i use an alpha release...

Salut,
jordi

I work with the iso's and zsync on my hard drive, then copy the end-result iso to the bootable media.

Tim

---

### Post by aviramof on 2010-02-16
tell me is there any information as to when can we expect gflrx driver for ati screen card?
 
my os crashed again because of something related to wmv real media codecs i think
it called pulse something any way installing the os is no problem but frankly without
ati driver i can't do much with this os compiz doesn't fully work and i can't see movies
in my lcd tv i can create dual view but the tv screen is pink like solorize or something 
like this but with pink color maybe because it's pal tv not ntsc. 
 
any way without solving this problem i would still need windows 7 so i can't use ubuntu 24/7 
and as such i see no reason to reinstall it again once i have this driver i don't care if it's not 
final i would be able to use it non stop.
 
thanks in advance.

---

### Post by VMC on 2010-02-16
> **IanW said:**
> I've found a good way to keep an up-to-date install disk is as follows:-

1: Download Latest daily image from [http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")
2: Install "zsync" using your package manager of choice
3: Run "zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync"
4: Run USB creator against resulting image, using a USB stick of >1GB.
5: 24 Hrs later, go to 3.

Using zsync instead of getting a fresh image greatly reduces the amount of bandwidth both you & Canonical pay to use.

This is exactly how I have been doing it for quite some time. Except step#5. I wait a few days or a week. Actually I found doing it on Sunday is best because there is fewer updates.

Also I have a Zsync folder on an NTFS partition that I have been using. On a whim I decided to use a linux ext4 partition instead, just as a test. Unbelievable it was much faster. I was thinking the ntfs-3g process is not needed on linux reads/writes. It might, and probably is, a fluke. I'll know more come next Sunday.

---

### Post by VMC on 2010-02-16
> **ratcheer said:**
> I have been formatting my DVD+RW disk each time before copying the new daily iso image to it. Is this necessary, or can I just overwrite it?

Thanks,
Tim

It your burning an ISO using Brasero, it automatically erases the disk. In fact it won't write otherwise. 

If your talking about a total format, I rarely do that. Only when I have errors will try that. It takes around 17 minutes for a complete format. Usually that fixes my errors, and I only have errors on large files, like DVD movies.

---

