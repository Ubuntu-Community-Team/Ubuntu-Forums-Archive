---
title: "Ubuntu boot error; USB 3; /dev/disk/by-uuid/xxxx does not exist"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Lycake on 2011-05-24
Hello,
i tried to install Ubuntu 11.04 on my new USB 3.0 drive. There were no problems with the installation but when I'm trying to boot it now, I get this message: 

/dev/disk/by-uuid/[long-set-of-numbers] does not exist. Dropping to shell!

I am new to this so I googled around a bit. Most people get this error because of wrong UUIDs in the grub config or fstab. I checked the UUIDs in the grub.cfg, fstab and blkid (booted from live cd). They all match.

Hope there is a genius out there who can help me with this.

Thanks

---

### Post by Rubi1200 on 2011-05-24
Hi and welcome to the forums :-)

I am no genius, but I know what you should do to start troubleshooting this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Hedgehog1 on 2011-05-25
As a side note:

Ubuntu will not boot from a USB 3.0 port with a USB 3.0 drive in it.

If you move the external drive to a USB 2.0 port, it will boot.

Once Ubuntu is booted, it can and read and write to USB 3.0 drives fine, and you can even install Ubuntu on a USB 3.0 drive (as you have found out).

You just can't boot from it. For now...


***The Hedge***

:KS

---

### Post by Lycake on 2011-05-27
Hi,
thank you for your answers.

I didn't had the time to test it again, yet, but I think I'll be able to run the boot info script this evening. But if Hedgehog is right, this is the problem. I'll try to boot from USB 2.0, too.

Relateing to the USB 3.0 problem: I found [this post]("http://www.meisterkuehler.de/forum/linux-unix/30706-loesung-ubuntu-usb-3-stick-booten.html") in a german forum. It sais, that I just have to add "[COLOR=#529E00][COLOR=#333333]xhci-hcd             " to[/COLOR][/COLOR] "[COLOR=#529E00][COLOR=#333333]/etc/initramfs-tools/modules" to get Ubuntu booted from my USB 3 port. I don't know what I'm doing there, so.. is it possible that such an easy solution could solve the problem?

Thanks,
cake
[/COLOR][/COLOR]

---

### Post by Rubi1200 on 2011-05-27
Well, that solution does seem deceptively simple. Of course, it would be great if it were that easy.

It would have been nice, though, to see others posting to confirm whether it works or not.

Let's wait and see if Hedgehog1 has anything to add before you go ahead and try it.

---

### Post by Dilot on 2011-05-28
Trying not to Hijack.

---

### Post by Hedgehog1 on 2011-05-28
> **Dilot said:**
> I am having the same problem (except I am not using USB 3.0, only 2.0).  Any kind of help would be great.
...
Dilot

Dilot,

Your issue is different, and I don't want to hijack this thread.

Please start a new thread with your issue and your boot script output, and we will help you on that thread.

Thanks!

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-28
> **Rubi1200 said:**
> Let's wait and see if Hedgehog1 has anything to add before you go ahead and try it.

Sadly, I don't have any USB 3.0 hardware to test it myself; all my testing was done by asking others who had issues with USB 3.0 to try things.

My German is rusty (at best) but let me see what I can see on that thread.  Right now the page will not load for me...

***The Hedge***

:KS

---

### Post by drs305 on 2011-05-28
Lycake,

When you post the RESULTS.txt, also please give us the UUID in the error message (or at least the first 5 digits or so). It will save us time by pinpointing which UUID is causing the system to complain.

---

### Post by Hedgehog1 on 2011-05-28
Well, if I am reading these links correctly, booting from USB 3.0 may be just one kernal away.

[bootable-usb-3]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/458792-boot-problem-nec-bootable-usb-3-port-2.html")

They are claiming being able to boot from USB 3.0 using the next kernel 2.6.39. Natty is at kernel 2.6.38.

Assuming I am understanding this, you do NOT want to change the /etc/initramfs-tools/modules to carry the "xhci-hcd " text; that entry appears to be for the testing phase of the new xchi driver.

It appears you will have to boot from UBS 2.0 until the next big Kernel update arrives.

***The Hedge***

:KS

---

### Post by JoeCounter on 2011-06-11
> **Lycake said:**
> Hi,
thank you for your answers.

I didn't had the time to test it again, yet, but I think I'll be able to run the boot info script this evening. But if Hedgehog is right, this is the problem. I'll try to boot from USB 2.0, too.

Relateing to the USB 3.0 problem: I found [this post]("http://www.meisterkuehler.de/forum/linux-unix/30706-loesung-ubuntu-usb-3-stick-booten.html") in a german forum. It sais, that I just have to add "[COLOR=#529E00][COLOR=#333333]xhci-hcd             " to[/COLOR][/COLOR] "[COLOR=#529E00][COLOR=#333333]/etc/initramfs-tools/modules" to get Ubuntu booted from my USB 3 port. I don't know what I'm doing there, so.. is it possible that such an easy solution could solve the problem?

Thanks,
cake
[/COLOR][/COLOR]

Great, that worked for me on Ubuntu 10.04 (Backtrack 5).
Just add **'xhci-hcd'** to your **'/etc/initramfs-tools/modules'** file and update your initramfs with **'sudo update-initramfs -u'**! ;)

After restart I was able to boot an USB 3.0 16 GB stick from my USB 3.0 laptop port.

Joe.

---

