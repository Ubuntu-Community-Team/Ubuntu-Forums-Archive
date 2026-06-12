---
title: "Different Behavior With Black Screen After Update/Reboot"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by Absinthe2001 on 2013-04-09
Ubuntu 12.10
I recently allowed the current update that involved Kernel 3.5.0-27-generic and got the blank screen issue. I was not able to ctrl-alt f1 etc.

What I did do, was reboot and at the grub menu, chose Advanced Options and then selected the the "Ubuntu, with Linux 3.5.0-27-generic" and hit the right arrow, and it boots happily. However, as long as I simply hit enter on the "Ubuntu" menu it boots to black. 

I don't see any difference between the two entries in grub.cfg so I can't understand what would be different from hitting enter when the grub menu comes up, versus going into the Advanced menu options and selecting the kernel. 

Here is just a snippet of the grub.cfg for those two entries. 

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-22021d73-d2f7-4f11-b853-886887e31b07' {
recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  22021d73-d2f7-4f11-b853-886887e31b07
        else
          search --no-floppy --fs-uuid --set=root 22021d73-d2f7-4f11-b853-886887e31b07
        fi
        linux   /boot/vmlinuz-3.5.0-27-generic root=UUID=22021d73-d2f7-4f11-b853-886887e31b07 ro   splash quiet $vt_handoff
        initrd  /boot/initrd.img-3.5.0-27-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-22021d73-d2f7-4f11-b853-886887e31b07' {
        menuentry 'Ubuntu, with Linux 3.5.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-generic-advanced-22021d73-d2f7-4f11-b853-886887e31b07' {
        recordfail
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd0,msdos5'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  22021d73-d2f7-4f11-b853-886887e31b07
                else
                  search --no-floppy --fs-uuid --set=root 22021d73-d2f7-4f11-b853-886887e31b07
                fi
                echo    'Loading Linux 3.5.0-27-generic ...'
                linux   /boot/vmlinuz-3.5.0-27-generic root=UUID=22021d73-d2f7-4f11-b853-886887e31b07 ro   splash quiet $vt_handoff
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-3.5.0-27-generic
        }

```

---

### Post by bogan on 2013-04-09
Hi!, **Absinthe2001**,

Here is the difference from your Grub.cfg:

menuentry 'Ubuntu' ---------------------------------------------"$menuentry_id_option 'gnulinux-simple-22021d73-d2f7-4f11-b853-886887e31b07'"
menuentry 'Ubuntu, with Linux 3.5.0-27-generic'--"$menuentry_id_option 'gnulinux-3.5.0-27-generic-advanced-22021d73-d2f7-4f11-b853-886887e31b07'"
  
Chao!, **bogan**.

---

### Post by Absinthe2001 on 2013-04-09
Thanks Bogan!

I will admit to being both blind as well as stupid if you can explain to me what the implications of that difference is? I am not I understand what is actually getting loaded when "gnulinux-simple-..." is invoked versus the explicit kernel version entry.

-- Abs

---

### Post by bogan on 2013-04-09
Hi!, **Absinthe2001,**

I was just pointing out the difference, as I had noted the same difference in my /boot/grub/grub.cfg with 3.5.0-27-generic.

However, I can not explain the difference in use between 'simple' & 'advanced', as both menu options boot correctly with my main 12.10 installation.

One possible difference is that this 3.5.0-27 is #46 and upgraded by the Proposed PPA.

I will check my other installations and Post if there is any difference.

Chao!,** bogan.**

---

### Post by bogan on 2013-04-09
Hi!, **Absinthe2001**,

I just checked the 12.`0 installations on an USB stick and an USB external HDD, both of which run 12.10. 3.5.0-26 #45 and neither have the same script wording as -27 #46.

That is, they go directly to the UUID without the 'gnulinux-simple-' or 'gnulinux-3.5.0-27-generic-advanced-' additional wording.

Edit: The above is not strictly correct!!

The additional wording is indeed present in grub.cfg in both #26 & #27, but it does not appear in the script of grub menu of either, which is where I checked to get the above conclusion.

I think you need to check the wording af the Grub Menu scripts, as there must be some effective difference there, mine are the same for both Ubuntu and ubuntu with 3.5.0-27.

**Edit**: Re: your last question. I think the answer lies in the wording: > $menuentry_id_option  ie it is not the 'menuentry' itself, but  a variable ' $menuentry' .

Chao!, **bogan.**

---

### Post by Absinthe2001 on 2013-04-09
I think a better question on my part is what does that actual line achieve? If you walk th escript you see that the initrd calls the same kernel file. So I am not sure what purpose that one with the "simple" achieves. I would have assumed that since it didn't contain an identifiable kernel in its name that it somehow pointed at some "default" area where settings would be kept. But then it goes on to explicitely call the kernel in the initrd command.

---

### Post by bogan on 2013-04-09
Hi!, **Absinthe 2001,**

Perhaps I was not clear enough.

What I should have said is that the part of grub,cfg that you quoted is not the part that controls the script sent to grub menu, rather it is this:```
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  b5aab3a2-0086-4a12-9276-46bb5a615038
```which in my installation is identical for both Ubuntu and Ubuntu with 3.5.0-26 & -27.

Presumably, in yours there is some difference, to account for it not working the same way. It is the actual grub menu script texts that you need to check. 

**Edit**: Re: your last question. I think the answer lies in the wording:                                                          "$menuentry_id_option".  ie it is not the 'menuentry' itself, but  a variable ' $menuentry' .




Chao!,** bogan.**

---

### Post by Absinthe2001 on 2013-04-09
Or so one might think... But you saw what the differences were and weren't between those two menu entry lines. They are the same.

---

### Post by xhiko on 2013-04-09
I'm having a similar issue: I get a black screen at first boot and have to hold the power button to shut the PC down. When I turn it on again I get the GRUB prompt, but in my case all options now boot correctly (Ubuntu and advanced option with all kernel choices).

I'm using a fresh install of Xubuntu 12.10

Is there any way to get the GRUB menu at first boot? Or correct this issue altogether?

---

### Post by bogan on 2013-04-10
@**xhiko,**

Try pressing 'Shift' as soon as the Bios splash screen closes.

You Posted: > When I turn it on again I get the GRUB promptI guess you meant the 'Grub Menu', listing boot OS options.

The 'Grub Prompt' is quite different and would imply a serious error.

Chao!,** bogan**.

---

### Post by Absinthe2001 on 2013-04-10
I believe you can change the setting of 

recordfail

This link will likely get you started:

[http://superuser.com/questions/124992/how-to-enable-boot-timeout-in-grub2](http://superuser.com/questions/124992/how-to-enable-boot-timeout-in-grub2)

---

