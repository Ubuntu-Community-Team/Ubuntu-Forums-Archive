---
title: "Where is /etc/pcmcia/config or equiv?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by SteveConley on 2007-01-20
I am new to Unbuntu - but have used Redhat, Knoppix, and others for several years.
This is the first 2.6 kernel I have tried - in fact that is why I tried Unbuntu.

I have a PCMLM56 modem/ethernet card in a Pii233 laptop.

In Redhat 9 this card "worked" fine.

In other versions of Linux (kernel 2.4) - I edited /etc/pcmcia/config to force it not to load the modem part  of this card.

I can no longer find this file in Ubuntu.

When booting I get the message: "Yenta no PCI IRQ, Cardbus ..."

I have attempted the following boot parameters:
APIC=off
noapic
with no effect.

IRQPOLL actually get it to boot with the card working, but in a few minutes of using it the machine locks hard - and must be powered off. I have repeated that multiple times.

Any idea where I can edit whatever file now contains the decsription for the cards now?

I have been looking around the internet for two days and have attempted to find it in the documentation, but documentation seems to point to 2.4 versions.

It also appears that lots of people have this problem - but I see few solutions - and the ones I have tried don't seem to work.

Thanks.

---

### Post by gborzi on 2007-01-20
The configurations file for pcmcia is /etc/default/pcmcia. I don't know what kind of configuration can be made on RedHat through /etc/pcmcia/config, so I'm not sure if the above mentioned file will be useful.

---

### Post by SteveConley on 2007-01-20
Actually that is also part of the problem - there is no /etc/default/pcmcia

The config file used to have all the descriptions of all the cards with "bind" statements, etc.
I have seen this file also on Debian 2.4 kernels.
So I am lost as to where it has disappeared to.
A "find" on the system turned up nothing.

config.opts only has memory and io include/exclusion areas.

I noticed that I did not explicitly state that this is Ubuntu 6.10.

The laptop happens to be a Clevo 8900M (rather old pii233 with 256MB and a 40GB HD).
Laptop works great though and has a 15" screen - so I was recycling it hopefully with a newer version of Linux.

---

### Post by gborzi on 2007-01-20
I have checked my system (I'm using 6.10 too on my laptop), the /etc/default/pcmcia file is created during the installation of the pcmcia-cs package. Is this package installed in your system ?

---

### Post by SteveConley on 2007-01-20
Yes, it is installed - pccardctl shows the card identifier too.

I am genrating a new kernel 2.6.19 and checking that out to see if it solves any of the issues.

The messages I have seen on the various forums are non-deterministic.

I also have the "repeating" key problem and I hoping that will get solved too (quite annoying).

I will post results of the kernel update  - but I still haven't been able to figure out where the card identifications are.

---

### Post by gborzi on 2007-01-21
The configuration file can be created with the command > sudo dpkg-reconfigure pcmcia-cs
you can try it and look for error messages. BTW, my /etc/default/pcmcia file is > # Defaults for PCMCIA (sourced by /etc/init.d/pcmcia)
PCMCIA=yes
PCIC=yenta_socket
PCIC_OPTS=
CORE_OPTS=
CARDMGR_OPTS=
# If REFRAIN_FROM_IFUP is set to yes, cardmgr will not bring up
# network interfaces. They should be brought up by hotplug instead.
REFRAIN_FROM_IFUP=yes
Hope this helps.

---

### Post by SteveConley on 2007-01-22
I have installed 2.6.19.2 and it looks a lot better. (It took about 9 hours to gen on the laptop itself).

Repeated and lost characters from keyboard have gone down from about 1 in 20 to probably 1 in 1000.

The Linksys PCMCIA card is correctly installed on boot. And the net comes up.

I still have the "Process for the file protocol died unexpectedly" - but this has appeared to be benign.

still no /etc/default/pcmcia - but apparently with 2.6 it is not needed - although I still want to know where the device database is ...

Next trick will be getting the USB connected Linksys WUSB54G wireless up.

---

### Post by SteveConley on 2007-01-22
BTW, gborzi, apparently pcmcia-cs is NOT installed.

Apparently it is not needed for 2.6 ??

I assumed it was installed because the card was getting mounted and in, infact worked somewhat in 2.6.17-10 if IRQPOLL was on.

I have been doing a lot of reading and it seems that 2.6 uses a cardbus controller instead?

The various notes are very ambiguous and most of the doc pointed to by the various 2.6 kernel implementations actually hasn't been re-written since 2.4.

But nowhere in the "cardbus" info have I foudn the card database either.

---

### Post by gborzi on 2007-01-22
Hello, the description of the pcmcia-cs package says >  This package is replaced by pcmciautils when running on newer
 kernels. If you only run kernels version 2.6.13 or later, this
 package can be safely removed.
The pcmciautils package can read a configuration file in /etc/default, but there isn't any such file on my system. There is an howto in the documentation, under /usr/share/doc/pcmciautils.

---

