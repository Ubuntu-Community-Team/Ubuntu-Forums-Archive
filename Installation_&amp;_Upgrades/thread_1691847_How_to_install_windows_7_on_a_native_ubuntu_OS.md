---
title: "How to install windows 7 on a native ubuntu OS?"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by devilsoulll on 2011-02-20
Hi
i recently bought an msi notebook that comes with windows 7 starter. on the second day i completely wiped out the HDD and installed ubuntu netbook. so as u can see now, i only have ubuntu on my notebook and i want to install back windows 7 along side with ubuntu.and if it can't be along side, then how to delete ubuntu and install windows 7 only through usb boot?
i did make a bootable usb with windows 7, but everytime i want to boot from usb at bios and select my usb, it selects and stays on a black screen with nothing is happening!
any help would be greatly appreciated

Dev

---

### Post by mikewhatever on 2011-02-20
First, you can't 'install windows 7 on a native ubuntu OS'.
Now, that terminology is out of the way, you have to make some unallocated space for Windows first, so boot from the Ubuntu live usb and shrink/delete the Ubuntu partition using Gparted under System->Administration.
After that, do whatever you have to do to boot the W7 installer.

PS: Doesn't MSI provide some easy way of reinstalling W7?:biggrin:

---

### Post by devilsoulll on 2011-02-21
> **mikewhatever said:**
> First, you can't 'install windows 7 on a native ubuntu OS'.
Now, that terminology is out of the way, you have to make some unallocated space for Windows first, so boot from the Ubuntu live usb and shrink/delete the Ubuntu partition using Gparted under System->Administration.
After that, do whatever you have to do to boot the W7 installer.
 
PS: Doesn't MSI provide some easy way of reinstalling W7?:biggrin:
 
it does provide that but only when u have something for windows in ur hard drive. or at least the recovery partition<<< cuz i formatted it :biggrin:
 
ok thnx for the info. i'll try that and see what will happen.
but b4 trying, by u saying make some unallocated space that means just delete the partition and do not format anything in FAT32 or any other system right? 
will that solve why my usb installer won't start when i boot through it?

---

### Post by mikewhatever on 2011-02-21
I think it doesn't matter if you format the space as fat32/ntfs or leave it blank, W7 should be able to deal with either. What Windows can't deal with is Linux file systems, which is what you have.
I don't know why whatever you put on the usb doesn't boot. Are they recovery files from MSI? If not, what and where from?

---

### Post by deconstrained on 2011-02-21
You could install VMWare in Ubuntu and run Windows inside of a virtual machine...

---

### Post by devilsoulll on 2011-02-21
> **mikewhatever said:**
> I think it doesn't matter if you format the space as fat32/ntfs or leave it blank, W7 should be able to deal with either. What Windows can't deal with is Linux file systems, which is what you have.
I don't know why whatever you put on the usb doesn't boot. Are they recovery files from MSI? If not, what and where from?
 
I have "windows 7" bootable on my USB. and i want to format the whole HDD and install a fresh copy of windows 7 through booting from that USB so that i can then install ubuntu along side with windows. but it freezes at a black screen with a blinking courser everytime i choose to boot from the USB.
 
im sending you from work pc right now. i'll do what you suggested as soon as i get home and reply what happened
 
thank you :)

---

### Post by mikewhatever on 2011-02-21
Perhaps that Windows7 on usb is not as bootable as you think.;)

---

### Post by teddy92 on 2011-02-21
If you want to make an usb drive to install windows 7 use windows 7 usb/dvd download tool! tryed it and it worked like a charm!
you need a windows 7 iso file!

---

### Post by devilsoulll on 2011-02-21
> **teddy92 said:**
> If you want to make an usb drive to install windows 7 use windows 7 usb/dvd download tool! tryed it and it worked like a charm!
you need a windows 7 iso file!
 
yes i have the win7 iso.
now im having a new prob. i used ubuntu live usb to delete all the partitions in my HD
but i get an error when i try to do so. it won't format my hd to any fat or ntfs system
just stay on unallocated space?
any ideas?

---

### Post by rvchari on 2011-02-21
> **devilsoulll said:**
> Hi
i recently bought an msi notebook that comes with windows 7 starter. on the second day i completely wiped out the HDD and installed ubuntu netbook. so as u can see now, i only have ubuntu on my notebook and i want to install back windows 7 along side with ubuntu.and if it can't be along side, then how to delete ubuntu and install windows 7 only through usb boot?
i did make a bootable usb with windows 7, but everytime i want to boot from usb at bios and select my usb, it selects and stays on a black screen with nothing is happening!
any help would be greatly appreciated

Dev

by the way you have posted, i think you wish to use win7 as well as ubuntu. now that you have wiped out win7 and installed ubuntu, i would like to suggest you to install virtualbox (you download from the virtualbox.org site and not the native virtualbox OSE that you fing in the ubuntu software center)

you can install win7 as a virtual machine and keep ubuntu safe.

---

### Post by dhirajv12 on 2011-06-20
But with virtualbox, can I access HDMI port??
I can see only CD and USB interfaces

---

