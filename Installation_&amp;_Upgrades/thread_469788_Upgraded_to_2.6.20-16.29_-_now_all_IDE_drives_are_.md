---
title: "Upgraded to 2.6.20-16.29 - now all IDE drives are seen as SCSI and DMA won't work"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by ishw on 2007-06-10
Yesterday did upgrade from 2.6.20-16.28 to 16.29.  Previous to this, I had DMA on on the DVD, and it worked well.  Now...

$ sudo hdparm -d1 /dev/dvd
/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

So the IDE DVD is seen as a SCSI, and therefor can't have DMA enabled.  From what I understand, people have experienced this problem and fixed it with the upgrade to 16.29.  Instead, 16.29 broke mine.

Please help, no dvd = very pissed off wife.

What other outputs do you want to see?

$ sudo hdparm /dev/dvd
/dev/dvd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

$ sudo hdparm -I /dev/dvd
/dev/dvd:
 HDIO_DRIVE_CMD(identify) failed: Input/output error

$ sudo hdparm -i /dev/dvd
/dev/dvd:
 Model=Pioneer DVD-ROM ATAPIModel DVD-106S 0114, FwRev=E1.14   , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

---

### Post by tgalati4 on 2007-06-10
Assuming you are using Grub to boot, you should be able to boot into your previous kernel to get the DVD working and then file a bug in the meantime until the next kernel rev fixes it.  You probably aren't the only one with this problem.

---

### Post by chalewa on 2007-06-10
yep same problem over here

---

### Post by chalewa on 2007-06-10
hmm well i just tried to revert back to 2.6.20-15.29 and the same problem is still ocurring...

---

### Post by ishw on 2007-06-10
Yes, using grub and booting to the older kernels doesn't work, the problem is still there.

---

### Post by NfF on 2007-06-10
well, best,but troublesome solution is to uninstall the IDE drivers,and install it together with the kernel. Or try uninstalling Ubuntu, and use the new kernel as default.

and anyway, ive messed up my ubuntu kernel. Where'd u get the Gnome(terminal) patches? could u pls reply with a link to a download web?and anyway, i need to upgrade my kernel, cuz the ndiswrapper(driver for windows hardware to function in ubuntu) needs a newer version of kernel. 

pls pls and also howd u upgrade the kernel? just copy and paste instructions.,

---

### Post by chalewa on 2007-06-10
> **NfF said:**
> well, best,but troublesome solution is to uninstall the IDE drivers,and install it together with the kernel. Or try uninstalling Ubuntu, and use the new kernel as default.

and anyway, ive messed up my ubuntu kernel. Where'd u get the Gnome(terminal) patches? could u pls reply with a link to a download web?and anyway, i need to upgrade my kernel, cuz the ndiswrapper(driver for windows hardware to function in ubuntu) needs a newer version of kernel. 

pls pls and also howd u upgrade the kernel? just copy and paste instructions.,


what

---

### Post by bierholen on 2007-06-10
I also have the same problem with my DVD burner.

1. Kernel 2.6.20-15: /dev/scd0 > burner couldn't burn anything

2. Kernel 2.6.20-16.28: /dev/hdc > burner was fine

3. Kernel 2.6.20-16.29: /dev/scd0 > burner can't burn anything any more


I don't understand why it switches back and forth. I was happy that the kernel update to 2.6.20-16.28 had fixed my problem of not being able to burn anything. Now I have the same problem again.

---

### Post by psiu on 2007-06-10
A related error is hddtemp not working again on my laptop--it initially didn't work--then the kernel update enabled it (drive appearing as hda not sda) and now it's back to...not there.

---

### Post by armalite on 2007-06-11
> **psiu said:**
> A related error is hddtemp not working again on my laptop--it initially didn't work--then the kernel update enabled it (drive appearing as hda not sda) and now it's back to...not there.

You could try adding "-w" to this line to /etc/default/hddtemp.

Old /etc/default/hddtemp:
```
OPTIONS=""
```

New /etc/default/hddtemp:
```
OPTIONS="-w"
```

And restart the hddtemp daemon:

```
sudo /etc/init.d/hddtemp restart
```

I found that this solved the reading temperature error i had with Feisty when I installed it, and still works after the 2 kernel upgrades (sda to hda and back).

---

### Post by ishw on 2007-06-11
But back to the question at hand...

What are the options for getting DMA enabled?

1) Anyway to get these drives back to IDE settings?
2) Anyway to enable DMA on the SCSI (but really an IDE) drive?
3) A kernel compile turning off SATA and enabling PATA as suggested by eleon216 in the original bug reported 4/27/07 - [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110636]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110636")
--- I tried this and it didn't work, all my drives were still seen as SCSI.
4) Reinstall off CD?  I'm afraid if I even go through the trouble of this that I won't be able to do an upgrade so I'm stuck with the CD kernel.  Is there anyway to just upgrade to the 16.28 but ignore the 16.29?

I wasn't kidding, my wife is really pissed about the DVD not working.  I need some serious help here.

---

### Post by Kuoi on 2007-06-12
Maybe you can try the following :

Type in terminal > sudo gedit /boot/grub/menu.lst

Now open nautilus and browse to folder "/boot/grub" , now open the following file "menu.lst.backup" OR "menu.lst~" OR "menu.lstbkup".

Look in one of the files at the bottom if you see you kernel  "Kernel 2.6.20-16.28"

Copy the hole line ... must be something like this ( lok out , this is an old one from mine ) > title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8d407c6e-9fdf-483b-b880-64b723da4a42 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

and paste your line in the "menu.lst"file you've opened with terminal .

Save this file , close everything and if you restart now , you should have an option to select the 2.6.20-16.28 kernel.
Boot this one , and let's hope it works well.

Hope this helps , Kuoi

BTW : If all works well , you can edit the " menu.lst" file again , and delete the lines from the kernel that isn't working.

---

### Post by rjtd on 2007-07-01
Same problem here.
IDE access makes my PC crawl down, because I can't enable DMA.
My IDE drives are now being detected as SCSI.
Any real fix for this?

---

### Post by deepclutch on 2007-07-01
the solution is to have old pata drivers to get working for our ide dvd/cd optical drives.but the $$$ question is how to achieve this?
as for me,i am getting some transfer error with pata drivers and changed to libata bcoz of a kernel boot option "irqpoll".
for the problem is with ata_piix or some BIOS settings :?
You can sure achieve that to get old parallel ata drivers work with some boot options may be which can be researched in ur linux-source extracted  Documentation/kernel-parameters.txt or gotohttp://www.linuxhq.com/kernel/v2.6/20/Documentation/kernel-parameters.txt

[http://www.linuxhq.com/kernel/v2.6/20/index.html](http://www.linuxhq.com/kernel/v2.6/20/index.html)
 [http://kernelnewbieswiki.org](http://kernelnewbieswiki.org)
yea.me too waiting for a soltn :(

---

### Post by SergeiFranco on 2007-07-10
This is exact same problem as I have (and many other people). It happened since Feisty release.
Here is the thread I made couple of month ago. [http://ubuntuforums.org/showthread.php?t=458873](http://ubuntuforums.org/showthread.php?t=458873) 
That is right, this problem has been awhile. Actually since they decided to drop old IDE drivers and rely on libata (which obviously works poorly with some IDE controllers).
Developers please fix this or make a workaround to have my IDE drivers as hdX (so I can use hdpram to force them to use 32bit and DMA).

Thank You.

---

### Post by geeforce on 2007-07-11
Yeah it's a shame that the people working for Ubuntu can't solve that problem. Even Gutsy has the same problem.

Debian is able to mount them as hdc etc. but missed the ip2200BG driver. Where's the humanity everyone is talking about?

It really can't be that hard!

---

### Post by deepclutch on 2007-07-13
yeah.Debian works gr8 with ide drives too.

---

### Post by Nortonw on 2007-07-13
Any Fix for this ??

---

### Post by hanzomon4 on 2007-08-25
Any fix for this?

---

### Post by cobelloy on 2007-09-14
yes, same drama here too - need a fix for this please.

my ide dvd burner is labelled /dev/scd0 and does not work properly, works fine in every other distro I tried as /dev/hdx

and I have a stupid proprietary wireless modem I cant replace that only works in ubuntu feisty - so swapping distros is out of the question too

come on! there are a lot with this same problem, how about a fix or a workaround?

---

### Post by cobelloy on 2007-09-28
I installed kernel 2.6.17-50-general and the dvd is recognised correctly and works fine, no other problems have arisen as yet as a result of kernel change.

---

### Post by tomski on 2007-10-01
I have just upgraded to gutsy and all my drives are the same all listed as sda,b,c,d instead of hda,b,c,d

Fix please anyone

---

### Post by grendelkhan on 2007-10-09
FWIW, libata is so flaky on my feisty box, that if I enable DMA, and I push any amount of data through that drive it crashes.  I've been living with this since feisty and it's driving me nuts that this is still an issue.

---

### Post by bPawn on 2007-10-20
any news? the problem is still here. Gutsy fully updated

---

### Post by grendelkhan on 2007-10-20
Well fudge.

---

### Post by the stench on 2007-11-06
Kernel 2.6.20-16-generic worked for me.

---

### Post by deepclutch on 2007-11-07
or better someone help preventing sr_mod being loaded first and ide-cd be the default.is it something to do with the initrd image :( i  need help.both on my debian sid and Ubuntu.please someone help out as in FOSS spirit :) .

---

