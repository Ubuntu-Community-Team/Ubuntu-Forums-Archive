---
title: "Lubuntu 20.04 installation problem with hp compaq 6715s"
date: 2021-07-05
forum: Installation &amp; Upgrades
---

### Post by buluntu on 2021-07-05
Hello,
I'm new here, new with lubuntu and bad in English but I try to explain my problem.
Trying to install 20.04 to my laptop. With Noapic selection lubuntu starts very slowly from installation media (dwd) and I can start installation from the icon of the desktop. I can do all selection and everything goes well. Only notice is that I'm not having internet connection. But when I select "install" it goes back to desktop screen and nothing happens.

I have already Vista in my laptop and I try to share disk with lubuntu automatic option during installation.

What should I do? Thanks & best regards!

---

### Post by GhX6GZMB on 2021-07-05
Live boot from a DVD takes around 4...5 minutes. I don't know if that's what you mean by "slow".
Don't just select language, but also keyboard layout (F3) during live boot.
I see no reason to use the "noapic" option, just select "Start Lubuntu" directly. You'll land on the desktop eventually, where you can start the real installation.

And make a plan for your disk partitioning (/, /home, SWAP etc.) first.

If your network connection is WLAN, you may have difficulties, as some network adapters need proprietary drivers that are not included in the install package. Best thing is to use a cabled network connection during installation.

Cheers.

---

### Post by buluntu on 2021-07-06
Without Noapic option live boot from dvd ends up to black screen and is same after few hours.
Language and keyboard selections are ok.

---

### Post by yancek on 2021-07-07
>  I can do all selection and everything goes well. Only notice is that I'm not having internet connection

Are you referring to Lubuntu on the DVD? Perhaps you could post some information on your hard ware as it appears to be an old machine.  Vista hasn't been supported for 4 years and was released 14 years ago.  Did you verify the download of the iso file of Lubuntu after download?  Lubuntu is generally good on older machines so there may be some other problem.

Also, your post is a bit confusing as your statement above contradicts your later statement below,  Is Lubuntu installed or is this problem on the DVD?

> But when I select "install" it goes back to desktop screen and nothing happens. 

---

### Post by sudodus on 2021-07-07
+1 to yancek's requests; and I would add some details:

Please specify brand name and model of

- computer (is hp compaq 6715s according to [this link](https://www.cnet.com/products/hp-compaq-6715s-15-4-turion-64-x2-tl-58-win-xp-pro-1-gb-ram-120-gb-hdd-series/) describing your computer?)
- CPU 
- Graphics chip or card (separate or built into the CPU)
- Amount of RAM

When we know this, it will be easier to suggest what to do.

[hr][/hr]
[This link about old hardware](https://ubuntuforums.org/showthread.php?t=2130640) might be helpful.

---

### Post by grahammechanical on 2021-07-07
Loading the Lubuntu live session and installing Lubuntu from a DVD is  certainly slow. Especially on a machine that Windows Vista was installed  on. The hardware is old and slow. The DVD drive might be a slow drive.

You make this statement:

> I can start installation from the icon of the desktop.

That  tells me that the Live session is running. Have you tried to set up an  internet connection? You will have to do that if you want to connect to  the internet by WiFi.

Regards

---

### Post by GhX6GZMB on 2021-07-07
> **grahammechanical said:**
> Loading the Lubuntu live session and installing Lubuntu from a DVD is  certainly slow. Especially on a machine that Windows Vista was installed  on. The hardware is old and slow. The DVD drive might be a slow drive.


I'm getting a bit fed up with this kind of knee-jerk dissing of old hardware. The DVD is 24x and a live boot takes 4...5 min.

I'm running a couple of HP Compaq 6910p laptops that are very similar to the 6715s, except they only have a 14.1" screen. About the same age too (2007/08)
They're extremely fast with Lubuntu, and faster than they ever were with Vista or XP.

The 6715s is a good match for Lubuntu and should install/run without a hitch.

@Buluntu, if you have the option, try installing with a cabled LAN connection for Internet. WLAN can be fixed later.

---

### Post by buluntu on 2021-07-07
Thanks, I'll take the laptop to my parents on weekend and try with LAN connection. I'll tell later if it helps.
Laptop specs according to attached file except memory 2GB.

---

### Post by sudodus on 2021-07-08
As we all know, it is an old computer, and the Sempron processor is low end. But with 2 GB RAM [I agree with ml9104 that] **it should be possible to install and run Lubuntu**. It is a good idea to take the laptop to your parents on weekend and try with LAN connection. Good luck :-)

[hr][/hr]
Finally, I'll remind you of [this link about old hardware](https://ubuntuforums.org/showthread.php?t=2130640).

The first few posts contain lots of tips how to check for things that might create problems in an old computer, and how to find ways to make things work.

And if you scroll down further in the link, you can find tips about other [non-Ubuntu] Linux distros, that are known to work well in old computers. But let us try more with Lubuntu and some other flavours of Ubuntu with a light foot-print, Xubuntu and/or Ubuntu MATE, before resorting to really lightweight Linux distros.

---

### Post by tea for one on 2021-07-08
> **buluntu said:**
> Thanks, I'll take the laptop to my parents on weekend and try with LAN connection. I'll tell later if it helps.
Laptop specs according to attached file except memory 2GB.

According to the specification details, you have a Broadcom wireless device.

Try and boot a live session again, open a terminal and enter:-

```
sudo apt install bcmwl-kernel-source
```

Is your wifi device recognised?

---

### Post by GhX6GZMB on 2021-07-08
@tea for one:

You've put your finger on the sore spot.
The Broadcom firmware needs to be installed before you can have a WLAN network (B43-fwcutter), and I've never been able to do this without an active LAN/Internet connection running. It's a chicken-and-egg situation.
Man, I love my old-fashioned LAN more every day :)

---

### Post by tea for one on 2021-07-08
@ml9104

Thank you for your comments.

During a [COLOR="#0000FF"]live[/COLOR] session with Ubuntu, the Broadcom firmware [COLOR="#0000FF"]is present[/COLOR] in the ISO and you can install it to check if it functions OK. 

Is it not the same for Lubuntu?

However, once installed the Broadcom wifi package is removed and then, as you mentioned, you will need a ethernet connection, alternative USB wifi or mobile phone tethering to install it again.

I'm sure that It is a matter of legal restrictions in certain regions.

MX Linux includes Broadcom wifi firmware after installation and I have always wondered why the Ubuntu family cannot have a similar arrangement?

---

### Post by GhX6GZMB on 2021-07-08
@tea for one:

Very interesting.
That the BC package is available in the live boot is new to me. But as I've never done an installation with WLAN, this explains my ignorance.
Installations supported by LAN Internet always run without a hitch. And the subsequent BC WLAN installation will have to be done without a running WLAN anyway.

I've no idea about the legal issues here, but Broadcom is not very friendly to the open source community in general.

Cheers.

---

### Post by buluntu on 2021-07-11
Hello again..
LAN connection did not help at all. Booting took about 20 minutes with noapic option. Without noapic just blanc screen after about 1hour. After booting with noapic option I started installing. After all selections and starting to "install now" I ended back to desktop and nothing else happened.

Thanks for further tips! I'll get to know them better too.

---

### Post by monkeybrain20122 on 2021-07-12
> **tea for one said:**
> @ml9104

Thank you for your comments.

During a [COLOR=#0000FF]live[/COLOR] session with Ubuntu, the Broadcom firmware [COLOR=#0000FF]is present[/COLOR] in the ISO and you can install it to check if it functions OK. 

Is it not the same for Lubuntu?

However, once installed the Broadcom wifi package is removed and then, as you mentioned, you will need a ethernet connection, alternative USB wifi or mobile phone tethering to install it again.

I'm sure that It is a matter of legal restrictions in certain regions.

MX Linux includes Broadcom wifi firmware after installation and I have always wondered why the Ubuntu family cannot have a similar arrangement?

 Not sure if this is the same as this problem where b43 was blacklisted after installation, to prevent that see the solution in last post  [https://forums.linuxmint.com/viewtopic.php?t=198531](https://forums.linuxmint.com/viewtopic.php?t=198531)

Or perhaps you need to check install third party software during installation, though the installer crashes if that is checked for Ubuntu20.04, not sure about the flavours.

---

### Post by buluntu on 2021-07-15
Any idea why I get segmentation fault and installation won't go further? See photo.

---

