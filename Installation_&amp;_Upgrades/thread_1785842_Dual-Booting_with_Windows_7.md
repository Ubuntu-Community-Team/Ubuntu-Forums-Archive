---
title: "Dual-Booting with Windows 7"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by ticktoast on 2011-06-18
So, tomorrow I'm going to receive a nice Windows 7 disc for my computer. However, I only want it for Photoshop and iTunes, really. I don't want to get rid of Ubuntu. Period. So I want to be able to dual boot my computer.

The only problem is I haven't been able to find any information on setting it up with Linux installed first. I've seen plenty of guides on how to install Ubuntu alongside Windows, but only if Windows is already installed.

Can anyone give me some pointers or send me a guide that could help me out? I know that Windows's bootloader is going to try to take over, and I'm going to need a bit of help, as I'm no tech genius.

---

### Post by YesWeCan on 2011-06-18
It's pretty easy, really. You have to make room on your disk for Windows. You can do this using a live CD and GParted to shrink your Ubuntu partition (you cannot do this on a running Ubuntu partition so you have to use a CD). It is probably best to make the space in front of Ubuntu. Just Google for how to use GParted, it's pretty easy to figure out.

Then you can boot your Win7 CD and tell it to install to the empty space.

You are already aware that the Ubuntu MBR will be over-written by the Windows MBR. So once you've installed Windows you won't be able to boot Ubuntu. So you have to reinstate the Ubuntu (Grub) MBR.
To do this, boot from live CD again and do
[COLOR="Navy"]sudo fdisk -l[/COLOR] to find the drive name, like sda, and the partition that linux is in, like sda2.
Then reinstall Grub
[COLOR="Navy"]sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

Then reboot into Ubuntu and run
[COLOR="Navy"]sudo update-grub[/COLOR]
to add Windows to your boot menu

OR
Run Windows in Ubuntu using VirtualBox. This is really easy and although Windows won't run quite as quickly it should be fine for Photoshop and iTunes. You download it from [http://www.virtualbox.org/](http://www.virtualbox.org/)
This will take more learning but it is a very useful tool. You can install any OS and try it out. You need a couple of GB of RAM for this to work well.

---

### Post by ticktoast on 2011-06-18
Thank you very much!
Just 2 small questions, though, if that's alright.
First, my Live CD has Maverick on it, not Natty. Do I need to write a new CD or will the old one still work?
And second, my Linux partition is an ext4 filesystem. I looked around a bit, but am still a bit unsure about accessing the files on the Windows partition. Is there a driver that can do this? And would I be able to read and write the files? Or just read them?

---

### Post by YesWeCan on 2011-06-18
You probably want to use a live CD that matches the Ubuntu on your hard drive. This is because the version of Grub may be different and the grub-install may not work. I am not sure, but better not risk it.

Natty will read and write your Windows NTFS partition, not a problem. Windows will neither read nor write your linux partitions.

---

### Post by ticktoast on 2011-06-19
Thank you very much, again.

I've run into a snag on the installation process, though. Hopefully this isn't too much.. 

My HD is partitioned and ready to go. However, I can't get the DVD to boot up after restarting.

It's not a copy from a store, so it's not neat and tidy, so to speak. I have a friend who works with Microsoft, and he was able to throw the files with a product key onto a DVD. I'm unsure of what I'm supposed to be doing with the install.wim or boot.wim files. I'm not used to working with Windows files at all, so I'm a bit lost...

---

