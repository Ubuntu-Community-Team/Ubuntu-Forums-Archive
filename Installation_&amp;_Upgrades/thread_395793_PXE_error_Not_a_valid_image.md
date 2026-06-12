---
title: "PXE error: Not a valid image"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by mys_shekar on 2007-03-28
Hi,
  I am trying to set up a netboot server using FC6, so that the clients
can be installed through the network.  On trying to boot the client, I
get the following message:

Searching for server (dhcp)...
Me: xxx.xxx.0.110, server: xxxxxx, Gateway xxx.xxx.0.254
Loading xxx.xxx.0.254:/lts/boot/pxe/pxelinux.bin error:not a valid image
Unable to load file
error: not a valid image

May I know where I am going wrong??

tnx,

---

### Post by DollaBillz217 on 2007-03-29
I think you issue might be with the image file you are trying to use, pxelinux.bin.  Try using pxelinux.0 as your image and see if that helps.  I too am in the middle of setting this up and am stuck on the same step, except I am using the pxelinux.0 bootloader.  The reason of using the pxelinux.0 bootloader is because the kernel can only handle somethin like 64KB so it uses the bootloader because it can handle much more.  Can you post your dhcp.conf file also so I can see if there are any issues with that as well.  If you fix this issue please email me at [email]codyw725@yahoo.com[/email] because I have been having this same problem for over a week now and cannot figure it out.  Thanks!

---

