---
title: "Help a noob installing his audio drivers please!"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-04-21
Hey guys, u see ive been good with my 9.10 ubuntu distro till yesterday... i was planning on using this pc for my clothing store so i can sell online, i gathered all my old pc parts, not that old but the hard drives,  I was like yes! this is gonna be cool, when i got to the store i realized that the hard drive died..................................................

I bought a new 500 gb hard drive and tried to install windows 7 but it couldnt, i guess it was the dvd disk, so i gave up and installed only ubuntu. I didnt had the speakers plugged in, i dunno if it affects, but as soon as the installation finished i rebooted the machine to find out that there was no drivers at all...

Ive tried everything ive found by googling, there are some steps i couldnt follow so i had to skip. So imagine, i was getting no where. SOmetimes i do everything but no help.

Im  A TOTAL NOOB.. i love ubuntu, ive been learning alot and i love commands, but u know im still a noob ...

Ive found "how tos" for installation of alsa drivers and pulse audio but i cant proceed at all when ppl just dont give exact details. Ur replying to a noob dude....

So if u go like  "Turn on sound support from kernel config" or something like that.. i dun really noe how to do that at all. Ive been googling like crazy i couldnt find how to do THAT.

Ive been trying from 10 pm yesterday night to 1 am today. Please help me out. I own a ECS 945GCT-M motherboard... i remember it was like "snd-hda-intel ALC 8something someting" the drivers from the last working distro.

Please help guys, gimme some details. Thanks. I dun wanna reinstall again!

---

### Post by P4man on 2010-04-21
assuming you havent messed things too badly following fragments of howto's, the solution can be trivial (though not always) :)

First, lets see exactly what card you have. Open a terminal (applications > accessoiries > terminal) and copy paste these commands:

```
lspci
```

(that is LSPCI in lowercase). Copy paste the output here.

Next, lets see if its not something muted. Play some music (dont use youtube or flash, as that could be a separate problem). Then in your terminal, type

```
alsamixer
```

You should get a "dos" style mixer. Use the arrow keys to navigate left/right, up/down to adjust volume and "M" key to toggle mute. Pay special attention the PCM channel is not muted.

We'll take it from there.

---

### Post by Zireth ZH on 2010-04-21
This is what appeared when typing lspci in the terminal....

backstage@backstage-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
03:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I tried alsamixer but it is only showing one bar of volume, and it is not muted.

Theres no hardware device detected on sound preferences... when using alsaconf it only detects ATI HDMI

---

### Post by P4man on 2010-04-21
Apparently its not seeing your audio device at all. The HDMI audio device is your videocard actually (if you connect a tv or monitor with HDMI, it gives both video and sound but its not the regular audio card).

Can you check in the bios of you computer if your onboard sound is enabled? Im guessing its turned off there.

---

### Post by Zireth ZH on 2010-04-21
I did that.. its enabled... any ideas?

---

### Post by P4man on 2010-04-21
Bummer. I was pretty sure it was disabled in bios :(
Lets see, open a terminal and paste in this command:

```
aplay -l
```

(thats APLAY -L in lowercase, but rather than typing, select it, press middle mouse button, in the terminal press middle mouse button again to paste).

---

### Post by Zireth ZH on 2010-04-21
aplay: device_list:207: no soundcards found...

---

### Post by P4man on 2010-04-22
Your sound card is not detected at all. Its not a driver issue afaict, its just like, not there. If you are 110% certain onboard audio is enabled in the bios (or is it set to "auto" ?), then Im gonna blame you motherboard and call it  a hardware issue. Perhaps you can consider picking up a cheap soundcard and plugging that in?

---

### Post by Zireth ZH on 2010-04-22
Ive made a fresh install of ubuntu.... I thought it would fix... but i guess ur right maybe is the mobo ... ill have to buy a sound card then... thanks alot for helping me out :)

---

