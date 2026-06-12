---
title: "Ubuntu 20.04 Windows 10 dual-boot on one disk."
date: 2020-11-05
forum: Installation &amp; Upgrades
---

### Post by sliwkahax on 2020-11-05
Hello.
I tried to make a dual-boot. I had ubuntu 20.04 before, then i made a bootable windows 10 installater flashdrive and i have installed it on a diffrent partition.
I thought there would be some sort of gui at boot, but no. It boots windows. 
Whenever i go into diskmgmt.msc the linux partition doesn't show up. (Probably cuz its an unknown type for windows)

Any possible way i can choose wich one i want to boot?

Thanks.

ror~

---

### Post by jdeca57 on 2020-11-05
As far as I know that is normal Windows behavior: it doesn't take other OS in account. So you have to fix it by booting in Ubuntu with the startup usb/DVD you used in the first place. A way to do this:
```
    Insert your Ubuntu CD, reboot your computer and set it to boot from CD in the BIOS
 and boot into a live session. You can also use a LiveUSB if you have created one in the past.
    Install and run Boot-Repair.
    Click "Recommended Repair".
    Now reboot your system. The usual GRUB boot menu should appear.
```

---

### Post by sliwkahax on 2020-11-05
I meant i had Windows, then i installed Ubuntu wiping Windows. And now i have ubuntu and windows on diffrent partitions (On a hard drive)
I installed all via flashdrive (iso). After wiping windows i had only ubuntu, and i had to wipe the flashdrive to make a space for the windows installer. (That windows that now boots instead ubuntu).

So i have to burn out an ubuntu iso again on the flashdrive wiping the windows installer?

---

### Post by tea for one on 2020-11-05
> **sliwkahax said:**
> Any possible way i can choose wich one i want to boot?

Yes, there is, assuming you have followed the advised installation process.

Have you installed Windows 10 and Ubuntu in UEFI mode?

Have a look at this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) - particularly General Principles

If you have installed both Windows 10 and Ubuntu correctly, you should be able to select either via their respective Boot Managers.

Do you know the dedicated key for your PC to access the UEFI Boot menu?

---

### Post by ajgreeny on 2020-11-05
We need to  know exactly where you are with this situation so go to Boot-repair in my signature there and run thr Boot-info script.

**Do not run default repair**,  simply run the script and post back here the pastebin  url you are shown. Our experts in this can then probably help more appropriately.

---

### Post by C.S.Cameron on 2020-11-05
Here is something that worked for me.
Create a Full install Ubuntu USB. 
Plug the USB into the computer and boot it in the same BIOS or UEFI mode as the OS's on the computer.
Run "sudo update-grub"
If there is a workable Ubuntu install on the computer, it should be added to the USB boot menu.
Boot from USB again, select the Ubuntu install on the computer.
You can try again selecting Windows from the grub boot menu.
If all works well, you know that you only need to reinstall grub on the computer for everything to work again.

---

### Post by sliwkahax on 2020-11-05
> **tea for one said:**
> Yes, there is, assuming you have followed the advised installation process.

Have you installed Windows 10 and Ubuntu in UEFI mode?

Have a look at this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) - particularly General Principles

If you have installed both Windows 10 and Ubuntu correctly, you should be able to select either via their respective Boot Managers.

Do you know the dedicated key for your PC to access the UEFI Boot menu?

The thing is idk if i installed both in UEFI mode.

For both OS, i have set that the boot will start from usb.

---

### Post by sliwkahax on 2020-11-05
> **tea for one said:**
> Yes, there is, assuming you have followed the advised installation process.

Have you installed Windows 10 and Ubuntu in UEFI mode?

Have a look at this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) - particularly General Principles

If you have installed both Windows 10 and Ubuntu correctly, you should be able to select either via their respective Boot Managers.

Do you know the dedicated key for your PC to access the UEFI Boot menu?

I checked it and i have installed windows with BIOS environment.
For ubuntu i have no idea.

---

### Post by yancek on 2020-11-05
I would suggest you read through the pages at the link posted above in post 4 as it should answer your questions and is the official Ubuntu documentation on the subject.  How old is your hardware?  Can you access the BIOS firmware and check the Boot tab to see if there is any reference to UEFI?  If you have installed windows in the older Legacy mode, then Ubuntu must also be installed in Legacy.  If you installed both Legacy and windows after Ubuntu, then windows by default will automatically overwrite the Grub code in the MBR so only windows boots.  If will not ask nor will it inform you this is being done and this has been the standard with windows for decades.  

If you are unable to obtain this information, get the boot repair software and run it from the link in post 5 above.  Use the 2nd option explained on that page and make certain you use only the Create BootInfo Summary and post the link you get when it finishes here.

---

### Post by sliwkahax on 2020-11-05
I wanted to make a dualboot Windows - Ubuntu.
I have windows installed in BIOS mode.
And i have heard that if i want a dual boot both OS have to be installed in the same mode.
Thanks.

ror~

---

### Post by CelticWarrior on 2020-11-05
> **sliwkahax said:**
> 
And i have heard that if i want a dual boot both OS have to be installed in the same mode.


Yes, that is correct, but if the machine is UEFI then ALL OSes should be installed in UEFI mode.
How it boots is how it installs.

---

### Post by sliwkahax on 2020-11-05
The thing is how do i boot it so it will install via legacy mode?

Btw thanks for the fast response.

---

### Post by CelticWarrior on 2020-11-05
The same way you did in order to install Windows?

The only situation where you may have to choose is with "UEFI + Legacy" settings in the firmware (UEFI). Then the USB media will be listed twice and one of them will have "UEFI:" something. 
If you already have Windows in Legacy mode then you can enable "Legacy only" in UEFI and that makes all USB media automatically boot in Legacy mode.

---

### Post by sliwkahax on 2020-11-05
I have no idea how i installed windows i just put the flashdrive and installed it.
When i tried to make it so it will boot from legacy there wasn't an option like that and in the desc it said "UEFI boot has higher priority than legacy boot"

---

### Post by CelticWarrior on 2020-11-05
Then my only suggestions here is for you to read your manual as well as the links already provided in your other thread.
Installing an OS nowadays is easy but there's a bare minimum knowledge required.

---

### Post by ajgreeny on 2020-11-05
What device options you are offered when you boot to the USB probably depends on how the USB install medium was created.

I always see the OS i want to install listed twice, first without UEFI in its name and lower down the list the same but with UEFI at the start of the name.
Not surprisingly the first will give you a BIOS install, the second a UEFI install.
Does that make sense and help you decide?

---

### Post by DuckHook on 2020-11-05
@sliwkahax

I have merged your separate threads, all dealing with the same topic. Please do not create duplicate threads. As you have demonstrated, it sows confusion among those trying to help and dilutes community effort.

---

