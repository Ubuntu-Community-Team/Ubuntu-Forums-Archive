---
title: "Setting 'try Ubuntu' as default"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by Vulpus on 2013-04-23
When booting into Ubuntu on USB I get asked if I want to 'try Ubuntu' or Install. I don't want to install as I am using this on different PCs. Can I do something to remove this question every time.

---

### Post by klein5366 on 2013-04-23
hi 
i use this multisystem usb it installs the os on the usbkey and uses grub2, if that is the only os on the key or the first one in the list it will boot right into it after a 30 second count down  that may be able to be changed i'v never tryed it , i use this to run back up software ubuntu 10.04, xubuntu 12.04, puppy, hearns bootcd, and clonezilla  .

the original page is in french so this is the page ran through google translator 
[http://translate.google.com/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fliveusb.info%2Fdotclear%2Findex.php%3Fpages%2Finstall&act](http://translate.google.com/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fliveusb.info%2Fdotclear%2Findex.php%3Fpages%2Finstall&act)

---

### Post by ibjsb4 on 2013-04-23
I believe you need a persistent usb install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistent+usb+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistent+usb+install&sa=Search&cof=FORID:9)

---

### Post by sanderj on 2013-04-23
> **Vulpus said:**
> When booting into Ubuntu on USB I get asked if I want to 'try Ubuntu' or Install. I don't want to install as I am using this on different PCs. Can I do something to remove this question every time.

Yeah, annoying indeed. So I'll be following this thread to see if it gives a solution.

---

### Post by dandroid13 on 2013-04-23
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Method 1 should be what you want.

---

### Post by C.S.Cameron on 2013-04-23
To bypass the try/install screen on a persistent install replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Boot time will be reduced by about a third.

---

### Post by Vulpus on 2013-04-23
> **C.S.Cameron said:**
> To bypass the try/install screen on a persistent install replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Boot time will be reduced by about a third.

Superb! Problem solved, thank you very much! :D

---

