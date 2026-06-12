---
title: "Install ubuntu16 on new HD with 2 other drives + OSs already - boot problems?"
date: 2017-03-18
forum: Installation &amp; Upgrades
---

### Post by brumman on 2017-03-18
Hope this isn't a duplicate but I just want to clarify what I think I found so far in the posts. 
I have 2 internal HDs one Ubuntu12.04 and the other Win7. I rarely use windows but I have the option of booting into it from the Ubuntu Boot loader menu. I am testing Ubuntu 16.04 (Live persistent USB) and am now ready to install it to a new internal 2T HD.

I know that the updates/programs on the live USB will not get installed but I am not sure about grub. Where will it reside? As long as all drives are connected during installation will all the OSs be added to the boot menu on whichever drive is set first in the BIOS (not uefi)? 
 I thought it safer to remove the 2 existing HDs while installing but now realise that then they would no longer be recognized by grub. 
On the new install is there any point in a separate boot partition or should I just let the ubiquity installer go with  /, /home, data partition and finally swap. I only have 4G ram but have never yet seen the swap on Ubuntu12.04 used! But I suppose that swap should be on Ubuntu16 too, because I eventually will remove Ubuntu12 and use that HD for something else.

---

### Post by howefield on 2017-03-18
> **brumman said:**
> I know that the updates/programs on the live USB will not get installed but I am not sure about grub. Where will it reside? As long as all drives are connected during installation will all the OSs be added to the boot menu on whichever drive is set first in the BIOS (not uefi)? 

You'll get the option of which disk to install grub to during the install process, wherever you choose grub will pick up all the operating systems it can find and add them. So, installing to your current boot drive should be fine. 

>  I thought it safer to remove the 2 existing HDs while installing but now realise that then they would no longer be recognized by grub.

That's correct. You could always run update-grub after the install and once the other drives are connected if you wanted to, that would add the other OSes.  
 
> On the new install is there any point in a separate boot partition or should I just let the ubiquity installer go with  /, /home, data partition and finally swap. I only have 4G ram but have never yet seen the swap on Ubuntu12.04 used! But I suppose that swap should be on Ubuntu16 too, because I eventually will remove Ubuntu12 and use that HD for something else.

I only use /, /Data and /swap with user folders symlinked to folders on /Data (which happens to be a separate disk). Swap is probably best to have even if it is only for badly behaving applications.

---

### Post by sudodus on 2017-03-18
You can remove the other two drives during the installation, shutdown, connect the other drives, and make sure to boot from the new drive (via the BIOS/UEFI menus). Then you can run

```
sudo update-grub
```

and the operating systems on the other drives will get entries in the grub menu.

But it should work too, if you install with the other two drives connected. This is easier to control in BIOS mode, and somewhat more difficult in UEFI mode (where the target drive for the bootloader is selected automatically).

---

