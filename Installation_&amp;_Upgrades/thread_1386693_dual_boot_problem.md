---
title: "dual boot problem"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by padmaiyer on 2010-01-21
hi, am an absolute novice. 
i have an internal 80gb hardrive and an external 320gb usb hardrive.
i wanted to try ubuntu 9.10 so downloaded it and follwed the steps for install. i installed it on a ntfs partition on my usb hd.
the installation went on smoothly with no errors.
when it finally told me to reboot after installation. i got the error:
GRUB loading...
error:no such disk
grub rescue>
i dont know what to do after this,
i changed the boot sequence to load from my usb hd.
now if try to load from internal hd, it sometimes shows me the above error, and sometimes just a blank screen.
i cant load xp or ubuntu. what should be done? can this problem be solved??
i could really use some help.

---

### Post by cenzorrll on 2010-01-21
did you try to install ubuntu on the ntfs partition, or did you make a new partition formatted to one of the ext's?

---

### Post by padmaiyer on 2010-01-21
> **cenzorrll said:**
> did you try to install ubuntu on the ntfs partition, or did you make a new partition formatted to one of the ext's?

i had partitioned my usb hd. was not using one of the partitions of it, so installed ubuntu 9.10 on that. 
i chose the option "install side by side choosing between them at startup"
then gave ubuntu 50gb of that drive, as it wasnt using the whole of it anyways(i.e 120gb)

---

### Post by cenzorrll on 2010-01-21
hmm, strange, are you unable to select either windows or ubuntu at all? if not then you'll probably need to make sure grub is pointing to the right partition for booting. I haven't messed with the new grub enough to really help you out as much as I would like.  Search the forums for grub2 and learn as much as you can before trying anything (if you can at least get to the grub menu by holding shift as you boot, then we can definitely get somewhere with what I know about grub).

if you can't boot either ubuntu or windows, then i would suggest for the time being is to get a hold of your XP disc or a windows recovery disk and do the repair thing (there's how to's everywhere on how to repair the windows boot loader, google is your friend here) that way you at least have windows running again and a working computer.

it's getting late here, so i won't be able to help out more until at least tomorrow afternoon/night (woohoo for school and work) so hopefully someone else will be able to chime in by then (hopefully with more grub2 experience than me)

you should also post the output of (from the terminal in the livecd):
```
sudo fdisk -l
```
and from where you installed ubuntu (under Places you should be able to see all your disks and partitions, select the one you installed ubuntu to) paste the contents, or attach, your /etc/fstab file

Hope you get this worked out before I get back (you have no idea how many times i've done something like this to myself, on accident and on purpose, so it's not the end of the world)

edit: i just thought of one more thing, when you installed did you do it from the livecd or from within windows? If you used wubi (from within windows) then i really can't help at all as it's a completely different way of installing.

---

### Post by cenzorrll on 2010-01-21
I think i found what you're looking for:

[Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

and toward the bottom of the first post:
```

External Drive Installs - Bug [bug/496435]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435")
Installs of Ubuntu on external drives can cause problems as grub-install uses device names (e.g. sda, sdb) rather than UUIDs in certain circumstances. If connected to another machine when an update of grub-pc is made, the upgrade may be written to the incorrect device and make the computer unbootable.

A workaround is posted on the bug link above.


External Drive Installs and MBR - Bug [bug/414996]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996")
When installing Ubuntu to a USB drive, the potential exists for GRUB 2 to write to the hard drive's MBR or split the installation between the hard drive and the USB drive (rather than completely on the USB device). This can render the main drive unbootable.

Workaround: During the final stages of the install there is an "Advanced" button which allows the user to select the install location.

```

and
```
error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:
[Boot Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")
```

I was thinking your problem would be the last bit I posted, caused by one of the first two.

---

### Post by padmaiyer on 2010-01-28
thanks a lot,
but that didnt work, i had to format my HD completely, and load xp.
then i loaded ubuntu using wubi.
i know its not the same, but its so much simpler

---

### Post by dlabelle11 on 2010-01-30
"grub loading error no such disk" This was the error I was getting, just
 like the OP and I think Im pretty much in the same situation as him with
 regards to his details.

I used this workaround from a previous post when I reinstall ubuntu on my
 usb drive.

""Workaround: During the final stages of the install there is an
 "Advanced" button which allows the install location.

and now ubuntu is running fine from this usb drive. Now I just have to get
 windows running again hopefully windows will fix itself when I pop in 
the windows cd.

---

### Post by presence1960 on 2010-01-30
> **dlabelle11 said:**
> "grub loading error no such disk" This was the error I was getting, just
 like the OP and I think Im pretty much in the same situation as him with
 regards to his details.

I used this workaround from a previous post when I reinstall ubuntu on my
 usb drive.

""Workaround: During the final stages of the install there is an
 "Advanced" button which allows the install location.

and now ubuntu is running fine from this usb drive. Now I just have to get
 windows running again hopefully windows will fix itself when I pop in 
the windows cd.

If windows is on the internal disk (sda) & ubuntu and GRUB are on the external disk boot into Ubuntu and open a terminal & run ```
sudo apt-get install lilo
```
This will install lilo. Now in terminal run ```
sudo lilo -M /dev/sda mbr
```

This will fix the MBR of the disk that has windows and you will be able to boot windows without the external plugged in

---

### Post by dlabelle11 on 2010-01-30
I fixed mine but I used the windows 7 cd there's a good thread somewhere with what commands to use once you get to the commad prompt but I lost it...  Either way I'm up and running perfectly for now...

thanks everyone

---

### Post by presence1960 on 2010-01-30
> **dlabelle11 said:**
> I fixed mine but I used the windows 7 cd there's a good thread somewhere with what commands to use once you get to the commad prompt but I lost it...  Either way I'm up and running perfectly for now...

thanks everyone

There are 3 ways that I know of to fix a windows MBR. One I posted. 

Second is to run in terminal from Ubuntu ```
sudo apt-get install mbr
``` to install package mbr then in terminal run ```
sudo install-mbr /dev/sdX
``` where X = disk, i.e. sda, sdb, sdc, etc.

The third way is what you mentioned. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") for instructions using the windows install CD/DVD

---

### Post by dannyf on 2010-01-30
> **cenzorrll said:**
> I think i found what you're looking for:

[Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

and toward the bottom of the first post:
```

External Drive Installs - Bug [bug/496435]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435")
Installs of Ubuntu on external drives can cause problems as grub-install uses device names (e.g. sda, sdb) rather than UUIDs in certain circumstances. If connected to another machine when an update of grub-pc is made, the upgrade may be written to the incorrect device and make the computer unbootable.

A workaround is posted on the bug link above.


External Drive Installs and MBR - Bug [bug/414996]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996")
When installing Ubuntu to a USB drive, the potential exists for GRUB 2 to write to the hard drive's MBR or split the installation between the hard drive and the USB drive (rather than completely on the USB device). This can render the main drive unbootable.

Workaround: During the final stages of the install there is an "Advanced" button which allows the user to select the install location.

```

and
```
error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:
[Boot Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")
```

I was thinking your problem would be the last bit I posted, caused by one of the first two.

O heck, I think that's my problem too. See my post at
[http://ubuntuforums.org/showthread.php?t=1394595](http://ubuntuforums.org/showthread.php?t=1394595)

Except my HD *was* encrypted with McAfee Endpojnt. Now I'm dead when I get to work on Monday :-( 
Danny

---

