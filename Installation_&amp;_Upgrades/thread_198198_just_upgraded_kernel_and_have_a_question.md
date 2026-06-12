---
title: "just upgraded kernel and have a question"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by revilot on 2006-06-16
I just installed dapper today (noob) and upgraded the kernel like the udate notifier suggested along with about 80 some other updates.  It seemed to go ok (other than killing my wireless, but I just performed the same operation I did earlier today to get that working again).  The only thing is when I rebooted i noticed it now has two seperate kernels listed in grub.  Why does it do that?  Can I, and how do I, get rid of the older kernel?

Also, when I booted up my quit button and another icon had moved rom their original spot in my toolbar.  I can't get the quit button to go back in the very top right corner anymore.

Thanks for any help.

---

### Post by TwistesdTexan on 2006-06-16
The way ubuntu boot to a grub is so you can choose which kernel you wish to boot with. It is always good to keep the 386 kernel to boot to in case something happen to the 686 or other kernel. As for the quit button? I must be using a different ubuntu format. Perhaps some one else is using either kubuntu or edubuntu can help you.

---

### Post by revilot on 2006-06-16
[QUOTE=TwistesdTexan]The way ubuntu boot to a grub is so you can choose which kernel you wish to boot with. It is always good to keep the 386 kernel to boot to in case something happen to the 686 or other kernel. As for the quit button? I must be using a different ubuntu format. Perhaps some one else is using either kubuntu or edubuntu can help you.[/QUOTE]

its not a 686 and 386 version im talking about, its two completely different versions of the kernel.  .23 and .25 are in my list. 

Also, I'm using regular ubuntu.  I'm talking about the log off button.

---

### Post by Nonno Bassotto on 2006-06-16
As for the old kernel, you can remove, but I wouldn't. I'd wait some time to be really sure that the new kernel works well for me and only then remove it. This is the reason it doesn't remove the old kernel: you may be happy with the old kernel and have bugs with the new. It can be removed using Synaptic, like every other program. Just be sure:
1) to remove only the old version
2) not to remove the dumb packages (those without version number), as they are there to make sure you will get kernel updates.

For the button, I assume you use gnome. Right-clicking an object on the panel should allow you to move it. If you are not able to move it past a fixed object, right-click on the fixed object and unselect "Block on the panel".

---

### Post by revilot on 2006-06-16
[QUOTE=Nonno Bassotto]As for the old kernel, you can remove, but I wouldn't. I'd wait some time to be really sure that the new kernel works well for me and only then remove it. This is the reason it doesn't remove the old kernel: you may be happy with the old kernel and have bugs with the new. It can be removed using Synaptic, like every other program. Just be sure:
1) to remove only the old version
2) not to remove the dumb packages (those without version number), as they are there to make sure you will get kernel updates.

For the button, I assume you use gnome. Right-clicking an object on the panel should allow you to move it. If you are not able to move it past a fixed object, right-click on the fixed object and unselect "Block on the panel".[/QUOTE]


Thanks for your help. I'm going to take your advice about leaving alone for a while, but for future reference, I can't seem to find where to locate the kernels in synaptic package manager.  Probably right in front of my face, but I'm not having any luck.  How could I locate them?  Thanks again.

---

### Post by Nonno Bassotto on 2006-06-17
The kernel packages are (I assume you use 386)
linux-image-2.6.15-23-386
linux-restricted-modules-2.6.15-23-386

There are similarly named packages without version number: these depend on the latest kernel version, and so they should not be removed, as they are needed to ensure you get kernel upgrades.

---

