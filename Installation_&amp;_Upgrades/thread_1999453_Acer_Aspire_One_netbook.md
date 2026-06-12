---
title: "Acer Aspire One netbook"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by groeswenphil on 2012-06-08
Hi,
I have an Acer Aspire One netbook. It had Ubuntu Netbook remix installed and worked well for years....well, actually it was pretty slow. I wondered whether an upgrade might help so installed the recent release from a USB drive.
The computer worked fine from the USB drive but when I tried to install it permanently to its flash drive this is what went wrong.

First of all, it asks me to adjust partition size.....but no advice on what to change it to. I'd rather not have any partitions at all but initially it offers me 11Gb and 4.4 Gb

Then, eventually it starts to install with a progress bar along the bottom of a window indicating that it is copying files. This takes about 20 minutes.....then nothing.
No indication that anything else is going to happen, even after leaving the computer to ponder overnight, still nothing. When I try a normal bootup, I get the initial Acer flashscreen then a blank screen with a flashing cursor.

I'm wondering whether Ubuntu is suitable for this old netbook as it only has 16Gb drive. Would another distro be more suitable?
Phil

---

### Post by cortman on 2012-06-08
> **groeswenphil said:**
> Hi,
I have an Acer Aspire One netbook. It had Ubuntu Netbook remix installed and worked well for years....well, actually it was pretty slow. I wondered whether an upgrade might help so installed the recent release from a USB drive.
The computer worked fine from the USB drive but when I tried to install it permanently to its flash drive this is what went wrong.

First of all, it asks me to adjust partition size.....but no advice on what to change it to. I'd rather not have any partitions at all but initially it offers me 11Gb and 4.4 Gb

Then, eventually it starts to install with a progress bar along the bottom of a window indicating that it is copying files. This takes about 20 minutes.....then nothing.
No indication that anything else is going to happen, even after leaving the computer to ponder overnight, still nothing. When I try a normal bootup, I get the initial Acer flashscreen then a blank screen with a flashing cursor.

I'm wondering whether Ubuntu is suitable for this old netbook as it only has 16Gb drive. Would another distro be more suitable?
Phil

Your netbook sounds perfect for [Bodhi Linux]("http://bodhilinux.com/"). I have an Acer Aspire One netbook myself- I juggled a number of distros around before settling on Bodhi. Couldn't be happier. Bodhi is based on Ubuntu and uses the same repositories, so you have all the advantages of Ubuntu in a very lightweight distro.
You could also try Lubuntu if you prefer.

---

### Post by Topsiho on 2012-06-08
I have an Acer Aspire One, with only 8 GB SSD.
It ran Ubuntu (1.04) quite well, but it (especially using FireFox) greyed out for some seconds quite often, so I now have Lubuntu 12.04 on it. No greying out any more :)

What I think that happened is that you are trying to install the new Ubuntu next to the old one, and that there is not enough free space for it, even to only copy the necessary files from your USB stick (that is why it stops copying: no space is found to put the data in).

I'm not sure, but I seem to remember that during the install you are asked to install on top (or over) the previous OS. That old OS is deleted, and it's space is used by the new one.

I hope you made a BACKUP of all your personal files which you would hate to loose ...

Topsiho

---

### Post by dinutu on 2012-06-08
> **groeswenphil said:**
> Hi,
I have an Acer Aspire One netbook. It had Ubuntu Netbook remix installed and worked well for years....well, actually it was pretty slow. I wondered whether an upgrade might help so installed the recent release from a USB drive.
The computer worked fine from the USB drive but when I tried to install it permanently to its flash drive this is what went wrong.

First of all, it asks me to adjust partition size.....but no advice on what to change it to. I'd rather not have any partitions at all but initially it offers me 11Gb and 4.4 Gb

Then, eventually it starts to install with a progress bar along the bottom of a window indicating that it is copying files. This takes about 20 minutes.....then nothing.
No indication that anything else is going to happen, even after leaving the computer to ponder overnight, still nothing. When I try a normal bootup, I get the initial Acer flashscreen then a blank screen with a flashing cursor.

I'm wondering whether Ubuntu is suitable for this old netbook as it only has 16Gb drive. Would another distro be more suitable?
Phil

I've recived the Aspire one 722 today and the first thing i did i installed ubuntu, first i did just the way you did, installed it on the USB drive, where i was installing tons of distros before and it just didn't start, when inserting into another computer after taht it asked to format it..anyway i took another usb drive, a new one, and it started smoothly. When installing it, it said that is not able to create some kind of directory-or couldn't find it..as i baught this acer for my mom, i decided to give it the last try before leaving my mom to struggle with the windows, i have installed it on a CD, everything went just fine. I am running it now, anyway, everything takes longer time than expected, just as you said, it took more than 20 minutes to install updates out of the already installed distro, then i have just cancelled it, after, when rerunning it, it said that half of the updates were installed already so what i think is that you need to wait more until it installs everything. As far as i see it is a quiet slow netbook and everything takes lots of time, just be patient. I still don't get it, why Acer placed 4 gigs of ram on a 1&#500;Hz processor is like having a an airbag on a bicycle. try the CD and be patient, specially on an older one, get rid of compiz, and better try lubuntu or puppy. hope it helps.

---

### Post by black veils on 2012-06-09
indeed Bodhi Linux or Lubuntu (this might be less intimidating) are the way to go, maybe even Xubuntu !

---

### Post by groeswenphil on 2012-06-10
Installed Bodhi on my Acer Aspire One netbook. Everything appears to be working except I cannot get wifi to connect.

I'm given the choice to connect to a hidden network or to a new network......well, I just want to connect to my existing network.
It appears to have identified my network, but then, I'm not sure whether I'm wpa, wpa2 personal or wep whatever. Do I enter a passphrase or a passkey? Far too many choices...anyway, it isn't connecting.

Thanks in advance,
Phil

---

### Post by black veils on 2012-06-10
you should probably make a new thread for the wireless issue. it shouldnt be difficult to sort. i doubt it is relevant that the system is bodhi linux, but mention that in the description of your problem.

---

### Post by groeswenphil on 2012-06-10
Sorted. Switch at front right hand side of keyboard. :O(

Working fine now.
Phil

---

