---
title: "Advice on Computer Setup"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Shibby73 on 2008-01-09
Hello... 

One of the things that really got me hooked on Ubuntu and causing me to chat it up among people I meet (when talking about computers) is the fact that when I first tried it as a live CD with 6.06 a year ago... it JUST WORKED!!   I am fairly computer illiterate but many others think I know what I am doing... I am just willing to try new things and try to learn about them.

Well... one computer that was a paperweight was an old PC that I own - I think it had WIN98 or something horrid on it... it would not start up and would lag... however I did add on a wireless network card (D-Link) a while ago.  With Ubuntu 6.06 I somehow managed to get it to connect.  Since then I have reformatted it's harddrive and put on a clean install of Ubuntu 7.10

Well... I don't have access to the internet now!?

I would like to get this old computer running Ubuntu and accessing the internet... I'm willing to put in whatever PC card it may need, and purchase a new wired/wireless router as needed. Recently I got a NETGEAR wireless switch... so I can actually share a laptop's EVDO internet connection at home when coupled with my present Belkin Pre-N router (although I am having some issues with accessing the Router's set-up at 196.168.2.1 or whatever the address is).

One annoying thing with going to Linux... you need 2 computers!!  You also need reliable internet access... not really complaining, I am able to always get to the internet on my laptop (which keeps me from going beyond dual booting until I get something new I guess).

So not being able to get to the internet on this old desktop PC is a bit troubling...
Unrelated... I recently got an external monitor for my laptop (22") and Ubuntu doesn't appear to like it much... but that is a different install... a different computer, and fun for another day.

Here's my lshw output (of note a long time ago I did use DSL... and I think I put an ethernet card in this computer... it unfortunately doesn't work however with my wired router) to share this with the forum I had to use a spare USB stick, and save it in Open Office and go to my other computer:

 > 
~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 639MB
     *-cpu
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.4.2
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci:0
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: d8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon RV200 QW [Radeon 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d0000000-d7ffffff ioport:c000-c0ff iomemory:dd000000-dd00ffff irq:10
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d000-d00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: SAMSUNG SV4002H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: PLEXTOR CD-R PX-W1210A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 697MB
                   capabilities: packet
              *-cdrom:1
                   product: CREATIVE DVD-ROM DVD1241E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@00:07.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:dc00-dcff ioport:e000-e003 ioport:e400-e403 irq:10
        *-usb:2
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 41
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:de013000-de013fff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9.1
             bus info: pci@00:09.1
             version: 41
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:de010000-de010fff irq:10
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 9.2
             bus info: pci@00:09.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:de011000-de0110ff irq:10
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: U3 Cruzer Micro
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@4:1
                   version: 0.10
                   serial: 00001675C6735213
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=200mA speed=480.0MB/s
        *-network UNCLAIMED
             description: Network controller
             product: ACX 100 22Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: d
             bus info: pci@00:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:ec00-ec1f iomemory:de012000-de012fff iomemory:de000000-de00ffff irq:11
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:07.4
          version: 40
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage


OK this is long so my questions are:

1) Should I bother with this hardware?
2) Should I  take out the wireless card &  get a new one?
3) Should I take out the "nonfunctional" internet card & get a new one?
4) Should I get a new router?

I am thinking perhaps I should just fork up money and get a new computer and junk this one (but save the hard drive as a back-up), get a new router, and make sure I have wired and wireless access on the new computer and run Ubuntu on it off one of the hard drives.  New PCs are going to have VISTA... (usually) so that is a whole new can of worms... I mean you don't throw away an operating system easily in my mind... LOL... and I am having a hard time throwing away this paper weight - earlier I was using it to play livestream music though... so with internet and ubuntu it was working for something.

Thank you for your advice, this work is not vital... I'm just monkeying around and thinking about cleaning house a bit if I can't get this thing to work.

~Shibby73~

---

### Post by Partyboi2 on 2008-01-09
If you are wanting a hobby, have some spare time, and want to save some cash then why not see what you can make your paper weight into?
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)
Buying another nic is normally only a couple of dollars,  but depending on your setup is it  needed?
As for the router, if it works then why buy a new one?
The hardware, does it preform to what you are wanting to use the pc for?

---

### Post by Kevbert on 2008-01-09
Your wireless card is probably the problem.  If you can pick up a wireless adapter based on the Ralink RT2561 or RT61 you should be able to get onto the internet.  I had a Belkin wireless card which was based on the Broadcom BCM4306 chipset and it was impossible to configure (stay away from Broadcom based cards as they are hard to configure.
My router is a Netgear DG834GT.

---

### Post by Gina on 2008-01-09
I have a Netgear DG834GT too - love it :)  Regarding Broadcom bcm43xx chipsets, I have one of those in my laptop.  It was easy to get working with Gutsy using the Restricted Drivers Manager to download and install the firmware.  Just a few mouse clicks.  Other wireless adapters using RaLink chipsets have been a problem though I did get a Belkin PCI card with RT2500 working after asking for advice here in the Wireless forum.

---

### Post by ugm6hr on 2008-01-09
If the acx driver doesn't work with Network Manager, maybe try Wicd (see link below).

Also - the acx driver does not support WPA - if your wifi is WPA, try ndiswrapper.

---

### Post by oldsoundguy on 2008-01-09
I have D-Link 520 wireless cards in two Gutsy boxes and both worked right out of the install when I used the system> administration> network>  and highlighted the wireless card.  Then I shut OFF the the enable roaming in the properties and then did the specifications including the password (auto DHCP).

I am also using a D-Link DI-624 router plugged into a Motorola Surfboard cable modem. (I also have one Gutsy box hard wired along with a separate XP box  .. plus another XP box wireless and on a KVM+audio setup with one of the wireless Gutsy boxes.

---

### Post by Craigus on 2008-01-09
D-Link 520's use the prism chipset. This is well supported and should work out of the box.

Shibby73 has an acx100 based card that will work with the default driver, but not with WPA. It may also be necessary to disable Network Manager, as discussed here:

[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu")

As ugm6hr says, the only solution that works with acx devices and WPA at the moment is to use ndiswrapper. That isn't particularly difficult to set up.

---

### Post by Shibby73 on 2008-01-09
> **Craigus said:**
> D-Link 520's use the prism chipset. This is well supported and should work out of the box.

Shibby73 has an acx100 based card that will work with the default driver, but not with WPA. It may also be necessary to disable Network Manager, as discussed here:

[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu")

As ugm6hr says, the only solution that works with acx devices and WPA at the moment is to use ndiswrapper. That isn't particularly difficult to set up.


Thank you guys.
Per this link:[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118539](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118539)

It appears if I just update to the latest version of Gutsy, then this problem will be fixed?
Otherwise it is all those steps on the wiki pages you directed me to?

I'd like a CD to work that gets internet access so I can make fixes on the machine as needed.
This copy+paste business between machines is for monkeys (grin).

A likely related issue: my Belkin router directs me on how to reset to factory defaults (which I did), it supports WEP and WPA security... so I'll have to run without the WPA I guess.

However the instructions direct me to enter the router's set-up webpage by directing my browser to 192.168.2.1 (without the http).  Now I know I had trouble doing this once before, and I don't remember what the fix was... but my stupid browsers keep adding the http:// and I can't get into the router's set-up!  I have looked through Opera and MSIE's options to disable this and can't seem to find the right setting... anyone else have a clue what I might be doing wrong?

Thanks,

~Shibby73~

I'm going to go ahead and reburn an ISO and reinstall Gutsy for now and hope someone has a response for getting into my router.  Next step will be to just ditch this poorly supported equipment... any recommendations?  I'd love to be smart enough to just fix this with a few patches, but without internet access it is less of a pain to just upgrade hardware and the kernal and not have to worry about this in the future.

---

### Post by Craigus on 2008-01-09
> browsers keep adding the http://

That shouldn't matter at all. I think the problem lies elsewhere.

How are you connected to the router ? Can you browse the internet on the machine that is trying to access the router ? What happens if you ping 192.168.2.1 ?

---

### Post by slolerner on 2008-01-09
i just loaded wicd.. ndiswrapper. the install rem'd my network manager. wired connection works, but still no joy with the wireless.

who needs to know what to help me get this compaq presario c508us working wirelessly?

probly something simple, but i haven't played long enough to find it. any help would be appreciated.

---

### Post by Shibby73 on 2008-01-09
> **Partyboi2 said:**
> If you are wanting a hobby, have some spare time, and want to save some cash then why not see what you can make your paper weight into?
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)
Buying another nic is normally only a couple of dollars,  but depending on your setup is it  needed?
As for the router, if it works then why buy a new one?
The hardware, does it preform to what you are wanting to use the pc for?

1) As far as spare time for this as a hobby... that is limited
2) Saving cash and making this "paper weight" usable is desirable, I am willing to spend some money to do this, and it would be a great box to learn on perhaps.  Of course, new computers would cost more and I could perhaps learn more useful things on a better back-up machine.
3) The Wireless card WAS working at one time, and severa; complicating variables exist to sort this out.
     a) It worked with Ubuntu 6.06 and I have since upgraded.
     b) I stopped my comcast cable since then and lost internet access at my place
     c) My router set-up has been reset to factory defaults and I can't get into it's set-up using 192.168.2.1 (either that just isn't working, or I can't seem to get the browsers to stop putting in the http:// all the time or searching the internet for the address)
     d) I am using my only working PC - a 4 year old laptop (dual booting to WinXP and UbuntuStudio), I can access the internet using an EVDO card on this machine... I can use my Netgear switch and my Belkin router (using the Ethernet cable) and share this connection successfully with my XBOX360... I should be able to share the wireless with my router if I can get it to work again (assuming I can access the set-up webpage). The D-Link wireless card in the old PC doesn't support all of the security features of the router, but I can use the lower grade security.
    e) There are now 17 different wireless signals around my appartment (likely making a secure router important, and channel selecting important... I don't think the factory settings will work with my router out of the box).
   f) Gutsy doesn't seem to support my card out of the box, I don't even see any of the other wireless routers since upgrading with a live CD and I reformatted the old PC HDD.
4) Possibly a new router and a new network card (for ethernet cable connectivity if not a WPA/WEP capable wireless card or combination) would solve these problems?  The router is a Belkin Pre-NF5D8230-4 and I am sure something better exists by now, probably something more Linux compatible?  Since I know the XBOX connects using the existing router and NETGEAR GS105 Switch... likely having a wired card in the old PC would work without replacing the wireless router.
5) Hardware performance... it isn't the latest.. I don't play games on it, or play many games for that matter... I would use it for internet access... as a back-up computer... web stream news, TV, radio... perhaps do some website stuff (access my Firstclass server [www.stansgnosticus.net](www.stansgnosticus.net)) and it could do most of this... I would love to be able to do Video streaming better and not have it hang up... it is old, it is not top of the line... don't think that matters that much though.
6) Hardware that I want and would be useful would be really something for what I do for a living... I am a resident physician and will be starting a Fellowship in July... I would love a Tablet PC (most electronic medical records can have remote access... so far where I am now that means I am stuck with WINXP for access using a Citrix/Juniper networks security protocol run over MSIE browser interface to run their applications... not sure what the situation will be for me starting in July... and frankly I don't have $3000 to buy the computer that would be most useful to me - if it truly exists.)
7) My overall goal and "hobby" if I have one would be less messing around with this old box and more  to explore power mobile computing solutions... I'd love to make Ubuntu the solution if that is possible... doubt handwriting recognition on a slate computer running Ubuntu would compare to Windows OneNote... but I have been surprised by a program in WINXP called RITEPEN. I know this because I have a windowsXP USB device that is a tablet and battery operated pen that permits writing... it isn't a mobile solution but gives the functionality of a pen-enabled computer I think similar to a WACOM device (but it only cost me <$30).  
8) I run UbuntuStudio on my current laptop... I am afraid to upgrade it to Gutsy because this is my primary machine... if I could upgrade a computer that I didn't mind wiping the HDD on as needed... then perhaps I could mess around with trying to see what Pen-enabled solutions exist in Linux.

Overall goal.... pen-enabled computing in Linux on a mobile computer like a SLATE Tablet PC... that is my hobby and goal.

Back to the post...
I looked at this wiki referenced above... appears to me that my card ought to work, it also appears that network manager is not installed and the directions for disabling it did not work.  I looked at the posts from that wiki related to the problem and bug report... perhaps a new Gutsy download will create a CD that will work with my present card.  If so... I should be able to atleast see my BELKIN router, but probably won't be able to actually connect through it.  That would make me happier and I would focus on trying to set up the belkin router.  Not sure how to get around the 192.168.2.1 problem however.  So if a new Gutsy install appears to fix the issue, then I'll try a new router if I can't fix the one I have... but if I'm at the store... I'll be tempted to just get a network card to plug in an ethernet cable instead and just be done with it since I don't ahve to worry about wireless access problems, dropped connections and slow speeds via the netgear switch+router combination.

Then I can focus on the other tasks at hand.

Will keep you posted.  Any tips for this router's issue would be great, and any more detailed instructions about getting this wireless card to actually find the router would be great too. 
I would love to be able to tell about how Ubuntu resurrected my junker PC... but I am much more pragmatic and don't mind spending a little to save me precious time and give me MORE FUN! :-)


~Shibby73~

"What I lack in knowledge and experience, I make up for with creativity and enthusiasm!"

---

### Post by Shibby73 on 2008-01-09
> **Craigus said:**
> That shouldn't matter at all. I think the problem lies elsewhere.

How are you connected to the router ? Can you browse the internet on the machine that is trying to access the router ? What happens if you ping 192.168.2.1 ?

I suspect the problem is somewhere else too. "Usually when this sort of thing has come up in the past it has always been attributable to...  human error." - HAL in 2001

Ok... I am connecting via my present laptop to the internet using an EVDO card right now.
I am sharing this internet connection and have an ethernet cable going from my laptop to my BLEKIN router.  I have tried accessing the card with and without being connected to the internet via the EVDO... no go.  I would hope the auto http thing doesn't matter, but my instructions explicitly state NOT to type that... can't seem to get around it from doing this.  I did note that if I type the wrong number by accident I immediately get an access denied error instead of a failure to connect type of error.

I ran some command (I'm in WINXP for convenience right now) and ran CMD and then IPCONFIG
States my thernet adapter local area connection is IP 192.168.0.1 with subnet mask 255.255.255.0 with no default gateway.

I am also seeing my PPP adapter with the Sprint Mobile Broadband - Pantech with a different IP address and a similar subnet mask that ends with .255 instead of .0
The default gateway matches my IP address, and there is no connection-specific DNS Suffix.

I have the router connected directly to this laptop so I'm not going through the switch to keep things simpler (since I know nothing about networking).

I will ping the IP address of the Ethernet Adapter and it's settings address (which is different 192.168.2.1): Pinging the IP address of the Adapter gets a quick reply.
Pinging the setup address times out 3 times.

Does this information help or confuse you (because I am totally confused about why it would not work)?

Thanks,

~Shibby73

---

### Post by Craigus on 2008-01-09
> States my thernet adapter local area connection is IP 192.168.0.1 with subnet mask 255.255.255.0 with no default gateway.

If that's the case, then I would expect your router to have an IP address 192.168.0.x

try numbers like 0, 100, 128, 255 for x .

---

### Post by Shibby73 on 2008-01-09
I just remembered something... a while back I was messing around and wanted to install a program called WAMPS??? I think that is what it was called, basically it put on Apache and MySQL and I think Python... it made my computer work like it's own server... stuff I shouldn't be playing around with given my attention span and lack of knowledge and help.

Could this be somehow messing me up?
I thought it was just related to "localhost" so that I could access files on my machine as if it was the internet... but I may be totally wrong.  It doesn't appear to be running right now... but I may have fubar'd something doing that install?

Please advise.

Thank you,

~Shibby73~

"A smart quote here won't obfuscate the above demonstration of my idiocy."

---

### Post by Shibby73 on 2008-01-09
> **Craigus said:**
> If that's the case, then I would expect your router to have an IP address 192.168.0.x

try numbers like 0, 100, 128, 255 for x .


Hmmm... that makes no sense to me... the set-up in the Belkin is fixed at 192.168.2.1 not any of the rest.... when I type in the 192.168.0.1 I get forbidden access.

Trying:
192.168.0.x and using 0-255 either gives me immediate forbidden access (1) or appears to time out as well.

?? weird

~shibby73

---

### Post by ugm6hr on 2008-01-10
Sorry - I'm getting a bit confused with all the unconnected posts....

To summarize (please confirm if I am correct):
You want to use WEP security.
You want to keep your existing wifi card (acx chipset).
You *may* get a wired ethernet (LAN) card.

Now for the advice....

The reason the router's setup page doesn't load is that you are not connected to it yet.

Seeing as how you have reset your router anyway - just reset it again.  Most routers default to non-secured.  Some have a default setting where you cannot access the setup page without a wired connection (Netgear specifically - not sure about Belkin).

Ensure you reinstall Ubuntu (so that the remnants of whatever else you have done are not going to interfere).

Then try Network Manager (click on the icon and see if it "sees" your wifi or any others).  If it sees others but not yours - then your router is probably broken, since most routers default to broadcasting their SSID to allow all users to see it.  If it sees your wifi - just select it and see if it connects, then try the 192.168.2.1 address if Firefox.  If it sees nothing, then NM is probably the culprit (assuming your acx card is working).

If the last (NM suspected), just open Terminal and see what comes out of the following command:
```
iwlist scan
```

This should manually list all networks (bypassing NM).  Hopefully this should now list your wifi.  If it does - connect maually with this series of commands (replace *interface* with wlan0 and put your *SSID*):
```
sudo ifconfig *interface* down
sudo dhclient -r *interface*
sudo ifconfig *interface* up
sudo iwconfig *interface* essid "*SSID*S"
sudo iwconfig *interface* mode Managed
sudo dhclient *interface*
```

Taken from kevdog's advice ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188))

This should at least allow you to connect to 192.168.2.1.  If this works - try wicd for a long term solution.

> If that's the case, then I would expect your router to have an IP address 192.168.0.x

This command will clear things up *once you are connected to your router*
```
route -n
```

---

### Post by Shibby73 on 2008-01-11
sorry about the broken posts... was replying to the other questions.

I do not care if I use WEP security right now... ideally yes... my connection should be as secure as possible and certainly as secure or more secure than a WINDOWS OS... sadly that may not be possible with my present hardware.

I managed to fix my router and got connected to the internet using the wireless set-up... I eventually got into my router's set-up screen... and I removed the Ubuntu 7.10 variable by using an Ubuntu 6.06 Live CD with the old pc.

So for me this is now an OS issue.  

The Ubuntu 7.10 distribution for some reason is not as good at the 6.06 for my wireless device.

This looks like a ridiculous task to get connected with a NEWER version.

Frankly,  the Ubuntu distributions will not be able to survive if people like me can't simply put in a LIVE CD and have access to the internet to download patches and find help on a working computer.

I don't have the luxury of time to pursue fixing UBUNTU on this computer, so if I can't do it simply then I'll just erase my 7.10 install andrun the 6.06 until a distro is made that addresses this with a live CD and new install.

Thank you for your help, this looks like good information.

Time permitting, before I do pursue the re-install again I'll see how far I can go with getting the Ubuntu 7.10 to connect to the internet using my wireless and WORKING router.

IMHO 7.10 is a distribution that is simply not ready for prime time.

Best regards,

~Shibby73~

---

### Post by Shibby73 on 2008-01-11
> **ugm6hr said:**
> Sorry - I'm getting a bit confused with all the unconnected posts....

To summarize (please confirm if I am correct):
You want to use WEP security.
You want to keep your existing wifi card (acx chipset).
You *may* get a wired ethernet (LAN) card.

Now for the advice....

The reason the router's setup page doesn't load is that you are not connected to it yet.

Seeing as how you have reset your router anyway - just reset it again.  Most routers default to non-secured.  Some have a default setting where you cannot access the setup page without a wired connection (Netgear specifically - not sure about Belkin).

Ensure you reinstall Ubuntu (so that the remnants of whatever else you have done are not going to interfere).

Then try Network Manager (click on the icon and see if it "sees" your wifi or any others).  If it sees others but not yours - then your router is probably broken, since most routers default to broadcasting their SSID to allow all users to see it.  If it sees your wifi - just select it and see if it connects, then try the 192.168.2.1 address if Firefox.  If it sees nothing, then NM is probably the culprit (assuming your acx card is working).

If the last (NM suspected), just open Terminal and see what comes out of the following command:
```
iwlist scan
```

This should manually list all networks (bypassing NM).  Hopefully this should now list your wifi.  If it does - connect maually with this series of commands (replace *interface* with wlan0 and put your *SSID*):
```
sudo ifconfig *interface* down
sudo dhclient -r *interface*
sudo ifconfig *interface* up
sudo iwconfig *interface* essid "*SSID*S"
sudo iwconfig *interface* mode Managed
sudo dhclient *interface*
```

Taken from kevdog's advice ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188))

This should at least allow you to connect to 192.168.2.1.  If this works - try wicd for a long term solution.



This command will clear things up *once you are connected to your router*
```
route -n
```


iwlist scan did not work.
I'm going to bed now... will check later this weekend to see if anyone has a simple way to get back my network manager.  I just don't comprehend why this is an issue when an earlier version worked fine out of the box.  After this weekend, I'll just install 6.06 since it works and aside from updating to a new OS more easily in later distros... I don't see any advantage to running 7.10 aside from it being "newer."
This is going to make it hard to recommend the latest distribution to others less patient than me.

~Shibby73~

---

