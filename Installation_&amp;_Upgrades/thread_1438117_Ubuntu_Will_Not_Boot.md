---
title: "Ubuntu Will Not Boot"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Garetty on 2010-03-24
I was installed Ubuntu just fine the other day. (8.10) I updated to 9.04 just fine. There I tried upgrading (Using the Update Manager) to 9.10. A lot of the files failed and I had to reboot. Before I did all the Updating (While I was still on 8.10), I installed StartUp-Manager, and did some stuff. Then when I did the update to 9.04, I restored everything in StartUp-Manager, not knowing that on the GRUB screen, it would try to boot 8.10. The update manager seemed to be failing a lot and told me it was aborting, and I had to reboot. So it did some other stuff and then I rebooted. But when I got to the GRUB screen, It did not have the options for 9.04, only 8.10. I tried the first option and it seemed to be loading fine, but not with the correct Boot Loading screen. (Which I think is because I did the restore on StartUp-Manager.) It was the one for 8.10. The bar looked to be loading normally, but stopped a little more than half way through. Then this screen popped up:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151329&stc=1&d=1269470884[/IMG]

I tried the rest of the options, but they didn't work either. (Except for Windows XP.) I do still have the GRUB screen, so I think there is a way to use the command line or edit the Boot Options to boot into Ubuntu. Is that possible?

---

### Post by cogier on 2010-03-24
All sounds a bit messy to me. I suggest you do a fresh install. If you have no backup use a live disk to rescue your home directory then start again.

---

### Post by Garetty on 2010-03-24
> **cogier said:**
> All sounds a bit messy to me. I suggest you do a fresh install. If you have no backup use a live disk to rescue your home directory then start again.

I'm probably going to do that... I don't have many files I needed on there anyways. Is there and way I can Remove Ubuntu so that I don't take up so much room on my hard drive when I do a fresh install?

---

### Post by cogier on 2010-03-24
If you do a fresh install you can guide the installer to write over the old version of Ubuntu

---

