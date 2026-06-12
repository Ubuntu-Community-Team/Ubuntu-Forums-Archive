---
title: "New in the field of linux world."
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Emperor_penguin on 2010-08-17
Hello to evryone):P, after many hacked versions of windows 7 i had to put out, i decided to use Ubuntu 10.04

As i'm very new in the Linux world, i'd like to say thanks to everyone that has the patience to explain certain doubts i might have.
:confused:
I'm about to install Ubuntu 10.04 lucid lynx 64 bits on my system,however i have some worries i'd like to share with everyone reading this.:guitar:

I'm very upset with Itunes company, i love using my ipod with the correct album arts in it, unfortunately i know there is no itunes for linux, there are some other programs to be used instead, which i have try amarok,gtkpod and rhythmbox without really success. The only programs that seems to work is gtkpod,but it's very odd it's use and i cant really enjoy playing music there.

From here, can i ask, Would be worth use Virtual box using either w7 or win xp for just the peace of mind? in others words, just use windows as a virtual boz just for being able to use itunes.
I have read that usb functions are hard to come by if you are using virtual pc? Is there any truth in there?:---)

2nd and last, i like linux net security and stability, however, i like playing Stalker Clear sky and Stalker Shadow of Chernobyl(booth on them on steam not retail cd):-#

I have been reading a lot of using steam with wine, also with Stalker-shadow of chernobyl seemed that worked, however, the clear sky edition, did not work? I havent tested it myself, so i cant really say either of them will work under wine?:-s

I thought to use virtual pc for playing the stalkers games, plus the itunes, too bad to know that the speeds i might be getting arent really fast and furthemore, i wont be taking full power of my ATI 3850 series at all, since virtual pc, emulates windows, not like wine that actually runs it translating to linux kernel operation. Before i forget, should i install the none open source drivers from ati or just use the open drivers from linux and then install the ati drivers for linux?[-o<

Summing up everything, what guys reckon i should use for itunes and for STALKER games?
Wine?Virtual pc? QEMU? or just install in other partition windows?(which i would rather not do
Thanks again for any help given, and a my regards to the developers of Ubuntu arround the world,:rolleyes: Microsoft time is running out! LINUX FOR HUMAN BEINGS!
Emperor Penguin.

---

### Post by pastalavista on 2010-08-17
I would recommend that you not use iTunes and not play games as both are time wasters. You only have so many days on this earth. Try learning something useful.

---

### Post by lechien73 on 2010-08-17
Welcome to Ubuntu, first of all :)

I don't know too much about gaming, but iTunes doesn't work properly under Wine - and versions of iTunes after 9.1 don't play happily in VirtualBox either (unless your processor has VT-x/AMD-v extensions).

Unfortunately IOS4 on my iPhone requires iTunes 9.2 or later, so I run it under VMWare Player. It's free to download from VMWare's site and seems to work ok.

---

### Post by Emperor_penguin on 2010-08-17
> **pastalavista said:**
> I would recommend that you not use iTunes and not play games as both are time wasters. You only have so many days on this earth. Try learning something useful.

If i dont use itunes or any program related to it, how come i'll be able to use my ipod?

Regarding Playing, your're right, but i play only when i really can do it.;)

Thanks either way

---

### Post by Emperor_penguin on 2010-08-17
> **lechien73 said:**
> Welcome to Ubuntu, first of all :)

I don't know too much about gaming, but iTunes doesn't work properly under Wine - and versions of iTunes after 9.1 don't play happily in VirtualBox either (unless your processor has VT-x/AMD-v extensions).

Unfortunately IOS4 on my iPhone requires iTunes 9.2 or later, so I run it under VMWare Player. It's free to download from VMWare's site and seems to work ok.

G'day mate:lolflag:

Thank you for welcome me, It's a really pain using wine with itunes, i have almost brake apart my current ubuntu 10.04 i just installed on my laptop, it took me 2 hours to clean up the mess of trying to use it.

Regarding the visualization, my it's a core 2 E8600( 3.3GHz) i reckon has the vt-x you are talking about.

cheers.

---

### Post by lechien73 on 2010-08-17
Yes, it does indeed: [http://ark.intel.com/Product.aspx?id=35605](http://ark.intel.com/Product.aspx?id=35605)

So you may be ok with VirtualBox and iTunes.

I had directed people towards PlayOnLinux here: [http://www.playonlinux.com](http://www.playonlinux.com) before. You may find some useful information there.

Enjoy the ride, anyway. I got rid of Windows some time ago and started using Ubuntu as my primary O/S, and I haven't looked back :)

---

### Post by Emperor_penguin on 2010-08-17
> **lechien73 said:**
> Yes, it does indeed: [http://ark.intel.com/Product.aspx?id=35605](http://ark.intel.com/Product.aspx?id=35605)

So you may be ok with VirtualBox and iTunes.

I had directed people towards PlayOnLinux here: [http://www.playonlinux.com](http://www.playonlinux.com) before. You may find some useful information there.

Enjoy the ride, anyway. I got rid of Windows some time ago and started using Ubuntu as my primary O/S, and I haven't looked back :)

Playonlinux.. i read some info about it, for what i can see in their web site, seems to run better than wine itself, this is due of integration into linux registry. I saw somewhere a way of using stalker games(with steam) using playonlinux, you had to download th dx9 and dx10. Would try it.:p

Regarding itunes, have you got any tutorial of how to enable usb functions using virtual pc? or qemu? Then install itunes itself and hopefully, brownse through you music, connect your ipod and sync your library? Seems complicated to do:confused:

I'm really trying to "enjoy the ride" with linux, im sick of windows and it's rogue programs, it's cracked versions, darn virus/spam and their damm rootkits, which can affect linux to, so my advice to evryone is to use Chkrootkit or rkhunter.

cheers.

---

### Post by lechien73 on 2010-08-17
You can download the latest VirtualBox from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

After installing your guest operating system, you will be able to download iTunes. You can access the USB devices by selecting them from the **Devices > USB** popup menu. If you're only going to be using your iDevice with VirtualBox, then you can create a USB filter so that it is always available to the guest, rather than having to go to the Devices menu every time.

If you run into problems with VirtualBox, then try installing your guest operating system on VMWare Player instead.

It's not that complicated - I've been synchronising iPhones on guest operating systems through VirtualBox for quite some time now :)

---

### Post by Emperor_penguin on 2010-08-17
> **lechien73 said:**
> You can download the latest VirtualBox from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

After installing your guest operating system, you will be able to download iTunes. You can access the USB devices by selecting them from the **Devices > USB** popup menu. If you're only going to be using your iDevice with VirtualBox, then you can create a USB filter so that it is always available to the guest, rather than having to go to the Devices menu every time.

If you run into problems with VirtualBox, then try installing your guest operating system on VMWare Player instead.

It's not that complicated - I've been synchronising iPhones on guest operating systems through VirtualBox for quite some time now :)

Quite right, i'll get running asap. In th mid time, do you have any information about a "how to do" regarding the virtual box install, use of itunes, sync and the usb filter thing, which i have had no idea that exist!:?:
Much obliged lechien73, your help is very appreciated.

Would post asap i've done all these things.

thank you!:D

---

### Post by lechien73 on 2010-08-17
It's quite straightforward, really:

[LIST]
[*]Download VirtualBox from the link I gave you.
[*]Install it by double-clicking on the downloaded file.
[*]In VirtualBox click on New to create a new VM, and follow the prompts. I've given mine 512Mb RAM, and created a new 40Gb dynamically expanding hard disk.
[*]I also changed the settings so that the network card was bridged rather than NAT.
[*]Plug in your iPod and, in the VirtualBox manager, go to Settings > USB.
[*]Click the icon with the green + sign and then click on your iPod from the list. This will create a new USB filter for when you install Windows.
[*]Unplug the iPod, then boot the new guest from a Windows CD and install Windows.
[*]After installation, start-up the Windows guest, and install the VirtualBox extensions, so that you can use Windows in full-screen mode.
[*]Then connect to the Internet, download and install iTunes.
[*]Plug back in your iPod and you should now be able to synchronise.
[*]If the iPod isn't detected by Windows, then open the little pop-up menu at the bottom of the screen, click Devices > USB and make sure there's a check-mark next to your iPod. If not, click on it again.
[/LIST]

The major work is in installing. After that, it's fairly easy to use.

---

