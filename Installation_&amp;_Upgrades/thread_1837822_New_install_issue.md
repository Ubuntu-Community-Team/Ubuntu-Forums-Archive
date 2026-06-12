---
title: "New install issue"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by twister2k33 on 2011-09-02
Maybe someone can help me. I'm new to Linux but have been looking online for days for a solution to my issue and nothing has helped.

I have a pavillion HPE-570F with AMD Phenom with 2tb hdd. I did a fresh install of UBUNTU 11.04 using the entire hard disk (I am not dual booting. I chose option to erase entire hdd and install Ubuntu). Ubuntu installs fine but when I reboot after installation, I get a Error: File Not Found and Grub Rescue Prompt.

I have re-installed at least 5 times and the same issue occurs every time. I boot to a grub rescue CD and it is unable to find any operating systems or grub files. However, when I boot to the live CD I used to install, it sees all those files and directories that were installed. (when booting to the live CD, the hdd files are located in /media/<long string of numbers and letters>

I've tried all the suggestions at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) so I'm at a loss what could be wrong.

For the record I installed Fedora 15, Redhat, and Centos and they all work fine. The issue is with Ubuntu and that's the distro I really want to use.

Anyone seen this issue and have any idea how to resolve it? I can add more information if needed but since I'm a noob I'm not really sure what would be helpful.

---

### Post by ~!geek!~ on 2011-09-02
I would suggest just a few checks: 1) Check for the md5sum of the iso you used to burn to create livecd or live-usb (If you did it like that). Not of much help because you mentioned you were able to install it, still just make sure. 
2) 
/**Following steps may be dangerous if you have precious data on the hard-disk. So if you have important data, try following some other guide from ubuntu forums to perform this as I m not providing comprehensive steps here**/
Try reinstalling the ubuntu, but this time choose the last option i.e. something else in ubuntu 11.04 install screen. Now just repartition the disk if you want or just delete all the partitions (in case you don't have anything to backup). Allocate sufficient swap area say 3 gb, Select the other partition and install ubuntu there. 
I hope it helps!!!

---

