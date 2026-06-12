---
title: "Jaunty is &quot;ready&quot; to be tested! Go get it!"
date: 2008-11-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2008-11-01
Just yesterday, the Jaunty testing forum opened, as well as the first changes to the repos for Jaunty. If you're feeling especially brave, are slightly mad, and want to experience a release from its very beginnings, try it out!

**_DO NOT DO THIS ON A PRODUCTION MACHINE UNLESS YOU KNOW WHAT YOU'RE DOING! JAUNTY IS CURRENTLY IN A PRE-ALPHA STAGE_**

**Step one:** Ask yourself if you really want to be at the bleeding edge. If you're sure, proceed to step 2.

**Step two:** Comment out all the Intrepid repos - this is an absolute must, and I recommend commenting out any extras you've added, in case there's a conflict.

```
sudo gedit /etc/apt/sources.list
```

In this file, put a "#" in front of every line (without quotation marks)

Next, paste this at the bottom of the file:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted multiverse universe

(Thanks to user "Int" for this)
[B]
Step Three:[/B] Update!

```
sudo aptitude update
```

After running this, close your terminal and click the update icon in the top bar, then click "install updates"

**Step Five:** You're on 9.04 Jaunty now! Run this in a terminal to see:

```
cat /etc/lsb-release
```

You should see:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"
```

Enjoy Jaunty!

---

### Post by fatality_uk on 2008-11-01
Thanks for the info dude! I have a wee little laptop that will help in the dev from Monday :D

---

### Post by barbedsaber on 2008-11-01
just incase you no one gets it.
BAD BAD BAD BAD BAD BAD idea if you want to be able to use your computer for anything.

---

### Post by jimi_hendrix on 2008-11-01
if there isa bug that is fatal and destroys my machine...will my machine become inoperable or just lose all data?

---

### Post by billgoldberg on 2008-11-01
> **jimi_hendrix said:**
> if there isa bug that is fatal and destroys my machine...will my machine become inoperable or just lose all data?

If you have to ask, don't use this Pre-Alpha.

---

### Post by Hire on 2008-11-01
> **jimi_hendrix said:**
> will my machine become inoperable or just lose all data?

Sure

---

### Post by northern lights on 2008-11-01
> **jimi_hendrix said:**
> if there isa bug that is fatal and destroys my machine...will my machine become inoperable or just lose all data?> **billgoldberg said:**
> If you have to ask, don't use this Pre-Alpha.+1

> **Hire said:**
> Sure
How can a "this or that" type question be answered by "Sure"?
There's now way software can make hardware inoperable beyond having to reinstall an OS.

---

### Post by billgoldberg on 2008-11-01
> **northern lights said:**
> 
There's now way software can make hardware inoperable beyond having to reinstall an OS.

Actually that's not true.

The Alpha or Betas of Ibex and other distro's using the same kernel bricked a few pc's.

That kernel had a flaw which caused some Intel part to physically break.

It wasn't broken beyond repair, but still.

---

### Post by pp. on 2008-11-01
> **northern lights said:**
> How can a "this or that" type question be answered by "Sure"?
There's now way software can make hardware inoperable beyond having to reinstall an OS.

For IT people, mathematician and some other people, "A or B" is true if A is true, B is true or if either are true. Hence, "sure" means either "this" or "that" or both "this and that" are true.

If the answer was "no", then that would mean that neither "this" nor "that" was true.

> **northern lights said:**
> There's now way software can make hardware inoperable beyond having to reinstall an OS.

Not so very many years ago, there were monitors being manufactured which you could damage by sending a video signal they weren't not meant to receive.

Also, it is technically quite possible to overwrite - say - the contents of the flash memory of a computer a component such that it would not work anymore. That would render the device inoperative in a way that was quite beyond the capabilities of a normal user to repair.

So, "sure" is a correct answer even if a bit on the terse side.

---

### Post by ssam on 2008-11-01
though it is very very rare for testing software to damage hardware.

from looking at the popcon stats around the intepid beta, ubuntu had at least 10,000 testers. with all the fedora/opensuse testers, kernel devs etc, there were maybe 20,000 people running 2.6.27 dev kernels. the number of people who reported they were hit by the intel ethernet bug was about 5.

if you do decide to test ubuntu make sure you keep an eye on the ubuntu dev mailing lists, the dev forum hear, the changes rss feed ( [http://feeds.ubuntu-nl.org/JauntyChanges](http://feeds.ubuntu-nl.org/JauntyChanges) ), planet ubuntu, and the fridge. if a nasty bug like the intel one is found again, you will know pretty quickly.

---

### Post by billgoldberg on 2008-11-01
> **ssam said:**
> though it is very very rare for testing software to damage hardware.

from looking at the popcon stats around the intepid beta, ubuntu had at least 10,000 testers. with all the fedora/opensuse testers, kernel devs etc, there were maybe 20,000 people running 2.6.27 dev kernels. the number of people who reported they were hit by the intel ethernet bug was about 5.

if you do decide to test ubuntu make sure you keep an eye on the ubuntu dev mailing lists, the dev forum hear, the changes rss feed ( [http://feeds.ubuntu-nl.org/JauntyChanges](http://feeds.ubuntu-nl.org/JauntyChanges) ), planet ubuntu, and the fridge. if a nasty bug like the intel one is found again, you will know pretty quickly.

I know, but still it can happen.

---

### Post by jimi_hendrix on 2008-11-01
> **pp. said:**
> For IT people, mathematician and some other people, "A or B" is true if A is true, B is true or if either are true. Hence, "sure" means either "this" or "that" or both "this and that" are true.

If the answer was "no", then that would mean that neither "this" nor "that" was true.


Main()
{
printf("now i will ask my questions in C code because it is very lieteral");

retun 0
}

---

### Post by evilkastel on 2008-11-01
yeah, you probably should have pointed out that is a pre-alpha and is in the same development level say... that windows 7? the main development encounter where they will decide what to add is in december, so you might understand this is at the very bloody filthy edge, and just developers (and daredevil developers by the way) would install this.

---

### Post by blakjesus on 2008-11-01
Is there any way to get this working in Virtualbox?

---

### Post by Prefix100 on 2008-11-01
> **blakjesus said:**
> Is there any way to get this working in Virtualbox?

I would guess install Intrepid in virtual box, then do the steps in post #1.

---

### Post by Laibcoms on 2008-11-01
> **pp. said:**
> Not so very many years ago, there were monitors being manufactured which you could damage by sending a video signal they weren't not meant to receive.



Hah... I did that... poof, smoke...  buy a new monitor :p

---

### Post by Mazza558 on 2008-11-01
> **evilkastel said:**
> yeah, you probably should have pointed out that is a pre-alpha and is in the same development level say... that windows 7? the main development encounter where they will decide what to add is in december, so you might understand this is at the very bloody filthy edge, and just developers (and daredevil developers by the way) would install this.

It's even less developed than Windows 7. There's currently no changes at all since Intrepid other than the 10 updates which change the repos and other small things like that. The first few updates will probably break X and lots of other things.

---

### Post by fatality_uk on 2008-11-01
As stated before, it's a VERY VERY bad idea to rely on Jaunty as any kind production machine.

---

### Post by bobbocanfly on 2008-11-01
Actually..this is almost perfectly safe right now. The repositories arent open for development, so developers cant upload to them. The only changes you are going to see right now is the new toolchain (gcc, g++ etc.) being uploaded, which could mess things up if you are compiling software. 

Just in case anyone thinks this is a good idea: As soon as the repositories open (in a couple of weeks), you will be getting hundreds of updates a day, a couple of them will make something break. Not recommended, unless you plan on doing a reinstall within the next few weeks.

---

### Post by Kevbert on 2008-11-01
Ready to spill some blood and try it on an old desktop. Hopefully the hardware requirement specs are the same as Intrepid.

---

### Post by toupeiro on 2008-11-01
Pre-Alpha's like this are great fodder for VM's...

BTW, for whomever said software cannot render hardware unusable beyond an OS install.  Let me remind you of the once infamous, and now likely completely forgotten, [Michaelangelo Virus]("http://en.wikipedia.org/wiki/Michelangelo_virus"), which literally wrote different sector and cylinder counts to your hard drive..  Simply reinstalling after being hit by this software virus wouldn't get you very far.  Something doesn't have to be dubbed "virus" to unintentionally do something similar with pre-alpha code....  Especially, a pre-alpha OS.

---

### Post by Changturkey on 2008-11-01
Man, you guys are eager.

---

### Post by Kevbert on 2008-11-02
Thanks Mazza558. Just updated Intrepid. There are only 12 updates today (2/11/08) Is that correct ? and the boot menu still shows Intrepid 8.10 ?

---

### Post by Starks on 2008-11-02
Pre-alpha code...

I know plenty of people that get off to this kind of stuff.

---

### Post by macogw on 2008-11-03
> **jimi_hendrix said:**
> Main()
{
printf("now i will ask my questions in C code because it is very lieteral");

retun 0
}

Error Line 5: Unknown operator 'retun'
Error Line 6: Character '}' found, missing opening '{'

---

### Post by Scruffynerf on 2008-11-03
> **jimi_hendrix said:**
> if there isa bug that is fatal and destroys my machine...will my machine become inoperable or just lose all data?

**IMPORTANT NOTE**

Please be aware that installing and running systems prior to a stable release you may experience any and all of the following:

Data Loss
Driver Loss
Firmware Loss
Potential permanently bricking of hardware (as in: Return to manufacturer)*

*As recently discovered with the e1000 wired networking drivers for what later became the Intrepid kernel.

---

### Post by TheSlipstream on 2008-11-03
This...this is actually serious? Wow, I thought the first post was a joke, but there is actually a Jaunty repo right now? Here I was thinking they just froze Debian Testing repeatedly during the Alpha period.

---

### Post by Joeb454 on 2008-11-03
ACK You said "sudo gedit" don't do it!!! ```
gksudo gedit
``` :D

Also - > **jimi_hendrix said:**
> Main()
{
printf("now i will ask my questions in C code because it is very lieteral");

retun 0
}

Try [php]#include <stdio.h>
int main()
{
   printf("now i will ask my questions in C code because it is very literal\n");

   return 0;
}[/php]

---

### Post by yorkie on 2008-11-03
I will be the first to ask has Jaunty got  a new theme, if not why 
first  of many

---

### Post by ghindo on 2008-11-03
> **yorkie said:**
> I will be the first to ask has Jaunty got  a new theme, if not why 
first  of manyIt's still pre-alpha, so no, it doesn't have a new theme yet.

---

### Post by ronacc on 2008-11-03
> **yorkie said:**
> I will be the first to ask has Jaunty got  a new theme, if not why 
first  of many

You're a day late  [http://ubuntuforums.org/showthread.php?t=968197](http://ubuntuforums.org/showthread.php?t=968197)

---

### Post by niccholaspage on 2008-11-03
My upgrade went fine. All it did is change meh operating system info.

---

### Post by meborc on 2008-11-04
i wouldn't touch jaunty with a pole... not before the second half of January anyways... then things will get interesting... before that - frustrating reinstalls... and i hope i don't hear any complaints from those who upgrade now... just read my sig ;)

---

### Post by philinux on 2008-11-04
> **meborc said:**
> i wouldn't touch jaunty with a pole... not before the second half of January anyways... then things will get interesting... before that - frustrating reinstalls... and i hope i don't hear any complaints from those who upgrade now... just read my sig ;)

Two hard drives ):P

---

### Post by ShirishAg75 on 2008-11-04
That is a good solution. Although I have a query, is it a good idea to not use Intrepid-proposed repository, the last time. 

I asked because during the Intrepid development cycle I had Hardy-proposed updates and during updates, had to downgrade quite a few packages in order to get the correct chain of updates from Intrepid, what do you think of that?

---

### Post by autocrosser on 2008-11-05
Three harddrives & tri-boot):P


> **meborc said:**
> i wouldn't touch jaunty with a pole... not before the second half of January anyways... then things will get interesting... before that - frustrating reinstalls... and i hope i don't hear any complaints from those who upgrade now... just read my sig ;)

---

### Post by cariboo on 2008-11-05
During the Intrepid run up, I doubt if I had to boot up my hardy partition more then 2 or 3 times. I ran Intrepid full time before the first alpha, although I did use rsync to keep my email directories synced up, just in case.

Sometimes I wonder if the people who complain about not having a new theme for every release, really use Ubuntu, or just boot it up when their friends come to visit to show them how l33t they are. :)

Jim

---

### Post by meborc on 2008-11-05
> **autocrosser said:**
> Three harddrives & tri-boot):P

it doesn't matter how many hard drives you have... when jaunty breaks, you need to reinstall to test it... or you are going to install it now, and leave it like it is if it breaks (which will happen in December for sure)?

---

### Post by Gina on 2008-11-05
If everyone took the view that they shouldn't test a new development until half way through or later then there would be no testing, nobody finding bugs and no bugs fixed!  It would be months of wasted testing time.  Having said that, I wouldn't recommend it for Ubuntu novices for two reasons - not knowing how to cope with a foul up and not knowing how to report the bug correctly.  AND of course, it's not recommended to try it on your one and only computer that you need for other purposes.  A spare machine is best.

---

### Post by plun on 2008-11-05
Well... it has started the big package update...:guitar:

Alsa 1.0.18 and PA 0.9.13

Lilo was thrown in with debconf...

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/thread.html)

Severe breakage risk..):P

---

### Post by meborc on 2008-11-05
> **Gina said:**
> If everyone took the view that they shouldn't test a new development until half way through or later then there would be no testing, nobody finding bugs and no bugs fixed!  It would be months of wasted testing time.  Having said that, I wouldn't recommend it for Ubuntu novices for two reasons - not knowing how to cope with a foul up and not knowing how to report the bug correctly.  AND of course, it's not recommended to try it on your one and only computer that you need for other purposes.  A spare machine is best.

in the beginning of the development cycle a lot of things are meant to be broken... just because many things collide and the devs need to testrun/trytogeteverythingworking themselves... they know the bugs and setbacks they are introducing for some greater good... no need for testing in that period... the community bug testing / bug tracking period starts when the big jump from intrepid to jaunty has been done... when the major breakage is repaired... do you thing that the devs don't do any testing themselves and that they don't notice that X is not starting after an upgrade? :)

reporting bugs in early weeks in to the 6 month cycle is going to bring more problems than solutions to the devs... i would wait till new year to start begging them to fix X although they know it is broken and why it broke before they introduced the upgrade that broke it :)

but that is of course my own oppinion

---

### Post by plun on 2008-11-05
> **meborc said:**
> in the beginning of the development cycle a lot of things are meant to be broken... just because many things collide and the devs need to testrun/trytogeteverythingworking themselves... they know the bugs and setbacks they are introducing for some greater good... no need for testing in that period... the community bug testing / bug tracking period starts when the big jump from intrepid to jaunty has been done... when the major breakage is repaired... do you thing that the devs don't do any testing themselves and that they don't notice that X is not starting after an upgrade? :)

reporting bugs in early weeks in to the 6 month cycle is going to bring more problems than solutions to the devs... i would wait till new year to start begging them to fix X although they know it is broken and why it broke before they introduced the upgrade that broke it :)

but that is of course my own oppinion

Well.. before Alpha 1 a lot are "As is".

It is rather interesting to manage a dev distribution with broken functions...  mainly with apt and aptitude when GUIs are broken or packages.

But to file bugs must be done with some thoughts...):P

Nearly all devs also just run in chrooted environments and they don't see
all errors...

After Alpha 1 "the GUI whining s"  can start....:lolflag:

---

### Post by Gourgi on 2008-11-05
i'd love to here some developers thoughts about the subject discussed here.
i want to hear what they think about the community testers upgrading to pre-alpha or alpha [1,2,3] and also about whether or not would be helpfull for them to our filling bugs till then.

---

### Post by plun on 2008-11-05
Developer announcement is now out....

> Hello world,

Following a brief period while we got the toolchain into shape, the
Jaunty Jackalope is now open for general development. [B][U]Please remember to
wear your seat-belt[/U][/B], and remember that bugs in the rear-view mirror may
be closer than they appear. [U][I][B]Automatic syncs from Debian will begin
shortly.[/B][/I][/U]

The release schedule for Jaunty is available at
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule). To summarise the next few
months, we expect to be able to produce the first milestone in
mid-November, to cease automatic syncs from Debian towards the end of
December or early January (this date is still uncertain, as it's proving
difficult to wedge in around UDS and Christmas), and to enter feature
freeze in mid-February.

[B]We do not recommend that users upgrade to Jaunty at this time; [B]it is
likely to be in very considerable flux until the initial round of merges
is complete[/B]. As ever, any developers wishing to take the plunge at this early stage should ensure that **they are comfortable with recovering from anything up to complete system failure.**[/B]

Good luck!

-- 
Colin Watson                                       

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000510.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-November/000510.html)


---

### Post by mixmatch on 2008-11-05
How feasible would it be to pick and choose packages out of [https://launchpad.net/ubuntu/jaunty](https://launchpad.net/ubuntu/jaunty) ? Obviously one would have to resolve dependencies from there as well...

---

### Post by Gourgi on 2008-11-05
[QUOTE=Colin Watson]
We do not recommend that users upgrade to Jaunty at this time; it is
likely to be in very considerable flux until the initial round of merges
is complete. As ever, any developers wishing to take the plunge at this early stage should ensure that they are comfortable with recovering from anything up to complete system failure.
[/QUOTE]

that's what i've been looking for, thanks !

---

### Post by autocrosser on 2008-11-06
One stable Hardy install & I run testing installs one back one week from the other--update the second one on a "safe" day---normally Sundays--very few updates then--that way, when one breaks, I use the second one to see the diffs & fix the first one......

Been testing software for well over ten years now & I do think I know what I like--only had to install Intrepid two times last cycle & I was in from day one to the very last...one reinstall was from a "opps" update @ 2am--was not thinking very well then......

I REALLY like testing pre-alpha software--You may not--but I like to & accept the risks/rewards/brain-strain that comes from it.

> **meborc said:**
> it doesn't matter how many hard drives you have... when jaunty breaks, you need to reinstall to test it... or you are going to install it now, and leave it like it is if it breaks (which will happen in December for sure)?

---

### Post by Yellow Pasque on 2008-11-06
Downloading Jaunty seems kind of boring right now, especially with so many issues still to be worked out in Intrepid. Call me when it gets GNOME 2.26 or a stable 2.6.28 kernel.

---

### Post by go7Ul1ai on 2008-11-06
> **Temüjin said:**
> Downloading Jaunty seems kind of boring right now, especially with so many issues still to be worked out in Intrepid. Call me when it gets GNOME 2.26 or a stable 2.6.28 kernel.

Of course it seems boring, work has only just being started on Jaunty -_-

---

### Post by stinger30au on 2008-11-06
i hope some one send an email to nvidia and lets them know, that way they have got 6 months to get their fingers in to gear and write a video driver that works for when it goes final!!

---

### Post by BCurtisWX on 2008-11-06
I would also like to note, for those of you who have Intrepid Ibex and want to test Jaunty.. use virtualbox and create a virtual disk and load the ISO, then install intrepid and change the repos.. this makes it so if anything breaks completely, you don't harm your system. (you can then delete the virtual disk and create a new one)

---

### Post by kyleabaker on 2008-11-06
> **BCurtisWX said:**
> I would also like to note, for those of you who have Intrepid Ibex and want to test Jaunty.. use virtualbox and create a virtual disk and load the ISO, then install intrepid and change the repos.. this makes it so if anything breaks completely, you don't harm your system. (you can then delete the virtual disk and create a new one)

+1

That's what I did. However, when Alpha 1 is released I'll feel ready to do the actual upgrade. I can handle problems here and there (also have another pc just in case), but for the most part Intrepid was very stable once it reached Alhpa 1 with minor problems if you know what you are doing.

But you're right. If you don't feel comfortable losing your data then use VirtualBox or just don't bother with Jaunty until it's released.

---

### Post by jerrylamos on 2008-11-07
Most (not all!) of the time dual boot does fine for testing shaky Alpha ubuntu's.  That way, if the test partition crashes I can boot the other partition to look at the wreckage.  Worked well on chasing Launchpad Bug #259358 "black screen freeze after login with Intel video" I reported on Aug 19, not fixed on release code 2 months later.  Update went out after, with the catch 22 you have to be running to get the update so that you can run.  Yes there's a workaround.

Once, an alpha formatted all 4 partitions on 2 drives before I realized what it was doing.

For a while I shared /home between the two test partitions but that went bonkers a couple of times.  I just copy files & Documents now.

Jerry

---

### Post by Slug71 on 2008-11-07
Does anyone know yet what we can expect in Alpha 1 or when details will be released?

---

### Post by plun on 2008-11-07
> **Slug71 said:**
> Does anyone know yet what we can expect in Alpha 1 or when details will be released?

Take a look at the sticky thread....8-)


A little slow pace for the moment....:)

---

### Post by cariboo on 2008-11-07
Testing Jaunty in a vm really  doesn't do much good, as you aren't using real hardware and any bugs that come up only pretain to running it in a vm. In my opinion you're testing the vm and not Jaunty.

Jim

---

### Post by plun on 2008-11-08
> **cariboo907 said:**
> Testing Jaunty in a vm really  doesn't do much good, as you aren't using real hardware and any bugs that come up only pretain to running it in a vm. In my opinion you're testing the vm and not Jaunty.

Jim

I have the same opinion and therefore I run it as a sharp install.

/home on a separarate partition and backups,  let it break !

---

### Post by jerrylamos on 2008-11-08
> **philinux said:**
> Two hard drives ):P

An Alpha last winter formatted all four installed partitions on two hard drives.  Still don't know how it happened however there was some developer buzz about it.

Jerry

---

### Post by MacUntu on 2008-11-09
That's why I stay away from installations and only do upgrades. :guitar:

---

### Post by autocrosser on 2008-11-09
Same thing here--I keep two upgraded installs--one I update on a weekly basis--when it looks "safe"--that way I still have one testing install alive if the other one "blows-up"--I also have one stable install as a final backup--have left Hardy there.


> **MacUntu said:**
> That's why I stay away from installations and only do upgrades. 

---

### Post by blazemore on 2008-11-10
Okay I'm interested in following the development, so I'm going to do this in a virtual machine

---

### Post by vishalrao on 2008-12-27
I'm only just now upgrading from Intrepid to Jaunty. :D

Changed my sources.list as in the OP, but update manager asks if I want to do a partial upgrade.

Should I? Or close that window and continue with regular upgrade, or do a simple "sudo aptitude upgrade" in the terminal?

---

### Post by taavikko on 2008-12-27
> **vishalrao said:**
> I'm only just now upgrading from Intrepid to Jaunty. :D

Changed my sources.list as in the OP, but update manager asks if I want to do a partial upgrade.


There's no need to manually edit sources.list soon after alpha1
Because, update-manager-core is able to do so, via
"do-release-upgrade -d" or "update-manager -d" If it isn't, check software-properties settings that it shows all releases.

Also concerning OP, why manually edit sources.list when we have this thing called "sed"

```
sudo sed -i 's/intrepid/jaunty/g' /etc/apt/sources.list
```

---

### Post by Gina on 2008-12-27
IMV it's better to install a new version into a new partition especially a development version which is almost certain to go wrong at some stage.  Then you have your old system to fall back on.  That is what I always do.  There are two Alphas out now so you can simply install from one of those - Alpha 2 preferably, otherwise there are a lot of updates to install.

---

### Post by taavikko on 2008-12-27
> **Gina said:**
> IMV it's better to install a new version into a new partition especially a development version which is almost certain to go wrong at some stage.  Then you have your old system to fall back on.  That is what I always do.  There are two Alphas out now so you can simply install from one of those - Alpha 2 preferably, otherwise there are a lot of updates to install.

I agree. It's even better to have a spare comp to try it on..

I upgraded yesterday my main comp. Which is been running nice since intrepid alpha 2 :D could say it's in a bit of a mess...

Tried twice on my subnotebook (aspireone) but shortly after decided to switch back to Intrepid, mainly because the working wireless drivers. 
Any news when ath5k or compliant drivers will appear on jaunty?

Main warning about using these dev-versions, DON'T!
If lacking basic skills to do so.
Make yourself useful in testing, contribute, don't just use because it's new and shiny!

---

### Post by vishalrao on 2008-12-27
Me want shiny!

Well, I stubbornly went ahead and started "sudo aptitude upgrade" since it shows about 465 mb of downloads while update manager apparently doesn't want to install all packages - gives that "partial upgrade" suggestion and only shows 333 mb available for download... its still downloading, will take about another 10 hrs with my pathetic speeds so I have some time to chicken out.

I think I just about have the basic skillz to play around with Jaunty at this stage :D If something breaks I can come crying to the forums!

Going to try Jaunty on my tablet PC since my desktop is used by others in the family for documents/web browsing etc. Just hope I don't "brick" the tablet - fingers crossed.

---

### Post by Gina on 2008-12-27
Golden rule - never do anything you don't know how to "undo".  Have anything of any value backed and be prepared to reinstall from scratch.  Indeed be "happy" to reinstall from scratch - it's very likely to be needed in development.

---

### Post by jerrylamos on 2008-12-27
> **Gina said:**
> Golden rule - never do anything you don't know how to "undo".  Have anything of any value backed and be prepared to reinstall from scratch.  Indeed be "happy" to reinstall from scratch - it's very likely to be needed in development.

Ready?  No it isn't.  Won't install.  For at least the last week and a half of daily builds, manual partitioning edit partition use as hangs ubiquity.  

I keep dumping full apport crash reports onto launchpad.  example 210982.  No replies or acknowledgements of any sort.  As far as I can tell no developers are interested in users installing jaunty.

This is a jaunty upgrade - I installed intrepid (trudge) then upgraded (trudge) I much prefer install daily build in a partition, if it crashes, then back up to the last daily build.  Multiple boot so I usually have a partition that will work - once, however, a Ubuntu alpha re-wrote entire partition tables on two hard drives.  Down the tubes.

Jerry

---

### Post by ShirishAg75 on 2008-12-27
please mark bugs like these [lpbug]210982[/lpbug]

The bug though is not of ubiquity but of system-config-printer. Are you sure you have given the right bug number?

---

### Post by Gina on 2008-12-27
> **jerrylamos said:**
> Ready?  No it isn't.  Won't install.  For at least the last week and a half of daily builds, manual partitioning edit partition use as hangs ubiquity.  

I keep dumping full apport crash reports onto launchpad.  example 210982.  No replies or acknowledgements of any sort.  As far as I can tell no developers are interested in users installing jaunty.

This is a jaunty upgrade - I installed intrepid (trudge) then upgraded (trudge) I much prefer install daily build in a partition, if it crashes, then back up to the last daily build.  Multiple boot so I usually have a partition that will work - once, however, a Ubuntu alpha re-wrote entire partition tables on two hard drives.  Down the tubes.

JerryI had a similar thing happen once - destroyed the partition table and I thought I'd lost the lot (was backed up though).  However, I ran ***testdisk*** from a live CD and rebuilt the partition table from the data on the HD.  It was a little tricky to remember and work out which data was in deleted partitions (by me) and which was wanted and in the partition table when it was destroyed.  But I succeeded in getting virtually everything back after letting ***testdisk*** rewrite the partition table.

As for Alpha 2, I haven't as yet succeeded in installing it but I have a couple more machines I can try on - so we'll see.

---

### Post by ronnielsen1 on 2008-12-27
The upgrade went fine for me. I figured I could always fix it if it broke and the partial upgrade followed by another upgrade went fine. No problems so far

> ron@ron-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"
ron@ron-desktop:~$ 


---

### Post by vishalrao on 2008-12-27
well what do you know, upgrading (sudo aptitude safe-upgrade) from intrepid amd64 to current jaunty appears to have worked smoothly for me.

by "smoothly" i mean i rebooted my tablet PC and logged into gnome with compiz goodness (nvidia go 6150) and broadcom sta (wl) wifi and sound all working.

it's almost im still on intrepid. uname shows kernel 2.6.28.3, about-gnome shows 2.25.3 :D

edit: firefox is still at 3.0.5 and openoffice still at 2.4.1, is that right? everything seems eerily stable and quiet :lol:

---

### Post by Yellow Pasque on 2008-12-27
Reinstalling the OS is for Windows users! If you're having an issue in Linux, research it, fix it, report it as a bug, etc. Ok, not everyone has time for that (but they shouldn't be using a pre-release if they don't), so the best advice I can give is to have a seperate /home partition. If you do have to reinstall the OS, you can keep your personal data, program preferences, bookmarks, etc.

---

### Post by plun on 2008-12-27
> **vishalrao said:**
> 
edit: firefox is still at 3.0.5 and openoffice still at 2.4.1, is that right? everything seems eerily stable and quiet :lol:

Well. for unknown reasons FF3.05 is "default" for Jaunty and you must manually install **firefox-3.1**

About:
[http://packages.ubuntu.com/jaunty/firefox-3.1](http://packages.ubuntu.com/jaunty/firefox-3.1)

---

### Post by ronnielsen1 on 2008-12-28
> so the best advice I can give is to have a seperate /home partition. If you do have to reinstall the OS, you can keep your personal data, program preferences, bookmarks, etc.
I know I should but I never have. The two main OSes I use are Mepis and Ubuntu. Mepis will let me reinstall or upgrade saving home (yes - even on same partition) and I usually back up Ubuntu home so it's an easy fix if something goes wrong.

---

### Post by sofasurfer on 2009-01-24
When creating a new sources.list for Jaunty, is it just a matter of copying my Intrepid .list and changing all instances of 'Intrepid" to "Jaunty"?

---

### Post by bruce89 on 2009-01-24
> **sofasurfer said:**
> When creating a new sources.list for Jaunty, is it just a matter of copying my Intrepid .list and changing all instances of 'Intrepid" to "Jaunty"?

The more usual way is to use *update-manager -d*, or *do-release-upgrade* instead of manually updating all the packages after changing the sources.list. Indeed, I used *update-manager -d* a few hours ago with complete success.

---

### Post by Gina on 2009-01-24
I prefer to install afresh into a separate partition for testing - leaving the released varsion as backup.  Development versions frequently go wrong - this is expected.  Use the Alpha 3 (or daily build).

---

### Post by Giric on 2009-01-24
Firefox is in 3.1 beta 2

OpenOffice.org is in 3.0.0

As of writing this, Gnome is in 2.25.5 (beta development for 2.26 sceduled for Mar 18 according to [http://live.gnome.org/TwoPointTwentyfive/](http://live.gnome.org/TwoPointTwentyfive/))

KDE is in 4.2 RC 2, IIRC.  Couldn't find the RC # on KDE's site.

Linux.org only lists Kernel 2.6.28.2-rc1  That Ubuntu's using a .3 doesn't surprise me, though. :)

---

### Post by go7Ul1ai on 2009-01-24
I'm starting a dist upgrade to Jaunty, usually I start testing in Alpha 1, I'm a litte bit late this time ^.^

x

---

### Post by Gina on 2009-01-24
Present kernel in Jaunty is 2.6.28-5

---

### Post by Yellow Pasque on 2009-01-25
> **Giric said:**
> Linux.org only lists Kernel 2.6.28.2  That Ubuntu's using a .3 doesn't surprise me, though.
The dash (-) in the Ubuntu revision is not equivalent to a dot (.) in the "vanilla" kernel.org revision.
Ubuntu uses its own custom kernel-source and numbers differently than kernel.org.

If you really want to know what vanilla kernel Ubuntu's kernel is based on, look at the changelog for linux-source-2.6.28.
At the moment Ubuntu 2.6.28-5... is based on vanilla 2.6.28.1

---

### Post by bruce89 on 2009-01-25
> **Temüjin said:**
> If you really want to know what vanilla kernel Ubuntu's kernel is based on, look at the changelog for linux-source-2.6.28.
At the moment Ubuntu 2.6.28-5... is based on vanilla 2.6.28.1

Actually, the source package is just *linux* since Intrepid (or Hardy).

---

### Post by Yellow Pasque on 2009-01-25
> **bruce89 said:**
> Actually, the source package is just *linux* since Intrepid (or Hardy).
"linux" and even "linux-source" are just meta-packages that point to the image and kernel source packages, respectively. The changelog for "linux-source" just notes exactly which source package it points to. The changelog for linux-source-<major kernel version> is the one with all of the details, and also tells you what "vanilla" kernel version it's based on.

---

### Post by bruce89 on 2009-01-26
> **Temüjin said:**
> "linux" and even "linux-source" are just meta-packages that point to the image and kernel source packages, respectively. The changelog for "linux-source" just notes exactly which source package it points to. The changelog for linux-source-<major kernel version> is the one with all of the details, and also tells you what "vanilla" kernel version it's based on.

*linux-meta* is the meta package, *linux* is the source package - [https://edge.launchpad.net/ubuntu/+source/linux](https://edge.launchpad.net/ubuntu/+source/linux). You're getting confused between source and binary packages.

---

### Post by isionous on 2009-01-28
What is the best way to revert from Jaunty back to Intrepid?

---

### Post by OrangeCrate on 2009-01-28
> **isionous said:**
> What is the best way to revert from Jaunty back to Intrepid?

There's no way to backup, you'll have to reinstall Intrepid.

---

### Post by isionous on 2009-01-28
> **OrangeCrate said:**
> There's no way to backup, you'll have to reinstall Intrepid.

Thanks, OrangeCrate.

---

