---
title: "Kernel removal"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by apoc on 2005-02-07
Hey, this proberly is trivial, (since google game me no help)

I followed the wiki on how to make a custom kernel, It just didn't want to start X after removeing APGART (I really would like fast write and smb for my nvidia card)..

so now I have to scroll down at the boot screen to select the old default kernel, Isn't there a simple command to uninstall the custom kernel with ?

I tried "sudo apt-get remove name_of_custom_kernel" but without luck.. 

Or do I have to delete the kernel and find a way to edit the boot screen ?

---

### Post by az on 2005-02-07
"I tried "sudo apt-get remove name_of_custom_kernel" but without luck."

What do you mean?  Did it not remove it?  Did it remove it, but leave the grub entry?


Unless you misspelled the name, or did not use kernel-package to package your new kernel, it should have removed it.

---

### Post by apoc on 2005-02-08
Thinking about it I proberly used autofinish for the name and had .deb at the end... will try when I get home from school

---

