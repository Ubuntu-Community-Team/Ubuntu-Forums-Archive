---
title: "How to set two different operating system."
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by sumantri_84 on 2008-11-05
How should i set two different operating systems to be on top.
I am using ubuntu and windows xp pro. Currently my defaults OS is ubuntu. Now i want to set,my windows XP as my default OS rather the my ubuntu. How should i , make my Windows Xp pro on the top when i on my pc.

---

### Post by m_duck on 2008-11-05
If you have XP already appearing on the grub list and just want to make it the default OS, the easiest way is to install the package "startupmanager" either via synaptic or terminal:
```
sudo apt-get install startupmanager
```

It will then be in System -> Administration -> Start-up manager (you may need to restart x or restart your pc before it shows up). Open this then on the "Boot Options" tab you can select the default operating system from the drop-down box.

---

### Post by sumantri_84 on 2008-11-05
ok, thank you.

---

### Post by sumantri_84 on 2008-11-05
I am still facing problem with its. I am currently using ubuntu the terminal to change the OS. But when i paste, the below code: i still cannot make Windows XP pro as my default.

 ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below.

---

### Post by m_duck on 2008-11-05
OK, if you are editing /boot/gru/menu.lst:

If you open your original menu.lst file that contained Ubuntu and Windows to boot, it can largely be left alone other than changing the line near the top that probably says
```
default      0
```
Just change the "0" to the line number where the Windows XP option is in the menu (first line is zero and includes the line saying "Other operating systems" if applicable).

So in mine for example, I change this to
```
default      6
```
as in my grub menu on boot, I have,
```
Ubuntu 8.04.1, kernel 2.6.24-21-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other Operating Systems:
Windows XP Professional
```
So windows is on the 6th line (beginning at zero).

I hope that makes some sense! If not, please ask me to clarify.

---

### Post by haylun98 on 2008-11-05
It found it better to use savedefault function because when you receive a kernal update your xp will not be the 6th line any more unless you remember to edit it straight after kernal upgrade.

default = 0
to 
default = saved

This way your xp will be saved as default after an initial boot. Then every you power up the xp selection should be automatically highlighted and after the countdown it will boot.

if you want grub to boot the last os booted including ubuntu, you can add:

savedefault

under ubuntu selections as well. Its all explained within:

boot/grub/menu.lst

---

### Post by sumantri_84 on 2008-11-07
Thank you for the help.

Finally, i had make XP pro as my default.

solution:
Just change the default is the easiest way to make  my XP as the default start up.

---

