---
title: "ubuntu 9.10 live usb does not persistent"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by hugebrush on 2009-11-21
I created a ubuntu 9.10 live usb by usb-creator, it does not persistent changes between boot up. Usb-creator created casper-rw file in the root folder of the live usb, but it does not be mounted after boot from the live usb.

---

### Post by teachop on 2009-11-21
Yes same experience here.  I figured I had messed it up, until your message.  This was true on several sticks, never worked.

---

### Post by gammonjosh on 2009-11-27
I have no problems getting 9.10 to boot with persistent off.  But it seems imposable to get it to boot with it on.  I've tried creating it both from windows xp, and ubuntu's usb start up disk creator.  I've partitioned my usb stick, modified files, etc but nothing has worked.  If anyone has made it work please post detailed instructions. ;)
Cheers,

---

### Post by Rescue9 on 2009-11-28
Same thing here. Plus, the audio that I read worked on my MSI GT735 does not work. I'm thinking about going back to 9.04 persistent.

---

### Post by wilee-nilee on 2009-11-28
To get the persistent you don't partition use the slider at the bottom after ticking stored in the extra space. You want that slider just barely short of fully to the right. and unetbootin doesn't have a persistent pass the session use as far as I know.

---

### Post by phillw on 2009-11-29
Hi, from memory, the default make usb-stick from the menu is  NOT persistant.

A great series of HowTo's for all sort of wied and wonderful things you can legally do with a usb pendrive is over here -->>  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It covers such delights as slicing a pen-drive, using gparted on it & even doing a dual boot one !!

Regards,

Phill.

---

### Post by hugebrush on 2009-11-29
Now I found my ubuntu 9.10 live usb only has persistent problem on my DELL inspiron 710m notebook, it worked fine on my DELL optical GX620.

I created a custom live usb that install some additional packages and change the timezone to asia/shanghai, it worked fine on my Dell Optical GX620, but worked like a none customized live cd on my DELL inspiron 710m:confused:

---

### Post by hugebrush on 2009-11-29
Problem solved:
There is a "casper" folder without persistent config which extracted from none customized live cd image in root of the second partition of the hard disk on my Dell inprison 710m notebook, it always loads the "live ubuntu system" in this "casper" floder, even booting from an usb storage. remove this "casper" folder, the live usb works fine. I think it's a syslinux bug.

---

### Post by gammonjosh on 2009-12-01
> **phillw said:**
> Hi, from memory, the default make usb-stick from the menu is  NOT persistant.

A great series of HowTo's for all sort of wied and wonderful things you can legally do with a usb pendrive is over here -->>  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It covers such delights as slicing a pen-drive, using gparted on it & even doing a dual boot one !!

Regards,

Phill.
I've tried [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) with no luck, it will not boot pass the ubuntu logo.  This is the same no matter what method is used to install live usb to my usb stick.

---

### Post by zx5000 on 2009-12-31
It looks like 9.04 does not either. 

I just tested this. 

[LIST=1]
[*]I booted from 9.04 CD.
[*]Created a new USB stick with 3.6GB persisent size.
[*]Rebooted from the USB stick.
[*]Checked the Boot Options ( F6 see below) and the everything looked right.
[*]Opened openoffice created and saved a document in ~/Documents.
[*]Rebooted and the file was gone.
[/LIST]

```

noprompt cdrom-detect/try-usb=true persistent file=/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

```

---

