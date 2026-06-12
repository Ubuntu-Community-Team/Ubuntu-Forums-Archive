---
title: "Update has broken my system"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by matdaimond on 2009-11-24
Hi,

I've been using Ubuntu Karmic amd64 for about a month. It was OK until I applied updates yesterday. I had been successfully updating my system before with that auto-update manager GUI application.

This time though it never boots up after I turned it off.

It passes grub, shows the white logo and then tty1 console appears. It asks for login and password, however it does not receive any text typed in. It just blinks all the time (not only the cursor, but the whole screen).

I have no idea what is going on with it, so I would be grateful for any advice on how can I repair it.


(Damn Canonical or whoever selects the updates, they should at least check if their updates are not destructive).

---

### Post by rmp73 on 2009-11-26
Got EXACTLY the same issue and it's bloody annoying... Help needed fast please?!

---

### Post by dhavalbbhatt on 2009-11-26
You guys aren't helping yourselves here at all. You need to tell the community what updates were applied and where you think the issue may lie.

As far as I know, the only updates that have been causing problems is the new linux kernal - 2.6.31-15. It seems that you need to reinstall your video drivers for the new kernal. I personally don't know how to do that, but you will find a lot of posts in here that can help you do that. My other advice is, if you can't boot into the newer kernal, can you boot into the older one? If so, keep doing that, until you can find a way to fix the newer kernal issue.

---

### Post by Bunnybugs on 2009-11-26
> **matdaimond said:**
> Hi,

I've been using Ubuntu Karmic amd64 for about a month. It was OK until I applied updates yesterday. I had been successfully updating my system before with that auto-update manager GUI application.

This time though it never boots up after I turned it off.

It passes grub, shows the white logo and then tty1 console appears. It asks for login and password, however it does not receive any text typed in. It just blinks all the time (not only the cursor, but the whole screen).

I have no idea what is going on with it, so I would be grateful for any advice on how can I repair it.


(Damn Canonical or whoever selects the updates, they should at least check if their updates are not destructive).

After grub loads, you are able to pick a boot-kernel... (just like Dual Boot) There are some options, you'll probably have 2 linux/ubuntu kernels, and the fitting recoverymode for every kernel. Try to run the recovery-mode for the blabla.1.15 kernel.

After that, reboot. When the system does the same, try to boot the blabla.1.14 kernel. This will boot up the old settings!

EDIT: Try to catch a LiveCD, insert it, and make sure your BIOS has CD/DVD as first boot-device!
If you've loaded the intro screen, pick 'Rescue a Broken System', this will repair your system (Rescue could be Repair, I'm not sure!)

---

### Post by coffeecat on 2009-11-26
posted in error

---

### Post by dhavalbbhatt on 2009-11-26
Here's the launchpad page for the error (assuming it is the kernal issue)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355)

---

### Post by coffeecat on 2009-11-26
> **matdaimond said:**
> Damn Canonical or whoever selects the updates

> **rmp73 said:**
> Got EXACTLY the same issue and it's bloody annoying

Did either of you enable the proposed repository?

---

### Post by rmp73 on 2009-11-26
Thanks for the suggestion.  I will try harder to provide more information in future.  As I'm only a recent convert (this tests my resolve though!) I'm still getting used to Ubuntu and simply don't yet know how to do some of the more technical prompt control steps.

The problem is indeed related to the new linux kernal - 2.6.31-15.  That said, I'm using an i386 build not AMD64. At least as far as I know.

I have just booted the 2.6.31-14-generic kernal and it's worked.  As I'm newish to Ubuntu I was at a bit of a loss on selecting either of the 'recovery' options from that menu as I ended up at a command prompt and besides rebooting was unsure what to do.  Rebooting 2.6.31-15 heralds no success whatsoever.

I'm using a Sony Vaio FZ11Z with a NVidea GeForce 8400M GT graphics card.  I don't want to have to start playing around with Grub or Xscreen settings given they're working fine under 2.6.31.14.  Is it true I should only really 'trust' even-number releases (12,14,16, etc) in future?  Or will there be some kind of upgrade/fix coming for this bug in 2.6.31-15?

Again thanks for your help.  Funny thing is I do enjoy learning about Ubuntu but you do rather expect patches and updates to work once released through the Update Manager.

---

### Post by rmp73 on 2009-11-26
> **coffeecat said:**
> Did either of you enable the proposed repository?

huh??

---

### Post by coffeecat on 2009-11-26
> **rmp73 said:**
> huh??

You're pardoned. :wink:

The reason I asked that is that a lot of new users enable the proposed updates repository thinking that's a good thing (which it isn't - not for new users) and then complain when their system breaks. It's a common reason for 'help, updates broke Ubuntu' type threads. But you clearly haven't enabled proposed - and that's a good thing.

From [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) :

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.If you're curious, have a look around in Synaptic. You'll soon find proposed - but don't enable it! :p

---

### Post by rmp73 on 2009-11-26
> **coffeecat said:**
> You're pardoned. :wink:

The reason I asked that is that a lot of new users enable the proposed updates repository thinking that's a good thing (which it isn't - not for new users) and then complain when their system breaks. It's a common reason for 'help, updates broke Ubuntu' type threads. But you clearly haven't enabled proposed - and that's a good thing.

From [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) :

If you're curious, have a look around in Synaptic. You'll soon find proposed - but don't enable it! :p

I didn't knowingly but may? have done inadvertently.  Can I 'roll back' to 2.6.31-14 or uninstall those elements that are causing me strife?

---

### Post by rmp73 on 2009-11-26
> **rmp73 said:**
> I didn't knowingly but may? have done inadvertently.  Can I 'roll back' to 2.6.31-14 or uninstall those elements that are causing me strife?

I would have only selected the important and recommended updates - now I've visited the URL you suggested...

---

### Post by dhavalbbhatt on 2009-11-26
> **rmp73 said:**
> huh??

What coffeecat is trying to say is - it is the user who chooses to download and install the software in Ubuntu - it is not Canonical that manages your downloads. 

Ubuntu manages software in repositories. There are various kinds of repositories for various kinds of software. you can read all about it here -

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

That being said, there are certain repositories which maintain software that is being tested and should not be downloaded/installed by "regular" users. If you have checked those repositories to be searched while performing an update, then you will be presented the option of installing "untested" software. Even after that, it is you, the user, who permits Ubuntu to update to the latest version of the software.

---

### Post by dhavalbbhatt on 2009-11-26
Got beatean!!

Sorry for the repeat advice!

---

### Post by coffeecat on 2009-11-26
> **dhavalbbhatt said:**
> What coffeecat is trying to say is 

I know, I can be very trying, can't I? :p

Just a fyi for rpm73. The -15 kernel that seems to be causing you grief probably was a regular release from the main repository, so don't worry about removing it just yet. Continue to use the -14 kernel until you find a fix or until a newer updated kernel gets released. Some people are reporting problems with the -15 kernel, but I should imagine this is affecting only a minority otherwise the forums would be awash with threads. The -15 kernel is running just fine here on three different systems. Not that that's much consolation for you but when whatever the issue is that has affected the -15 kernel has been identified, there won't be long to wait for a newer fixed version.

---

### Post by rmp73 on 2009-11-26
> **coffeecat said:**
> I know, I can be very trying, can't I? :p

Just a fyi for rpm73. The -15 kernel that seems to be causing you grief probably was a regular release from the main repository, so don't worry about removing it just yet. Continue to use the -14 kernel until you find a fix or until a newer updated kernel gets released. Some people are reporting problems with the -15 kernel, but I should imagine this is affecting only a minority otherwise the forums would be awash with threads. The -15 kernel is running just fine here on three different systems. Not that that's much consolation for you but when whatever the issue is that has affected the -15 kernel has been identified, there won't be long to wait for a newer fixed version.

Well, I've decided to use Synaptic Package Manager to remove linux-image-2.6.31-15-generic, and its dependant packages (linux-generic, linux-image-generic, linux-headers-2.6.31-15-generic and linux-headers-generic) and selected the equivalent 2.6.31-14 packages for reinstallation (my idea of rolling-back.

I'm going to 'reboot' and see what happens.  If that goes OK, then I'll check back here and then perhaps (depending how brave I feel) might try the update to 2.6.31-15 again and see if it self-heals.

BTW, there was no 'repair' option on my LiveCD indeed it said go into the OS and use a web-browser to look for help.  Anyone have a URL to the 'right' LiveCD image with a repair option on it?

---

### Post by rmp73 on 2009-11-26
Well that bit at least worked... Now the question of staying on 2.6.31-14 or try the update... What say ye' all?

---

### Post by dhavalbbhatt on 2009-11-26
I just downloaded and installed the newer version of the kernal on one of my machines, and it seems to be working! Again, not a big respite to you folks that can't make it work, but as coffeecat says - hang in tight! Sooner or later, there's gonna be a fix for that.

Coffeecat - trying is not a bad thing!

---

### Post by coffeecat on 2009-11-26
> **rmp73 said:**
> Well that bit at least worked... Now the question of staying on 2.6.31-14 or try the update... What say ye' all?

You're doing well, but you're giving yourself unnecessary work. :) You didn't actually need to reinstall the -14 kernel. It was there, unchanged all the time. The grub menu gave you the choice of booting with the -14 or -15 kernel.

If you now apply the update, you'll get the same -15 kernel back that caused you problems before. Trouble is, if you don't install the -15 kernel, you'll keep getting nagged to update it. And if you lock the -14 version (you can lock a version in Synaptic so that it doesn't get updated), you won't get prompted when the fixed -15 version becomes available (or -16 or -17 if that happens).

I'll tell you what I'd do. I'd let it install the -15 kernel and then just keep booting into the -14 kernel until this problem blows over. :wink:

---

### Post by rmp73 on 2009-11-26
> **coffeecat said:**
> You're doing well, but you're giving yourself unnecessary work. :) You didn't actually need to reinstall the -14 kernel. It was there, unchanged all the time. The grub menu gave you the choice of booting with the -14 or -15 kernel.

If you now apply the update, you'll get the same -15 kernel back that caused you problems before. Trouble is, if you don't install the -15 kernel, you'll keep getting nagged to update it. And if you lock the -14 version (you can lock a version in Synaptic so that it doesn't get updated), you won't get prompted when the fixed -15 version becomes available (or -16 or -17 if that happens).

I'll tell you what I'd do. I'd let it install the -15 kernel and then just keep booting into the -14 kernel until this problem blows over. :wink:

Thanks coffeecat.  I chose to refresh the -14 to be sure that package and any dependants were all present and correct before rebooting.  I was aware they were installed.

re: 2.6.31-15... I'd so much rather not have to slow down my boot time by being present and hitting 'ESC' to get the menu up to select 2.6.31-14

Also, I did read somewhere that you should only install even-numbered packages and releases... any truth in that?

---

