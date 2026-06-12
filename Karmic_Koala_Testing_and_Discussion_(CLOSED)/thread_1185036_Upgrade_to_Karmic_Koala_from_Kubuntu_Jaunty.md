---
title: "Upgrade to Karmic Koala from Kubuntu Jaunty"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Naatan on 2009-06-11
Hi, can anyone explain to me how I should upgrade to karmic koala from Kubuntu Jaunty? I tried downloading the cd and adding it to my sources.list, but when I run "do-release-upgrade" it simply says no upgrades were found.

Anyone?

Thanks

Edit:

I'm talking about the Alpha of course.

---

### Post by lindsay7 on 2009-06-11
Hit the alt + F2 keys at the same time.

Then type "update-manager -d" in the terminal without the quotation marks.

At the top of the screen you get, there will be a choice to get the upgrade version.

---

### Post by Naatan on 2009-06-12
Thanks lindsay, that worked!

---

### Post by Ric_NYC on 2009-08-14
Thank you!

---

### Post by slakkie on 2009-08-14
do-release-upgrade -d 

it is not documented in with the application, but i found it on a wiki somewhere a while ago. That's how i upgraded to 9.10

---

### Post by saivin on 2009-08-24
> **slakkie said:**
> do-release-upgrade -d 

it is not documented in with the application, but i found it on a wiki somewhere a while ago. That's how i upgraded to 9.10
Thanks Slakkie.  Am upgrading to karmic now. (Thanks to lindsay7 too, checked the GUI method but reverted to CLI).  

Could you please explain what is '-d'?

---

### Post by taavikko on 2009-08-24
> **saivin said:**
> 
Could you please explain what is '-d'?

If in doubt of options in a command, check out the man/help
```
man command
command --help
```

This particular option is to check for --devel-release (-d)

---

### Post by slakkie on 2009-08-24
> **taavikko said:**
> If in doubt of options in a command, check out the man/help
```
man command
command --help
```

This particular option is to check for --devel-release (-d)

do-release-upgrade doesn't have a man, or a help... Most of the functions however are the same as the regular update-manager.

---

### Post by taavikko on 2009-08-24
> **slakkie said:**
> do-release-upgrade doesn't have a man, or a help... Most of the functions however are the same as the regular update-manager.

Was just referring in general that man/help is useful when finding out the options.

```
tta@dv5:~$ do-release-upgrade --help
Usage: do-release-upgrade [options]

Options:
  -h, --help            show this help message and exit
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Try upgrading to the latest release using the upgrader
                        from $distro-proposed
  -m MODE, --mode=MODE  Run in a special upgrade mode. Currently 'desktop' for
                        regular upgrades of a desktop system and 'server' for
                        server systems are supported.
  -f FRONTEND, --frontend=FRONTEND
                        Run the specified frontend
  -s, --sandbox         Test upgrade with a sandbox aufs overlay
```

---

### Post by saivin on 2009-08-24
taavikko,
thanks for the clarification.  sorry for not doing basic homework.

---

### Post by octoberdan on 2009-09-19
> **slakkie said:**
> do-release-upgrade -d 

it is not documented in with the application, but i found it on a wiki somewhere a while ago. That's how i upgraded to 9.10

Thank you so much! I've been looking for a way to cleanly upgrade Ubuntu  releases from the CLI for quite some time.

---

### Post by octoberdan on 2009-09-19
> **octoberdan said:**
> Thank you so much! I've been looking for a way to cleanly upgrade Ubuntu  releases from the CLI for quite some time.

It stopped at 100% [Working] :-(. I guess it's not 100% working...

---

### Post by Duncan J Murray on 2009-09-20
What is the best way to upgrade from Jaunty to Karmic?

As a recent convert from Windows XP, I found that reinstalling Windows every 6 months kept it from getting slow and unuseable.  Would it not be better to install Karmic (when it arrives of course) by backing up, burning the ISO to a CD, and installing it as a fresh install?

Or does this not matter in linux land?

Many thanks in advance.

Duncan.

PS completely happy with jaunty - I'll only be upgrading because I'll be curious!

---

### Post by kansasnoob on 2009-09-20
> **Duncan J Murray said:**
> What is the best way to upgrade from Jaunty to Karmic?

As a recent convert from Windows XP, I found that reinstalling Windows every 6 months kept it from getting slow and unuseable.  Would it not be better to install Karmic (when it arrives of course) by backing up, burning the ISO to a CD, and installing it as a fresh install?

Or does this not matter in linux land?

Many thanks in advance.

Duncan.

PS completely happy with jaunty - I'll only be upgrading because I'll be curious!

I prefer multi-booting:

[ATTACH]129201[/ATTACH]

In that case I began with:
sda1 = Win XP
sda2 = Extended
sda5 = Jaunty /
sda6 = Jaunty /home
sda7 = Mint Gloria /
sda8 = Mint Gloria /home
sda9 = SWAP

Then I added:
sda3 = Karmic /
sda10 = Karmic /home

I used a primary partition for Karmic / because I plan on dumping Win XP soon and it's best to begin with a primary partition.

The advantages to that are:

1. It's very easy to transfer all of my wanted data (including Firefox and Opera profiles) from either Jaunty or Gloria's /home folders.

2. If Karmic breaks I need only restore GRUB to either Jaunty or Mint and keep on going until I feel like fiddling with Karmic again.

3. If I decide to keep Karmic and dump Jaunty, or vice-versa, no problem - just a bit of repartitioning or I can reformat the correct partitions for my next "experiment".

4. It's fun:)

---

### Post by legolas_w on 2009-10-10
> **lindsay7 said:**
> Hit the alt + F2 keys at the same time.

Then type "update-manager -d" in the terminal without the quotation marks.

At the top of the screen you get, there will be a choice to get the upgrade version.

Does this method upgrade the boot loader as well as gnome and other ubuntu packages?
I read in another forum that some of Karmic packages (new grub) will not install correctly when we upgrade from 9.04 and we must perform a clean install to have them.


Thanks

---

### Post by kansasnoob on 2009-10-10
> **legolas_w said:**
> Does this method upgrade the boot loader as well as gnome and other ubuntu packages?
I read in another forum that some of Karmic packages (new grub) will not install correctly when we upgrade from 9.04 and we must perform a clean install to have them.


Thanks

If you upgrade from A Jaunty install with legacy grub, you'll still have legacy grub after upgrading.

The same is true of the file system. If you upgrade a Jaunty that's formatted ext3, it'll still be ext3 after the upgrade.

---

### Post by legolas_w on 2009-10-10
Thanks for the reply.
Is there anyway to upgrade to the new boot loader as well? I mean without re-installing the OS.


Thanks.

---

### Post by slakkie on 2009-10-10
Yes, you can convert grub legacy to grub2 without reinstalling. 

[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

---

### Post by celticbhoy on 2009-10-10
Getting this trying to upgrade my desktop :-

Done downloading            
Exception during pm.DoInstall():  E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.

Could not install the upgrades 


Any help to get past this.

---

### Post by slakkie on 2009-10-10
celtic, search the forums for this error, have seen it before. Think the solution was to remove openoffice.org-filter-binfilter package and redo the upgrade. But check the forums first to confirm this action.

You should be able to install the openoffice package after the upgrade iirc.

---

### Post by celticbhoy on 2009-10-10
Cheers slakkie, thats got me past the hurdle.

---

