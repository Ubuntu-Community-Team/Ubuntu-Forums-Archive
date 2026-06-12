---
title: "Dual boot problem"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by vfactor on 2005-05-25
Hi all

I am a complete Linux newbie trying to set up my system dual boot Xp and Ubuntu.  Here's my situation:

I have XP installed in Raid0 SATA (build in controller).  I installed ubuntu on an independent IDE HD .  During installation, Ubunto never asked me to make dual boot. I guess because it didn't recognize XP on the SATA RAID.

I can boot into Ubunto w/o problem or XP (changing boot selection in Bios). Now I would like to make a dual boot loader.

I searched the net and I decided to go with the boot.ini (windows XP) modification since I probably use windows more at this stage.

So I did the **dd** command to make a boot.mbr file and copied it to C:\  (windows XP). I also modified the boot.ini by appending the line :

C:\boot.mbr="Ubuntu Linux"

At the  next boot I see the option Ubuntu Linux but when I chose it, it just displayed "GRUB" and froze there.

Obviously something I did sth wrong but just can't figured it out.

Is there anyway to know if the .mbr file is good ?

In ubuntu my boot hardisk is listed as hdc  but I see hdc1, hdc2, hdc3 (swap..) should I do *dd if=/dev/hdc* or should I use *hdc1* ?

Well if anyone knows the answer plz help or if there's a simpler way to do it ?

I don't really want to mess up with my XP MBR or run into a chance of loosing my RAID since I have important datas on it.

Sorry for the long post, I did try to google the answer but it came up with what I did so I am kinda stucked ...


Thank you for your help

---

### Post by Kamping_Kaiser on 2005-05-25
[QUOTE=vfactor]Hi all


In ubuntu my boot hardisk is listed as hdc  but I see hdc1, hdc2, hdc3 (swap..) should I do *dd if=/dev/hdc* or should I use *hdc1* ?

Well if anyone knows the answer plz help or if there's a simpler way to do it ?

I don't really want to mess up with my XP MBR or run into a chance of loosing my RAID since I have important datas on it.
[/QUOTE]

I'm not entirely sure, but if you enable the disc ubuntu is on, and use the live cd to "rescue" grub, does that detect the raid XP?
As for the DD this or that, hdc1 would be the ubuntu root partition, so you probably dont want a dd of that.

Sorry if this hasnt realy helped....

---

### Post by sebastyan on 2005-05-25
Try to install Ubuntu loader on teh same drive with windows ( MBR ) this should work !

---

### Post by vfactor on 2005-05-25
Thanx for the quick answer.

I am scared to mess up with windows MBR since I read that a lot of people have problem restoring it to the original state.

Does Ubuntu automatically mount floppy drive to /media/floppy or should I mount it manually ?

Is there a third party boot loader (boot from floppy for example ) and let you choose whether to boot from SATA RAID or IDE hard disk like Bios but on the fly ?

Thank you

---

### Post by vextorspace on 2005-05-25
When you set it up to boot the windows drive first, you switched the boot order of the drives so the window drive comes first, right?  I am pretty sure this changes the designation of the drives in grub.  Do you get a chance to enter into the grub menu through escape before it hangs?  If so, then I would say switch the drives in bios, boot your ubuntu, do a less /boot/grub/menu.lst and write down the ubuntu entry.  Then reboot, switch the bios to boot the windows drive but ask it to boot ubuntu.  Hit escape to get the grub menu, and type the commands for ubuntu from the grub menu, only replacing the (hd0,#)'s with (hd1,#)'s.  If this boots, change the entry in the menu.lst. on your ubuntu partition.  I think you have to also setup grub which you do with a 
sudo grub
setup (hd1) if you booted with the windows drive first, or setup (hd0) if you booted with the ubuntu drive as the primary drive.

The other way to deal with this situation is to boot the ubuntu drive first, and put a windows entry in grub, using grub for your bootloader.  Since windows doesn't like it's boot drive to be 2nd in the hard drive chain, you have to put
map (hd0) (hd1)
map (hd1) (hd0)
entries in your menu.lst for the windows option.


-Doug

[QUOTE=vfactor]Hi all

I am a complete Linux newbie trying to set up my system dual boot Xp and Ubuntu.  Here's my situation:

I have XP installed in Raid0 SATA (build in controller).  I installed ubuntu on an independent IDE HD .  During installation, Ubunto never asked me to make dual boot. I guess because it didn't recognize XP on the SATA RAID.

I can boot into Ubunto w/o problem or XP (changing boot selection in Bios). Now I would like to make a dual boot loader.

I searched the net and I decided to go with the boot.ini (windows XP) modification since I probably use windows more at this stage.

So I did the **dd** command to make a boot.mbr file and copied it to C:\  (windows XP). I also modified the boot.ini by appending the line :

C:\boot.mbr="Ubuntu Linux"

At the  next boot I see the option Ubuntu Linux but when I chose it, it just displayed "GRUB" and froze there.

Obviously something I did sth wrong but just can't figured it out.

Is there anyway to know if the .mbr file is good ?

In ubuntu my boot hardisk is listed as hdc  but I see hdc1, hdc2, hdc3 (swap..) should I do *dd if=/dev/hdc* or should I use *hdc1* ?

Well if anyone knows the answer plz help or if there's a simpler way to do it ?

I don't really want to mess up with my XP MBR or run into a chance of loosing my RAID since I have important datas on it.

Sorry for the long post, I did try to google the answer but it came up with what I did so I am kinda stucked ...


Thank you for your help[/QUOTE]

---

### Post by djpharoah on 2005-05-25
its kinda tricky when u have your linux partition on another physical drive.

However its very simple should you know what your hdds are labelled as in grub.

```
sudo nano -w /boot/grub/grub.conf
``` 

that line should get the grub.conf file.

to add windows xp into your bootloader config file this is the code you add to the grub.conf

```
title=Windows XP
root (hdx,x)
makeactive
chainloader +1
``` 

NOTE: the line "root (hdx,x) has to be changed to whatever hdd the windows partition is on. If windows is on its own then the partition is 0, and since its raided the hard drive would prolly be sdx, since that indicates scsi/sata

gl

---

