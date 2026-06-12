---
title: "Major crash during upgrade"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by GuiGuy on 2010-12-04
Just tried to upgrade my mythbuntu box from lucid to maverick.

It crashed during the upgrade. On re-boot it now stops at a dialog telling me its running in low graphics mode because it cannot load/find the nvidia drivers. I am unable to close the dialog. No mouse, no keyboard.

ESC will not let me interrupt the boot to get to a recovery console.

Do I panic now?

---

### Post by sikander3786 on 2010-12-05
No need to panic yet :-)

Press and hold down Shift key at Bios screen. Grub menu should pop up. (If you are using Grub2, the default key is Shift and not Esc ;-) )

Select Recovery > Drop to root shell and do a few commands.

```
dhclient eth0
```

Where eht0 is your network interface.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

If the above one is unsuccessful,

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Please post back the errors encountered (if any).

---

### Post by GuiGuy on 2010-12-05
> **sikander3786 said:**
> No need to panic yet :-)

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Please post back the errors encountered (if any).

Many thanks. The crash was actually due to a faulty motherboard.

Can I assume that the same approach as you listed can be used for recovery when significant hardware is changed?

TIA

---

### Post by sikander3786 on 2010-12-05
No that command just installs the updates.

If you plan to change your motherboard, the only thing you need to be conscious about is your graphics card. If any proprietary drivers are installed, remove them and then re-install them for the new graphics card.

Other than that, Linux Kernel is smart enough to load proper modules for different devices every boot :-)

---

### Post by GuiGuy on 2010-12-05
> **sikander3786 said:**
> 
Other than that, Linux Kernel is smart enough to load proper modules for different devices every boot :-)

OK, got it almost sorted. I wasn't able to get a recovery console up, but was lucky in that on boot I got a message that some HDDs couldn't be mounted. It gave me an opportunity to access a root prompt which let me back in. 

I had to change the MB. The only one at hand was one running ATI gfx, whereas the previous one was nvidia. I overcame that.

[B]Sound is the only thing that isn't working and it's driving me crazy. Sound is Linux's (Ubuntu's) Achilles Heel, I suppose.  VLC plays sound fine through the HDMI connection, but other apps (XINE, mplayer, mythtv etc), no go. After eight hours of stuffing around and getting nowhere it's enough to drive a man to windows. ;)
[/B]

That said, neither ESC or SHIFT gives me the recovery console on boot. I have four other Ubuntu (10.04 and 10.10) PCs & notebooks here. All behave the same; pressing either ESC or SHIFT on boot does nothing. Seems crazy that there is no way to break the boot sequence.

Cheers

---

### Post by sikander3786 on 2010-12-06
Sound issue needs a new thread under Multimedia & Video ;-)

And you need to press and **hold** down Shift key as soon as computer starts until you see the Grub menu ;-)

---

### Post by GuiGuy on 2010-12-06
> **sikander3786 said:**
> Sound issue needs a new thread under Multimedia & Video ;-)

[rant]No, my head is now hurting so much from the convoluted obfuscated stuff I have been reading that I think only another OS will save my sanity. NB: I have been sifting through the multimedia threads. Given all of the problems so many folks are having with sound you'd think someone would realise that all is no well on the Linux Sound Front. It is a confusing mess IMO[/rant]

> And you need to press and **hold** down Shift key as soon as computer starts until you see the Grub menu ;-)

Alas, no. Doesn't work on my boxes. Nor does holding down [esc]. :(


Cheers

---

### Post by sikander3786 on 2010-12-06
I feel sorry for your troubles.

But I also feel that the problem you got was due to your "faulty motherboard" as you suggested above, rathen than Ubuntu itself. And you might be aware of the fact that you can't change motherboard for a Windows install. You just need a clean/new install when you swap/change motherboard ;-)

Choosing an OS is definitely your personal choice. Choose the one that best suits and fulfills your needs :-)

And I am not sure why you can't see the Grub menu :confused: It should be either Shift or Esc key.

If you need help on that, we need to see if /etc/default/grub is there and if yes, we need to see does it contain.

```
cat /etc/default/grub
```

Hopefully, you would be out of troubles soon. This way or another ;-)

Good Luck!

---

### Post by GuiGuy on 2010-12-06
> **sikander3786 said:**
> I feel sorry for your troubles.
Choosing an OS is definitely your personal choice. Choose the one that best suits and fulfills your needs :-)

I was kidding, but you knew that. We are masochists after all ;)

> And I am not sure why you can't see the Grub menu :confused: It should be either Shift or Esc key.

I can confirm that neither the ESC key or SHIFT key lets me break the boot sequence. ESC used to back in 9.10, if I recall. I noticed it stopped in 10.04

Recovery used to come up by causing an unscheduled shutdown. I notice now only a hard disk check is prompted, A bit like Windows, if you like. 

> If you need help on that, we need to see if /etc/default/grub is there and if yes, we need to see does it contain.

Looking into my /etc/grub thingie I see
> 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"


Is that it? 

I do appreciate your effort here, so many thanks. 

At the moment the missing HDMI sound is getting all of my attention. I have analogue and SPDIF working though, so that's something. 

Cheers

---

### Post by sikander3786 on 2010-12-06
Was that the complete output of this one?

```
cat /etc/default/grub
```

I hope it wasn't. Please copy/paste everything you see after running that :-)

---

