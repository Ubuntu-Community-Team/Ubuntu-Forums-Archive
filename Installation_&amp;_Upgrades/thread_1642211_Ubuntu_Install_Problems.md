---
title: "Ubuntu Install Problems"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by deal_89 on 2010-12-10
Hi, I am new to Ubuntu and have been trying to install 10.10. The install seemed to go fine but nothing loads and all i see is a single line flashing after the bios. I am now going to reinstall and cross my fingers. but can anyone tell me what this problem might be and what i can do about it?
Thanks
Deal

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

Assuming Ubuntu was installed successfully, from Bios screen, press and hold down Shift key until you see Grub menu. Highlighting the first entry in Grub menu, press 'e' to edit it. Navigate to words "quiet & splash", delete them and type "nomodeset" instead. Press Ctrl + X to boot. Hopefully, you'll see the desktop this time.

Go to System > Administration > Additional Drivers and install the current drivers for you graphics card and get rid of that problem permanently ;-)

---

