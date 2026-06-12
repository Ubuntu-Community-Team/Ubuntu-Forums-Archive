---
title: "I can't run a .run file"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by eram on 2008-07-26
Ok, So I have a problem.
I downloaded a .run file.
Can anyone please tell me how to install it?
Thanks!

---

### Post by Chris11 on 2008-07-26
Might this help you?

[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")

---

### Post by eram on 2008-07-26
I tried that, I get an error saying that it must run it as root.
How do I do that?
Thanks!

---

### Post by oldos2er on 2008-07-26
sudo ./filename.run

---

### Post by eram on 2008-07-26
Ok, tried that, I received this error message: "You appear to be running an X server; please exit X before installing." How do I do that?
Thanks!

---

### Post by perlluver on 2008-07-26
> **eram said:**
> Ok, tried that, I received this error message: "You appear to be running an X server; please exit X before installing." How do I do that?
Thanks!

What .run package are you trying to run?

---

### Post by oldos2er on 2008-07-26
> **eram said:**
> Ok, tried that, I received this error message: "You appear to be running an X server; please exit X before installing." How do I do that?
Thanks!

 What exactly is this *run file? Video driver?

 One way to do this is to reboot, and select a "recovery mode" kernel from grub. No X server is started, and you'll be logged in as root, so you can skip the "sudo" portion of the command I gave you earlier. You may need to "cd" to the directory where the *run file is located. 

Another way to stop X is to run the command "sudo /etc/init.d/gdm stop". Run your *run file, then to restart X type "sudo /etc/init.d/gdm start".

---

### Post by eram on 2008-07-26
> **perlluver said:**
> What .run package are you trying to run?

NVIDIA Graphics Card Driver.

---

### Post by jolx on 2008-07-26
have a look at [this]("http://ubuntuforums.org/showpost.php?p=5327502&postcount=72")

---

### Post by Growbag on 2008-07-26
Before doing that you will have to install build-essential and the kernel headers for your kernel.

Plus be aware that each time a kernel update comes out you will have to recompile the Nvidia module (ie run the file again) or you won't have a desktop!

Seeing as you are rather new at this, it might be best to use the standard Ubuntu restricted driver instead!

---

### Post by oldos2er on 2008-07-26
eram, you should have a look at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by eram on 2008-07-26
> **oldos2er said:**
> eram, you should have a look at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Yes, looks great! I will try that. But first. I messed up my system, so I need to undo the changes I did first.
Here's what I did: After installing the Libc Development Package, I did ```
sudo /etc/init.d/gdm stop
``` Then I installed the new NVIDIA driver, every thing went fine, it said it had finished and told me to restart  the computer. I did so, after selecting the kernel in the Grub loader, the loading started, but the login screen never came, the screen just stayed black.
I'd appreciate it if any one knows any thing that I can do to undo this.
Thanks!

---

### Post by eram on 2008-08-16
never mind!
I fixed it and now I've got a great screen resolution!

---

