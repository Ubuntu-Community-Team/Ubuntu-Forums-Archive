---
title: "Fresh Install, won't boot to grub"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by kyle38 on 2015-01-31
Hello,


I have a Zotac xs ad11 mini PC that  has UEFI firmware. I have successfully run Ubuntu 14 live media in UEFI  mode and installed, but my firmware will not boot it.

The boot options recognize the SSD and the "ubuntu" boot option that was created, but neither load an OS or Grub. My url is [http://paste.ubuntu.com/9987465](http://paste.ubuntu.com/9987465)

Please let me know if you can identify any other issues.

P.S. there is a legacy mode for USB booting, but it is not enabled for HDD/SSD boot. Legacy booting is not an option:/

---

### Post by oldfred on 2015-02-01
I am not sure but part of issue is drive order.
Your Kingston flash drive is seen as sda and hd0.
But then install is hd2 in both UEFI and and hd1 in grub menu.

Boot0000* ubuntu    [COLOR=#ff0000]HD(2[/COLOR],1000,f3800,0642990c-88b3-49ae-9a67-ff826051b91f)File(EFIubuntushimx64.efi)

Line 285
set root='[COLOR=#ff0000]hd1[/COLOR],gpt4'

When you reboot to boot install, do you still have flash drive plugged in?

But Ubuntu does use UUID 19ea... and a search so it should find correct partition.
And UEFI used GUID which script does not show and it should find correct partition.

---

### Post by kyle38 on 2015-02-07
After much experimentation with various bootloaders, install methods, etc. I broke down and got a new SDD. Turns out the Mushkin Atlas SDD is not compatible with the Zotac AD11, although this isn't documented (other than by omission on the Zotac recommended hardware manual page). Standard install after booting in UEFI mode worked fine. Thanks for the response and all the help from those in chat.

---

