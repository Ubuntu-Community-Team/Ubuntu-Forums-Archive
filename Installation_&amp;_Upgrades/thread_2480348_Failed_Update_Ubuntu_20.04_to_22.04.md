---
title: "Failed Update Ubuntu 20.04 to 22.04"
date: 2022-10-26
forum: Installation &amp; Upgrades
---

### Post by vinx2 on 2022-10-26
Hello everyone,

Last Sunday I tried to upgrade my Ubuntu 20.04 to Ubuntu 22.04, but the upgrade proposed from Ubuntu Software Update didn't work then I used the terminal.
On the final stage something went wrong and received a message saying upgrade was not successful.

From that moment I couldn't use the file manager and I decided to reboot, which failed. 
After some googling I found a procedure [https://koen.vervloesem.eu/blog/fixing-a-failed-upgrade-to-ubuntu-2204-lts-in-recovery-mode/](https://koen.vervloesem.eu/blog/fixing-a-failed-upgrade-to-ubuntu-2204-lts-in-recovery-mode/) to repair the failed upgrade using the recovery mode, but was unable start the recovery mode for Ubuntu 20.04. Failing message here as well. 
 
On my laptop I have Windows 10, Ubuntu 20.04, Ubuntu 18.04(didn't remember this one was still here). I also have a USB with Ubuntu 19.10. Don't have USB with Ubuntu 20.04.

So, how can I fix the broken upgrade without losing my data? I prefer not to install Ubuntu 22.04 but fix Ubuntu 20.04.

Can I use recovery mode or live USB from above versions (Ubuntu 18.04, 19.10) or I need a live USB with Ubuntu 20.04?

Can anyone help?
Thanks

---

### Post by grahammechanical on 2022-10-26
> but was unable start the recovery mode for Ubuntu 20.04. Failing message here as well.

The wording of messages is helpful. Do you get a Grub boot menu? Can you select Advance Options for Ubuntu? Do you see a Linux kernel with recovery mode? What happens when you select that? Do you get to a recovery mode menu? There should be at least two different Linux kernels. One kernel from 22.04 and one kernel from 20.04.

With three operating systems where do you keep your data? On a separate home partition? On a partition kept especially for data? Can you load 18.04? If so, you might be able to use 18.04 to transfer data from the messed up 20.04/22.04. You might be able to download and copy the Ubuntu 22.04 ISO image to a USB stick.

Regards

---

### Post by vinx2 on 2022-10-27
Thanks for your answer

On booting, grub prompt the option on OS to start. If choose Ubuntu as usual, nothing happens. it continue to try booting without success and keep showing Lenovo on the screen.

Then go for recovery mode

This is the failing message from Grub->Ubuntu 20.04 Advanced Option ->recovery mode
[B]/lib/recovery-mode/recovery-menu: line 120: /lib/recovery-mode/options/whiptail::No such file or directory


[/B]A part from that I can also run recovery mode for Ubuntu 18.04 or use live USB.

I don't get Grub anymore but this because I changed the boot order from Ubuntu 18.04 shell using **[COLOR=var(--black-800)][FONT=var(--ff-mono)]efibootmgr. [/FONT][/COLOR]**[COLOR=var(--black-800)][FONT=var(--ff-mono)]Did this to boot from USB.
[/FONT][/COLOR]Not a big problem by the way because I can use Windows Recovery to choose what to boot.

I can download Ubuntu 20.04 on USB. Wanted to know if this is the best way to go or there is a better option

Thanks

---

