---
title: "Installed Ubuntu within Windows Vista, doesn't boot to desktop?"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Totakeke on 2008-08-06
I just installed Ubuntu under Windows Vista, but when I select "Ubuntu" from the boot menu, it just gives me a command prompt and says "grub>". How can I get to the desktop? Thanks.

---

### Post by tuxxy on 2008-08-06
How do you mean you installed it under vista, did you set partitions up correctly, are you able to log in?

---

### Post by Totakeke on 2008-08-06
Sorry, I should've been more specific. I installed it through Windows, and it doesn't have it's own partition, I just installed it in my C:\ drive on my main partition. So to answer your question, it doesn't have its own, no. I installed it from Windows.

---

### Post by tuxxy on 2008-08-06
You shouldnt of done this, unless you mean in a virtualmachine on your windowsor through wubi?  

I think you should of read the install guide first as you may have damaged your windows now, you were meant to partition a space on your hard drive first for Ubuntu so it didnt install over windows.  Then you should of booted your comp with the ubuntu CD in as you would if you were installing windows.

It is possible to install from the GUI but you would need to run the live CD and click on the install icon on the desktop.

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

---

### Post by Totakeke on 2008-08-07
I didn't think I had to partition, I was trying to install Ubuntu using Wubi. I would dedicate a partition to it if I was doing a clean install, but the menu from the CD has the option to install within Windows, so that's what I did.

---

### Post by tuxxy on 2008-08-07
So did you run the live CD yes? even if you use wubi to install it still will need partitiong at some point when you are running the install process.

---

### Post by Totakeke on 2008-08-07
Yes, I ran the Live CD. I was reading this, [http://www.maximumpc.com/article/howtos/howto_install_linux_risk_free_with_no_formatting_or_repartitioning_required](http://www.maximumpc.com/article/howtos/howto_install_linux_risk_free_with_no_formatting_or_repartitioning_required), and it said Linux would install just as an application within Windows.

---

### Post by tuxxy on 2008-08-07
The live CD and wubi bring you to the same installer as running the CD at bootup, when you installed there would of been an option for running the install over the full disk or keeping it to a free partition, you would of needed the second one.

---

### Post by Totakeke on 2008-08-07
There was, and I selected the option that will install it separately, so I don't have to dedicate any space to it. In fact, I just uninstalled and reinstalled again, and once it reboots for the second time, after I go through all the Linux prompts and it installs, I just get a prompt. What's going wrong? Should I download the ISO again and reburn it? Thanks again.

---

