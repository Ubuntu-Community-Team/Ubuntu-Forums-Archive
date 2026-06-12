---
title: "Never Again"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by mouseclone on 2007-04-23
Never again will I ever do an upgrade.  This was the biggest pile of horse crap i have ever seen.  Next to windows that is.

People have raved and raved about how user friendly Ubuntu is in comparison to other Linux OSes.  Microsoft does the same thing.  Why would I switch from one OS to another just to have the same problems when upgrading the OS.

I thought that this would be easier.  I guess I was wrong.  I will know better next time, and just do a clean install.  With a clean install every 6 months I am sure that Linux will run great just like Windows does if you clean install it every 6 months.

I love Linux and I am not switching back.  I know that you guys are trying to support as much as you can.  I really just needed to rant.  I just hate spending the past 3 months setting up my computer and getting it where I want it to have an upgrade break the whole thing and I have to start over at square one.

Nvidia drivers, need to be fixed now.  The password for the admin and a new screen for storing the admin password on a keyring pops up and tells me that I'm screwed because gksudo password and this admin password are different?!  Oh well I hope that I was able to get around it with doing a sudo su at the term and then user-admin from there.. I reset the password but yet to see if that would work.

One thing, and this is just an fyi, that I hate about MS is when they upgrade they change a lot of different things.  I hope that my future upgrades will not be like this one, if i do any more.

Other than that guys and gals keep up the good work.. I will continue to work on my problems here until i deside that fdisk is a better option.

---

### Post by trinity! on 2007-04-23
Six hours trying to do a CLEAN install of Ubuntu server.  Six hours of seeing "Can't mount CD" errors. Six hours of trying this and trying that and re-downloading and reburning and checking the forums for answers that do not exist.  Six hours and nothing to show for it but a fresh install of MS Windows 2003 Server.  Took 30 minutes.

---

### Post by bwhite82 on 2007-04-23
You've just mentioned one of the downsides to having a 6-month release cycle for a linux distro. Not enough testing can get accomplished in that timeframe, let alone creating updated, stable packages.

---

### Post by mouseclone on 2007-04-23
Well now I am to the point of not having sound and having to reconfigure my video card ever single time I reboot my computer just to have it looking crappy.  time to go to [http://Linuxtracker.org](http://Linuxtracker.org) and see what is out there.

---

### Post by zvacet on 2007-04-24
it is a bit o true in your posts and I understand you,but saying that reinstall Ubuntu every 6 months is the same as reinstall windows every 6 months is not true.After 6 months you will get improved Ubuntu in many ways.Will your windows reinstall be improveed after 6 months?If you have problems just post it here.Sometimes your post will be unanswered then post again.it is not easy or even possible to answer every question right away.Just don´t give up.

---

### Post by Mongoose on 2007-04-24
I hate this release as much as anyone here from a quality control standpoint.  Still, Ubuntu provides live cds and this community forum to help you see how the release is going/turned out.  Always use a live cd test if you have one before upgrading any operating system.  People have been bitching about and filing bugs for a while now.  A simple visit to the fiesty forums would've helped you avoid these issues.  You can spread some blame on upstream kernel development letting this kernel series fall behind on quality standards, and the shortened cycle of release didn't help when ubuntu changed a lot of policies like sata/ata on top of that.

Take a deep breath now.  You should downgrade to Edgy or LTS or whatever you were using before until these bugs get fixed.  You can do this if you know what you're doing with pinning and manual deps, or you can install Edgy/LTS over your Feisty and just avoid hosing your /home and /opt partitions.  Sign up for launchpad and track the bugs you're having, and when they're fixed you can upgrade and not worry -- hopefully after you do an updated live cd test.   ;)

People wanting their bugs fixed should jump on launchpad and give the devs more info where it's needed.  If I had more time ( it's 0300 here now ) I'd help debug all these issues I'm having.  I'm starting to track all my bugs waiting to see how they turn out.  A lot of issues will get fixed with upstream changes sooner or later for things like the kernel issues for input devices.  It took a lot of evidence to prove to them PS2 mice weren't working for many people example.  "Works for me on my 440BX board."  I loved that reply.  ^^

---

### Post by Soarer on 2007-04-24
I guess, for balance, I should say YMMV. It doesn't help at all, I know, but the upgrade went just fine for me, and everything works OOTB.

Sorry you're having problems, though :(

---

### Post by mouseclone on 2007-04-24
> **zvacet said:**
> it is a bit o true in your posts and I understand you,but saying that reinstall Ubuntu every 6 months is the same as reinstall windows every 6 months is not true.After 6 months you will get improved Ubuntu in many ways.Will your windows reinstall be improveed after 6 months?If you have problems just post it here.Sometimes your post will be unanswered then post again.it is not easy or even possible to answer every question right away.Just don´t give up.

zvacet:  Aye, it was a bit hasty for me to say and compare Windows to Ubuntu/Linux like that.  I know that the devs for Ubuntu/Linux work hard to get this stuff out to us.  In answer to your question about if my install would be any better with windows the answer is NO.

Currently on a clean install of Windows there are 80+ updates +SP2 + more updates afer that.  The office install and then still more updates.  God forbid you put something on a Windows computer that kills something.  you will have hell to pay.  That and the fact that SPs and updated have killed programs in the past on windows, in some cases with very little work around.

As for down grading I might do that.  I don't really care about my /opt directory.  I don't mind reinstalling everything clean.  My /home is on another HD all together, so no worries there.  I am just really upset about it is all.  I was hoping that my first experience would not be a disappointment and it was.

guess I either need to revert to 6.10 or just reinstall it.  I just hate going though the mplayer install .. haha.

---

### Post by deej_1977 on 2007-04-24
Well from what I experienced when installing 7.04 I got the feeling Feisty is definitely not ready for prime time and is - in true MS style - something that will need new patches quickly.

On my HW (Core 2  E6600 with Geforce 8800GTS) it installed fine at first but when installing the nvidia drivers it installed modules that conflict with the kernel :/. Now X refuses to start of course.

Furthermore for some reason it wants to install both the x64 and i386 generic kernels (uh?). Also, after the first install, on a brand new hard disk, fsck fired up and started correcting errors in the ext3 partition. And the package manager definitely is often confused on which architecture it should choose when installing modules. And thanks to the [slow guys at Creative labs]("http://opensource.creative.com/") I don't have sound yet either but that's not Feisty's fault, just needed to get it of my chest.

No this release just doesn't seem ready for the latest & greatest in HW and it will be removed this week-end.

Offtopic @mouseclone: you can slipstream your XP SP2 CD with the latest packages through apps like [RyanVM's update pack]("http://www.ryanvm.net/msfn/updatepack.html"). That saved me a lot of time!

---

### Post by wieman01 on 2007-04-24
I simply recommend Dapper LTS... It is a bit outdated, I have to admit. It is not as nice as other versions of Ubuntu, but at the end of the day it is very stable and reliable. No messing around. It is a shame they don't get a grip on their development & release strategy, but that's just the way it is with Ubuntu. The flipside of the coin is that we get fairly up-to-date software repositories every six months and a system that is being continuously improved.

---

### Post by subscrive on 2007-04-24
[http://ubuntuforums.org/showthread.php?t=421001&highlight=SPs](http://ubuntuforums.org/showthread.php?t=421001&highlight=SPs)
And I was thinking of dist-upgrade between 2 LTSs!

I guess I better not do it.

~A.

---

### Post by mouseclone on 2007-04-24
I don't so much care for bleeding edge unless I'm testing.

I love the idea behind the upgrade every 6 months please don't get me wrong there.  Maybe they will take what the have with 7.04 and make it stable in 7.10.  That would be ideal i guess. the .04's for bleeding and the .10's for stables.  Still get a stable one out ever year and a bleeding edge every year as well.

Right now I'm downloading 1.04 DVD and CentiOS 5.  I have Dapper at the house... I will try and get it install tonight and see what happens.  I need another computer at home to play with and not to use my main computer to do distro updates on.

I have enjoyed Ubuntu up until this point.  It was just the upgrade that pissed me off so bad.  Oh well I will just Fdisk /dev/sda1 and mount /dev/sdb1 to /home and will have all the saved files i care about.

Shouldn't take more than a few hours i hope to get things back up and running.

---

### Post by Big Ed on 2007-04-24
I just finished a dist-upgrade on an AMD-64 desktop and an i386 server.  Small problems with both but nothing too serious.  They are up and running now.

I am very happy with the upgrade system.  Beats the heck out of a re-install.  :)

Ed

---

### Post by jml on 2007-04-24
This discussion does a great job of highlighting the trade offs with different distros, release cycles and hardware.  Like mouseclone, I am not very interested in bleeding edge software unless absolutely necessary.  For my workhorse computer, (the one that has to just work all the time, no fancy hardware,) I run Debian Etch.  Rock solid distro, and only security updates, no unnessary updates.  Not cutting edge but modern enough for my needs at home.  Granted the release cycle is a bit long, but for my home computer that's ok.  My travel laptop has more esoteric needs including WPA encrypted wireless, so for me Ubuntu is the best choice here.  I do dread upgrading though, I usually wait a few weeks for the dust to settle, then I will take the plunge.  In short, the more I have to modify and tweek the distro to do what I want, the less often I want to upgrade it.

Joe

---

### Post by yabbadabbadont on 2007-04-24
There were similar issues (and complaints) when Edgy was released.  Just do what I did, wait at least one month after release before doing a clean install of the next version.  That won't help much if the released install media won't work with your hardware (even if previous versions did...), but it will allow time for solutions and work arounds to be posted to the forums.

---

### Post by SteveF on 2007-04-24
One thing that I do is to install both Ubuntu and Kubuntu on different partitions (if you prefer one dist, you could initially install it to two locations).  I keep most of my data on a common drive.

When a new release comes out, I upgrade one in case it is not clean I have the other to continue my work.  Once the initial one upgrades cleanly (or I've worked out the bugs) I'll update the other.  If a full reinstall is needed, I can still mount the bad version and get files off of it.

Yes twice the work, but I don't lose my machine and I don't usually need a full reinstall.

My personal experience has been hit and miss.  Sometimes clean install first try and sometimes one or two issues that I have to work out (like for Feisty grub menu never upgraded and I lost mouse usage for a little while).  Once required a full reinstall.

Steve

---

### Post by willcox on 2007-04-24
Well, speaking by myself,  I would say that I've had success upgrading from 6.1 &#8594; 7.04. For the 1st time with a distro.
I'm coming from the old times, you know, red hat 6.9 &#8594; fedora core 5.. I switched to ubuntu precisely by the inconvenient of "fresh intalls" each ½ year. Look, I'm not lazy, but always need all my time to do a lot of activities. And everybody knows the time required for this.

TIPS:
-You have to wait until the update manager advise you about the upgrade.
-I should say that I had success, because I simply restored my original repos (from the very first time I ran ubuntu 6.10). But FIRST, uninstalled all the "foreign" software, of course, including automatix2.
-Do not expect a good upgrade having sweet, acid, hard, etc. software; BTW, do you remember what did you install 3 months ago with its repo?

I do recognize too, that it was a "traumatic" process to my linux box...guess why?
Yeaph! the endless nvidia's problem. But it was a "piece of cake" according with these instructions:
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

Have a nice uprades!

---

### Post by craigyjack on 2007-04-24
The upgrade for me did not go well either. Well, it didn't work. I tried upgrading from 6.10 to 7.04 with the update manager, and it crashed halfway through leaving me with half Edgy packages, and half Feisty packages. Needless to say it didnt boot back up after that. So I did a clean install, and I am actually happy I did that now.

I would just definitely recommend you use a separate partition for root and home, and therefore when you upgrade, all your settings and such are saved, and you just upgrade the root partition. I set it up like that this time around, and I'm glad.

And I am definitely pleased with Feisty Fawn's usage. It seems so much fast than Edgy to me. And it seems a lot more easy on my CPU than Edgy was.

I havent come across any bugs in Feisty, so I cant input there. The only thing I had trouble with was the nvidia driver with the restricted drivers manager (but that isnt supported by Ubuntu, so not their fault). And I eventually got all that fixed anyways.

I am happy with Feisty :)

-Craig

---

### Post by Tux Aubrey on 2007-04-24
I'm pretty sure I said "never again" after Edgy - but then went ahead and tried to upgrade to Feisty when the Beta came out anyway.  Totally borked.   But like YabbaDabbaDont, I have a "dual install" - two versions of Ubuntu on the same machine.   I managed to do a clean install over the broken one once the  final release appeared but it still gave me about three days of headaches - nVidia-style.   Once I ironed out the nVidia problems (with the help of these forums), Feisty has been genuinely great for me. I still have no window decorations in Beryl, but I have given that up as too beta for me.

Surprisingly, an upgrade on an older laptop I have worked a treat - but its a pure intel machine.

Having several machines or dual booting two versions on the same machine (bearing in mind that you only have one operational GRUB!) gives you the ability to play around and work through any problems while staying connected and productive.  Its actually a great learning experience - seriously.  If I had just one machine, I'd be in a real panic and probably wouldn't have persevered with Ubuntu at all after my Edgy fiascos, which would have been a real shame (for me).

Aubrey

---

### Post by Mongoose on 2007-04-24
Oh, you kids never did the libc5 to glibc or 1.x to 2.x kernel transistions.  Good times.  ^^

Anyway kernel bugs + package bugs = don't install this unless you test with live disc first.

---

### Post by greenhat on 2007-04-24
I did a clean install on an old machine and it worked fine so I decided to try Feisty on my main desktop box. 

I tested it first with the Live CD and since that seemed to work, I held my breath and did the upgrade.  I had to reboot once due to a hardware problem I've been having, but after that.  It turned out perfect!  I was amazed.  It's been running just fine ever since.  

Since the upgrade of my desktop turned out so well it's tempting me to do an upgrade on my MythTV backend. But I think I'll play it safe and use another hard drive and do a clean install just so I can fall back to a working system if things go wrong and my wife just has to watch something right away ;-)  

Couldn't be happier with the little fawn so far :grin:

---

### Post by IgnorantGuru on 2007-04-25
I'll put my two cents in here...  I haven't tried Feisty yet - I usually give it a little time to cool.  When I do try it, I will first backup my existing Ubuntu partition.  Then I'll probably install Feisty on an extra partition to see how it gets along with my hardware, and to let me configure it at my own pace without affecting my working system partition.  Once it's ready, if it makes the grade, I will then tell grub to boot that partition instead of the old one.  Painless and pretty safe.

I love linux, and I think the community does a great job with it, but I don't have a lot of confidence in upgrades.  I've yet to see any OS or dist that really handled it well, probably due to the complexities involved.  So my preference is to do a fresh install, but using partition backups and extra partitions for a stable transition.  I think expecting upgrades or even fresh installs to go through without a hitch is unrealistic at this point, for any OS or dist.  The dev cycle is just too fast for that.  Better to accept that fact and anticipate it.

Here is my how-to on backing up partitions if this helps...  [http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)

It's been working great...  when the kernel update a few weeks ago brought down my system, it was a 5 minute fix to restore it, and then I read up on how to make the update work and tried it again successfully.  That's my approach to updates and upgrades - prepare!

---

### Post by GuiGuy on 2007-04-25
> **mouseclone said:**
> Never again will I ever do an upgrade.  This was the biggest pile of horse crap i have ever seen.  Next to windows that is.

People have raved and raved about how user friendly Ubuntu is in comparison to other Linux OSes.  Microsoft does the same thing.  Why would I switch from one OS to another just to have the same problems when upgrading the OS.
<SNIP>


I agree with your sentiments and context. I wasted last weekend with the crappy "upgrade" only to have to restore the previous image a few hours later.

And while I am at it, can we please stop Adept auto-update throwing the "There is a new version available" in our face? It is a dangerous thing not to be touched by noobies.

(K)Ubuntu upgrades NEED to be everybit as good as the clean installer.

---

### Post by techristian on 2007-04-25
Let's see.

No sound.
No wireless.
and only 600X800 video on a laptop capable of 1280X768

Would I say that this is the "easiest LINUX EVER" .....nope.

PCLINUXOS was the easiest for me. 

Dan









*** Advertising removed by staff ***

---

### Post by Wight_Rhino on 2007-04-25
> **Soldierboy said:**
> You've just mentioned one of the downsides to having a 6-month release cycle for a linux distro. Not enough testing can get accomplished in that timeframe, let alone creating updated, stable packages.

Bingo!
+1

---

### Post by mouseclone on 2007-04-25
Well I went though a mess trying to get things worked out with the upgrade and then decided to download a shell burner and get the iso so that I could do a clean install.  Now I just need to get my Nvidia set back up and programs installed.

I did follow some of yalls advice this time.  I set up 2 80gig partitions on the primary hd.  I'm going to run 7.04 for now and when the next one comes out I wil install it to the second partition.  Then use it until the next upgrade and do a clean install of it.  This way I can have cutting edge if i care too.  Or I can use it to test out other distros.  I don't know why I didn't think of it before.

I personally don't back up my home system.  I try not to put anything on a computer that i can't afford to loose.  At times I do back my personal data up to my web server so that i have a copy of it somewhere.

All in all I don't think that I will be going though the pain of upgrades any more.  I stopped doing it with Windows just because of some inherited problems that can occur.  I guess the same hold true for Ubuntu upgrades as well.

On the install last night of 7.04 everything came up.  My sound video and such.  But I installed the nvidia-glx-config and nvidia drivers and GUI crashed again.  Guess it is time to refer back to the nvidia guide to get it going again.  But everything else seems to be in working order.

One thing that I have realized out of all of this is that I still have a lot to learn about Linux in general.  I'm great at windows issues but then again i have been working on windows for over 10 years, and started on windows 3.11 for workgroups.

I still feel like i have more control in Linux even though I still don't know half of what is going on.  At least I can kill things.

---

### Post by got_nix on 2007-04-25
damn.. i dunno but I never get upgrade trouble.. other than what i arleady expect. wifi i never expect to work after an ugprade because new a new kernel would be install.. i also expected my composite desktop to fail as well.. but everything else.. works flawlessly and i've been upgrading since i started out at breezy badger

---

### Post by mouseclone on 2007-04-25
Well this has been a great conversation.  I have picked up some tips that will aid me in future installs.  i have been reading over some VMWare stuff and I think that I might just run a VMWare server at home so that i can just use Images and if one breaks then I'm good to go.  Just change the image on the server and i'm back up and running.  I'm sure it is not that easy though.  We will see.

---

### Post by methane on 2007-04-25
<rant>Ha.  I was thinking the same thing this morning when I switched my monitor on and saw on non-legible (since the graphics on the window were messed up) error message from installing.  I think it was something about GLX, but I've no idea how to tell. The window wouldn't redraw itself.  Now I've left my computer at home on and I'm afraid to reboot since I don't know if it will even do that!  I have to back-up my data from the past couple of weeks first and then see if I can' t restart the upgrade.
I should have known it wouldn't work the same way that going from Dapper to Edgy didn't work (on my laptop OR on my desktop).  And of course, on Edgy, wireless never was functional, so I re-installed Dapper!  Ahh,, good times.
</rant>

---

### Post by mouseclone on 2007-04-27
Methane:  It will reboot.  Well at least mine did.  I wouldn't fight with it though.  It wasn't worth it to me.  You can learn, well I say that, but you will more than likely have brain over load, more about a system when it is broken trying to fix it.  After 3 days, I just reinstalled my OS and kelp on trucking.

One thing for sure though, and it is like I stated before, I don't thing that any OS is worth the upgrade.  When I started this thread I was pissed.  I was looking for more than I got.  After sitting down and thinking for a while, I know that it would be impossible for the devs to test every possible configuration.  Linux is so diverse, so many ways to do different things.  To top all that off if you compile something on your own, then it would be crazy to think that it wouldn't be broken when you upgrade.

After installing 7.04 clean, I'm very happy with the product.  Polished enough for me anyways.  Sorry for slamming the devs earlier.

Also, I would sugest that if you really want the right to bitch, be part of beta testing.  That way you can send information back to the Ubuntu Devs that is catered to your set up.  I didn't do beta testing.  Maybe I will next time.  I would say the more people beta, the better the over all product/project is.

---

### Post by mikexgough on 2007-04-27
I used the upgade button from edgy................same issues and screen resolution issues,nvidia etc.
Not impressed after a few months fettling the system to my liking, gone back to dapper just now and it's a good job I back up all my work............I may just upgrade to Edgy.........maybe, just maybe but Feisty can wait a while if ever

---

