---
title: "EMERGENCY--Dual Boot Problem"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by shimmey on 2008-11-16
First I installed XP, then Ubuntu. The grub works very well.
Today I installed Vista, then used the method in full circle(15th) to fix the grub dual boot menu.
As the method said, I typed:
////
#>grub
grub>root (hd0,9)
setup (hd0,0)
quit
////

Unfortunately, either the xp or vista can't boot...

Is here anybody know how to solve this problem?
Now I can only boot ubuntu. But I really need xp, because many materials and programs could only run in it!

And I found a fatal problem, the first partition can't be found even! I can only see it in fdisk command list. Last time I met this kind of problem before on my desktop, I lost a partition... Who can help me?

Thanks for any help!

---

### Post by taurus on 2008-11-16
What is the method in full circle (15th)?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2008-11-16
> **shimmey said:**
> First I installed XP, then Ubuntu. The grub works very well.
Today I installed Vista, then used the method in full circle(15th) to fix the grub dual boot menu.
As the method said, I typed:
////
#>grub
grub>root (hd0,9)
setup [COLOR="Red"](hd0,0)[/COLOR]
quit
////

Using "setup (hd0,0)" installs Grub to the boot sector of sda1, which is probably your Windows partition; that's unfortunately most likely why you can't boot Windows now. You should use "setup (hd0)" instead to install Grub to the MBR (Master Boot Record). 

If sda1 is your Vista partition, you'll need your Vista Install CD to fix it; if you don't have a Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Just boot that up, go to the command line, and run:
```
bootrec /fixboot
```
And that should make Vista bootable again. Go ahead and run the Grub commands again to install Grub to the MBR (hd0), and you should be fine. Let me know how it goes.

---

### Post by shimmey on 2008-11-24
I've found a way to add a VISTA on the computer which installed XP and ubuntu already.
Please see:
[http://leelfin.spaces.live.com/blog/cns!FED522780D4C63DB!210.entry](http://leelfin.spaces.live.com/blog/cns!FED522780D4C63DB!210.entry)

---

