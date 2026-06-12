---
title: "lilo.confg? grub?"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by thot135 on 2010-09-15
Hello. I wanna add a new entry to the set of bootable kernels but I can't find* lilo.conf* or *grub.conf*. What do I have to do?

Thank you for listening. I'll wait for your answer.

---

### Post by oldfred on 2010-09-15
We need to know more about your configuration and what you are trying to do. This will tell us about your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by psusi on 2010-09-15
Run sudo update-grub.

---

### Post by thot135 on 2010-09-15
.

---

### Post by thot135 on 2010-09-15
I built bzImage.mykernel and wanted to add it to the set of bootable kernels by editing lilo.conf, such as:
----------
image=/boot/bzImage.mykernel
label=mykernel
root=/dev/hda5
read-only
----------
but I couldn't find lilo.conf.
Now I know my ubuntu uses GRUB2 but this is totally different.
What do I have to do?

---

### Post by Rubi1200 on 2010-09-15
> **thot135 said:**
> Hello. I wanna add a new entry to the set of bootable kernels but I can't find* lilo.conf* or *grub.conf*. What do I have to do?

Thank you for listening. I'll wait for your answer.
Do as oldfred suggests and post the results of the bootscript.

It would also be helpful if you tell us what operating systems you have installed, how much RAM, graphics card etc.

The more information we have, the better advice we can offer.

Thanks.

---

### Post by psusi on 2010-09-15
> **thot135 said:**
> I built bzImage.mykernel and wanted to add it to the set of bootable kernels by editing lilo.conf, such as:
----------
image=/boot/bzImage.mykernel
label=mykernel
root=/dev/hda5
read-only
----------
but I couldn't find lilo.conf.
Now I know my ubuntu uses GRUB2 but this is totally different.
What do I have to do?

Run sudo update-grub

---

