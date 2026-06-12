---
title: "Upgrade from 14.04 to 14.10 no change"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2015-02-18
I clicked as required to start the upgrade process, the progress screen appeared, and the orange progress bar slowly traveled from left to right, then, I was asked to restart to complete the process.  I did so, only to discover that there was no change to my system.  What happened?

Thanks.

Caruso

---

### Post by fantab on 2015-02-18
What do you mean "there was no change to my system'?

Post the output of:
```
lsb_release -a
```

and

```
cat /etc/apt/sources.list
```

---

### Post by ajgreeny on 2015-02-18
The look will be just about identical for 14.04 and 14.10, so if you are using the same configuration for the DE it will probably not tell you that the underlying OS has changed.

---

### Post by Bucky Ball on 2015-02-18
Possibly what you've achieved is moving from an LTS release which is supported until April 2019 to an interim release that has about six months support remaining before you need to upgrade to 15.04. If you have a good reason to do this, then great. If not, well ... ;)

As has been mentioned, for all intents and purposes, 14.04 and 14.10 are not going to look much different.

---

### Post by craig10x on 2015-02-18
When you boot up, it should say ubuntu 14.10 on the log in screen, if it does, you got it! ;)
14.10 doesn't really look any different, it has refinements, a newer kernel (3.16) and newer apps ins some cases...If the upgrade is 100% perfect, then everything carries over perfectly from the old install, all your settings, apps, data, etc...

By the way, if you have any ppas in your software sources, always uncheck them before doing an upgrade, and then re-check them after the upgrade (although the upgrader will turn them off automatically so if you didn't, check to see if they are off)...

Open the terminal, and type: uname -r   does it respond that you are running a 3.16 kernel?  If you are...you are on 14.10...
Some prefer to go LTS to LTS every 2 years, others prefer upgrading to each new 6 month version, to have the latest stuff...i am in the latter category, and have been getting perfect upgrades every time, so it's not a bad way to go, either...

---

### Post by carusoswi on 2015-02-19
Perhaps I should have explained that I am a long-time user of Ubuntu, since 6.04.  I didn't run the upgrade expecting to be blown away from all the bells and whistles.  Actually, my 14.04 installation had broken recently - installation had been working fine, as most Ubuntu installations do. Then, last weekend, when I booted up, the computer would freeze just after I entered my password.  I posted a question about that here on the forum. 

When several suggestions did not solve the problem, I decided to simply do a reinstall of 14.04, which went smoothly.

Then, while re-installing some of my software, I noticed that 14.10 was out, and decided to upgrade.

The upgrade progressed as I would have expected, but, when I rebooted my machine, the screen continued to show 14.04 LTS.

Running the commands listed by a couple of you in this thread also return 14.04 LTS as the operating system version.

Ubuntu displays the version each time you boot it, and my system is still showing 14.04 LTS.

I really appreciate how simple it was to reinstall 14.04.  The screen displays a very clear message showing which operating systems are installed (in my case, Ubuntu 14.04 and Win7) with clear options to erase 14.04 only (which erases all your 14.04 software and settings) or to erase the entire computer (including 14.04 and Win7).

It used to be necessary for me to open Gparted (or whatever flavor of similar being used), examine partitions, etc.)  This has never really been a problem for me, and I have never accidentally fried whatever Windows installation I was booting at the time, but 14.04's simplistic dialog screen is pretty much foolproof and so much simpler.

At any rate, the re-installation went smoothly, the upgrade did not take for whatever reason.

I am curious why.

I may try another upgrade this weekend.  I'm in no rush at this point.

Thank you for your replies in an effort to answer my question.

If anyone has further thoughts, please share them.

Respectfully,

Caruso

---

### Post by deadflowr on 2015-02-19
During the upgrade, did you never get the remove old packages screen at the end?
(or did you just skip the mundane)
Curious as well...

---

### Post by carusoswi on 2015-02-19
I confess that, after I started the upgrade and it got going, I walked away from the machine.
Came back some time later to a message on the screen inviting me to restart now.
I figure that should have done it.
What do you think.
Thanks.
Caruso

---

### Post by deadflowr on 2015-02-19
Hmm, seems odd.
I've always gotten the clean up screen at the end.
Regardless of how long it sits awaiting me...

Did you perhaps only run an update and not a release upgrade.
The release upgrade runs through a couple screen before it starts.
First is a small window that should have stated stuff like:
> Preparing Upgrade
Setting up new software channels
Getting new packages
Installing the upgrades
Cleaning Up
Restarting the computer

Then you would get a window with a Details button dropdown, and information up top about the size of the upgrade and how long it calculates the update the take to download the new packages.
Then you would click on the Upgrade button on this page to actually begin the upgrade.

Did you see any of this?

---

### Post by grahammechanical on 2015-02-19
I have noticed when testing upgrades, that sometimes user interaction is needed. We may need to confirm this and that. My guess is the absence of user in put eventually caused the upgrade to stop. 

Regards.

---

### Post by deadflowr on 2015-02-19
Yep, they do tend to need user input, particularly in regards to replacing a configuration file or two.
(One of those things you tend to forget about that happen during a release upgrade; Or at least I forgot about them.)

Usually though, it'll simply wait, and wait, and wait.
But it shouldn't finish as those configuration files need to be in place when the package is getting it's turn in the upgrade dance, as it were. And since the system has decided that those packages need to be dealt with, it doesn't simply move on to another package. It'll just pause.

---

### Post by craig10x on 2015-02-20
When doing an upgrade i do occasionally check to make sure everything is moving along ok...and at the very end, there is one interaction that is needed. It asks if you want to remove obsolete files...i hit the yes box, and then it cleans things up and then the window comes up to ask you to restart...if he didn't do that at the end, then perhaps that is what messed up the upgrade...And i have been getting 100% perfect upgrades every time.
Also, make sure any ppas you have in your software sources (ex: google chrome updater) are unchecked prior to starting the upgrade (re-check after new system is installed)...

---

### Post by carusoswi on 2015-02-21
Well, I posted the question out of curiosity, but my curiosity has been trumped by my need to move on, so I re installed 14.04 from scratch and will upgrade at some other time (or download 14.10 and install it from scratch).
I have almost always upgraded when moving from one version to the next, and, since 6.04 have never experienced this system.  I did have some PPA's active, but would expect the install process to complain about them, not just gloss over and run/complete the upgrade process with no effect.
I may have come back to respond to the clean-up old files thing.  I don't remember, but I probably did.  I've upgraded so many times over the years that I just wasn't into watching the whole process (didn't watch my reinstall, either, it just happened - responded whenever interaction was necessary)
Thanks for the replies.
Caruso

---

### Post by ajgreeny on 2015-02-22
I would certainly forget about 14.10 for now as it has only two more months of support so is hardly worth the palaver of upgrading the OS.

Better to wait for 15.04 and clean install , or my preferred option; stay with 14.04 which is superb and stable, unless, of course, you have some problems with hardware in 14.04 that will be overcome in a newer version.

---

### Post by carusoswi on 2015-02-23
> **ajgreeny said:**
> I would certainly forget about 14.10 for now as it has only two more months of support so is hardly worth the palaver of upgrading the OS.

Better to wait for 15.04 and clean install , or my preferred option; stay with 14.04 which is superb and stable, unless, of course, you have some problems with hardware in 14.04 that will be overcome in a newer version.

Well, tried the upgrade again yesterday and all went smoothly (I watched this time, LOL).  The sad part is that, for me, it represents no improvement over 14.04, so I rolled back to that version and will keep it until 15.04 LTS is out.

I have some windows aps that I always try to run in Ubuntu, and, for whatever reason, they ran (or ran better) for me in 14.04.

I need these aps, but life does not end for me if they do not run in Ubuntu as I dual boot Win7.  I just prefer to do everything in Ubuntu if possible.

I thank everyone for the replies.

Caruso

---

### Post by Bucky Ball on 2015-02-23
> **carusoswi said:**
> ... I rolled back to that version and will keep it until 15.04 LTS is out.



There is no 15.04 LTS. 15.04 is not a long-term support release. They come every two years, so you're looking at 16.04 LTS. 14.04 LTS is supported until April 2019, though, so up to you when you want to upgrade. LTS releases upgrade to the next LTS release, by the way, leapfrogging the interim releases in between (14.04>16.04, leapfrogging 14.10, 15.04, 15.10). ;)

---

