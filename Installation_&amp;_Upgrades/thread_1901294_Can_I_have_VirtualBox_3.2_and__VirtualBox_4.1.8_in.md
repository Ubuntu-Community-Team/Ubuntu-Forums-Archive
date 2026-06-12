---
title: "Can I have VirtualBox 3.2 and  VirtualBox 4.1.8 install?"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by StutteringJohnSmith on 2011-12-28
Can I have VirtualBox 3.2 and  VirtualBox 4.1.8 install?

I am using ubuntu 10.4 and I have VirtualBox 4.1.8 installed and running a number of guest os but I been trying to get a guest working that everyone is telling me I need version VirtualBox 3.2.  Can someone please tell me if I can have VirtualBox 3.2 and VirtualBox 4.1.8 both installed at the same time and how do I do it!

---

### Post by hsoulen on 2011-12-28
Interesting question...

I am not 100% positive but I would say "No".

The reason is the kernel driver, even if you use a tarball instead of a deb you are going to have to load the kernel driver for that version of VirtualBox, unless you unload/load the version needed at run-time I do not see how this is possible.

That said, I am not a Vbox expert so don't take my word as gospel.

Cheers,

Hank

---

### Post by kalfusisagod on 2011-12-28
I would post this is the Ubuntu Virtualization sub forum. Also virtualbox.org has a good forum. But I'm going with a no on this one. Maybe you can run a virtual box within a virtual box though.

---

### Post by ubix on 2011-12-28
> **StutteringJohnSmith said:**
> Can I have VirtualBox 3.2 and  VirtualBox 4.1.8 install?No, remove old (3.2) VB first with Synaptic Package Manager. Then install  4.1.8. It should pick up all your data files and setups from earlier installation.

Just make sure you shut down rather than save all the virtual machines you have in your VirtualBox. This means you need to start all your VMs and make sure you then shut them all down by selecting **Send the shut down signal**. Do not **Save the machine state** or even worse **Power down**.

---

### Post by CharlesA on 2011-12-28
> **ubix said:**
> No, remove old (3.2) VB first with Synaptic Package Manager. Then install  4.1.8. It should pick up all your data files and setups from earlier installation.
This.

Both versions will conflict with each other and as such cannot be installed at the same time.

---

### Post by ubix on 2011-12-28
***StutteringJohnSmith***, I have just realized that you may have to do some manual tweaking during installation such as specifying your data files and snapshot folders if you had them in non-standard places to get your data files to be recognized, since I am not sure pre 4.* VB releases had the ~/.VirtualBox folder or if the removal of 3.* VB removes these folders too.

The control files for VirtualBox are now in a each guests folder and the VB control file is in your ~/.VirtualBox file on version => 4.*. These files do not get removed in pos-3.* versions and should be picked up by VirtualBox during installation.

If you want to be absolutely sure ask for help on [VirtualBox](https://forums.virtualbox.org/index.php) dedicated forum. 

Regardless, do not forget to shut down rather than save all your VMs, before removing and reinstalling the VirtualBox software.

---

