---
title: "Resize operation aborted"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Mehul Agrawal on 2011-01-13
When installing ubuntu.After i choose a drive where i want to install ubuntu.
and choose its size.
and start to install error comes..
"An error occured while writing the changes to the storae device.
 The resize operation has been abored"
 
and running chkdsk dosent help and the drive is already defragmentated.

---

### Post by Rubi1200 on 2011-01-13
Hi and welcome to the forums :)

Boot the computer with the LiveCD, choosing to try NOT install.

Go to Applications > Accessories > Terminal

Run the following commands and post the output back here (copy/paste for best results):

```
sudo parted -l

sudo fdisk -lu
```

Thanks.

---

### Post by Mehul Agrawal on 2011-01-13
Did not work.still same error.
 
> **Rubi1200 said:**
> Hi and welcome to the forums :)
 
Boot the computer with the LiveCD, choosing to try NOT install.
 
Go to Applications > Accessories > Terminal
 
Run the following commands and post the output back here (copy/paste for best results):
 
```
sudo parted -l
 
sudo fdisk -lu
```
 
Thanks.

---

### Post by Rubi1200 on 2011-01-13
How exactly are you trying to install?

Which version of Ubuntu?

Do you have other operating systems on the computer?

---

### Post by srs5694 on 2011-01-13
> **Mehul Agrawal said:**
> Did not work.still same error.

Rubi1200 asked you to post the output here. Those are diagnostic commands, not repair commands. The intent was to let us see some technical details of your configuration, which might help us better advise you. Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings, which will preserve the formatting, making it easier to interpret.

---

