---
title: "How to revert Kernel updates?"
date: 2015-10-11
forum: Installation &amp; Upgrades
---

### Post by JustAnotherGuitari on 2015-10-11
Hey everyone,

So I'm running Ubuntu Gnome on my Dell XPS 13 and I recently did an apt-get upgrade to 3.19.0-30-generic. I'm using FDE and when it prompts to enter my decryption password on boot, the keyboard doesn't work. When I force shutdown the machine and reboot, it gives me the option (from advanced Ubuntu options menu) to boot from 3.19.0-28-generic. How can I remove .30 and only boot to .28 so I can actually log into my machine? 

Thanks!

---

### Post by Dennis N on 2015-10-11
Read  "Manually Setting a Specific Kernel as the Default", and the sections below that "Setting a Submenu entry as the default" and "Submenu Designation Examples" on the page:  

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

There are several ways discussed there to specify a kernel to use. Note that the newer grub menu use the title **Advanced options for Ubuntu** for the submenu. Use the exact title the matches your grub menu, including capitalizing where needed.

Run **sudo update-grub** after making changes to /etc/default/grub.

---

### Post by ajgreeny on 2015-10-11
You can remove that version of the kernel with your package manager, using **apt-get remove** or **synaptic** or I assume software-center, though I never use that so I don't know how it deals with kernels.  If you want to use a GUI to do it install synaptic and use that; it is the best GUI package manager for Ubuntu.

You will then need to make sure you don't allow the kernel to update again by checking at every update what is to be updated, or perhaps better, reconfigure grub to boot to an earlier kernel by editing /etc/default/grub as follows according to the info at [https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

---

