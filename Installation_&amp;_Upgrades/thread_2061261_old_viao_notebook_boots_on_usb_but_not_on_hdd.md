---
title: "old viao notebook boots on usb but not on hdd"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by pjmuller on 2012-09-22
Dear all,

I'm completely new in the ubuntu scene but was very positively surprised after I played with the live demo of Ubuntu 12.04 that I booted from my USB.

However, when I wanted to go from play to actual use (so install it locally on my notebook) I got a problem. 
my Sony Viao FZ21M (with nVidia 8400M GT graphical card) doesn't boot from the HDD. 

What happens? I get a purple screen for a couple of seconds, then my screen turns off and the computer just freezes. If I boot in secure mode I get plenty of text output. The last lines are something like this:

```

Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness 
HEST: Table not found.
PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO

```

I have read many forum threads on 'failed booting' but I don't find the issue.

Here is some information you probably need.
- I first installed ubuntu 12.04 32bit alone on my pc, when I had this issue I thought it might have to do with grub.
- Then I installed windows 8 first (to make use of its bootloader), but after installing Ubuntu next to it, the same problem stays
- in live mode (booted from USB), my graphical card wasn't recognized, so my resolution stayed on 1024. I read topics on how to install the nvidia driver, but didn't do that yet as I thought it was nonsense to do in a temporary live environment.


Can somebody help me into the world of Ubuntu?
I guess the problem lies or with the booting (grub), or with my graphical card.

Greetings,
Pj

---

### Post by carl4926 on 2012-09-22
If it doesn't boot with the safe option (which includes nomodeset), I'm not sure.

This is just a thought:
You could boot the live cd/usb and chroot in to the installed system
And install the driver that way.

Or is there a way to get a text mode login in Ubuntu, I don't know? Anyone?
You could then install it

---

### Post by pjmuller on 2012-09-22
So you suggest I boot with the usb,

run 

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc

sudo chroot /mnt
```

Do the installation of the graphic driver.
And then

```
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Correct?

---

### Post by carl4926 on 2012-09-22
Correct
Where sda5 is /

---

### Post by carl4926 on 2012-09-22
> **carl4926 said:**
> Correct
Where sda5 is /

And I think that is

```
sudo apt-get install nvidia-current
```

---

