---
title: "maverick update kernel 2.6.35-32"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2012-01-20
Hello,

today I received a message that my kernel is about to be updated. My question is:
how can I find out about the changes and their influence on my perfectly stable system? I do know that updates might cause an issue, yet, their philosophy is to make things better. How I can verify that these changes are going to make better my life?

Thank you,
Regards!

---

### Post by snowpine on 2012-01-20
The site you're looking for is [http://packages.ubuntu.com](http://packages.ubuntu.com)

specifically: [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.35.32.41/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.35.32.41/changelog)

You'll see the most recent change is marked "urgency: low" and was an "ABI bump."
[http://en.wikipedia.org/wiki/Application_binary_interface](http://en.wikipedia.org/wiki/Application_binary_interface)

If you are a real Linux nerd then you can study the source code in great detail and understand the exact changes.

Generally speaking, kernel updates are very safe, because if there's a problem, you can simply choose the old kernel in your GRUB boot menu. :)

---

### Post by Claus7 on 2012-01-20
Hello,

thanks a lot for your detailed answer!
One more that might come to mind is: if I have tampered for example with my network, how this kernel updates will 'tolerate' the changes I have made?

Regards!

---

### Post by SeijiSensei on 2012-01-21
Pretty much the only aspect of kernel upgrades that affect networking are the device drivers.  Usually these changes are for the better, especially when it comes to wifi devices.

I'm not sure what you mean by "tampering" with your network, but I doubt a kernel upgrade will matter.  As snowpine says, if there's a problem you can boot the prior kernel from grub.

A more complicated issue arises when you use software that needs to build compatible kernel modules for each release.  For me, both VirtualBox and the NVIDIA driver qualifies.  You need to have dkms and build-essential installed in these cases so that the installer can compile and install the required kernel modules.

Edit:  I just upgraded to the -32 kernel without incident.

---

### Post by Claus7 on 2012-01-21
Hello,

thanks... a lot!

your answers cleared the things to me. Just to mention by tampering I meant:
cat /etc/network/interfaces

and changing some things about the interfaces file, in order to improve my network. Yet, in the end, I left it unaltered. 

Thank you,
Regards!

---

