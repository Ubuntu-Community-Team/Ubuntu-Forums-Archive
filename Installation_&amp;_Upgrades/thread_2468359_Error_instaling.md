---
title: "Error instaling"
date: 2021-10-26
forum: Installation &amp; Upgrades
---

### Post by ecco-1210 on 2021-10-26
Hi guys

I'm trying linux for first time but unfortunately I can't even install it, I have a PC with Nvidia graphics and have two problems, first black screen (already tryed to use nomodeset) and if screen is correct when checking disks it stops in 13% and says
"Cheking ./pool/restricted/n/nvidia-graphics-drivers-460/libnvidia-gl-460_460.91.03-Oubuntu0.20.04.1_amd64.deb"
I'm trying to install Ubuntu 20.04.3 LTS

---

### Post by T6&amp;sfpER35% on 2021-10-26
where exactly did you get the ISO from?

---

### Post by ecco-1210 on 2021-10-26
The Ubuntu official page [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

---

### Post by MAFoElffen on 2021-10-27
Check your md5sum of your download ISO file to make sure it is okay and not corrupted. You can do that from whatever OS your downloaded that from. If not corect, download, create your install media and try again.

---

### Post by grahammechanical on 2021-10-27
I am looking at this from a different direction. I may be wildly off track but here goes. 

Do you have secure boot turned on?

Try installing Ubuntu and not to tick the box to install third party software. Ticking that box will install, or in your case, try to install a proprietary video driver (Nvidia). Not ticking that box might get Ubuntu installed with an open source video driver (Nouveau)

If you get a working Ubuntu you can activate the Nvidia driver by opening Software & Updates>Additional Drivers tab. You need to be connected to the internet for this to work.

There is one more thing. By not ticking the box to install third party software you will be missing certain audio and video codecs that you might need. They are in the Ubuntu Restricted Extras package.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Regards

---

