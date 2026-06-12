---
title: "Dual Boot Uninstall 9.10 Wubi"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by dwith on 2009-12-02
I used the latest version of Wubi to install 9.10 on an Dell Laptop (XP Pro) hard drive. Karmic works well on the laptop. The problem comes into play when uninstalling with Wubi. Ubuntu uninstalls from the hard drive correctly as if it were a stand alone program, but the master boot record menu still lists Ubuntu. I have manually deleted an extra wubildr file under the C drive as many have suggested. This did not remove Ubuntu from the boot menu. Installing a new master boot record does not change the problem either. Functionally, the laptop is fine. I will soon be giving it to someone else and would like the menu to be cleaned up. I have carefully gone through other posts on the topic, but have not found any advice that led to a solution. Any light would be appreciated. A registry issue? Thanks.

---

### Post by garvinrick4 on 2009-12-02
In Windows command line.  "bcdedit" without qoutes.

You will see a wubi in the windows grub. Edit it out


"bcdedit /delete {  # in the same brackets as these}"

Code does not include qoutes but keep the brackets.


This happens in Wubi sometimes when it is uninstalled by way of program Add and Remove programs in  Windows.  Wubi has to be uninstalled from its own uninstaller in its folder in 
Windows. If you uninstalled it that way do not take offense, it is just the only time I have seen Wubi stay attached to Windows DOS4Grub.

Be careful in "bcdedit' in Windows make sure you got the right one the one that says WUBI.

---

### Post by ottosykora on 2009-12-03
as you have XP, check what is in your file boot.ini
if entries to ubuntu there, you can delete them simply.

or comment them out for testing.

---

