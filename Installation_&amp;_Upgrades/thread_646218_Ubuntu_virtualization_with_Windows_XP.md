---
title: "Ubuntu virtualization with Windows XP"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by mukta on 2007-12-20
hello :

          I would like to run Ubuntu on my PC. However I need Windows XP for a little use.
         Could we have Virtualization and run XP as a guest OS.

        Could you guide us through the steps.

        Thank you and Regards,
        Srinivas

---

### Post by eternicode on 2007-12-21
I remember trying this....never did get it to work.

Anyway, if you insist on trying, [Venture Cake]("http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/") claims that they can get you up and running in 15min.  I also tried a guide on [advicesource.com]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html"), but neither guide helped me.  Perhaps you'll have better luck.

---

### Post by chewearn on 2007-12-21
If reusing existing XP installation is not a requirement (i.e. are able to install a new XP as guess OS; then you have more options that just VMWare.

Here is one which I am familiar with:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by mukta on 2007-12-21
Thank you to Eternicode and Astalavista.

Do we require special hardware for this. Do we need Intel IVT or AMD V processors with suitable
motherboards, or will all of virtualization be taken care of in software.

Thank you and Regards,
Srinivas

---

### Post by chewearn on 2007-12-21
> **mukta said:**
> Thank you to Eternicode and Astalavista.

Do we require special hardware for this. Do we need Intel IVT or AMD V processors with suitable
motherboards, or will all of virtualization be taken care of in software.

Thank you and Regards,
Srinivas

First let me repeat I'm only familiar with KVM; so I can only tell you about that.

There are other virtualization, like VirtualBox, Zen, etc.  You might find the others better or easier to use, etc.

But to answer your question, KVM needs to have Intel or AMD hardware virtualization supported.  Most Intel / AMD chips sold in last few years already have this available.  If you have an older hardware without hardware virtualization, KVM will drops back to QEMU, which is a software emulation (i.e. it will run very slow).

---

### Post by snkmad on 2007-12-21
I have installed WinXP inside my Ubuntu 7.10 using VirtualBox.
I just followed this [Guide]("http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html").
Its really simple, fast, and VirtualBox is free.

---

### Post by mukta on 2007-12-21
Thank you. I will try.

Srinivas

---

