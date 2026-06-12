---
title: "[SOLVED] Can´t run Ubunt-8.04.1"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2008-08-24
I´ve been using Linspire/Freespire for more than 5 years.:) I want to try Ubuntu and I can´t make it run.

The live CD works fine, but when I install it I have problems with the monitor resolution. Subsequently, when I restart the computer, and I choose Freespire in another partition, I can´t make it run either.:confused:

Does someone know what happens?

Thanks in advance!:)

Terraman

---

### Post by akudewan on 2008-08-24
> **Terraman said:**
> I´ve been using Linspire/Freespire for more than 5 years.:) I want to try Ubuntu and I can´t make it run.

The live CD works fine, but when I install it I have problems with the monitor resolution. Subsequently, when I restart the computer, and I choose Freespire in another partition, I can´t make it run either.:confused:

Does someone know what happens?

Thanks in advance!:)

Terraman

What kind of errors are you getting, in both cases ? Is it just the monitor resolution in Ubuntu ?

---

### Post by Ehtetur on 2008-08-24
Hi Terraman and welcome to Ubuntu! :twisted:

You didn't mention the type graphics card in your PC...
There are sticky posts at the top of [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") that give you a step-by-step for setting up ATI or nVidia cards...

Also, as you just installed Ubuntu, you may want to check for any updates.. (there a quite a few)
> sudo apt-get update
Good Luck!

Ehtetur

---

### Post by Terraman on 2008-08-24
> **akudewan said:**
> What kind of errors are you getting, in both cases ? Is it just the monitor resolution in Ubuntu ?

Aparently, it´s just a monitor resolution in Ubuntu, but it´s in a very low resolution, which I can harly see, and it´s divided in four horizontal screens.:(

In Freespire, after a long command secuences, which normally don´t appear, the OS doesn´t start.:(

Thank you!

---

### Post by Terraman on 2008-08-24
> **Ehtetur said:**
> Hi Terraman and welcome to Ubuntu! :twisted:

You didn't mention the type graphics card in your PC...
There are sticky posts at the top of [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") that give you a step-by-step for setting up ATI or nVidia cards...

Also, as you just installed Ubuntu, you may want to check for any updates.. (there a quite a few)

Good Luck!

Ehtetur

Thank you Ehtetur,

I´ve updated it. I´ll check the graphic card and let you know.:)

---

### Post by Terraman on 2008-08-24
> **Ehtetur said:**
> Hi Terraman and welcome to Ubuntu! :twisted:

You didn't mention the type graphics card in your PC...
There are sticky posts at the top of [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") that give you a step-by-step for setting up ATI or nVidia cards...

Also, as you just installed Ubuntu, you may want to check for any updates.. (there a quite a few)

Good Luck!

Ehtetur
Graphic card: OpenChrome

---

### Post by kagashe on 2008-08-24
> **Terraman said:**
> Graphic card: OpenChrome[URL="https://help.ubuntu.com/community/OpenChrome"]Ubuntu documentation for OpenChrome.
[/URL]

After going through the document I think it does not apply to Ubuntu Hardy.

Try using vesa driver first so that the installed system works.

kagashe

---

### Post by Terraman on 2008-08-24
Thank you Kagashe,

Despite the fact that I´ve been using Linux for several years I´m not very clean on this OS. Thus, I don´t know how can I make your suggestion work. Please, let me know more details.

Terraman

---

### Post by forger on 2008-08-24
1) Is it an LCD monitor? Do you use a DVI or VGA output?
From some users I helped seems that using an LCD monitor with a DVI to VGA **adaptor** gives a better resolution
2) > Graphic card: OpenChrome
Isn't this the driver name? What is the brand/model of the graphics card?
3) The subject of this post is not right, you can run it, but the monitor resolution isn't correct :)

---

### Post by forger on 2008-08-24
To get some more info about your graphics card, execute the following commands in menu Applications > Accessories > Terminal:
```
sudo lshw -class display
sudo lspci
```

Reply with the full output

---

### Post by Terraman on 2008-08-24
Thank you Forger,

1) It's an LCD monitor an LG L1550S model
2) I don't know the driver's name nor the brand model of the graphic card
3) Maybe your right, it isn't well posted.

Here's the full output:

lshw -class display
-su: lshw: command not found

lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

Terraman

---

### Post by kagashe on 2008-08-25
> **Terraman said:**
> 
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

TerramanThere is a bug in Ubuntu Hardy for your card. You can read about it [here]("https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-video-openchrome/+bug/244413").

You need to add the line
> Driver "openchrome"
in the device section of xorg.conf file. The section should read:
> Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection


open the file to edit through the following command:
> gksudo gedit /etc/X11/xorg.conf

kagashe

---

### Post by Terraman on 2008-08-25
Thank you folks!

Finally it works!

Terraman

---

