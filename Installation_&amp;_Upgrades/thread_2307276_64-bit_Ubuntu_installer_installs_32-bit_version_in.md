---
title: "64-bit Ubuntu installer installs 32-bit version instead!"
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by thomas82 on 2015-12-23
Hello Forum,

As the title states, I'm trying to install 64-bit Ubuntu on my machine, and even after doing everything correctly (or so I think), the 32-bit version gets installed instead.

Here's an exact explanation of what I've been doing:

1) In Windows 7 64-bit (already installed), I download the most recent version of Ubuntu 64-bit from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  -- the drop down menu on the right is selected for 64-bit.

2) I then use the Universal USB Installer to create a bootable USB out of an external hard drive, selecting the 64-bit version of Ubuntu I've just downloaded as the ISO.

3) I power off the computer, boot from the external hard drive, and follow all of the Ubuntu installation instructions.

4) Checking the Ubuntu install version shows that it is a 32-bit install, NOT a 64-bit install.

Proof:

[IMG]http://i.imgur.com/61CjiQR.png[/IMG]

Furthermore, I'm unable to install any 64-bit software on Ubuntu, so I know it's not installing correctly.

I thought maybe the link to 64-bit Ubuntu 14 was wrong, so I tried downloading an older Ubuntu 12 64-bit version instead, but that did not work either.

Any ideas?

Thanks!

---

### Post by deadflowr on 2015-12-23
What's the full name of the iso file you have.
Does it end with amd64 or i386?

---

### Post by thomas82 on 2015-12-23
amd64

Full file name: ubuntu-14.04.3-desktop-amd64

---

### Post by thomas82 on 2015-12-23
Also, I should add that after booting from the external HDD if I opt to "try Ubuntu" instead of install, it looks like the trial version is a 64-bit version of the OS.

---

### Post by sudodus on 2015-12-23
Maybe there is a temporary confusion at the link you have used. The following link should bring you the correct iso file(s).

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

You should check it with ***md5sum***, see [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ajgreeny on 2015-12-23
How are you managing to get an external HDD to boot to a  live OS?
I think that it is impossible to run a live OS from a normal hard drive, and that it is only possible from a USB or DVD.

Have I misunderstood what disk you really have or what you are doing?

---

### Post by deadflowr on 2015-12-23
> **ajgreeny said:**
> How are you managing to get an external HDD to boot to a  live OS?
I think that it is impossible to run a live OS from a normal hard drive, and that it is only possible from a USB or DVD.

Have I misunderstood what disk you really have or what you are doing?

Out of the box I don't think you can install a live os from a hard drive.
But you can add an isofile to the GRUB bootloader.
Of course this requires GRUB, which you won't have in Windows.

Alas, though, I think the odd part of it all is
> Also, I should add that after booting from the external HDD if I opt to "try Ubuntu" instead of install, it looks like the trial version is a 64-bit version of the OS.
I can see it being one or the other, but not both, The iso image would be a tad bigger in size.
Definitely not normal, and I haven't seen a single user report such behavior before...

---

### Post by grahammechanical on 2015-12-23
Please run this command and tell us what it says.

```
uname -a
```

This is what I get.

> graham@sdb7-Dev:~$ uname -a
Linux sdb7-Dev 4.3.0-4-generic #13-Ubuntu SMP Fri Dec 11 14:18:44 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu does not have a combination ISO image that will install either a 32 bit or a 64 bit version. It could be that the label on the Details page is some kind of a misprint. And you are the first to notice it. Or that some internal label in the CPU that identifies its architecture is inaccurate.

Regards.

---

