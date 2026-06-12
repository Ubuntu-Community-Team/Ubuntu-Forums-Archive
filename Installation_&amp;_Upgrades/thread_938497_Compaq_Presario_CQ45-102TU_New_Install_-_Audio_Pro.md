---
title: "Compaq Presario CQ45-102TU New Install - Audio Problems"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by dococo on 2008-10-04
I am trying to install Ubuntu on my new Compaq but I am having problems with the audio. Some background:

In order to get the wifi to work I installed Intrepid since it would not work with hardy (I read this tip on another post). After installing all the updates it worked fine.

Now when i boot up I hear the drum roll (a good sign) but it seems to get into a loop. In other words the sound card is recognised but it would appear that the drivers are not correct. I have followed various threads on checking the sound card and I have tried installing the latest ALSA upgrade (even the new R3). I also tried Removing ALSA and trying OSS but this resulted in the sound card not being recognised so I reverted back to ALSA.

Anyway, I have come to the point where i am stuck for ideas. Any help or suggestions would be most appreciated. Below I have listed the output of aplay -l and lspci -v with some background specs - which makes the tread rather long -sorry!! 

Thanks....

-----

Compaq  Presario CQ45-102TU
CPU 		Intel Core 2 Duo P8400 (2.26 GHz,FSB 1066 MHz, L2 3 MB)
Chipset 	Intel PM 45

Ubuntu
Release 8.10 (Intrepid)
Kernel 2.6.27-4-generic


aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]

  Subdevices: 0/1

  Subdevice #0: subdevice #0


lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0

	Capabilities: <access denied>

	Kernel driver in use: agpgart-intel

	Kernel modules: intel-agp



00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]

	Memory at 80000000 (64-bit, prefetchable) [size=256M]

	I/O ports at 8110 [size=8]

	Capabilities: <access denied>



00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0

	Memory at 96500000 (64-bit, non-prefetchable) [size=1M]

	Capabilities: <access denied>



00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 16

	I/O ports at 80e0 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 17

	I/O ports at 80c0 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 18

	Memory at 9c804c00 (32-bit, non-prefetchable) [size=1K]

	Capabilities: <access denied>

	Kernel driver in use: ehci_hcd

	Kernel modules: ehci-hcd



00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 22

	Memory at 9c800000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel



00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

	I/O behind bridge: 00007000-00007fff

	Memory behind bridge: 9b800000-9c7fffff

	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0

	I/O behind bridge: 00006000-00006fff

	Memory behind bridge: 9a800000-9b7fffff

	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0

	I/O behind bridge: 00005000-00005fff

	Memory behind bridge: 99700000-9a7fffff

	Prefetchable memory behind bridge: 0000000092400000-00000000933fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0

	I/O behind bridge: 00003000-00004fff

	Memory behind bridge: 98700000-996fffff

	Prefetchable memory behind bridge: 0000000093400000-00000000944fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0

	I/O behind bridge: 00002000-00002fff

	Memory behind bridge: 97600000-986fffff

	Prefetchable memory behind bridge: 0000000094500000-00000000954fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=06, subordinate=08, sec-latency=0

	I/O behind bridge: 00001000-00001fff

	Memory behind bridge: 96600000-975fffff

	Prefetchable memory behind bridge: 0000000095500000-00000000964fffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 20

	I/O ports at 80a0 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 22

	I/O ports at 8080 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at 8060 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 19

	I/O ports at 8040 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: uhci_hcd

	Kernel modules: uhci-hcd



00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0, IRQ 20

	Memory at 9c804800 (32-bit, non-prefetchable) [size=1K]

	Capabilities: <access denied>

	Kernel driver in use: ehci_hcd

	Kernel modules: ehci-hcd



00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32

	Capabilities: <access denied>



00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, medium devsel, latency 0

	Capabilities: <access denied>



00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297

	I/O ports at 8108 [size=8]

	I/O ports at 811c [size=4]

	I/O ports at 8100 [size=8]

	I/O ports at 8118 [size=4]

	I/O ports at 8020 [size=32]

	Memory at 9c804000 (32-bit, non-prefetchable) [size=2K]

	Capabilities: <access denied>

	Kernel driver in use: ahci

	Kernel modules: ahci



00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: medium devsel, IRQ 11

	Memory at 9c805000 (64-bit, non-prefetchable) [size=256]

	I/O ports at 8000 [size=32]

	Kernel modules: i2c-i801



03:00.0 Network controller: Intel Corporation Device 4237

	Subsystem: Intel Corporation Device 1211

	Flags: bus master, fast devsel, latency 0, IRQ 2295

	Memory at 99700000 (64-bit, non-prefetchable) [size=8K]

	Capabilities: <access denied>

	Kernel driver in use: iwlagn

	Kernel modules: iwlagn



04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 2296

	I/O ports at 3000 [size=256]

	Memory at 93410000 (64-bit, prefetchable) [size=4K]

	Memory at 93400000 (64-bit, prefetchable) [size=64K]

	Expansion ROM at 93420000 [disabled] [size=128K]

	Capabilities: <access denied>

	Kernel driver in use: r8169

	Kernel modules: r8169



05:00.0 System peripheral: JMicron Technologies, Inc. Device 2382

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at 97600300 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>

	Kernel driver in use: sdhci-pci

	Kernel modules: sdhci-pci



05:00.2 SD Host controller: JMicron Technologies, Inc. Device 2381 (prog-if 01)

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: fast devsel, IRQ 16

	Memory at 97600200 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>

	Kernel modules: sdhci-pci



05:00.3 System peripheral: JMicron Technologies, Inc. Device 2383

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 11

	Memory at 97600100 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>



05:00.4 System peripheral: JMicron Technologies, Inc. Device 2384

	Subsystem: Hewlett-Packard Company Device 30f7

	Flags: bus master, fast devsel, latency 0, IRQ 11

	Memory at 97600000 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>

---

### Post by dococo on 2008-10-08
Any help on this problem would be greatly appreciated since I have still not found a solution. Or should I post a request in the audio section? Thanks

---

### Post by sunnsi on 2008-10-14
I also met the same problem. My laptop is HP compaq CQ45-124TX.
It will always repeats the last piece of sound.

---

### Post by dococo on 2008-10-14
The only additional reference I can find to this problem is a bug report that seems to be the same issue. see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

There doesn't yet appear to be a resolution yet so I am not sure what to do.

I would hate to have to return to the dark side...!!

---

### Post by sunnsi on 2008-10-17
I have tried Archlinux,  the problem remains. 
So I do not think it is the bug of ubuntu.

---

### Post by dococo on 2008-10-17
I think the problem relates to the alsa drivers. the intel sound card is not supported or requires some alteration to the settings. 

Note, I have also tried OSS sound drivers but this resulted in the sound card not being recognised at all.

Finally I updated Ubuntu today on a standard update and it now no longer recognises my sound card with alsa.

I have not yet found a solution and no one else seems to be posting / replying.

Let me know if you find any solution. Thanks

---

### Post by sunnsi on 2008-10-17
I have updated my alsa driver to the latest version. The problem is the same.
I think the main problem is here:

$ sudo alsactl init
Unknown hardware: "HDA-Intel" "Generic 10de ID 3" "HDA:111d76b2,103c30f7,00100302 HDA:11c11040,103c137e,00100200" "" ""
Hardware is initialized using a guess method

But I do not know how to fix it.

---

### Post by hmarkg on 2008-10-17
I have the audio problems too. My laptop is Compaq Presario Cq45-129TX. There is sound coming from the speakers but the problem is that its very disturbing. Erm I do not know how to discribe it.?? It seem to be repeating itself in a loop non-stop until I mute the volume from the volume control manager myself. Pressing the mute buttom on my laptop does not work at all. 

I have tried downloading software such as Pulseaudio Preferance, Pulseaudio Device chooser and other driver that can be found in the synaptic pakage manager but it didnt solve my problem.

---

### Post by dococo on 2008-10-17
On my Compaq I have the Altec Lansing speaker system. I think we have similar problems. When I boot up I used to hear the drum roll and it would repeat in a sort of echo. I do not get any other sound functionality. However, my mute and volume buttons do work (or used to - see below).  

Since I downloaded the latest Intrepid updates yesterday my sound card is no longer recognised so I seem to have gone backwards. Note I am using Intrepid since the wifi doesn't work with Hardy.

Now the only sound I hear is a beep if I press the wrong key, for example in the terminal.

Like you I have tried various options including pulse and OSS but both seem to make the problem worse. In fact I reinstalled Intrepid at one point to make sure I had cleaned out all the changes I made.

Let me know how you get on.

---

### Post by hmarkg on 2008-10-18
Ya out laptop has the same speakers. Mine is also Altec Lansing. And yes we have the same problem as how you described. I'm still searching how to solve this problem and will update you if i happen to solved it.

---

### Post by dococo on 2008-10-18
Unfortunately I have spent too much time trying to sort this out. I have not found a solution and so have had to revert to Vista. Note that the vista install went really well and the sound quality from the audio is excellent.

Let me know if you find a solution. I would consider moving back to Ubuntu since I have used it for sometime on my old Acer. It is a shame that hardware vendors do so little to support open source.

Good luck and keep me posted.

---

### Post by Alzyme on 2008-10-29
> **dococo said:**
> Unfortunately I have spent too much time trying to sort this out. I have not found a solution and so have had to revert to Vista. Note that the vista install went really well and the sound quality from the audio is excellent.

Let me know if you find a solution. I would consider moving back to Ubuntu since I have used it for sometime on my old Acer. It is a shame that hardware vendors do so little to support open source.

Good luck and keep me posted.Perhaps you could try HP's unofficial BIOS f.11c (try searching for F.11C.rar). It worked for me with Ubuntu 64bit 8.04 and a HP CQ45 series notebook (intel chipset), even XP was able to detect the audio devices instead of reporting them as unknown.

Credit to the Ubuntu OS though, normally I wouldn't expect much support for the latest machines but they seem to be doing very well.

---

### Post by dococo on 2008-10-30
Thanks for the tip. I installed the latest BIOS version F.13 when i installed vista so maybe this would help Ubuntu find the audio system. 

Perhaps a stupid question but would F.13 supercede F.11C? I can find the F.11C.rar file but all the sites are in either chinese or Vietnamese (I think) so I am not sure if I should try this. What I might do is try booting up from the Intrepid install disc and see if the sound is recognised with F.13 since I haven't tried this before.

If you have any thoughts please let me know.

As you say Ubuntu does a great job and I really like the system so would like to come back from the dark side asap!!

---

### Post by Alzyme on 2008-10-31
My thoughts ??? 

I think it's interesting that BIOS f.11c shows that HP could make installing other operating systems easier yet they decided not to do so with f.12 and AFAIK f.13

F.11c origin appears to be around the same time as f.12. Logic would suggest f.11c came before f.12 but I wouldn't be surprised if it were afterwards. As for not feeling comfortable using it, that's understandable, I don't know if there is anything untoward with it and HP are not supporting it.

Yes, most of the f.11c files seem to be on Chinese sites, there appears to be both the windows flasher (Winflash) and the DOS flasher (flashit) packages.

If I had known how closed the HP InsydeH2O BIOS system was I would have probably brought a different brand. Only offering the ICH9M in AHCI configuration and that the EFI BIOS legacy emulation sucks in places is dissapointing for me.

---

### Post by hmarkg on 2008-11-02
Thanks for updating shell try it. And yeah ubuntu is doing very good in terms of support for new machines.
[dococo]:interesting why do you call microsoft the dark side..??

---

### Post by aiview on 2008-11-02
&#32534;&#35793;alsa 1.0.18&#26368;&#26032;&#39537;&#21160;&#65292;&#21487;&#20197;&#35299;&#20915;&#36825;&#20010;&#38382;&#39064;&#21527;&#65311;

&#21442;&#32771; [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by hmarkg on 2008-11-03
How do I update my BIOS from ubuntu... I do not know...

---

### Post by hmarkg on 2008-11-04
I found out this [thread]("http://ubuntuforums.org/showthread.php?t=318789&page=5") and i got stuck until the part when ciscosurfer's instruction (In thread #1) asked to copy the flashing tool and the new BIOS file to /mnt/temp. I got an error message saying that the file is too big for the FDOEM.144 file directory. 
Alzyme could you show me how did you did it on your computer, since we have almost the same laptop... Thanks in advance...

---

### Post by Alzyme on 2008-11-08
> **hmarkg said:**
>  Alzyme could you show me how did you did it on your computer, since we have almost the same laptop... Thanks in advance...Answered [[color=blue]**_here_**[/color]]("http://ubuntuforums.org/showpost.php?p=6133093&postcount=49")

---

### Post by hmarkg on 2008-11-09
Hey Alzyme... No problem for the late reply... I find that people in this forum are very helpful just like a big family XD...

---

### Post by hmarkg on 2008-11-11
Alzyme I've just update my BIOS to HP F.13 Bios but i didnt seem to solve my audio problem in ubuntu 8.10 (64-bit) :(

Even F.12 didnt worked...!!! :(

---

### Post by hmarkg on 2008-11-16
So what do I do now...???

---

### Post by Alzyme on 2008-11-16
Only f.11c works for the audio at this time, have you tried it? 

But remember it's an unofficial release so HP may refuse to accept your warranty if you use it.

---

### Post by hmarkg on 2008-11-17
> Only f.11c works for the audio at this time, have you tried it? 

But remember it's an unofficial release so HP may refuse to accept your warranty if you use it.  

I have downloaded it but i do not know how to install it. I've just installed vista to update my bios.

---

### Post by Alzyme on 2008-11-18
> **hmarkg said:**
> I have downloaded it but i do not know how to install it. I've just installed vista to update my bios.
Which one did you download? 
There is a DOS version that uses flash.bat and a windows version that uses winflash.bat.

To use the DOS version you just need to boot into real DOS and run **flash.bat**, use a free HD partition or bootable usb flash drive. You can backup your BIOS easily with this by ```
flashit.exe mybackup.fd /g
```

To use the windows version run **winflash.bat** with administrator privileges, here is a link to a windows version [[color=blue]_Winflash_[/color]](http://bbs.benber.com/attachment.php?aid=9039).

Be careful to let the windows one run its course and not have any unnecessary programs running while flashing.

---

### Post by hmarkg on 2008-11-19
> Which one did you download?

I downloaded from the link you gave on this [post ]("http://ubuntuforums.org/showpost.php?p=6133093&postcount=49"). 

> To use the windows version run winflash.bat with administrator privileges, here is a link to a windows version Winflash.


I've also tried the latest link you gave but it seem to have problem everytime I extract the files. help...:confused:

---

### Post by Alzyme on 2008-11-19
What sort of problem? If it's a problem extracting the archive and your downloading with vista perhaps you could download a freeware program called Tugzip to extract the files.

IMHO though using a DOS bootable usb pen drive with the first download you did and running file flash.bat is probably safer.

If you want use the DOS method maybe this [color=blue]_[http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive](http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive)_[/color] will help.

BTW f.14 is out, I have not tried it but as regards the audio device problem I'm not expecting it to be any different from f.04 f.12 & f.13.

---

### Post by hmarkg on 2008-11-19
> What sort of problem? If it's a problem extracting the archive and your downloading with vista perhaps you could download a freeware program called Tugzip to extract the files.
 

The problem is not the unzipping part is the downlaoding part. It will not finish downloading everytime.

> BTW f.14 is out, I have not tried it but as regards the audio device problem I'm not expecting it to be any different from f.04 f.12 & f.13. 

I have tried it yesterday. Its the same, still having problem with the sound.

---

### Post by hmarkg on 2008-11-20
Weeehuuuu..... Guess what.... Wakakaka... I just manage to download and "downgrade" my BIOS to F.11C and walah... Got sound already.... Thanks thanks...

---

### Post by Alzyme on 2008-11-20
IIRC you may need to play with the mixer as the volume slider seems not to be synchronized to the master volume control but one of the other volume controls, at least in 8.04 anyways. No big deal though really.

---

### Post by hmarkg on 2008-11-20
> IIRC you may need to play with the mixer as the volume slider seems not to be synchronized to the master volume control but one of the other volume controls, at least in 8.04 anyways. No big deal though really.

Mine seem to be able to synchronized with the master volume.

---

### Post by Bikkne on 2009-01-18
I've bought a Compaq Presario CQ45 102TU, and I installed Kubuntu 9.04 Jaunty Alpha 2 on it.  I had no sound and the speaker button was red. The fix that people had for Intrepid 
adding "options snd-hda-intel enable_msi=1" 
at the end didn't work here, because it seems like the Ubuntu team already added it... I looked around and found an undocumented solution on a suse forum. 
In the: "/etc/modprobe.d/alsa-base"
I added: "options snd-hda-intel model=hp-m4" 
before "options snd-hda-intel enable_msi=1", and now everything works.
As they said on that forum, that "hp-m4" was nowhere to be found in the Alsa documentation though, there was a "dell-m4" which I tried earlier, it made the speaker symbol lighten up but there was no sound.

Hope this can help anybody with similar problem.  (if I remember right they also suggested "hp-m6" which I haven't tried coz "it just worked" :))

(The system has been working smooth, got the new openoffice.org working by "only use openoffice dialogs" only thing left now is waiting for the updates xserver 1.6 and Mesa 7.3 for the Intel Graphics and the MySql update to 5.1 so it utilizes the same as Amarok, )

---

### Post by andresFang on 2009-03-02
Hi all of you, i'm on a CQ45-115 LA , i used to have no sound on my ubuntu intrepid ibex, but i read this post and fix it, now i have sound

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

works perfectly, just follow the instructions

---

### Post by csbonito on 2009-03-03
> **andresFang said:**
> Hi all of you, i'm on a CQ45-115 LA , i used to have no sound on my ubuntu intrepid ibex, but i read this post and fix it, now i have sound

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

works perfectly, just follow the instructions



hello  andresFang
I have a CQ45-118 LA 
i was wondering what model did you put instead of hp-dv5 to get sound, cus i have the same problem, no sound on speakers and only on the headphones

I wish you could help me with some instructions here

In any case thank you for your help

---

### Post by utkatt on 2009-04-11
i've just entered the line below in file /etc/modprobe.d/alsa-base

options snd-hda-intel enable_msi=1.

It worked for me. hope it works for everyone else.

Thanks

---

### Post by dhruvasagar on 2009-05-12
I edit my /etc/modprobe.d/sound file and put this :

```
options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel
```

This sorted out my audio problems. I noted that model=dell-m4-1 worked equally well instead of the model=dell-m4-2 as shown above.

Hope that helps you.

---

### Post by dhruvasagar on 2009-05-12
I also went to System->Preferences->Sound and selected ALSA Advanced Linux Sound Architecture for all and HDA STI SB as the default mixer

---

