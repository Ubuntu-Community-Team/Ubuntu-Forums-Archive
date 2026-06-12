---
title: "Boot Error from flash drive 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ScottG89 on 2011-04-29
I downloaded 11.04 last night and installed it onto a flash drive, but after I restart the computer and select the USB to boot first, it comes up with a boot error. I tried this on another computer to see if the iso didn't install right but it works completely fine. I don't know what else to do. I tried reinstalling the iso and redownloading also just for the hell of it.

---

### Post by ajgreeny on 2011-04-29
What is the boot error you get?

Without knowing that, you are not going to get much help here.

It's a bit like telling your garage that your car is not going, and expecting them to tell you why  not before they've even seen it.

---

### Post by ScottG89 on 2011-04-29
All it says it boot error on a black screen, nothing else at all

---

### Post by jiapei100 on 2011-05-29
Hi, ScottG: I've got exactly the same problem as yours.

I'm using a USB 2.0 interface, but my USD flash drive is USB 3.0 compatible? Is it a problem from Ubuntu 11.04? Or from USB itself?

Rgds
Pei

> **ScottG89 said:**
> I downloaded 11.04 last night and installed it onto a flash drive, but after I restart the computer and select the USB to boot first, it comes up with a boot error. I tried this on another computer to see if the iso didn't install right but it works completely fine. I don't know what else to do. I tried reinstalling the iso and redownloading also just for the hell of it.

---

### Post by jiapei100 on 2011-05-30
Is it possible that it has something to do with the file format? 'cause I format the flash drive to EXT4, maybe to use the flash drive as a bootable drive, I need it to be formated into FAT ??

A bit weird and unclear. Can anybody give me a hand?

Thanks...

Best Regards
Pei

> **jiapei100 said:**
> Hi, ScottG: I've got exactly the same problem as yours.

I'm using a USB 2.0 interface, but my USD flash drive is USB 3.0 compatible? Is it a problem from Ubuntu 11.04? Or from USB itself?

Rgds
Pei

---

### Post by t.h.w. on 2011-08-09
Same here...

Works fine with 9.10, but not with 10.10 and 11.04... 

(I use the USB Startup Disk Creator in 9.10)

Found possible solution:
type 'live'

See also: 
[http://forums.linuxmint.com/viewtopic.php?f=46&t=60133&p=343962](http://forums.linuxmint.com/viewtopic.php?f=46&t=60133&p=343962)

---

### Post by ottosykora on 2011-08-09
@scottg89

installed on flash drive... well you might tell what exactly did you do, where did you install the grub bootloader.

The usb stick has to be bootable first , still many are not when you buy them, they just have fat32 partition with no mbr on it.
Sometimes I have to use the HP usb formating tool to have at least some mbr space on the stick for potential installer then.
[http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)


So when you did format it, was it done with the ubuntu instaler? And did you select the right drive to install the grub?

---

