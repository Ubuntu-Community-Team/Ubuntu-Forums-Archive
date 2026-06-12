---
title: "Install  Windows 7 after Ubuntu"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by emmagood on 2012-04-28
Hi,

  I have Windows XP and Ubuntu installeed in my system. I will like to install Windows 7. Can anyone tell me how to do so?

Thanks,
Emma Good

---

### Post by darkod on 2012-04-28
You want to install it over XP or you want to have all three OSs?

---

### Post by fantab on 2012-04-28
Also tell us more about your hard drives... how many do you have?

---

### Post by Rubi1200 on 2012-04-28
Posting the full specifications for the computer also helps, especially RAM and graphics card.

Thanks.

---

### Post by emmagood on 2012-04-30
Hi,

  Thanks for your responses. I want to keep windows XP and install Win7. I have 2 HDDs. One SATA 500 GB with Ubuntu and WinXP and another ATA 80 GB in which I want to install Win7. I have 2 GB RAM and on board graphics processor (intel board).

Pls. advice.

Emma.

---

### Post by fantab on 2012-04-30
> **emmagood said:**
> Hi,

  Thanks for your responses. I want to keep windows XP and install Win7. I have 2 HDDs. One SATA 500 GB with Ubuntu and WinXP and another ATA 80 GB in which I want to install Win7. I have 2 GB RAM and on board graphics processor (intel board).

That should be easy. Just install Win 7 to 80 GB HDD, during installation you have to make sure that you are installing Win7 to the said HDD. You must first Partition you 80gb. After installation you must log into Ubuntu and update Grub.

Or 

Before proceeding to install Win7 you should unplug SATA 500 GB and Install Win7 on 80GB... after installation plugin SATA 500. Then log into Ubuntu and update grub.

The second method is safer.

---

### Post by emmagood on 2012-05-01
how to update ubuntu grub ....


Thanks,
Emma.

---

### Post by darkod on 2012-05-01
Boot ubuntu and in terminal do:
sudo update-grub

---

### Post by emmagood on 2012-05-01
Just to confirm... will it work for ubuntu installation through wubi...?


Thanks,
Emma.

---

### Post by darkod on 2012-05-01
It will, but it doesn't make any sense for wubi. When we are talking about ubuntu, we are usually talking about the standard dual boot.

When you have wubi, you still have your windows bootloader on the MBR and that is your primary bootloader. You can select windows there. Why would you boot wubi just to select windows again.

PS. In fact, is your question related to whether update-grub will work for wubi, or the windows 7 installation? Do you have XP and wubi right now, or XP and ubuntu? There is a big difference.

---

### Post by emmagood on 2012-05-01
> **darkod said:**
> 
PS. In fact, is your question related to whether update-grub will work for wubi, or the windows 7 installation? Do you have XP and wubi right now, or XP and ubuntu? There is a big difference.

OK... when I start the computer, I get a black background with options windows XP and ubuntu on the screen. Apart from that, I loaded Ubuntu through Wubi.

Emma.

---

### Post by darkod on 2012-05-01
Yes, you have wubi installed into XP.

I have no idea how installing win7 would interfere with the setup. I think wubi will remain into XP. I don't use wubi so I am not sure.

---

### Post by emmagood on 2012-05-01
Ok.... does anyone have any ideas how to update wubi grub after installing win 7. I have Win XP installed with wubi in it. Also will that be required? 

Thanks,
Emma Good

---

