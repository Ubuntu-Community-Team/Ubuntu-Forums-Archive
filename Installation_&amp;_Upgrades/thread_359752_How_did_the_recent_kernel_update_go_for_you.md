---
title: "How did the recent kernel update go for you?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by lojic on 2007-02-12
I was curious if we could get a basic summary of how the recent kernel update went, so I thought I'd post a poll. I realize this poll is susceptible to self-selection bias (i.e. possibly those experiencing problems are more likely to respond), but it may help give a picture of the current situation.

My intent is that this might help provide some feedback for future updates.

This is **not** the best thread to discuss the actual issues - there are many other threads for that, and many of them have solutions posted already.

**UPDATE:** considering that many of us have multiple installations, and you can only vote once, I think it makes sense to choose the worst one to vote on. No, I'm not being negative, but if you have 2 machines, and one went fine and the other is still having problems with no solution, then **you**, as a user, are still having problems with no solution.

---

### Post by JamieC on 2007-02-12
I always hold back with kernel updates and await posts regarding issues. I think it's sensible to wait a while to see possible issues which may arise and how such issues can be resolved.

I saw several posts regarding a loss of wireless functionality with the new kernel as well as sound issues, however, knowing that I had a previous kernel to fall back on I decided to bite the bullet and upgrade.

I did so and restarted. I was greeted with a built in shell and tty errors. I always keep forgetting to change the default root value to prevent kernel updates from updating the grub menu.lst file with incorrect parameters. Once I fixed the line, I received the 'dreaded' X server errors.

One thing I always forget to do is to reinstall the nVidia proprietary drivers. So, I simply re-installed the restricted modules for the new kernel version and viola, all is well.

Furthermore I do not have any issues at all (as of yet). If I had remembered to reinstall the video card driver and got round to fixing the boot parameters, I would not have had any issues with the kernel update.

Wow, that was unnecessarily lengthy, but hey! Hope it helps.

---

### Post by mikewhatever on 2007-02-12
Good idea lojic. Cheers!
After the upgrade, xserver fails to start for 2.6.17-11-generic. Luckily, the older version still worked. Reinstalling nvidia drivers with envy, while booted into 2.6.17-11, and reconfiguring xorg, brought GUI up, but there was no wireless, and no direct rendering, also, the max resolution was low. Doing the above, broke the older kernel, so that I decided to undo the changes, revert back to the older kernel, and comment the newer one out of grub menu. Currently, I am uncertain whether to try to mess around some more, or completely remove 2.6.17-11, and lock the working kernel to prevent any further upgrades.

Update: After installing the linux restricted modules for the newer kernel, and reinstalling nvidia driver with envy, xserver starts under the new kernel, but fails under the old one. If I fix the old one by reinstalling the driver again, x does not work under the new one again. I don't think this is right.

---

### Post by Sunflower1970 on 2007-02-12
I have three different installations.

One was a painful installation, but after some work, I got the system running fine.
Second one...well, in the end it was easier to just start from scratch and install all the updates before I did anything else. Then that upgrade went smoothly (only took a long time to do)
Third one went smoother than I could have imagined. Zero troubles...of course I waited a few days befoe I did anything to see if others were still having problems. :)

---

### Post by confused57 on 2007-02-12
I have several installations, but had no problems whatsover with any of them:

1.) Breezy to Dapper upgrade, pc w/ FX5500 GeForce, using "nv" driver...the original Breezy was installed over a year ago.

2.)2 Dapper installs(one on Dell 4550 with Nvidia legacy, other on pc with integrated Sis video)

3.)Simply Mepis 6.0

4.)Ubuntu Lite with base Dapper 6.06.1

5.)Edgy install, no problems.

---

### Post by Catsworth on 2007-02-12
Not sure, it's possible that it's [screwed a whole load of things up](http://www.ubuntuforums.org/showthread.php?t=359815), but I don't know enough about Ubuntu to know whether or not to attribute this lot to the kernel update.....

---

### Post by PrinceArithon on 2007-02-12
I'm using Edgy and all went really well.

---

### Post by highneko on 2007-02-12
Voted: I had problems, but I found a satisfactory solution.

When trying to use the new kernel gdm wouldn't start which I expected to happen because of nvidia. So went into a non-graphical terminal thing and updated. Rebooted and it was working fine. I personally like problem solving things like this, but new users would be turned off with such things.

---

### Post by spd106 on 2007-02-12
After going through the last big upgrade from Dapper to Edgy I have become very cautious about upgrades/updates that involve major system packages. 

Since I rely on a third party repo for the nvida 9xxx series driver I knew that it was important to make sure the driver had been recompiled for the new kernel ABI bump. This knowledge really only comes with experience, I certainly wouldn't have coped if I hadn't understood what was going on.

As others have said previously, it pays to hold off updates for a few days and monitor the situation.

---

### Post by bluenova on 2007-02-12
I had to dist-upgrade from the non-graphical terminal, and then reload some modules. No problem for me to sort out, but once again the reason I don't recommend Ubuntu or Linux in general to anyone who 'just uses' a computer for everyday use. It's these mishaps that stop Ubuntu from competing with MS Windows and Mac OS.

---

### Post by BLTicklemonster on 2007-02-12
I have two installations, one was Dapper, and I upgraded it to Edgy a couple of weeks ago, and it has never worked since. I gave up and will probably just reinstall edgy on that, and attempt to go to Feisty on it, and try getting all my settings where I want on it.

Then comes this update. I updated Saturday night but never rebooted or anything because there was no notification that the system need a reboot, so I was thinking this was a "soft" kind of upgrade. Well, yesterday our gaming clan had a match, and just before we were to meet prior to the match, I decided to reboot. Bad idea. So there I was, unable to boot to ubuntu, so I quickly brought up my windows partition, and attempted to play in windows. Let me tell you, once you get Unreal Tournament set up right in linux, there's nothing you can do to it in windows to get it to match. So I totally stunk in our first map. I bailed right quick, and told the clan to hang on and put someone else in in my place, and tried uninstalling and reinstalling nvidia-glx (the problem is, it says x is configured wrong, I go through all the no, I don't care's and then end up at a blinking white cursor where I would expect to be at the command line where I could dpkg-reconfigure xserver-xorg, but I never get there) from ... what's that second option? recovery, I guess. Well, I did that, and it still would not start, so I got all smart alecky and just chose to boot from the previous kernel in grub, and it worked. 

Sucks I had to do that, and I have no idea how to get this version working.

---

### Post by Stef@n on 2007-02-12
I voted for: "I had problems, but found a satisfactory solution" although I don't know exactly what that solution was. 

I couldn't get into gdm because the new kernel-update screwed my nvidia-drivers. So I used the envy-script to install the driver again. From this point on I was able to boot into gdm again. But beryl refused to work. The reason was, I think, because 3d-acceleration was turned off (wasn't able to turn it on again). Tried reinstalling the driver, but this had no effect.

After a couple of reboots gdm didn't work again. So I installed the nvidia driver via envy again, which (surprisingly!) turned 3d-acceleration on again. Tried beryl again (worked!) and everythings back to normal. No idea what happened!

---

### Post by paulmerchant on 2007-02-12
It would be good if kernel updates came flagged quite a bit differently than just normal, everyday updates. It's too easy for all of us to just accept the latest updates without realizing that it might be something major, like the kernel, and may require rebuilding drivers.

I find kernel updates to almost always catch me off guard and they seem to cause a ton of problems for others who weren't expecting them.

---

### Post by lojic on 2007-02-12
> **paulmerchant said:**
> It would be good if kernel updates came flagged quite a bit differently than just normal, everyday updates. It's too easy for all of us to just accept the latest updates without realizing that it might be something major, like the kernel, and may require rebuilding drivers.

I find kernel updates to almost always catch me off guard and they seem to cause a ton of problems for others who weren't expecting them.
I agree. I've posted a couple threads related to this:

Better package descriptions:
[http://www.ubuntuforums.org/showthread.php?t=358485](http://www.ubuntuforums.org/showthread.php?t=358485)

Timestamps of packages to allow us to know when to take the plunge :)
[http://www.ubuntuforums.org/showthread.php?t=358023](http://www.ubuntuforums.org/showthread.php?t=358023)

---

### Post by Dylnuge on 2007-02-12
No problems here, happy to report.

---

### Post by karachuonyo on 2007-02-12
Well the upgrade broke my desktop but i managed to get the nvidia drivers working again and the system is somehow working. However when playing games the resolution keeps varying out of sync and the games just suck. I'm working on it currently to get a fix. Could do with some help here. I'm hesitant to upgrade my laptop despite it not having standalone graphics card.

---

### Post by charon79m on 2007-02-12
Normal issues with ATI drivers needing rebuilt.  Did that without issue and installed.  3d works great.

Experiencing random failures of fglrx causing me to drop out of gnome and back to the login screen.  The event logs are of little help, and booting to the previous kernel works fine.

Will continue to research.

---

### Post by markwren on 2007-02-12
The kernel update has not "gone" for me ...

Ubuntu has something to prove with kernel and version updates after a couple of high profile problems in the last year or two.

So I always watch the forums for problems before commiting to a kernel update. The last few kernel updates have been fine. But this is the first big update for a long time, and even now there are STILL issues outstanding on the forums.

It gives the impression that, as kernel updates come from a separate team (Soyuz ... who?), there's a problem with the process of risk/benefit (whether to accept/reject an update on principle) and ACCEPTANCE testing by Ubuntu decision makers themselves? ... including testing of the actual update process in typical setups (e.g. 3d graphics and wifi networking)? ... followed by preparation of RELEASE NOTES issued PRIOR to the release?

So that's a vote for "ignoring it". Please count it! (In the UK "spoiled" voting papers are not counted in elections any more.)

---

### Post by C-A on 2007-02-12
My upgrade went ok because I had read the forums first before upgrading. I would just like to voice that I think most people end up installing third party drivers including people new to linux. If the intent if this distribution is to keep it as new user friendly as possible, something needs to happen to keep so many people from upgrading, rebooting, and then having a blank screen.

An idea is an auto script to run before a kernal upgrade to search for drivers that will no longer work and a chance to roll back to the "official" drivers.

---

### Post by lonniehenry on 2007-02-12
Using edgy 64. Update broke xorg, wifi and vmware,  I fixed xorg which broke old kernel, recompiled ndiswrapper for broadcom wifi, and used sudo /usr/bin/vmware-config.pl for vmware.  Was not to bad to do except I had forgotten what a pain it is to do the wifi. I would like a way of doing it in an easier way.

---

### Post by Argus on 2007-02-12
Lost X after the reboot, but just reran ENVY at the command prompt. Envy did have a error but everything worked out good.

---

### Post by maxamillion on 2007-02-12
i haven't upgraded ... i'm waiting it out, i read about too many issues on the forums to make me want to bother.

---

### Post by Schluppy on 2007-02-12
I just finished the update via synaptic a few minutes ago, rebooted and have no apparent problems.

Like many others have suggested, I find it wise to monitor the forums for a few days when kernel or otherwise major updates come down the wire before committing.

---

### Post by cainlevy on 2007-02-12
Lost my wifi and my ATI drivers after the "upgrade". I think it's completely ridiculous to have to monitor forums before upgrading a such a minor version bump. Especially when Ubuntu is trying to make upgrades easy and automatic.

Having to monitor forums before an upgrade is the Gentoo way. I left Gentoo cuz I got sick of maintaining my laptop. I really expected better from Ubuntu.

---

### Post by shane2peru on 2007-02-12
The update overwrote my menu.lst incorrectly, which is really annoying because I only have **one OS** on my computer.  It tried booting off of hda4 or something???  :confused:  What is that all about?  I was quite shocked when I couldn't get into my computer.  I was more annoyed to find that it had done the same to others.  I had to re-install my grub to get it correct.  What a mess, took me about an hour or so to fix.

Shane

Oh, nice poll by the way, I have been wondering just how many had problems with this update.  I'd say, not a good update for the majority.

---

### Post by Kateikyoushi on 2007-02-12
> **JamieC said:**
> I always hold back with kernel updates and await posts regarding issues. I think it's sensible to wait a while to see possible issues which may arise and how such issues can be resolved.

I do the same especially because I am lazy to patch it every time they come out with a new kernel to be able to undervolt the CPU. Which is more important for me than whatever they could possibly add to the kernel so I stick with the first edgy kernel till feisty.

Not mentioning even before could start the update got the broken packages message which was a good indicator of the coming major breakage.

---

### Post by viper on 2007-02-13
Broke my wireless............

---

### Post by housam on 2007-02-13
I've up-dated my Edgy kernel and every thing is fine. I'm using an hp compaq nx7400. I think that as long as you use a powerfull machines , the install,the up-date and the upgrade works just fine.

---

### Post by g8m on 2007-02-13
I noticed the unchecked boxes when first checking the updates. So I waited a day, and the upgrade went flawlessly on my laptop. After that I upgraded the desktop. The desktop has vmware and the nvidia drivers installed. After rebooting I choose recovery, reinstalled the nvidia drivers and ran the vmware-config script again. Exited and everything worked, I think....

---

### Post by Kateikyoushi on 2007-02-13
Why would it work better on powerful machines than on the low end ?

---

### Post by Rob on 2007-02-13
Did an update last night without thinking about it. Rebooted the computer and X didn't work. Thought it might be because I'd just moved the computer from one location to another, but now realise it is likely to be an Nvidia driver problem after the kernel update.

Hopefully I'll find the time to fix it soon, and wish I'd thought about it more and found a better time to break my computer...

I'd been thinking recently I don't really need the Nvidia driver for this computer, so I might take this opportunity to go back to the opensource one (nv, I think?)

---

### Post by lojic on 2007-02-13
> it is likely to be an Nvidia driver problem after the kernel update

In my case, installing linux-restricted-modules-2.6.17-11-generic did the trick. Others have run the envy script.

---

### Post by phansiizwe on 2007-02-13
I had to reinstall the Nvidia drivers (running the Nvidia installer worked for me) and recompile ndiswrapper to get my wireless going again. Now everything's fine again.

I made some scripts for myself in the progress, for when it happens again. Nice scripting exercise...

---

### Post by liamjamesbooth on 2007-02-13
upgrade on my laptop in edgy went absolutely fine!
only problem is on the dapper upgrade on my desktop, music (_only music_, not video or on firefox)   plays slower/slower bitrate for some reason,? works fine if i boot back into 2.6.15-27 ? ah well:guitar:

---

### Post by Man_Beach on 2007-02-13
> **maxamillion said:**
> i haven't upgraded ... i'm waiting it out, i read about too many issues on the forums to make me want to bother.

I'm with you there - I'm not updating _anything_ if I can't be positive that Ubuntu will still work when I've done it. My wife has got a job that depends on a working computer.

---

### Post by housam on 2007-02-14
> **Kateikyoushi said:**
> Why would it work better on powerful machines than on the low end ?

I realy don't know but I've noticed from the forum that the powerful machines has less troubles in general. just a remark.

---

### Post by victor_c26 on 2007-02-14
So X didn't start, so I'm guessing it broke my 9746 nvidia drivers. 

I'm back using the nv drivers as the 87 series drivers don't support the 6100 int. chip on this machine. :(

---

### Post by silverpig on 2007-02-14
My main workstation was fine, but my mythbox was hosed for a few hours. I've got it working again after a video driver reinstall, but not as well as before. It's locked up playing a few videos a few times, and reboots leave the sound not working for anything using the internal myth video player until I manually kill esd. Also, my remote stopped working, and I had to reinstall the drivers for that.

---

### Post by justin whitaker on 2007-02-14
So, has anyone upgraded everything but the kernel and see what breaks?

---

### Post by PrinceArithon on 2007-02-14
I originally posted that I found no problems, but I did after all.  It broke Beryl...I haven't tried to uninstall reinstall beryl, but so far it broke beryl.

---

### Post by phansiizwe on 2007-02-14
> **victor_c26 said:**
> So X didn't start, so I'm guessing it broke my 9746 nvidia drivers. 

I'm back using the nv drivers as the 87 series drivers don't support the 6100 int. chip on this machine. :(

Have you installed them using the Nvidia installer (the .run file from the Nvidia website)?
I just ran the installer again and everything was fixed!

---

### Post by persona_o on 2007-02-14
still haven't resolved my problems - I have to reinstall the nvidia drivers I think, but I don't know how to do that from the command line and don't want to mess anything up (I have it all set up the way I like, and I've been reading [horror stories]("http://www.ubuntuforums.org/showthread.php?t=360212") about people having trouble with their drivers). 

Ah well, the previous kernel version seems to work fine, with the existing nvidia drivers and beryl, no problems since the other updates too (there was a GNOME update I believe a couple of days ago). I guess I'll just wait for the next major release and reinstall when it comes out.

---

### Post by yabbadabbadont on 2007-02-14
I had problems with the update but, since I always boot to the console, it wasn't a big deal.  My satisfactory solution was to wipe ubuntu and give FreeBSD a try.  ;)  After a couple of days I reinstalled ubuntu and didn't have any trouble.  (and no, I wasn't using any kernel modules from outside of dapper/main :p)

---

### Post by camini on 2007-02-14
Have the same problem on my Edgy install with nVidia (for Beryl) drivers.

highneko, how difficult is it to get the latest nVidia drivers from terminal?
Can you post the procedure?

---

### Post by ajm2005 on 2007-02-14
my kernel doesn't appear to have been updated. it's still -10. should I manually install -11? what is the "point" of this kernel upgrade, anyway? are their important new features to be gained?

---

### Post by samwyse on 2007-02-14
Worked for me. I use the accelerated Nvidia-drivers from the repos. People with problems are using from other sources (nvidia-installer)? :confused:

---

### Post by lojic on 2007-02-14
> **ajm2005 said:**
> my kernel doesn't appear to have been updated. it's still -10. should I manually install -11? what is the "point" of this kernel upgrade, anyway? are their important new features to be gained?
I'd like to know the reason for the -11 upgrade as well. I started the following thread:

[http://www.ubuntuforums.org/showthread.php?t=358443](http://www.ubuntuforums.org/showthread.php?t=358443)

But I don't think anyone that knows ever bothered to respond. IIRC when I did kernel upgrades on SUSE, the descriptions always had a list of fixes, etc. that were included so I could determine if any of them were important enough for me to upgrade.

---

### Post by jbonll05 on 2007-02-14
Two totally different home built machines came through without a hitch! Both started with Breezy in 2005. Did a complete new install of Edgy in Nov.2006, on both machines, have followed regular updates since. Both machines are used daily.
JB; Ubuntu since Oct05

---

### Post by buuntuu! on 2007-02-15
updated and the sound was gone.
somehow the pcm channel got disactivated.
rightclick on the speaker-icon and Cntrl+O did the trick:)

---

### Post by Patrick K on 2007-02-15
I had problems. First off the upgrade renamed my Ubuntu partitions so GRUB was wacked. Second, nvidia drivers were foobared. Third, fstab was rewritten with incorrect mount points for several partitions (two partitions were mounted on the same mount point). Fourth, swap was incorrectly mounted and inactive. Got it all sorted out eventually thanks to the live cd, GParted, SuperGrub, and the Envy script.

---

### Post by NarsilAnduril on 2007-02-15
... -11 broke my WiFi (D-Link DWL-G650 on a Compaq Evo N160 - Edgy)

Found a solution : downgrade to -10 ! (default = 2 in /boot/grub/menu.lst)

Bis mess ... for what ?

---

### Post by klato on 2007-02-15
I still haven't updated the kernel yet...after reading all the horror stories, I wanted to wait until there were no problems with the packages or dependencies or whatever.  My update icon indicates that there are 6 updates available, all kernel related if I remember correctly (at work right now).  Might update this weekend, when I'll have time to fix something if it goes wrong.

---

### Post by Cariboo1938 on 2007-02-16
> **klato said:**
> I still haven't updated the kernel yet... Might update this weekend, when I'll have time to fix something if it goes wrong.Hi,
Without being negative, well, you'll better be prepared that something goes wrong. [HERE]("http://www.ubuntuforums.org/showthread.php?p=2163523#post2163523") you can find what other people did, but I was not successful yet following their instructions. It would certainly be appreciated if you could post your success in detail---
kind of a 'walk through' to help the other 61% ([POLL]("http://www.ubuntuforums.org/showthread.php?t=359752&page=6&highlight=update") result) who weren't successful yet!

[COLOR="Purple"]Hi klato,
I attached a text file explaining how I got it working! 
Don't be afraid you won't need to much time to get it going!
Good Luck[/COLOR]

---

### Post by bvanaerde on 2007-02-16
> **lonniehenry said:**
> Update broke vmware

Same here.
It took a while before I noticed it, as I was doing a lot of stuff at the same time.
I just clicked on vmware in the menu, and it never appeared. So after 15 minutes I was like "hey, I forgot to open vmware" :) 

So then I used the terminal, and then it said something about a broken config, and how to fix it.

My ATI drivers didn't work anymore either -- back to Mesa.
I solved that by using the [Envy]("http://albertomilone.com/projects.html") installer.

---

### Post by IgnorantGuru on 2007-02-16
I would say this was a very poorly tested and implemented kernel update.  The fact that lots of people have 3rd party drivers and restricted modules should not be a surprise to the devs.  Having an  automated update that renders >50% of machines inoperable is not a quality product.

If Ubuntu devs just consider this business as usual, I think their product is going to go the way of Microsoft - racing to 'improve' things while breaking more than they fix.  They need to slow down, look at what happened here, and make some fundamental changes to their approach.

Automatic updates should be tested more carefully and thoroughly than anything.  When people are manually upgrading or reinstalling, they expect to deal with bumps in the road.  But to have a routine update cause havoc like this is a different story.  It will disincline people to use updates, which defeats the purpose of timely security updates, not to mention creating an unstable environment.

Time to reassess and reevaluate whatever procedures led to this mess.

---

### Post by shane2peru on 2007-02-16
> **IgnorantGuru said:**
> I would say this was a very poorly tested and implemented kernel update.  The fact that lots of people have 3rd party drivers and restricted modules should not be a surprise to the devs.  Having an  automated update that renders >50% of machines inoperable is not a quality product.

If Ubuntu devs just consider this business as usual, I think their product is going to go the way of Microsoft - racing to 'improve' things while breaking more than they fix.  They need to slow down, look at what happened here, and make some fundamental changes to their approach.

Automatic updates should be tested more carefully and thoroughly than anything.  When people are manually upgrading or reinstalling, they expect to deal with bumps in the road.  But to have a routine update cause havoc like this is a different story.  It will disincline people to use updates, which defeats the purpose of timely security updates, not to mention creating an unstable environment.

Time to reassess and reevaluate whatever procedures led to this mess.

Well stated, and I agree.  I was very happy to find this thread, so I could voice my complaint in a form of a vote.  And by the looks of the results it is not isolated problem because of a few machines.  They really need to look at the process of releasing updates so Ubuntu doesn't go down hill.  I love Ubuntu, but if updates like that become a norm, they will fall fast.  Just calling for a check up of the development system.

Shane

---

### Post by morpheus01 on 2007-02-17
Still using Windows, still pi**ed off. 

Any sign of an update yet we can upload with an ethernet cable and that will fix the intel wireless card???

As mentioned previously I purged the old kernal and had difficulties installing a driver on the new one.

Thanks, all.

---

### Post by Kateikyoushi on 2007-02-17
This seems worse than I imagined, I better wait another week with this upgrade or maybe till next one appears.

---

### Post by rolando2424 on 2007-02-17
I still haven't made the upgrade.

I'll have to wait a few days to do it.

---

### Post by mikewhatever on 2007-02-17
> **Kateikyoushi said:**
> This seems worse than I imagined, I better wait another week with this upgrade or maybe till next one appears.

No point waiting, since it's not gonna change. As the  official statement says, you'll have to reinstall all third party stuff. I kind of hope they'll see what's going on and learn, because that update was a real killer.:confused:

---

### Post by persona_o on 2007-02-18
The latest automatic update got the new kernel working for me. I was using the previous version, and installed the updates. It installed the correct drivers, etc. and Beryl is working fine.

---

### Post by dgermann on 2007-02-18
Hi--

Have 4 Dapper boxes and had not a problem at all. I did the upgrade for all of them this weekend.

Because of the problem this fall, I have made it a policy not to upgrade anything to do with the kernel until checking these forums first, and then probably waiting some days. This is a production environment and I cannot afford a lot of time to fix problems, especially midweek.

One thing I noticed: when the kernel update first came up for me I checked to see what it wanted to install. It said two of the updates would be held back. When I actually did the upgrade yesterday, that holdback was no longer there. Looks to me like something was fixed in between.

:- Doug.

---

### Post by Kateikyoushi on 2007-02-19
> **mikewhatever said:**
> No point waiting, since it's not gonna change. As the  official statement says, you'll have to reinstall all third party stuff. I kind of hope they'll see what's going on and learn, because that update was a real killer.:confused:

I do not have time to patch it so could undervolt again therefore I might as well upgrade to feisty that's what I am considering now. not just this upgrade, there was the xorg upgrade etc...

---

### Post by shane2peru on 2007-02-20
I have had errors ever since the upgrade, and I just realized why.  My fstab was written incorrectly and swap was not mounting, and couldn't be found.  Every time I rebooted I got errors saying that the panel crashed and this crashed and that crashed, etc, I never knew why until I was thinking about making some partition changes and realized my fstab was incorrect and my swap was not being mounted!  That makes two things it messed up the Fstab and my menu.lst for grub were both written incorrectly.  That is sad!  

Shane

---

