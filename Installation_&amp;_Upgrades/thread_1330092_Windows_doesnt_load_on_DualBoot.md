---
title: "Windows doesnt load on DualBoot"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by dilip123 on 2009-11-18
Hi,  just installed the latest ubuntu version after dividing up my old windows partition into a couple other ones. unfortunately, now windows vista doesn't load- it appears as Windows Vista (loader) in the boot menu, but when selected, the computer goes back to the dell startup screen and returns to the grub menu. the laptop is dell xps m1210. does anyone have solutions? ive tried startup repair from the vista CD a couple times. not working.
thanks

---

### Post by darkod on 2009-11-18
OK, number 1: If you tried startup repair with vista, even if it didn't succeed you might have damaged grub2 bootloader. First you have to tell us whether grub2 menu still loads up at boot.
If not, you need to start ubuntu with the CD and selecting Try Ubuntu option then read here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Item number 13, Reinstalling Grub2 from LiveCD.

If grub2 menu is still there but as you said ubuntu is working and vista not, just post back here and there are other steps to check it out.

And for future reference, you NEVER resolve grub problems with windows startup recovery process. It can only delete grub saving windows bootloader on top of it.

---

### Post by dilip123 on 2009-11-18
thanks, ubuntu is loading fine. vista is not. should i try reinstalling grub2 anyway just in case there is a problem there? or  is that not an issue

---

### Post by darkod on 2009-11-18
Since grub menu and ubuntu are loading fine it seems ok.
Now, open terminal, Applications -> Accessories -> Terminal and run:
sudo fdisk -l (that's small L)

It will give you information about your disk and partitions. Paste the result here.

You can also run
sudo update-grub

It will show few lines like found kernel, found vista loader on /dev/sda1. Paste the result here too. We'll know more after that.

---

### Post by dilip123 on 2009-11-18
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *        9469        9729     2096482+   b  W95 FAT32
/dev/sda3               8        5106    40957717+   7  HPFS/NTFS
/dev/sda4            5107        9468    35037765    5  Extended
/dev/sda5            5107        7783    21502971   83  Linux
/dev/sda6            7784        9185    11261533+  83  Linux
/dev/sda7            9186        9468     2273166   82  Linux swap / Solaris

Partition table entries are not in disk order


the ntfs partition is the vista one. the fat32 is mediadirect (irrelevant). 

for the second command:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

thanks

---

### Post by darkod on 2009-11-18
That's the problem, if you notice the * mark after /dev/sda2 that means is marked as boot, while vista should be on /dev/sda3.

It might be easier for you to create manual entry, otherwise you would have to turn your disk around. :) The partitions are very confusing, but I'm not used to branded machines, maybe that's why. :)

Mount /dev/sda3 (if it has a name just go in Places and click on it, it will ask for your ubuntu password once more and mount it. Then open it and see if file called bootmgr is present right there in the root of /dev/sda3 (not root of ubuntu).

If it's there I think I can figure out a manual entry for you. Grub2 is still new to me too.

PS. As you could see yourself, two entries for Vista were found. That means there should be two in your grub menu. I guess you tried both of them because it seems to me the second Vista entry should work fine.

---

### Post by dilip123 on 2009-11-18
ah. thanks a lot. bootmgr is indeed there. 
im sure its much much newer to me.

---

### Post by darkod on 2009-11-18
Well, this could do the same as the menu entry, just boot into dell logo, but lets try.

Open the file /etc/grub.d/40_custom with:
sudo gedit /etc/grub.d/40_custom

At the end add:

menuentry "Windows Vista (new)" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader /bootmgr
}

NOTE: In the above text you need to replace the CFFCFF... value with your /dev/sda3 partition UUID. You can get the UUID by running:
sudo blkid

Write the UUID as it is, small and capital letters make difference. After you put the above text and replace the value, click to save the 40_custom file and close it.

After that run again
sudo update-grub

Now you should have Vista (new) in the menu after you reboot and see if that works. If it does, we will get rid of the ones that don't work.

---

### Post by darkod on 2009-11-18
Sorry, something urgent came up, gotta go out. Hope it worked, if not we'll sort it out bit later. Maybe someone else will jump in too.

---

### Post by dilip123 on 2009-11-18
ok: this is what i get for sudo update-grub:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

windows vista (new) is there on the boot menu. but gives me: error- invalid signature when selected.
thanks

---

### Post by dilip123 on 2009-11-18
> **darkod said:**
> Sorry, something urgent came up, gotta go out. Hope it worked, if not we'll sort it out bit later. Maybe someone else will jump in too.
its ok, thanks for your help

---

### Post by darkod on 2009-11-18
Edit the 40_custom again but this time instead of chainloader /bootmgr try:
chainloader +1

You already probably figured out, after making changes to grub2 config files you need to run
sudo update-grub

always. See if that works.

---

### Post by dilip123 on 2009-11-18
thanks darkod, but still same issue with the Vista(new).

this may not be relevant but i forgot to mention last time that the sda2 when loaded now says Windows is resuming (and gives a loading bar) but then only goes to a black screen and stay that way. It wasnt this way before the changes to the file, before it tried to load Mediacenter but failed.

and you probably realized this, but my files i n the Vista section are all in tact as i can view them from ubuntu, its just booting.

---

### Post by dilip123 on 2009-11-19
bump.
any possible solutions?

---

### Post by darkod on 2009-11-19
There is confusion about why your partitions are created like that. I think grub2 simply can not "swallow" it.
How about trying this:
Use your vista dvd to repair the vista boot, that should resolve any possible issues with the windows boot process. I think the option was called Repair Computer or similar. Unfortunately most probably it will also erase grub2 from the MBR but that's not a disaster.
After that is done, install grub2 if necessary and see whether it will create automatic entry for vista that will just work as default.

---

### Post by darkod on 2009-11-19
What do you have on the /dev/sda2 FAT32 partition? By the numbers it looks like 2GB partition. What's there?

I think that partition might be confusing things but I can't be sure how it will affect your vista if you just delete it. That is one option. Do you use it at all?

---

### Post by dilip123 on 2009-11-19
the 2Gb is dell media direct, and yeah i was thinking of deleting it anyway since it doesnt start either. i think some boot files for the and vista may have gotten mixed up or something. ill try deleting tomorrow. 

I tried using Vista Start Up repair a couple times but it did nothing. at first it identified problems, but nothing was solved at all. 
ill get back here after deleting the sda2 partition. thanks

---

### Post by darkod on 2009-11-19
I was hoping that deleting that partition will help vista restore too, provided it doesn't mess up the vista installation and I don't see how it would do that. There is a very good tutorial for restoring vista with screenshots and everything here:
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

After deleting /dev/sda2 vista will have no option but to restore the bootloader and boot files on /dev/sda3 where they should be. And with no /dev/sda2 to create confusion I hope grub2 will pick up vista on /dev/sda3 straight away. That's my theory at least. :)

---

### Post by dilip123 on 2009-11-19
ah i see! im getting excited now :p, but i dont have time to try it now...ill try deleting and then try a start up repair. thanks

---

### Post by darkod on 2009-11-19
Don't forget, even if the procedure restores vista it will destroy grub2 on your MBR. Then you will have to run the procedure to reinstall grub2.
But restoring vista will be step forward, reinstalling grub2 afterwards shouldn't be a problem.

---

### Post by florus on 2009-11-19
What would happen if Dilip used gparted to set sda3 as a boot partition and remove the boot status from sda2 without formating anything? Could that work?

---

### Post by darkod on 2009-11-19
It's not just the boot flag. We also tried manual entries pointing directly to the partition, didn't work. Something is very fishy with the partitions. I would get rid of that one especially if it's not used.

---

### Post by dilip123 on 2009-11-20
:p:p:p it worked! and without even destroying grub. basically deleting media direct and running startup repair immediately fixed it (startup repair took 2 seconds). and both ubuntu and windows still work fine. so now ill just delete that Vista (new ) boot thing.

thanks darkod and also florus for your input.

---

### Post by hydrurga on 2009-11-20
I don't know if it's of any help to anybody but the Vista bootloader can be a bit problematic at times. When I ran Ubuntu along with Vista I used a program called EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) to manage the Vista bootloader and it made the whole process smooth.

---

### Post by darkod on 2009-11-20
Glad it worked. Enjoy it now, you deserved it. :)

PS. You can mark the thread solved, above the first post there are Thread Tools, you can do it there. It helps other people.

---

