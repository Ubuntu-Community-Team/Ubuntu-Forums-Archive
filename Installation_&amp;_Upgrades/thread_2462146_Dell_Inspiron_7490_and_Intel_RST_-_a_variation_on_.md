---
title: "Dell Inspiron 7490 and Intel RST - a variation on the usual complaint"
date: 2021-05-14
forum: Installation &amp; Upgrades
---

### Post by mathum on 2021-05-14
So, can't switch to AHCI as so many of us have sadly discovered. This means the computer will not accept Ubuntu or other mainstream distro)
And yet, i can install and run Endless OS (but i don't like it much)

So, is there any hope of applying Endless's install magic to mainstream distros?

---

### Post by grahammechanical on 2021-05-14
I have just posted this link in another thread. There might be something in it that is useful to you and other Dell users.

[https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc)

Regards

---

### Post by oldfred on 2021-05-15
Can you do a full install to an external drive?
I for years did full installs to any flash drive larger than 16GB. Install was very slow, but with some changes to reduce writes, they have worked. 
I do not use them for daily use, and they do have limited life.

But then I installed to a SSD in an external USB3 adapter.
 I upgraded my desktop with newer NVMe drive & removed the smaller M.2 SSD. So to use SSD I purchaced a inexpensive M.2 to USB adapter. It is almost as fast as it was as when an internal drive and lot faster then my internal HDD.
I am just about to the point of not buying any more USB flash drives (I have a lot) and only buy SSDs.

---

### Post by dddman on 2021-05-15
You should still be able to run Ubuntu in a virtual machine.  I do not have the AHCI problem, but this works for me.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by mathum on 2021-05-15
Thank you for your reply. I have read that article. The problem is that the Inspiron 7490 has no way to switch to AHCI, and so the C: drive is not seen by the Ubuntu install. It's a known problem that only Endless OS has seemed to be able to overcome. Again, thanks for taking the time.

---

### Post by mathum on 2021-05-15
Thanks for responding. I'll have to give that a try.

---

### Post by mathum on 2021-05-15
Thank you oldfred for your reply. The machine in question is a laptop, usually used away from a power source or even a table, so an external SSD has limited appeal in this case.
It's been a while or two since i tried making a persistent Ubuntu USB. I never really had much luck with that. I'll try again in the hopes that the available tools have improved (or that i have!).
Thanks again

---

### Post by vanguard478 on 2021-06-10
This was recently posted on the Dell Inspiron 7490 forum. Haven't tried this myself but will try in few days. You can check the post here :[https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true#M17730](https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true#M17730)

---

### Post by mathum on 2021-07-16
I found tis code which apparently worked for some folks:
[https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true](https://www.dell.com/community/Linux-General/Inspiron-7490-BIOS-How-to-turn-off-intel-RAID-on-and-swith-disk/m-p/7891053/highlight/true)

I ran into some snags running it and had a convo with Cubic PPA (cubic-wizard) who provided this to be run in the CUBIC virtual window:

=====================================

Here are the correct instructions (just four simple commands):

    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
wget -q [https://deb.endlessos.org/keys/eos-pub-archive-key.asc](https://deb.endlessos.org/keys/eos-pub-archive-key.asc) -O- | apt-key add -
echo "deb [arch=amd64] [https://deb.endlessos.org/debian](https://deb.endlessos.org/debian) master endless" | tee -a /etc/apt/sources.list.d/endlessOS.list
apt update
apt install linux-headers-generic/master linux-image-generic/master

    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

On the Kernel tab of Cubic's Options page, be sure to select the newer kernel you just installed (5.11.0-19).

=========================

It allowed me to get an installation on disk, but a new problem emerged:

"The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not Boot."
And on exiting the installer crashed.
I used all the defaults and minimum install, ran the install with fast boot off and secure boot off. (I am dual-booting with windows)

It looks like a bug. Has anybody else had this problem? How did you fix it?

So close and yet so far!

 

Link to the CUBIC conversation:

[https://answers.launchpad.net/cubic/+question/697981](https://answers.launchpad.net/cubic/+question/697981)

---

### Post by oldfred on 2021-07-16
What drive are you installing into?
And what drive is ESP - efi system partition on?

Ubuntu's  Ubiquity installer assumes ESP is on first drive or sda/hd0 or first  NVMe drive, if installing in UEFI mode. Of incorrect install in BIOS  mode on gpt partitioned drive without bios_grub partition. 
If that drive does not have ESP, or is not seen then install of grub bootloader fails.

Very old bug, still not fixed. Not important if install is to one drive in AHCI mode that has ESP.
Two drive installs or external drives often have issue.

Post this:
sudo parted -l

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or  if you have ESP on second or external drive, you can just reinstall  grub, either manually or using Boot-Repair's advanced mode & full  reinstall of grub to correct drive.

---

### Post by mathum on 2021-07-17
Thanks for the detailed explanation oldfred, but i may found the answer to my prayers with the help of people at Cubic and a Dell forum.
For anyone like me frustrated by Dell and wanting to install Ubuntu on an Inspiron 7490:



This worked, easily! (I include Nuliel's great work from above to make a complete (i hope) instruction set all in one place. The primary difference is the code entered in Cubic's console (thanks for the help Nuliel and Cubic people!)

Use a separate Linux system to make the custom ISO

1. Generation of iso

First download an iso that you want to modify (I used ubuntu-20.04.2.0-desktop-amd64.iso).

Then you can install the PPA of cubic with:

sudo apt-add-repository ppa:cubic-wizard/release
sudo apt update
sudo apt install cubic

Then open cubic, it will ask you to define a working folder and the iso file downloaded before.

Continue, you will obtain a console.

Then use the code below:

apt update

apt install grub-efi-amd64-signed

wget -q [https://deb.endlessos.org/keys/eos-pub-archive-key.asc](https://deb.endlessos.org/keys/eos-pub-archive-key.asc) -O- | apt-key add -

echo "deb [arch=amd64] [https://deb.endlessos.org/debian](https://deb.endlessos.org/debian) master endless" | tee -a /etc/apt/sources.list.d/endlessOS.list

apt update

apt install linux-headers-generic/master linux-image-generic/master

rm /etc/apt/sources.list.d/endlessOS.list

apt update

You can continue with default parameters (just choose the kernel that has been installed, not the old one!), and it will generate a modified iso compatible with Dell Inspiron 9490!

You can burn this iso on a usb key. You just have to pay attention that you utility to burn the iso file must create a UEFI compatible usb key (that's the case with Etcher but many others utilities will do the same)

 

2. Prepare windows

Boot the Dell Inspiron 7490 on windows, and first disable fast startup (you can follow for example [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup) )

NOTE: I made the new partition during the Ubuntu install.

That's all for windows.

 

3. BIOS configuration

Go in the BIOS and disable Secure Boot, this is useful to install nvidia driver.

 

4. Install Ubuntu or variant

Now you can insert your usb key and boot on it (it's F12 to choose the usb key)

---

