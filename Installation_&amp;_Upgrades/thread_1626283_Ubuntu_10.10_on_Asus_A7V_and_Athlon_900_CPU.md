---
title: "Ubuntu 10.10 on Asus A7V and Athlon 900 CPU"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by bmathise on 2010-11-20
Hi. I have been using Ubuntu for some years and I'm satisfied with it. However, from 10.04 and up I have had problems booting the new kernels. The latest kernel I can boot is 2.6.31-20-generic. All newer kernels will just hang during boot. There seems to be a conflict with the ACPI. I get an error message that tells me to upgrade my BIOS. I did, and there were no difference. I still had to boot the old kernel. After upgrading to 10.10, the Nvidia driver won't work. Synaptic tells me it is installed, but when I try to activate it, I'm told there are no drivers installed. Now I suspect that I have to boot the new kernel to get the Nvidia driver to show up and work. What do I have to do to boot the new kernels on my old Asus A7V motherboard with the Athlon 900 Thunderbird CPU and 1024 MB RAM? I tried switching off the ACPI in BIOS, but still no luck. 
If you need to see any log files, let me know which one(s).
And, yes, I know, I should replace this old oversized calculator with a real computer, but I'm flat out of money :) .
Thanks for any help that may let me continue to use my favourite OS, Ubuntu and Gnome.
Bjorn

---

### Post by mörgæs on 2010-11-21
Does it work when adding boot options?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bmathise on 2010-11-22
Thanks for your reply, Mörgæs. I'm stuck at work now. Will check it out when I get home.

---

### Post by bmathise on 2010-11-22
OK, I tried to remove "quiet splash" and add "acpi_osi=" to the kernel lines in /boot/grub/menu.lst. It didn't do anything. The 2.6.32-25-generic kernel doesn't boot at all. The 2.6.31-20-generic kernel boots, but can't start X so it falls back to tty1. This is most likely because it can't find the nvidia driver any more (I guess). The 2.6.31-20-generic recovery will boot and start X in low resolution (still not finding the nvidia driver). I have seen some text about acpi conflicting with something else, flying over the screen while booting. That's why I thought this might be the problem.

---

### Post by dino99 on 2010-11-22
> **bmathise said:**
> OK, I tried to remove "quiet splash" and add "acpi_osi=" to the kernel lines in /boot/grub/menu.lst. It didn't do anything. The 2.6.32-25-generic kernel doesn't boot at all. The 2.6.31-20-generic kernel boots, but can't start X so it falls back to tty1. This is most likely because it can't find the nvidia driver any more (I guess). The 2.6.31-20-generic recovery will boot and start X in low resolution (still not finding the nvidia driver). I have seen some text about acpi conflicting with something else, flying over the screen while booting. That's why I thought this might be the problem.

Looking at your comments, it seems that you always have made dist-upgrades:

- "/boot/grub/menu.lst" : its outdated and you need to remove it, now grub2 is used (grub-pc)

- " start X in low resolution" : again it seems you are using an oldish and outdated xorg.conf, now the kernel directly deal with X

So lets going on:

sudo rm -f /boot/grub/menu.lst
sudo rm -f /etc/X11/xorg.conf

open synaptic and:
- search and remove/purge ALL the installed grub packages
- install grub-pc and grub-common : a dialog box will ask you where to install grub2, choose the disk on which you boot on ( /dev/sd?)

i suppose you might have some orphan packages, some broken symlinks and so on, so its a good idea to install and run bleachbit and gconf-cleaner

Then reboot and check driver activation (system admin additional driver)

If you still have issues with nvidia:
into synaptic: remove/purge ALL the installed nvidia packages, then install nvidia-current, nvidia-common, nvidia-settings.

---

### Post by bmathise on 2010-11-22
OK ... Thanks, dino99. You're right, I already did the dist-upgrade to 10.10. I also noticed an error of mine - I didnt use the latest kernel. The latest kernel I have is 2.6.35-22, and it behaves exactly like the 2.6.31-20 kernel. 

Now I have to try your suggestions. I just have to make a backup first :)

---

### Post by bmathise on 2010-11-22
I have moved too fast. When installing grub-pc, I got a message that said that a line had been extracted from the old menu.lst, and would I please verify that the line was correct. Well, the line was blank, and I knew right away that I made a mistake when I clicked Next. Dino99, you don't happen to know where I can find the command I should have found during installation, and where to enter it? As it is now, I boot into a "terminal" with a grub prompt ( grub> ).

---

### Post by bmathise on 2010-11-23
To be more specific, what commands do I have to enter from the grub prompt to boot my ubuntu installation? Do I simply enter the commands in the kernel line in the old menu.lst or what?
I'm trying to read up on grub 2, but most of the stuff is about setting up grub 2 when an OS is already booted.

---

### Post by bmathise on 2010-11-24
I tried to enter the commands in the old menu.lst, and it almost booted up. 
>  
uuid the_long_string_given_in_menu.lst
kernel /boot/vmlinuz-2.6.35-22-generic
root=uuid=the_long_string_given_in_menu.lst
initrd /boot/initrd.img-2.6.35-22-generic
boot

This made the system start to boot, but after a while, it got stuck in another console. If I remember correctly, the prompt was (initfs).
What did I do wrong?I tried several kernels and several entries for root, but no luck.
The uuid gives me boot from hd1,5 if that is of any help.
I can use a live CD to gain access to my harddrives, so if needed, I can modify config files and get any log files you might need to see.

---

### Post by bmathise on 2010-11-25
I managed to boot up Windows by entering
> 
root hd0,0
makeactive
chainloader +1

Then i tried to boot Ubuntu the same way:

> uuid 4fc211ed-1560-4150-bfd3-9dea2e24d9d5
kernel /boot/vmlinuz-2.6.35-22-generic ro
root hd1,5
initrd initrd.img-2.6.35-22-generic

Ubuntu started booting, but there was something wrong with root. It couldn't find a lot of files. Instead of looking for the files in /dev or /etc it looked for them in /root/dev and /root/etc (e.g. couldn't mount /dev at /root/dev No such file)
Then I ended up in a console with the initramfs prompt.
Anyone got a clue what I'm doing wrong here? Do I have to reinstall Grub2 from a live CD? Is that possible? My Ubuntu 9.10 and 10.04 CD's from Canonical won't boot. Can I use a Debian 5 or Slax live CD to reinstall Grub2? I'm kinda lost here now. I have Windows, but I want Linux back.

---

### Post by bmathise on 2010-11-26
Anyone have a clue about this? I feel I'm talking to myself. If you need any information from the system - logs or anything - let me know. I can access all files on my system, using a live CD.

---

### Post by bmathise on 2010-11-28
Anyone know how I get out of BuzyBox and into Ubuntu?
My Ubuntu installation is on hd1,5. Is that the same as sdb5 in Grub1 and sdb6 in Grub2?

---

### Post by bmathise on 2010-12-01
Guess I'm stuck with Windows 2000 Pro for a good while then. At least, it boots. 
Ubuntu, Linux Mint, OpenSUSE will not boot at all. Debian 5, DSL, Slax will boot fine from a live CD. I'm putting further use of Linux on ice until I can afford a new computer. Thank God for Open Office, so I can continue to access my documents in Windows.

---

### Post by mörgæs on 2010-12-01
You could also try searching a little wider first. 

Reinstalling Ubuntu 10.04 or 10.10 using the alternate ISO and / or the minimal ISO is a good first step, if the regular ISO does not work.

If you are using a USB for booting, creatning it with Unetbootin is the best option.

---

