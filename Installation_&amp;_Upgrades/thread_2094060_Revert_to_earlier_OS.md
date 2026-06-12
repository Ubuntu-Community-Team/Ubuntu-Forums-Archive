---
title: "Revert to earlier OS"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by Claypool on 2012-12-12
Hey, I screwed up and updated Ubuntu 12.04 to 12.10. Didn't know that it would be more taxing on the graphics end. I am running on and old XP machine dedicated to Ubuntu now. How can I go back either to 12.04 or Xbuntu or even a lighter resource version of Ubuntu?  I made a few bootable ISO disks but none of them worked when I tried to reboot using the optical drive as number 1 boot sequence. Any help would be appreciated. Thank you.

---

### Post by Androzani1 on 2012-12-12
Burn a live CD of Ubuntu 12.04 or X or Lubuntu. Back up everything and install. :)

If it fails, do you have Secure Boot/UEFI?

---

### Post by Claypool on 2012-12-12
What is Secure Boot/UEFI? I thought I made a live CD of 12.04 bootable ISO.

---

### Post by Androzani1 on 2012-12-12
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Basically, MS use it to stop you from using Linux. Since Linux installed originally, I imagine that is not the problem. 

Is the CD drive damaged?

---

### Post by Claypool on 2012-12-12
No signs of any damage. I tried it on Ubuntu, Xubuntu. Perhaps I did not make the bootable disk correctly. I am using CD burner XP. Ckeded off make disk bootable and then burned the file to the disk.

---

### Post by arpanaut on 2012-12-12
You do not use make disk bootable, you need to burn iso as image.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by lisati on 2012-12-12
> **Androzani1 said:**
> [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Basically, MS use it to stop you from using Linux. Since Linux installed originally, I imagine that is not the problem. 

Is the CD drive damaged?

If it's an older machine that came with XP, then it's likely to have a more traditional BIOS than the newer UEFI. I wouldn't worry about it too much.

---

### Post by Claypool on 2012-12-12
I reburned as an ISO image, tried to reboot and got the upgraded Ubuntu. I don't get it.

---

### Post by Claypool on 2012-12-12
Is there a way to delete/reformat/erase the drive now?

---

### Post by Mark Phelps on 2012-12-12
> **Claypool said:**
> I reburned as an ISO image, tried to reboot and got the upgraded Ubuntu. I don't get it.

That means you're not booting from the optical disk -- as that would show the version you burned.

Need to check your default boot order in the BIOS.

Also, you should see if your PC will allow you to press F12 while booting and select the optical drive.

---

### Post by Claypool on 2012-12-12
I had changed to boot order to make the optical drive first so I don't understand.

---

### Post by Claypool on 2012-12-12
OK, got it working using the F12. Installing 12.04 once again. Thanks for your help.

---

