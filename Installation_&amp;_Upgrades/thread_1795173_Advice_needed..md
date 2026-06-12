---
title: "Advice needed."
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by elpuir on 2011-07-02
My laptop crashed recently. Now I have installed Ubuntu 11.04. I would like to have Windows 7 installed in parallel. So I was planning to use GPartition to create a partition and install Win 7. Since my CD Drive doesn't work, I have created a USB of Win 7 CD. But my friend says, I can't install Windows 7 with Ubuntu on and it's best to first install Windows and then Ubuntu. Is he right? If so, why?

---

### Post by sanderd17 on 2011-07-02
Windows will overwrite the MBR (master boot record) so that you can't boot ubuntu anymore.

So your friend is right, it is easier to install Windows first, but repairing the MBR isn't difficult either.

Just install Windows, than you boot an Ubuntu live USB and you execute the steps at  this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This will repair the MBR so that you'll be able to choose between windows or Ubuntu.

---

