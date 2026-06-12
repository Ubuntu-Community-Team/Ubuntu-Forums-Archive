---
title: "Viglen MPC - update blackscreen plus kernel synch problem on new install"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by gebbione on 2011-01-29
Hi all,

I have searched and subscribed to a number of threads fairly related to this issue but i though I post my own as some of them where slightly different and I could not get around the solution suggested.

I have recently purchased a Viglen MPC and I have run the usual update selecting all packages including the kernel.

At reboot the unit gets to a black screen, really it does not send any signal to the monitor anymore. I guess this might be a X or something related problem. 

Based on the Viglen suggestions I edit the grub load options (see screenshots)

[IMG]http://gebbione.dreamhosters.com/MPC_viglen/bootLines_2.jpg[/IMG]
and add the lines " pnpbios=off pci=noacpi vga=791 " or even the "pnpbios=no noapic acpi=off" as suggest in other articles
like in this screenshot 

[IMG]http://gebbione.dreamhosters.com/MPC_viglen/bootString_2.jpg[/IMG]
The standard (upgraded) xubuntu loaded on the MPC does not load with these options and it gives me a "kernel panic - not syncing: Attempted to kill init" 

[IMG]http://gebbione.dreamhosters.com/MPC_viglen/bootError_2.jpg[/IMG]

I have also followed the article from Duncan Sample at this URL,[http://sample.me.uk/blog/post/mpc-l_xubuntu_install](http://sample.me.uk/blog/post/mpc-l_xubuntu_install)
Using these steps (as per above pnpbios-no etc) i get to the shell only if i boot with the failsafe distro of clonezilla, i manage to do all the mounting operations and enter the new root shell and when i try to do a kernel update the system tells me that i have already the latest/correct version installed.

Also i have tried to re-install xbuntu but i get stuck to a screen that does not help as you can see from the image, where i get to when the xubuntu is installing

[IMG]http://gebbione.dreamhosters.com/MPC_viglen/screen_while_install.jpg[/IMG]

My favourite approach would be to understand why I really get the blackscreen problem, so if I could just fix this from the shell it would be great.

Please let me know your suggestions on how to go about it.

---

