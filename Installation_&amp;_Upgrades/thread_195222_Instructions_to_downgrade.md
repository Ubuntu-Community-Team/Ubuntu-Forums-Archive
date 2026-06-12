---
title: "Instructions to downgrade"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by LeeM on 2006-06-12
Sorry, I'm having too many device problems with Dapper (camera won't mount, can't record on blank CD, removable drives [USB and Firewire] aren't being seen,....). 
What is the procedure for "downgrading" back to Breezy, for now!

Thanks!

---

### Post by Joeb on 2006-06-12
I'm not sure of downgrade procedures, however, I got my firewire devices to work (ipod, actually) by plugging it in and then from the command line typing:

sudo rmmod ieee1394
sudo rmmod sbp2
sudo ohci1394
sudo modprobe sbp2

After that, firewire worked as expected.

As for the rest, what are the actual problems you are experiencing?

---

### Post by LeeM on 2006-06-13
[QUOTE=Joeb]I'm not sure of downgrade procedures, however, I got my firewire devices to work (ipod, actually) by plugging it in and then from the command line typing:

sudo rmmod ieee1394
sudo rmmod sbp2
sudo ohci1394
sudo modprobe sbp2

After that, firewire worked as expected.

As for the rest, what are the actual problems you are experiencing?[/QUOTE]

Things are getting better, so I am backing off from the brink a little. Still frustrating however. 

Here are the problems I was having, and what I have done to try to correct them:

1. camera not mounted. When I connect it (USB), Konqueror opens with URL:
system/media/camera, and shows a folder icon for Canon PowerShotA80 (which is the correct model). When you try to open that folder, it responds,
"an error occured while loading system:/camera/camera/camera
unknown error
Bad parameters"

I can get around this (ugH) by using a USB film reader on the chip.

2. Couldn't burn a CD. I installed k3b, and now I can burn CDs.

3. Couldn't access removable drives (on Firewire and USB). Something is hosed up in automounting. I played around with /etc/fstab a little, and can get most removable media partitions up now. Any idea why a drive that used to show up as /dev/sda* now shows up as /dev/sdc*? (Where * = 1,2, etc.)

Still can't access Firewire drive. When I tried
sudo rmmod ieee1394

as you suggested, it replied:
ERROR: Module ieee1394 is in use by sbp2,ohci1394
 
What does that mean?

Thanks!

LeeM

---

### Post by az on 2006-06-13
Have you go kubuntu-desktop still installed?  If not, install it.

---

### Post by Joeb on 2006-06-13
[QUOTE=LeeM]
Here are the problems I was having, and what I have done to try to correct them:

1. camera not mounted. When I connect it (USB), Konqueror opens with URL:
system/media/camera, and shows a folder icon for Canon PowerShotA80 (which is the correct model). When you try to open that folder, it responds,
"an error occured while loading system:/camera/camera/camera
unknown error
Bad parameters"

I can get around this (ugH) by using a USB film reader on the chip.

2. Couldn't burn a CD. I installed k3b, and now I can burn CDs.

3. Couldn't access removable drives (on Firewire and USB). Something is hosed up in automounting. I played around with /etc/fstab a little, and can get most removable media partitions up now. Any idea why a drive that used to show up as /dev/sda* now shows up as /dev/sdc*? (Where * = 1,2, etc.)

Still can't access Firewire drive. When I tried
sudo rmmod ieee1394

as you suggested, it replied:
ERROR: Module ieee1394 is in use by sbp2,ohci1394
 
What does that mean?

Thanks!

LeeM[/QUOTE]


I'm not a KDE user, but I'm not sure your problems are KDE specific.  Just incase, like azz suggested, make sure you have kubuntu-desktop installed.  It installs kde and a lot of support packages and scripts that might solve your problems if it's not installed (since k3b wasn't installed, I'm wondering if that might be the case)

As for the /dev/sda* becoming /dev/sdc or whatever, that usually depends on what what order the ports and devices are being found and can change from boot to boot depending on what is plugged in.  Therefore, if you have hardcoded something in your /etc/fstab for a particular /dev/sd* it's possible that isn't in the right place anymore because of something else.  It is possible to set udev rules to tell the udev system where to assign certain things.

To get rid of the errors when trying to do the rmmod steps I posted, you will have to have the firewire devices unplugged from the computer.  Otherwise, you will get the messages you are getting, because the modules are infact in use.  If the devices are unplugged, try changing the order of the rmmod statements or if you manually mounted something, you will have to manually unmount it first.

I'm not sure why you are having the problem reading the card in your camera but not in a card reader.  Hopefully someone else will be able to help on that one.

---

### Post by LeeM on 2006-06-14
[QUOTE=Joeb]I'm not a KDE user, but I'm not sure your problems are KDE specific.  Just incase, like azz suggested, make sure you have kubuntu-desktop installed.  It installs kde and a lot of support packages and scripts that might solve your problems if it's not installed (since k3b wasn't installed, I'm wondering if that might be the case)

As for the /dev/sda* becoming /dev/sdc or whatever, that usually depends on what what order the ports and devices are being found and can change from boot to boot depending on what is plugged in.  Therefore, if you have hardcoded something in your /etc/fstab for a particular /dev/sd* it's possible that isn't in the right place anymore because of something else.  It is possible to set udev rules to tell the udev system where to assign certain things.

To get rid of the errors when trying to do the rmmod steps I posted, you will have to have the firewire devices unplugged from the computer.  Otherwise, you will get the messages you are getting, because the modules are infact in use.  If the devices are unplugged, try changing the order of the rmmod statements or if you manually mounted something, you will have to manually unmount it first.

I'm not sure why you are having the problem reading the card in your camera but not in a card reader.  Hopefully someone else will be able to help on that one.[/QUOTE]

Thanks to both you and azz for the helpful suggestions. I did install kde-desktop (after seeing the previous email). It did help somewhat.

I'll look into the udev suggestion. Sounds like a real possibility.

Also, I'll try removing the Firewire drive and following your earlier suggestion.

LeeM
:p

---

### Post by pereira on 2006-06-18
I had the same problem to auto mount my camera: Canon Powershot SD450. With Digikam I didn't have no problem, but opening with konqueror I got the errors "Unknown errors Bad parameters".

Thanks.

---

