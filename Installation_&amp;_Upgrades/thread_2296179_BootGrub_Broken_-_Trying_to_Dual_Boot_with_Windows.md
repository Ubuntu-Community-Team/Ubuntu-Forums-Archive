---
title: "Boot/Grub Broken - Trying to Dual Boot with Windows 10"
date: 2015-09-24
forum: Installation &amp; Upgrades
---

### Post by nfmcclure on 2015-09-24
I am trying to install Ubuntu (preferably 15.04) alongside my Windows 10 installation on my laptop.  I have completely broken the boot (and|or) grub though.  I'll give as much detail as I can, describe what the computer is doing, and try to explain how I got there.

It seems that Ubuntu has lost track of which drive to boot up.  I suspect this, because it fits the description of this post: [http://ubuntuforums.org/showthread.php?t=1561735](http://ubuntuforums.org/showthread.php?t=1561735)

Here's what I went through:
```

grub> ls
(hd0) (hd0,msdos1) (hd1) (hd1,gpt9) (hd1,gpt8) (hd1,gpt7) (hd1,gpt6) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2)
grub> ls (hd1,gpt7)/
lost+found/ boot/ etc/ media/ var/ bin/ dev/ home/ lib/ lib64/ mnt/ opt/ proc/ root/ run/ sbin/ srv/ sys/ tmp/ usr/ vmlinuz initrd.img cdrom/ core initrd.img.old

```

All the other partitions return msdos stuff or unknown or random things.  Let me know if you want to see them.  But it would appear my Ubuntu install is on (hd1,gpt7)... ?except for the cmdpath below?

```

grub> set prefix=(hd1,gpt7)/boot/grub

grub> set root=(hd1,gpt7)

grub> set
?=0
cmdpath=(hd1,**[COLOR=#ff0000]gpt2[/COLOR]**)/EFI/ubuntu
color_highlight=black/light-gray
color_normal=light-gray/black
feature_200_final=y
feature_all_video_module=y
feature_chainloader_bpb=y
feature_default_font_path=y
feature_menuentry_id=y
feature_menuentry_options=y
feature_nativedisk_cmd=y
feature_ntldr=y
feature_platform_search_hint=y
feature_timeout_style=y
grub_cpu=x86_64
grub_platform=efi
lang=
locale_dir=
net_default_ip=(null)
net_default_mac=(null)
net_default_server=
pager=
prefix=(hd1,gpt7)/boot/grub
pxe_default_server=
root=hd1,gpt7
secondary_locale_dir=

grub> ls /boot
efi/ grub/ (all the things System, abi, config, memtest86+, vmlinuz, System.map, initrd.img)-3.19.0-28-generic

grub> insmod /boot/grub/x86-64/linux.mod
error: `linux` is already loaded

grub> linux /vmlinuz root=/dev/sda7 ro
grub> initrd /initrd.img
grub> boot

```

A few things to note here.  From the name (hd1,gpt7), I was led to believe that the dev point would be dev/sdb7. Using sdb7 results in a drive not found error.  Using sda7 actually got me to boot.  This takes me to a login screen and when I login, the screen freezes and goes all funny looking.

When I hit Ctrl + Alt + F1, I can log in to the computer via command line.

What do I do from here?  What can make it so that Ubuntu recognizes this partition?  Any help or guidance is greatly appreciated.

Overview of what I've done so far:
[LIST=1]
[*]Created a Ubuntu 14.04 live USB. 
[*]Installed Ubuntu on approximately half of the hard drive (~466 GB partition). 
[*]Everything was great, until the computer froze mid-install of some software (CUDA libraries). 
[*]The computer rebooted into a recovery shell and I spent hours figuring out how to get it to boot. 
[*]Here is the other thread that I posted, in which a kind soul helped me to get it to boot:  [http://ubuntuforums.org/showthread.php?t=2295848](http://ubuntuforums.org/showthread.php?t=2295848) 
[/LIST]

Now... My problem:
[LIST=1]
[*]I started the upgrade to Ubuntu 14.10, en route to 15.04.  The computer was freezing up randomly before that. (I thought an upgrade would fix that). 
[*]After completing the upgrade, the computer rebooted into a GRUB shell.  And now start all my problems as previously stated. 
[/LIST]

---

### Post by Bucky Ball on 2015-09-24
*Thread moved to **Installation and Upgrades**.*

Because ... your problem is that 14.10 is no longer supported. Dead. No repos, no upgrade. Unsure how it completed. You tried to upgrade to 14.10 and it has crashed the system and broken grub in the process by the looks of it. If we can get it booting, we might find a fine mess in there. Having said that, no harm in trying. Curious as to what you might find.

The best option in my opinion is to boot from live media> 'Try Ubuntu'> backup your valuable data to an external device> Clean install 15.04 which, incidentally, is an interim release which will die in January 2016. 14.04 LTS is supported until 2019 as it is a long-term support release.

Good luck with it. :)

PS: You could also try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Do the recommended repair and post a link to the bootinfo script output here. Thanks.

---

### Post by uninvolved on 2015-09-24
There is also the automated boot repair which has saved my bacon a couple of times. This can be found here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I doubt it will fix their underlying problem BUT it may enable them to boot into what's left of the OS.

---

### Post by nfmcclure on 2015-09-24
> 
There is also the automated boot repair which has saved my bacon a couple of times. This can be found here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I doubt it will fix their underlying problem BUT it may enable them to boot into what's left of the OS.


> 
PS: You could also try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Do the recommended repair and post a link to the bootinfo script output here. Thanks.


Thank you for the replies!

I was able to install boot repair from the command line I can get into.  But running 'boot-repair' results in this error:

```

user@computer:~$ boot-repair
Gtk-warning **: cannot open display:

```

Is there a way to run this via command line interface without a GUI?

---

### Post by uninvolved on 2015-09-24
Run it from the Live CD/DVD/USB.

---

### Post by Bucky Ball on 2015-09-24
You need to get into the same directory in the terminal as Boot Repair, then run 'boot-repair'. You can right click the Boot repair folder in the file manager and 'Open in a terminal'.

---

### Post by nfmcclure on 2015-09-25
> **uninvolved said:**
> Run it from the Live CD/DVD/USB.

Thank you all for the replies.  I did not know I had to do this via the live usb.  I did and got everything booted.  I'm running into more problems booting because I think I messed up my video card drivers.  That's a separate issue though.

---

### Post by Bucky Ball on 2015-09-25
> **nfmcclure said:**
> I did not know I had to do this via the live usb.

[You don't. ]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") You need to be in the correct directory when you run the boot-repair command, which it doesn't look like you were. :)

```
**user@computer:~**$ boot-repair
```

You probably needed to be in:

```
/home/user/Downloads/boot-repair
```

... or something close.

See post #6 and sorry to repeat myself, but ........................................

---

