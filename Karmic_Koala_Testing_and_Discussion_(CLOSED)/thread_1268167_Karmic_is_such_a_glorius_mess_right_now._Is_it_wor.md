---
title: "Karmic is such a glorius mess right now. Is it worth doing a fresh install of it?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-09-16
Topic is pretty self-explanatory.

The past 72 hours have been a living hell for testers and devs.

Is it worth reinstalling using Alpha 5 or the latest dailies?

---

### Post by Westmeath on 2009-09-16
Alpha 6 is due out tomorrow.

---

### Post by ELD on 2009-09-16
> **Westmeath said:**
> Alpha 6 is due out tomorrow.

Doesn't mean much will be cleaned up though, after all it is just another day, unless some people have been holding back packages.

---

### Post by joey-elijah on 2009-09-16
I love the title! I'm SO glad karmic was my first Alpha testing! 

I remember testers complaining of the quiet ride that Jaunty and Ibex were :P

---

### Post by 23meg on 2009-09-16
> **ELD said:**
> Doesn't mean much will be cleaned up though, after all it is just another day, unless some people have been holding back packages.

It *does* mean much will be cleaned up, relatively. Milestone releases are reasonably free of showstopper bugs.

---

### Post by MacUntu on 2009-09-16
> **joey-elijah said:**
> I love the title! I'm SO glad karmic was my first Alpha testing! 

I remember testers complaining of the quiet ride that Jaunty and Ibex were :P

Naaah, this little merge thingy doesn't count. So far I've found more alpha in Win 7 RTM than in Karmic. :P

---

### Post by andrek on 2009-09-16
I did a reinstall from alpha4 livecd yesterday ( alpha5 livecd is unable to get through gdm here ), updated the system and it works perfectly. The only thing is that I don't see usplash at all ( some text on startup, and then quickly goes into xsplash so the full boot process is pretty quick ) but I don't think that's a bug :)

---

### Post by VMC on 2009-09-16
I thought of doing just that, until I applied all the updates from end of yesterday and today. Now I'm back to "normal". I went through various stages of recovery. The worse not being able to even get to recovery mode, to needing fsck on every boot, to now it appears all is well.

---

### Post by infamousrev on 2009-09-16
I installed the daily build install today.

After install I had a command prompt.

After I did aptitude full-upgrade, everything worked fine.

---

### Post by ELD on 2009-09-16
> **23meg said:**
> It *does* mean much will be cleaned up, relatively. Milestone releases are reasonably free of showstopper bugs.

Even though the ATi bug has been pushed to the beta release milestone, sorry but that is just so annoying, such a big bug as well. As i keep seeing posts made about it, and i keep complaining about it ;)

It would be better to slap in a quick workaround by default for bug -> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126) rather than leave it so many people cannot boot and test without messing around with workarounds themselves.

---

### Post by Eclipse. on 2009-09-16
I can see alpha 6 being delayed a day or so just untill all the boot issues are sorted, I just done a fresh install alpha 5 onto my desktop and upgraded and ended up in a mess.

---

### Post by VMC on 2009-09-16
> **Eclipse. said:**
> I can see alpha 6 being delayed a day or so just untill all the boot issues are sorted, I just done a fresh install alpha 5 onto my desktop and upgraded and ended up in a mess.

Here is the weird part. I guess we're all still in a mess. It wasn't until a recent grub2 did it come to light. The boot up process was hidden, until update removed splash and I could see all the errors wizz by.

Funny thing is, late last night I had splash removed and no errors. But I would be surprised if alpha6 gets delayed.

---

### Post by ELD on 2009-09-16
I am just keeping a good eye on the bug report for ATi users, i sincerely hope it gets fixed soon, i want to play heh.

---

### Post by Moop on 2009-09-16
I had to chroot in using a live cd yesterday to finish the updates. After that everything has been working great. I'm using 64bit Ubuntu.

I'm not dual booting and don't have any proprietary drivers installed.

---

### Post by Starks on 2009-09-16
> **VMC said:**
> Here is the weird part. I guess we're all still in a  mess. It wasn't until a recent grub2 did it come to light. The boot up  process was hidden, until update removed splash and I could see all the  errors wizz by.

Funny thing is, late last night I had splash removed and no errors. But I  would be surprised if alpha6 gets delayed.
Alt+F1 or Alt+F2 during boot up will show you that.

---

### Post by TheForkOfJustice on 2009-09-16
Is it possible to take my current Karmic partition and make it available in a chroot from my Jaunty partition so I can stop rebooting to this delightful mess?

---

### Post by SigmaSanti on 2009-09-16
I hope alpha 6 works, because I had problems with alpha 5 the gdm. If 6 gets delayed... I think I will try alpha 4 and update like an earlier person said.

---

### Post by Starks on 2009-09-16
And I just realized I misspelled glorious.

Lack of sleep is finally catching up with me.

---

### Post by VMC on 2009-09-16
> **Starks said:**
> Alt+F1 or Alt+F2 during boot up will show you that.

It should, but doesn't work for me. It just goes dark and stays dark until that god-awful xsplash kicks in.

---

### Post by Moop on 2009-09-16
> **TheForkOfJustice said:**
> Is it possible to take my current Karmic partition and make it available in a chroot from my Jaunty partition so I can stop rebooting to this delightful mess?

[http://ubuntuforums.org/showthread.php?p=7952958#post7952958](http://ubuntuforums.org/showthread.php?p=7952958#post7952958)

---

### Post by autocrosser on 2009-09-16
What mess???? I've been watching the updates as they happen & while I waited 24 hours for the libc6 bit to smooth out--I've had a fairly easy ride of things--nothing worth noting unlike times past that everyone's systems were b0rked by xorg updates--what have I missed? :confused:

---

### Post by DougieFresh4U on 2009-09-16
> **autocrosser said:**
> nothing worth noting unlike times past that everyone's systems were b0rked by xorg updates--what have I missed? :confused:

Amen to that!!Those wonderful days of xorg trashing test boxes almost daily :mad::mad:

---

### Post by Slug71 on 2009-09-17
Needs to do a fresh install of Alpha 6 tomorrow. System just hangs at boot after updates yesterday. :guitar:

---

### Post by VMC on 2009-09-17
> **Slug71 said:**
> Needs to do a fresh install of Alpha 6 tomorrow. System just hangs at boot after updates yesterday. :guitar:

I think most of us went through that. Have you tried any of the remedies given? You can try chroot'ing from another distro, and then update the system that way. It won't hurt. Afterall you have to take the time and download the new cd and then install it. If updating your current alpha install it just may work. Its worth a shoot.

Just try this [**method**]("http://ubuntuforums.org/showpost.php?p=7960338&postcount=3") I described and see if works.

---

### Post by Arla on 2009-09-17
As someone somewhat new to Ubuntu, I went back to Alpha 5 and haven't dared touch update since :)

I know, I know, this is what testing is all about, but I haven't the first idea how to fix the issues yet, so am going to stick to Alpha5 until I know these problems are resolved.

---

### Post by dino99 on 2009-09-17
hey guys,

karmic is back 

last packages upgraded wiped all my troubles:
- grub menu is ok
- karmic boot
- x start
- logs are clean

happy end

Thanks dev

---

### Post by gmc on 2009-09-17
So by the sounds of it... it's still not safe to return to pool yet.

I'm going to wait for the A6 fresh install reviews before I attempt Krazy Karmic again. In the mean time, my AA0 with Jaunty needs some love (130Gb of updates) as I've not looked at it for about a month now.

G

---

### Post by Johnsie on 2009-09-17
I had the mess going on... it took me a while to fix it but I've got Gnome running again (manually with startx). I'm hoping that a dist-upgrade in the next few days will fix everything.

---

### Post by kansasnoob on 2009-09-17
Well, I did try reinstalling with the 9/16 daily build and manual partitioning still failed.

Of course the day before (during the big crash) the same was true and the image was also oversize.

Things seem to be in a state of flux right now!

---

### Post by kansasnoob on 2009-09-17
> **gmc said:**
> So by the sounds of it... it's still not safe to return to pool yet.

I'm going to wait for the A6 fresh install reviews before I attempt Krazy Karmic again. In the mean time, my AA0 with Jaunty needs some love (130Gb of updates) as I've not looked at it for about a month now.

G

Eeeerrrr, uuuuhhhhh, Krappy Koala at this point :P

They'll get it straightened out!

---

### Post by arvvvs on 2009-09-17
I have a OS thats screwed up thanks to updates, and tehn over screwed up by my attempts to fix it, and then one that can't mount USB HD's, or even seperate partitions for crap.

---

### Post by arvvvs on 2009-09-17
I have a OS thats screwed up thanks to updates, and tehn over screwed up by my attempts to fix it, and then one that can't mount USB HD's, or even seperate partitions for crap.  
so yes

---

### Post by ubongo2008 on 2009-09-17
> **TheForkOfJustice said:**
> Is it possible to take my current Karmic partition and make it available in a chroot from my Jaunty partition so I can stop rebooting to this delightful mess?

if you want a full X-session without any major drawbacks ... no

@Topic ... actualy half of my system is Karmic the other half is Jaunty amd64 i needed to do that because of random crashes of some apps now everything is stable and i backed up my box and then did an update but well there have been way to much errors so i am back to my "Karunty"

---

### Post by bela42 on 2009-09-17
I#d rather say no. Spent some time last night to get it back up via alpha 5 and dist-upgrade, but then it is still worse than alpha 5.

Frequently crashing: Evolution, Tracker indexer, Nspluginviewer, Compiz, Totem.

Network manager won't allow editing my connection anymore...

Gnome Bluetooth still dysfunctional...

etc.

I wonder how they want to get this sorted out in six weeks...

---

### Post by Sophont on 2009-09-17
To answer the title question: There is no need for a fresh install (unless your system got in serious trouble during the last couple of days).

I waited out the whole problem and did my usual
sudo aptitude safe-upgrade
yesterday and everything works fine (or occasionally no worse than before :-) ).

Boot *feels* a bit faster - but could be illusion - I didn't benchmark and it's no dramatic change.

---

### Post by buonaparte on 2009-09-17
Anybody knows when A6 is out?

---

### Post by waspbr on 2009-09-17
writing  from  karmic here, I did a fresh install last night, I have to say it was very much necessary, I have a separate /home/ partition so I didn't lose anything essential but it is still a chore. I also have a jaunty / partition just in case. Since karmic wouldn't boot, I went on to jaunty and checked karmic'c partition out. For starters there was not /etc folder, actually, a whole bunch of folders was missing.

so yeah, a fresh install was very much in order.

---

### Post by keplerspeed on 2009-09-17
Well, not yet: [http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

Supposed to be out today, must be some holdups.

---

### Post by Ric_NYC on 2009-09-17
Updating the system now...
Let's see what happens...

---

### Post by autocrosser on 2009-09-17
All of you still need to remember that Karmic IS still alpha & b0rked systems, breakage & eating kittens WILL HAPPEN---If you are not willing to work thru b0rkage--wait til the RC comes out.

I follow the developers list & look at all the updates BEFORE I install them--held back libc6 for 2 days because I saw that it was going to be a problem & avoided all this mess. Sorry that your systems were b0rked, but if you are new to testing you should use more caution & not just install because the developers sent it down the pipeline......

---

### Post by grandtoubab on 2009-09-17
That is the beauty of testing to have problems.:confused:
Most of the time the community give workaround:popcorn:
If you want to  be in a quiet world keep using the LTS version:lolflag:

---

### Post by Slug71 on 2009-09-17
> **VMC said:**
> I think most of us went through that. Have you tried any of the remedies given? You can try chroot'ing from another distro, and then update the system that way. It won't hurt. Afterall you have to take the time and download the new cd and then install it. If updating your current alpha install it just may work. Its worth a shoot.

Just try this [**method**]("http://ubuntuforums.org/showpost.php?p=7960338&postcount=3") I described and see if works.

Two problems with this. 
1. I only have Vista and Karmic installed on our laptop. Yes its on my production machine.

2. Im not connected to the internet at boot because i have to enter a damn Network Manager keyring password at every login for wireless.

---

### Post by anubhavrocks on 2009-09-17
> **Slug71 said:**
> Two problems with this. 
1. I only have Vista and Karmic installed on our laptop. Yes its on my production machine.

2. Im not connected to the internet at boot because i have to enter a damn Network Manager keyring password at every login for wireless.

You can use the iwconfig command to associate with the AP.

---

### Post by omarly on 2009-09-17
> **andrek said:**
> I did a reinstall from alpha4 livecd yesterday ( alpha5 livecd is unable to get through gdm here ), updated the system and it works perfectly. The only thing is that I don't see usplash at all ( some text on startup, and then quickly goes into xsplash so the full boot process is pretty quick ) but I don't think that's a bug :)
After doing an update, the whole box was unusable. Did a reinstall of alfa4, and had NO desire of updating. Works quite good. :) 
For me and my dell XPS m1530 I appriciate the louder sound, better response and the new setup for my 3g-modem which works without doing extra mod on the username and password - nice job! :) 

After the team have fixed the MAJOR bugs lately appeared, I am sure this is gonna be a really SUCCESS release.

All the best 2 u all
Peace love and enlightenment

---

### Post by L_V on 2009-09-17
Alpha 6 should be postponed for at least 1 or 2 weeks to get something usable and tested a bare minimum by the development.

---

### Post by artir on 2009-09-17
> **L_V said:**
> Alpha 6 should be postponed for at least 1 or 2 weeks to get something usable and tested a bare minimum by the development.

It's an alpha: release what you have. You do all the testing and all that with the final version

---

### Post by solitaire on 2009-09-17
> **L_V said:**
> Alpha 6 should be postponed for at least 1 or 2 weeks to get something usable and tested a bare minimum by the development.

Don't think they would take THAT drastic a reaction!

a day or so, yup i can see that! 

But remember this IS still alpha so it's bound to have a borked package here and there, and were TESTING it and finding loads of bugs (which is a good thing!)

The sooner they release Alpha-6 the sooner the rest of the bugs can be spotted and fixed.

If you don't wish to help in fixing bugs then wait till the beta (in a couple of weeks).

but this is just my opinion...

I love borking systems ^_~
and can't wait for A-6 later today (fingers & toes crossed)

Peace!

---

### Post by Sophont on 2009-09-17
> **L_V said:**
> Alpha 6 should be postponed for at least 1 or 2 weeks to get something usable and tested a bare minimum by the development.

Mate - this *is* the testing. :-)

The partial upgrade mess of couple days ago is already over - I upgraded yesterday and there was no problem. Boot is a bit faster. Couple warnings during boot visible now - but just mentions that I should cleanup some udev rules (will wait that out for a while).

Just got some Evolution crash message after login - shrug - don't use that myself ([https://bugs.launchpad.net/bugs/432023](https://bugs.launchpad.net/bugs/432023)).

I haven't noticed any new problems so far. Karma is not 100% on this machine - but nothing major, nor anything that keeps me from using it fully (except I'm waiting to get radeonHD or fglrx 3D support for games/Compiz).

Alpha 6 is not a release - not even a release candidate - just a snapshot that's reasonably expected to boot. There's no good reason I can see why they should postpone it. Alpha means that this is the phase where bugs get hunted and killed. And to do that it needs to be spread around so the devs can get feedback from a variety of setups and machines. If you hold back Alpha snapshots because they ain't perfect yet then you actually slow down the bug fixing.

If the risk of breakage is not something you you are not prepared for then - as many have said above already - the alpha phase is not for you. Meanwhile - thanks for testing.

Tips:
Install VirtualBox OSE (it's in the repo). Install a VM with Karma. Always update that first. Check what the bleediest of bleeding edgers wrote on the forum. Avoid Partial Upgrades.
Use
> sudo aptitude safe-upgrade
on the command line instead of UpgradeManager.

With those rules I use Karmic relatively peacefully on my main machine directly on the metal with hardly any issues (I had a VM since Alpha 2 and installed on my main Laptop Alpha 4). But I also have backups, an 
ethernet cable available and know how I can recover when things bork up too much.

This is at least the 3rd time I upgraded during alpha and I never had to reinstall. The only reinstall I ever did (since Feisty) was after Hardy release because I wanted to use the full disk after I wiped the long unused XP partition on my old laptop.

---

### Post by bacardiandwatermelon on 2009-09-17
I just downloaded a daily build and it installed fine. Glad this episode is over hehe :-P

---

