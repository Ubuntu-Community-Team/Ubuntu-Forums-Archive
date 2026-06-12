---
title: "How to uninstall?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by brown049 on 2008-04-26
I was wondering if anyone could advise me how to uninstall Unbuntu 8.04rc from my pc.  It was installed along side Vista which the pc came with.  Unfortunately after trying to get my wireless card working with ubuntu i have failed.  I wish to remove it so that my pc boots straight into windows rather than forgetting to hit the right keys and going into ubuntu which I no longer wish to use.

Any advice would be most appreciated.

Kind Regards

Mike

---

### Post by tamoneya on 2008-04-26
first you should over write the linux partition and resize the vista partition to take up the unused space.  This can all be done through the linux liveCD.  ```
sudo gparted
```Remove the ext3 partition and make the ntfs partition take up all the unused space.  Then put the vista install disk in and tell it to repair your windows installation.  This will replace GRUB with the linux bootloader and make it so that you boot directly into windows.

---

### Post by volkswagner on 2008-04-26
> **brown049 said:**
> I was wondering if anyone could advise me how to uninstall Unbuntu 8.04rc from my pc.  It was installed along side Vista which the pc came with.  Unfortunately after trying to get my wireless card working with ubuntu i have failed.  I wish to remove it so that my pc boots straight into windows rather than forgetting to hit the right keys and going into ubuntu which I no longer wish to use.

Any advice would be most appreciated.

Kind Regards

Mike

Seems drastic, no chance in getting wifi working?  If you are just wanting to have vista be the default os, you can edit grub.  Have any other versions/distros run your wireless?

---

### Post by ad_267 on 2008-04-26
Sorry it didn't work out for you. If you want to keep ubuntu installed but just boot into windows by default you can edit the file /boot/grub/menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Then you can change this line:
```
default         0
```
To whatever number windows is in this file.

If you want to completely remove ubuntu then follow what tamoneya said.

---

### Post by tamoneya on 2008-04-26
you should note that default has a 0 based index.  So the first item is 0 and the second item is 1.

---

