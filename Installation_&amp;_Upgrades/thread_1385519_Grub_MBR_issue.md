---
title: "Grub MBR issue"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Athlon1 on 2010-01-19
Hi

I have installed Kubuntu on a usb stick. (hope this is right place for this question)

I installed version 9.04 from a disk that came with linux magazine. After installation I can only boot pc if the usb stick is plugged into pc before I turn it on. I then gat a menu with 5 options. The first is Kubuntu and the last is Windows XP. If I try to boot my pc without the usb stick plugged in I get a GRUB error message.

I think this is the GRUB menu which means that it must have amended the Master Boot Record.

If I try to boot my pc without the usb stick plugged in I get a GRUB error message.

This is generally a minor inconvenience and a great security measure. My worry is that I am notorious for losing usb sticks. If I lose this one I wont be able to boot pc.

Is there a way to remove GRUB and restore the MBR?

Thanks

---

### Post by darkod on 2010-01-19
If you have the XP install disc just follow the procedure here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Athlon1 on 2010-01-20
Thanks for the link. Unfortunately I cannot find the original Dell recovery cd that came with the pc. The pc is a Dell Dimension 5000 that is about 5 years old..

I do have a copy of Windows XP that I had intended to use on another machine. Will this work for recovery or does the Dell recovery disk have stuff that is specific to the way they set up their machines?

---

### Post by darkod on 2010-01-20
> **Athlon1 said:**
> Thanks for the link. Unfortunately I cannot find the original Dell recovery cd that came with the pc. The pc is a Dell Dimension 5000 that is about 5 years old..

I do have a copy of Windows XP that I had intended to use on another machine. Will this work for recovery or does the Dell recovery disk have stuff that is specific to the way they set up their machines?

No problem. That XP copy will do the job. You will not install it, just repair the bootloader so you're allowed to use it and then install it on another computer.

If it doesn't work, there is option to do it with the ubuntu cd too, I just don't have the commands at hand. I can look if this doesn't work.

---

### Post by Leppie on 2010-01-20
> **Athlon1 said:**
> Thanks for the link. Unfortunately I cannot find the original Dell recovery cd that came with the pc. The pc is a Dell Dimension 5000 that is about 5 years old..

I do have a copy of Windows XP that I had intended to use on another machine. Will this work for recovery or does the Dell recovery disk have stuff that is specific to the way they set up their machines?
you can also use ubuntu to restore your mbr:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
ignore the warning/message it will generate, after this your system should boot straight into windows ;)

---

