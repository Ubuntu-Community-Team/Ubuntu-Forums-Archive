---
title: "Error 11: unrecognized device string"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by beep1314 on 2007-07-25
I have xubuntu 7.04 with a clean install on an old Toshiba 2595cdt laptop.  The acpi=force message appears at startup and also the computer won't shut down all the way (it still has the background image but no hard drive activity).

I read here that I needed to add acpi=force to /boot/grub/menu.lst in the kernel line to fix these problems.  The laptop shut down just fine after doing that, but when I tried to reboot I get 

Error 11: unrecognized device string
Press any key to continue

Cannot boot past this.  Must have made a typo.... is there any way to fix this problem without having to reinstall Xubuntu?

Thanks

---

### Post by confused57 on 2007-07-25
> **beep1314 said:**
> I have xubuntu 7.04 with a clean install on an old Toshiba 2595cdt laptop.  The acpi=force message appears at startup and also the computer won't shut down all the way (it still has the background image but no hard drive activity).

I read here that I needed to add acpi=force to /boot/grub/menu.lst in the kernel line to fix these problems.  The laptop shut down just fine after doing that, but when I tried to reboot I get 

Error 11: unrecognized device string
Press any key to continue

Cannot boot past this.  Must have made a typo.... is there any way to fix this problem without having to reinstall Xubuntu?

Thanks

You could try highlighting your Xubuntu entry in your grub boot menu, press "e" to edit, then highlight your kernel line, press "e" again, remove the acpi=force, press "enter", then press "b" to boot.

You also can mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
the only difference using the Xubuntu live cd is that you would need to use nano, instead of gedit to access your /boot/grub/menu.lst.

---

### Post by beep1314 on 2007-07-26
I tried those steps but the same error showed up again.  When I checked the kernel line acpi=force had reappeared.  I don't seem able to save changes at that point.  
As for the Live CD, I just have 64Mbs of ram.  The Live CD page says that is to little.....  Can the same thing work with the alternate CD, if so, how?

Thanks

---

### Post by confused57 on 2007-07-26
> **beep1314 said:**
> I tried those steps but the same error showed up again.  When I checked the kernel line acpi=force had reappeared.  I don't seem able to save changes at that point.  
As for the Live CD, I just have 64Mbs of ram.  The Live CD page says that is to little.....  Can the same thing work with the alternate CD, if so, how?

Thanks
No, the method I described is temporary...if it allows you to boot into Xubuntu, you can make it permanent:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```

Ctrl+x, y, enter...this will save your changes

You won't be able to use the Ubuntu live cd with 64 Mb ram...you might be able to use the Damn Small Linux live cd.

Added:You can try this for your shutdown problem, open a terminal:
```
sudo nano /etc/modules
```
add this line to the end of the file:
```
apm power_off=1
```

---

### Post by beep1314 on 2007-07-26
The shutdown command left the moniter on to a dos screen but did shut down the hard drive.  Is there more that I can do?

---

