---
title: "Installation problem"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2010-11-16
I just upgraded my laptop from Ubuntu 9.10 to 10.04 from the update manager. The upgrade seemed to go flawless. I restarted the laptop after completion of the installation as recommended. After restart the ubuntu splash screen shows up and then the screen goes blank and nothing happens. Does anyone know how to check the problem and fix it. Thanks

---

### Post by mörgæs on 2010-11-17
Maybe you need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by sikander3786 on 2010-11-17
I hope you've got an Nvidia graphics card.

Press and hold down Shift key at your Bios screen until you see the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot.

If the boot was successful, go to System > Administration > Hardware Drivers and activate recommended drivers for your card. Reboot and the problem should disappear for Good.

---

### Post by bhishan on 2010-11-19
Thanks for the reply guys. I selected the second kernel in the boot menu and it worked. Then I again upgraded to 10.10 and it seems to be working fine except it is super slow.

---

### Post by mörgæs on 2010-11-20
Then a clean install of 10.10 is probably worth trying.

---

### Post by bhishan on 2010-11-22
> **mörgæs said:**
> Then a clean install of 10.10 is probably worth trying.

That was the main problem. Its an old laptop and gave errors whenever I tried to boot the live cd's of all ubuntu 9.10, 10.04 and 10.10. Finally 9.04 live cd worked and I installed it in the laptop. Then I upgraded it 3 times to get 10.04.

---

### Post by mörgæs on 2010-11-22
Have you tried the alternate CD?

---

### Post by bhishan on 2010-11-24
> **mörgæs said:**
> Have you tried the alternate CD?

That could be a good idea. Maybe will try it after 11.04 comes out.

---

### Post by bhishan on 2010-12-05
> **mörgæs said:**
> Have you tried the alternate CD?

I tried using the alternate CD. It wouldn't even boot from the CD.

---

