---
title: "Huawei E620 - does it work in lucid yet?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bumanie on 2010-04-14
Really want to use lucid on my laptop, but up to Beta 2, cannot get Huawei E620 usb modem to work. Has anyone got one of these working in lucid? With Beta 2, network manager didn't even recognise the device. I tried the modeswitch program, but that made no difference.
I am thinking about downloading the daily build with a later kernel than Beta 2 has got; has the later kernel made a difference to anyone with this device? This modem works fine on 9.04, but won't work on 9.10 or lucid up to this point.

---

### Post by philinux on 2010-04-14
> **bumanie said:**
> Really want to use lucid on my laptop, but up to Beta 2, cannot get Huawei E620 usb modem to work. Has anyone got one of these working in lucid? With Beta 2, network manager didn't even recognise the device. I tried the modeswitch program, but that made no difference.
I am thinking about downloading the daily build with a later kernel than Beta 2 has got; has the later kernel made a difference to anyone with this device? This modem works fine on 9.04, but won't work on 9.10 or lucid up to this point.

Hi,

Seen this somewhere lol.

Try installing usb-modeswitch. Have a read of the description from synaptic.

---

### Post by bumanie on 2010-04-14
Thanks Phil, but I tried that and it made no difference. It mounts as a storage device although lsusb lists it as the correct usb-modem - it's quite odd that 9.04 connects it without a problem, but 10.04 won't even recognise it in network manager even when added via 'edit'. It's really disappointing not to be able to use the latest ubuntu with mobile broadband.

---

### Post by philinux on 2010-04-14
> **bumanie said:**
> Thanks Phil, but I tried that and it made no difference. It mounts as a storage device although lsusb lists it as the correct usb-modem - it's quite odd that 9.04 connects it without a problem, but 10.04 won't even recognise it in network manager even when added via 'edit'. It's really disappointing not to be able to use the latest ubuntu with mobile broadband.

Is there a bug report? If you search huawei on this forum you'll find you're not alone. Shame it dont work.

---

### Post by bumanie on 2010-04-14
There are a number of bug reports - was just hoping the latest kernel may have fixed the problem. I'm on limited downloads at present and thus wanted to know if the latest kernel had made a difference before I used precious bandwidth to get a daily build - would do it if the modem works, but if it doesn't, I don't want to 'waste' the download.

---

### Post by philinux on 2010-04-14
> **bumanie said:**
> There are a number of bug reports - was just hoping the latest kernel may have fixed the problem. I'm on limited downloads at present and thus wanted to know if the latest kernel had made a difference before I used precious bandwidth to get a daily build - would do it if the modem works, but if it doesn't, I don't want to 'waste' the download.

Just a thought have you tried it with wicd instead of network manager? Also there is a fix committed on this bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Have you seen this page?

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

---

### Post by -humanaut- on 2010-04-14
I concur with trying Wicd seems to smooth out the problems of "networkmanager"

---

### Post by bumanie on 2010-04-14
No I haven't. Do you think that would work? Guess I give it a go.

---

### Post by philinux on 2010-04-14
> **bumanie said:**
> No I haven't. Do you think that would work? Guess I give it a go.

Very small download. Fingers crossed.

---

### Post by bumanie on 2010-04-14
Tried wvdial and wicd - but end up with dependency issues. I'll see if I can download the dependencies and transfer them to lucid - it really should not be this problematic.

---

### Post by bumanie on 2010-04-14
I give up - every dependency I download, wants another - too much trouble. I'll just keep using 9.04 on my laptop.

---

### Post by bumanie on 2010-04-16
There seems to be an issue with a number of Huawei devices in 10.04 and it has been sent to upstream kernel developers to try and find a fix. Crossing fingers that a fix is found before final release!

---

### Post by solitaire on 2010-04-16
I'm having a problem like this with my E156G dongle.

[http://ubuntuforums.org/showthread.php?t=1455802](http://ubuntuforums.org/showthread.php?t=1455802)

It's stuck at a USB flash drive,
I've installed usb_modeswitch and that does not see the device.
(the dongle works in 9.10 and Win7 I tested it last night).

---

### Post by keithpeter on 2010-04-18
> **bumanie said:**
> There seems to be an issue with a number of Huawei devices in 10.04 and it has been sent to upstream kernel developers to try and find a fix. Crossing fingers that a fix is found before final release!

Especially since this is a long term support release. I've just walked into this one myself.

---

### Post by blackest_knight on 2010-04-22
hi 

I use an E620 with 9.10 with no issues 


however ubuntu-10.04-beta2-netbook-i386.iso which i downloaded last night
recognises  huawaei but not that its a modem. I raised this issue months ago and was hoping it might have been fixed. 

The E620 is the standard contract modem in Ireland for Three 

This is a critical bug.

---

### Post by philinux on 2010-04-22
> **blackest_knight said:**
> hi 

I use an E620 with 9.10 with no issues 


however ubuntu-10.04-beta2-netbook-i386.iso which i downloaded last night
recognises  huawaei but not that its a modem. I raised this issue months ago and was hoping it might have been fixed. 

The E620 is the standard contract modem in Ireland for Three 

This is a critical bug.

Stick with 9.10. Meanwhile click the affects me. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

### Post by blackest_knight on 2010-04-23
well after banging my head against a brickwall all day everything i tried has failed i tried the latest kernel build (no more than 4 days old at the latest) with lucid and lost the ability to use my E156 modem as well.

currently connected with the E620 in one USB Port and a PNY usb stick with unetbootin and a 9.10 desktop version.

The vodafone option cant be installed because of dependency issues in Lucid.
Gnome2-extra or something it's been split into smaller packages and it gets sticky rapidly.

i'm going to have to sit this mess out I can't really continue with a contract modem which is unusable under lucid.

---

### Post by bumanie on 2010-04-25
I still can't get a connection with the E620 - these are very common devices. If Canonical/ubuntu/linux wants to be seen as an alternative to the other two major OSes, this needs to be fixed, especially as lucid is a LTS release. My last download was RC release with the latest (at that point) kernel.

---

### Post by blackest_knight on 2010-04-25
yes it works now :) on the live CD (usb created with unetbootin

but not quite out of the box 
digging around i found a couple of posts 
I downloaded the following 2 deb files 
saved them to a micro sd card in the modem 
and booted of a usb stick with 10.04rc i386 iso.

usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb


sudo modprobe option


I initially tried the sudo modprobe option but seemed to have no effect.
then i installed 
usb-modeswitch-data with gdebi and followed up with usb-modeswitch

at this point lsusb still showed pid of 1046 on removing and reinserting the modem the modem was correctly recognized and after setting up a gsm profile i was able to connect and write this post. 

of course this probably will be lost after rebooting being a live cd and i have to take the next step and install to my ssd (again)

hopefully this will work for other people.

---

### Post by owise1 on 2010-04-26
I have the E620 - vodafone and had it working with 9.10 using the "drivers" from [www.betavine.net](www.betavine.net).  Installed the netbook version of 10.04 beta2 and used exactly the same process and all works via network manager.

Cheers

Dave

---

### Post by clhsharky on 2010-04-26
HI 

If your trying Lucid and have wifi problems try a newer kernel first before moving back to previous release. .34.rc5 is very stable and a lot more wifi friendly. You do know that where the drivers are.

Sharky

---

### Post by bumanie on 2010-04-26
Thanks to blackest_knight and others at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547"), this is finally solved. 
Download these 2 .debs
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb
install them and then setup your gsm modem via 'edit connections'. In my case, I also had to disable CHAP in configure settings under ppp settings.

Thanks again to all who helped solve this for the many E620 users.

Now I can update!

---

### Post by alexfish on 2010-04-26
Hi
 

 pleased you got the modem working,  
 

 as regards the usb modeswitch,
 

 however this may present a problem to other devices , these could be ones that are recocognised by the kernel, I have a both zte and a huawie devices ,if the modeswitch {the intergrated package} is installed then I am  presented with what you describe in the first post, as it resets the device to be seen as storage and not seen as the modem
 

 anyone presented with this problem could try Sakis 3g as it only implements modeswitching if the device has not been switched IE the usb mode_switch is included
 

 [http://ubuntuforums.org/showthread.php?t=1331660](http://ubuntuforums.org/showthread.php?t=1331660)
 

regards 


alexfish

---

### Post by bumanie on 2010-04-26
alexfish - that is useful information that may be helpful to some. Some of this 3g stuff is becoming a bit of a nightmare due to the nature of the files pre-installed on the devices so that they will work on windows - pity someone doesn't provide linux only modems - guess the market is too small. Any way, one can always be happy that the linux community comes up with work-arounds for these issues. Again, thanks to all who helped.

---

### Post by alexfish on 2010-04-26
your not half right there with that one,

unless the Network Manager keeps up then there could be further problems ahead, 

one good thing about Sakis3g it overcomes a few of the major issues surrounding getting the device recognised, and also the options to use wvdial or direct with the ppp , most notable when you can configure the device in NM but can't connect, so then you have to resort to wvdial or gnome ppp

As regards Developing and Programming is concerned this is a script file and well worth reading , as it is possible a step in the righ direction

Regards

alexfish

---

### Post by StuartN on 2010-04-26
> **bumanie said:**
> Thanks again to all who helped solve this for the many E620 users.

Is it still necessary to either have the modem inserted before bootup or to run usb_modeswitch from the commandline? Or is the modem now correctly detected if you plug it in during a session?

---

