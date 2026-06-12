---
title: "when is the safe time to upgrade (or tips on upgrading)"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-02-28
Since the big python upgrade, i imagne a lot of people had their jaunty installs foobared. I was thinking of upgrading only when a new alpha/beta is out, but that might be anexaggerated measure... So i'd like to hear what you tricks are to make safe upgrades during alpha stages.

---

### Post by Gina on 2009-02-28
I don't think there's any such thing as a "safe upgrade" during alpha stages.  Alpha means likely to be bad!  It can only be considered "safe" after final release and not necessarily then on all machines.  It's always important to have good (tested) backups.

---

### Post by Stochastic on 2009-02-28
That's like asking where the safe place to step on a minefield is.

I don't like to use the analogy of a minefield with Ubuntu, but maybe more of a sink-hole-field (where time disappears mysteriously)?

Testing is testing... test early, test often, help us all improve.

---

### Post by TrueTom on 2009-02-28
Update via the command line an check if it wants to remove packages. If it does check again a few hours later, if not you should be fine then...

---

### Post by Hobbsee on 2009-02-28
After it's released.

---

### Post by jfernyhough on 2009-02-28
> **Hobbsee said:**
> After it's released.+1

If you really want to, though, grab the latest alpha CD image and install it. Then on your first set of updates use Synaptic and go through the packages manually, one by one if necessary. It should be fairly easy to find which packages are causing removals and unmark them (or mark all of the others).

This is how I've avoided borking my install after the python upgrade - I have updates for python, gimp, openoffice all waiting patiently for the other python-based programs to be rebuilt.

---

### Post by philinux on 2009-02-28
Never do a partial upgrade.

---

### Post by BLTicklemonster on 2009-02-28
That's a good question. I thought perhaps that I could upgrade from Hardy a couple of weeks ago, but it was a catastrophe. I have tons of spare space, and actually made sure I had a partition empty just in case this time ;) and it came in handy because I could not recover and had to do a fresh install on a blank partition. Fortunately all the cool stuff I had in /home/me was there to be dragged over to the new partition.

No idea why I couldn't use Ibex, but I'm a bit afraid to try it again. I might download the live cd and install it on a blank partition later, and see how it goes.

Anyhow, I've had plenty of luck on upgrades in the past once a version is out for a while. Which has nothing to do with alpha releases, I'm just bored and figured I'd post something other than lol or +1.

---

### Post by Vorian Grey on 2009-02-28
Probably the safest time to upgrade would be when the next alpha is released.

---

### Post by andrewabc on 2009-02-28
You should definitely download a live cd to see what works and doesn't work on the livecd by default. If everything works fine on the livecd, then at least you don't have to worry about filing lots of bugs, and can wait until at least the beta or RC before installing. I assume you've installed alpha/beta ubuntu releases before and know what to expect, aka format/reinstall several times possible, along with any data loss?

I had to format/reinstall my jaunty install twice in the past 2 weeks. Mostly because it was the easiest solution to problems. It is being tested on an old computer, and there isn't anything important on it, so it doesn't really matter other than the time spent. But I like to know what works/doesn't work on my computers before final release, because at final release it is a bit late to start reporting bugs to get fixed.

---

### Post by BLTicklemonster on 2009-02-28
Yeah, I agree. I'm in the process of downloading 8.10 now.

---

### Post by Kow on 2009-02-28
I always upgrade my desktop at the beta release, but even then it isn't surely safe. It was either gutsy or feisty in which a bad libc upgrade was pushed through after beta-freeze which b0rked everyone's system. You had to do chroot from a livecd environment to fix it.

---

### Post by talkingwires on 2009-02-28
I just switched over to Jaunty, right in the middle of the whole Python situation, and haven't had any problems. The trick is to upgrade in stages instead of typing "apt-get dist-upgrade" and hoping for the best.

I check the forums first, to see if there's any major issues. Then I do the upgrade in stages, each one more likely to cause breakage: kernel and core libraries first, applications and other libraries next, then Gnome. I do a dist-upgrade last for X, network-manager, and packages that need to be added or removed last, as that step has the most potential for breakage. If apt says a package needs to be removed and I don't recognize what it is, I look it up to make sure, first.

---

### Post by andrewsomething on 2009-02-28
First of all, during development there will be breakage. This can't be stressed enough.

Next, there are some tips in this thread about upgrading existing development installs, but the original question seems to be more about upgrading from Intrepid to Jaunty. Doing a clean install from a milestone release is probably the safest bet, but if you want to upgrade an existing install here's what I do. 

I find that the safest time to do the upgrade is during the milestone freeze. Right after an Alpha or Beta release, main opens up again and uploads that have been waiting are pushed in. It sounds a little unintuitive, but I find that right after a release is one of the worst times to upgrade.

Also, checking the forums is good, but if you are going to use the development version you really should be subscribed to _at least_ the devel-announce mailing list.

---

### Post by BLTicklemonster on 2009-02-28
Intrepid installed now. Audio didn't work, had to change to soundblaster from auto in settings, then viola, surround sound was simple for the first time ever. I love the "shall we peruuuuuse the internet for the proper codecs?" feature when trying to play something, also.

Except for pulse audio being allowed anywhere near it, this version of Ubuntu has a lot of things right for once.

---

### Post by nanog on 2009-02-28
unfortunately jaunty is running flawlessly on dell mini 9 and m1330. 

please, please give me some breakage, developers!

---

### Post by autocrosser on 2009-02-28
I always CHECK if a partial upgrade is indicated...As the old map makers put on the edge "beyond be Dragons...."  As soon as I see the signs, I fire-up the forum & see if anything is buzzing in the community---you will most likely find a wealth of info in the lead page--lastly, Do Not Do partial-upgrades--they can leave your system in a unstable state (Imagine---a unstable Alpha:P ).....And I do not blindly upgrade--I will put off anything surrounding the non-upgraded software until it looks Ok---that will save you about 50% of the time---the rest.....well, it's a Alpha after all & you need to know how to recover from a real Foobar'd mess to even be here..........And yes, I watch the dev lists--my Email load is around 2~300 per day & I at least read thru the dev-announce & discuss...

TalkingWires---Mate--it has been a while from the Fawn--you might update (grin) your Testing info........

---

### Post by autocrosser on 2009-02-28
> **nanog said:**
> unfortunately jaunty is running flawlessly on dell mini 9 and m1330. 

please, please give me some breakage, developers!


Just wait my friend..........

And nanog---Hardy has been over-tested also ;)

---

### Post by Scubdup on 2009-03-03
> **Vorian Grey said:**
> Probably the safest time to upgrade would be when the next alpha is released.Do you mean by this, upgrade to Jaunty when the alpha for Killer Koala is released?

This noob was getting all excited about his first upgrade and counting down the days to April, but now I'm thinking about holding off.

(Without wanting to threadjack, and only if they're easily answered - a couple of noob questions: Is an upgrade - excepting any subsequent glitches -  a painless process - ie, will it be flagged up in the notification area and require a one-click "yes please - upgrade" or is it more involved. And second question, when in the month do the upgrades come out - at the beginning or the end?)

---

### Post by ELD on 2009-03-03
I don't install it until it is officially released, but i do download and test alpha/beta/rc live cds now and then, like today i will burn alpha5 and take it for a spin, but i won't install.

---

### Post by nyarnon on 2009-03-03
Safe is the keyword here. Save is equivalent to stable release?

---

### Post by jerrylamos on 2009-03-03
Never to jaunty if you have Intel graphics like i830 and i845, see launchpad bug #304871.  Linux people "upstream" of Ubuntu decided to exploit some capabilities of the latest and greatest and expensivist hardware and aren't interested in the rest of us.  The fatal bug has been around since before Alpha 1 and doesn't seem to have any solution so far.

Two pc's here, IBM Thinkpad and IBM Think Centre, after 2 months of battling jaunty are back on 8.10 intrepid (rescue mode apt-get remove compiz compiz-core).   Sounds just like Microsoft, if you want to keep up with Windows you have to keep buying more hardware and creating more toxic trash.  It's a shame to me because the two IBM pc's run just fine for Intrepid internet, flash, office write & spreadsheet, digital photos, mail...  Just not jaunty.

Two others, an IBM laptop and a Compaq Presario with ATI graphics are doing O.K. with jaunty much of the time depending on the state of Pulse Audio changes.  They are dual boot so if the latest build has problems just boot the preceding one that ran O.K.

Jerry

---

### Post by nyarnon on 2009-03-03
@ jerrylamos

This has nothing to do with buying only the newest hardware. In fact I run compiz on hardware much older then yours. Now you think again, what could possibly be the reason those bad-*** upstream compiz guys will just not support your hardware? Do they have it in for you? Do they have contracts that make them have you buy new stuff? Or did ibm/intel simply put cheap **** in your pc that just isn't up to the task?

---

### Post by andrewabc on 2009-03-03
> **jerrylamos said:**
> Never to jaunty if you have Intel graphics like i830 and i845, see launchpad bug #304871.  Linux people "upstream" of Ubuntu decided to exploit some capabilities of the latest and greatest and expensivist hardware and aren't interested in the rest of us.  The fatal bug has been around since before Alpha 1 and doesn't seem to have any solution so far.

Two pc's here, IBM Thinkpad and IBM Think Centre, after 2 months of battling jaunty are back on 8.10 intrepid (rescue mode apt-get remove compiz compiz-core).   Sounds just like Microsoft, if you want to keep up with Windows you have to keep buying more hardware and creating more toxic trash.  It's a shame to me because the two IBM pc's run just fine for Intrepid internet, flash, office write & spreadsheet, digital photos, mail...  Just not jaunty.

Two others, an IBM laptop and a Compaq Presario with ATI graphics are doing O.K. with jaunty much of the time depending on the state of Pulse Audio changes.  They are dual boot so if the latest build has problems just boot the preceding one that ran O.K.

Jerry

I have a intel pentium 4 i845 chipset with tnt2 graphics card. Jaunty is working good. I guess I'm lucky that I don't have that bug report. 
I bought that computer 7 years ago. I don't really expect ubuntu to stick with older software versions so that my old computer can run, at the expense of newer computers not taking advantage of new software technologies. Also, people expect compiz to work on 7 year old computers? Wouldn't that severely slow down the old computer? OR does a decent graphics card solve the compiz slowing computer down?

Intrepid would not even boot on that computer (errors would constantly show up on the screen nonstop and would have to press power button to stop it).

---

### Post by GARoss on 2009-03-03
I'm learning fast that it's never safe!;)
I will freely admit that I am completely new to linux (Ubuntu 8.10 1 month ago) I can only give a very inexperienced opinion.
I'm looking for options other than Windows. My objective is to test one of these & decide on one by the full release later next month. From what I've seen, Ubuntu & Kubuntu are great OS. Other than video editing & perhaps gaming, I see no reason not to switch completely over to one of these. 
In testing, I installed Ubuntu 8.10 to get an opinion if we would even like it. For about 3 weeks it has been & still is, very stable. 
Then, I though, lets give Kubuntu jaunty a look too, even with full knowledge that's it's an alpha release. Installation of Alpha 4 (mid last week) went fairly smooth. By the weekend I had some plasmas working, installed a printer driver & the scanner was working; when suddenly, I see an upgrade is available. Big mistake! Now things are acting weird. Tried to uninstall what I thought might be the problem; bad idea, too. Wound up downloading alpha 5 & reinstalled over a4. All looked good until I updated my Nvidia driver. Made history again! Crash - couldn't even log in. Reinstalled a5 again & selected an older driver (173) this time. I also took some advice I read here not to install an upgrade that removes anything else. Well, I cannot use the debian installer for some reason; probaly due to the Python issue but not sure how to check that.
All in all, it's been fun in an odd-challenging sort of way. My advice would be not to try & do anything too serious until a stable release is out.:D

---

### Post by jp_coll2003 on 2009-03-04
It doesn't bother me if its alpha or beta. The only safe way is too make sure you do regular backups and if it all goes tits up which it does from time to time, just re install and put all you important stuff back on. I have an external hard drive by the way.

---

### Post by Gina on 2009-03-04
I have Jaunty running on my AMD K6-2 450MHz (see sig) which is ten years old :)  It does seem a touch slow when compared to my more recent machines though :lol:

---

