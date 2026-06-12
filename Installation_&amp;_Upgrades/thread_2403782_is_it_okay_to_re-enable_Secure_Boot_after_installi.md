---
title: "is it okay to re-enable Secure Boot after installing Lubuntu?"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by ardouronerous on 2018-10-16
When installing Lubuntu on UEFI systems, do I really need to disable Secure Boot? And if I have to disable Secure Boot to install Lubuntu on UEFI systems, is it okay to re-enable it after installation?

Reason why I'm asking this is due to these threads I'm reading, "[I was hacked]("https://ubuntuforums.org/showthread.php?t=2403247")" and "[measures against rootkits]("https://ubuntuforums.org/showthread.php?t=2403688")" by user MikeCyber, apparently he was infected by a BIOS rootkit.

Can Secure Boot protect against BIOS rootkits?

Thanks.

---

### Post by yancek on 2018-10-16
You might take a look at the link below which gives a pretty detailed explanation of Secure Boot.

[https://www.howtogeek.com/116569/htg-explains-how-windows-8s-secure-boot-feature-works-what-it-means-for-linux/](https://www.howtogeek.com/116569/htg-explains-how-windows-8s-secure-boot-feature-works-what-it-means-for-linux/)

If you have and are using the shimx64.efi file, you should be able to leave Secure Boot on.  See the link below for more details.

[https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64](https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64)

The user in the first link you posted doesn't really give enough information to validate his claim and also makes reference to a BCD folder in the System Reserved/Boot directory which is a windows folder and partition.

---

### Post by Qew on 2018-10-16
This laptop I'm using is dual booting with Windows 10 and has always had Secure Boot enabled. I had no problems installing Ubuntu 16.04 a couple of years ago with it enabled, nor any issues when it upgraded to 18.04. Try installing with Secure Boot enabled. If you have issues doing so, then try disabling Secure Boot.

BTW, while Secure Boot adds an additional hurdle against rootkits and the like, it's not infallible. The best defence to such things is user diligence.

---

