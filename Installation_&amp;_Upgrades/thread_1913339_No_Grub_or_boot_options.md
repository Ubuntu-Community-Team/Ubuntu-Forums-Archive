---
title: "No Grub or boot options"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by celticzero on 2012-01-22
Hello, this is my first time posting here. A few years ago I installed Ubuntu(I think 9.10) just to play around and had zero issues installing/dual booting. I have just recently re partitioned my main windows boot drive and made some space available for Ubuntu. I installed everything and it seemed to go smoothly but when I attempt to boot, grub doesn't load and it boots straight to ubuntu. If I go into BIOS and set Windows Boot as my first priority, it will boot to windows, but if I set first priority to the actual HDD that Windows and Ubuntu are installed on it boots straight to Ubuntu. I am using Windows 7 64 bit and trying to dual boot Ubuntu 11.10. Thank you for any help.

---

### Post by nipunshakya on 2012-01-22
Hi. First off all, welcome to the forum
Seeing at your description, it seems like windows and linux are booting in harmony. Just the thing is u aren't getting the grub loader to show u the menu from where u wish to select between os.
so, first u boot to ubuntu. Then goto /etc/default/grub and open the grub file. There, u change the line GRUB_TIMEOUT=30
 after that, goto terminal and type
 ```
sudo update-grub
```
Restart your machine. u will get your grub and 30 seconds to choose between your OSs..
hope this helps.

Regards,WinuxUser

---

### Post by celticzero on 2012-01-22
I followed your instructions exactly and am still having the same issue.

---

### Post by nipunshakya on 2012-01-22
ok a couple of questions here....
1. is your windows and ubuntu on same drive?
2. did u save your file last time(which i said u to edit)? silly question #2 but still....

---

### Post by celticzero on 2012-01-22
They are both installed on the same HDD yes. The only way I can get Windows to boot is to go into BIOS and select Windows Boot Manager as my #1 option, if I select the HDD itself, it will boot straight to unbuntu. The file saved, I've verified its been edited properly.

---

### Post by nipunshakya on 2012-01-22
okay boot to ubuntu and try as suggested from the following link.

[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

Hope this time it will work.Goodluck
Regards,WInuxUser

---

### Post by celticzero on 2012-01-22
It is telling me that my PC is in BIOS boot mode (makes sense) and that I need to switch it to EFI. How do I go about doing that?

---

### Post by darkod on 2012-01-22
I have never seen a "Windows Boot Manager". I am not sure if we are talking about EFI boot, instead of BIOS boot. Usually you specify what hdd to boot from in BIOS, not any windows boot manager.

Can you tell if you are using EFI boot or BIOS boot?

Also, follow the link in my signature, run the boot info script, and post the results here as explained there. It will show more details.

---

### Post by nipunshakya on 2012-01-22
hmm...i had done a grub repair to myself using that tool i suggested you, but i have no idea about switching from BIOS to EFI ... im sorry about that query mate..Maybe its best for you to wait for someone to help you out with this situation...Sorry

The least i can do for u in this situation is provide this link:
[http://technet.microsoft.com/en-us/library/hh290677%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/hh290677%28WS.10%29.aspx)

Regards,WinuxUser

---

### Post by celticzero on 2012-01-22
Apparently it is in BIOS boots and not EFI. I have never seen "Windows Boot Manager" before these either. I believe it appeared when I attempted to install wubi, but I can't be sure. Right now though it is the only way to boot to windows as selecting the HDD that Windows and Ubuntu are installed on results in booting straight to Ubuntu. 

I tried running the grub repair tool and now I can't boot to Ubuntu at all.

---

### Post by darkod on 2012-01-22
> **celticzero said:**
> It is telling me that my PC is in BIOS boot mode (makes sense) and that I need to switch it to EFI. How do I go about doing that?

You should be able to make that choice in BIOS. But the problem is that with EFI, there is a small efi system partition where the bootloaders go, and both windows and ubuntu bootloader try to install there effectively deleting the other one.

If you plan to dual boot with EFI you need to do more investigating on google about how to accomplish that.

On the other hand, I think you will not be able to use BIOS boot if windows was installed to use EFI. I am not 100% sure, but I think it can't simply switch.

---

### Post by nipunshakya on 2012-01-22
> **celticzero said:**
> Apparently it is in BIOS boots and not EFI. I have never seen "Windows Boot Manager" before these either. I believe it appeared when I attempted to install wubi, but I can't be sure. Right now though it is the only way to boot to windows as selecting the HDD that Windows and Ubuntu are installed on results in booting straight to Ubuntu. 

I tried running the grub repair tool and now I can't boot to Ubuntu at all.

Sorry that the tool didn't work out. Thats coz your firmware wasn't confirmed.
Your ubuntu's boot calls are being made from the EFI while windows' boot calls are being made from the BIOS. However, your EFI interacts first with your hardware and that might be the reason why u get ubuntu to load directly as you power on your pc

---

