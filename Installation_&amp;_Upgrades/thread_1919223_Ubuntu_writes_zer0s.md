---
title: "Ubuntu writes zer0s"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by AKAndrew on 2012-02-02
Well hi!

Today I've installed Ubuntu on my PC as a second OS, on Windows XP SP3 with the "Ubuntu installer for Windows". All good till I get in it...
The problem is that it writes, types zeros by his own. I unplugged my keyboard, even reinstalled this software a few times, but it did not helped me at all. It still writes that zeros so I can't do anything about it.
I can't take any pictures because I have not installed enthernet on Linux yet... To see what I am talking about, press 0 on the main screen, or anywhere else...

I have to mension that this goofy thing does no happens on XP...



Any ideas?

---

### Post by Desann243 on 2012-02-03
Have you tried at least 2 different keyboards?

---

### Post by |{urse on 2012-02-03
looks like your 0 key is stuck

---

### Post by AKAndrew on 2012-02-03
I had already said that I've tried to unplug my keyboard but it did not stopped to write that zeros.
If it was from my keyboard I could notice that since I was on Windows XP.

---

### Post by AKAndrew on 2012-02-03
bump.
Realy need some help...

---

### Post by ottosykora on 2012-02-03
ok, I understand it is a WUBI installation, the linux is in virtual drive right?

Can you try to start the same version of linux from live CD for example, to see if this problem persists?

---

### Post by AKAndrew on 2012-02-03
I have just tryed it from the stick... still writes those zeros...
In Oracle VirtualBox on Windows this ain't happen.

Anything else I could do to stop it from writing those 0s?

---

### Post by |{urse on 2012-02-03
Oh sorry yes you did say that.
forum blindness

I know this is gonna sound like a bummer but you should really install ubuntu the normal way. I'm sure if you did this bug would most likely go away.

just curious what model of keyboard do you have? is it a gaming keyboard with a turbo switch? Is it usb or ps2? Do you have any other usb devices connected? Game controllers laying on the floor maybe?

---

### Post by AKAndrew on 2012-02-03
I can't and I won't install Linux on this PC as a primary OS if this is what you want to say. This is a family-computer and the others don't know how to use Linux.

My keyboard is a Genius k640. Just a multimedia keyboard, nothing fancy.



Sorry for my creepy english language and explanation. I'm a 15years old Romanian guy :-).

---

### Post by |{urse on 2012-02-03
[IMG]http://1.bp.blogspot.com/_6GyQjwWOmQA/Skikgd9R5gI/AAAAAAAAAdc/ygS65JHZW38/s400/GeniusKeyboard16e.png[/IMG]

> **Desann243 said:**
> Have you tried at least 2 different keyboards?

I'd try a different keyboard, do you have another keyboard?

---

### Post by QIII on 2012-02-03
I think the poster has pretty much shown enough for us all to gather that it is not a problem with his keyboard.  The behavior does not occur in Windows.

OP:  Let me understand this.  You say that this occurs in a Wubi install, but not if you install in a virtual machine in Virtualbox?  Is that correct?

---

### Post by AKAndrew on 2012-02-03
@**|{urse** I have just done that too... still the same old sh*t.


@**QIII** Yes, that is correct :-).

---

### Post by QIII on 2012-02-03
So we seem to have gotten back on track:  this is a Wubi installation question and that's what you were asking about all along.

Correct?

I'm no Wubi expert, so I'll have to leave that to others.

If you don't get a resolution, is virtualization a suitable work-around for now?  

By the way -- there is no reason to excuse your English.  We understand that there are users all around the world.  We try to work around language barriers as best we can.

---

### Post by AKAndrew on 2012-02-03
No. At this moment I don't have any others than this one...


All I wanted to know is just **how to stop the OS from writhing those zeros... **that's all.

---

### Post by QIII on 2012-02-03
The problem with the zeroes is related to your Wubi install, I believe.  That will have to wait for someone with more Wubi expertise than I.

What I am suggesting is to leave Windows as the primary OS (so your family doesn't get confused), install Virtualbox in Windows and install Linux as a virtual machine so you can at least use it.  You will have internet connectivity in Linux that way.

When someone else in your family starts the computer it will just be good old Windows.  Only you will know to start Virtualbox and get to Linux.

---

### Post by AKAndrew on 2012-02-03
I did that for about two months, but the performance of Linux on that VirtualBox is very poor. If I'd open mozilla and the terminal on Ubuntu in VB, and then I open a folder it will move just like my great grandmother, and she's dead. You got the point...

I have a dual-core 1.6GHz Intel E2140, 1.5GB of RAM and only 160GB on HDD.

---

### Post by QIII on 2012-02-03
I understand that a Wubi install has performance drawbacks as well.  Do you think that if you did an actuall dual boot, you could show your family how to select Windows from the GRUB menu?  That would give you native performance in Linux.

Wubi is generally not considered to be the ultimate set up (although some use it permanently) but rather as a temporary "test drive".

My daughter has a very old laptop with 512MB of memory and a PIII and a 20GB drive.  She runs an Ubuntu derivative called Bodhi with the Enlightenment desktop.  You would never know what a wimpy machine it is.

Mind you:  this is only a suggestion in case nobody can come up with the Wubi answer for you.

---

### Post by AKAndrew on 2012-02-03
I already can benefit of that 'native performance' because I have Ubuntu as a second OS, but it keeps writing those zeros...

Sorry, but I don't want to try any derivative or some sort of thing untill I won't deplete all of the resources on this Ubuntu.

---

### Post by bcbc on 2012-02-03
I would think that this is very unlikely a wubi problem (since that's been brought up more than a few times). I've certainly never seen anything like this before.

I recommend booting up an Ubuntu CD (select "Try ubuntu") and then see if you have the same problem. If it's fine, then maybe there's a problem with Wubi detecting your keyboard locale settings in Windows (that's a guess). 
If you still get zeroes running the live CD, then it's something with the keyboard + ubuntu.

---

### Post by QIII on 2012-02-03
It is at least obliquely related to Wubi.  You may be right about your guess.

The OP clearly says this behavior was not manifest with Ubuntu running in a virtual machine.

---

### Post by bcbc on 2012-02-03
Virtual machines provide a hardware abstraction layer so you can never be sure whether Ubuntu is really compatible with your hardware. Wubi and normal Ubuntu directly access the hardware.

It's easy to rule out normal Ubuntu running a live CD. If wubi is the cause, it's likely setting the keyboard to the wrong type (but in that case I'd expect a key mapping problem, not zeroes). I have't seen anything like this, but anything is possible.

I once had a keyboard that caused BSODs on my laptop. They changed the motherboard a few times, and finally replaced it with a different model. I still have that keyboard 7 years later - never had a problem with it since on any computer... so you never know.

---

### Post by ottosykora on 2012-02-04
yes, but OP states that the problem is here also when running from usb live media.

This must be some problem between linux and bios or so .

I would try some other distro, something more simple perhaps, to run from externeal media as CD etc. 
To see if it is something general connected to particular kernel, or distro.

Wubi itself is not very much different once started from real install, so I believe in this case even partition install will not help much.

---

### Post by AKAndrew on 2012-02-04
_**A review of all I've tryed so far:**_
* To boot up Ubuntu on VirtualBox - [COLOR=Green]problem does not persist[/COLOR]
* To boot up Ubuntu on VirtualBox with another keyboard - [COLOR=Green]problem does not persist[/COLOR]
* To boot up Ubuntu as a second OS(after Windows) - [COLOR=Red]problem persists[/COLOR]
* To boot up Ubuntu as a second OS(after Windows) with another keyboard  - [COLOR=Red]problem persists[/COLOR]
* To boot up Ubuntu from a USB  Stick - [COLOR=Red]problem persists[/COLOR]
* To boot up Ubuntu from a USB Stick  with another keyboard  - [COLOR=Red]problem persists[/COLOR]


What other distro do you recomand to try?

---

### Post by ottosykora on 2012-02-04
well, you could start with some small bootable linux like partedmagic or puppy linux or something like that and then try lubuntu or xubuntu to see if it has something to do with graphical interface or linux kernel itself.

Also try some older ubuntu distro in live mode (usb stick or cd), it will have older kernel, so we can pinpoint it to right direction.

It is clearly some hardware or bios problem, as those are virtual in virtual machines.

---

### Post by AKAndrew on 2012-02-04
Alright, I've tried Ubuntu 10.04.03 - still writes zeros. As well as in BartedMagic...


**[COLOR="DarkRed"]But[/COLOR]**, I've noticed someting during booting partedmagic. While the system shows me what task do it has to complete*(initiating installation, copying files on RAM etc.) *, the computer was typing in there zeros too, and then it shows that '[COLOR="DarkGreen"]**[SIZE="2"]DONE[/SIZE]**[/COLOR]' response of tasks. 
I thought that it was from the OS, but it wasn't...

Should I upgrade my bios and then try this again?

---

### Post by AKAndrew on 2012-02-04
Updated the BIOS. Still made that thing...

---

### Post by |{urse on 2012-02-04
> **QIII said:**
> I think the poster has pretty much shown enough for us all to gather that it is not a problem with his keyboard.  The behavior does not occur in Windows.

I disagree, I've had quite a few gaming keyboards that similar issues under ubuntu that worked fine under windows. It usually was due to the keyboard having a typematic turbo switch. 

I was awaiting the OP's response as to whether switching keyboards helped.

So what now? Motherboard?

---

### Post by QIII on 2012-02-04
My apologies, everyone.  I did not read post #7 carefully enough until  after the poster gave us a review.  It is happening in a straight-up  installation and I was mistaken in thinking it had something to do with  Wubi.  And bcbc made a good point about the hardware abstraction in VBox, which may be why the problem does not occur there.
   
      As to keyboard itself as the fault, I still think that he has still eliminated that.   He has  switched the keyboard and has even disconnected the keyboard.  Notice  that in all the cases where there was no abstraction, even after  changing keyboards, the behavior persists.

It also persists between versions of Ubuntu and when he uses PartedMagic.

So if, for the moment, we set aside keyboard and particular OS, we have the hardware between -- and a question about how that is behaving with Linux in general.
 
 AKAndrew gave us some of the info about his machine, but we may need more. As much as you can give us.  |{urse suggested motherboard, which is a pretty good place to look.

 So, AKAndrew, could you give us the make and model of the machine?   Maybe we can find some other similar behavior with that particular line.

I understand you are having some difficulty with this, but could you try to find some way to post the results of 

```
lspci -v
```even with all of the extraneous zeros showing up?  I know that is going to be difficult, but it might help.

---

### Post by AKAndrew on 2012-02-05
_**lspci -v**_
[http://www.pastebin.com/UCMGatEh](http://www.pastebin.com/UCMGatEh)

_**Rig:**_
CPU: Intel(R) Pentium(R)Dual CPU E2140@1.60GHz LGA775
GPU: nVidia GeForce 7200GS 256MB
Motherboard: Biostar P4M900-M7 SE
[ *BIOS Updated on 2008-03-13]("http://www.biostar-usa.com/app/en-us/mb/introduction.php?S_ID=289#")
Memory: 1.5GB DDR2 533MHz
HDD: WestDigital 160GB Buffer 8MB
OS: Microsoft Windows XP SP3

Display: LG FLATRON L1919S
Keyboard: Genius K640
Printer: Canon PIXMA IP5000
Mouse: A4Tech X-718BK
Speakers: Logitech X530 5.1

---

### Post by AKAndrew on 2012-02-05
bump...

---

### Post by bcbc on 2012-02-05
Have you tried [booting with nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")? It's normally required with nvidia cards. Your symptoms don't seem typical for this, but try it anyway.

---

