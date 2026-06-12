---
title: "No windows 8 option in the Grub menu, automaticalling loading the ubuntu 13.04"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by aayus on 2013-07-05
I just know installed the ubuntu 13.04 alongside the windows 8. Everytime i turn on my lappy, its shows the grub menu but do not shows the windows 8 load option init.
I did everything as asked in various threads.
Disabled the fast option.
Disabled the sesure boot and changing the boot option to "COS and UEFI".
Creation the partion in the disk for the ubuntu.
Then in that partion while installing the ubuntu alongwith windows 8, created these partions "/, swap and reserved bios area" through the option "Something else" option.
I was successfully able to install the 13.04. But after installing it i am not getting the option to load my windows 8 again.


Please anyone help hoe to get rid of this issue.

---

### Post by MikeCyber on 2013-07-05
sudo update-grub

in a terminal should detect Windows 8. Is it on another hd? Maybe change bios boot sequence.

reserved bios area? I only use swap (same as my installed RAM) and /. Make sure to not delete any Windows 8 created stuff.
Else reinstall win8 and boot with the Ubuntu live cd to do the above command or grub-repair.

---

