---
title: "How to downgrade to Ubuntu 10.04"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by lyuba on 2010-10-16
Hello!

Could you please tell how is it possible to downgrade to the Ubuntu 10.04 from Ubuntu 10.10?

I have two reasons for doing it:
1. My internal microphone stopped working in new kernel (ThinkPad Egde 13')
2. New Ubuntu's look and feel is ugly.
Probably this problem may be solved with installing the theme, but it seems not to affect the font, which is the most terrible thing in new release's design.
Is it possible to have the 10.04's look and feel here in 10.10?

Thank you for your suggestions in advance!

---

### Post by mörgæs on 2010-10-16
There is no option to downgrade. You will need a clean install.

By the way, you shouldn't think of this as stepping 'down'. 10.04 is finally getting stable, so now is the time for switching to this one, not away from it.

---

### Post by soldier1st on 2010-10-17
well thats too bad as i have a Ubuntu user who had 10.04 and everything worked but as soon as she was upgraded to 10.10 from 10.04 a few issues arose like when a screensaver launches after a set time it logs her off yet when she previews them it does not and firefox is partially disabled. she can't right click anywhere in firefox and she is unable to access the bar that holds the file/edit/history/bookmarks/tools/help and before the upgrade all was fine.

---

### Post by Mark Phelps on 2010-10-17
You have my sympathy ... for what it's worth.

Twice every year, we see lots of posts from folks who "upgrade" to the latest Ubuntu version, discover that their PC no longer works properly ... and then come here asking how to downgrade.

A reasonable question ... especially from former (or current) MS Windows folks who DO have the option to do a full OS roll-back shortly after upgrade.

Unfortunately, Canonical STILL has not seen fit to build this into Ubuntu.

And, when I have posed this on these forums, I get soundly thrashed by all the others who claim that folks should (somehow?) just know that they should do a backup BEFORE doing the upgrade -- so they can restore it later.

Personally, I disagree with that point of view. MS Windows has been providing full OS rollback capabilities ever since the early Vista days now.  This should be something that Canonical should be providing.

---

### Post by paulop on 2010-10-17
I also wish to downgrade after discovering that the driver for my nvidia GeForce2 graphics card hasn't yet been upgraded to work with xorg-1.9, so now I'm stuck with a crappy display mode (and it's taken me quite a while just to get to that because I was originally only given a command prompt after the 10.10 upgrade).

But before I rush in headlong and make things worse, I would like to know if doing a fresh install of 10.04 will overwrite specific configurations I had when I first set up Ubuntu. I'm specifically thinking of my NFS mount and my wireless driver (which took ages to get working and has always worked since). I fear that doing a fresh install will take my system back to a "clean" state where everything needs resetting to how I had it before the 10.10 upgrade. If that's the case, I would rather wait a few weeks for the graphics driver to be fixed.

---

### Post by dougalkerr on 2010-10-17
Personally I use Ultimate Edition which is based upon Ubuntu but, does not suffer from some of the glitches that seem to affect Ubuntu, specifically sound and graphics problems to some degree or other.

I believe the developers at the UE web site take Ubuntu and refine it if you like...

I converted to full time UE user just a few months ago and apart from it being a bit slow upon booting (due to the heaps of software that loads) it is as near perfect a Linux distro that I have come across.

I have had no issues with missing codecs like I used to with Ubuntu and other things like the microphone being muted by default in Ubuntu 10.10 is working properly in UE.
The graphic themes installed as standard to be used through Emerald Theme Manager are very nice compared with what you get as standard in Ubuntu and the Splash screens for Logon and Logoff that have recently been finished are more than a match for that other operating system.

Good one TheeMahn! my hat is off toy you...

Also, as the developer states, he will not release a new release distro till all testers are satisfied that everything works.

Version 2.8 is about to be released, based upon Ubuntu 10.10 so lets hope all is well. If it is anything like the other versions based upon all other releases of Ubuntu then it will work better than Ubuntu straight off. Be aware though that because of the graphics demands I have found that you need to have a decent spec of computer to benefit from all the work that has gone into developing this distro.
It is certainly worth trying version 2.7 to see if you like it. It is based upon Ubuntu 10.04 and works really well and there is a dedicated forum too. Good luck with what ever you decide to do but, a clean install is the only way to go. I agree with what the experts say and that is that upgrading is not ideal...

---

### Post by pierrem-m on 2010-10-20
I'd like to add my two cents worth here as well. I've done the upgrade tp 10.10 and now various programs log me out whilst shutting down everything that's open.

And one of the programs in Cisco's Packet Tracer which I really need for my CCNA Course! Fortunately I have Win2K PC that I can run Packet Tracer on but this is hardly ideal! Another program triggering this most annoying behaviour is Google Earth!

A full system rollback should be a mandatory feature!!!

After all, if Microsoft can do it why can't Canonical?

---

### Post by mörgæs on 2010-10-20
In many cases the problem is not 10.10 itself but the fact that people did an online upgrade. If there are problems that can not be solved, a fresh install is the first to try.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by STOIE on 2010-10-20
In response to the no driver for new Xorg.

I had the same issue, rolled back Xorg and got it working again.


1) Enable SSH and make sure it's working (with a static IP on the machine too!!!) *SERIOUSLY DO THIS*

2) Grab the lucid packages from the ubuntu packages site, namely:
* xserver-xorg-core
* xserver-xorg
* xorg
* xserver-xorg-input-all
* xserver-xorg-graphics-all

3) Remove all the xorg packages.
*MANUALLY* remove them.
sudo apt-get remove <pkg>

4) Install new packages.
*MANUALLY* install them.
sudp dpkg -i <pkg>
Make sure u install graphics and inputs LAST

5) Add your driver back into the xorg.conf

6) Reboot, if all goes well it should work.

IF NOT:
You have SSH running as a backup (that almost killed me, luckily I had it enabled!!!)

If it works, have a maz to thank yourself for all the good work! lol :P

---

### Post by utnubuuser on 2010-10-20
My 2 bits...

I just can't seem to say this often enough.  For those checking this thread for roll-back related info, the best solution for "rolling-back" is to make sure that when you do your initial installation, install  WITH A SEPARATE /home PARTITION!!!!

A separate /home partition allows you to easily re-install while retaining files, folders, data, settings, etc, etc.

Isofar as "Canonical should" goes, the only real change that "should" be made by Canonical is to have a separate /home partition as the default installation set-up.  - It's the Debian /way.

---

### Post by utilitytrack on 2010-10-20
> **lyuba said:**
> Hello!

Could you please tell how is it possible to downgrade to the Ubuntu 10.04 from Ubuntu 10.10?


It's very good thought to use more tested and stable versions of Ubuntu.

One way (very simple, applied to all Debian-based distros) is to change contents of [FONT="Courier New"]/etc/apt/sources.list[/FONT] file, and then upgrade whole system to any previous release.

---

### Post by Ozdemon on 2010-10-20
> One way (very simple, applied to all Debian-based distros) is to change contents of [FONT="Courier New"]/etc/apt/sources.list[/FONT] file, and then upgrade whole system to any previous release.

So does this mean if I go through the /etc/apt/sources.list, substitute lucid lynx for every mention of maverick meerkat, then do an update I will be (safely) back to 10.04?

---

### Post by utilitytrack on 2010-10-21
Roughly speak, yes.

---

### Post by mutt850 on 2010-10-23
I have decided that 10.10 is not ready for prime time, since upgrading from 10.04 I have suffered from continuous hangs on boot, when it does boot I have residual menu ghosts on the desktop, slow menus, cannot us my email unless I am connected by wifi any other type of connection and evolution has the "work online" greyed out. There are so many other problems that did not exist in 10.04 I cannot remember them all.   Being new to Ubuntu, started using it last year with ver. 09.04 and have become a fan but 10.10 is acting to much like Windows. I expect more than this from Ubuntu.  Would be nice to have an easy downgrade option.

---

### Post by cgroza on 2010-10-23
Only if you do a fresh install you may say that its ubuntu's fault. But with an online upgrade anything can happen. So try a fresh install.

---

### Post by utilitytrack on 2010-10-23
> **mutt850 said:**
> Would be nice to have an easy downgrade option.

Yes, all Debian-based distros have exactly this option is in contrast to Default OS wich you specified. Such option are entries in [FONT="Courier New"]/etc/apt/sources.list[/FONT] file. How to downgrade I posted above.

---

### Post by freeediver on 2010-10-23
Well I'm sitting here still using 8.04 and debating doing the upgrade to 10.04, it's sitting unchecked on my update list.
What is the current consensus should I press the button or wait a couple more weeks? What issues can I expect when I update to 10.04 now?
Thanks

---

### Post by utilitytrack on 2010-10-24
> **freeediver said:**
> What issues can I expect when I update to 10.04 now?

Look on this forum, and you will find.

---

### Post by freeediver on 2010-10-24
I spent an hour looking yesterday before I posted this, I had located the thread a week ago but can't find it now.
Sometimes you need to know Exactly what to search for.
Is search working properly?

---

### Post by mörgæs on 2010-10-24
There is some kind of search option for the forum, but I hardly use it. Best is to google and add **site:ubuntuforums.org** to the search string.

If you are unsure about 10.04, just boot the live CD and test for your particular hardware. Radeon graphics cards are a main problem, for example.

---

### Post by mörgæs on 2010-10-24
By the way, if you choose to upgrade, you will end with 10.04 running on Grub1, not Grub2 as the case in a clean install. If you want Grub2, this is an upgrade process in itself.

---

### Post by Charlie91 on 2010-10-24
> **utnubuuser said:**
> ...best solution for "rolling-back" is to make sure that when you do your initial installation, install  WITH A SEPARATE /home PARTITION!!!!  A separate /home partition allows you to easily re-install while retaining files, folders, data, settings, etc, etc.  ...the only real change that "should" be made by Canonical is to have a separate /home partition as the default installation set-up.  - It's the Debian /way.

I think this was mentioned in the Ubuntu documentation (creating a separate /home partition), and I applied it.  When Maverick made it impossible to use my computer (I have low RAM which I guess is a big culprit), I just re-installed Lucid easily--all users' files were preserved (of course one should NOT format the partition--box should be unchecked).

Good suggestion to make /home separate, and perhaps have an easy option to revert back to a previous version if something horrible happens.

---

