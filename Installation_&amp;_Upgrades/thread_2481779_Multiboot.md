---
title: "Multiboot"
date: 2022-12-08
forum: Installation &amp; Upgrades
---

### Post by ajithrock on 2022-12-08
Hi I need to install Ubuntu 22.04, Zorin OS and manjaro along with my windows 10. I need a proper guide to install above my three Linux os.
I have already installed windows 10 in my machine. Is there any order to install above three os?

---

### Post by oldfred on 2022-12-08
Did you install in UEFI boot mode to gpt partitioned drive?
Last install will be the grub that is in control. But major grub updates to other installs, may change boot order and that that install first in boot order.
You just have to manage grub. 
What install will be your default? It probably should be your last install.

You may want to have a separate data partition or two, so you can share data. Do not try to share any system partitions other than ESP.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by TheFu on 2022-12-08
> **ajithrock said:**
> Hi I need to install Ubuntu 22.04, Zorin OS and manjaro along with my windows 10. I need a proper guide to install above my three Linux os.
I have already installed windows 10 in my machine. Is there any order to install above three os?

Don't multi-boot. Use virtual machines.  Problem solved.  

Plus you can run all three concurrently, not just 1 at a time.  Having multiple systems booting is a risk and bad things can happen.  Add in that MSFT thinks they are the only OS in the world, and bad things are caused by MSFT breaking the other OS installations.  It doesn't happen every month, but if history is correct, you'll have a bad day about once a year.

To run multiple OSes, you'll need a hypervisor.  If you keep Windows on the hardware, then the choices come down to 
a) Oracle VirtualBox - this is a free option, but has some license restrictions.
b) VMware Player - this is a free option, but has some limitations.
c) VMware Workstation - this is non-free and you can call someone at VMware support to complain.  VMware tends to take longer to support new Linux releases, so beware.
d) Whatever MSFT is selling.  They used to give away their hypervisor. It was included in some versions of MS-Vista and later.  It may be a "Home" or "Professional" thing. I don't keep up with what MSFT does. It could still be free in Win10 Professional. IDK.

There are some other, less popular options for Windows too.  Now, if you run Linux on the hardware, then you can use a, b, c, and a number of other hypervisors, which are free and built into the Linux OS.  XenNG and KVM+QEMU are extremely popular enterprise-level Linux hypervisors.  Redhat, Amazon, Oracle (their linux servers) and nearly every VPS in the world uses KVM.

For beginners with virtual machines, probably the easiest to use and understand is Virtualbox.  You'll find lots of people use it on Linux and on Windows VM hosts.  [https://www.virtualbox.org/](https://www.virtualbox.org/)  That would be my recommendation for anyone with the goal you have.

---

### Post by Dennis N on 2022-12-09
Just a tip on multibooting the distros you named:
If you expect to boot Manjaro from Ubuntu or Zorins grub menu, it won't work. You will need to either fix the Manjaro menu entry, or else use the grub chainloader command.

---

### Post by Dennis N on 2022-12-09
Just a tip on multibooting the distros you named:
If you expect to boot Manjaro from Ubuntu or Zorins grub menu, it won't work. You will need to either fix the Manjaro menu entry, or else use the grub chainloader command.

---

### Post by mIk3_08 on 2022-12-12
> **ajithrock said:**
> Hi I need to install Ubuntu 22.04, Zorin OS and manjaro along with my windows 10. I need a proper guide to install above my three Linux os.
I have already installed windows 10 in my machine. Is there any order to install above three os? It would be more look nicer if you will setup a bootloader for this. There are lots of know bootloader on the web. Here are some of the list refind, easybcd, clover efi bootloader, opencore, refit and etc. Good Luck. Regards and cheers

---

