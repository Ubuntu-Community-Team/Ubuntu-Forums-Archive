---
title: "Broken Video after clean install"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by d4ni on 2012-07-22
I've just made a clean install of 12.04 x64 and this is what happens after first time trying to use it...

[IMG]http://i47.tinypic.com/14nodac.jpg[/IMG]

My vidcard is: NVIDIA GeForce GTX 570

I can't try it with another vidcard because I don't have one and my motherboard ([CrossFireX] GigaByte GA-970A-D3 AMD 970) does not have one.

If I do Cntrl+Alt+F1 it stays the same.

Any ideas? Thanks!

---

### Post by bogan on 2012-07-22
Hi!, **d4ni,**  Welcome to this Forum, there is a full trouble shooter in Post #1 of the 'Blank Screen' Sticky.

A good deal more info is need than that partial screenshot. Please send a full mscreen shot, but use a Thumbnail or a link to a store site.

Does it happen before the log-in screen?, before login or after?

Does it do the same if booted to Recovery? using the various options?

Or when logged in to other Desktop choices?

Have you tried editing the Grub menu script ? say with 'nomodeset' added to the 'Linux' line. [To get to edit mode: press 'e' with the Ubuntu entry highlighted; 'Ctrl +x' afterwards, to boot.]

Can you get to a tty ? [ Text Terminal]?

If so, please Post:
```
lspci | grep -iA3 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```Chao!, bogan.

---

### Post by d4ni on 2012-07-22
This problem happens after I select Ubuntu in grub, so I guess it's the Login screen, I try to Ctrl + Alt + F1 but nothing happens I can't get to a terminal but...

I tried in recovery mode and I got to a terminal. Here are the commands you asked for.

```
deini@deini:~$ lspci | grep -iA3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570 HD] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
deini@deini:~$ sudo apt-cache policy nvidia-current
[sudo] password for deini: 
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
deini@deini:~$ cat /sys/module/nvidia/version
cat: /sys/module/nvidia/version: No such file or directory

```

Thanks!

---

### Post by gordintoronto on 2012-07-22
This might be helpful:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by d4ni on 2012-07-23
Thanks everyone, solved by entering in recovery and installing nvidia-current. Reboot and ready.

---

