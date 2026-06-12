---
title: "Move GRUB and create boot image"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by matt_man22 on 2006-05-31
Hey guys,

I installed Ubuntu with the Live CD, and it automatically installed GRUB to the MBR.  I would like to restore the Windows boot loader (which I know how to do) but then I would like to be able to dual boot into Linux.  I have been searching how to create a boot image of Grub, but haven't been successful yet. I would then install Grub to my root partition and the image onto Windows for booting.

Thanks for your help.

P.S., I have no floppy drive, but I have USB keys.

---

### Post by Herman on 2006-06-01
You could make yourself a GRUB CD-RW by following [this link.]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")

---

### Post by matt_man22 on 2006-06-01
Any way to create an image from the MBR, move that to Windows for booting, and then reinstall GRUB in my root directory?

---

### Post by matt_man22 on 2006-06-01
Still trying to figure it out...any ideas?

---

### Post by Underhill on 2006-06-01
Assuming hda1 is where your current boat loader is located and you want to save it to the floppy (temporarily) for the transfer. (Change it to suit your need).

1. Boot Ubuntu, enter this command: dd if=/dev/hda1 of=/mnt/floppy/linux.lnx bs=512 count=1
(linux.lnx file will be created)

2. Boot Windows. Copy linux.lnx and put it in your Windows partition, for example on C:\linux.lnx

3. Restore your Windows boot loader.

4. Open your boot.ini (System Properties --> Startup and Recovery --> Setting --> Edit)

Add the following line (assuming you put the linux.lnx in C:\)

c:\linux.lnx="Ubuntu Linux"

Reboot and enjoy.

---

### Post by gadgetgirl on 2006-06-01
I was about to post that info too, but Underhill got to it first. :) Here's an article on the same topic too: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3) .

I have a dual boot setup now with XP and Dapper beta, using the Windows boot loader in the MBR. I'm going to blow away the Dapper partition tonight and reinstall with today's release (Network Manager is severely borked and I want to start again with a clean install). Just so I understand correctly, I should not use the 6.06 desktop CD if I don't want grub installed to the mbr, right? How much of a pain is it to restore the Windows boot loader to the mbr (and how)?

---

### Post by matt_man22 on 2006-06-01
Thanks Underhill.  Is that command safe with a USB key?

gadgetgirl, if you have the Windows XP restore disk, just load it up, and use the command Fixmbr.  Should be all set after that.

---

### Post by gadgetgirl on 2006-06-01
Thanks for the info Matt. 

"dd if=/dev/hda1 of=/mnt/floppy/linux.lnx bs=512 count=1" is safe with a USB key. It just grabs a 512 byte snapshot of the linux boot sector and write it to a file, named linux.lnx in this case.

---

### Post by matt_man22 on 2006-06-01
[QUOTE=Underhill]Assuming hda1 is where your current boat loader is located and you want to save it to the floppy (temporarily) for the transfer. (Change it to suit your need).

1. Boot Ubuntu, enter this command: dd if=/dev/hda1 of=/mnt/floppy/linux.lnx bs=512 count=1
(linux.lnx file will be created)

2. Boot Windows. Copy linux.lnx and put it in your Windows partition, for example on C:\linux.lnx

3. Restore your Windows boot loader.

4. Open your boot.ini (System Properties --> Startup and Recovery --> Setting --> Edit)

Add the following line (assuming you put the linux.lnx in C:\)

c:\linux.lnx="Ubuntu Linux"

Reboot and enjoy.[/QUOTE]

Would I then need to do something with GRUB (if it was installed in the MBR), or will Windows boot to Linux through GRUB after I copy the image file.

---

### Post by garba on 2006-06-01
[QUOTE=matt_man22]Would I then need to do something with GRUB (if it was installed in the MBR), or will Windows boot to Linux through GRUB after I copy the image file.[/QUOTE]

no, I think that's all there's to it, no need for extra tinkering IMHO

---

### Post by matt_man22 on 2006-06-01
Everything went well.  Thanks guys.  Here's all the steps I did:

1. Installed Ubuntu off of LiveCD (it installs GRUB to MBR)
  -Bypass this by using the alternate CD and installing GRUB to a floppy/USB Key.

2. Boot Ubuntu

3. Run 
```
sudo dd if=/dev/hda of=~/linux.lnx bs=512 count=1
```
  -(use hda to get beginning of disk, or the MBR)

4. Copy linux.lnx from Home folder to C:\ in Windows

5. Add C:\linux.lnx="Ubuntu Linux" to C:\boot.ini in Windows

6. Run Windows XP recovery disk, hit R to repair, enter password or hit enter

7. Use current Windows install and then type Fixmbr and accept

Now you can keep Windows boot loader and still boot to Ubuntu.

---

