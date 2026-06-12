---
title: "Heads up: Last HAL update makes system hang at boot"
date: 2009-05-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by afv on 2009-05-11
"Screenshot":

[[IMG]http://img122.imageshack.us/img122/6461/dsc05582.th.jpg[/IMG]]("http://img122.imageshack.us/img122/6461/dsc05582.jpg")

Anyone with the same problem?

---

### Post by super.rad on 2009-05-11
Just had the update, can't eject my cd drive at the moment so won't try restarting

---

### Post by alffjeld2 on 2009-05-11
did the update, not able to boot now, have made a bugreport: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/374921](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/374921)

---

### Post by plun on 2009-05-11
a new HAL is uploaded...

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000986.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000986.html)

"Ubuntu Installer" throw in a [bunch of packages]("https://lists.ubuntu.com/archives/karmic-changes/2009-May/thread.html") so it maybe takes time time to [compile and distribute]("https://launchpad.net/ubuntu/+builds")  ?


a possible chroot situation if a user is trapped.

---

### Post by alffjeld2 on 2009-05-11
hi mate!
do you have a link, or any tips on howto fix this with chroot?
im quit new to more advanced use, but want to learn some more.

---

### Post by plun on 2009-05-11
> **alffjeld2 said:**
> hi mate!
do you have a link, or any tips on howto fix this with chroot?
im quit new to more advanced use, but want to learn some more.

This is a good start

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Note, "Setting up the chroot"

It can take time until the new Hal package is ready....

---

### Post by alffjeld2 on 2009-05-11
thanks mate!
helsningar från norge!

---

### Post by plun on 2009-05-11
> **alffjeld2 said:**
> thanks mate!
helsningar från norge!

More about howto chroot a complete install

[http://onlyubuntu.blogspot.com/2007/03/how-to-fix-broken-ubuntu-feisty-fawn.html](http://onlyubuntu.blogspot.com/2007/03/how-to-fix-broken-ubuntu-feisty-fawn.html)

feisty >> karmic and so on....

---

### Post by Starks on 2009-05-11
If you absolutely need the binaries now...

[https://launchpad.net/ubuntu/karmic/+source/hal/0.5.12~rc1+git20090510-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/hal/0.5.12~rc1+git20090510-0ubuntu2)

---

### Post by Starks on 2009-05-11
> **Starks said:**
> If you absolutely need the binaries now...

[https://launchpad.net/ubuntu/karmic/+source/hal/0.5.12~rc1+git20090510-0ubuntu2]("https://launchpad.net/ubuntu/karmic/+source/hal/0.5.12%7Erc1+git20090510-0ubuntu2")
And they break hal further...

How wonderful. Hopefully I'll be able to fix this using netroot when the fix comes out.

*Typing from Live USB*

---

### Post by davideotape on 2009-05-11
So, this seems to be the first major breakage of the dev cycle then. :(

---

### Post by philinux on 2009-05-11
I always hang fire updating to see messages like this. Mind you I usually post them too.

Got 2 HD's jaunty on one karmic the other. Think I'll wait while the fix comes out before booting karmic.

Thanks for the heads up.

---

### Post by ghindo on 2009-05-11
> **davideotape said:**
> So, this seems to be the first major breakage of the dev cycle then. :(I believe you mean ":)"

It's *good* to have breakage in the development cycle, so we can avoid it in the final release.

---

### Post by plun on 2009-05-11
We also seems to have bad luck..... a pending build for 64 bits

> [NEEDSBUILD]   	 amd64 build of hal 0.5.12~rc1+git20090510-0ubuntu2 in ubuntu karmic RELEASE
**Pending (4005)** 

I have no idea how this is resolved.....:confused:

---

### Post by davideotape on 2009-05-11
> **ghindo said:**
> I believe you mean ":)"

It's *good* to have breakage in the development cycle, so we can avoid it in the final release.

Very good point, but would you agree that it would be better to not have any breakages at all? :popcorn:

---

### Post by taavikko on 2009-05-11
Not affected here.

just did a reboot, and went through nicely.
May not be related to HAL at all.
There's been quite a few upgades recently...

---

### Post by plun on 2009-05-11
> **taavikko said:**
> Not affected here.

just did a reboot, and went through nicely.
May not be related to HAL at all.
There's been quite a few upgades recently...

I noticed one another guy at Ubuntu+1 IRC with exactly the same trouble.... but maybe here we go...:---)

about chrooting :)

I am unsure about this syntax...
> 
chroot into your feisty drive.

**sudo chroot /media/feisty su**

[http://onlyubuntu.blogspot.com/2007/03/how-to-fix-broken-ubuntu-feisty-fawn.html](http://onlyubuntu.blogspot.com/2007/03/how-to-fix-broken-ubuntu-feisty-fawn.html)



su or su-

as I recalls it su-    :confused:

---

### Post by autocrosser on 2009-05-11
I'm at work right now & I did have the problem about 7am Pacific--booted into my backup Karmic, moved my user files that had not been updated in the last couple of days & I was running again---when I get home I'll post the chroot script I've made--you need to bind several things before you apt-get the chroot---you can just chroot & update, but it will throw lots of errors.....


AH---BREAKAGE!!!!!!!!!!!!!!!!!!!!:guitar:

---

### Post by Starks on 2009-05-11
hal 0.5.12~rc1+git20090510-0ubuntu2 does not fix the issue.

I dpkg'd all of the resulting binaries and tried to restart hal. No dice even after a restart.

(btw, it's times like that this that I'm grateful to have a decent chroot script)

---

### Post by jfernyhough on 2009-05-11
AFAIK, the main things to bind are /proc and /dev - or at least, this works for me. :D

```
$ sudo mount -o bind /proc /media/disk/proc
$ sudo mount -o bind /dev /media/disk/dev
$ sudo chroot /media/disk
```

--edit
Just updated (some devicekit packages... interesting) and got this: >  * Reloading system message bus config...                                       Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
Something tells me it's not a good idea to bind my running dbus to my chroot... :D

---

### Post by Starks on 2009-05-11
I'm pretty stupid for using my laptop, my only machine, as a Karmic+Win7 box. 

But I'm glad that I keep all my important documents and files on my USB keys which also double as Live USB images.

---

### Post by jfernyhough on 2009-05-11
You're not stupid, you're advanced!

:lolflag:

---

### Post by vikrant82 on 2009-05-11
> **Starks said:**
> I'm pretty stupid for using my laptop, my only machine, as a Karmic+Win7 box

Not alone.

I even read the heads up with hal~~ubuntu1. Then suddenly i saw, ubuntu2 version, I assumed this is the fix and upgraded. 

Now will have to be patient to not to restart. :)

But guess what, this is the fun. Who wants a stable OS :P Give us more breakages .. :guitar:

---

### Post by Starks on 2009-05-11
I guess I live for the abuse then.

:3

---

### Post by Kow on 2009-05-11
> **vikrant82 said:**
> Not alone.

I even read the heads up with hal~~ubuntu1. Then suddenly i saw, ubuntu2 version, I assumed this is the fix and upgraded. 

Now will have to be patient to not to restart. :)

But guess what, this is the fun. Who wants a stable OS :P Give us more breakages .. :guitar:

You could just boot a livecd, chroot, then force downgrade to the last working version. [https://launchpad.net/ubuntu/+source/hal/0.5.12~rc1+git20090406.46dc48-2ubuntu3](https://launchpad.net/ubuntu/+source/hal/0.5.12~rc1+git20090406.46dc48-2ubuntu3)

---

### Post by Starks on 2009-05-11
Downgrading the packages didn't help.

---

### Post by eTM_ on 2009-05-11
Who needs hal anyway :) Steps to become operational in karmic again:

1) Boot in recovery mode
2) gdm and hal no longer automatic starting (e.g. through rcconf tool)
3) apt-get install xserver-xorg-input-keyboard
4) apt-get install xserver-xorg-input-mouse
5) reactivate your xorg.conf from years ago
6) Add to xorg.conf:

Section "ServerFlags"
  Option      "AutoAddDevices"    "false"
EndSection

7) /etc/init.d/gdm start
8) :cool:

---

### Post by Starks on 2009-05-11
From IRC:

<ion_> Install libdbus-1-3 from jaunty to get a working system while waiting for the fix.


[http://packages.ubuntu.com/jaunty/libdbus-1-3](http://packages.ubuntu.com/jaunty/libdbus-1-3)

---

### Post by vikrant82 on 2009-05-11
> **Kow said:**
> You could just boot a livecd, chroot, then force downgrade to the last working version. [https://launchpad.net/ubuntu/+source/hal/0.5.12~rc1+git20090406.46dc48-2ubuntu3](https://launchpad.net/ubuntu/+source/hal/0.5.12~rc1+git20090406.46dc48-2ubuntu3)

Why boot with live cd, when I have still not restarted... I tried downgrading already (the 5 hal packages.. ) still hal cannot start happily ..

---

### Post by vikrant82 on 2009-05-11
> **Starks said:**
> From IRC:

<ion_> Install libdbus-1-3 from jaunty to get a working system while waiting for the fix.


[http://packages.ubuntu.com/jaunty/libdbus-1-3](http://packages.ubuntu.com/jaunty/libdbus-1-3)

Thanks, starks that worked.

---

### Post by 3vi1 on 2009-05-11
> **Starks said:**
> From IRC:

<ion_> Install libdbus-1-3 from jaunty to get a working system while waiting for the fix.


[http://packages.ubuntu.com/jaunty/libdbus-1-3](http://packages.ubuntu.com/jaunty/libdbus-1-3)

Many thanks, Starks - worked for me too.

---

### Post by seeker5528 on 2009-05-11
On the down side, kinda annoying.
On the Plus side, I finally had a reason to try the recovery boot option. :P

I didn't narrow it down to a specific package, forced all the dbus and hal packages out and loaded the ones from Jaunty.

Later, Seeker

---

### Post by Sarvatt on 2009-05-11
working fine now as of dbus 1.2.14-2ubuntu5, safe to upgrade back up from the jaunty one :)

---

### Post by Nullack on 2009-05-11
Yep its fixed

---

### Post by ktp on 2009-05-11
> **Sarvatt said:**
> working fine now as of dbus 1.2.14-2ubuntu5, safe to upgrade back up from the jaunty one :)

And the fun stops :)

---

### Post by afv on 2009-05-11
> **Sarvatt said:**
> working fine now as of dbus 1.2.14-2ubuntu5, safe to upgrade back up from the jaunty one :)

Confirmed. 8)


> 
dbus (1.2.14-2ubuntu5) karmic; urgency=low

  * debian/patches/50-timeout-11_tests.patch: Remove the bit about
    .gitignore.  My life would be so much easier if the bzr developers
    were killed in a freak unit testing accident

 -- Scott James Remnant < [email]scott@ubuntu.com[/email]>   Mon, 11 May 2009 23:56:58 +0100


:lol:

---

### Post by autocrosser on 2009-05-11
> **jfernyhough said:**
> AFAIK, the main things to bind are /proc and /dev - or at least, this works for me. :D

```
$ sudo mount -o bind /proc /media/disk/proc
$ sudo mount -o bind /dev /media/disk/dev
$ sudo chroot /media/disk
```--edit
Just updated (some devicekit packages... interesting) and got this: Something tells me it's not a good idea to bind my running dbus to my chroot... :D


Here's the one I've been using---you need to add the cp /etc/resolv.conf to the script----I have all the drives in my system fstab'd to /mnt.....

```
#!/bin/bash
sudo mount --bind /dev /mnt/Karmic/dev
sudo mount --bind /proc /mnt/Karmic/proc
sudo mount --bind /sys /mnt/Karmic/sys
sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolv.conf
sudo chroot /mnt/Karmic su
```

So just sub in your info & you're good to go..............

---

### Post by autocrosser on 2009-05-11
> **ktp said:**
> And the fun stops :)


YA---but it got everyone's attention :P

I just went into my backup Karmic drive & played with my main until a update came thru that was golden :)

---

### Post by ktp on 2009-05-11
> **autocrosser said:**
> YA---but it got everyone's attention :P

I just went into my backup Karmic drive & played with my main until a update came thru that was golden :)

I hope it got everyone's attention :P  This thread was very active.  It is good to see more people are starting to take a dive into early dev builds.

---

### Post by davideotape on 2009-05-12
I've also fixed this problem using recovery mode. Just dropped into shell with networking and did a sudo apt-get upgrade. Bring on the next breakage \\:D/

---

### Post by jerrylamos on 2009-05-12
My karmic is deader than a doorknob.  Twice.  Thanks, hal.

Time to re-install jaunty, replace jaunty with karmic, try update & upgrade, etc.

Dual boot is nice.

Jerry

---

### Post by Nullack on 2009-05-12
it wasnt dead.....you simply could have recovery mode booted to a netroot prompt and grabbed the new binaries. It took me no more than 60seconds to fix.

---

### Post by super.rad on 2009-05-12
I just chrooted from Fedora, did the updates then restarted. All working fine now

---

### Post by davideotape on 2009-05-12
> **Nullack said:**
> it wasnt dead.....you simply could have recovery mode booted to a netroot prompt and grabbed the new binaries. It took me no more than 60seconds to fix.

+1

That's exactly what I did. It was simple and quick. No way near needing a complete re-installation:-s

---

### Post by cl333r on 2009-05-12
I thought HAL is going to be dumped in favor of DeviceKit in Karmic?

---

### Post by Starks on 2009-05-12
> **cl333r said:**
> I thought HAL is going to be dumped in favor of DeviceKit in Karmic?

It's a gradual process.

---

### Post by jerrylamos on 2009-05-12
> **Nullack said:**
> it wasnt dead.....you simply could have recovery mode booted to a netroot prompt and grabbed the new binaries. It took me no more than 60seconds to fix.

Glad it worked for you.  Not for me.  If I'm looking for bugs I like to have a clean install (if possible) at this early stage.

Anyway back up & running.  There's always tomorrow for a new set of update bugs...

Jerry

---

### Post by dagrump on 2009-05-12
Playing with early stuff could be a risk to my health;) had move the machine, then climb up on the corner of a desk & have to use a freaking wire?
I could fall and break a hip!
The risks I take.
Wish they were all that easy.

---

