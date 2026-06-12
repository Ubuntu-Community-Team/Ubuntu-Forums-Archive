---
title: "Freeze on Install"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by soaring747 on 2007-09-16
I wasn't sure which one to post this in, since it probably covers about three different subject areas.

I have an ACER Aspiron 5050 with a Turion-64 MK-38 processor. The 7.04  live CD froze after I selected "Install Ubuntu". I also tried it with safe graphics, that didn't solve the problem.

After checking the hardware compatibility list, it seems that Ubuntu should support the hardware. I am certain this is a processor problem since it froze immediately after kernel initiation. That, and google returns numerous forum posts with compatibility problems involving the Turion 64 and Ubuntu. (All of which I found didn't apply to my case since the error occurred elsewhere in the installation process.)

Is there a special boot command I should try?

---

### Post by Pumalite on 2007-09-16
Here is a collection you could try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

---

### Post by soaring747 on 2007-09-16
That helps with the 'how to edit' bit.

What specifically should I edit? How can I make the kernel not hang?

---

### Post by Pumalite on 2007-09-16
At boot you hit 'e' for edit, and there you enter your parameter.

---

