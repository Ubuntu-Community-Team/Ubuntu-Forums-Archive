---
title: "ubuntu-12.10-desktop-amd64 doesn;t fit cd ?"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2012-12-26
ubuntu-12.10-desktop-amd64.iso
 downloaded and tried to make cd. but it says it requires a cd 763.8Mb capacity. i can usually get cd for 698 Mb only.
how do i go about installing this to a usb 16Gb flash drive?

---

### Post by oldfred on 2012-12-26
The installs kept getting bigger & bigger. They used to be a bit oversized and would still work on a CD. Now you have to use a DVD or a smaller flash drive.

I now install to my flash drive from my hard drive with grub2's loopmount, but you have to have an install using grub2 to use that.

Are you putting a full install or persistence install on your larger flash drive?

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by ramaswamyps on 2012-12-26
i am running 3 inux installs on my toshiba saellite-c855d over windows 8/windows 7
i am not installing grub to hd0 as w64 and 32 indows will not boot with grub2 installed. i had serious troubles previously in my 2 old laptops.
also this is a new laptop and under warranty. system recovery will be difficult if not impossible with grub2 in the mbr.
i have been able to install pclinuxos in usb flash and from that grub i can boot my gentoo 64 and 32 bit installs.
i just want to replace pclinuxos to ubuntu-12.10
i was running 12.04 LTS in the hd0 but now running short of space for windows 8 so removed it.
i have vmware-workstation installed n windows 7 and i can boot and install t in vm
can i just copy to usb from vm player install folders?
how can i make initrd after in usb to boot as hardware changes will affect the vm initrd to boot

any help n this regard is welcome.
thanks for the reply

---

### Post by oldfred on 2012-12-26
I do not know about virtual installs. 

But I would recommend a full clean install and copy your data from /home over if you want to save those settings. Otherwise you have a lot of reconfiguration to do.

---

### Post by ramaswamyps on 2012-12-26
can i just burn this iso downloaded on to a dvd ?
in vm it removes most of the packages at finalising install.
ubuntu-12.10 installs and runs in vm but too slow.
i am sure just copying / to usb will not work


as you said i need to clean install

---

