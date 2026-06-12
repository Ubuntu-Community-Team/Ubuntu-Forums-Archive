---
title: "Error:cannot find GRLDR in all devices,press Ctrl+Alt+Del to restart."
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by zhenhao on 2015-08-06
Try (HD0,0): NTFS5: No grldr
Try (HD0,1): NTFS5: No grldr
Try (HD0,2): invalid or null
Try (HD0,3): invalid or null
Error:cannot find GRLDR in all devices,press Ctrl+Alt+Del to restart. 

Hi...can I help me solve this problem. Now even can't getting into my Windows7 system. I install the Linux in my pendrive, and after I try to open then become like that. Is't gt some mistake or error when I install it. Help me plssss.....

---

### Post by ajgreeny on 2015-08-06
I suspect this error shows that you have installed Ubuntu using WUBI; ie installed it within a running Windows OS.

WUBI is no longer supported so I'm afraid you are not likely to get much help in this forum any more, and unfortunately I have no knowledge of how using it might affect your Windows installation to stop that from booting.  You may need to use your Windows DVD if you have one, or the recovery DVD you should have made when you were recommended to do so at first boot of Windows.

Wait for more replies before doing anything as there may be others here who can help you, but do not try to use WUBI again because, as I say, it is not supported now, and few forum members can help with its use.

---

### Post by oldfred on 2015-08-06
I think that is the very old grub4dos boot loader, usually used by EasyBCD and Neosmart.

[https://neosmart.net/wiki/cannot-find-grldr/](https://neosmart.net/wiki/cannot-find-grldr/)

With Ubuntu we prefer to use grub2 as the boot manager or menu of operating systems as  well as the boot loader for Linux based systems.

---

### Post by yancek on 2015-08-06
Since you are posting here, can we safely assume you are using Ubuntu?  Which release?  When do you get that error, when you select Ubuntu from the menu?  Did you actually install your Linux system on a pen drive?  or did you use some software to put a Live CD on a pen drive?  What do you mean by "try to open"?  Try to open what?

---

