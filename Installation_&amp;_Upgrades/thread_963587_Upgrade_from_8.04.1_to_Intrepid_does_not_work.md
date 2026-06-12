---
title: "Upgrade from 8.04.1 to Intrepid does not work"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by erlguta on 2008-10-30
I have follow the upgrade instrucctions:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I select normal releases and it only install 1 package and uninstall 1 package??!!
Then it hangup in clening...
I reboot the system and i can't start administration > software updates.
If i start in console 'sofware updates' i can see:

$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException

If i go to System > Update manager it says me the he must do one Partial actialization...and then this error:

An upgrade from 'intrepid' to 'hardy' is not supported with this tool.

:confused::confused:

From intrepid to hardy???

What to do now?

Tahnk you.

IMHO. Honestly i do not know how ubuntu doing things so bad version after version and with so many serious errors can continue to have this legion of fans. But people already are getting tired of your enthusiastic marketing campaigns (Wow! Best new intrepid than EVER!) that do not correspond at all with reality.

Sorry to be so hard, but I think that here there is much enthusiasm but also a lot of incompetence and a lot of improvisation.

---

### Post by Noxn on 2008-10-30
Mine is stuck in cleaning too...

But i didnt restart until now, im waiting like 1 hour, stuck in this cleaning.

Help?!?

---

### Post by jaznow on 2008-10-30
I've waited for long time, and cleanup worked fine.

It just takes loooong time, if you notice the system usage of hard drive, you will see that its reading all the time the harddrime, its actually working.
After that long wait (like 1 hour...) it asks you to delete some outdated packages, i've clicked yes, after deleting, it asks you to rebbot system to continue the upgrade...

After restart, my system displays this last message: 

Running local boot scripts (/etc/rc.local),and does nothing...

I guess the update server is too busy to answer so many people updating...


Thanks!.

---

### Post by revoman3 on 2008-10-30
Try downloading the ISO first then burn it a disc and then update your system using that disc, that's what I do :)

---

### Post by Noxn on 2008-10-30
Im waiting, and i noticed that cpu and Hd is working.

I hope it stops cleaning ...

---

### Post by erlguta on 2008-10-30
> **Noxn said:**
> Mine is stuck in cleaning too...

But i didnt restart until now, im waiting like 1 hour, stuck in this cleaning.

Help?!?

And installed to you a 1 single package how me?. 
Wow thats a super intrepid installation!. 
With a single package required is installed all those super improvements which canonical announce in that way so sensationalism.
I have long time with ubuntu and I've seen everything, but honestly, I think that my patience is running out.

---

### Post by Noxn on 2008-10-30
Upgrade from a cd?

But my pc IS already updating, but stuck or something, gonna wait max 2 hours more...
Dont want to shutdown now and risk something.

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> Im waiting, and i noticed that cpu and Hd is working.

I hope it stops cleaning ...

Yup, it will, tell me if everything is ok after that, mine just displays that "running scripts /etc/rc.local" and does nothing...

---

### Post by Noxn on 2008-10-30
Okay

---

### Post by erlguta on 2008-10-30
> **Noxn said:**
> Okay

But it should not say installing packages instead of cleaning?. So it does not hang?. 
It is little clever, no?
Like i stopped the clening porcess and i rebooted the system, I will try to update like the old style. aptitude safe-& & aptitude upgrade full-upgrade.

---

### Post by jaznow on 2008-10-30
> **erlguta said:**
> But it should not say installing packages instead of cleaning?. So it does not hang?. 
It is little clever, no?
Like i stopped the clening porcess and i rebooted the system, I will try to update like the old style. aptitude safe-& & aptitude upgrade full-upgrade.
It actually removes OBSOLETE packages , so you can install the new ones without conflicts... :)

---

### Post by Noxn on 2008-10-30
Uhmm, dude, cleaning means it deletes the installers etc i think, if its cleaning the installing stuff is already done...


edit: Got ninjad!


edit2:
CLEANING STOPED
its now continuing the update :D

---

### Post by jaznow on 2008-10-30
Hey, what i've investigated so far,

After the cleaning, as I said, it reboots and i'm seeing the /etc/rc.local script thingui, but i've noticed screen blinks for like 4 times Edit:(so i must guess, it is trying to start X session to continue its upgrade...)

I have gone to another console using Alt+F1, logged in, and tried to issue command startx, it fails 'couse it cant find the ATI module (accelerated...), and it wont start X.

So, what i'm trying now is to find the way to repair /etc/X11/xorg.conf so it WILL start the darn X, so i can continue my upgrade, but it this time have not been able to manage it to make it start...

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> Uhmm, dude, cleaning means it deletes the installers etc i think, if its cleaning the installing stuff is already done...


edit: Got ninjad!


edit2:
CLEANING STOPED
its now continuing the update :D

Hey, now what, after reboot? O_O

---

### Post by Noxn on 2008-10-30
Nothing, its still updating, i didnt restart.

After the stucking, its now removing something, but at least its not stuck.

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> Nothing, its still updating, i didnt restart.

After the stucking, its now removing something, but at least its not stuck.
Ok, i want to know what does do after reboot...

Mine is failing to start X (i had ATI propietary driver before upgrading...)

---

### Post by Noxn on 2008-10-30
Okay, just finished and rebooted,

Now im stuck in CLI and i could log in,

But still stuck in CLI

StartX didnt help

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> Okay, just finished and rebooted,

Now im stuck in CLI and i could log in,

But still stuck in CLI

StartX didnt help

Same problem than me... i guess lot of people will have same problem...

---

### Post by Noxn on 2008-10-30
Help us please :(

---

### Post by jaznow on 2008-10-30
Can you tell me wich error displays when you try to do, startx from a CLI?

Mine shows that couldnt find "ati" module, and "mouse" module, both give error, and fail...

---

### Post by Noxn on 2008-10-30
Dunno, something about my mouse, and screen, and stuff.

---

### Post by evinart on 2008-10-30
Still waiting and it's still cleaning up...

---

### Post by Noxn on 2008-10-30
OH! and i remember that the update asked me about removing "Obsolete" packages or something!
Maybe that thing just deleted all my programs? becouse i cant even start Mplayer from the CLI!

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> OH! and i remember that the update asked me about removing "Obsolete" packages or something!
Maybe that thing just deleted all my programs? becouse i cant even start Mplayer from the CLI!

Can you tell me if you have an ATI video card? i think they dropped support for some ATI video cards...

---

### Post by Noxn on 2008-10-30
i dont know... but i think not

But that doesnt explain that my mplayer is gone!

---

### Post by tomszyszko on 2008-10-30
I started the update 2 hours ago, but it is stuck on package 1871, and every 5 mins it says that it is downloading at 243b/s, 39 days 21 hours and then it disappears. All the other files were downloading quickly. Is there any way to get it to skip this file??:(:(:(

---

### Post by Noxn on 2008-10-30
Dudes, i got an idea, maybe it installed the SERVER EDITION in the update, instead of the DESKTOP edition?!?!?!?!?!


WE ARE DOOMED :(((((

---

### Post by Noxn on 2008-10-30
is there anyway repairing/something from the CD??

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> is there anyway repairing/something from the CD??
I'm downloading the 8.10 dvd at this time, i'm going to try! :D

---

### Post by Noxn on 2008-10-30
Okay, im downloading too, tell me if you got any luck.



WE NEED SOME HELP HEREEEE!

---

### Post by meatlegs on 2008-10-30
I've just downloaded the Alternate cd ISO. I plan on upgrading from Hardy by mounting it on my hard drive.
Has anyone else tried this method with success??

p.s. the alternate ISO downloaded in less than 30 min! woot!!

---

### Post by jaznow on 2008-10-30
> **Noxn said:**
> Okay, im downloading too, tell me if you got any luck.



WE NEED SOME HELP HEREEEE!

It will take some time to download, i'll go out of office ,have dinner, have sleep, and tomorrow morning 7.A.M (spain local time) will try to solve this mess,... my working computer is all messed up becouse of this update... darn! i got too much confindence on ubuntu... now i'm stuck on this without being able to work!
Hope i can solve this tomorrow

See ya guys, good luck!

---

### Post by Noxn on 2008-10-30
Cya

---

### Post by Noxn on 2008-10-30
Is it possible that the thing with "Obsolete programs etc" just uninstalled my Lynx, firefox, mplayer, and like everything else, just to boot into the cli?

---

### Post by Zyphrexi on 2008-10-30
I dunno about you guys, but I'm on intrepid development version, and for whatever reason the package sources won't load. I wouldn't do a dist-upgrade without a complete updated source. I figure the server load is really heavy, so I'm grabbing the iso through a torrent. You can mount an iso and use it as a source you know.

It's always slow like this with a new release, so it's best to be patient.

---

### Post by Noxn on 2008-10-30
At the moment am still stuck in the CLI...

---

### Post by mstorin on 2008-10-30
Mine hung on cleaning for hours but finally finished and now wants to remove 456 packages. Every app on my system. I'm a newbie and I don't know if I should let it do that. If I do, do I have to reinstall everything? What's going on here?

---

### Post by erlguta on 2008-10-30
I am desperate of how things are done so bad in ubuntu. Version after version does not seem to learn. Did anyone tried this in canonical before release intrepid?.
There must be thousands of people with this problem.
I had a hardy fresh install.
So what went wrong?

---

### Post by Zyphrexi on 2008-10-30
I'm still getting source weirdness, failing to fetch on update and what not. I'm running apt-get update in term now, to see if it still hiccups.

I can't replicate the problems you guys are having since I was running (and still am) intrepid development version. For those of you still having problems, could you be more specific, I'll try to help you if I can.

ok, apt-get update worked fine now. I'll try upgrading in a bit.

---

### Post by erlguta on 2008-10-30
I think i solved it whit the old style (like debian way):
aptitude update
aptitude safe-upgrade
aptitude full-upgrade

Anyway I'm very upset with of how bad and improvised way that the things are done in ubuntu.

---

### Post by Noxn on 2008-10-30
> **erlguta said:**
> I think i solved it whit the old style (like debian way):
aptitude update
aptitude safe-upgrade
aptitude full-upgrade

Anyway I'm very upset with of how bad and improvised way that the things are done in ubuntu.

That solved the problem? youre now booting right?

(I still got the problem, with not GUI, only cli etc)


And anyway, why are my firefox/lynx/mplayer packages OBSOLETE, and got removed?!!?!?!
This update was a failure :(

---

### Post by erlguta on 2008-10-30
Yes it solved mi problem.
I did it by hand.
I checked that al my /etc/apt/sources.list point to intrepid instead of hardy and i did the upgrade.
In the rebbot dkms build my fglrx driver for my ATI and now i am in Intrepid.

---

### Post by Zyphrexi on 2008-10-30
> **erlguta said:**
> 
Anyway I'm very upset with of how bad and improvised way that the things are done in ubuntu.

well I never encountered any problems. maybe it's just you.

I always just use apt-get anyway. I don't care much for the update-manager. 

EDIT::
> And anyway, why are my firefox/lynx/mplayer packages OBSOLETE, and got removed?!!?!?!
This update was a failure 

check your sources.list

you're supposed to disable 3rd party sources and whatnot. If you've got a lot of custom builds that don't match up with the distribution maintained version it'd probably get removed.

also make sure ubuntu-desktop is installed or it won't update properly. afaik...

---

### Post by Noxn on 2008-10-30
ErlGuta:
You think that 3 commands could help me?

And Zyphrexi:
Well, i did what it said on ubuntu.com!
Like many others.
Ohh... So you think firefox (that came with hardy) and more or less everything Gnome needs "Doesnt match up with the distribution maintained version"?!?
sure...

---

### Post by Zyphrexi on 2008-10-30
I said 'if'. ErlGuta just posted what worked for him. I'm not ubuntu.com, I'm just a user trying to share what I know, in the hopes it might help. Don't get angry with me.

---

### Post by Noxn on 2008-10-30
Sorry, im a bit... angry... you know, having a more or less trashed OS isnt cool.

---

### Post by ultra2033 on 2008-10-30
So I'm upgrading on an Aspire One, and it's already been just shy of 4 hours on the "Cleaning Up".

I notice that this thing is working, and using an internet connection, so i assume that it is verifying packages with the mothership as it goes. Well it's 5pm here and i wants to goes homez. :P

Is there a way to safely cancel this things, and start it up at home or do I have to leave it here.

Thanks,
John

---

### Post by grapegrower on 2008-10-30
I think everyone just needs to take a deep breath and step back for a second. There's no reason to start blaming anyone for an issue that your having with a new OS upgrade/install. There are millions of combinations of hardware and the testers try to get the best product that they can, but there is no way they can guarantee your setup to work.

Anyone that hasn't started a install/upgrade needs to take these easy steps to make sure that they have fewer issues. First of all backup all your data and config files so if you have to do a clean install then your ready to rebuild the system. If you have the money I'd have a backup drive that you can play with to see what the new version will do on your box. I personally mirrored a copy to my backup and did the upgrade to RC1 the other day with no issues whatsoever, but if I had an issue all I had to do was shutdown and replace my old drive and I'd be back to work in 2 minutes. It's worth the 50 or 60 bucks a cheap drive will cost to know you won't be down all week after an upgrade.

I've read that a clean install is best versus an upgrade, like I said I upgraded with no trouble but went ahead and did a clean install just to clean out any issues that I might have had. Good thing I did, my boot time went from taking 40 seconds to 31 seconds. I'm always adding software to try it out and there was obviously something in there that was slowing me down :)

The other thing that I've read about the dedicated video drivers and non-channel software is to uninstall them. So go back down to the vesa video driver before you start your upgrade and remove anything that you loaded by hand so you won't have conflicts.

Just remember the people that are helping you here are doing so out of the kindness of their own hearts and don't really need railed on, and that goes for the fine folks at Canonical that provide us all with this great free software!!


Tim

---

### Post by Zyphrexi on 2008-10-30
for those who think it's possible to bork a system by cancelling an upgrade, I'd like to take the time to say that I've successfully rm'ed /boot, and when I started using ubuntu (with breezy unstable) I replaced my sources list with debian ones and still somehow managed to fix it and get an operable system. That's mainly because I don't give up, and enjoy the challenge though.

noxn: i really don't know how to help you, you say all you got is cli? 
are you familiar with nano? I prefer it over some of the other cli-based text editors. can you give us a bit more information about your system? nvidia/ati etc.

if you have an nvidia card, can you post output for

```
lsmod | grep nv
```

---

### Post by perlluver on 2008-10-30
As the poster above me said, it is better to do a clean install then to Update.  With the new version of XOrg, a lot of the proprietary drivers have been updated.  Please be patient, and let us help you.  There are still a lot of people updating, and the forums are going in and out.  We all work for free here, and have other things to do.  

The best advice is to do a clean install, not update, I updated a minimal install and my system is having some bad side effects, so I am waiting for my free disc to arrive.

---

### Post by ljoslin on 2008-10-30
I have upgraded 2 systems so far using "update-manager -d" with out a single problem....Both systems are AMD 64s with nVidia cards one laptop one desktop, the only issue I had was the downloads only going at ~60k/s...but that is expected with a new release.

-=ljoslin=-

---

### Post by blake82 on 2008-10-30
I'm having a similar problem (after upgrade, system boots into cli)

startx returns "-bash: startx: command not found"

--AND--

my network adaptor has mysteriously stopped working!
I can ping ip addresses all day, and it tells me that the network is unreachable.

I have a feeling that if I can connect to the internet from the cli, then I'll be able to do an apt-get update and an apt-get upgrade... but I need to get this figured out

Any suggestions?

Thanks!

Blake

---

### Post by Noxn on 2008-10-31
Tim and Zyphrexi:
Well, many users just use the upgrade option - Because it says so on ubuntu.com
Im just a bit confused that this "error" happened to many.
I mean, the upgrade removed like everything. That was clearly not supposed to happen, and its not only me.



Gonna try the 3 commands Erlguta said:
aptitude update
aptitude safe-upgrade
aptitude full-upgrade

edit:
I got no internet connection.

Someone has a suggestion that could help me out?
Maybe some repair cd or something...

---

### Post by Noxn on 2008-10-31
> **blake82 said:**
> I'm having a similar problem (after upgrade, system boots into cli)

startx returns "-bash: startx: command not found"

--AND--

my network adaptor has mysteriously stopped working!
I can ping ip addresses all day, and it tells me that the network is unreachable.

I have a feeling that if I can connect to the internet from the cli, then I'll be able to do an apt-get update and an apt-get upgrade... but I need to get this figured out

Any suggestions?

Thanks!

Blake

Try typing the name of some app you have, like firefox, mplayer, or something.
If nothing is found you did the same much users did: when asked to want removed around 400 "obsolete" programs, you clicked okay, like i did. Now i dont have any of my programs, and gnome etc wont work either...

Hope someone can answer us

---

### Post by GooglieS on 2008-10-31
sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

:(

---

### Post by Noxn on 2008-10-31
I hope the devs could fix this, and make the fix downloadable for CD, couse my linux box doesnt have internet after the upgrade...

---

### Post by GooglieS on 2008-10-31
I've just put sources.lst from my IBEX to my HARDY and run sudo apt-get update and sudo apt-get dist-upgrade. But I think, that it is not a true solution for this problem...

---

### Post by leofishman on 2008-10-31
> **Noxn said:**
> Tim and Zyphrexi:
Well, many users just use the upgrade option - Because it says so on ubuntu.com
Im just a bit confused that this "error" happened to many.
I mean, the upgrade removed like everything. That was clearly not supposed to happen, and its not only me.



Gonna try the 3 commands Erlguta said:
aptitude update
aptitude safe-upgrade
aptitude full-upgrade

edit:
I got no internet connection.

Someone has a suggestion that could help me out?
Maybe some repair cd or something...

Try $sudo ifconfig eth0 up
then $sudo dhclient

I did that and now I am in the middle of aptitud safe-upgrade lets hope it works.

---

### Post by spooner on 2008-10-31
> **GooglieS said:**
> sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

:(

I had this problem as well... it turns out that the failed upgrade (one package) had changed my release name "lsb_release -a" to Intrepid.
So I edited "/etc/lsb-release" back to 8.04 hardy and re-ran the upgrade from update-manager...

Seem to be going ok this time (its actually fetching files!)...

---

### Post by Noxn on 2008-10-31
> **leofishman said:**
> Try $sudo ifconfig eth0 up
then $sudo dhclient

I did that and now I am in the middle of aptitud safe-upgrade lets hope it works.


Gonna try, hope it works

edit:
HOLY S*** (sorry)

Thank you a tousand times!

Status:
Internet [X]
Aptitude update [X]
aptitude safe-upgrade [X]
aptitude full-upgrade [X]

---

### Post by leofishman on 2008-10-31
Finish with the full-upgrade

It can't use video drive

---

### Post by Noxn on 2008-10-31
so, i now did the thing for the internet connection, the upgrades, etc, still boots into cli.

what could i have done wrong?
(everytime it asked me i did the standart option)

---

### Post by glis on 2008-10-31
Same Here.

It works until i need to perform a startx... missing nv module :(

---

### Post by leofishman on 2008-10-31
Finally I succeded, used the info in this post:
[http://www.espaciolinux.com/foros-tema-t25558.html](http://www.espaciolinux.com/foros-tema-t25558.html)

$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-$(uname -r)

$ sudo apt-get install xorg-driver-fglrx
$ sudo depmod -a

$ sudo aticonfig --initial
$ sudo aticonfig --overlay-type=Xv
Reiniciamos la PC.

---

### Post by Noxn on 2008-10-31
> **leofishman said:**
> Finally I succeded, used the info in this post:
[http://www.espaciolinux.com/foros-tema-t25558.html](http://www.espaciolinux.com/foros-tema-t25558.html)

$ sudo apt-get update
$ sudo apt-get install linux-restricted-modules-$(uname -r)

$ sudo apt-get install xorg-driver-fglrx
$ sudo depmod -a

$ sudo aticonfig --initial
$ sudo aticonfig --overlay-type=Xv
Reiniciamos la PC.

$ sudo apt-get install linux-restricted-modules-$(uname -r) gave me an error, about it cant be get or something...

How do i know if i got an ati?

edit:
Im not sure this will help me, what if i dont have an ati?

---

### Post by meganox on 2008-10-31
I can't burn CDs under Hardy, have not found a fix. :mad:

Attempted to install Intrepid to a LiveUSB to install off that, usb-creator couldn't create a bootable stick, UNetbootin completely trashed the partition table on my internal HD leaving me without an OS: [http://ubuntuforums.org/showthread.php?t=964903](http://ubuntuforums.org/showthread.php?t=964903)

Clean installed Hardy from CD, applied all updates and attempted to dist-upgrade to Intrepid, since that seems to be the only upgrade path available to me.

Upgrade failed - couldn't fetch some packages - more than 2.

Restarted upgrade, it only wants to install 2 packages.  Hangs, or maybe just takes HOURS, on cleanup.

Going to clean install Hardy again and forget about Intrepid.  It seems to me that a distribution that fails to upgrade on standard hardware from a completely clean and fully updated previous version has some SERIOUS PROBLEMS.

Edit: I'd like to point out that dist-upgrading is not only official supported it is RECOMMENDED.  If I could clean install from a CD or USB I would although the people who say "just clean install, there's less problems" sound like they've had too much experience with Windows.  Having to burn Linux ISOs on Windows in order to install is NOT ACCEPTABLE.

---

### Post by glis on 2008-10-31
I couldn't agree more Meganox. 

It seems so hard to find solutions.

---

### Post by Noxn on 2008-11-01
Ultra agree with meganox.

I thought the dist upgrade (or the update manager) should work RIGHT, until now the only thing it did wrong was, uninstalling ALL my programs, including all my progs, and system stuff...

If theres something different problem, then i dont know it.


PS: i couldnt burn in hardy too

---

### Post by aperomsik on 2008-11-02
Upgraded one machine last night with "update-manager -d". Things went mostly smoothly until I tried to reboot and was faced with just the console login. I logged in and tried "startx" and got an error "no screens found" and there was also some error about the contents of xorg.conf. So I deleted xorg.conf and ran "sudo /etc/init.d/gdm restart" and that got things going, but with the non-restricted video driver. Just to be sure I tried to run the NVidia settings control panel and it said to run nvidia-xconfig, so I did... Things seem to be pretty much back to normal now.

---

### Post by Noxn on 2008-11-02
> **aperomsik said:**
> Upgraded one machine last night with "update-manager -d". Things went mostly smoothly until I tried to reboot and was faced with just the console login. I logged in and tried "startx" and got an error "no screens found" and there was also some error about the contents of xorg.conf. So I deleted xorg.conf and ran "sudo /etc/init.d/gdm restart" and that got things going, but with the non-restricted video driver. Just to be sure I tried to run the NVidia settings control panel and it said to run nvidia-xconfig, so I did... Things seem to be pretty much back to normal now.

Thanks... but i dont know what grafik card i have...
Can you tell me something that may help me anyway?

---

### Post by Therion on 2008-11-02
I did and upgrade (against my own advice) instead of doing a clean install.  There were some minor issues right off th bat and then over time I discovered more even larger issues began rearing their head's. I couldn't do a proper clean install because the partitioning editor kept barfing on creating a swap space partition and kicking me out of the install process (even if I tried to continue without creating a swap partition).   

I caved in and reinstalled Hardy which just runs like a dream on my system.  I'm glad I did...

---

### Post by pcero on 2008-11-02
I am a new Ubuntu user (only a year) and I upgrade with all of these error you find. Only with a clean install I can get a full functional Ubuntu. Completely clean, with new partition of the disk and install (previous backup, of course)

---

### Post by Noxn on 2008-11-02
what should i backup? just the home folder?

---

### Post by pcero on 2008-11-03
> **Noxn said:**
> what should i backup? just the home folder?

I began like everybody, a mesh. Then, I prepared Home in another disk, but I had some problems. At that moment, I have all my data in another disk. When I finish my work (midday and at nigth) I mount this disk and I move all day data there. So, in disk system I have Home only with email (.mozilla-thunderbird) and some directories I want to maintain configuration (.mozilla or .openoffice.org2) to copy to a DVD or USB drive. I do not need nothing more. 20 minutes to install Ubuntu and 15 to update and 30-60 minutes for another programs/utilities and all is done. I only need to copy these directories. All my data are in another disk I have in the front of the computer and I can take it out to save, move...

---

### Post by DustofDust on 2008-11-03
> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

[quote="main.log"]2008-11-03 15:04:14,964 INFO release-upgrader version '0.93.32' started
2008-11-03 15:04:15,638 DEBUG svg pixbuf loader failed (Error displaying image)
2008-11-03 15:04:15,732 DEBUG Using 'DistUpgradeViewGtk' view
2008-11-03 15:04:15,859 DEBUG enable dpkg --force-overwrite
2008-11-03 15:04:16,039 DEBUG lsb-release: 'hardy'
2008-11-03 15:04:16,039 DEBUG _pythonSymlinkCheck run
2008-11-03 15:04:16,052 DEBUG openCache()
2008-11-03 15:04:19,436 DEBUG /openCache()
2008-11-03 15:04:19,436 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2008-11-03 15:04:19,437 DEBUG checkViewDepends()
2008-11-03 15:04:19,437 DEBUG running doUpdate() (showErrors=False)
2008-11-03 15:04:25,630 DEBUG openCache()
2008-11-03 15:04:31,076 DEBUG /openCache()
2008-11-03 15:04:31,077 DEBUG doPostInitialUpdate
2008-11-03 15:04:31,077 DEBUG quirks: running intrepidPostInitialUpdate
2008-11-03 15:04:31,077 DEBUG running intrepidPostInitialUpdate
2008-11-03 15:04:34,797 DEBUG Foreign: 
2008-11-03 15:04:34,798 DEBUG Obsolete: linux-restricted-modules-2.6.24-19-generic linux-headers-2.6.24-21-generic libisc35 libdns35 libx264-64 linux-ubuntu-modules-2.6.24-21-generic linux-headers-2.6.24-19 linux-headers-2.6.24-21 linux-ubuntu-modules-2.6.24-19-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic libdvdread4 linux-headers-2.6.24-19-generic linux-image-2.6.24-19-generic
2008-11-03 15:04:34,799 DEBUG updateSourcesList()
2008-11-03 15:04:34,924 DEBUG rewriteSourcesList()
2008-11-03 15:04:34,935 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy main universe restricted'
2008-11-03 15:04:34,940 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid main universe restricted' updated to new dist
2008-11-03 15:04:34,940 DEBUG examining: 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy universe main multiverse restricted #Added by software-properties'
2008-11-03 15:04:34,944 DEBUG entry 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties' updated to new dist
2008-11-03 15:04:34,944 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-updates main universe restricted'
2008-11-03 15:04:34,949 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-updates main universe restricted' updated to new dist
2008-11-03 15:04:34,950 DEBUG examining: 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-updates universe main multiverse restricted #Added by software-properties'
2008-11-03 15:04:34,953 DEBUG entry 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-updates universe main multiverse restricted #Added by software-properties' updated to new dist
2008-11-03 15:04:34,953 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy multiverse'
2008-11-03 15:04:34,959 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid multiverse' updated to new dist
2008-11-03 15:04:34,959 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-updates multiverse'
2008-11-03 15:04:34,962 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-updates multiverse' updated to new dist
2008-11-03 15:04:34,963 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-backports main multiverse universe restricted'
2008-11-03 15:04:34,968 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-backports main multiverse universe restricted' updated to new dist
2008-11-03 15:04:34,968 DEBUG examining: 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-backports main multiverse universe restricted #Added by software-properties'
2008-11-03 15:04:34,972 DEBUG entry 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-backports main multiverse universe restricted #Added by software-properties' updated to new dist
2008-11-03 15:04:34,972 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner'
2008-11-03 15:04:34,972 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner' updated to new dist
2008-11-03 15:04:34,972 DEBUG examining: 'deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner'
2008-11-03 15:04:34,973 DEBUG entry 'deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner' updated to new dist
2008-11-03 15:04:34,973 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-security main universe restricted'
2008-11-03 15:04:34,978 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-security main universe restricted' updated to new dist
2008-11-03 15:04:34,979 DEBUG examining: 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-security universe main multiverse restricted #Added by software-properties'
2008-11-03 15:04:34,982 DEBUG entry 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-security universe main multiverse restricted #Added by software-properties' updated to new dist
2008-11-03 15:04:34,982 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-security multiverse'
2008-11-03 15:04:34,987 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-security multiverse' updated to new dist
2008-11-03 15:04:34,988 DEBUG examining: 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-proposed main multiverse universe restricted'
2008-11-03 15:04:34,991 DEBUG entry 'deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-proposed main multiverse universe restricted' updated to new dist
2008-11-03 15:04:34,992 DEBUG examining: 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) hardy-proposed main multiverse universe restricted #Added by software-properties'
2008-11-03 15:04:34,995 DEBUG entry 'deb-src [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) intrepid-proposed main multiverse universe restricted #Added by software-properties' updated to new dist
2008-11-03 15:04:35,015 DEBUG running doUpdate() (showErrors=True)
2008-11-03 15:04:57,570 DEBUG openCache()
2008-11-03 15:05:08,833 DEBUG /openCache()
2008-11-03 15:05:12,651 DEBUG Installing 'hpijs' (Distro KeepInstalledPkgs rule)
2008-11-03 15:06:45,688 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2008-11-03 15:06:45,712 DEBUG openCache()
2008-11-03 15:06:46,367 DEBUG /openCache()[/quote]

[quote="apt.log"]Log time: 2008-11-03 12:37:57.641790
Log time: 2008-11-03 12:38:04.587458
Log time: 2008-11-03 12:38:44.628918
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 12:39:01.750451
Log time: 2008-11-03 12:39:16.816589
Log time: 2008-11-03 12:39:40.994930
Log time: 2008-11-03 12:40:12.058645
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 12:40:20.266931
Log time: 2008-11-03 12:41:24.640789
Log time: 2008-11-03 12:41:31.220316
Log time: 2008-11-03 12:42:00.640568
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3

  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 12:42:11.509331
Log time: 2008-11-03 12:56:54.734182
Log time: 2008-11-03 12:57:01.032780
Log time: 2008-11-03 12:57:31.045601
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 12:57:54.625309
Log time: 2008-11-03 13:01:29.421754
Log time: 2008-11-03 13:01:53.993190
Log time: 2008-11-03 13:02:23.557975
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 13:02:30.198863
Log time: 2008-11-03 13:10:14.351545
Log time: 2008-11-03 13:10:20.603077
Log time: 2008-11-03 13:10:50.520102
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 13:10:59.225791
Log time: 2008-11-03 13:24:52.699964
Log time: 2008-11-03 13:25:26.050437
Log time: 2008-11-03 13:26:58.251225
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3

Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 13:33:25.529832
Log time: 2008-11-03 15:02:07.731671
Log time: 2008-11-03 15:02:14.115633
Log time: 2008-11-03 15:02:41.368037
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 15:02:51.001489
Log time: 2008-11-03 15:04:19.418160
Log time: 2008-11-03 15:04:31.068665
Log time: 2008-11-03 15:05:08.815135
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcc-4.3-base as dep of libstdc++6
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing update-manager-core as dep of update-manager
Installing gimp-help-common as dep of gimp-help-en
Installing libsqlite3-0 as dep of tracker
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing citadel-mta as dep of at
Installing citadel-common as dep of citadel-mta
Installing citadel-server as dep of citadel-mta
Installing libcitadel1 as dep of citadel-server
Installing libical0 as dep of citadel-server
Installing libsieve2-1 as dep of citadel-server
Installing db4.6-util as dep of citadel-server
Installing libggzcore9 as dep of libggzmod4
Installing cupsys-client as dep of cupsys-bsd
Installing python2.5-minimal as dep of python2.5
new important dependency: gettext
Installing gettext as dep of friendly-recovery
Installing libssl0.9.8 as dep of openssh-client
Installing libpci3 as dep of vbetool
Installing libc6 as dep of libc6-i686
Installing at-spi as dep of python-pyatspi
Installing cpp-4.3 as dep of cpp
Installing libgmp3c2 as dep of cpp-4.3
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc-4.3 as dep of gcc
Installing libc6-dev as dep of gcc-4.3
Installing linux-libc-dev as dep of libc6-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing libntfs-3g24 as dep of ntfs-3g
Starting
Starting 2
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5270 as a solution to libperl5.8 4
  Removing libperl5.8 rather than change perl-base
Investigating libgnome2-canvas-perl
Package libgnome2-canvas-perl has broken dep on perlapi-5.8.8
  Considering perl-base 5270 as a solution to libgnome2-canvas-perl 2
  Removing libgnome2-canvas-perl rather than change perlapi-5.8.8
Investigating libpurple0
Package libpurple0 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libpurple0 1
  Removing libpurple0 rather than change libperl5.8
Investigating libgnome2-perl
Package libgnome2-perl has broken dep on libgnome2-canvas-perl
  Considering libgnome2-canvas-perl 2 as a solution to libgnome2-perl 1
  Removing libgnome2-perl rather than change libgnome2-canvas-perl
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 1 as a solution to pidgin 1
  Removing pidgin rather than change libpurple0
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on libgnome2-perl
  Considering libgnome2-perl 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libgnome2-perl
Investigating adobe-flashplugin
Package adobe-flashplugin has broken dep on libgtk2.0-0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 1 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 4 as a solution to libsnmp15 4
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 4 as a solution to hplip 2
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 1
  Removing hpijs rather than change hplip
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 1 as a solution to foomatic-db-hpijs 0
  Removing foomatic-db-hpijs rather than change hpijs
 Try to Re-Instate adobe-flashplugin
Done
Installing hplip as dep of hpijs
Installing libsnmp15 as dep of hplip
Starting
Starting 2
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 1 as a solution to libsnmp15 3
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 3
  Removing libperl5.8 rather than change perl-base
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 3
  Removing libsnmp15 rather than change libperl5.8
Investigating hplip
Package hplip has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hplip 1
    Reinst Failed because of libsnmp15
  Removing hplip rather than change libsnmp15
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 5263 as a solution to hpijs 10000
  Added libsnmp15 to the remove list
  Fixing hpijs via keep of libsnmp15
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 5263 as a solution to libsnmp15 10000
  Added libperl5.8 to the remove list
  Fixing libsnmp15 via keep of libperl5.8
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5263 as a solution to libperl5.8 10000
  Added perl-base to the remove list
  Fixing libperl5.8 via keep of perl-base
Investigating libcairo-perl
Package libcairo-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libcairo-perl 1
  Holding Back libcairo-perl rather than change perlapi-5.10.0
Investigating libgnome2-vfs-perl
Package libgnome2-vfs-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgnome2-vfs-perl 0
  Holding Back libgnome2-vfs-perl rather than change perlapi-5.10.0
Investigating libgtk2-perl
Package libgtk2-perl has broken dep on perlapi-5.10.0
  Considering perl-base 10000 as a solution to libgtk2-perl 0
  Holding Back libgtk2-perl rather than change perlapi-5.10.0
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
 Try to Re-Instate perl-base
Re-Instated perl-base (10 vs 5)
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 10000 as a solution to libperl5.8 10000
  Removing libperl5.8 rather than change perl-base
 Try to Re-Instate libcairo-perl
Re-Instated libcairo-perl (5 vs 4)
 Try to Re-Instate libgnome2-vfs-perl
Re-Instated libgnome2-vfs-perl (4 vs 3)
 Try to Re-Instate libgtk2-perl
Re-Instated libgtk2-perl (3 vs 2)
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Investigating libsnmp15
Package libsnmp15 has broken dep on libperl5.8
  Considering libperl5.8 10000 as a solution to libsnmp15 10000
  Removing libsnmp15 rather than change libperl5.8
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 5263 as a solution to hpijs 10000
Package hpijs has broken dep on libsnmp15
  Considering libsnmp15 10000 as a solution to hpijs 10000
Done
Log time: 2008-11-03 15:06:46.361811[/quote]

what can i do?

i have installed amarok, comix, java 6, thunderbird, smplayer, videolan.

i NEED open office 3, the reason why i wanted to upgrade.

---

### Post by Noxn on 2008-11-03
I mean because i need to reinstall, and i wanted to know what i need to keep

---

### Post by DustofDust on 2008-11-03
i do not know but problem is solved.

---

### Post by dwingojr on 2008-11-05
[FONT="Arial"]This worked for me. Open a terminal window and execute the following, in order:

sudo apt-get update
sudo apt-get install ubuntu-desktop

Good luck![FONT="Arial"][/FONT][/FONT]

---

