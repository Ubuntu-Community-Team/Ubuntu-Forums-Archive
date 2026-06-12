---
title: "Installing Kubuntu 7.10 on a Medion Akoya MD96380"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by bentob0x on 2008-01-04
Dear Ubuntu community, 

Last night I installed Kubuntu 7.10 on my laptop and I want to share here my experience and a few hiccups that happened while I installed everything.

I'm using Kubuntu/Ubuntu for almost a year now and I'm very happy with the distro (some rough edges here and there but it's getting there).

_**1) Laptop specs**_
The laptop is a **Medion Akoya MD96380** and the full specs are available here: _[http://www.medion.de/md96380/be_fr/noflash.html](http://www.medion.de/md96380/be_fr/noflash.html)_ (french only, sorry :s)

_**2) Minor install problems**_
Apart from a startup error message which persists after Kubuntu was installed (... Failed to allocate mem resource ...), the install was very fast as usual:

22:52	Start install (double-click on desktop icon once the live CD did fully load up)
23:11	The installer told me that everything was installed and that I needed to restart (but I could keep on using the live install CD if I wanted to)

First of all, at some stage the installer couldn't verify the security of the deb repositories (I wasn't connected via my Ethernet port and obviously, the wireless card didn't get picked up by the installer).  After the restart, I ran 'sudo apt-get update' but I couldn't do any updates as the 'unverified' deb repositories were commented out.  I had to manually edit the /etc/apt/sources.list file to uncomment the deb repositories to be able to do an update.

After I uncommented the repositories, I ran again 'sudo apt-get update' but the update **didn't update anything**.  The 'version upgrade' button was available tho and I clicked on it, everything seemed to work then.

This is the second time that I do a Kubuntu install and that adept tells me that there is an upgrade available even tho I use the most recent distro CD.  I can't remember if the first time I was connected to the internet from the start of the install but I think I was.

This is something that should be fixed for future versions of Kubuntu as I downloaded the Kubuntu 7.10 CD and adept shouldn't offer me to do a version upgrade but simply an update on the currently installed version.  I think this is confusing.  Also, even tho it is very good to have a check on the repositories for security reasons, if the install comments out the repositories because there is no network way to check that they are valid, once the computer gets connected to the internet, the OS should offer to check the repositories and then uncomment them itself (without having to 'hack' into the sources.list files to get it to work).

Anyway, after the version upgrade and after having downloaded 191Mb of updates, everything was finally setup properly (not everything yet as I haven't had the time to go through all the hardware features of my laptop but most of it anyway).

So I started to install a few software (Yakuake, Firefox, etc) and everything ran smoothly.

_**3) Rights problems**_
I started to have a problem with the 'administrator mode' system while changing the drivers (I wanted to use the nvidia restricted drivers).  The administrator mode didn't allow me to edit anything at all (it seemed as if it was just ignoring my password).  I had to use 'kdesu kcontrol' to do so.  The drivers installed without any problems and I rebooted.

_**4) Video card problems (nVidia 8600M GS 256Mb DDR2)**_
After the reboot, the font size of the interface was different (bigger) than the one used by the non-restricted drivers even tho the monitor resolution is the same.  Why is that?  Also, I don't have the choice to modify anything under 'System Settings -> Monitor & Displays', only one resolution is suggested.  If I use nvidia-settings, I have a bit more options in there but still nothing convincing in terms of full control of your video card.  Anyway, I shouldn't have to go through the nvidia-settings to simply change the monitor resolution and refresh rate.  I'm far from being an expert in Xorg/nVidia but I shouldn't be one to change my screen resolution and refresh rate.

Also, the temperature of my video card was full green with the first yellow line, which scared me a bit already.  Is there anything that should be setup through the drivers or the system to make sure the fan runs a bit more often?

I'd like to point out here that I had a few issues with nVidia video cards and the xorg.conf file, not this time particularly but more generally through various Kubuntu installs.  This is something that _really_ needs to be ironed out properly.  Being able to have an easy and full control over your video card settings, monitor resolution etc is something that should be totally smooth and transparent.  A big effort is already being made through he restricted drivers system but a better monitor detection and maybe an expert-only mode to force and setup some refresh rates and resolutions via a GUI would be very nice (with warnings about possible damage done to monitors etc).  I'll try to make another post to explain a bit more the various issues I faced while trying to setup the monitor/video card on different machines.

_**5) Backgrounds problems**_
I wanted to change my desktop background and at some point I found myself in a menu that seemed to connect online to let me choose different backgrounds (highest rated etc).  I choose one and applied it but it didn't change anything on my desktop.

_**6) Questions**_
- When you enter your password for administrative actions, how long does Kubuntu remembers your password?
- If I go to administrative mode under 'System Settings -> Monitor & Displays' and enter my password for this, is my password remembered for another section like if I want to do some admin stuff with Firestarter?
- When installing a custom background from an image you have on your desktop, does it copy the image on your desktop in the backgrounds folder (/usr/share/wallpapers/) or does it link to where the image is?

_**7) Conclusion**_
I still have to do a few things on the laptop:
- sort the video resolution properly
- install and see if I can use all the features/hardware of the laptop 

If you have any questions, suggestions, advices, don't hesitate to let me know about them :)

- bentob0x

---

### Post by icheyne on 2008-01-05
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by bentob0x on 2008-01-11
Hi again,

I couldn't do anything on my laptop for the last week or so.  Here I am again for a bit more happy hacking on it.

First of all, lspci and lsusb:

**lspci**:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:00.0 Multimedia controller: Philips Semiconductors Unknown device 7160 (rev 03)
```

**lsusb**:
```

Bus 006 Device 002: ID 0bda:0116 Realtek Semiconductor Corp.
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 003: ID 05e3:0503 Genesys Logic, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Second, more things that doesn't seem to work 'out of the box':
- the sound doesn't seem to output from the speakers where the front jack works fine
- the brightness up/down fn buttons (fn+F6 and fn+F7) don't work at all (when on battery or on main power)
- The wireless card has been detected and works but no software was installed automatically (KWifiManager).  Is this a bug in Kubuntu 7.10 install?

I'll try to resolve those issues one after the other starting from the speakers sound.  I'll post replies to this tread with further updates

- bento

---

### Post by bentob0x on 2008-01-11
Sound system:

First here is the current state of the various sound elements in KMix:

**_KMix_**:
**Output**:
[LIST]
[*]Headphones
[*]PCM (no on/off switch)
[*]Front
[*]Front mic
[*]Mic
[*]Speakers
[/LIST]

**Input**:
[LIST]
[*]Capture
[*]Capture
[/LIST]

**Switches**:
[LIST]
[*]IEC958 (turns on/off the front S/PDIF plug)
[*]Caller ID
[*]Off-hook
[*]Input source combo box (containing Mic and Front mic, set on Mic)
[*]Input source combo box (containing Mic and Front mic, set on Mic)
[/LIST]

**_Here are the sound issues_**:
[LIST]
[*]There is no sound coming from the built-in speakers.
[*]I did set the KMix master channel to 'PCM' and when I click on the tray icon to change the slider, everything works as expected except the 'Mute' button (there is no on/off switch on 'PCM').
[*]The 'Headphones' switch doesn't seem to do anything but the fn+F3 and fn+F4 button do work.  They do change the 'Headphones' slider value.
[*]The 'Front' and 'Speakers' volume seems to be both tied to the front mini-jack.  Both work 'almost' as expected (see Checks on KMix/Output section further below).
[/LIST]

**_Questions_**:
[LIST]
[*]What are 'Front mic' and 'Mic' doing in the Output tab?
[*]Why is there two identical 'Capture' sliders?  I suppose its for the front mic mini-jack and the built-in microphone but if it's the case, why don't they have two different captions like there are two on the Output tab (Mic and Front mic)?
[*]What is the Caller ID switch?
[*]What is the Off-hook switch?
[*]What are the combo box in the Switches tab for?
[/LIST]

The following checks were made to see what was going on exactly with the sound output.

**_Checks on KMix/Output tab_**:
**Check 1**:
- turn all switches to off
- turn 'Front' switch to on
Result: sound comes out of front jack

**Check 2**:
- turn all switches to off
- turn 'Speakers' switch to on
Result: sound comes out of front jack

**Check 3**:
- turn all switches to off
- turn 'Front' switch to on
Result: sound comes out of front jack
- change slider on 'Speakers' left or right
Result: sound gets muted
Action: turn 'Front' switch off then on again brings the sound back
Note: the exact same (inverted) result happens when turning 'Speakers' on and changing the slider on 'Front'

**Check 4**:
- turn all switches to off
- put all sliders at same volume
- turn 'Front' switch to on
Result: sound comes out of front jack
- turn 'Speakers' switch to on
Result: no changes, sound still there
- turn 'Speakers' switch to off
Result: sound is off even tho 'Front' switch is still on
Action: turn 'Front' switch off then on again brings the sound back
Note: the exact same (inverted) result happens when starting with 'Speakers' and then turn off 'Front' switch

**Check 5**:
- turn all switches to off
- put 'Front' slider to 75%
- put 'Speakers' slider to 25%
- turn 'Front' switch to on
Result: sound comes out of front jack
- turn 'Speakers' switch to on
Result: sound volume is now 25%
Note: the exact same (inverted) result happens when turning 'Speakers' on and turning 'Front' to on, sound volume is now 75%

More to come ...

- bento

---

### Post by bentob0x on 2008-01-13
Found somebody else who has bought the same laptop and is trying to get the PCMCIA TV Tuner card working here: [http://ubuntuforums.org/showthread.php?t=665022]("http://ubuntuforums.org/showthread.php?t=665022")

---

### Post by Partyboi2 on 2008-01-13
> _**6) Questions**_
- When you enter your password for administrative actions, how long does Kubuntu remembers your password?default for sudo is 15 min
can change it by editing visudo

---

### Post by kvonb on 2008-01-13
_-_

---

### Post by bentob0x on 2008-01-13
Thx for your replies guys.  

@ Kvonb: I added that line in the /etc/modprobe.d/alsa-base file and rebooted but no changes.  I also had a look at that link you sent but still no luck :(

I have kept on working a bit on that sound/speakers issue and a wierd thing happened since then: in KMix/Output, between Mic and Speakers, a new 'Digital' slider has appeared.  I don't know what that is.  I have taken off the PCMCIA TV Tuner card since then and this might have triggered the new slider but I don't think so as it doesn't make much sense to me.  Also, in KMix/Input, a new 'Digital' slider has appeared also (no changes in KMix/Switches).

So I'm puzzled, why is there a new 'Digital' slider now???

---

### Post by bentob0x on 2008-01-13
I have also realised that when I do:

```

lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`

```

I'm getting:

```

00:1b.0 0403: 8086:284b (rev 03)

```

And as per this article: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"), I should have the bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133") which basically shouldn't give me any sound at all.  The problem is that I DO have sound coming out of the front mini-jack but not on the speakers.

This is turning into a big investigation ...  But there is no better way to learn :)

-  bento

---

### Post by bentob0x on 2008-01-13
A bit more on the sound end.

When I run:
```

cat /proc/asound/card0/codec#* | grep Codec

```

It outputs:
```

Codec: Realtek ALC883
Codec: Generic 11c1 Si3054
Codec: Realtek ID 268

```

After reading a bit this page: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")   I've found a 'medion' setting under the ALC883 section:
```

ALC883/888
3stack-dig	3-jack with SPDIF I/O
6stack-dig	6-jack digital with SPDIF I/O
3stack-6ch    3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo  6-jack digital for Intel demo board
acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
**medion**	Medion Laptops
medion-md2	Medion MD2
targa-dig	Targa/MSI
targa-2ch-dig	Targs/MSI with 2-channel
laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e	Lenovo 101E
lenovo-nb0763	Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
6stack-hp	HP machines with 6stack (Nettle boards)
3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
auto		auto-config reading BIOS (default)

```

So I edited the alsa-base file to add the line:

```

options snd-hda-intel model=medion

```

Unfortunately, I still don't have any sound coming out of the speakers but something funny happened: the fn keys to put the sound up and down (fn+F3 and fn+F4) now go between 0% and 11%, not any further, 11% is the max.

Appart from that, I have much more sliders in the 'KMix/Output' but surprise surprise, no sound at all (no headphones sound anymore).

I suppose that I have to try every single setup there and see if I can find one that is working perfectly for this laptop.

- bento

---

### Post by kvonb on 2008-01-14
-

---

### Post by vervelover on 2008-01-15
I also have a Medion laptop (RIM2150) and I also have the integrated speakers issue, and I couldn't find a way to work it out.. also I noticed the sound coming from the headphones jack is way too low even at max volume settings..

---

### Post by bentob0x on 2008-01-22
Ok, an update:

It seems that the following alsa config works 'almost' completely with the laptop:

Edit alsa-base (I use Vim but use whatever you like to edit the file):
```
sudo vim /etc/modprobe.d/alsa-base
```

And then add the following line to the very end of the file:
```
options snd-hda-intel model=6stack-dig
```

A couple of problems tho, the fn speakers key only swaps between 0% and 11% (but doesn't seem to do anything on the sound), and the various channels in KMix aren't corresponding to the right outputs.

I'll post a full explanation of the various KMix channels in a later post.

- bento

---

