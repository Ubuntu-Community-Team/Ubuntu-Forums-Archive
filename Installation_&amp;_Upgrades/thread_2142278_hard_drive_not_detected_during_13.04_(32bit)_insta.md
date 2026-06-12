---
title: "hard drive not detected during 13.04 (32bit) install"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by neekos on 2013-05-05
greetings!
i have a dell laptop here that has a dual boot installed on a single hard-drive.. linux mint 13 + win 7.
i want to either replace linux mint with ubuntu 13.04 or remove both OSs and just have one install remaining of ubuntu.

i made a usb key from the ubuntu installer and ran it.. and found that after choosing 'something else' for the installation options, the installer does not see my laptop's hard drive - it only sees the usb key that i am installing from and offers me the option of installing ubuntu to that!

does anyone know why this might be?

thanks

---

### Post by gdesilva on 2013-05-05
I would re-do the usb key. I tried to boot off a DVD and ran into some weired problems then I re burned my DVD and all was OK after that.

Hope this helps

---

### Post by neekos on 2013-05-05
i just re-downloaded the ubuntu image on a different pc, with different os and copied it to the usb key using a different usb key installer.. and the same result when attempting to install with it.. 
i went into ubuntu and used the live cd on the destination laptop and ran 'disks' and saw that the hard drive is not listed at all..

---

### Post by darkod on 2013-05-05
If there is an error in the partiton table, the disk/partitions will not be listed correctly.
If the disk had gpt table and was converted to msdos with windows, it doesn't delete the backup gpt table as it should, so linux tools get confused which table to display later.

Boot again in ubuntu live mode, open terminal and see what this outputs:
```
sudo parted -l
```

If you are running raid, or Intel RST (mix of hdd and small ssd for caching), it might not show the disk correctly.

---

### Post by neekos on 2013-05-05
i just ran sudo parted -l
and only the usb key is listed - the ssd drive is not.. there's no raid on the laptop.
the installation order of the existing 2 operating systems was windows 1st.

---

### Post by darkod on 2013-05-06
The disk is not seen by the OS at all. Double check if you can see it in bios. Double check the connections. It looks like it's not connected correctly, not detected by bios, or dead.

---

### Post by neekos on 2013-05-06
i am able to use the drive to boot into two other OSs just fine, i am using it to type this message.. so there is no actual hardware/bios error that i am aware of.

---

### Post by neekos on 2013-05-08
i resolved this now. i mis-read the text that is shown by the installer popup message about unmounting partitions; when i chose differently the hard drive was listed and i installed successfully. ;)

---

