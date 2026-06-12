---
title: "Grub question regarding dual boot."
date: 2009-11-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-11-05
Have karmic on disk one with grub installed to mbr.

Put karmic to upgrade to lynx on disk two with grub on sdb1. Should I have put grub on sdb at the advanced install phase?

---

### Post by cariboo on 2009-11-05
If you install on two separate disks, yo may run in this bug #[lpbug]420933[/lpbug]

---

### Post by philinux on 2009-11-05
Ok I'll leave grub on sdb1 pbr then. Seems to work fine, apart from the blocklists warning.

---

### Post by xebian on 2009-11-05
you can always install anytime

grub-install /dev/ur-dev-name

---

### Post by ssam on 2009-11-05
i found that karmic's installer likes to put grub on mbr no matter what you tell it. messed up my nice chainloading multiboot system.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/409575](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/409575)

i think linux distros should always install grub onto their own partition, and then put a grub on mbr that chainloads the other partitions. make sure each distro can update its own grub when there is a kernel update.

---

### Post by philinux on 2009-11-05
> **ssam said:**
> I found that karmic's installer likes to put grub on mbr no matter what you tell it. .

I clicked Advance at stage 8 and told it to use sdb1 and it did I think. How can I tell?

---

### Post by ssam on 2009-11-05
> **philinux said:**
> I clicked Advance at stage 8 and told it to use sdb1 and it did I think. How can I tell?

that what i did, but for me it overwrote the existing grub1 installed there, with entries to chainload each partition.

---

### Post by VMC on 2009-11-05
> **philinux said:**
> I clicked Advance at stage 8 and told it to use sdb1 and it did I think. How can I tell?

Is stage 8 during the install process?

To check if its really on you pbr try chainloading it.

---

### Post by ronacc on 2009-11-05
the ubuntu installer is definately not putting grub where you tell it to , I have been playing with this for days , it seems that ubiquity (the karmic version at least ) is putting grub2 in the mbr of hd0 no matter what you tell it .I have done 4 fresh installs from the karmic release cd and have tried several different ways to get it to put grub on the 2nd hard drive ( ide secondary slave ) I have tried telling the installer  to put it on sdb twice, sdb1 once and hd1 (by manualy typing that in ) once . also when you select advanced on the last page of the installer (stage 8 ) (hd0) is already filled in on the entry line but if you click on the dropdown box the drives are listed as sda ,sdb , etc . and furthermore if after booting to desktop if you mount a drive via place>computer it identifies itself as XX gb  filesystem which also is what is shown on the tab when you open the partition with nautilus which however shows the UUID in the window title , none of which necessarily correspond to the drive order as listed by the bios of the box . this is unmitigated CRAP , they need to pick one thing and Identify the drives in ONE SINGLE WAY everywhere . this hdx,y  here uuid there and sdxy someplace else is ......   .

---

### Post by philinux on 2009-11-05
> **ronacc said:**
> the ubuntu installer is definately not putting grub where you tell it to , I have been playing with this for days , it seems that ubiquity (the karmic version at least ) is putting grub2 in the mbr of hd0 no matter what you tell it .I have done 4 fresh installs from the karmic release cd and have tried several different ways to get it to put grub on the 2nd hard drive ( ide secondary slave ) I have tried telling the installer  to put it on sdb twice, sdb1 once and hd1 (by manualy typing that in ) once . also when you select advanced on the last page of the installer (stage 8 ) (hd0) is already filled in on the entry line but if you click on the dropdown box the drives are listed as sda ,sdb , etc . and furthermore if after booting to desktop if you mount a drive via place>computer it identifies itself as XX gb  filesystem which also is what is shown on the tab when you open the partition with nautilus which however shows the UUID in the window title , none of which necessarily correspond to the drive order as listed by the bios of the box . this is unmitigated CRAP , they need to pick one thing and Identify the drives in ONE SINGLE WAY everywhere . this hdx,y  here uuid there and sdxy someplace else is ......   .

Hi Ronnac, glad you joined the party,

It was, when I had grub-legacy Jaunty on sda as I was chainloading into Karmic's grub2 on sdb1. Now I dont get the second grub menu for sdb1 so whats happening? It just boots lucid from the grub2 on sda or hd0.

Maybe this is the way to go for dual boot.

This is what I get from lucid.
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-2-generic
Found initrd image: /boot/initrd.img-2.6.32-2-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda1
done
```

---

### Post by ronacc on 2009-11-05
In my case karmic was already on sda (hd0) and I put lucid on sdb (hd1) , I can add a stanza to the karmic grub.cfg and boot into lucid but booting at all from the mbr on sdb is a no go . If I try it gives me "grub loadingread error" which I believe comes from the grub legacy still there from jaunty .see my thread " a cautionary tale " elsewhere in this forum . If you notice a difference in drive #s between that thread and this one its because in between reinstall 2 and 3 I moved the drives around in the box to see what difference that made .

---

### Post by philinux on 2009-11-06
Yep, just to clarify.

I've got Karmic on disk 1 and lucid on disk 2.
The installer put all the correct files into /boot/grub on disk2. Just dont know if it put grub on /dev/sdb1.

Now when I boot up the os prober has successfully put the stanzas in for lucid including recovery modes. Selecting lucid boot it up fine.

But I never see the grub menu from disk2 lucid, as you would expect. I guess I would have to set up a chainload/configfile for it from the grub on disk 1.

---

### Post by ronacc on 2009-11-06
my /boot/grub files are going to the right place and they are showing the correct uuid,s and drive designations , it is the portion of grub that goes in the mbr that is not being written to the right place.If I set that drive to be the 1st boot drive using the bios boot order It doesn't even get as far as the grub menu .

---

### Post by philinux on 2009-11-06
> **ronacc said:**
> my /boot/grub files are going to the right place and they are showing the correct uuid,s and drive designations , it is the portion of grub that goes in the mbr that is not being written to the right place.If I set that drive to be the 1st boot drive using the bios boot order It doesn't even get as far as the grub menu .

Right I might try then next reboot.
Meanwhile boot_info_script says

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

---

### Post by ronacc on 2009-11-06
boot_info_script ? where did you find that ? I was looking for something like that , I used super grub disk to figure out which grub was where . also does boot_info_script understand grub2 ? I searched synaptic and didn't see it .please attach the script so I can try it .

---

### Post by VMC on 2009-11-06
> **ronacc said:**
> boot_info_script ? where did you find that ? I was looking for something like that , I used super grub disk to figure out which grub was where . also does boot_info_script understand grub2 ? I searched synaptic and didn't see it .please attach the script so I can try it .

Good question, because "sudo find / -name *boot_info_script* -print"
finds nothing.

---

### Post by philinux on 2009-11-06
> **ronacc said:**
> boot_info_script ? where did you find that ? I was looking for something like that , I used super grub disk to figure out which grub was where . also does boot_info_script understand grub2 ? I searched synaptic and didn't see it .please attach the script so I can try it .

No worries. Although the info to run it is wrong. I run with this.
sudo ./boot_info_script032.sh

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

According to this it can find grub2. Seems to fail on me.
[http://www.boot-land.net/forums/index.php?showtopic=7851](http://www.boot-land.net/forums/index.php?showtopic=7851)

---

### Post by ronacc on 2009-11-06
thanks , gotta leave 8 minutes ago :D I'll get it and try it when I get back .

---

### Post by ranch hand on 2009-11-06
I am not sure that the script is up to date in relation to grub2.  Grub2 may be not "known" to it.

---

### Post by philinux on 2009-11-06
> **ranch hand said:**
> I am not sure that the script is up to date in relation to grub2.  Grub2 may be not "known" to it.

Here's an extract.
```
############### List of files whose contents will be displayed.
Boot_Files="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    **/grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg**
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    boot/kernel*.img
    "
```

---

### Post by ranch hand on 2009-11-06
I have not, I admit, looked at it lately.  Nice to see those boys are on top of things.  That is one handy bugger.

---

### Post by philinux on 2009-11-06
> **ranch hand said:**
> I have not, I admit, looked at it lately.  Nice to see those boys are on top of things.  That is one handy bugger.

Yes but take a look at post #14 and it's output.:confused:

---

### Post by philinux on 2009-11-06
Ok part solved.

From the grub2 community documentation on "Custom Menu Entries" I added these line to /etc/grub.d/40_custom. This now gives me the grub2 menu from sdb1. So during the install to sdb grub was installed to sdb1.
Question is what would have happened if I'd have installed grub to sdb mbr.

All I need now is to get rid of the osprober entries. More reading.

#```
!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Grub on sdb1" {

      set root=(hd1,1)

      chainloader +1

      }
```

Fully solved.

Added this line to /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true
```

Now that wasn't too bad. I've got the same structure as I had with menu.lst

If I had not done this I would have had to remember to run update grub on karmic everytime lucid got a grub update.

---

### Post by ranch hand on 2009-11-06
> **philinux said:**
> Ok part solved.

From the grub2 community documentation on "Custom Menu Entries" I added these line to /etc/grub.d/40_custom. This now gives me the grub2 menu from sdb1. So during the install to sdb grub was installed to sdb1.
Question is what would have happened if I'd have installed grub to sdb mbr.

All I need now is to get rid of the osprober entries. More reading.

#```
!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Grub on sdb1" {

      set root=(hd1,1)

      chainloader +1

      }
```Fully solved.

Added this line to /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true
```Now that wasn't too bad. I've got the same structure as I had with menu.lst

If I had not done this I would have had to remember to run update grub on karmic everytime lucid got a grub update.
If you add these to your 40_custom there is no need to ever update them.  These are my Lounge Lizard installs but it works just as well for Kinky Kitty.

If you save the 40_custom file as 06_custom it will put those entries on the tope of your menu on the screen.

With your case I would leave the 40_custom file that you have where it is so that you don't have the chain load stuff in your menu.  That way 06 is clean.
EDIT
I can't boot to my sdb drive either.  I think I may have to try this stuff of yours and see if it works.

Do you use RAID?  I do not and have thought that this might be part of the problem.  I am not going to use RAID.

---

### Post by philinux on 2009-11-06
No raid and the grub2 menu that comes up from disk 1 is just as i want it.

Karmics kernels first then the entry "Grub on sdb1" nicely chainloads into grub2 on disk2.

---

### Post by ranch hand on 2009-11-06
Yup gonna try this.

I have change my testing plan and am not screwing with 32bit so I can use both internal drives for "normal" stuff.  It would be nice to be able to boot both from one menu now.

---

### Post by ronacc on 2009-11-06
back home and got a chance to run boot_info_script032.sh . thanks philinux , I'm going to keep that in my tool kit .The results confirmed what I suspected grub2 only installed on sda . unknown grubs on sdb ,c,d  . sdb should also be grub2 , sdc and d should be grub legacy . confirmed this by switchng around the boot order in bios to try to boot from each drive , only sda had a working grub of any version and I could use it to boot into any of my 4 installs by selecting from the menu . sdb when set in bios to boot gives "grub loadingread error" ,sdc and sdd give nothing but a blinking cursor after the post finishes no message of any kind . sdc and sdd did have working grub legacy installed in the mbr , where the heck did they go ? sdb did have a working grub legacy that should have been replaced with grub2 when I installed "lucid".I had a mobo failure on this box during the last couple of weeks of karmic and now have a spare mobo that I'm not fond of installed , my gigabyte mobo will be back from warranty soon and when I install it I am going to start fresh  , I'll format all 4 install drives and see what happens when I put a different install on each , thats the luxury of having a test box , you can play some real games:lolflag:

---

### Post by ranch hand on 2009-11-06
@ronacc
Yup, REAL games.

Big FUN.

---

### Post by philinux on 2009-11-07
To Ronacc and RH,

Fun and games indeed. I'm getting the hang of grub2 now. Bit of a learning curve eh boys. :lolflag:

---

