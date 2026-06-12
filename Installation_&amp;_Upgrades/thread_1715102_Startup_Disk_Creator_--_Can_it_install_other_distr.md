---
title: "Startup Disk Creator -- Can it install other distros?"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2011-03-26
Can I point the Ubuntu Disk Creator to an openSUSE iso and create a bootable USB flash drive?

---

### Post by Dutch70 on 2011-03-26
Startup Disk Creator only works with Ubuntu based OS's. 

For other OS's you'll have to use Unetbootin. I don't think you'll have any luck with openSUSE though. 
Might want to check their forum before you even bother.

---

### Post by Rebelli0us on 2011-03-26
Thank you. I was thinking that it's better to create a bootable USB flash drive instead of burning a CD every time.

---

### Post by Dutch70 on 2011-03-26
> **Rebelli0us said:**
> Thank you. I was thinking that it's better to create a bootable USB flash drive instead of burning a CD every time.

I totally agree. It's easier, faster, cheaper & better for the environment. Since, as I said in another post. Most of the cd's end up in a landfill somewhere instead of a display computer at Office Depot where they should be. :P

Edit: You may have to install "imagewriter" from synaptic in order to create a live usb for OPENsuse.
[[COLOR="RoyalBlue"]http://en.opensuse.org/Live_USB_stick#Install_ImageWriter[/COLOR]]("http://en.opensuse.org/Live_USB_stick#Install_ImageWriter")

---

### Post by adduds on 2011-03-29
im having the same problem with suse and debian but image writer doesn't list my isos in myoperating systems folder when i browse it....

i tried unetbootin' for debian and suse no dice

tried

dd if=suse.iso of=/dev/sdc1 

but it doesn't boot

i'm now looking into writing several OS iso's to a single dvd

---

### Post by Dutch70 on 2011-03-29
I'm having the same problem, let us know if you find something that works. Probably should check in the Suse forums though.

---

### Post by whych on 2011-03-30
To make an openSUSE live usb, all you need to do is use dd to copy the openSUSE-live.iso to your usb stick, but ...

BEWARE THIS WILL OVERWRITE ANY DATA ON THE USB STICK

Open a terminal and with no usb stick mounted, type:
sudo fdisk -l (lowercase L)
to get the disk names.
Now insert your usb stick and when it mounts, do another
sudo fdisk -l
and note the device name of the usb stick.
It should show as /dev/sdx

Now in the terminal cd to the place you downloaded the openSUSE-live.iso and type:
sudo dd if=openSUSE-live.iso of=/dev/sdx
Where sdx is the usb stick.
When it finishes, you can boot from this and openSUSE will automatically set up a persistent install.

---

### Post by jackytan on 2011-03-30
thank you mate 
your sharing is good to me, i am also getting stuck in some same problem

---

### Post by Rebelli0us on 2011-03-30
> **whych said:**
> To make an openSUSE live usb, all you need to do is use dd to copy the openSUSE-live.iso to your usb stick, but ...

BEWARE THIS WILL OVERWRITE ANY DATA ON THE USB STICK

Open a terminal and with no usb stick mounted, type:
sudo fdisk -l (lowercase L)
to get the disk names.
Now insert your usb stick and when it mounts, do another
sudo fdisk -l
and note the device name of the usb stick.
It should show as /dev/sdx

Now in the terminal cd to the place you downloaded the openSUSE-live.iso and type:
sudo dd if=openSUSE-live.iso of=/dev/sdx
Where sdx is the usb stick.
When it finishes, you can boot from this and openSUSE will automatically set up a persistent install.


Thank you. Is this equivalent to what the "Ubuntu Disk Creator" does? Or the "extract to.." option in the Archive Manager available by right-clicking the iso in nautilus?


... here's what it got:

```
sudo dd if=openSUSE-GNOME-LiveCD-x86_64-Build0754-Media.iso of=/dev/sdc
1374208+0 records in
1374208+0 records out
703594496 bytes (704 MB) copied, 332.642 s, 2.1 MB/s

```


2 mb/s seems slow, it's a class 10 device that reads/writes at ~10mb/s. Anyway, I'm gonna boot it and let you know what happended.

---

### Post by Rebelli0us on 2011-03-30
Boots splash screen but no Desktop, disk access light blinks forever.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=187555&stc=1&d=1301498064[/IMG]

---

### Post by adduds on 2011-03-30
i ended up doing a bloody burn onto a dvd just for suse! lame

---

### Post by whych on 2011-03-31
@Rebellius
If you look at the error message you got from the screen shots, the .iso is corrupt (It tells you the checksum is wrong.)
> 
check: md5sum is wrong

Download the iso again and do a checksum on the iso before writing it to usb.

Yes, unfortunately it does take a while to write to the usb stick!.

@adduds
You had the right idea, but you were trying to write to /dev/sdc1 and not /dev/sdc

---

### Post by C.S.Cameron on 2011-03-31
Try installing to an 8GB flash drive in the same manner you would install to PC.
It is way safest to disable your internal drive first.

---

### Post by Dutch70 on 2011-04-05
Well, I finally got it on the usb stick. It boots up and shows the openSUSE splash screen with a little bar as if it's loading, but never seems to finish. 

I've tried creating the usb stick twice, same result. MD5sum is correct.
Really disappointed :(

---

### Post by Rebelli0us on 2011-04-05
> **Dutch70 said:**
> Well, I finally got it on the usb stick. It boots up and shows the openSUSE splash screen with a little bar as if it's loading, but never seems to finish. 

I've tried creating the usb stick twice, same result. MD5sum is correct.
Really disappointed :(

Same here, as I posted above. What if you unpack the ISO with 7-zip and put the contents on the USB flash?

---

### Post by Dutch70 on 2011-04-05
> **Rebelli0us said:**
> Same here, as I posted above. What if you unpack the ISO with 7-zip and put the contents on the USB flash?

No idea, but from what I've been reading. It may help to choose failsafe mode, or acpi=off. I'm going to give that a try now. Thinking openSUSE is more trouble than it's worth right now.

---

### Post by whych on 2011-04-06
> **Dutch70 said:**
> Well, I finally got it on the usb stick. It boots up and shows the openSUSE splash screen with a little bar as if it's loading, but never seems to finish. 

I've tried creating the usb stick twice, same result. MD5sum is correct.
Really disappointed :(

How did you create the live usb?
Did you use dd to copy it like I posted earlier? (it won't run otherwise - suse use kiwi as the live bootloader and not any of the ubuntu, fedora systems to load a live image.)


When you choose to run the live usb stick, hitting escape will give you the boot messages which should give you some idea of what is happening on boot.

Look for more help at the opensuse forums:
forums.opensuse.org

---

### Post by Dutch70 on 2011-04-06
> **whych said:**
> How did you create the live usb?
Did you use dd to copy it like I posted earlier? (it won't run otherwise - suse use kiwi as the live bootloader and not any of the ubuntu, fedora systems to load a live image.)

When you choose to run the live usb stick, hitting escape will give you the boot messages which should give you some idea of what is happening on boot.

Look for more help at the opensuse forums:
forums.opensuse.org

Yes I used dd to copy it, about 4 times now. I keep getting the same result. I've also tried hitting the esc button to see if I noticed anything strange, the only thing I noticed is it said read only, but that's correct isnt' it? 

I've also checked their forums & their advice was to choose failsafe or no acpi. They both give me a black screen.

> **Rebelli0us said:**
> Same here, as I posted above. What if you unpack the ISO with 7-zip and put the contents on the USB flash?

I really don't know how to do that. If you try it and it works for you, let us know.

---

### Post by winecurmudgeon on 2011-05-19
I followed the DD instructions, and it worked. The thing I did was to run the safe install, so I could watch it run. It took a while, but it finally loaded as a live disk.

---

### Post by whych on 2011-05-19
The problem with most live distros is when it comes to detecting your video setup, especially for nvidia cards.
(fedora live is no better than opensuse for this)
Opensuse have an updated section for video cards which applies to almost all distros and is worth a read.
I have found that in some cases installing from the distro's dvd overcomes these problems.
You don't have the space on the live distro to add all the special cases that are on the dvd.

---

### Post by lykwydchykyn on 2011-05-19
I recently discovered a tool called "multisystem" for making a USB stick boot to multiple distros / boot disks:

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I've been pretty pleased with how it works.  They have instructions on the site for installing it  on Ubuntu, though it works on most distros.

---

### Post by spcwingo on 2011-05-19
> **lykwydchykyn said:**
> I recently discovered a tool called "multisystem" for making a USB stick boot to multiple distros / boot disks:

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I've been pretty pleased with how it works.  They have instructions on the site for installing it  on Ubuntu, though it works on most distros.

A big +1 for multisystem.  Why just have one distro on your flash drive When you can have many?  :guitar:

---

### Post by Linux_junkie on 2011-06-02
> **whych said:**
> To make an openSUSE live usb, all you need to do is use dd to copy the openSUSE-live.iso to your usb stick, but ...

BEWARE THIS WILL OVERWRITE ANY DATA ON THE USB STICK

Open a terminal and with no usb stick mounted, type:
sudo fdisk -l (lowercase L)
to get the disk names.
Now insert your usb stick and when it mounts, do another
sudo fdisk -l
and note the device name of the usb stick.
It should show as /dev/sdx

Now in the terminal cd to the place you downloaded the openSUSE-live.iso and type:
sudo dd if=openSUSE-live.iso of=/dev/sdx
Where sdx is the usb stick.
When it finishes, you can boot from this and openSUSE will automatically set up a persistent install.

I used the above instructions to burn Fedora 15 iso to a USB memory stick all went well but when I try to boot up using USB nothing happens just get flashing cursor.

---

### Post by whych on 2011-06-02
You need to use the fedora live usb creator to create a fedora live usb.
I think it's in one of the ubuntu repos.
Filter on liveusb creator or liveusb-creator.
Fedora uses a different system for the live usb to openSuSE.

---

