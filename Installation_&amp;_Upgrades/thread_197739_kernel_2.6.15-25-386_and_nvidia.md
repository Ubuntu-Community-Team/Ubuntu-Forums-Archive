---
title: "kernel 2.6.15-25-386 and nvidia"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by infoseeker on 2006-06-16
I have recently upgraded to kernel 2.6.15-25-386, and the problem is that I cannot get X configured correctly. I have a FX5200 Graphics card.

The previous kernel (2.6.15-23-386) works normally.

I have tried 'sudo dpkg-reconfigure xserver-xorg-core' and/or 'sudo nvidia-xconfig' and neither gets X configured correctly.

Have I missed something here ?

---

### Post by frodon on 2006-06-16
You should read the tseliot's guide : [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by mozetti on 2006-06-17
Definitely use the guide linked to above, and pay particular attention to the 'linux restricted modules' part. Each kernel has a diffent set, and they are needed for the driver to work.

---

### Post by infoseeker on 2006-06-18
> You should read the tseliot's guide : [http://doc.gwos.org/index.php/Latest...NEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest...NEL_IS_UPDATED)

Worked perfectly BTW :)

---

### Post by FredB on 2006-06-19
What is strange that when there is a kernel update, every time apt-get tells me it will install the restricted module packages which is up-to-date with kernel version.

But why not on some people's machine ?!

---

### Post by tseliot on 2006-06-19
[QUOTE=FredB]What is strange that when there is a kernel update, every time apt-get tells me it will install the restricted module packages which is up-to-date with kernel version.

But why not on some people's machine ?![/QUOTE]
Because you have the dummy package (e.g. linux-386) which does it for you.

---

### Post by FredB on 2006-06-19
[QUOTE=tseliot]Because you have the dummy package (e.g. linux-386) which does it for you.[/QUOTE]

Ok. So, I am using the simplest - and painless - way to upgrade.

Thanks for the info. I was worried to be one of those who don't have upgrade problems and I felt a little alone.\\:D/

---

