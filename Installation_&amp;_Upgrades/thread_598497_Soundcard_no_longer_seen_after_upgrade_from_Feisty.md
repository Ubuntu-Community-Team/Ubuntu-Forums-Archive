---
title: "Soundcard no longer seen after upgrade from Feisty"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by aspie on 2007-10-31
I have been eagerly awaiting the Gusty release of Ubuntu Studio, as my E-mu 1820M soundcard should have become supported.

I did a clean install, and in general things went well (with the notable exception of my wireless card).

However, now my system doesn't even see the 1212m PCI card that is part of the 1820M, and was seen under Feisty.  

Here is the output from ***lspci.***  All I see is the on-board VIA AC97, and a Creative Audigy card (that is not there!  I'm guessing this is my 1212M card that has been incorrectly identified)

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0e.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)

```

Any ideas how to go about fixing this?

---

### Post by aspie on 2007-11-07
OK, I have made a little progress with his, and think that this output from dmesg is related to the problem:

```
[   44.431169] emu1010: Special config.
[   44.431251] emu1010: EMU_HANA_ID=0x7f
[   44.449873] firmware: emu/hana.fw not found. Err=-2
[   44.449880] emu1010: Loading Hana Firmware file emu/hana.fw failed
[   44.461061] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   44.463093] EMU10K1_Audigy: probe of 0000:00:0e.0 failed with error -2

```

Any ideas how to move this on?

---

### Post by stewartjm on 2007-11-08
I think the problem is that the alsa-firmware package is missing from the Ubuntu repositories.  This probably isn't the "right" way to do this, but it worked for me.

download the latest alsa-firmware package from:
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

tar -xvjf the archive
cd into the emu subdirectory and run the following commands:
```
gcc fw_writer.c
./a.out
sudo mkdir /lib/firmware/emu
sudo cp *.fw /lib/firmware/emu
```

you can unload and reload the driver with:
```
sudo modprobe -r snd_emu10k1_synth
sudo modprobe -r snd_emu10k1
sudo modprobe snd_emu10k1
```

---

### Post by aspie on 2007-11-08
Thanks for the help :)

Well that seems to work just fine, the lights are now lit on the dock!  Now, I just have to figure out how to route sound through this thing in Linux. 

Thanks again, much appreciated

---

### Post by ebbot7 on 2007-11-11
Hi, I'm a 1820 user too, and it sounds great that something finally is happening driverwise:) I wonder if the 1820M driver works with my 1820-card?!? I got to try this...tomorrow hehe

---

### Post by aspie on 2007-11-12
I reckon it will work for the 1820 too, but please post when you have tried it.  I'd really like to know.

---

### Post by ebbot7 on 2007-11-12
Anyone succesful with with the driver for 1820? I haven't got the time this week to try for myself, but I will get into asap...
aspie: yeah, I reckon it will work too, it's close enough, the only thing that differs are the D/A converters. I guess the "architecture" are similar :)

---

### Post by mightysween on 2007-11-16
Aspie, have you tried it in the latest Ardour? 

I'm hesitant to declare victory, but I have had some positive things happen.  The cardbus is recognized, and the correct lights on the dock come on and I hear the "click" that the EMU 1616 makes when the driver loads in Windows.

There is, of course, no patchmix.   But Ardour is capable of assigning inputs directly from pcm devices...and right now it seems that I can select multiple inputs (14 of them).

I'm pretty excited...I think this we might finally be making progress toward actually having a professional multitrack option for linux!

I am going to bring in some more hardware to test with in coming days and I will post my results.



> **aspie said:**
> Thanks for the help :)

Well that seems to work just fine, the lights are now lit on the dock!  Now, I just have to figure out how to route sound through this thing in Linux. 

Thanks again, much appreciated

---

### Post by aspie on 2007-11-16
Hi have tested it (briefly) with Ardour 2.0.5.  I connected an SM58 mic to the "mic A" input, and it worked fine.  

Prior to this I had messed around with AlsaMixer, but maybe I ddn't need to for Ardour.  

The whole ALSA, JACK thing is a little confusing to me at the moment. 

 I never thought I'd say it, but I kinda miss Patchmix.  I hope some clever person writes an Linux alternative soon.  I'm even tempted to have a go myself, but I just don't now where to start!

---

### Post by mightysween on 2007-11-16
> **aspie said:**
> ... I never thought I'd say it, but I kinda miss Patchmix.

Ha!  I feel the same way.  I absolutely hated Patchmix in Windows at first, then I started realizing it was a necessary evil.   Now we're stuck with no Linux equivalent.

But it seems to me that Ardour should have the capability to do everything that Patchmix did, and more.   Basically, since JACK would take care of identifying and routing all the inputs to the software, Ardour could act without the Patchmix "middleman" handle the assignment of pcm channels to tracks, routing through effects busses, etc. 

I decided to try it out tonight, and I am also getting a signal through the mic channels on the front of the 1616  dock.   That is a good sign.   But I am not seeing any signal from any of  the other inputs, nor can I seem to make more than one work at a time.   

But this is as close as I've ever seen it to working...I can taste Windows-freedom!

:)

---

### Post by mightysween on 2007-11-17
Bah. :(   Somehow I have managed to screw things up and not only will the 1616 not work, Ubuntu will not even boot with the card inserted in the pcmcia slot.

I have tried a fresh install, and a re-install of the alsa 1.0.15 files...no luck.

If I insert the card after booting, it shows up in the Hardware Information...but I'm not able to make the dock work, and the modprobe commands just freeze my terminal.

Guess I'm heading back to square one!

---

### Post by aspie on 2007-11-18
I'm sorry to hear that, sounds like a real PITA.  I wish I could help you, but I really have no idea where to start.  Please let us know if you get it fixed.

---

### Post by Ashrael on 2007-11-21
Has everybody tried booting from cd, sometimes it will work there... Please post your experiences..

There's 100+ post about gutsy sound, i'm starting to think there's more to this...


thanx

[http://ubuntuforums.org/showthread.php?t=618554](http://ubuntuforums.org/showthread.php?t=618554)
[http://ubuntuforums.org/showthread.php?p=3805039#post3805039](http://ubuntuforums.org/showthread.php?p=3805039#post3805039)

---

### Post by aspie on 2007-11-21
I'm running Ubuntu Studio, so I don't have the option of booting a LiveCD at the moment.  If I download a "standard" version of Ubuntu I will give it a try and let you know.

---

### Post by Ashrael on 2007-11-22
Keep me posted ASPIE!  I am getting a bit down about it, because i get hardly any feedback...

THX!

---

### Post by mightysween on 2007-11-25
I tried booting from the CD...still no luck.

After reinstalling everything and trying out about a dozen different distributions, I learned that a combination of ALSA driver > 1.0.15 and kernel version of > 2.6.23 are required to make it work at all and that full support of the EMU audio systems is still in development.   In fact, if you look at the release notes for the kernel releases (and candidates) up to 2.6.24 you will see a lot of progress...

So, I am now running Ubuntu updated to 2.6.23-experimental.   And finally, some progress.   The E-mu 1010 is properly recognized, and the Audio Dock is functional.   The repository I used to add this to Ubuntu was [http://kernel-archive.buildserver.net/debian-kernel/](http://kernel-archive.buildserver.net/debian-kernel/) trunk main.   Of course, the odds of screwing up your system are very high so treat this as "experimental", indeed.

Now, I'm back to the point I've been stuck at before...the hardware works, but we have little software to control it.   

At least now I can get to the task of trying to figure out how to control the 1616 now that it is running in Linux.   Until then, my recording remains in Windows XP...

---

### Post by aspie on 2007-11-26
Thanks for the info **mightysween**  I have my 1820M running under 2.6.22-14, but it doesn't seem too reliable just yet.  I get ALL lights on, on the AudioDock sometimes.  However it is working OK most of the time, and your post is good news.  I guess (or hope) that things will only get better from here.

---

### Post by mightysween on 2007-11-26
Yes, there is progress for sure.

I think we're right back at the point you mentioned earlier...longing for that wonderfully complicated PatchMix type of software. :)

I'm positive that the hardware is working properly.   I can assign each input on the dock to a /dev/dspX device, and I can hear the click in the dock when I select the input level functions--just like in patchmix.    It is all there...except a way to interface it with a recording application!

Hopefully someone smarter than me is working on this. ;)

---

