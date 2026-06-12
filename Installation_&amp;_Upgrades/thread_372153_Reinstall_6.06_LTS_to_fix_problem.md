---
title: "Reinstall 6.06 LTS to fix problem?"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by jimrothstein on 2007-02-27
I have been using 6.06 LTS with automatic updates on my Acer Aspire 5102 for about 6 months with few problems.

However, my usb devices (mouse, memory stick) stopped working after recent automatic upgrade to 2.6.15-28-386.
I am fairly certain I have this bug;   #54419
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419) and none of the suggestions work for me.

My question is NOT about this bug.  Rather, it seems to me that all I really need is to do go back to original Ubuntu CD (August 2006) and reinstall the earlier kernel without the bug.  I am newbie and not sure how to do this so I don't harm any of the data on my notebook.

That's one question, but please keep reading.

I did boot from this original CD (August 2006) just to see if it recognizes the usb devices. But no, it does not.  (My devices - mouse, memory stick -  all work on other machines. ) So my second question is a bit imprecise: I am lost about  to do to get Ubuntu (with usb support) working again on my notebook.  Can't seem to go forward and can't go backward.  

Just fyi, here's dmesg | tail - but again suggestions for bug 54419 don't fix. 
```
[17184943.180000] usb 1-1: new low speed USB device using ohci_hcd and address 7
[17184943.360000] usb 1-1: device descriptor read/64, error -110
[17184943.644000] usb 1-1: device descriptor read/64, error -110
[17184943.924000] usb 1-1: new low speed USB device using ohci_hcd and address 8
[17184944.104000] usb 1-1: device descriptor read/64, error -110
[17184944.388000] usb 1-1: device descriptor read/64, error -110
[17184944.668000] usb 1-1: new low speed USB device using ohci_hcd and address 9
[17184945.076000] usb 1-1: device not accepting address 9, error -110
[17184945.252000] usb 1-1: new low speed USB device using ohci_hcd and address 10
[17184945.660000] usb 1-1: device not accepting address 10, error -110
```

Thanks for reading.

jim

---

### Post by chewearn on 2007-02-27
Not sure if you are aware, but after every new kernel update, the old kernel is available; you can still revert back to the old kernel by selecting the corresponding grub entry during boot-up.

---

### Post by jimrothstein on 2007-02-27
Yes, my apologies,  I should have mentioned that I did try and boot with  the old kernels listed in GRUB.

Usb devices do NOT work (even though they did before).  This is why I was trying to reinstall Ubuntu from scratch, i.e. CD (but not lose existing data).

---

### Post by chewearn on 2007-02-27
I'm not sure how to help you on solving the USB problem, not an expert myself.

But, based on your description:
1. USB used to work with liveCD.
2. USB worked before kernel update.
3. USB stopped working after kernel update
4. USB stopped working from the liveCD, not just the updated kernel
5. USB stopped working if you revert back to old kernel

My suspicion is it might just be co-incidence that the USB breaks after you update the kernel.

On your question about preserving your data, I assume you have your data in your home folder; and you have not move your home folder to a separate partition.  Then, I suggest the safest way is to backup to somewhere else.  You will have to copy the data out of your installation partition anyway.

---

### Post by jimrothstein on 2007-02-27
Hi.

Yes, you have the sequence of events exactly right.

Also correct that /home is NOT on separate partition and so will backup data.

Will also bring notebook to shop - perhaps it is hardware problem.

Assuming my problem is usb hardware and I get it fixed, is it fair to assume that my old kernels (in GRUB, the ones that DID support usb) will begin to work again? (i.e. no need to reinstall from scratch using CD)

Thanks for your help.

jim

---

### Post by jimrothstein on 2007-02-28
Visited computer shop.  Apparently the Southbridge of my Acer Aspire 5102 is destroyed. Bought a PCMCIA card with 2 USB slots and now usb mouse works, all kernels.

Apologies for false alarm.  And bug; #54419?  I dunno.  Shouldn't there be an easier way to sort hardware from software/kernel issues?

Appreciate all the help.

---

### Post by chewearn on 2007-02-28
> **jimrothstein said:**
> Apologies for false alarm.  And bug; #54419?  I dunno.  Shouldn't there be an easier way to sort hardware from software/kernel issues?


Well, that's the million dollar question, ain't it?  I faced this question almost daily in my work.  ](*,)

---

