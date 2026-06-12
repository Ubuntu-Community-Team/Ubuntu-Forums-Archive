---
title: "[SOLVED] Installation of Windows in addition to UBUNTU"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-07-23
I am a complete newbie at this - so please understand if my question appears stupid !!. I am 100 % Ubuntu, my "C" drive is 250 GB and totally committed to UBUNTU. However I have the odd situation where I need to open a Windows application. I have tried WINE but it is not very reliable. My question is :- I have the Windows bootable CD - how can I install this on to my machine to work with UBUNTU,as a second boot, and NOT disturb my UBUNTU operation.:confused:

---

### Post by LaRoza on 2008-07-23
> **Dyffo said:**
> I am a complete newbie at this - so please understand if my question appears stupid !!. I am 100 % Ubuntu, my "C" drive is 250 GB and totally committed to UBUNTU. However I have the odd situation where I need to open a Windows application. I have tried WINE but it is not very reliable. My question is :- I have the Windows bootable CD - how can I install this on to my machine to work with UBUNTU,as a second boot, and NOT disturb my UBUNTU operation.:confused:

A few clarifications:

[list]
[*] If you are using Ubuntu only, there is no "C:" drive. That is a pre DOS naming convention kept for backward compatibility.
[*] You can't easily install Windows next to Ubuntu.
[/list]

The best thing, if you have the hardware for it, would be to run Windows in a Virtual Machine, that way you could use it while you are in Ubuntu without having to deal with partitioning.

---

### Post by Dyffo on 2008-07-23
> **LaRoza said:**
> A few clarifications:

[list]
[*] If you are using Ubuntu only, there is no "C:" drive. That is a pre DOS naming convention kept for backward compatibility.
[*] You can't easily install Windows next to Ubuntu.
[/list]

The best thing, if you have the hardware for it, would be to run Windows in a Virtual Machine, that way you could use it while you are in Ubuntu without having to deal with partitioning.
Running Windows  in a Virtual sounds to be just fine - question is - how do I do this ?? could you guide me through the procedure.

---

### Post by Sef on 2008-07-23
> Running Windows in a Virtual sounds to be just fine - question is - how do I do this ?? could you guide me through the procedure.


[Virtualization]("https://help.ubuntu.com/8.04/serverguide/C/libvirt.html#libvirt-installation") check:

> libvirt

The libvirt library is used to interface with different virtualization technologies. Before getting started with libvirt it is best to make sure your hardware supports the necessary virtualization extensions for KVM. Enter the following from a terminal prompt:

 egrep '(vmx|svm)' /proc/cpuinfo

If nothing is printed, it means that your cpu does not support hardware virtualization.


If something is printed, then click [here]("https://help.ubuntu.com/8.04/serverguide/C/libvirt.html#libvirt-installation").

---

### Post by Dyffo on 2008-07-23
ALL DONE - Works really well - SO FAR !!!!! Thanks for your help

---

