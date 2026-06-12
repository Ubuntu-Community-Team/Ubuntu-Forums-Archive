---
title: "VMWare 6.5 Kubuntu Intrepid doesn't capture mouse"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by unclecameron on 2008-10-25
I've been running Kubuntu Hardy on various VM's on VMWare Workstation 6.5 running on and Intrepid host, but when I try to upgrade my guest Kubuntu's it horks the mouse and keyboard so bad that I can't really use them.

This occurs after I reboot following a successfull dist-upgrade inside an existing hardy VM install. It also occurs on ubiquity if I simply boot the VM from the rc .iso. The OS "thinks" the mouse is about 200px straight up and 50px to the left of where it actually is, and the keymap won't let you tab through ubiquity and just use "enter" to get as far as you can, does anyone have any ideas? I can't use system wide mouse modifiers, because then the other VM's wouldn't work right.

---

### Post by Anicka on 2008-10-28
I'm bumping this post out of purely selfish reasons as I have exactly the same problem with upgrading my Ubuntu. I was wondering if it had anything to do with the new handeling of input devices (HAL instead of xorg)? Anyway the mouse is not clicking where the cursor is.

If I do a clean install, vmware-tools doesn't compile the vmsocks-module and the hgfs-module refuses to start even though it compiles without errors. However, the mouse clicks where the cursor is, but it doesn't get captured by the vm automatically.

---

### Post by unclecameron on 2008-10-28
looks like it works in Virtualbox, so it must be driver specific to VMWare, and only on Intrepid.

---

### Post by Anicka on 2008-10-28
As I understand it there are two major changes that would be possible suspects in this affair. As I said before the handling of inputdevices has changed. Maybe by updating the system rather that install it clean, there is something in this transition that doesn't work. If I understand it correctly, the vmmouse-driver is still handled by xorg. So if the xorg.conf is scrambled during upgrade, the vmmouse would naturally get very confused.

Secondly there seems to be a lot of reports (also from other linux-distros) about problems due to the new kernel 2.6.27. There are things in it that has changed (I don't know exactly what, not savvy enough), vmware doesn't recognise it and there is trouble. I was so happy when I installed workstation 6.5, because I had no error messages, no tweaking to do, it just worked with Hardy. Now if I want to upgrade to Intrepid, I know it will break my set-up.

I agree with you, this is by no means an error in ubuntu, it is a development where vmware is not keeping up speed. Sadly enough, it is a constant problem, where vmware is lagging in its development. I would understand if I was using an old or even obsolete version of their program, but I'm using the newest they have and still it is behind.

If I get the time I might try to install again, but with the open tools and see if it makes things better, but we need the upgrade to work and not only the new install.

---

### Post by unclecameron on 2008-10-28
It didn't seem to matter if I attempted a fresh install or dist-upgrade, the effect is the same... Yoo Hooo...VMWare guys (listening?)

---

