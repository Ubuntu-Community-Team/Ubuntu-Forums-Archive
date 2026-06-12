---
title: "Grub menu not showing when dual booting Win10/Ubuntu"
date: 2019-12-18
forum: Installation &amp; Upgrades
---

### Post by theunforgiven71 on 2019-12-18
Hi,

I've installed Ubuntu 18.04 (I'll update later) on dual boot on a HP laptop running Windows 10.

Grub is not showing at startup so computer directly boot on Windows 10. I can boot on Ubuntu going to BIOS' boot menu.
- I've tried forcing it using the following command on Windows: ```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```
- I've tried to update grub.
- I've tried to use boot-repair. Boot-repair doesn't fixed it, even after setting bootmgr to ```
sda2/efi/ubuntu/shimx64.efi
``` (according to the pop-up that showed up when boot-repair was done).
You can find here boot-repair's logs: [http://paste.ubuntu.com/p/XN6Y96pGHv/](http://paste.ubuntu.com/p/XN6Y96pGHv/)

How to bring back Grub menu at boot (or any menu to dual boot)?

Thanks !

---

### Post by yancek on 2019-12-18
If you can boot Ubuntu from the BIOS, do that and open a terminal and run the following command.  Post the output here.

```
sudo efibootmgr
```

On my HP laptop on boot, I access the BIOS setup by hitting first the Esc key then the F10 key.  You should have similar settings.  If you have a System Configuration tab, go to that and then go to Boot Options and then UEFI Boot options.  Here you should see OS Boot Manager.  You should see a small arrow to the left of this option.  Highlight OS Boot Manager by using the arrow key on the keyboard and hit Enter.  You should see both windows and ubuntu there so highlight ubuntu with the arrow key and then hit the F6 key to move it up then F10 and Enter to save and exit.  If you don't have these options, you should have something similar.  I'm sure all HP laptops don't use the same method but it should be similar.

---

### Post by oldfred on 2019-12-18
I do not think directly related, but you need to have Windows fast start up off. Report says this:
>  Windows is hibernated, refused to mount. 



You should have Ubuntu first in UEFI boot order & Windows second. Line 1088.
sudo efibootmgr -v
After Boot-Repair reinstalled grub which uses efibootmgr to set boot order:
>         BootOrder: 0000,3003,3000,3002,3004,2001,2002,2003 
    

But some with HP have said using efibootmgr to set boot order, works only once. HP then seems to reset order. But if you go into HP's UEFI and change boot order from there it should work.

Others have had to change hard drive or fallback boot entry.
That is /EFI/Boot/bootx64.efi. With Windows bootx64.efi is a copy of Windows boot file. Grub now normally makes bootx64.efi a copy of shimx64.efi, so booting hard drive boots Ubuntu. And you may be able to set hard drive as first in boot order.

See this, you can delete duplicates & set boot order (if it works).
man efibootmgr

sudo efibootmgr -v
Boot order, Ubuntu entry first. If hard drive first then make 3000 first.
        sudo efibootmgr -o 0000,0003,3000

Delete duplicates:
sudo efibootmgr -v
sudo efibootmgr -b 3005 -B
I would delete all but one hard drive entry.

---

### Post by theunforgiven71 on 2019-12-19
Hi,
@yancek: as you said, I access boot menu by pressing ESC then F9. But when I go in BIOS to change boot order, I can only move "OS Boot Manager" on higher or lower priority, I can't "open" it to define Ubuntu as top priority (see screenshot below)

@yancek @oldfred : here is a pastebin of the efibootmgr command. And after every reboot, it resets to what is shown using argument -v 

Here is a picture of bios' boot menu: [https://i.ibb.co/yfnHdxk/IMG-20191219-190422.jpg](https://i.ibb.co/yfnHdxk/IMG-20191219-190422.jpg)

Picture of bios' boot order: [https://i.ibb.co/FbcnwGX/IMG-20191219-190235.jpg](https://i.ibb.co/FbcnwGX/IMG-20191219-190235.jpg)

Picture of grub screen when I select Ubuntu from boot menu: [https://i.ibb.co/qRMLddb/IMG-20191219-190513.jpg](https://i.ibb.co/qRMLddb/IMG-20191219-190513.jpg)
The "system setup" bring me back to the ESC menu where I can choose between boot menu, BIOS,...

Do you have any idea to fix it? Thanks :)

---

### Post by oldfred on 2019-12-19
System Set up is supposed to take you into UEFI/BIOS.

Can you not move Ubuntu entry up when in UEFI/BIOS, says at bottom of screen to use the arrow keys? And does it not stick?

---

### Post by yancek on 2019-12-19
The second image you posted above shows System Configuration, UEFI boot order and below that OS Boot Manager which should be able to be accessed by first hitting the Esc key then the F10 key.  The first image shows the boot options under OS Boot Manager which includes Ubuntu.  Use the keyboard down arrow key to highlight Ubuntu, then hit the F6 which should move it up.  If that works, hit F10 and then the Enter key to exit and save the change.  The Esc and F9 boot option is a one time change for that specific boot and does not save the change.

---

### Post by theunforgiven71 on 2019-12-20
Hi, it's a selection menu, I can't move entries

---

### Post by oldfred on 2019-12-20
That would normally be the UEFI boot menu.
In UEFI is a boot tab where you can change UEFI boot settings.

With HP Escape & f10 is UEFI  and Escape f9 is boot menu.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by theunforgiven71 on 2019-12-20
F1 System Information
F2 System Diagnostics
F9 Boot Device Options
F10 BIOS Setup
F11 System Recovery

So, F9 menu let me choose on what I want to boot, not change order (first picture in previous post) and F10 just show OS Boot Manager, not Ubuntu (second picture)

---

### Post by theunforgiven71 on 2020-01-14
Bump

What can I do to fix it please?
Thanks :)

---

### Post by oldfred on 2020-01-14
In F10 you should have boot tab where you can set boot order.

But some with HP, said they had to update UEFI to be able to reset boot options.

And while most systems will let you use efibootmgr to set boot order, HP seems to always reset on reboot.
Grub uses efibootmgr to set itself first in boot order when installed.

---

