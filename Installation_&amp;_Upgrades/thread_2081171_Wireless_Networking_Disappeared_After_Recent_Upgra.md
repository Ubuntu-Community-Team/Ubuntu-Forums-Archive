---
title: "Wireless Networking Disappeared After Recent Upgrade to Kernel"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by rohart on 2012-11-06
A recent upgrade (this morning) to Kernel 3.5.0-18 has resulted in wireless networking not showing up in Available Networks. Had I not had wired networking available connecting to the internet would have been impossible.

Wireless networking is showing up in Edit Networks but not in Available Networks.

Anyone else found this?

---

### Post by Inoki on 2012-11-06
This is precisely the reason why I was worried giving Ubuntu a shot once more. I think I'll just skip any future updates.

---

### Post by dannyboy79 on 2012-11-06
sometimes the kernel can induce some regression for some modules, it happens. if you hit shift upon boot up, you should be presented with the grub menu, chose the last kernel that worked and boot into that.

then change grub so it boots to the kernel you know worked automatically until you can learn more about the kernel regression with that particular module.

what wifi card do you have?
```
lshw -class network
```

---

### Post by Inoki on 2012-11-06
> **dannyboy79 said:**
> sometimes the kernel can induce some regression for some modules, it happens. if you hit shift upon boot up, you should be presented with the grub menu, chose the last kernel that worked and boot into that.

then change grub so it boots to the kernel you know worked automatically until you can learn more about the kernel regression with that particular module.

what wifi card do you have?
```
lshw -class network
```

My question would be, can I simply skip these updates and use the kernel that works 100% for me for all time, or at least a new version of Ubuntu is introduced? I'm having the base, 3.5.0-17 and I'd like to keep it, since it works flawlessly.

---

### Post by dannyboy79 on 2012-11-06
you certainly can run the same kernel all the time, as I said, set which kernel boots and works for you within grub.

---

### Post by Inoki on 2012-11-06
> **dannyboy79 said:**
> you certainly can run the same kernel all the time, as I said, set which kernel boots and works for you within grub.

Thanks for the reply. Is there some way to ignore kernel updates completely? Or do I have to manually untick them each time an update comes.

---

### Post by dannyboy79 on 2012-11-06
give this a try [http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)

---

### Post by Inoki on 2012-11-06
> **dannyboy79 said:**
> give this a try [http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)

Thank you so much for this! This is something I've been looking for in Ubuntu for years! Thank you!

---

### Post by Notclive on 2012-11-10
Try installing linux-headers-generic then reinstall bcmwl-kernel-source.

---

