---
title: "additions greyed out"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by irvdk on 2007-09-13
I installed Microsoft virtual machine2007 to go along with Vista business edition.  It installed just fine and then I started to install Feisty Fawn to run on the virtual machine.  It starts to install and then tells me to install the additions.  I go to Action> and the update additions is grayed out.

Could someone help me??

Thanks,
Irv

---

### Post by aquavitae on 2007-09-13
I had the same problem with.... MS virrtual PC I think - one of the MS things anyway.  I think the problem is the updates only work on a MS guest - i.e. Microsoft's way of forcing you to use windows inside a vm.  I'd suggest you try [virtualbox]("http://www.virtualbox.org") instead.  Its opensource and has a really easy interface.  Got it working here with no problems.

---

### Post by jfinkels on 2007-09-13
> **irvdk said:**
> I installed Microsoft virtual machine2007 to go along with Vista business edition.  It installed just fine and then I started to install Feisty Fawn to run on the virtual machine.  It starts to install and then tells me to install the additions.  I go to Action> and the update additions is grayed out.

Could someone help me??

Thanks,
Irv

I'm not certain because I have not used Microsoft Virtual PC that much, but I believe choosing the "Actions > Install additions" button actually mounts a virtual disc image and autoruns some goofy Windows executables that let you move your mouse in and out of the window without releasing it, and let you drag and drop files from the host system to the guest system to copy them, and other stuff like that. Virtual PC probably doesn't give you the option to mount the virtual disc because you do not have a Windows guest operating system, and therefore would not be able to run the executable files on their goofy virtual disc image.

---

### Post by jfinkels on 2007-09-13
> **aquavitae said:**
> I had the same problem with.... MS virrtual PC I think - one of the MS things anyway.  I think the problem is the updates only work on a MS guest - i.e. Microsoft's way of forcing you to use windows inside a vm.  I'd suggest you try [virtualbox]("http://www.virtualbox.org") instead.  Its opensource and has a really easy interface.  Got it working here with no problems.

Yup, or try VMWare. Open Source software is better and cheaper than Microsoft's proprietary software.

---

### Post by aquavitae on 2007-09-13
> **jfinkels said:**
> Yup, or try VMWare. Open Source software is better and cheaper than Microsoft's proprietary software.Isn't vwmare also MS software...?  Or am I just confused?

---

### Post by irvdk on 2007-09-13
Microsoft just made it free:
[http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx)

---

### Post by jfinkels on 2007-09-13
> **aquavitae said:**
> Isn't vwmare also MS software...?  Or am I just confused?

I think you are confused. VMWare is...VMWare, Inc. software. [http://en.wikipedia.org/wiki/Vmware](http://en.wikipedia.org/wiki/Vmware)

---

