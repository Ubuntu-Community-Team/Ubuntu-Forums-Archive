---
title: "How to Install Encrypted Ubuntu 24.04 on Multi-Boot MacBook Without Removing Other OS"
date: 2024-07-08
forum: Installation &amp; Upgrades
---

### Post by xma1 on 2024-07-08
Hi everyone,


I currently have a MacBook set up with a dual (or triple) boot system, running OSX, Windows, and Ubuntu 22.04. I use rEFInd to choose between the systems.


I now need to install an encrypted version of Ubuntu (preferably Ubuntu 24.04). However, during the installation process, I've only found options to encrypt the disk, which removes all other systems from my MacBook.


How can I install an encrypted version of Ubuntu without removing my existing installations, ensuring that only the Ubuntu partition is encrypted?


Thanks in advance for your help!

---

### Post by TheFu on 2024-07-10
Doing this isn't advised.  There are many dangers. You'll need to manually install everything. Look for guide for how to do that.  I haven't seen any 24.04 manual install+encryption guides. I think the last manual install guide with encrypt I saw was for 18.04, perhaps 16.04, by Paddy.

However, there are other options.
a) Only have 1 disk connected and do a normal installation, checking the Whole Drive Encryption option.  After the fact, connect the other 3 disks and use rEFInd to select which OS to boot.

b) Choose your main OS, install it with whole drive encryption, then use a hypervisor and virtual machines to run the other OSes.  Since the VM settings appear as a full machine to the guest OSes, you can choose to use whole drive encryption on those VM installs, or just trust the physical installation whole drive encryption to be sufficient to protect the system. After all, you trusted that OS enough to install it on the computer.

Using whole drive encryption in a multi-boot setup might be interesting, but it isn't exactly secure for a number of reasons.  It provides 3 methods for an "evil maid" to grab the entire OS and take it without your knowledge for the encryption to be attacked outside your control.  I suppose, there's always an "evil maid" attack even for single OS installs too.  

From a practical standpoint, booting each OS off a different USB3.2 SSD storage device is probably the best option. Just keep the storage with you at all times. There are some small, fast, m.2 2242 SSDs with USB3.2 interfaces.  Of course, you can use slow SDHC flash storage or anything in between too.

Not really what you wanted to hear.  OTOH, some people are really stubborn and want what they want. If you are that type, please take good notes and create a how-to guide for others to follow.  Note all the details - exact machine, exact storage setup, exact OS release versions, for the next person.

---

### Post by oldfred on 2024-07-10
I have had good luck with M.2 SSD on external USB with an USB to M.2 adapter.
I now have two.

My Dell laptop PC needed new motherboard and Ubuntu worked but Windows did not. I ended up having to use Dell's recovery which totally restored drive to as new or erased my entire Ubuntu install. Testdisk could not even find old partitions. But that install was just copy of my desktop, so no data lost.
But I then used my one external SSD to boot Dell laptop which just has Kubuntu on it. So purchased a newer larger M.2 memory card & another adapter.

Mac seem to have unique issues with every year's release. Very new Mac are just now starting to be supported.

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind](https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind)

Most with Mac seem to not use grub as boot manager but use rEFInd.
I have used rEFInd on a tiny flash drive for emergency boot, but do not use it normally.
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by yancek on 2024-07-10
I don't use encryption myself so can only refer you to the site below which explains how to encrypt POST install.  It is specific to 20.04 and I have no idea if the process is the same for 22.04.

[https://jumpcloud.com/blog/how-to-encrypt-ubuntu-20-04-desktop-post-installation](https://jumpcloud.com/blog/how-to-encrypt-ubuntu-20-04-desktop-post-installation)

---

### Post by xma1 on 2024-07-18
Thank you for the answer. I will try to do it manually next week if I have time.


- Adding a second HDD is not feasible. My notebook only has two USB ports, and USB is too slow compared to PCI-SSD. The MacBook also doesn&#8217;t have an extra slot for another internal disk.


- Using a VM is not an option either. It&#8217;s too slow, and while I prefer Linux, on a Mac you have to use macOS for hardware compatibility. macOS has slow boot times, a terrible mouse acceleration curve, and other issues that prevent me from using it as my main system, though I need it for some projects. Windows is theoretically usable in a VM, but configuring the hardware connections to the VM (USB and COM ports) requires a lot of setup.

---

### Post by shaform2 on 2024-08-02
It was possible to do this in 22.04, but seems like the new installer no longer has this feature. Wondering if there are workarounds to achieve this.

For reference, here are some related posts regarding this problem:

* [https://askubuntu.com/questions/1515615/disk-encryption-in-ubuntu-24-04-lts](https://askubuntu.com/questions/1515615/disk-encryption-in-ubuntu-24-04-lts)
* [https://www.reddit.com/r/Ubuntu/comments/1ceblzx/unable_to_install_ubuntu_2404_installation_with/](https://www.reddit.com/r/Ubuntu/comments/1ceblzx/unable_to_install_ubuntu_2404_installation_with/)

---

### Post by shaform2 on 2024-08-02
Ok, I've found a workaround. While the Ubuntu 24.04 installation media has the new installer, some other flavors still use the old installer. So if you install other flavors such as Ubuntu Unity 24.04, it would become possible to install Ubuntu into an encrypted partition without needing to delete other partitions. I haven't tested other flavors except for Ubuntu Unity 24.04, but I am guessing this would also work for other flavors.

---

### Post by xma1 on 2024-09-02
Thanks for Answer, I will try it with Ubuntu Unity 24.04.

---

### Post by markxma1 on 2024-10-06
Thank you! I needed to create an extra boot partition, but it worked. Sorry for the long response; I had a lot of work to do.

---

