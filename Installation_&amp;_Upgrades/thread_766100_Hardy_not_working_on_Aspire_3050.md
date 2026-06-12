---
title: "Hardy not working on Aspire 3050"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by lambdacore on 2008-04-25
hey HAI.

i sadly have an Acer Aspire 3050 laptop.
Gutsy wasn't going very well on that computer (and i checked around, it seems it was like that for everybody) with stuff like wireless not working and sound buggy.

anyway. when i saw that Hardy was in alpha, i tried downloading it and installing it. but, upon choosing "installation" from the boot menu, the orange bar would load to about 25% and freeze there. for hours. i tried leaving it on all night. nothing happens, just freezes. it wouldn't work by upgrading through the manager either. it downloaded, had fun with the packages then reboot. and it wouldn't work.

then i saw the beta and tried. same thing.

i was full of hope for the release.

of course it does the same. i just can't install it on my damned laptop and it makes me really really sad.

anyone have the same issue?
or have any idea?
or maybe have beer? hmm, beer.

thanks :D

---

### Post by lambdacore on 2008-04-25
holy moley.

---

### Post by lambdacore on 2008-04-25
oh well.

---

### Post by bumz714 on 2008-04-29
I have an Acer Aspire 5050-3786 and I too tried installing Hardy Alpha and Beta. I thought it was the CD media, thought it was the ISO, but now I think it might have to do with kernel 2.6.24-16.

I was able to install Hardy, but kernel 2.6.24-16 refuses to activate swap and fails to load Synaptics Touchpad. If I start Hardy with kernel 2.6.22-14 it loads fine.

I'm not sure, still a noob myself.

---

### Post by gamma-ray-burst on 2008-05-12
anything new?
it really really annoys me not to be able to install it.

---

### Post by Darkchef on 2008-05-14
yeah id like to have an official fix for this , has this been submitted to launchpad?

---

### Post by roadrocket13 on 2008-05-21
as of 5-19-08 the official Hardy release LiveCD was used to install to an Acer Aspire 3050, though wireless is non-functioning at the moment. any tips on that would be appreciated.

---

### Post by clb137 on 2008-05-21
> **roadrocket13 said:**
> as of 5-19-08 the official Hardy release LiveCD was used to install to an Acer Aspire 3050, though wireless is non-functioning at the moment. any tips on that would be appreciated.

what wirless  card do you have.  use lspci nd post the results to me, i am running ok with an acer 3690.

clint

---

### Post by mini_g on 2008-05-23
> **clb137 said:**
> what wirless  card do you have.  use lspci nd post the results to me, i am running ok with an acer 3690.

clint

Name: RaLink RT2500 802.11g Cardbus/mini-PCI 
ID: 09:00.0 0280: 1814:0201 (rev 01)

---

### Post by clb137 on 2008-05-26
> **mini_g said:**
> Name: RaLink RT2500 802.11g Cardbus/mini-PCI 
ID: 09:00.0 0280: 1814:0201 (rev 01)


Sorry thought you had a broadcom wireless, as far as aware your card should be ok, i will do some digging for you,you could try "ear media" its based on heron and everything works out of the box, inclluding all media its a very good distro, 

check [www.distrowatch.com](www.distrowatch.com) you can get a link

or

[http://www.earos.dk/](http://www.earos.dk/)

have fun

clint

---

### Post by clb137 on 2008-05-26
hi,

You could also try this 

[http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500](http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500)

Clint

---

### Post by mini_g on 2008-05-27
](*,)](*,)](*,)](*,)

I accidently submitted my ASUS' wireless card ID...  :oops:

Here's my lspci -n without it inserted:
```
00:00.0 0600: 1002:5950 (rev 10)
00:01.0 0604: 1002:5a3f
00:04.0 0604: 1002:5a36
00:05.0 0604: 1002:5a37
00:06.0 0604: 1002:5a38
00:07.0 0604: 1002:5a39
00:12.0 0101: 1002:4379 (rev 80)
00:13.0 0c03: 1002:4374 (rev 80)
00:13.1 0c03: 1002:4375 (rev 80)
00:13.2 0c03: 1002:4373 (rev 80)
00:14.0 0c05: 1002:4372 (rev 83)
00:14.1 0101: 1002:4376 (rev 80)
00:14.2 0403: 1002:437b (rev 01)
00:14.3 0601: 1002:4377 (rev 80)
00:14.4 0604: 1002:4371 (rev 80)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5975
**02:00.0 0200: 168c:001c (rev 01)**
08:01.0 0607: 1524:1412 (rev 10)
08:01.1 0501: 1524:0530 (rev 01)
08:01.2 0805: 1524:0550 (rev 01)
08:01.3 0501: 1524:0520 (rev 01)
08:01.4 0501: 1524:0551 (rev 01)
08:02.0 0200: 10ec:8139 (rev 10)
```

I believe that it's "02:00.0 0200: 168c:001c (rev 01)" (*Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)*)

The restricted driver manager said that the driver is enabled for this device, however it still is not working.

I found that the 3050 is apparently supported under the 2.6.25 kernel under *acer-wmi*, however there is a patch from [here]("http://code.google.com/p/aceracpi/") *(Note: At this time, the site that is hosting the Ubuntu patch is currently down, however the source code is still on there.  I have yet to try to install it though.)* that can be applied to enable the functionality of most everything that Acer has placed into many of their notebooks.

---

### Post by clb137 on 2008-05-27
hi,

a couple more for you to try

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

or download [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)

then

sudo make
sudo make install
sudo modprobe ath_pci

if you use 7.10 "blacklist ath5k"

be sure build-essentials installed

clint

---

### Post by roadrocket13 on 2008-06-05
it has been suggested that Ubuntu sometimes misidentifies the wireless card in use, especially Atheros cards.
regardless, lspci output yields;

```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
**02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

the instructions detailed in this particular thread solved my issue with respect to wireless;

Post #7 on this thread
[http://ubuntuforums.org/showthread.php?p=4790652](http://ubuntuforums.org/showthread.php?p=4790652)


working on sound next. anybody have any luck?

---

### Post by mini_g on 2008-06-06
> **roadrocket13 said:**
> 
working on sound next. anybody have any luck?

Thanks for the help on the wireless issue.  I'll see how it helps upon reboot.

The sound issue is easy though.

I have the Volume Control working with the HDA ATI SB (Alsa).  Sound is by default able to be received by the front audio jacks on the Aspire 3050, but to be able to get speaker audio, the surround sound needs to be unmuted.  When it is unmuted, the front audio jack does not trip the auto-mute ability when a device is inserted.  It just needs to be remuted.

Also, all of the outputs of audio are sent via ALSA as the default audio server.  Pulseaudio is too finicky with this system to be of use.

---

### Post by Stupid_newbie on 2008-06-12
I had the same problem to the original Question of not bieng able to install on Acer 3050


What I did was went to the Acer website (Canadian website) and downloaded BIOS updator for Windows VISTA.  (I was still running xp at the time)

[http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=3981&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17](http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=3981&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17)

I ran it..and once it updated my BIOS i was able to install Ubuntu 8.4

I hope this helps anyone with a 3050

---

### Post by lambdacore on 2008-06-24
Hey hi.

I did as Stupid_newbie said, updating the BIOS with the given link, and it worked wonderfully.

Thanks a whole bunch to that guy :D

So if you have the same problem as I had, just update your BIOS and Hardy will install without any trouble.

Hell yeah.

---

### Post by InTheShires on 2008-07-28
I've also got the Acer 3050, and I'm having the same problem, and I've been trying for days now to get this sorted and I'm at the end of my tether.

Like the OP, trying to install from the disc is impossible. 

Prior to updating my bios I was getting a message about wrong driver, and to use "8139too" instead. The only way around this, (for me) was to load Windows on, and choose the "help me boot the CD" option in the install options. However, once Ubuntu was installed I couldn't install any updates from the CD because it wouldn't mount the CD via Synaptics. (Despite the CD being accessable from the desktop)

So, after much hair pulling, I updated the BIOS via the Acer FTP, which includes newer bios updates than they show in their driver update section. (I needed to do this anyway for Windows, as it wasn't setting aside the correct amount of VGA RAM)

So, updated the bios, (solved the VRAM issue) but now upon trying to install Ubuntu, I get nowhere fast. 

It hangs on the Orange bar, about 20-25%, and goes no further. (Seems to stop reading CD, but I know sweet FA!) 

My Acer 3050 has the Broadcom wifi chip. 

Please help, and be gentle with me, 'cos I'm no expert, but am willing to try!

---

### Post by InTheShires on 2008-07-29
Just to add to my above post, I have also tried the bios that was posted above, and it doesn't help me. Nor does using the latest v3.15 version on the Acer ftp.

I have also tried the EarOS distro mentioned above somewhere, and that gives me the very same problem. (Stops on Busybox screen, and just sits showing [initramfs] or whatever it may be.)

I'll keep checking back in the hope somebody will shed some light on this for me. 

Regards.

ITS

---

### Post by InTheShires on 2008-07-30
Never mind. Got there in the end. A search on here for 8139too, initramfs and busybox showed me the fix I needed. 

By pressing F6 during the bootscreen install procedure and typing the following allowed me to install HH. (v8.4.1)

```
all_generic_ide floppy=off irqpoll
```

---

### Post by InTheShires on 2008-09-30
Sorry for bringing this old thread back back up, but re my post above regarding the "all_generic_ide floppy=off irqpoll" work around to get Ubuntu installed on my laptop.

Basically, now Ubuntu is installed and been happily running for a good few months, I was wondering if I can speed up the boot time now, as adding that fix above really slows the boot time up quite considerably. (2mins +, of which is mostly taken up with that fix, once the Ubuntu splash screen starts, it's boots in a sensible time.) 

Do I still need this line added now, or would it be safe to remove it?

If it's safe to delete it, and still get it booting up properly, how and what do I need to do?

Or, should I just accept this "bug" as it seems to not like my laptop's BIOS, and live with the boot time?

Hope this makes sense!

Regards, ITS.

---

### Post by InTheShires on 2008-10-03
Bump. (Sorry)

---

### Post by govi on 2008-10-09
I have the same laptop and had the same issue, but I almost solve all the problems. your trouble is the bios, just flash the bios to ver. 1.3302 and then you be fine.Find the bios from the acer website. I just downgrade the bios to that version and I don't have any trouble. after the installation, run update and upgrade, then just enable the restricted devices and restart the laptop, then you will not have any issue with the vga and wireless. except the sound.

---

### Post by InTheShires on 2008-10-17
Ok, thanks for that.

I've put that BIOS on, but now how do I edit out that line of code I had inserted originally, because it's still there so it's still taking an age to boot up.

Surely I wouldn't have re-install the O/S again?

---

### Post by InTheShires on 2008-10-19
Bump, bump. (Sorry)

---

