---
title: "system-config-lvm error message at startup - ubuntu 16.04 - LVM frozen"
date: 2016-06-27
forum: Installation &amp; Upgrades
---

### Post by iscandarster on 2016-06-27
Hi,

[LIST=1]
[*]Just installed unbuntu 16.04 on a Asus zenbook ux305la 8Go RAM - 256 SSD - i7 CPU, and tried to launch LVM Manager from the launcher to resize root partition and make a data partition, but got an error message (see below). LVM opens a terminal, have to enter my passwd, LVM opens but got this error message in the terminal and impossible to click into LVM it's frozen.
[*]Error message in the terminal : "Unable to show VG because it contains features that are not supported in current version of system-config-lvm."
[/LIST]

Total installation is brand new from this morning and packages sync with the Software Updater.
Any clue ?

---

### Post by Dennis N on 2016-06-27
Is Windows installed on the machine? If so, it may have something to do with the problem. I have the LVM Volume Manager installed in Lubuntu 16.04, and it launches correctly. See screenshot of volume group screen. I tested a bit further: to resize Lubuntu 16.04 I clicked on lubuntu_1604 under "Logical View" and I get three buttons, Remove Logical Volume, Create Snapshot, and Edit Properties. The Edit button allows me to expand the LV. 

Maybe you can do the job from the terminal instead.

You might test with a terminal command to see if the Volume Group is shown:

```
dmn@Kayleigh:~$ sudo vgdisplay
[sudo] password for dmn: 
  --- Volume group ---
  VG Name               common_vg
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  17
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               2
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               85.93 GiB
  PE Size               4.00 MiB
  Total PE              21997
  Alloc PE / Size       16640 / 65.00 GiB
  Free  PE / Size       5357 / 20.93 GiB
  VG UUID               90He13-7Tei-oVH2-KUtT-rcNJ-j2ZC-dlAGDJ
```

---

### Post by iscandarster on 2016-06-27
The installation has wiped out every thing on the machine. This is a single boot with ubuntu 16.04. The only thing it"s a SSD (?!). Every thing has been set up with Ubiquity or the Software Updater. 
I included a screenshot of the situation :

lvm was launched from the launcher. I opened another term to show the information provided with command line, and I also launched gparted too at the end to have another view.
I don't want to use command line because I didn't found a clear tutorial on how to reduce the root partition, and create a new one with data with simple, clear explanation on just my need, not having to understand all the theory and the commands for just that simple need. 

[ATTACH=CONFIG]269825[/ATTACH]

Does it help ?

---

### Post by banceu_sergiu_ione on 2016-06-27
Here is a nice [wiki]("https://wiki.archlinux.org/index.php/LVM") about LVM

From what I see from your screen-shot, you need root privileges to can do that. Now, I do not know how you can run it with root privileges.
I believe that if you try to resize ( shrinking) the root / volume, you will need 1st to unmount it but since you use it will be impossible if not run from a LiveUSB. Since I am not sure, wait t bit see if someone who better know replay. In meanwhile you can read that nice wiki.k

---

### Post by Dennis N on 2016-06-27
I have no suggestions on fixing the "unable to show vg..." problem. A short search did not turn up anything I would consider similar. I made my lvm setup post-install and not with ubiquity. That is a difference between yours and mine, but may not be material.

It's not clear what you actually want: You said you wanted to "resize root partition and make a data partition". Right now on your system there is no root partition. You have an EFI system partition (sda1), a boot partition (sda2) and an lvm partition (sda3). By root partition do you mean the root LV (logical volume) inside sda3?  By create a data partition do you mean a new data LV inside sda3? I gather you do not intend to shrink sda3.

You objectives need to be clarified. These things can be done with lvm commands, should you decide to learn about them.

---

### Post by Dennis N on 2016-06-27
Looking again at you graphic, it is hard to read the right panel of the "Logical Volume Management" window, but it sure looks like it is displaying the data in there, even though it does not show the graphic in the center pane. "Unable to show..." may only refer to the graphic display, and everything else is still functional.

That graphic in the center panel is just a visual aid. That makes me wonder if you can open the "Logical View" section in the left panel (click on "Logical View"), select the logical volume used for root, press the edit button, and get the popup window to resize it? 

So, you may be able to use the system-config-lvm after all.

---

### Post by iscandarster on 2016-06-28
Ok I understand. Will do it from ubuntu on a stick (cause now I can :)
Thx for helping out guys

---

### Post by Dennis N on 2016-06-28
> **iscandarster said:**
> Ok I understand. Will do it from ubuntu on a stick (cause now I can :)
Thx for helping out guys

Great! So you found you are able to use the LVM Manager? Yes, you need to have the LV unmounted to resize it, so you need to do that from live media if you have no other OS you can work from.

---

### Post by iscandarster on 2016-06-29
Not really ! Chose to let it go : When booting from USB with standard iso ubuntu there is no graphical lvm installed on it and have no time to built a specific one...

---

