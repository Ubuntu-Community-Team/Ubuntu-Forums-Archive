---
title: "Feisty Fawn upgrade and Nvidia"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by o0Jerry0o on 2007-04-05
I had installed Feisty using update-manager. Feisty seems to change the classification of the nvidia cards for the video drivers...
I use Nvidia-glx for my geforce4 440 Go but, Feisty forces me to use nvidia-legacy which does not allow me to do much since I can't play any games with that.

---

### Post by xopher on 2007-04-05
> I use Nvidia-glx for my geforce4 440 Go but, Feisty forces me to use nvidia-legacy which does not allow me to do much since I can't play any games with that.

This is because the nvidia-glx in feisty is version 97.55 - which doesn't support your videocard anymore. You should remove nvidia-glx-legacy alltogether, and install 96.31, which will become a second legacy branch soon. They aren't available as a deb yet, so you have to install them using he official installer found on nvidia.com:

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)

---

### Post by o0Jerry0o on 2007-04-06
I'll try this right now and post back the results. ^^

---

### Post by o0Jerry0o on 2007-04-07
The Nvidia driver didn't work for me, i'm not sure you understood my problem...
See I have a Geforce4 440 Go video card (32mb), while I was on Ubuntu Edgy Eft I used Nvidia-Glx drivers which have Open Gl support (I ran Beryl + AIGLX Perfectly) but now on Ubuntu Feisty Fawn i am forced to use Legacy which limits my use of games and direct rendering completely! 
The Nvidia driver you advised did not work, what else can I do?

---

### Post by Hobbes on 2007-04-08
No he is right... i have a geforce go 440 64 mb and it is in the same category... until recently (on edgy and even on feisty until the recent upgrades) I could use nvidia-glx, but now it tells me to use legacy.  As he said above and is said elsewhere... there are new "legacy" drivers which support our cards...

I am trying the link now to see if I can get mine working.... otherwise you will just have to use legacy until ubuntu finds a way to include the new drivers.

---

### Post by Hobbes on 2007-04-08
well I got the driver posted above to install after a couple tries... you have to download the package called NVIDIA-Linux-x86-1.0-9631-pkg1.run then: hit ```
 ctl-alt-F1 
``` to exit your xserver, then login and type in ```
sudo killall gdm 
``` to kill your xserver, then ```
 sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run 
``` to install the driver.  That should work, with a few error messages perhaps... you can get back into your xserver without restarting by doing ```
 sudo /etc/init.d/gdm start
```

good luck :)

---

### Post by o0Jerry0o on 2007-04-09
Thanks, but I did try.. didn't work for me though.. I got it to install but said something about the kernel and would'nt load the xserver, the last known good driver for me was 8776 I might just try that. Thanks for your support though. ^^

---

### Post by jbtito03 on 2007-04-09
Hi guys...

I got the same message.. kernel source not found. Well.. i too a look aroud and the only kernel source for nvidia is for a higher version of the drivers. 

Any idea what to do and where to find the other source?

Thx

JB

---

### Post by Hobbes on 2007-04-09
Yea, I'm not sure how to get around that problem... I think I have linux-source-2.6.20 (the package) installed, but I'm not sure if that's the one necessary or not.

hopefully the driver will be packaged and put into the ubuntu repositories soon anyway...

---

### Post by jbtito03 on 2007-04-10
Well... some of you guys did it. I am just wondering how? What was the exact procedure?

Cheers

JB

---

### Post by amphet on 2007-04-10
Thanks for the heads-up, I have the same card and was hoping to upgrade to feisty when it was released which I won't be doing until theres a way around this.

---

### Post by amphet on 2007-04-12
has anyone been able to install the 8776 drivers in feisty?

---

### Post by Hobbes on 2007-04-12
I recently (day ago?) got an upgrade of package nvidia-glx which looked like it took me back to the new "legacy" driver, 9631.

That should mean that all is well and people with nvidia geforce3/4 (go) should be up to date and at full capacity (composite, etc.).

Thanks to the ubuntu devs for fixing this so quickly.

---

### Post by o0Jerry0o on 2007-04-13
Hmm i'll give that a try Hobbes, thanks for the heads up

---

### Post by o0Jerry0o on 2007-04-15
I was able to fix the problem using this handy guide!, [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)

---

### Post by amphet on 2007-04-16
> **o0Jerry0o said:**
> I was able to fix the problem using this handy guide!, [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)
thanks for the link, now I'm ready to upgrade.

---

