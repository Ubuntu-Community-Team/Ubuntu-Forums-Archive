---
title: "Dell Optiplex GX270: Can't boot from live CD."
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Irvine_himself on 2014-05-24
I have been given a second hand "Dell Optiplex GX270" and wish to install Ubuntu, unfortunately no matter what I do, it refuse to boot from the live CD:   

I have tried F2 and changing the Bios setting to "OS install", the only effect seems to be cutting available memory to 256 MB. I have also tried F12 and telling it to boot from the CD rom device, which it seem to accept but then ignores 

It currently has XP professional installed, although, due to staff changes, no one knows the administrator password. (This is one of the reasons why it was donated.)

  I have tested the live CD on a laptop and it is a good burn, so I am out of ideas and would be grateful for any advice.  

Irvine

---

### Post by sudodus on 2014-05-24
- Standard Ubuntu won't install and won't run with only 256 MB RAM. It needs 2 GB to run reasonably well. How much RAM totally is there in the computer?

- Is there an Intel Pentium 4 processor? What frequency (GHz)?

***I suggest that you try Lubuntu or Xubuntu 14.04 LTS***. Lubuntu needs 512 MB RAM and Xubuntu needs 1 GB RAM to run well. The differences are that these community flavours of Ubuntu have ultra-light and medium-light desktop environments and some application programs are lighter.

*Edit*: There might be driver problems in 14.04 LTS. In that case you can try ***Xubuntu 12.04 LTS*** or some light-weight re-spin based on Ubuntu 12.04 LTS, for example ***Bento, Bodhi*** or ***LXLE***.

If the computer does not want to boot from CD, the problem might be a bad CD drive. But computers with Pentium 4 CPUs are usually modern enough to boot from USB. So you can try flashing/cloning a Lubuntu or Xubuntu iso file to a USB pendrive (or USB hard disk drive). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Irvine_himself on 2014-05-24
Sorry, maybe I wasn't to clear. It is only when I switch the Bios to "Os install" that there is a limit of 256 MB, otherwise using the boot menu there is 1Gb. I know that strictly this is not enough, but I have previously ran lucid lynx with similar memory. Although I will certainly look at downloading a lightweight Ubuntu distro.

It is a Pentium 4 processor running at 2.6Ghz, Hyper-threading is disabled, Cpu speed is normal and Bus speed is 800 Mhz

I also thought there might have been a problem with the disc drive, and tried to load a Xp  pro recovery disc, the disc drive certainly ran, but since I was asked for the unknown password I was unsure as whether the recovery program actually loaded? Is there a way to test the disc drive?

In the F12 boot menu, there is only four choices:

1 Normal
2 Primary Master drive
3 Hard disc drive C:
4 IDE CD-ROM device

Will the ability to boot from a USB show up without actually having a boot-able USB present?

Thanks for replying 

Irvine

---

### Post by Irvine_himself on 2014-05-24
Ps:
I just remembered that when I ran the recovery disc, I no longer had the option of logging on as a guest, so I am fairly sure the recovery disc loaded.

Irvine

---

### Post by LastDino on 2014-05-24
At that config you will be best served with Lubuntu. Booting from USB option showing up or not depends on how your BIOS is configured, on my PC I only get option of ''boot from other devices'' some specifically show ''boot from USB''.

---

### Post by mörgæs on 2014-05-24
I have one of those. If you haven't done already I recommend upgrading BIOS to the latest available.

---

### Post by sudodus on 2014-05-24
> **Irvine_himself said:**
> Sorry, maybe I wasn't to clear. It is only when I switch the Bios to "Os install" that there is a limit of 256 MB, otherwise using the boot menu there is 1Gb. I know that strictly this is not enough, but I have previously ran lucid lynx with similar memory. Although I will certainly look at downloading a lightweight Ubuntu distro.

It is a Pentium 4 processor running at 2.6Ghz, Hyper-threading is disabled, Cpu speed is normal and Bus speed is 800 Mhz

I also thought there might have been a problem with the disc drive, and tried to load a Xp  pro recovery disc, the disc drive certainly ran, but since I was asked for the unknown password I was unsure as whether the recovery program actually loaded? Is there a way to test the disc drive?

In the F12 boot menu, there is only four choices:

1 Normal
2 Primary Master drive
3 Hard disc drive C:
4 IDE CD-ROM device

Will the ability to boot from a USB show up without actually having a boot-able USB present?

Thanks for replying 

Irvine

> **Irvine_himself said:**
> Ps:
I just remembered that when I ran the recovery disc, I no longer had the option of logging on as a guest, so I am fairly sure the recovery disc loaded.

Irvine

In this case I think the CD drive is good. It *should* boot from CD with item 4 of the F12 boot menu. If it does not, try to change the default boot order in a BIOS menu and reboot. If still no go, follow the advice by *mörgæs* and flash the newest BIOS into the computer. You may need DOS to do that. There are several free versions of DOS, for example FREEDOS.

---

