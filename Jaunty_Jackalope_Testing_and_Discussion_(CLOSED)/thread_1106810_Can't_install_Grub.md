---
title: "Can't install Grub"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Melhisedek on 2009-03-26
Hello there, just tried latest daily build of Jaunty and wanted to install it, everything went fine except the install GRUB part :/ It said it can't install it to master boot record and that it is a fatal error.

Any ideas why?

I have Vista 64 Ultimate installed as well.
Thank you for your time!

---

### Post by loomsen on 2009-03-26
Did you format your /boot partition as ext4? Won't work then, try assignning a smaller ext2/ext3 partition, about 500MB should work then I think...

---

### Post by philinux on 2009-03-26
> **Melhisedek said:**
> Hello there, just tried latest daily build of Jaunty and wanted to install it, everything went fine except the install GRUB part :/ It said it can't install it to master boot record and that it is a fatal error.

Any ideas why?

I have Vista 64 Ultimate installed as well.
Thank you for your time!

Why not install grub to the / partition of your dual boot and use easybcd to modify vista's bootloader, leaving the mbr intact.

---

### Post by Melhisedek on 2009-03-26
Both of you just lost me :/ I think I'll wait for the beta and graphical release and hope it will work than

---

### Post by wjp.reg on 2009-03-29
> **loomsen said:**
> Did you format your /boot partition as ext4? Won't work then, try assignning a smaller ext2/ext3 partition, about 500MB should work then I think...

I installed 9.04 beta last eve and selected ext4 for separate /boot, /, and /home partitions.  As mentioned above, it was a no go for grub on my 100MB /boot partition (grub error 16).  I wish I new about this problem before hand.  I tried to reinstall grub, to no avail, and ended up reinstalling, changing /boot back to a 100MB ext3 partition and this time grub was operating as it should.

I checked launchpad but did not see the grub error listed for Jaunty.  Should I report this?

Thanks,

---

### Post by Melhisedek on 2009-03-30
Well I tried again today, I was using inbuilt partitioner and setting it to install Linux on the "Largest free place" (about 100Gig).

It created / as ext3 and created about 500mb of swap. I got the same error again, fatal error on disc hd0.
I tried again and at the end of the installation process I chose advanced and set loader to install to dev/sda and still got a same error.

Any ideas good folks? :D

---

### Post by Melhisedek on 2009-03-30
bump

---

### Post by element_G on 2009-03-30
I have jaunty on two machines, only one of them had this issue but here is what I did:

After I got the grub error from ubiquity (the installer on the live CD), I installed gparted in the livecd and took a look at my drive. Apparently the partition I installed to (a single ext3) was "unformatted" (gparted showed a black color). So what I did was I used gparted to delete this partition and make a new ext3. Then I installed through ubiquity making sure that the format chekcbox was not checked when selecting a partition to be / .

---

### Post by Melhisedek on 2009-03-30
can I install gparted with "normal means" 

> sudo apt-get install gparted

while not having anything else installed (booted on LiveCD) ?

---

### Post by gaspard.leon on 2009-03-30
If you can't use gparted from the Ubuntu LiveCD there are heaps of live cds that include Gparted, for example:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Melhisedek on 2009-03-30
> **element_G said:**
> I have jaunty on two machines, only one of them had this issue but here is what I did:

After I got the grub error from ubiquity (the installer on the live CD), I installed gparted in the livecd and took a look at my drive. Apparently the partition I installed to (a single ext3) was "unformatted" (gparted showed a black color). So what I did was I used gparted to delete this partition and make a new ext3. Then I installed through ubiquity making sure that the format chekcbox was not checked when selecting a partition to be / .

Did exactly like you said and still no go :(

---

### Post by Melhisedek on 2009-03-31
bump

---

### Post by mhenriday on 2009-03-31
**Melhisedek**, if nothing else seems to work, you could try re-installing **Hardy**, updating, and then upgrading to the **Jaunty** beta. In my experince, **GRUB** is preserved....

Henri

---

### Post by Melhisedek on 2009-04-01
Sadly its a no go. Tried installing 8.10 but still the same error, tried creating just one partition ext3 with no swap and still same problem :/ Can it be some BIOS setting or some hardware trouble?

Can I install grub from Windows somehow or from bootable disc, just GRUB and than see if Ubuntu can install over it. This is driving me crazy :(

---

### Post by element_G on 2009-04-01
you can try installing EasyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) from windows (don't know much about it, but is an alternative to GRUB) or try using the Super Grub Disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by loomsen on 2009-04-01
> **Melhisedek said:**
> Sadly its a no go. Tried installing 8.10 but still the same error, tried creating just one partition ext3 with no swap and still same problem :/ Can it be some BIOS setting or some hardware trouble?

Can I install grub from Windows somehow or from bootable disc, just GRUB and than see if Ubuntu can install over it. This is driving me crazy :(

So, did u have any non Vista (Linux, XP, ME---) installed before?

Ugly as can be, if you happen to have a Samsung Notebook purchased after 09/2008, you could suffer from a Vista recovery partition which is written to the BIOS.

We tried everything, straight down to nukeing the disk. But as the recovery partition isn't written to the disc... 

However, if you didn't have any prior linux installed, I seriously wouldn't recommend going with the beta. Cause you'll most likely end up exactly......... -> HERE.

(Try booting with acpi=off noapic nolapic)

You should be able to boot a livecd if you pass this flags (At the menu, hit F6 and <Space> for every option, a X will appear next to it.)

But, even tho it will prlly let u boot, you won't have acpi support... So no backlight reducing, no resolution switching, no volume altering and most of all not even a power manager. If you pull the AC your notebook will simply turn off immediately.

--> No Fun At All

(You can check your BIOS for an entry like "Purchase Date: 09/2008")
But if you can't boot any other than Vista, this most likely will be it.



--------> If you think none of the above applies, get:
```
sudo apt-get install mbr
```

from a live CD.  To install the Master Boot Record, run:
```

sudo su -
install-mbr /dev/(h|s)da1
```

Just enter what applies to you, /dev/sda1 or /dev/hda1

*I'm not responsible for any broken/breaking Partitiontables, you should know what you're doing dealing down there imho. Same applies for alpha/beta/prereleases, again imho*

---

### Post by Melhisedek on 2009-04-02
No it is not Notebook, it is PC that I put together, Abit P5Q Deluxe, C2Duo E8400 CPU and 4 gig RAM.

Only thing installed on my disc is Vista Ultimate 64. I have another SATA disc and even one IDE that is not connected atm. 

I followed advice above and went with 8.10 version which is not beta but the same problem applied. I've checked google and this has happened before but everyone got around it differently, like some resized partition and it worked, some tried installing without swap and it worked, some resized swap and so on. If I understand correctly GRUB doesn't format partition as it should and hence the error as it can't install. I'll try it once more later today and dig up some threads for you guys to check out. Sadly I don't dare install "mbr" as I'm afraid I'll nuke my Windows partitions (a lot of data)

---

