---
title: "Installed  10.04.4     &amp;  lost      Mandriva"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by kliq on 2012-05-25
Hello.

At work I use Mandriva 2008 {can't change that now because there is paid-for software installed in it that can not be transferred to anywhere else}.

From next April the UK Inland Revenue require us to run their software and Ubuntu is [one of two of] their designated choices of Linux.

So I installed Ubuntu which works fine, BUT  ..........
then when I selected Mandriva at the Boot Screen ..........
nothing booted up.

It turns out that Mandriva requires to be booted up from whatever it put in the first 63 sectors of the hard drive.
VERY fortunately, for entirely unrelated reasons, I had backed-up those sectors last week and so I have been able to get Mandriva working again.

So, two points:
1) To prevent any surviving commercial users of Mandriva getting sacked and then commiting suicide when they too eventually do an alongside-install of Ubuntu and have no boot sector back-ups to fall back on, can the development team please at LEAST add-in a routine to back-up the first 63 sectors of the hard drive so that the unfortunate person has some hope of restoring their original system.

2) Can anyone please tell me how to modify the Mandriva  menu.lst   file (below), so that when I select Ubuntu from the Boot-Menu it will start Ubuntu; there is only one hard drive and it has three partitions: Ubuntu on hda3, Mandriva on hda2 and something unmentionable on hda1.
```


timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,1)/boot/gfxmenu
default 0

title linux
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda2  splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

title linux-nonfb
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hda2 
initrd (hd0,1)/boot/initrd.img

title failsafe
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hda2  failsafe
initrd (hd0,1)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

```Thank you

---

### Post by 2F4U on 2012-05-25
A grub1 tutorial for Ubuntu can be found here:

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Please note that Ubuntu now uses grub2. Appropriate tutorials for grub2 can be found here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2%20Other%20Os]("https://help.ubuntu.com/community/Grub2%20Other%20Os")

It should be no problem to either get Mandriva to boot Ubuntu or vice versa.

---

### Post by kliq on 2012-05-26
Thanks.

Being a work computer, it is impractical for me to be trying bootloaders that I likely can not get to work.
I have to be able to start Mandriva at the push of the Reset button.
Only the existing Grub1 bootloader can do that for me, so I have to get that working with Ubuntu.

I have tried:

```

title linux-Ubuntu
kernel (hd0,2)/boot/vmlinuz-2.6.32-38-generic  root=/dev/hda3   vga=788
initrd (hd0,2)/boot/initrd.img-2.6.32-38-generic
```and also:
```

title linux-Ubuntu
kernel (hd0,2)/vmlinuz  root=/dev/hda3   vga=788
initrd (hd0,2)/initrd.img

```in the menu.lst file, but neither worked;
 a BIOS message popped up for the blink of an eye [couldn't read it] and then the screen stayed blank.
AFAIKS - that should have worked, so I am starting to think that Ubuntu needs something extra (??)

Ubuntu /boot  looks like:
```

abi-2.6.32-38-generic
config-2.6.32-38-generic
grub/
initrd.img-2.6.32-38-generic
memtest86+.bin
System.map-2.6.32-38-generic
vmcoreinfo-2.6.32-38-generic
vmlinuz-2.6.32-38-generic

```and in / there are:
```

initrd.img
vmlinuz

```Mandriva's  /boot/grub/device.map file looks like:
```

(fd0) /dev/fd0
(hd0) /dev/hda

```any ideas, please.

---

### Post by darkod on 2012-05-26
Have you tied without the vga parameter? You might need that only for Mandriva.

In general, it could be video driver related. Try first wihout any vga parameter, if that doesn't work try to replace the vga with nomodeset.

---

### Post by oldfred on 2012-05-26
Almost sure grub2 would have boot mandriva, but since you want grub legacy this is a boot stanza to boot the most current kernel. Change to your drive & partition.


```
title    Most Current Ubuntu on sda3
root    (hd0,2)
kernel   /vmlinuz root=/dev/sda3 ro quiet splash
initrd  /initrd.img

```

---

### Post by kliq on 2012-05-26
[darkod]("http://ubuntuforums.org/member.php?u=946366"):
Your idea about vga was correct.
Ubuntu started - but didn't complete and dropped into Busybox.
However the error message a few inches above it on the screen related to a search for the hard drive - 'hda' and - luckily - I remembered that Ubuntu doesn't use the 'hda'  format but the 'sda' one instead.
So I changed menu.lst to read:
```

title linux-Ubuntu
kernel (hd0,2)/vmlinuz  root=/dev/sda3
initrd (hd0,2)/initrd.img

```and then - success.

Thank you to you too [[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711").
You'd have got me there too if my memory had been less with it.

But I now have another problem with this CD here:
 [http://ubuntuforums.org/showthread.php?t=1987803](http://ubuntuforums.org/showthread.php?t=1987803)

---

