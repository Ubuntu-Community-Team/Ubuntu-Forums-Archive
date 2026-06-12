---
title: "No grub menu after installation"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Druidika on 2010-05-09
I had Windows 7 x64 installed, and then installed Ubuntu 10 from the LiveCD. I can now boot into Ubuntu just fine, but I never get the Grub menu that allows me to choose to boot into Windows. I already tried 'sudo update-grub2', which gave no errors but didn't work either.

---

### Post by Catharsis on 2010-05-09
Hold down Shift while you boot to get the grub menu:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202](http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202)

---

### Post by Druidika on 2010-05-09
That doesn't work either unfortunately, I tried both left and right Shift keys.

---

### Post by darkod on 2010-05-09
Download the Boot Info Script from the link in my signature. Move it on desktop for example. Run it with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with info about your boot process. Copy the content here and wrap it in [CODE] tags for easier reading. You can do that by selecting the text you want and hitting the # in the toolbar above when creating your reply.

Those results give excellent info what is going on.

---

