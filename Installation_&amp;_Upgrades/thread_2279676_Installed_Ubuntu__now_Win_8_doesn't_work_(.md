---
title: "Installed Ubuntu  now Win 8 doesn't work :("
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by Astralogic on 2015-05-25
Hi, I installed Ubuntu along side windows but now when I choose Windows from the boot menu it fails to load saying cannot load image.

Any ideas how to fix this?

Thanks

---

### Post by yancek on 2015-05-25
More information will be needed and the easiest way to get that, since you are able to boot Ubuntu, is to go to the site below and download boot repair and run it.  Be sure to only select the option to "Create a BootInfo Summary" and post the output here.  That should give enough information for someone to suggest a possible solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Astralogic on 2015-05-25
[Here is the link]("http://paste.ubuntu.com/11349871/") to the information you requested.

---

### Post by oldfred on 2015-05-25
I do not think they fixed grub to boot Windows from secure boot.
You can directly boot Windows from UEFI boot menu or one time boot key often f10 or f12.

If you want to use grub menu to boot Windows secure boot needs to be off and Windows not hibernated or fast startup off which is always on hibernation.

---

### Post by Astralogic on 2015-05-25
Thanks that works perfectly.

---

