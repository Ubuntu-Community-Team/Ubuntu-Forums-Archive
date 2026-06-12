---
title: "Virtualization of windows under ubuntu: How with OEM CD?"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by nikdo on 2007-05-11
Hello,

I have a gateway computer that came preinstalled with windows. This means that although I have the cd with valid key, I can only 'restore' from it.

I am trying to do virtualization (qemu, VirtualBox, VMWare - hasn't decided which one yet, but leaning towards qemu) under ubuntu. However for this apparently I need a 'real' windows cd.

It seems that manufacturers pulled a fast one on consumers: you get a windows cd from which you cannot do normal install. Thus, the virtualization software will not be able to install from this type of cd.

Any advice how to go about this? I have read some stories that one has to go and get 'regular' boot sector for win xp, burn this onto a new cd and add the rest of the restore cd (i386 folder?). Possibly hacking some keys and other things.

Is there a simpler way? If not, what is the procedure then?

Thanks a million!

---

### Post by nab on 2007-05-11
Hi Nikdo,

For VM-Player there is VMware Converter, which converts your installed system to virtual machines. [http://www.vmware.com/products/converter/]("http://www.vmware.com/products/converter/")

Well I never tried this myself and I don't think this is elegant ...

Hope this helps,
Nikolaus

---

### Post by nikdo on 2007-05-11
I believe I heard of this solution, but not too keen on going that way as my current windows partition o nthe drive is bloated and a little messed up, so I rather do a clean re-install.

Any other ideas on how to make that non-oem cd out of the oem one?

thanks a lot guys / gals!

---

### Post by kyphi on 2007-05-11
I run VirtualBox in Ubuntu with XP installed from an OEM disk without any problems.

Even though your computer came with Windows preinstalled, you must be able to install from your OEM disk.
What happens if your Windows system crashes beyond repair and you have to reformat and reinstall?  That is what you OEM disk is for.

---

### Post by jbro on 2007-05-11
> **nab said:**
> For VM-Player there is VMware Converter, which converts your installed system to virtual machines. [http://www.vmware.com/products/converter/]("http://www.vmware.com/products/converter/")

Well I never tried this myself and I don't think this is elegant ...
You are right, it is not elegant. I have a ThinkPad and seven system restore CDs. First, I had to back up my data from my previous Windows installation since the installation itself was having some stability problems. Then I nuked the old windows, did a system restore, used VMWare Converter to make a virtual machine and then ran this. I certainly would rather have created a VM and done an install, but with the IBM system restore disks, this is not possible. The lack of an install CD also made it impossible to use VirtualBox. I hate it when vendors don't just give you a Windows install CD.

Now, with an OEM CD, I don't see why you can't do the install. It may require you to activate the software for the virtual machine, but that shouldn't be a problem. In fact, I had to call Microsoft to activate my VM Windows the first time I ran it. I don't know if the service rep understood what I was saying, but she gave me a new  install code nonetheless.

Good luck and regards,
jbro

---

