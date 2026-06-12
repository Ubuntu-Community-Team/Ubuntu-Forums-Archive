---
title: "Installing windows over Linux"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by speckynuisance on 2010-03-03
My windows vista stopped booting so I had re-install vista. Now that I have done that Vista automatically boots every time I turn on my computer. I can still see that the Linux partition is there but I do not know how to boot it.

Any help would be much appreciated, thanks

---

### Post by sam.reader on 2010-03-03
I do not exactly remember the path but I suggest you go follow the below path
Start>>Run>>"msconfig">>Go to boot option
You should be able to get the option here
I will check it later when my brother brings home his windows laptop

---

### Post by tommcd on 2010-03-03
You need to provide some more detail here.
Did you already have Ubuntu installed to a dedicated partition before you reinstalled Vista? Or did you install Ubuntu inside Windows using Wubi?
I assume you had Ubuntu installed to it's own partition, since a reinstall of Vista would overwrite a wubi install I would think.
> Installing windows over Linux
The title of your thread implies that you installed Vista over Ubuntu and Ubuntu is gone. 
If you still have Ubuntu on it's own partition then you can reinstall the grub boot loader to the MBR and get your Ubuntu back.
Which version of Ubuntu did you install? This is important, because Ubuntu 9.10 uses grub2 and prior versions of Ubuntu use grub-legacy. The procedures for reinstalling them are different.

And welcome to the Ubuntu forums!

---

