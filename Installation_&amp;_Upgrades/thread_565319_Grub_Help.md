---
title: "Grub Help"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by YaAqoB on 2007-10-02
Hello all.
I reinstalled windows a while back and now GRUB no longer appears so I can choose to boot ubuntu.
I have read the other threads and when I attempt the fixes it leaves mew with nothing booting and I have to do a fixmbr from the windows recover console.
When I type "find /boot/grub/stage1" I get (hd1,0) in return.
I then type "root (hd1,0)"
followed by "setup (hd0)" and I get a succeeded report.
When I reboot nothing loads. I have also tried "setup (hd1)" but same result.

My hard drives are as follows.
Disk0 = entire partition for Windows XP
Disk1 = entire partition for Ubuntu 7.04

Any help would be great.

Thanks

---

### Post by overlord.gaurav on 2007-10-02
I haven't yet tried this with Ubuntu Live CD, but I'm sure it works with the Ubuntu alternate CD.

Insert the Ubuntu alternate CD & reboot.
When the CD boots, select Rescue broken system.
This will start something similar to the installation which you had done the last time.
When the setup reaches "Installing Base System" cancel it.
Then directly scroll down and select "Install Boot Grub Loader".
Once installed, reboot and its done!

---

### Post by YaAqoB on 2007-10-02
Thank you very much. I'll try & find an alternative CD and give it a go.
Thanks again.

---

