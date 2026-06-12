---
title: "Installation freezes during Network card detection"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by Wintermute on 2005-07-30
Hi all. 

I'm quite new to linux, I've only tried a Mdk 10.1 for few months; now I was going to try Ubuntu 5.04.

But I've got a problem that didn't let me install Ubuntu at all..

When the installation program starts to search for my network card it freezes and I'm forced to cut off the energy.

My hardware config is:

MB ECS k7s5a
amd athlon xp 2000+
640mb  RAM
HD maxtor 60Gb
HD maxtor 200Gb
Dvd burner DVD dual layer LG
Dvd player DVD LG 48x
Ati radeon 9600xt 128mb
ieee 1394 pci card
Integrated sound card (the one with the ac'97 drivers..)
_Network card Ethernet 3com based on 3C905TX _

I have to say that with WinXp my card works great, also with Mdk 10.1

And why the hell does the installation program freeze!!! It shouln't. Maybe it should tell me that something is wrong...I don't like to cut off energy...

Tahnks for any help...  :smile:

Add on:

I saw few seconds ago on [this page](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28network%29%7C%28cards%29) that maybe my net card is not supported by Ubuntu!!! 

Do I have to get a new card???!!!!  [-X

---

### Post by Wintermute on 2005-07-30
Can anyone help me???

I was thinkin about unplug my network card and try to install ubuntu... maybe once it's installed I could find a way to make the card work...

Also, my dsl modem works both with ethernet or usb connection...

Is there a way to use a usb modem with Ubuntu?

Waiting for help!!!!!!!!!!!  ](*,)

---

### Post by tdjokic on 2005-07-31
> I was thinkin about unplug my network card I don't have much experience with Ubuntu, but it must be a way to do quoted action w/o physically unpluging. Look here and you will get an idea [http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)  . Is there something like that in Ubuntu?

---

### Post by Wintermute on 2005-07-31
Maybe should it be this?  netcfg/disable_dhcp=true

I found it in the help section of the installation program...

I even tried it but it still freezes!!!!!!!!!!!!

I'm seriousely thinking about try a different distro... Mdk worked great with hardware detection... but it is too big for my tastes...

Help still needed...  ](*,)

---

### Post by heimo on 2005-07-31
So it's 3c509, Etherlink III, ISA-bus card? It's definitely supported, so if you can unconnect it for now and then install goes through cleanly, you could probably put it back / configure network afterwards and do some package upgrading (which would be otherwise done automaticly). That's what I'd try.

 There's probably a way around this, using some parameters for that device, maybe using expert mode in install - or something like that, but I'd just take it off and install offline. At least that way you can make sure that hangup is caused by network card / autodetecting it.

Is that a viable plan?

---

### Post by Wintermute on 2005-07-31
[QUOTE=heimo]So it's 3c509, Etherlink III, ISA-bus card? It's definitely supported, so if you can unconnect it for now and then install goes through cleanly, you could probably put it back / configure network afterwards and do some package upgrading (which would be otherwise done automaticly). That's what I'd try.

 There's probably a way around this, using some parameters for that device, maybe using expert mode in install - or something like that, but I'd just take it off and install offline. At least that way you can make sure that hangup is caused by network card / autodetecting it.

Is that a viable plan?[/QUOTE]

Thank u heimo... I think that's what I'm going to try....
BTW my net card is not what u say but an ethernet 3com 905tx pci card (chipset is 3c905tx).

But I have to add that I found out I've got some problems also in WinXp, and I'm thinkin it's a IRQ problem... my net card is detected by Xp but it only works if I plugin in the pci slots another card, that it could be anything, a dialup modem, another net card (that doesn't work at all). Also in the same IRQ (11) is present my ieeee1394 pci card!! If I leave the 3com card alone it doesn't work!! The system seems to be unable to start the card!! Ps. never had problems with Mdk..

I'm going crazy!!!  ](*,)

---

### Post by heimo on 2005-07-31
Sounds like p'n'p / irq related problem, but can't be sure. I'd probably try putting cards in different slots and tweaking related BIOS settings (looking at the screen at the very beginning of boot / POST for IRQs). Nowadays IRQs can be shared, but sometimes it can cause conflicts. Don't really know what's happening here.

Oh.. these 3com card names... 509, 905... If I'm not mistaken, kernel module is 3c59x. modinfo 3c59x:
 ```
description:	3Com 3c59x/3c9xx ethernet driver LK1.1.19 10 Nov 2002

``` 

It should be easy one - should work very well and require no manual settings. My hunch is that when you get hardware conflict (?) sorted out (possibly using BIOS settings), this card will work flawlessly. It should also be easy to install beforehand, but if you can see at the very beginning of boot that this card and some other device share resources, try to make it not to. (use Pause|Break key to halt that screen, if it goes by too fast).

---

### Post by Wintermute on 2005-08-03
Hi again... 

I installed Ubuntu, it was net card blame! I unplugged the net cards and Ubuntu got installed!

Now I'm trying to make work the card under Ubuntu...

I plugged in the card and start Ubuntu; a card was detected cause I can see it in the 
configuration panel.

I configured the card but it doesn't work..

Then I re-opened the configuration panel to try some changes but Ubuntu freezed!!

i had to cut off the energy...!!!  ](*,) 

Then reboot.... it stops and freezes on "hotplug" during booting.... What the.....!!!!!!!!!!! 

help if u can....

---

### Post by heimo on 2005-08-03
Read /var/log/messages, search any errors or text string  3c59x

You could probably disable hotplug temporarily (chmod a-x /etc/init.d/hotplug), so you can boot with card attached, and then open two terminals - on the other, you run tail -f /var/log/messages and on the second: modprobe 3c59x

Does it freeze? Do you get any errors on the first terminal?

EDIT: 3c905 -> 3c59x

Possible solutions: disable ipv6, load module at early stage of boot
(details later, if neccessary) May be related:
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=107389]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=107389")

```

sudo gedit /etc/modprobe.d/aliases
change 
alias net-pf-10 ipv6
to
alias net-pf-10 off

```

Put 3c59x on its own line in the beginning of file /etc/modules

---

### Post by Wintermute on 2005-08-03
Thank u heimo!!  :razz: 

I'll try soon and let u know...

Greetings from Italy!  :lol:

---

### Post by heimo on 2005-08-03
[QUOTE=Wintermute]Thank u heimo!!  :razz: 

I'll try soon and let u know...

Greetings from Italy!  :lol:[/QUOTE]

Thanks! Hopefully you get at least some new information and these changes won't make your system unusable. It's always a small possibility, so it could be nice if you have a Live CD - Ubuntu or Knoppix available. Not neccessary, but a good "insurance" anyway.

I edited my previous post, added some details, changed chmod u-x to chmod a-x

Let us know how you're doing. It's a bit mysterious problem, network cards are usually very easy to setup.

---

