---
title: "Should I really upgrade?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by shmeeter on 2007-04-19
Hi all!  

A few questions, hopefully others are wondering what I am wondering.

**First -** I'm considering upgrading to Feisty.  I *just* installed amd64 Dapper on my laptop, and *just* got pretty much everything working.  Still a few tweaks left, like side buttons on mouse, but getting there.

For wireless, I had to use ndiswrapper to get my Broadcom BCM4318 going.  Is that supported natively, now?

Sound was a pain, especially with Flash.  I had to use nspluginwrapper.  Do ya think that will be more smooth now?  Maybe native or whatever?

I was planning on subscribing to the "if it ain't broke, don't fix it" and "don't mess with a working system" mentalities, but if the benefits are great enough, I might do it.  Do you think I should upgrade?

**Second -** Using the 32-bit version of Feisty was recommended.  Any benefit?  I would prefer to stick with the 64-bit OS.  I can still just install a 32-bit versin of Firefox, right?

**Third -** I guess the right way to do it if I do decide to upgrade is to first upgrade to Edgy.  My upgrade manager doesn't present that option, though.  What do I do, use the CD?  I think I already have one somewhere.  Should I burn a new one in case of fixes, etc?  Or, is it possible to enable the automatic upgrade?  And what is up with ```
sudo apt-get dist-upgrade
``` or whatever.  Will that get me Edgy?  Or does that just bring installed software up to latest version?

Okay, thanks all!
Shmeeter
Gateway 7510gx - AMD 64 3700+
Ubuntu 6.04(.01?) Dapper Drake LTS
Dual boot w/ WinXP 64

---

### Post by tgm4883 on 2007-04-19
What are the reasons your looking to upgrade?  If your looking to upgrade just to have the latest then I wouldn't do it.

If you have most things setup and working, and there is no reason that you NEED feisty, then leave it alone

---

### Post by astronic on 2007-04-19
I agree with tgm4883: 6.06LTS will still have a long time of security support and if everything you need works, don't change it. Version number fetichism and featuritis both are two common enemies of a well-administered system.

If you should still decide to upgrade, please read the corresponding update notes and remember that 1) you can't directly update from 6.06 to 7.04, but have to upgrade to 6.10 first and 2) you should use update-manager instead of apt-get/aptitude.

HTH,
Stefan

---

### Post by shmeeter on 2007-04-20
Hi, thanks for replying.

Now, granted, I am even less likely to install Feisty now than I was before, but you folks may be missing a subtelty of my question.  I know not to just jump into upgrading for upgrading's sake.  What I want to know is whether or not my wireless will be supported 'out of the box,' and whether things like sound with Flash plugin works better, things like that.  Yes, I have a working system, so to speak, but I consider it hacked together.  Should I be happy with what I have, or can Feisty be cleaner?

To answer questions/concerns raised:

tgm4883 - My reasons primarily center around having to use wrappers for primary functions: ndiswrapper and nspluginwrapper to be specific.  This seems inefficient.  I want to know if better native support is available.

astronic - Version number fetichism aside (which, no matter what I say, is impossible to defend against), you brought up a concern of mine: update manager.  I do not see the option to upgrade to Edgy in my update manager.  Is there a repository I have to enable or something?

Anybody else - I would like to ask again my other questions: Any good reason to go 32-bit, and what's the deal with apt-get dist-upgrade?  Really, what's the deal with apt-get?  Is Synaptic just a front end for apt-get?

Thanks again!  I'm just chuggin' along over here...
Shmeeter

---

### Post by John Williams on 2007-04-20
I'd let the current set of kernel bugs settle down a bit. Lots of unable to boot, land in the busybox prompt errors being reported.... This change from hdx to sdx is still not fully resolved, IMHO.

---

### Post by astronic on 2007-04-20
> **shmeeter said:**
> 
astronic - Version number fetichism aside (which, no matter what I say, is impossible to defend against), you brought up a concern of mine: update manager.  I do not see the option to upgrade to Edgy in my update manager.  Is there a repository I have to enable or something?
Please just read the Upgrade-Notes ([https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")), it's all there. Quote: > If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c" 

The -c (or equivalently --check-dist-upgrades) switch instructs Update Manager to look for upgrades. By default, the Ubuntu 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.

HTH,
Stefan

---

### Post by wkulecz on 2007-04-20
If it ain't broke, don't fix it!

Unless 7.04 has something you need and can't get for what you are currently running I say leave well enough alone.

I'm still running: RedHat 6.1 (half a dozen systems) RedHat 8 (a samba server where I back up data) Windows 2000 (XP and Vista are all pain and no gain for what I do) Ubuntu 6.06 (half a dozen systems, chosen for LTS).  All these systems do 100% of what they are required to do and are more reliable than the power company.  I don't see an upside to upgrading any of them.

If you want to play, fine, get a second drive or system and install to it.  I've spare drives that I've tried FC5x64 on (not there yet for me) and a few other distros and various Vista release candidates.

--wally.

Edit:  I do my best to keep up with security patches for any systems connected to the net, but otherwise I leave well enough alone!

---

### Post by astronic on 2007-04-20
> **wkulecz said:**
> If it ain't broke, don't fix it!
While I agree with that...

> I'm still running: RedHat 6.1 (half a dozen systems) RedHat 8 (a samba server where I back up data)
...I would not do that, if those systems are connected to the internet, because no matter how well your old software works, you will definitely want security support for systems used in a potentially hostile environment.

Regards,
Stefan

---

