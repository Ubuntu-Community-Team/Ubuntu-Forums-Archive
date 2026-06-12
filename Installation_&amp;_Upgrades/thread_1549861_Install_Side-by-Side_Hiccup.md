---
title: "Install Side-by-Side Hiccup"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by JPS913 on 2010-08-10
Hey Everyone,

Just installed Ubuntu 10.04 on my home laptop after testing it (and loving it) on my work desktop just this morning. First time Ubuntu user and looking to be a long one, too.

Anyways, I used the "install side-by-side" on both machines, but my laptop, with Vista, has a weird side effect. At the boot screen, I chose Windows Vista and it booted the recovery tool (I forgot the exact name). I was worried at first, but when I chose the actual Windows Recovery option below it to attempt to fix it, it booted Vista. So it seems in the process of partitioning the HDD for Ubuntu I somehow switched what each partition boots. Is there a way to correct this?

Please let me know any information you'll need to help me out with this. I can provide screenshots if needed. Thanks a lot and I'd appreciate any help I can get.

---

### Post by ajgreeny on 2010-08-10
Is there only the one entry on your grub menu for windows, or are there two?  If there are two you can just choose the other one at grub and it will hopefully take you straight to Vista.  If there is only the one, I think something must have gone wrong when grub was installed.

Try running ```
sudo update-grub
``` in terminal and see if that solves the problem.  If not get the boot-info-script from  my signature, run it and report back here with the RESULTS.txt file it produces.

---

### Post by Mark Phelps on 2010-08-10
> **JPS913 said:**
> So it seems in the process of partitioning the HDD for Ubuntu I somehow switched what each partition boots. Is there a way to correct this?

You didn't switch anything. This is a side-effect of GRUB2 where the menu generator gets confused and lists the Vista/Win7 partitions in the wrong order.

My own experience with GRUB2 is that, unless something is a major problem, to just leave it alone.

The alternative, as far as I know, would be for you to have to hand-code a boot script for your Vista partitions, after disabling the one already there.

---

### Post by JPS913 on 2010-08-10
Thanks for the tips, you two. I'll try them when I get home and report back the results. 

Also, would you know how to restore the toolbar? I think it disappeared after I accidentally shutdown during some updates. 

Thanks!

---

### Post by JPS913 on 2010-08-11
Here are the results from the boot script you sent me. Also, I ran that grub update command you sent me and posted the results as well in. I notice that if you compare the two results, "sda2" looks like it's what boots Vista (winload.exe?) but the grub update results show that that partition is called the Windows Recovery Environment, which is what I originally was asking about. Thanks for the help and I hope to hear back soon.

---

