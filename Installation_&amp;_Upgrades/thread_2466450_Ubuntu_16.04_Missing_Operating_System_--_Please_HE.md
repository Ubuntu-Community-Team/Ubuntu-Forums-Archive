---
title: "Ubuntu 16.04 Missing Operating System -- Please HELP"
date: 2021-08-27
forum: Installation &amp; Upgrades
---

### Post by ramster2 on 2021-08-27
Hello,

I am using Ubuntu 16.04. I was using the computer normally, just like any other day, until today when I turn on my computer, it says Missing Operating System.
I do not know what went wrong and how it got wrong. I don't have any other OS installed (most problem I found in forums is that people have 2 OSes in their machine).
Well, I only have 1, and now it won't boot. How do I fix this?  & If there is no way to fix it, please inform me the best way to retrieve my files in the computer.

If possible, please provide step-by-step instruction, because I am not good at Linux.

My PC is Asrock Deskmini 110W, with intel i3 8300.
Thank you

---

### Post by Impavidus on 2021-08-28
Ubuntu 16.04 has been unsupported since April 2021, so we can't help you with that. (You may have signed up for Canonical's Extended Security Maintenance, in which case it isn't completely unsupported.) We can help you with saving your data and getting a supported release of Ubuntu.

In any case, you need a live disk to gain access to your harddrive. If you want to rescue your current system, best to use a live disk of that release of Ubuntu, but I suggest you just wipe it and install the latest LTS release instead, possibly a lighter flavour. Have you got backups of your important files? If not, you've just learned a lesson. With a live disk you should be able to get your files off the harddrive and on an external drive, provided your harddrive isn't broken.

---

### Post by monkeybrain20122 on 2021-08-28
While it is true that 16.04 is unsupported but it is a cause of concern that your OS suddenly disappears, it is certainly odd, maybe your hd has died.

---

### Post by yancek on 2021-08-28
That is likely a hardware failure of some kind.  Had the same error on a 1 month old laptop and it was a failure of a connector to the drive on the motherboard.  Not saying that is your problem but I expect it is similar, drive failure, connector problem or similar so I would follow the suggestions in post 2 and get a live usb of Ubuntu or similar and backup your data as a first step.

---

### Post by grahammechanical on 2021-08-28
Enter into the motherboard's UEFI set up utility and check to see if it has a hard drive listed to boot from. Some machines have a LED that indicates hard drive activity. Does your machine have such a indicator? Does it indicate hard drive activity?

If you still have the USB or DVD of 16.04 that you installed from you can try booting from that. If successful, you can use the Disks utility to check hard disc status and run diagnostic tests. And Run GParted and see what it says about your drive partitions.

Regards

---

### Post by ramster2 on 2021-09-27
It just so happen that I have a faulty hard drive. So it was a hardware problem. Thanks for all your help.

---

