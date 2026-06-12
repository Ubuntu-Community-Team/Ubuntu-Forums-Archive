---
title: "Cannot boot back into Windows 10"
date: 2020-03-27
forum: Installation &amp; Upgrades
---

### Post by sullivar on 2020-03-27
I installed Ubuntu over Windows 10 on a Dell XPS 13 laptop. Ubuntu works fine but lost the ability to boot back into Windows. I ran Ubuntu boot repair and it could still not boot into Windows. The boot repair generated a text report:

  	 	 	 	   [http://paste.ubuntu.com/p/Fr872MwYbz/](http://paste.ubuntu.com/p/Fr872MwYbz/)
  
If anyone can interpret that for me I would be most grateful.

Roger

---

### Post by ubfan1 on 2020-03-27
You may be able to get into Windows from the EFI menu, which is some function key like f12 at power-up to allow you to select boot device/OS.  That bypasses grub completely.  grub's os-prober did not find Windows, so until that is fixed, Windows will not appear in the grub menu.  Some things to check: 1)the Windows power management options (really buried) to turn fast boot off., 2)Raid to be turned off and ahci drivers added 3)Secure boot appears to be off, which is OK, but should not be necessary.,...

---

