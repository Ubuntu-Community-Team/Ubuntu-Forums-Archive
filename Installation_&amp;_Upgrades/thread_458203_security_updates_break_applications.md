---
title: "security updates break applications"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by eg-maverick on 2007-05-29
Why do security updates break applications, causing a reload of headers and apps? Specifically, when I installed the pushed security updates, my vmplayer stopped working. This is because the security update did something to the kernel. But it didn't do enough. Not only did I have to reinstall the application, I had to re-install C header files so that I could reinstall vmplayer. I believe that anyone using linux/ubuntu in a business environment needs to have a virtual machine to run business apps that aren't available and interoperable on linux. Why should I have to reinstall it every time there is a kernel security update? At least include the header files with the update.
Craig

---

### Post by jamesjtucker on 2007-05-29
Craig,
  I use vmware at work, and am familar with this issue (although i dont use the player, this should be somewhat similar)
   When you upgrade the kernel (which is most likely what happened), you will need to rebuild the kernel modules for Vmware and some other applications that build custom kernel modules. Vmware uses this custom generated kernel module to interface with the virtual machines. (im sure someone can provide a more technical explanation, if needed). 
   After a kernel update, you will need to build a new kernel module that works with the new kernel, and in order to do that, you will need the headers, but those *should*  update with the kernel install. If not its a simple one liner to install them. 
   For me, after each kernel update, i need to run /usr/bin/vmware-config.pl which will create and load the new module, and then its done, no need to reinstall at all. 
   In a typical business environment, kernel updates are done very rarely because of situations like this, thats why my IT guys here only support RedHat officially, but im impatient and cant stand redhat anyway :)

   Does that help at all? I cant tell if you were asking a question or just blowing off some steam...

---

### Post by jamesjtucker on 2007-05-29
a few quick notes: 
I checked the vmware player docs, and it does use the same config script to build the kernel modules. 
[http://www.vmware.com/pdf/vmware_player200.pdf](http://www.vmware.com/pdf/vmware_player200.pdf)   Page 11.

  The reason you need to build the kernel module, is because Ubuntu is not officially supported (but i think that may have changed with the latest vmware release.. i need to check) The officially supported distros have built in kernel modules that plug and play.

---

### Post by LarsBjerregaard on 2007-05-29
Sounds like you've been bitten by this: [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662) like a lot of other people. Please consider my suggestion on: [http://ubuntuforums.org/showpost.php...&postcount=194](http://ubuntuforums.org/showpost.php...&postcount=194)

---

