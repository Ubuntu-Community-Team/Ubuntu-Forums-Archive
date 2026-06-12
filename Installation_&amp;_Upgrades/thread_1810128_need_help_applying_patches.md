---
title: "need help applying patches"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by mick171 on 2011-07-22
hello, I'm fairly new to Linux but I need assistance applying the 3 patches mention here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802278](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802278)

I'm trying to get my usb 3 drives to work.

I have already updated the xhci drivers which involved creating a kernel. This was partially successufull but now I experience the issues mentioned in the above url.

I would like to read if possible a document that covers the complete process of
1) checking if a patch is on already or
2) receiving the patch
3) applying the patch

I've had a look around without much success and have even tried step 2 above, but I don't really know what I am doing.

Please help.

---

### Post by mick171 on 2011-07-23
Ok.. this is hard for me.

How do i install the following patch?
[http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=commit;h=e2b0217715c6d10379d94bdfe5560af96eecbb7c](http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=commit;h=e2b0217715c6d10379d94bdfe5560af96eecbb7c)

and 

[http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=commit;h=001fd3826f4c736ce292315782d015f768399080](http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=commit;h=001fd3826f4c736ce292315782d015f768399080)

and finally

[http://article.gmane.org/gmane.linux.usb.general/48323](http://article.gmane.org/gmane.linux.usb.general/48323)

---

### Post by dino99 on 2011-07-23
devs comments:

[http://answerpot.com/showthread.php?2743888-+xhci_hcd%3A+Etron+EJ168+controller+unusable](http://answerpot.com/showthread.php?2743888-+xhci_hcd%3A+Etron+EJ168+controller+unusable)

Applying patch:

[https://wiki.ubuntu.com/PackagingGuide/PatchSystems](https://wiki.ubuntu.com/PackagingGuide/PatchSystems)

---

### Post by mick171 on 2011-07-24
Thanks for that. I'm still going to need assistance. 
So I need to download the diff file.
This url [http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/gregkh/usb-2.6.git;a=summary)
suggests the url to download the file as 

[http://git.kernel.org/pub/scm/linux/kernel/git/gregkh/usb-2.6.git](http://git.kernel.org/pub/scm/linux/kernel/git/gregkh/usb-2.6.git)

but this doesn't exist.. which means I'm doing something wrong.

Please advise.

---

