---
title: "No loginscreen after upgrade from 9.10 to 10.04"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by gartoffel on 2010-05-19
Hi everyone!

I recently upgraded our test server **from ubuntu 9.10 to 10.04 LTS** (both: amd64 server) using the CLI (sudo aptitude full-upgrade) **via RMM3 KVM** (Intels remote management module), which was always working properly with 9.10.
The upgrade was as easy as always and all the upgraded packages seemed to work fine. OK, let's reboot.

After rebooting I saw the "enter bios" screen, then the "enter hw-raid cli" and finally the boot messages up to:
```

[    4.428709] EXT4-fs (dm-1): mounted filesystem with ordered data mode
[    4.488918] usb 5-1: configuration #1 chosen from 1 choice
[    4.585765] igb 0000:01:00.1: Intel(R) Gigabit Ethernet Network Connection
[    4.585865] igb 0000:01:00.1: eth1: (PCIe:2.5Gb/s:Width x4) 00:15:17:da:dc:19
[    4.586038] igb 0000:01:00.1: eth1: PBA No: 1030ff-0ff
[    4.586130] igb 0000:01:00.1: Using MSI-X interrupts. 4 rx queue(s), 4 tx queue(s)
```
then **the screen went blank** (no cursor, no text) with a greenish background (I don't have to tell you that we have no KDE, Gnome or whatsoever installed on that machine. It's a simple CLI accessible server). I fixed the greenish background using "nomodeset noplymouth" in the grub boot settings, and tried several other options...
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset fb=false"
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth nomodeset fb=false"
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 fb=false"
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 fb=false noplymouth"
etc.
```
Source: [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

...but the screen remained blank, though not greenish anymore.

I was a bit shocked first, but let's be honest: it's a test server, so that's excatly what it's for :)
I did then access the machine via SSH which worked without any problems and started to do some research. I found out, that I just don't see what's happening on the screen, but **keystrokes still work** (tried to log in, tried to Ctrl-Alt-Del, everything works!).
Normally, one would say: Buy a new screen! :P
But hey, **this is a remote KVM session** and it worked up to the moment, where I upgraded to 10.04. So, that's not an argument. What I can't tell you yet is, if the problem only concerns the RMM3 KVM session or also the local tty. The server is located in a datacenter and I'd have to travel quite a bit to access it directly.

Let's summarize:
- Grub is loading the correct kernel
- Machine is booting properly
- Seconds before the login screen WOULD appear, the screen goes black and blank
- Keystrokes still work, just not displaying anything

Some other useful information:

lspci | grep VGA:
```

07:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)

```

cat /proc/cmdline:
```

BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-server root=/dev/mapper/lvm--group-system ro nomodeset noplymouth

```

Any help would be highly appreciated. Thank you!

---

### Post by marquivon on 2010-06-01
Hi - were you able to figure out the problem? I've spent all day doing it without any luck. I just bought a new server with Intel rmm3, and thought that I'll keep that in the data center and do all the installation etc. remotely.

However, in the initial testing that I'm doing, I'm not able to even get past the installation screen. I earlier tried vga=789 and other modes - these worked with Ubuntu 8.04, but not with 10.04 (probably because it is grub2). I tried to boot with Ubuntu 32bit Desktop, and it did show the "green" screen briefly, but then showed the Ubuntu desktop just fine.

---

### Post by Magnus1234 on 2010-06-02
I have exactly the same problem with Ubuntu 10.04 64bit server. The VGA card is the same.
I see the bios screen and the booting process through RMM3 until Ubuntu starting process. However when Ubuntu gets start the remote console gets blank (black or green color). The keyboard works because I can see it in the physical console monitor. I have tried all of the mentioned possibilities above.

Do you have any solution? It is quite important to make it work.

---

### Post by marquivon on 2010-06-02
I have not been able to figure it out yet. I downgraded to grub instead of grub2, but the issue persists. Putting vga=786 or vga=791 in the boot parameters, and using xforcevesa and i915.modeset=0 also didn't help.

---

### Post by marquivon on 2010-06-02
Well, considering the critcality of situation I'm in, I've to say goodbye to Ubuntu for this server. I'm moving on to Debian. I downloaded 8.5 MB mini.iso for amd64 from debian.org and the network install is in progress. It also didn't work out of the box, but providing vga=769 in the boot parameters worked well.

My primary purpose is using virtualization and kvm, and this guide will update me to the latest I guess, so I'm a bit happy. [http://aj.garcialagar.es/blog/virtualization-with-kvm-and-debian-lenny/](http://aj.garcialagar.es/blog/virtualization-with-kvm-and-debian-lenny/)

---

### Post by gartoffel on 2010-06-02
> **marquivon said:**
> Hi - were you able to figure out the problem?

Hi marquivon and Magnus1234

No, sorry. Even though we spent several days trying to fix this issue, the problem persists.
Funny thing is, that if you attach a display directly, everything works fine. I need to point out, that when connecting via RMM3, we can see the bootup process up to a certain extend and then, the screen goes black. But there has to be a solution somewhere...

Anybody?

---

### Post by Magnus1234 on 2010-11-03
Hi,

Is there any news about this problem?
I have tried to modify some grub settings however it does not help.

I think it should solve in server version somehow. Other case we have to replace Ubuntu with Debian.

---

### Post by hedermisi on 2011-09-08
Hello!

We had the same problem with an intel server equipped with console module. Setting kernel parameters like vga= did not help. 
Just as in the op's case the directly connected screen worked, but we saw a blank screen after a few seconds on the virtual console software. 

However the fact that it went away only in the middle of the booting process give us a clue. We figured out that the cause of the problem is the loading of the vga16fb module. 

So we added these lines into /etc/modprobe.d/blacklist-framebuffer.conf:

blacklist vga16fb
blacklist vgastate (but maybe this line is unnecessary)

and the problem went away.

Hope this helps someone!
Cheers!

---

