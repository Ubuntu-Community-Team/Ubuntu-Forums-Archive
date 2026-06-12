---
title: "Karmic freezing after boot"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by HelmutN on 2009-12-12
After the Grub menu selection I get a terminal screen with the following information:
 Boot from (hd0, 0) ext3 18ebd363-befe-43fb-...
Starting up...
 And this freezes booting

but this only happens with the kernel 2.6.31-16 the kernel 2.6.28-9 is running well with karmic so it  seems to be a kernel problem but i get no message therfor i dont know what is the problem.
I have removed the quit and splash option but no message.
maybe somebody can help me

---

### Post by s3MA00RRNY on 2009-12-12
sudo apt-get install --reinstall linux-image-2.6.31-16-generic

---

### Post by HelmutN on 2009-12-12
i have tried to reinstall but it does not solve the problem.
i get the same problem when i boot from the live-cd

---

### Post by s3MA00RRNY on 2009-12-12
Enter lspci at the terminal and post the output.

---

### Post by HelmutN on 2009-12-13
now i'am up and  running,
i have changed the parameter memory hole to disabled in the Bios

thanks all for your help

---

