---
title: "Xen Ubuntu &amp; Windows"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Vati-Khan on 2006-07-25
my current desktop needs to be replaced, so I have some thoughts about configuration and hardware investment

While I use Ubuntu 90% of the time I sometimes need Windows. Until now I used VMWare to solve this issue, but performance was quite poor when working for a long time (especially file IO) and I couldn't play because of poor graphics. 

So my status quo is

Ubuntu 6.06
Windows XP VMWare Image
Windows XP Partition

So after studying Xen 3 for a while I found out that I can use Windows XP with it and that I can dedicate a physical partition/hdd to the VM instead of an image file. 

So finally the question:
**Can I install Windows like a normal install and choose to start it from BIOS or via XEN under Linux???** 
Only if there is hope to make it work I will give it a try or else it would only be time wasted

I'd appreciate any help or pointers to where I can find in depth info that could help

VK

---

### Post by A-star on 2006-07-27
good question,
I would like to know that also.

---

### Post by nihilocrat on 2006-07-28
Since Xen is a "hypervisor", it requires kernels specially modified to use it and thus give the humongous performance boost Xen provides. This means you can't run unmodified versions of OSes. However, newer multicore processors have the ability to do this with Xen. According to [this HOWTO](http://www.xensource.com/files/xen_install_windows.pdf), you need a "VT-enabled Intel system or an AMD-V enabled system". I have no idea which specific processors these are, but they are probably very, very modern (made within the past year).

---

### Post by Vati-Khan on 2006-07-28
that I know thanks

the real question is is it possible to boot the same Windows-System form Xen as Guest and directly from bios. If not - I'm not willing to spend extra money for an Intel 9xx or Athlon X2 CPU

leaving for the weekend,
wish you have nice days yourselves

cu monday

---

### Post by umonkey on 2006-07-29
I just ordered a new laptop which I would like to use for running both Windows and Linux software. I really hate using dual boot and since my laptop will have a cpu with Intel's VT capability I would like to use a VMM. 

I would also be interested in knowing the answer to Vati-Khan's question. Being able to use the same installation to boot from bios or under Xen would be ideal.

---

