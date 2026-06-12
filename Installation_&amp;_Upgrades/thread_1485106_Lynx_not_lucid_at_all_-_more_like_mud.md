---
title: "Lynx not lucid at all - more like mud"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by tiggsy on 2010-05-16
OK. I unexpectedly got "upgraded" to lucid lynx just now. And i've rebooted since, but the problems are still there.

First thing: when you start up you get "An error occurred while mounting /proc/bus/usb" and you have to hit S for the boot to continue

Second thing: the workplace switcher has gone down to 1 workplace, and although I can get multiple columns, i cant get the rows... why no rows requested? makes no sense

Third thing: all windows open on top of each other and the top bar which contains the minimize button is missing, so you're stuck with them where they are - AND you can't pick them up to move them.

Fourth thing: the windows don't have tabs in the status bar, so you can't move them to another workspace.

Fifth thing: the version of firefox that came with it doesn't work with tab kit, which is pretty much essential

PLEASE someone tell me how to fix all this stuff (well, probably not 5, that's just a wait thing, i guess)

What a terrible upgrade.

---

### Post by mistichu on 2010-05-16
If you dont mind i would just do i fresh install of ubuntu 9.10 or 10.04 are you using any usb devices on your computer ? ie mouse or keyboard? just backup what you absolutely have to have and fresh install btw i think you may have hit the wrong button in update manager i did that once and had the magical upgrade to 10.04 with a working mouse but no keyboard as you can imagine its pretty hard to login but that was with my desky with usb keyboard and ps/2 mouse lol and for the firefox thing just update firefox then open firefox and go to addons and hit find updates (which finds update for the addons XD)
 
are you using a custom motherboard ?
or a offbrand motherboard cause that might cause the proc/bus/usb error which means that your usb device should work?

---

### Post by coffee412 on 2010-05-16
Had the exact same problem on a box. Did a different box before that and it ran fine. What I forgot to do was to do a complete UPDATE (apt-get update) before the upgrade. I figure thats what did it.

Did you do an update/reboot before the Upgrade?

Reinstall I hate to say.


coffee

---

### Post by tiggsy on 2010-05-16
I'm not sure how to do a reinstall of Lynx - and a lot of stuff just isn't working. For example, I tried to use terminal, but that won't work at all, so i can't edit the file to take out the line about /proc.... It opens, but it doesn't accept keyboard input. As you can probably tell, my keyboard is working fine - and so is my mouse. This i guess is a bonus.

Right now i'm working in firefox and I have 2 windows overlapping. Luckily the top ine is quite small, being a BBC iPlayer Console (I was listening to the radio earlier), but it is covering the File... etc menus at the top and there seems no way to get it to go away. 

I think I'll just revert to Karmic, as I have a disk for that. And it worked before. Oh god I hope it will work after a reinstall.

In answer to people's question, I didn't even realize I was doing an upgrade, I thought it was the regular daily updates. So, i think all the normal updates had been done, but cant be sure.

And I just went with the default answer for all the upgrade questions, so I would assume that it SHOULD be working ok. Grrrr

---

### Post by kansasnoob on 2010-05-16
> **tiggsy said:**
> OK. I unexpectedly got "upgraded" to lucid lynx just now. And i've rebooted since, but the problems are still there.

First thing: when you start up you get "An error occurred while mounting /proc/bus/usb" and you have to hit S for the boot to continue

Second thing: the workplace switcher has gone down to 1 workplace, and although I can get multiple columns, i cant get the rows... why no rows requested? makes no sense

Third thing: all windows open on top of each other and the top bar which contains the minimize button is missing, so you're stuck with them where they are - AND you can't pick them up to move them.

Fourth thing: the windows don't have tabs in the status bar, so you can't move them to another workspace.

Fifth thing: the version of firefox that came with it doesn't work with tab kit, which is pretty much essential

PLEASE someone tell me how to fix all this stuff (well, probably not 5, that's just a wait thing, i guess)

What a terrible upgrade.

How do you get "unexpectedly" upgraded?

I've tested upgrades to Lucid from both Karmic and Hardy and there are at least three chances to say NO!

---

### Post by darkod on 2010-05-16
> **tiggsy said:**
> 
In answer to people's question, I didn't even realize I was doing an upgrade, I thought it was the regular daily updates.

I understand your frustration, but at least to my knowledge this can't be true.

The button to UPGRADE to a newer release is completely different and separate in the update manager.
As a matter of fact, in the settings you can disable being given the possibility to upgrade.

You plan to reinstall Karmic back (which would mean you know how to do it) but you say you don't know how to clean install Lucid??? Absolutely the same procedure.

Backup your data, and if going to try a clean install Lucid is a much better choice. One of the reasons being it's LTS. Karmic will stop being supported relatively soon, and then you will have to think about upgrade or clean install anyway. Why not do it now?

Probably your upgrade went wrong so there are lots of hiccups with your system right now as you explained. But clean install is always better than upgrading.

---

### Post by tiggsy on 2010-05-16
The reason i chose the downgrade was because i actually like Karmic. Also I already have a disk, and from what i've read there's some doubt as to whether I'll be able to write a new one for lucid

But anyway.

I just downgraded. Now i'm getting: 
```

mount: mount point /dev/shm does not exist
mountall: mount /dev/shm [313] terminated with status 32
mountall: Filesystem could not be mounted: dev/shm
mount: mount point /dev/shm does not exist
mountall: mount /dev/shm [313] terminated with status 32
mountall: Filesystem could not be mounted: dev/shm
fsck from util-linux-ng 2.16
/init: mountall main process [309] terminated with status 4
/dev/sda1: clean 244902/15073280 files, 46185872/60291937 blocks (check in 3 mounts)
Mount of root filesystem failed
A maintenance shell will now be started

```

a reboot did not fix this

unexpectedly, because I was working on something and didn't read the update box carefully, just clicked to do the upgrade. Then when it was downloading everything I thought I might as well go with it. Wish i hadn't

I can't backup. I have insufficient room. I did buy another disk for this purpose, but a friend's disk failed, so i gave it to him. I can't afford to get another one right now, and anyway, don't have time to wait for it to arrive.

---

### Post by mistichu on 2010-05-16
> **tiggsy said:**
> The reason i chose the downgrade was because i actually like Karmic. Also I already have a disk, and from what i've read there's some doubt as to whether I'll be able to write a new one for lucid
 
But anyway.
 
I just downgraded. Now i'm getting: 
```

mount: mount point /dev/shm does not exist
mountall: mount /dev/shm [313] terminated with status 32
mountall: Filesystem could not be mounted: dev/shm
mount: mount point /dev/shm does not exist
mountall: mount /dev/shm [313] terminated with status 32
mountall: Filesystem could not be mounted: dev/shm
fsck from util-linux-ng 2.16
/init: mountall main process [309] terminated with status 4
/dev/sda1: clean 244902/15073280 files, 46185872/60291937 blocks (check in 3 mounts)
Mount of root filesystem failed
A maintenance shell will now be started

```
 
a reboot did not fix this
 
unexpectedly, because I was working on something and didn't read the update box carefully, just clicked to do the upgrade. Then when it was downloading everything I thought I might as well go with it. Wish i hadn't
 
I can't backup. I have insufficient room. I did buy another disk for this purpose, but a friend's disk failed, so i gave it to him. I can't afford to get another one right now, and anyway, don't have time to wait for it to arrive.
have you tried a fresh install ?

---

### Post by tiggsy on 2010-05-16
Right. I just did the nearest I can do to a fresh install, as I cannot backup.

The result seems to be pretty much the same as before. 

 Still no pickupable bar, and windows still get stuck where they are. I did manage to get round the problem with the extra window on firefox by using Alt-F which closed the main one, then closing the second one through System Monitor. On reboot, I got a window where I could deselect the second window, so that's ok. But

 I still don't get offered rows on the workplace switcher, so I can only have a long line, which is awkward to use, as I have the switcher in the right hand panel for ease of use.

In addition, I now have a lot of stuff in my top panel which are just black squares, and firefox is one of those. But i guess these may repair themselves. I've noticed this on previous upgrades.

But why are there no longer any convenient for switching tabs in the bottom bar (status bar?) and why is there no way to move windows? What kind of fools designed this version anyway?

---

### Post by ed-koala on 2010-05-16
If you have an install CD of any version, use that to wipe your partition clean and then reinstall fresh. That'll fix things.

---

### Post by tiggsy on 2010-05-16
i have some 220gb of data on that drive. wiping it is not an option. even backing it up is not an option

---

### Post by warpasylum on 2010-05-16
I second reinstalling.  It sounds like your install is hosed.  I keep all my files on an external hard drive so that I don't lose anything if I have to reinstall or accidentally break my system.  I'd honestly have to say you're best off reinstalling though.

---

### Post by ed-koala on 2010-05-16
How much free space do you have on your hard drive(s)?  If you can squeeze out 220g of space (I know, prob not) you can save the data to its own partition and do a reinstall.

If you really want to go the hard route, use what space you DO have, save part of your data to freed space in a separate partition. Delete partial saved stuff from main install, free up more space, repeat.

---

### Post by tiggsy on 2010-05-16
Ubuntu has obviously been chasing Windows far too slavishly - There is NO NEED to issue buggy stuff, just because Microsoft does.

I should have stayed with Hardy. That was reliable.

As it stands it looks as if I'm going to have to mothball this computer AGAIN while I get another disk to backup to (or maybe just install the system on, and use the existing disks as pure data). This is so annoying, I already lost some 4 months use of this computer due to a main board crash - and the fact that so far as installing new motherboards is concerned I'm obviously no good (and I had to wait for my daughter to visit and do it for me after my attempt failed to work completely).

I just got all the data back sorted on this computer, now I have to do the same on the old and sad thing I am reduced to using while I get the cash together to buy another disk. I used to think Ubuntu was great, but with every upgrade it seems to get less and less reliable.

---

### Post by jvector on 2010-05-16
Sorry, I am late into this thread. I had troubles doing an (intentional) upgrade from 9.10 to 10.04 similar to what you first reported, and the same symptoms (all windows in the same place, no decoration controls (i.e. minimize etc.). It all sounds very like an issue with a particular graphics card on your PC (Intel 85852) - try saying 

lspci | grep VGA

if you see that name (Intel 85852) then the info in this link 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
could help. It is not the simplest page to understand, but basically it involves interrupting your boot-up by hitting 'e' at the time the boot manager offers you a list of systems to boot and adding some text to the boot command lines; and you can, if that works, make it a permanent fix so you do not have to do that every time.

I realise you have reverted to 9.10 bit *if you still have* your 10.04 as a boot option that might help get you further.

I wish you luck :)

---

### Post by wfajber on 2010-05-17
For what it's worth, I get the same error message. I had the problem when I first installed (Karmic -> Lucid via upgrade), so I started fresh with a CD install. 

Just this last hour I get that message so I am guessing something appears changed in the hardware. I had an ipod plugged in at one point and now it isn't. I also had a disc in one of the dvd drives... Beats me right now, which of course why I am looking in the forums.

However the very fast start must do some guessing/preloading/compiling of the load sequence to make it go so smoothly, so perhaps there is a way to reset that.

However even now once I get past the inconvenient "Press S to Skip" message, it works fine, so I am not too worried for myself.

---

### Post by wfajber on 2010-05-17
I found this change fixed the error message for me. See:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1468486](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1468486)

Good luck!

---

### Post by tiggsy on 2010-05-17
Well, i did a fresh install and the error message (which was not really that important anyway) went away. So did all the other problems.

Now I got to spend a few hours or days getting sound working, video working, installing my preferred software, trying to remember all the alarms i lost on kalarm (some of which were important and work related). If only Ubuntu could get its act together and not cause these problems in the first place

---

### Post by tiggsy on 2010-05-17
Thanks to everyone that helped/tried to help.

When I remember how to, I will mark this solved.

---

### Post by vijaym on 2010-05-17
I found that a fresh install is best. 

For ease of use, I created a separate partition for /home. This allows a fresh install and still keeps all your data.

My installations are on 
* a MSI Wind U100 Plus Netbook
* HP x64 laptop
* generic desktop

all work well and are 'clean' installs.

The issue of the loss of minimise buttons and so on are linked to something around compiz.

---

### Post by kafkaian on 2010-05-17
Agr! This is grim. I thought I'd upgrade to an LTS to last me until the next LTS (and computer upgrade) thinking that this might be as reliable as Dapper and save me worrying about upgrading again for a while. What a mistake! I really don't have the energy left to mess around with this anymore. I had already bought a netbook with Windows 7 for some reliability (I never thought I'd say that)and a good job I did.

So! I'm stuck with a boot edit screen and wondering whether to toil with screwdrivers and get an old hard drive installed (to clean install) or to try and struggle with some more time consuming software troubleshooting.

I think I'll take the dog for a walk instead and forget about those important emails I was going to write (address book stuck on now dead system) and that standard letter I needed to get out tomorrow.

As others, I eventually boot up to login screen and get stuck on Desktop after that. Get mouse pointer BUT no icons, taskbar.

Any howto worth reading? Any reason why I shouldn't just jump in the River Rae along with my Lucidly crummy PC?

---

### Post by tiggsy on 2010-05-18
I had to back up, and do a complete clean install - which is fine for me, as I have another computer i can download and burn the image with - but not everyone can do this. And even so, I lost around 48 hours work mucking around trying to get stuff to work, reinstate other stuff and so on, so it's basically a nightmare.

But it did work.

And for information for someone who wanted to know if i was using non-standard kit. I have the graphics card I've always had, i dunno a Radeon or something. It came with the machine, and the motherboard is a slightly worse version of the one that came with the machine as well, I'm afraid. 4 years or so of 14 hours a day wears down the best machine eventually. Plus the cooler over the top of the chipset (north bridge) suddenly decided to detach itself for no reason, so that fried. But none of this has caused any problem with Hardy or Karmic, so unless Lucid is less reliable (as i suspect), it shouldn't be a problem.

---

