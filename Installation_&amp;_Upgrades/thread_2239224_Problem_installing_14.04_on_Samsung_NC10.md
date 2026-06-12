---
title: "Problem installing 14.04 on Samsung NC10"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by Alasdair_Beal on 2014-08-12
I first installed Ubuntu 12 via WUBI, then upgraded successfully to 13.10. I tried upgrade to 14.04 a few months ago but it failed. My computer cannot boot from USB (I have checked), so I reinstalled 13.10 via WUBI, which worked fine. Yesterday I tried again to upgrade to 14.04. Half way through installation, message was 'cannot install 14.04 to stable configuration, so stopping installation and recovering to 13.10'. When that process completed I had 13.10 screen but when I tried reboot, message 'serious errors were found when checking the disk drive for /.'. If I press I for Ignore, message 'The disk drive for /tmp is not ready yet or not present'. 

Is it worth trying manual recovery? If so, what should I do after pressing 'M'? The alternative is to reinstall 13.10 from scratch via WUBI.

What do you recommend?

---

### Post by ajgreeny on 2014-08-12
Are you certain the netbook can not boot from a USB; it should be able to do so, but you will need to press a key to show the boot priority and set it there.
See [https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10)

Assuming it can, and will, boot from USB you can install 14.04, though I would suggest Lubuntu or maybe Xubuntu on that hardware, not Ubuntu with the unity interface.

---

### Post by Alasdair_Beal on 2014-08-12
Dear Friend,
Yes I am certain the netbook will not boot from USB - I checked in the manual etc. and it definitely does not.
What is my best option now to get 13.10 working again - reinstall by WUBI, or try manual recovery?

---

### Post by hakuna_matata on 2014-08-12
> **Alasdair_Beal said:**
> message 'serious errors were found when checking the disk drive for /.'.  If I press I for Ignore, message 'The disk drive for /tmp is not ready  yet or not present'.  
[URL="http://askubuntu.com/questions/454143/upgraded"]http://askubuntu.com/questions/454143/upgraded-to-14-04-reboot-fail
[/URL][http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1](http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1)
[http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696]("http://ubuntuforums.org/showthread.php?t=2217829&p=13001696")

.......

---

### Post by Alasdair_Beal on 2014-08-13
Dear hakuna,
Your recommendation worked and I booted into Ubuntu successfully. However when I opened Terminal to edit grub and followed your instructions, it opened the file as 'read only' and would not let me save the change. Do you know how I can fix this?
Thanks

---

### Post by hakuna_matata on 2014-08-13
If you try this post: [http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

insert** gksudo: **[http://ubuntuforums.org/showthread.php?t=2217829&p=13035996#post13035996](http://ubuntuforums.org/showthread.php?t=2217829&p=13035996#post13035996)

---

### Post by Alasdair_Beal on 2014-08-13
Dear hakuna,
Success! Thanks for your help.

---

