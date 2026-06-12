---
title: "Trying to upgrade from 5.10 to something recent"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by redaxe90 on 2011-12-11
Howdy folks,

I'm relatively new to working with Linux and managed to install Ubuntu from an old install CD I had, running 5.10. I wanted to upgrade it to something recent, but for some reason it basically tells me to stick it where the sun don't shine.

I've been trying to use the information from the following pages, to get things happening:

[https://help.ubuntu.com/community/EOLUpgrades/Breezy](https://help.ubuntu.com/community/EOLUpgrades/Breezy)
[https://help.ubuntu.com/community/EOLUpgrades/Dapper](https://help.ubuntu.com/community/EOLUpgrades/Dapper)
and [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I also downloaded the most recent version of Ubuntu, i.e. 11.10 and burned it to a CD, meaning to do a clean install, since the machine is basically a trial and error machine, helping me to learn about the OS and it's inner workings.

The problem with the new CD is that the computer doesn't boot from it, it just hangs there, like it's waiting for the CD to start spinning. Yet when I've inserted it after the OS has finished booting up and I've logged into my account, it displays perfectly. I was thinking that maybe I could start the upgrade from within Ubuntu, by finding an executable file somewhere on the CD, but nothing pops up, at least not that I can spot.

So here I am, completely stumped, trying to figure out what the devil I did wrong, if anything. By all means ask for anything you might consider relevant, I'll try my best to work out if I know what's been going on.:confused:

---

### Post by bluexrider on 2011-12-11
you may have to check the boot sequence in the BIOS. Set it to BOOT from cd/dvd

to do this. when first turning on the machine and while watching the screen, at first appearance of writing hit F2, possibly F12 during the boot process. this should take you to the BIOS menus

---

### Post by redaxe90 on 2011-12-11
Already did that. It's set to boot first from floppy, second from CD/DVD and third from HDD. The problem is that at boot time it detects the CD, but hangs before trying to run anything from it.

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> Already did that. It's set to boot first from floppy, second from CD/DVD and third from HDD. The problem is that at boot time it detects the CD, but hangs before trying to run anything from it.

do you have any OS currently installed and working

---

### Post by redaxe90 on 2011-12-11
> **bluexrider said:**
> do you have any OS currently installed and working

Currently I'm working from Ubuntu 5.10, it's not broken that badly I think, at least I can still work OK'ishly, apart from having a long since redundant Firefox to play with.

I don't have a CD/DVD writer in the computer, only an old optical drive with no disk writing capabilities. I used my wife's Win7 laptop to write the 11.10 installation CD, though that should have worked without a hitch.

Note that I used this same DVD drive to install 5.10 a few times over, so it's quite bemusing how it can give me trouble on a more recent distro.

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> Currently I'm working from Ubuntu 5.10, it's not broken that badly I think, at least I can still work OK'ishly, apart from having a long since redundant Firefox to play with.

I don't have a CD/DVD writer in the computer, only an old optical drive with no disk writing capabilities. I used my wife's Win7 laptop to write the 11.10 installation CD, though that should have worked without a hitch.

Note that I used this same DVD drive to install 5.10 a few times over, so it's quite bemusing how it can give me trouble on a more recent distro.
I know not of a way to upgrade from 5.10 to 11.10 via CD/DVD other than to do a fresh install.
using the CD you burnt from your laptop. are you able to boot from it on the laptop?

i want to make sure the CD is actually bootable. you should be able to use the Live session from the CD

---

### Post by redaxe90 on 2011-12-11
> **bluexrider said:**
> I know not of a way to upgrade from 5.10 to 11.10 via CD/DVD other than to do a fresh install.
using the CD you burnt from your laptop. are you able to boot from it on the laptop?

i want to make sure the CD is actually bootable.

I would have thought so, since it was an iso CD I downloaded from the ubuntu website. The name of the file was  _**ubuntu-11.10-desktop-i386.iso**_ and I used the disk image burner that's built into Win7

I must admit that my desktop machine is a dinosaur, so it might be possible that it's too weak to run the distro, but I thought it should be able to at least start up the CD and tell me what's on it from boot

Since the first attempts at upgrading from within failed me completely, I decided to try a fresh install of the latest version, since I don't have anything especially important sitting anywhere on the system disk anyway, but still the damn thing hung on me.

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> I would have thought so, since it was an iso CD I downloaded from the ubuntu website. The name of the file was  _**ubuntu-11.10-desktop-i386.iso**_ and I used the disk image burner that's built into Win7

I must admit that my desktop machine is a dinosaur, so it might be possible that it's too weak to run the distro, but I thought it should be able to at least start up the CD and tell me what's on it from boot

Since the first attempts at upgrading from within failed me completely, I decided to try a fresh install of the latest version, since I don't have anything especially important sitting anywhere on the system disk anyway, but still the damn thing hung on me.
the concern IS if the CD image is bootable or not. it may not be therefore your attempts at booting ANY machine would fail.

does it boot in the laptop

---

### Post by redaxe90 on 2011-12-11
> **bluexrider said:**
> the concern IS if the CD image is bootable or not. it may not be therefore your attempts at booting ANY machine would fail.

does it boot in the laptop

That's the next thing to try I guess. Sometimes those CDs have a way of cheating bootability.
I'll give it a go and report back.

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> That's the next thing to try I guess. Sometimes those CDs have a way of cheating bootability.
I'll give it a go and report back.
ok then, will check back later

---

### Post by redaxe90 on 2011-12-11
Well, it's confirmed, the CD is FUBAR and won't boot on any computer at all. So that means I'm back to square one, unless it's possible to write the contents of the file to a USB pen drive in such a manner that it becomes bootable. Any ideas on how I'd go about that??

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> Well, it's confirmed, the CD is FUBAR and won't boot on any computer at all. So that means I'm back to square one, unless it's possible to write the contents of the file to a USB pen drive in such a manner that it becomes bootable. Any ideas on how I'd go about that??

well, if you downloaded it from a known good source and are using a decent burning software then you shouldn't have any issues. 
so, burning the CD should be done at the lowest possible speed, I prefer ImgBurn but use whatever works for you.

if its an older system I doubt it would support booting from USB however if it does you can do this [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by redaxe90 on 2011-12-11
I'm downloading the latest version of Nero Kwik burner, for the Win laptop. Hopefully that gives me more control over the burning speed of the next CD. I'll report back once I've tested all options from that moment on.
Thanks for the responses so far

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> I'm downloading the latest version of Nero Kwik burner, for the Win laptop. Hopefully that gives me more control over the burning speed of the next CD. I'll report back once I've tested all options from that moment on.
Thanks for the responses so far
no problem. once burned give it a test drive in the laptop before running over to the desktop.

---

### Post by redaxe90 on 2011-12-11
> **bluexrider said:**
> no problem. once burned give it a test drive in the laptop before running over to the desktop.
Well, the Nero Kwik burner didn't have the option to burn images, so I downloaded something else and found out that the slowest cd burning speed the laptop has is 10x, which I used.

The verification worked perfect, but then it didn't work when I tried to boot the laptop with it. I'm going to try booting the test machine and report back once that's finished. I wonder what the hell I'm going to have to do to get this thing to work properly, maybe use another computer to burn. Fortunately my stepson has a computer with a burner, so I could possibly test it there if all else fails.

---

### Post by bluexrider on 2011-12-11
> **redaxe90 said:**
> Well, the Nero Kwik burner didn't have the option to burn images, so I downloaded something else and found out that the slowest cd burning speed the laptop has is 10x, which I used.

The verification worked perfect, but then it didn't work when I tried to boot the laptop with it. I'm going to try booting the test machine and report back once that's finished. I wonder what the hell I'm going to have to do to get this thing to work properly, maybe use another computer to burn. Fortunately my stepson has a computer with a burner, so I could possibly test it there if all else fails.


Here is a web sight that you can get a free burner and instruction on how to burn slower speeds
[http://iso.snoekonline.com/iso.htm](http://iso.snoekonline.com/iso.htm)

---

### Post by redaxe90 on 2011-12-13
Thanks for the pointer, but I found a way around the problem. Since the second CD I burned failed also, I decided to download an older version of Ubuntu, resulting in my downloading the 10.04LTS version and that installed without a hitch, more or less.

Firefox keeps crashing on me, so I had to install first Seamonkey and then following that I got my grubby paws on Google Chrome and am running that now. Next thing on my list of things to do is to learn how to deactivate unnecessary applications from starting up at all. I'll be reading up on loads of things here, I've got a lot to learn.

Thanks for the patience and help

Tomas

---

### Post by oldos2er on 2011-12-13
What are your hardware specs?

---

### Post by bluexrider on 2011-12-13
> **redaxe90 said:**
> Thanks for the pointer, but I found a way around the problem. Since the second CD I burned failed also, I decided to download an older version of Ubuntu, resulting in my downloading the 10.04LTS version and that installed without a hitch, more or less.

Firefox keeps crashing on me, so I had to install first Seamonkey and then following that I got my grubby paws on Google Chrome and am running that now. Next thing on my list of things to do is to learn how to deactivate unnecessary applications from starting up at all. I'll be reading up on loads of things here, I've got a lot to learn.

Thanks for the patience and help

Tomas
at least you are up and running with something

---

### Post by bluexrider on 2011-12-14
OP could you please mark this 

(SOLVED)

---

### Post by redaxe90 on 2011-12-14
> **oldos2er said:**
> What are your hardware specs?

I can't quite remember the complete details, but as far as I can remember, it's old AMD Tbird 1GHz CPU, 512MB RAM and a 64MB Siluro graphics card.

I managed to get 10.04 up and running and then updated to 10.10
I'm actually rather apprehensive about upgrading this one much further, since I've been reading that the 11 family is quite slow on old systems. I reckon I'll make do with what I have now and only upgrade once I've been able to save up the cash to improve on the hardware side of things.:)

---

### Post by redaxe90 on 2011-12-14
> **bluexrider said:**
> at least you are up and running with something

Absolutely, your pointers gave me something to work with and thanks for that. I'll be sure to pop in again when I run into the next wall :)

---

### Post by nothingspecial on 2011-12-14
You'd be better off using [Lubuntu]("http://lubuntu.net/") with thoses specs.

---

### Post by redaxe90 on 2011-12-14
> **nothingspecial said:**
> You'd be better off using [Lubuntu]("http://lubuntu.net/") with thoses specs.

So is it possible to switch over to Lubuntu from Ubuntu, without much fuss?? I'm still trying to get to grips with Linux overall, so for me it all sounds kinda Chinese, no offense intended.

I will switch over if it's possible without having to do a clean install again, since it's way too much hassle for my taste, at least for the time being.

---

### Post by nothingspecial on 2011-12-15
Well, you can either install lxde or install the lubuntu-desktop meta package. Installing lxde will just give you the lxde desktop environment to choose at login. Installing lubuntu-desktop will pull in all the lightweight apps that come bundled with lubuntu.

Personally, I'd start again and have a nice clean lubuntu but I can understand why you wouldn't want to :)

---

### Post by kurt18947 on 2011-12-15
I agree with Lubuntu.  Nice distro for older less powerful machines.

---

### Post by mörgæs on 2011-12-15
> **redaxe90 said:**
> 
I will switch over if it's possible without having to do a clean install again, since it's way too much hassle for my taste, at least for the time being.

At the end of the day a fresh install is far less hassle than modifying and upgrading.

If the CD drive does not burn reliably, you can just burn Lubuntu 11.10 on another computer. After that you will have to use one hour for a fresh install, at the most. Compare that to the number of hours you have used by now.

---

### Post by redaxe90 on 2011-12-15
> **mörgæs said:**
> At the end of the day a fresh install is far less hassle than modifying and upgrading.

If the CD drive does not burn reliably, you can just burn Lubuntu 11.10 on another computer. After that you will have to use one hour for a fresh install, at the most. Compare that to the number of hours you have used by now.

Thanks for reminding me about the frivolous use of time, I feel kinda shamed ;)

Well, seems like it's trying for yet another distro-burn, I'll hopefully avoid messing things up too badly there. But I'll do it after Christmas, too much work and chores around the house until I get some relaxing time from work between holidays.

Again thanks for all the tips guys, I can understand why my friend suggested I pop in here for assistance.:guitar:

---

### Post by mörgæs on 2011-12-15
> **redaxe90 said:**
> Thanks for reminding me about the frivolous use of time, I feel kinda shamed


You shouldn't. It's just called learning :-)

> **redaxe90 said:**
> 
Again thanks for all the tips guys, I can understand why my friend suggested I pop in here for assistance.

You are welcome. Maybe some day soon you are the one answering questions here...

---

### Post by redaxe90 on 2011-12-15
> **mörgæs said:**
> You are welcome. Maybe some day soon you are the one answering questions here...

Well, hopefully I can get to the point of being able to answer the most basic questions, but at the moment I just don't have enough time to dedicate to computers, I just needed a computer to run relatively smoothly and I've come to the point of hating Windows with a vengeance, brought on by Vista and Win7.

Gaman að sjá að Íslendingar eru alls staðar að koma að gagni ;):guitar:

---

### Post by mörgæs on 2011-12-16
Við erum bráðum að stjórna heiminum :-)

---

### Post by redaxe90 on 2011-12-16
:lolflag:
Switching back to English, it's fine to mark this as solved, albeit with a rather p***ed off roundabout method :)

---

### Post by mörgæs on 2011-12-16
Fine, I have done it this time. The switch is in 'Thread tools', if you want to do it yourself next time.

---

