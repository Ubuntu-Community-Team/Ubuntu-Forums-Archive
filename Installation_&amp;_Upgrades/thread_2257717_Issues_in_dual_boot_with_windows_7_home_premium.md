---
title: "Issues in dual boot with windows 7 home premium"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by eldude2 on 2014-12-22
Hi everybody!

So I'm stuck with this:

After creating a new partition via Gparted Live I installed windows 7 (in the partition with ntfs file system) that has runned smothly.
The issue comes after this, I am now unable to even run ubuntu 14.04 from the cd, it just not boots (black screen) and automaticaly boots windows 7 after a while. My idea to solve the problem and configure the dual boot is this:

1 - unmount the two created partition and merge them into one;
2 - install ubuntu and grub;
3 - recreate the second partition (where windows will be installed);
4 - install windows and cross my fingers.

Any sugestions of what could be th reason for the issue mentioned above and how can I solve it without the PItA listed above??

---

### Post by yancek on 2014-12-22
Have you changed the boot priority back to boot from the CD/DVD drive?

---

### Post by oldfred on 2014-12-22
You can install Windows 2nd, but it always installs its boot loader to the MBR (if BIOS) and you have to use the Ubuntu live installer as a repair tool to reinstall grub to MBR.
Usually best to install Windows first if totally reinstalling, but not required.

You may have to do a full cold reboot to get into BIOS and set CD/DVD as first or use one time boot key to boot Ubuntu on DVD. 
Slight chance that DVD is now damaged and does not boot. I have always preferred to use flash drives as in the past I often burned "coasters" or defective CDs. With flash drive I can reuse it many times.

---

### Post by eldude2 on 2014-12-22
OK, it makes sense. I'll try applying those suggestions and give some feedback.
Thanks for the help fellows!

---

### Post by eldude2 on 2014-12-22
everything has, aparently, runned somoothly. grub has been instaled (from software center) as for the ubuntu OS but it keeps booting to windows.
In need of more advice.

---

### Post by eldude2 on 2014-12-22
could it be something wrong with the grub config?
the dual boot option doesn't even appears.

---

### Post by oldfred on 2014-12-22
Need to see details of what is where:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

