---
title: "Acer Logo appears twice before Ubuntu finally opens"
date: 2020-02-04
forum: Installation &amp; Upgrades
---

### Post by virtjames123 on 2020-02-04
I recently installed updates on my newly installed ubuntu 18.04 LTS. I rebooted my PC afterwards and it won't boot. Only shows a message: Failed to open \efi\boot\mmx64.efi -Not found Failed to load image \efi\boot\mmx64.efi - Not found Failed to start MokManager: Not found Something has gone seriously wrong: Import_mok_state() failed :Not found 

Then I tried altering boot options to add yet another ubuntu efi boot option and moved it up the list and it boots. The problem now is that it tries to boot then goes back to acer logo twice before it finally opens. It now takes quite a bit of time to boot. Any ideas?

---

### Post by dragonfly41 on 2020-02-04
What does **efibootmgr -v**
return?

---

### Post by virtjames123 on 2020-02-04
Here it is

---

### Post by CelticWarrior on 2020-02-04
Disable Secure Boot.

---

### Post by virtjames123 on 2020-02-04
I have Windows 10 installed on the same laptop and it doesn't have the same problem.

---

### Post by virtjames123 on 2020-02-04
Already disabled it.

---

### Post by dragonfly41 on 2020-02-05
Based on my own experiments recently I would take a leap of faith and install rEFInd alongside the usual Grub. rEFInd just provides added options in the menu but you can use laptop "one time boot option" to launch rEFInd from the list of boot options. You can see the installed files in /boot/efi/EFI/refind/ and other boot installations are untouched.

[https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub/760971#760971](https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub/760971#760971)

Installing rEFInd when Ubuntu is launched .. could be via LiveUSB ..

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

---

