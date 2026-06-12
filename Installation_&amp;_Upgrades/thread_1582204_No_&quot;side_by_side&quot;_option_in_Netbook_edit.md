---
title: "No &quot;side by side&quot; option in Netbook edition"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by rayms on 2010-09-26
Hello everyone,

After succesfull (dual-boot) installation of Ubuntu 10.04 on my desktop and laptop, I wanted to do the same for my netbook. I downloaded the Ubuntu Netbook edition ([http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)), and doing the same as before I wanted to select the " install them side by side" option. But in the installation menu (which is not the same as on screenshots on the [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) website, where they use the screenshots from desktop edition) there is no such option. Is that only possible with the desktop distribution? Am I doing something wrong?

---

### Post by mikewhatever on 2010-09-26
As far as I know, the installers for the netbook and the desktop editions are identical, simply because the very same installer is used for both. I think the 'side by side' option is only shown when the installer detects a Windows installation. Is there a Windows installation, and is it detected? If the 'side by side' option is not available, then what options are?

---

### Post by rayms on 2010-09-26
> **mikewhatever said:**
> As far as I know, the installers for the netbook and the desktop editions are identical, simply because the very same installer is used for both. I think the 'side by side' option is only shown when the installer detects a Windows installation. Is there a Windows installation, and is it detected? If the 'side by side' option is not available, then what options are?

Thank you for replying: It sees the standard Windows XP installation (which has a C and D drive) and gives me the options erase the disk and configure manually. I do not see the side by side option like the screenshot on the instructions page

---

### Post by TheBritishEditor on 2010-09-26
I've had the exact same problem. How many partitions are on your drive already?

---

### Post by rayms on 2010-09-27
It has two partitions C and D, which is the default HP installation, which has never been changed

---

### Post by Mark Phelps on 2010-09-27
> **rayms said:**
> It has two partitions C and D, which is the default HP installation ...

Not in my experience ... is that the "default HP installation".

Instead, they generally include another partition called HP_TOOLS (or something like that), and they often also include another partition called RECOVERY (or something like that).

Those other partitions (especially the RECOVERY one) might be hidden, which is why you might not see them.

---

### Post by mikewhatever on 2010-09-27
When the 'side by side' option is not present, the easiest way to install Ubuntu is in two separate steps: one - preparing the unallocated space, two - installing.

_Step one_
Boot from the CD/usb and select 'Try Ubuntu'.
When the desktop loads, open System->Administration->Gparted, and manually resize the existing Windows partition, usually the largest on the hdd. Resizing will create unallocated space for the future Ubuntu installation. When done, close Gparted and launch the installer.

_Step two_
At the partitioning stage, look for a the option - "Use the largest continuous free space". If selected, that option will make the installer use the previously prepared unallocated space.

---

