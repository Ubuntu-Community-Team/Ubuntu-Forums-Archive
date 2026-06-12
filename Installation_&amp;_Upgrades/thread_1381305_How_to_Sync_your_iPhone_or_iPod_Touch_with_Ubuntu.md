---
title: "How to: Sync your iPhone or iPod Touch with Ubuntu"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by foxmajik on 2010-01-14
This article describes briefly how to get your iPod Touch or iPhone to sync in Ubuntu.

After getting tired of booting up Windows in VirtualBox and waiting for the painfully slow iTunes to sync my iPod Touch, I decided to do some research to see if there had been any headway made in getting iPod Touch to sync with Ubuntu.  The good news is, it now works with just a few commands!  No compiling things, downloading things, etc. and only minimal configuration is needed.

This article assumes you're using Karmic Koala.

First, add the PPA that has the versions of the software we need to make syncing work:
```
sudo add-apt-repository ppa:pmcenery/ppa
```
Next, install the software:
```
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common gvfs-fuse libgvfscommon0 IFUs libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libiphone-utils python-libiphone0 iphone libplist++1 libplist-utils python-plist libplist + +1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
```
Add yourself to the Fuse user group:
```
$ Sudo adduser $ USER fuse
```
Now edit Fuse's configuration file to allow all users to mount/unmount Fuse filesystems:
```
sudo nano --nowrap /etc/fuse.conf
```
Uncomment the line user_allow_other by removing the pound sign, then save the file.

Now reboot. After rebooting and logging in, when you plug in your iPod you should be asked what you want to do with it just like any other MP3 player.

---

### Post by blur xc on 2010-01-14
Just a question- Is this just for syncing music?  Or can you also back up your iphone contacts, apps, and personal junk on the iphone as well?  I was under the impression you needed iTunes for that...

Thanks,
BM

---

### Post by foxmajik on 2010-01-14
I only use it for music so YMMV.  I can't imagine what else you'd use a music player for.  ;-)

---

### Post by blur xc on 2010-01-14
> **foxmajik said:**
> I only use it for music so YMMV.  I can't imagine what else you'd use a music player for.  ;-)

Well... I spend a lot more times playing games on the iPhone than I do listening to music.  In all actuality, I don't even have any music on the iPhone...  I use it to make calls, browse the web, check emails, text, take pics, shoot video...  it does abit more than just play music.  I don't have an ipod touch, but I understand it's pretty much an iphone w/o the phone part...  Have you been to the app store?  Don't they all work on the ipod touch too 
(except ones that need the phone part)?  A lot of news sites describe the ipod touch as a hand held gaming system.

Not to mention, if I drop my iphone in the toilet and brick the thing, I can just plug the new one into itunes and restore everything to where it was when I did the last backup.  All I'm out is the $200 or whatever for the new phone...

When you can do that in linux, then I'll be happy...

BM

---

### Post by partsdale on 2010-01-14
I also use my iPhone for more than just music. Does this solution assume a jailbroken phone? And do we know if the contacts, calendars and all actually do sync, or if it's just the music?

---

### Post by foxmajik on 2010-01-14
Then this tutorial is not for you.  ;)

---

### Post by foxmajik on 2010-01-14
> **blur xc said:**
> Well... I spend a lot more times playing games on the iPhone than I do listening to music.  In all actuality, I don't even have any music on the iPhone...  I use it to make calls, browse the web, check emails, text, take pics, shoot video...  it does abit more than just play music.  I don't have an ipod touch, but I understand it's pretty much an iphone w/o the phone part...  Have you been to the app store?  Don't they all work on the ipod touch too 
(except ones that need the phone part)?  A lot of news sites describe the ipod touch as a hand held gaming system.

Not to mention, if I drop my iphone in the toilet and brick the thing, I can just plug the new one into itunes and restore everything to where it was when I did the last backup.  All I'm out is the $200 or whatever for the new phone...

When you can do that in linux, then I'll be happy...

BM

Then this tutorial is not for you.  ;-)

In fact maybe this forum is not for you.  It is all about a Linux.  If Linux makes you unhappy, maybe you would like to visit a forum for a different operating system.

I have used the app store.  It is pretty nice.  However you can use it on the iDevice without the need for iTunes.

Also, I rather prefer Rock for apps, which lets me use the applications I choose without having a filter against apps that duplicate functionality, or do not meet with the expectations of Apple's other terms of use.

This post is for people who need help with managing music on their iDevice.  It is not intended to spark a flame war.  If it is not useful to you, it is time to move on.

---

### Post by foxmajik on 2010-01-14
> **partsdale said:**
> I also use my iPhone for more than just music. Does this solution assume a jailbroken phone? And do we know if the contacts, calendars and all actually do sync, or if it's just the music?

It is not needed to jailbreak your device to manage music with these packages.

---

### Post by blur xc on 2010-01-14
> **foxmajik said:**
> Then this tutorial is not for you.  ;-)

In fact maybe this forum is not for you.  It is all about a Linux.  If Linux makes you unhappy, maybe you would like to visit a forum for a different operating system.

I have used the app store.  It is pretty nice.  However you can use it on the iDevice without the need for iTunes.

Also, I rather prefer Rock for apps, which lets me use the applications I choose without having a filter against apps that duplicate functionality, or do not meet with the expectations of Apple's other terms of use.

This post is for people who need help with managing music on their iDevice.  It is not intended to spark a flame war.  If it is not useful to you, it is time to move on.

Now you are jumping to conclusions-  Your post is titled "**How to: Sync your iPhone or iPod Touch with Ubuntu"**and there's no mention in your original post that this only applies to music.  I was asking for clarification.  Then you smugly (maybe even with a touch of arrogance) asked what else would I use a music player for, and I answered you.

And as a matter of fact, you might be surprised at this- so make sure you are sitting down (and if you are at your computer, chances are you are sitting down...), some people have had thier iPhones LONGER than they've been with Linux, or even known about Linux, or even that FOSS exists!  Holy Crap!  Imagine that!  

And no, I'm not ready to ditch my contract w/ AT&T, and throw away my monetary investment in the iPhone while it's still in good working order for an Android phone, none of which are really all that the iPhone is yet anyway, but that's a topic for another thread.  They are getting close, and maybe by the time our iPhone is old and worn out, there'll be a suitable Android replacement available.  But 'til then, I'll make due with I have, and for now that means dual booting or running itunes in a windows vm.

Thanks for the how-to anyway.  

And I like this forum, Linux, and FOSS very much, thank you...

BM

---

### Post by cyper on 2010-05-07
There also a method to backup and restore iPhone in Ubuntu. I never had to do that to my device thus I'm not sure about flawlessness of that process.
```
man idevicebackup
```
or
```
idevicebackup --help
```

---

### Post by collectperth on 2010-07-04
foxmajik is right guys,  and i might add iphone with ubuntu was a bit of a wait for us, jailbroken smailbroken !!! leave the phone alone if you don't want your security breached ie russian hackers,  be thankful you can afford one. ubuntu is free!! you cant have it all

---

### Post by DrJohn999 on 2010-07-05
VirtualBox 3.2.6 has vastly improved the graphics driver speed for me using WinXP Pro SP3, dual processors, I/O APIC, PAE/NX, VtX-AMD-V, Nested Paging, 64 mB display w/ 3D and 2D accelerations, and PIIX4 IDE HD controller.

Now iTunes 9 syncs my iPhone at something like a decent speed, about 1 minute on average if I'm not downloading something new.

---

### Post by charlesvr on 2011-04-20
Tried. I used by ipod touch, created a backup folder and followed instructions. It ended with my terminal telling me that the ipod refused to be backed up....oh....

---

### Post by foxmajik on 2011-04-20
> This article assumes you're using Karmic Koala.

---

