---
title: "Ubuntu newbie; neither my old Windows 7 or my new Ubuntu boots now. Help me"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by anandbobby on 2010-08-08
Hi all,
  I downloaded ubuntu a few days back and installed last night on my old HCL laptop. It is a Core Duo, 1 Gb RAM, 120 Gb HDD. I installed Ubuntu from within Windows in a separate partition (7 Gb). Today morning I updated it and installed some softwares from the repository. I am not sure if this is the mistake. During the update I selected around 15 softwares to download & install. After the update the machine required a restart but I cancelled it ( Restart Later) and continued with my application installation. Finally I restarted my machine and I'm getting a error msg. Not even my boot option menu which prompts me to enter either into Windows or Ubuntu appaers now. I cannot loose my Windows. All my data are in there. Ubuntu, I'm ready to even perform a fresh install if necessary. Can anybody help me get inside Windows atleast to backup my data. Thanx a lot in advance. Please help me out guys.

The error msg is:
error: no such device: f0e88c3a-8a7c-48ed-8fa2-d730e4a0299c
grub rescue>

I dunno if this would help; But this is wat appears on the window.

---

### Post by dino99 on 2010-08-08
nothing is broken but that uuid giving this error. So boot with a ubuntu live cd or usb stick, then open a console and run:

sudo blkid

that will list all the uuid , one of them need to replace the wrong one on the boot line (take note of them exactly) then exit and remove the cd, next will boot on hdd

as grub2 dont know about multi boot (due to the wrong uuid), the menu is hidden when you boot; to see it you have to hold "shift" key down at end of bios process

then select the boot line into grub menu, edit it (E) and change the wrong uuid by the one found by blkid (same lenght), then boot (ctrl+X)

to make the change permanent with the good uuid, into a console:

sudo grub-mkconfig
sudo update-grub

---

