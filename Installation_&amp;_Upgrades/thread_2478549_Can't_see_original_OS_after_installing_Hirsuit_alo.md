---
title: "Can't see original OS after installing Hirsuit alongside"
date: 2022-08-29
forum: Installation &amp; Upgrades
---

### Post by cheapodonuts on 2022-08-29
As per title, I've installed Hirsuit from a Linux Shop usb stick, (never been used before). I installed it alongside my older version, so I could extract files later. But now I don't see any way to start up the previous OS. Hopefully there's a way to sort this, as I have a bunch of photos stored on the earlier system.

Thanx in advance for any assistance you guys. &#127856; &#128077;

---

### Post by guiverc on 2022-08-30
All of Ubuntu 21.04 (*hirsute hippo*) is ***end of life*****.**

A end of life announcement can be read here - [https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Lubuntu's EOL notice can be read here - [https://lubuntu.me/hirsute-eol/](https://lubuntu.me/hirsute-eol/)

Lubuntu 21.04's upgrade path was to the next release, but that was gone with [21.10 reached EOL itself]("https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/") (*Lubuntu's announcement is [here]("https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/")*).

I'd suggest not trying to use it, instead using a *supported* release.  The 21.10 EOL notice lists the current *supported* release of Lubuntu.

Do note:   Even if you can't *boot* the older OS (*you gave almost no details*), you should be able to `mount` the partition(s) to ensure your files are present, and copy them to somewhere safe (*even just use them*).

---

### Post by cheapodonuts on 2022-08-30
Thanks for the info.
 Heh, there are no details I can give as my laptop simply starts Hirsuite. So I'll have to do the 'mount' thing, it's been years since I did anything like that. I think I'll buy a portable hard drive, so I can just empty my camera's memory card into it each day. I've just ordered the recent LTS USB version from Linux Shop anyoo. Can't believe I had an unopened one in the desk for so long!!! &#55357;&#56837;
Thanx again buddy &#55357;&#56833;

---

### Post by yancek on 2022-08-30
When installing a newer release of  Ubuntu and its derivatives, grub is usually updated and you should have had an entry in grub for the older release.  Did you try running sudo update-grub?  Do you know which partition the older release is on, same for the newer release.  Did you run fdisk to see what partitions you have just in case it installed over the old release?  If you used the Install Alongside option, that should not have happened.   You should be able to mount the partition from the new install and copy the files you want to the new system.  If you get a new external drive, you should do backups to it on at least  weekly/bi-weekly.

---

### Post by oldfred on 2022-09-01
If an older system, you may want a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

If you have a flash drive, you can download the ISO and use an installer to extract ISO to flash drive to boot live installer & install Ubuntu. 

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)

---

### Post by cheapodonuts on 2022-09-02
Thanx for all your suggestions everyone.
I've only realised belatedly that I didn't mention the double Lubuntu install in the title! Eejit! 
 I'll be having a go at it all after my holiday as I'm relaxing with family at the mo. &#128075;&#128715;&#65039;&#128513;&#128077;&#127829;

---

