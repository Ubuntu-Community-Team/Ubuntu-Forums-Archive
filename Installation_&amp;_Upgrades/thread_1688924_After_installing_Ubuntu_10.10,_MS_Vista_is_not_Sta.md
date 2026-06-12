---
title: "After installing Ubuntu 10.10, MS Vista is not Starting!"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by Aditya Purohit on 2011-02-16
Hello, I have just installed ubuntu with a USB key, I have Vista  installed in drive C: .


In grub i see 2  windows vista option, First  option brings me to a Sony Viao recovery partition and not to the real operative system Second Option brings me to a blank screen. 

I can access all my files on the disk from ubuntu, but I would like to  be able to restore the vista boot loader and use again windows when I  need it.

Is there a way to restore vista's boot loader? I don't have vista recovery cd because vista was pre-installed on Sony Viao laptop.

I need some help and I wanted to explain the best way I could the situation

Thanks & Regards

Aditya

---

### Post by Rubi1200 on 2011-02-16
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

