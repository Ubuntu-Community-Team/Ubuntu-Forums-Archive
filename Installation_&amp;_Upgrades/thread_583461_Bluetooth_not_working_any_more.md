---
title: "Bluetooth not working any more"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by MickS on 2007-10-20
Upgraded from feisty last night and after solving a few minor snags everything works except my bluetooth. I can send stuff to my phone OK but not from the phone to the PC any idea what to do.
I am running Kubuntu if that helps and just to reiterate it worked fine with feisty, the only change is the upgrade to gutsy. 
TIA

Mick

---

### Post by Calavera07 on 2007-10-21
Same problem for me.

I have two computers (desktop and laptop) and a USB bluetooth dongle. I configured the desktop computer (not the laptop) for bluetooth in Feisty, and worked well. After updating both computers to Gutsy, the laptop works ok (can see bluetooth devices, send and receive files in Gnome, etc). 

The desktop one, after upgrading,  can send files by commandline (gnome-obex-send), but not from nautilus. It is not "visible" for other devices, the "explore devices" menu in gnome is empty. In "bluetooth preferences" the adapter name is allways empty, and the options for operation mode are all greyed out.

I suspect that having bluetooth configured in feisty has ruined bluetooth in Gutsy...

Any idea?

---

### Post by cogitordi on 2007-10-21
It's not just with the upgrade. I did a fresh installation on two computers to replace Feisty Fawn instances in which Bluetooth was working. Under Gibbon, Bluetooth doesn't work. Nautilus>SendTo has no Bluetooth entry.

---

### Post by MickS on 2007-10-21
That's a relief at least I'm not alone, hope some one comes along with a fix soon.

Mick

---

### Post by _Zardoz_ on 2007-10-22
Same problem here.

Ubuntu 7.10 upgraded from 7.04, Gnome.

---

### Post by 3-U-ser on 2007-10-24
It's easy: just install the **gnome-bluetooth** package, which is needed to make bluetooth appear in the dropdown menu. ;)

---

### Post by _Zardoz_ on 2007-10-24
> **3-U-ser said:**
> It's easy: just install the **gnome-bluetooth** package, which is needed to make bluetooth appear in the dropdown menu. ;)

Just said bluetooth's file _receiving_ function doesn't work _anymore,_ that means it worked before upgrade. Of course gnome-bluetooth it's already installed for this reason, almost on my system.

---

### Post by McTek on 2007-10-24
Be sure to delete the "other" program, can't remember name but it had blue in the title.I used synaptic to uninstall it. Then reboot and install Gnomebluetooth. I used apt-get install.

---

### Post by cogitordi on 2007-10-25
> **3-U-ser said:**
> It's easy: just install the **gnome-bluetooth** package, which is needed to make bluetooth appear in the dropdown menu. ;)

Yes, this worked for me. But what's the rest of this Bluetooth functionality, then? It doesn't do anything that a user expects or needs it to do.

---

### Post by vegardh on 2007-10-26
I had to install:
Applications -> Add/Remove -> Bluetooth File Sharing

and start it.

---

### Post by rahimveron on 2007-10-26
Same here, though i can send file to my SE T610 mobile but when i want to send file from mobile to pc the name of the PC is not shown on my Mobile Menu.
Both are paired ok. When i go to my Bluetooth option on my mobie menu it show my PC's name, but when i want to send something from my mobile to pc then the PC's name is not shown in the list of paired devices.

---

### Post by MickS on 2007-10-26
> **vegardh said:**
> I had to install:
Applications -> Add/Remove -> Bluetooth File Sharing

and start it.

I've got that but it still doesn't work in Kubuntu, haven't tried it in Gnome yet because I want to get it working in Kubuntu.

Mick

---

### Post by MickS on 2007-10-26
> **rahimveron said:**
> Same here, though i can send file to my SE T610 mobile but when i want to send file from mobile to pc the name of the PC is not shown on my Mobile Menu.
Both are paired ok. When i go to my Bluetooth option on my mobie menu it show my PC's name, but when i want to send something from my mobile to pc then the PC's name is not shown in the list of paired devices.

Mines the same except the phone does show the PC, if I remove the trusted pair entry and try sending from my phone again, up pops the thing to put the pin in, first on the phone and then on the PC, it just wont go further and send the files I get a message on the phone saying it can't connect, try again?

Mick

---

### Post by rahimveron on 2007-10-26
Yes thats exactly my probs, sorry could not explain as clearly as you did.
 In Feisty i had kbluetoothd and was able to send/receive from both, but i cannot fing the package in Gutsy repo.

---

### Post by Flutterby on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/157746](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/157746) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem here, using a fresh Kubuntu install.

I reported this here: [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/157746](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/157746)

Maybe it helps if you guys pitch in there. :)

---

