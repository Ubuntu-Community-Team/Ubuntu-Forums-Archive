---
title: "Wubi is not doing anything."
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Extol11 on 2012-04-26
So I had 10.04 installed on my laptop through wubi but I decided to uninstall it and install 12.04 from scratch. I made this decision after noticing that the upgrade on my virtual machine didn't go really well. Some new features were left out and it still moved a bit slow. Well, I inserted the disc into the laptop, it prompts to install with wubi, I select yes, then tell windows it's ok to let the program make changes to my computer and nothing happens afterwards. I want to know if there are some other people having the same problem since it worked perfectly the first time with 10.04. I haven't made any important changes to my hardware or software since then. Any help will be greatly appreciated.

---

### Post by techsupport on 2012-04-26
> **Extol11 said:**
> So I had 10.04 installed on my laptop through wubi but I decided to uninstall it and install 12.04 from scratch. I made this decision after noticing that the upgrade on my virtual machine didn't go really well. Some new features were left out and it still moved a bit slow. Well, I inserted the disc into the laptop, it prompts to install with wubi, I select yes, then tell windows it's ok to let the program make changes to my computer and nothing happens afterwards. I want to know if there are some other people having the same problem since it worked perfectly the first time with 10.04. I haven't made any important changes to my hardware or software since then. Any help will be greatly appreciated.

Instead of using Wubi, I suggest installing VMWare Player for free and then installing Ubuntu 12.04 virtually in VMWare instead.  That is better for the long term instead of using Wubi.

---

### Post by Extol11 on 2012-04-26
> **techsupport said:**
> Instead of using Wubi, I suggest installing VMWare Player for free and then installing Ubuntu 12.04 virtually in VMWare instead.  That is better for the long term instead of using Wubi.

I'm using virtual box for m 12.04 upgrade, but I just don't like using virtual machines in laptops. It's definitely not ideal, IMO. But thanks for the suggestion.

---

### Post by techsupport on 2012-04-26
> **Extol11 said:**
> I'm using virtual box for m 12.04 upgrade, but I just don't like using virtual machines in laptops. It's definitely not ideal, IMO. But thanks for the suggestion.

Does you laptop BIOS not support virtualized 64-bit processes or?

Then you would probably try installing a dual boot instead of using Wubi.

Wubi has always been a real pain.

---

### Post by Extol11 on 2012-04-26
> **techsupport said:**
> Does you laptop BIOS not support virtualized 64-bit processes or?

Then you would probably try installing a dual boot instead of using Wubi.

Wubi has always been a real pain.
I'll get back to you on the bios thing but at least I downloaded 10.04.4 and it did work with it. How do I make a dual boot? Just boot from the disk and select to install it along side? If I feel like uninstalling Ubuntu for an upgrade (which I prefer to downloading upgrades) can I invert the process easily? I'll check the bios thing and come back.

---

### Post by bcbc on 2012-04-26
See this: [http://askubuntu.com/questions/125015/can-i-install-12-04-by-using-wubi](http://askubuntu.com/questions/125015/can-i-install-12-04-by-using-wubi)

---

### Post by techsupport on 2012-04-26
> **Extol11 said:**
> I'll get back to you on the bios thing but at least I downloaded 10.04.4 and it did work with it. How do I make a dual boot? Just boot from the disk and select to install it along side? If I feel like uninstalling Ubuntu for an upgrade (which I prefer to downloading upgrades) can I invert the process easily? I'll check the bios thing and come back.

Yes, of course. That is what everyone does if they install Ubuntu side by side with Windows.  You would simply boot from the live USB Stick of Live Bootable Ubuntu 12.04 and use gparted to delete your old Ubuntu root and swap partitions.  And reuse the free space to place a new root and swap parition for a fresh install of Ubuntu side-by-side. It will reupdate grub and everything too. No worries. 

Wubi is for test drives of Ubuntu. Not meant for production system usage. That is why you are having such a hard time with it right now probably.

---

### Post by Extol11 on 2012-04-26
> **bcbc said:**
> See this: [http://askubuntu.com/questions/125015/can-i-install-12-04-by-using-wubi](http://askubuntu.com/questions/125015/can-i-install-12-04-by-using-wubi)

Thanks for that link.

---

### Post by techsupport on 2012-04-26
> **Extol11 said:**
> Thanks for that link.

No problem. I'll check back later in case you need further assistance and don't forget to mark this thread as solved when you are done here.

---

### Post by jadtech on 2012-04-27
wubi install is working fine I am running 12.04 no issues on dell m5030

---

