---
title: "Can't Install Geforce 7600GS Driver!"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by pkw on 2007-09-01
Can anyone help please? I am trying to install the Geforce 7600 GS driver but I keep getting this message:

The NVIDIA SETUP program could not locate any drivers that are compatible with your current hardware. Setup will now exit.

At present I have an integrated 2000 series card which came with my comp. I am on Windows XP. Where am I going wrong? I have tried disabling current card and installing but with no success. What else can I do?

Thanks

pkw

---

### Post by deaf_girl on 2007-09-01
Have you looked at this

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Pumalite on 2007-09-01
You can also at the Terminal do this:
sudo apt-get install nvidia-glx-new

---

### Post by WiFi Ed on 2007-09-01
> **pkw said:**
>  I am on Windows XP. Where am I going wrong?

I will avoid the cheap shot:)  You could try going to nvidia's website and download the latest Windows XP driver for your video card. Double-click the downloaded file and it should install without too much drama.

Edit: Upon re-reading your post I must ask: Do you have a 7600GS video card installed in your pc? Your post is not clear...

---

### Post by pkw on 2007-09-02
Thanks 

Done that from site and Graphics Card is a integrated NVIDIA 2000 series.

---

### Post by WiFi Ed on 2007-09-03
Just to be sure (I'm a little slow sometimes):

You installed a 7600GS video card.

You re-booted and went into the BIOS and disabled the onboard video, or made sure it was set to auto-detect and saved any changes before exiting the BIOS setup.

You try to install the downloaded 7600 driver but get the "The NVIDIA SETUP program could not locate any drivers that are compatible with your current hardware. Setup will now exit." message.

When you continued the re-boot, did XP say "New hardware detected"? Or, if you look in Device Manager, under Display Adapter does it say something about an NVIDIA 7600GS or does it still show the integrated 2000 video? If it doesn't show the 7600 card, try right-clicking on the integrated 2000 device and choose "Uninstall" and re-boot.

I don't have any other suggestions for the moment...

---

### Post by pkw on 2007-09-08
Thanks again for your help Wif iEd.

No it doesn't show the card, I think i shall uninstall the 2000 series first and try again. Won't be for a while tho so don't hold your breath!

pkw

---

