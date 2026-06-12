---
title: "[SOLVED] bcm43xx: Error: Please help"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by jakupl on 2008-03-15
First of all, I am defenatly no power user, so please help me step by step :KS

I have been running ubuntu for a month now. I have had windows also all the time dual boot.

Recently I kinda messed up my ubuntu, so I thought "why not just reinstall Ubuntu, and use the possibility to erase windows"
and so I did.

I booted on the Live cd. Pressed "Install" and erased windows. I rebooted my computer and to my horror I got a black screen displaying this.



[197.328000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[219.356000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

[241.384000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


I always get it three times, but the numbers between the "[]" are never the same :confused: .

please help me, as I can't afford having no computer right now.
thanks

ps. When installing, I always have to write the parameter "hpet=disable", because I have an ASUS A6Rp computer. But it has probably nothing to do with it.

---

### Post by dicecca112 on 2008-03-15
That just means the firmware for the Broadcom wireless is not installed.  Do you have any issues without wireless or do you want to know how to install your wireless?

---

### Post by jakupl on 2008-03-15
yeah :guitar:

how do I install it when i cant get past that black screen.:confused:

---

### Post by Pumalite on 2008-03-15
You might need to get wired to the Internet during install and configure your wireless later.

---

### Post by jakupl on 2008-03-15
yeah but i am always wired to the internet :confused:

---

### Post by Pumalite on 2008-03-15
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by ctsdownloads2 on 2008-03-15
Seriously, this is nuts. I have have three working Ralink cards (two USB), not this Broadcom nonsense and because my notebook unfortunately came installed with this curse from Microsoft, I too am again (regression anyone?) looking at a nice black screen with the b43-phy0 error.

I really have no interest in using this and would like to know how we are supposed to use our OS with this ongoing roadblock? I want to not have this show-stopping error and instead, simply get booted into my Ubuntu Heron alpha install. I went through this with Gutsy as well, but not to this degree.

We need solutions, not "it's a feature" because trust me, looking at a black screen is most certainly not. :(

How do I bypass this and get onto the Live Heron CD without being forced to move onto another distro?

*Looking into some boot options to see if I can bypass this headache - I sincerely hope this is fixed or better yet, reality is hit and support for this problem chipset is just set to ignore when this goes LTR.*

---

### Post by Pumalite on 2008-03-15
You cannot make a kernel for every hardware in the world.

---

### Post by jakupl on 2008-03-15
hehehe I dont understand your link.

I cant even log on, so where should I write the commands.

all I get is a black screen with the error text.

---

### Post by jakupl on 2008-03-15
```
$ lspci -n | grep '14e4:43'
```

says
```

02:03.0 0280: 14e4:4318 (rev 02)
```

---

### Post by ctsdownloads2 on 2008-03-15
> You cannot make a kernel for every hardware in the world.

True, however other distros magically seem to avoid supporting problem chipsets and allow users to tackle this themselves. I have been using Linux long enough - 2003 - and I love much of what Ubuntu does. 

And obviously, some hardware works, other does not. Yet when I have seen Ubuntu slide down hill with their wish to make broadcom work at the cost of alienating users, something is wrong. Dapper, Edgy, Feisty and Gutsy - all worked when I did some minor tweaking and I managed to get the LiveCD past this totally avoidable error. Not this alpha though, this is going to give Ubuntu a huge black eye as trying to support something that is causing an entirely new problem is just foolish. Dump the support for the problem chipset, let's get things booted for the love of Pete. And I say this considering the sheer number of notebooks using Broadcom these days. I am hardly the only one that is going to be really peeved about this. But hey, let's point at the hardware...that works elsewhere in the Linux universe...hmmm. ;) I feel where you are coming from, but this is a lot like digging a ditch with a spoon. I like to think the community has grown up away from this kind of thinking in 2008. We need to put more effort in the open solutions and less into settling with poor support for really badly supported hardware IMHO.

----

Just for the record, things are looking grim. Tried a few pre-boot options like "acpi=off noacpi", still no hope. Guess I will have to do a full install and see what things look like there. At least from that point, I can blacklist that POS chipset once and for all. ](*,)

---

### Post by Pumalite on 2008-03-15
Install with the Alternate CD. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by ctsdownloads2 on 2008-03-15
> hehehe I dont understand your link.

I cant even log on, so where should I write the commands.

all I get is a black screen with the error text.

I am just going to do a hard drive install, see if that takes. Then blacklist the problem from there if it works. If not, looks like this release will be the same sort of thing I found with Feisty - which is really too bad.... :confused:

---

### Post by ctsdownloads2 on 2008-03-15
Pumalite: Good idea, thanks for that. But I must ask, what are the key differences? More choices during the install: kernel selection, etc?

Thanks! ;)

edit: Actually, I am trying to get an do testing with the Heron alpha, is there an alternate CD for it yet?

---

### Post by jakupl on 2008-03-15
anyone...

---

### Post by Pumalite on 2008-03-15
The Alternate CD is made to avoid hardware/graphics problems that you seem to have.

---

### Post by ctsdownloads2 on 2008-03-15
Looks like this is not news...

[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/188282](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/188282)

And the thing to watch is how important it is to be marked - that will be key as to seeing a real solution to it. Apparently the 64bit version has been fixed, yay for them I guess. :mad:

As suggested previously, going to try the Alternarnate Cd: Daily build of Heron is here: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) 
  

 hardy-alternate-i386.iso 

Giving this  a shot - thanks all.

---

### Post by Pumalite on 2008-03-15
> **ctsdownloads2 said:**
> Looks like this is not news...

[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/188282](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/188282)

And the thing to watch is how important is marked - that will be key as to seeing a real solution to it. Apparently the 64bit version has been fixed, yay for them I guess. :mad:

As suggested previously, going to try the Alternarnate Cd: Daily build of Heron is here: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) 
  

 hardy-alternate-i386.iso 

Giving this  a shot - thanks all.
You comments belong more here:
	 Ubuntu Testimonials & Experiences

---

### Post by ctsdownloads2 on 2008-03-15
> 
You comments belong more here:
Ubuntu Testimonials & Experiences

The opinion portion of the comments, sure. But the bug troubleshooting definitely belongs here as clearly, this is an installation issue. :) I might even give you belonging in the development forums, but certainly not Testimonials & Experiences - it is totally off topic for bug fixing and tracking IMO.

---

### Post by jakupl on 2008-03-15
> **Pumalite said:**
> The Alternate CD is made to avoid hardware/graphics problems that you seem to have.

 me :confused: well maby, but i cant make an alternate while running the live version.

Is there no simple way of avoiding my problem?

When I installed it 1 month ago, I never experienced this problem... very strange.

---

### Post by Pumalite on 2008-03-15
Your bug remark belongs to Hardy Heron Alha5 which is still in development and is not Gutsy.

---

### Post by ctsdownloads on 2008-03-15
> Your bug remark belongs to Hardy Heron Alha5 which is still in development and is not Gutsy.

Umm, no kidding? Yeah, I think I established which release it was early on, thanks. Quote from my first entry here:

> I really have no interest in using this and would like to know how we are supposed to use our OS with this ongoing roadblock? I want to not have this show-stopping error and instead, simply get booted into my Ubuntu Heron alpha install. I went through this with Gutsy as well, but not to this degree.

:)

Regardless, it is an installation issue, using Ubuntu, I fail to see the problem? I even acknowledged that this was an alpha release.

---

### Post by ctsdownloads on 2008-03-15
> me  well maby, but i cant make an alternate while running the live version.

Is there no simple way of avoiding my problem?

When I installed it 1 month ago, I never experienced this problem... very strange.

Yeah, it sucks, but it is not even a Release Candidate yet, so with any luck this will be fixed soon(ish). Short of removing the problem device or using the alternate Cd as suggested to me earlier, not sure what else can be done. Going to try the alternate install myself, will post back with success or failure.

 Again, have you tried to install or just run as LiveCD?

---

### Post by Pumalite on 2008-03-15
> **jakupl said:**
> me :confused: well maby, but i cant make an alternate while running the live version.

Is there no simple way of avoiding my problem?

When I installed it 1 month ago, I never experienced this problem... very strange.
You might want to try some boot parameters. Here is a guide and a collection of them to be tried alone or in combination:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
Start with the most common:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791
I'd clean the lens in the burner, just in case.

---

### Post by ctsdownloads on 2008-03-15
Doh!! 

> pnpbios=off

Thanks, this is exactly what I was trying to find before. Was doing most of them from memory to no avail, but this is the one the creator of Knoppix was always raving on about, especially with older kernels - thanks! ;)

*Edit: still no love, looks like I will need to wait for the alternate daily Heron CD to finish downloading - hope it works...*

---

### Post by ctsdownloads on 2008-03-15
Well, this may be it here for boot parameters.

> module_name.blacklist=yes

So I am speculating that I would blacklist bcm43xx specifically in this instance of the b43-phy0 error?

Referenced from:

[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)

*Edit: No good, even though it should have passed through on the install despite being unknown as boot parameters, it failed as well. Wee! *

---

### Post by jakupl on 2008-03-15
Thanks for your help. It must have simply been the cd lens or somthing... well, I just reinstalled ubuntu and it worked perfectly \\:D/:-\":-({|= Over and out ;)

---

### Post by Pumalite on 2008-03-15
You are welcome. Good luck.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

