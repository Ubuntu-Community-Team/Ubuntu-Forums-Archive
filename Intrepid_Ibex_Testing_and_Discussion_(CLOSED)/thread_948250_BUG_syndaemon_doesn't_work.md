---
title: "BUG: syndaemon doesn't work"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by biasquez on 2008-10-15
hi, syndaemon doesn't work on intrepid.

---

### Post by wgrant on 2008-10-15
> **biasquez said:**
> hi, syndaemon doesn't work on intrepid.

It works fine here (I wrote much of the XInput properties port).

Are you using amd64, perchance?

---

### Post by biasquez on 2008-10-15
no, intel 32 bit. 
in my Xorg.0.log i have this (**) Option "SHMConfig" "true"

syndaemon works fine sometimes. is it possible to debug it?

---

### Post by wgrant on 2008-10-15
> **biasquez said:**
> no, intel 32 bit. 
in my Xorg.0.log i have this (**) Option "SHMConfig" "true"

syndaemon works fine sometimes. is it possible to debug it?

Try running it with -S; that will force it to use SHMConfig. If that works fine, turn SHMConfig off, try without -S, and see if it's any better.

---

### Post by biasquez on 2008-10-15
with -S works fine but i found problem (i think). in gnome-session i launched syndaemon with an other cmd using operator &&. now i splitted these two  cmd and syndaemon works fine. so,now syndaemon works fine on startup but i see this: if i kill process of syndaemon launched on startup and trying to launch it again in terminal, syndaemon doesn't work.
thanks for your corporation.

---

### Post by wgrant on 2008-10-15
Please try [my new binary](http://people.ubuntuwire.com/~fujitsu/syndaemon).

---

### Post by biasquez on 2008-10-15
i'm using your ppa repo

---

### Post by wgrant on 2008-10-15
> **biasquez said:**
> i'm using your ppa repo

I'm not going to upload that one to my PPA yet. Just grab that binary and run it with './syndaemon whatever args you normally use go here'. Omit the -S, as I want to see how it goes without using SHMConfig.

---

### Post by biasquez on 2008-10-15
it works fine but now old binary works fine too.

---

### Post by _oOMOo_ on 2008-10-15
Hi, how do we proceed now? Use -S for syndaemon? I'm a bit confused.

---

### Post by wgrant on 2008-10-15
> **_oOMOo_ said:**
> Hi, how do we proceed now? Use -S for syndaemon? I'm a bit confused.

Last week I ported syndaemon to use the new XInput device property infrastructure, meaning that one can use syndaemon without having to enable SHMConfig. -S forces syndaemon to use SHMConfig, and I recommend against it.

---

### Post by _oOMOo_ on 2008-10-15
That sounds good. At the moment I have SHMConfig on in xorg.conf, and this line added to my sessions:

```
syndaemon -i 0.7 -d
```

which no longer works. Do I need to alter anything other than simply removing the SHMConfig line in xorg.conf?

Many thanks

---

### Post by wgrant on 2008-10-15
> **_oOMOo_ said:**
> That sounds good. At the moment I have SHMConfig on in xorg.conf, and this line added to my sessions:

```
syndaemon -i 0.7 -d
```

which no longer works. Do I need to alter anything other than simply removing the SHMConfig line in xorg.conf?

Many thanks

What happens if you run it in a terminal? Which architecture are you using?

---

### Post by _oOMOo_ on 2008-10-15
I'm using amd64.

```
$ syndaemon -i 0.7 -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  149 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Cheers

---

### Post by wgrant on 2008-10-15
> **_oOMOo_ said:**
> I'm using amd64.

```
$ syndaemon -i 0.7 -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  149 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Cheers

/me breathes a sigh of relief.

Upgrade libxi6; we finally tracked down this issue and I fixed it about 12 hours ago.

---

### Post by _oOMOo_ on 2008-10-15
> **wgrant said:**
> /me breathes a sigh of relief.

Upgrade libxi6; we finally tracked down this issue and I fixed it about 12 hours ago.

:D splendid. One less reason to edit xorg.conf. Now if you could just add the 2 finger and 3 finger tapping behaviours to the touchpad GUI....:)

---

### Post by wgrant on 2008-10-15
> **_oOMOo_ said:**
> :D splendid. One less reason to edit xorg.conf. Now if you could just add the 2 finger and 3 finger tapping behaviours to the touchpad GUI....:)

Uni prevented that for Intrepid, but it should be there for Jaunty (we're discussing it at UDS).

For now you can use xinput to set them without editing xorg.conf or using SHMConfig.

---

### Post by wgrant on 2008-10-17
Can everyone using syndaemon on Intrepid please grab xserver-xorg-input-synaptics 0.15.2-0ubuntu6~wgrant2 from my PPA and try its new version? We need testing if this is to be fixed in Intrepid.

---

### Post by _oOMOo_ on 2008-10-17
> **wgrant said:**
> Can everyone using syndaemon on Intrepid please grab xserver-xorg-input-synaptics 0.15.2-0ubuntu6~wgrant2 from my PPA and try its new version? We need testing if this is to be fixed in Intrepid.


I have your .deb installed now, and when I try syndaemon I get:

```
:~$ syndaemon -i 0.7 -d
Can't access shared memory area. SHMConfig disabled?
```

SHMConfig is not enabled in xorg.conf

Cheers

---

### Post by wgrant on 2008-10-17
> **_oOMOo_ said:**
> I have your .deb installed now, and when I try syndaemon I get:

```
:~$ syndaemon -i 0.7 -d
Can't access shared memory area. SHMConfig disabled?
```

SHMConfig is not enabled in xorg.conf

Cheers

Which type of touchpad do you have? What is the output when you run 'xinput list-props' on it?

---

### Post by _oOMOo_ on 2008-10-17
> **wgrant said:**
> Which type of touchpad do you have? What is the output when you run 'xinput list-props' on it?

:~$ xinput list-props 4
Device 'SynPS/2 Synaptics TouchPad':
Segmentation fault (core dumped)

That's new - I issued this command the other day and there was no problem/crash

---

### Post by wgrant on 2008-10-17
> **_oOMOo_ said:**
> :~$ xinput list-props 4
Device 'SynPS/2 Synaptics TouchPad':
Segmentation fault (core dumped)

That's new - I issued this command the other day and there was no problem/crash

/me cries.

You are on amd64, aren't you? Has it worked in the last week?

---

### Post by _oOMOo_ on 2008-10-17
Yes the touchpad works fine, in fact syndaemon works if I enable SHMConfig and use the -S flag (I haven't tried that since installing your package though).

I was tinkering with xinput the other day when you mentioned that you can alter parameters on the touchpad using it, which was when I tried the above command....that would have been 2 days ago.

It was definitely prior to the libxi6 update - that arrived a few hours later.

---

### Post by wgrant on 2008-10-17
> **_oOMOo_ said:**
> Yes the touchpad works fine, in fact syndaemon works if I enable SHMConfig and use the -S flag (I haven't tried that since installing your package though).

I was tinkering with xinput the other day when you mentioned that you can alter parameters on the touchpad using it, which was when I tried the above command....that would have been 2 days ago.

It was definitely prior to the libxi6 update - that arrived a few hours later.

OK, I can reproduce the segfault with an amd64 client on an i386 server, but only on the Synaptics device. What the... I thought I'd fixed these issues for good!

---

### Post by wgrant on 2008-10-18
It seems that my fix for the last amd64 issue caused the opposite issue in some places due to a single missing line... I'm rebuilding the affected stack in my PPA.

---

### Post by mariner09 on 2008-10-18
For what it's worth, I grabbed the new binary and it works on 32-bit Intrepid without having to add SHMConfig to my xorg.

Would I be better off adding your PPA at this point?

If so, can you give me the URL?

---

### Post by wgrant on 2008-10-18
> **mariner09 said:**
> For what it's worth, I grabbed the new binary and it works on 32-bit Intrepid without having to add SHMConfig to my xorg.

Would I be better off adding your PPA at this point?

If so, can you give me the URL?

This bug only affects 64-bit architectures. But please add "deb [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main" to your sources.list, update and upgrade - I'd like a fair bit of testing on both archs, and there's nothing dangerous there any more.

---

### Post by _oOMOo_ on 2008-10-18
I've added your ppa, and the segfault is gone.

```
:~$ xinput list-props 4
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled:		1
	Synaptics Edges:		1632, 0, 5312, 0
	Synaptics Finger:		25, 0, 30
	Synaptics Tap Time:		180
	Synaptics Tap Move:		220
	Synaptics Tap Durations:		180, 0, 180
	Synaptics Tap FastTap:		0
	Synaptics Middle Button Timeout:		75
	Synaptics Two-Finger Pressure:		257
	Synaptics Scrolling Distance:		100, 0
	Synaptics Edge Scrolling:		1, 1, 0
	Synaptics Two-Finger Scrolling:		0, 0
	Synaptics Edge Motion Pressure:		30, 0
	Synaptics Edge Motion Speed:		1, 0
	Synaptics Edge Motion Always:		0
	Synaptics Button Scrolling:		1, 1
	Synaptics Button Scrolling Repeat:		1, 1
	Synaptics Button Scrolling Time:		100
	Synaptics Off:		0
	Synaptics Guestmouse Off:		0
	Synaptics Locked Drags:		0
	Synaptics Locked Drags Timeout:		5000
	Synaptics Tap Action:		2, 3, 0, 0, 1, 2, 3
	Synaptics Click Action:		1, 1, 1
	Synaptics Circular Scrolling:		0
	Synaptics Circular Scrolling Trigger:		0
	Synaptics Circular Pad:		0
	Synaptics Palm Detection:		1
	Synaptics Palm Dimensions:		10, 0
	Synaptics Pressure Motion:		30, 0
	Synaptics Grab Event Device:		1
:~$ syndaemon -i 0.7 -d
Can't access shared memory area. SHMConfig disabled?

```

Cheers, Jon

---

### Post by wgrant on 2008-10-18
> **_oOMOo_ said:**
> I've added your ppa, and the segfault is gone.

```
[snip]
:~$ syndaemon -i 0.7 -d
Can't access shared memory area. SHMConfig disabled?

```

Cheers, Jon

OK, that was a nasty 64-bit unsafeness bug to fix... please try [this new one](http://launchpadlibrarian.net/18664539/xserver-xorg-input-synaptics_0.15.2-0ubuntu7~wgrant3_amd64.deb). syndaemon works for me on amd64 now.

---

### Post by _oOMOo_ on 2008-10-18
That's fixed it! Brilliant, works just as before except with SHMConfig off.

---

### Post by _oOMOo_ on 2008-10-20
The bug is fixed only as long as I use the version of xserver-xorg-input-synaptics that you provided for download a couple of posts ago...update manager keeps wanting to install the broken version.

Cheers,

Jonathan

---

### Post by _oOMOo_ on 2008-10-24
Syndaemon still not working with the default packages...

---

