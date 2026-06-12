---
title: "installed up to grub prompt"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by kenlprotech on 2008-10-30
Trying this OS for the first time. I am using a 384MB Presario 5010 with 10GB IDE boot and 160GB on separate medley raid controller.

I managed to *[FONT="Fixedsys"]skate[/FONT]* through the downloaded 8.04 i386 server CD install, creating partitions on both drives, marking hd0,0 bootable, booting from the built-in IDE. (Found my NIC and using DHCP.)

'We' completed the text mode install stuff, rebooted and now I am at the grub prompt. I am unclear where to go from here. I read about grub commands (root, kernel, initrd) but only the root (hd0,0) seems to work. (is our kernel file name "kernel-image-2.6.24-19-generic-di" ...?)

Is there a concise doc which takes me through the rest of my installation? Did I end up here because of a unexpected problem or is this typical?

TIA, and sorry if the answer is right in front of me.

---

### Post by cariboo on 2008-10-30
What do you mean at the grub prompt? Do you have a menu with different boot choices? Or are you actually at a command prompt, like this?

```
jim@alexis:~$ 
```

There is no gui for the server so if you were expecting a desktop of some sort, you installed the wrong version. If you did wanted to install the server version, then you should install a lightweight desktop, as you are a little low on resources to run a full gnome desktop.

If you want to install a desktop and you are at the command prompt, type the following:

```
sudo apt-get install xubuntu-desktop
```

Enter the password you set during installation, the password will not be echoed back when you type it in, this is to prevent shoulder surfers from getting your password when you log in.

This will install a fairly lightweight desktop that should run quite well on your system. 

Jim

---

### Post by caljohnsmith on 2008-10-30
How about first posting:
```
sudo fdisk -lu
```
And please identify all your partitions. Also, when you get the grub prompt on start up, try:
```
grub> find /boot/grub/menu.lst
grub> find /grub/menu.lst
```
Do either of those commands say they found Grub's menu.lst?

---

### Post by panda726 on 2008-10-30
There seems to be a known issue with IDE and SATA drive ordering, and I believe this also exists between IDE and RAID drives.  Whichever drive you installed to, you probably will find that according to grub, the correct drive is the other one.

I have a setup with one SATA drive and two IDE drives.  In Ubuntu, the drives are ordered IDE1, IDE2, SATA, but in the boot grub they are ordered SATA, IDE1, IDE2.

I would try to find grub's menu.lst, as caljohnsmith said, and if it is found, try:
```

grub> configfile (hd1,0)/boot/grub/menu.lst

```
Replace the drive/partition numbers with whatever grub gives you, and make the path conform to where you found menu.lst.  This should bring up your grub menu, from which you can edit one time the boot sequence.

Still, post the output of "sudo fdisk -lu", unless of course you get everything running before you post it.

Tor

---

### Post by Cobbs on 2008-10-30
> **cariboo907 said:**
> What do you mean at the grub prompt? Do you have a menu with different boot choices? Or are you actually at a command prompt, like this?

```
jim@alexis:~$ 
```

There is no gui for the server so if you were expecting a desktop of some sort, you installed the wrong version. If you did wanted to install the server version, then you should install a lightweight desktop, as you are a little low on resources to run a full gnome desktop.

how do you check to see if the server edition was installed?  Because when I boot up, I get the console login that you were talking about...

---

### Post by kenlprotech on 2008-10-31
[COLOR="DarkRed"][FONT="Lucida Console"]Ahhh... the server doesn't have a gui. That makes great sense. My goal is to install a demo Zimbra server, so I hope I am heading down the right path. [Production machine(s) will have better hardware. & clients will have the gui.]

The boot screen appears  _quickly_  and looks like this:

[SIZE="1"][FONT="Fixedsys"]GNU GRUB version 0.97 (nnnnnn lower / nnnnnn upper memory)

[ Minimal BASH-like .......

grub>[/FONT][/SIZE]

1) There are no boot choices, just what appears above
2) I have not found menu.lst
3) sudo is not a recognized command

My gut tells me nothing much has installed yet. It did tell me to reboot after going through the text install menu.

Looking forward to new suggestions.[/FONT][/COLOR]

---

