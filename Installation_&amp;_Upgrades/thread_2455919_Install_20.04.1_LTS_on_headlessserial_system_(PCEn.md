---
title: "Install 20.04.1 LTS on headless/serial system (PCEngines APU)"
date: 2020-12-30
forum: Installation &amp; Upgrades
---

### Post by etrask on 2020-12-30
Hello all

I am having a hell of a time getting the Ubuntu Server LTS installer to work, on a PCEngines APU box. This box has no graphical output at all, only serial and network.

My ultimate goal is to have a bare bones server LTS install, running LXD. I'll administer the system over SSH, and run a few services inside LXD containers, and leave the bare metal system relatively "vanilla."

I used to do this quite easily with Debian and LXC, but it's become cumbersome there too. I'm hoping Ubuntu/LXD will be easier... if I can get the dang thing installed!

My process:
I've written ubuntu-20.04.1-live-server-amd64.iso to a bootable USB.

Insert the USB into the APU box, and have PuTTY connected to the box via console cable (115200n8).

Boot from the USB. I immediately (as I would expect) get an error about gfxboot not working that leaves this on screen:
[IMG]https://i.imgur.com/9t92lpQ.png[/IMG]
(console wrapped around, so it's a bit messy. Relevant bits at top)


A blinking cursor implies it wants input. If I do nothing, this loops. I type "help" and it brings me to a text-based installer help:
[IMG]https://i.imgur.com/SqafFex.png[/IMG]
On this page, it will give me about 1 second before the installer does... something... and stops accepting input (notice the cursor moved down a line). If I interrupt it and press Fx to read help files, it will let me actually enter boot commands, however none of them work:
[IMG]https://i.imgur.com/z8JgNFE.png[/IMG]
Nothing I enter on this screen works. I will get a "failed: No such file or directory" regardless of what I input.

I have this machine being issued a DHCP reservation, so it gets the same IP no matter what OS is running, etc. I have noticed that if I let the installer sit, an open SSH port appears on its IP after a minute or two. I presume this is an SSH server running ON the Ubuntu installer, though for the life of me I cannot find any login info for this. I'm not even sure it would help me. At that point the console has become useless to me.

I feel I'm missing something obvious here. I've searched the forums, and the internet in general, but answers to this have eluded me. Any help would be appreciated!

Thank you for your time.

---

### Post by TheFu on 2020-12-30
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
That's the issue.  To my knowledge, all Ubuntu distros require some graphics.  You might check the "Alternative Installer", perhaps it is serial-ready?

I doubt Ubuntu Server is any easier than Debian.  It is certainly more bloated. Of that, I'm certain.  Canonical only distributes LXD as a snap on all platforms now.

LXD should work on any modern 64-bit Linux distro.

BTW, I run an APU2 with OPNSense for my router.

---

### Post by etrask on 2020-12-30
Thank you for the link. I did see this before. Unfortunately, it operates under the assumption that Ubuntu is already installed on your system, and you just need to configure some pieces of software to work on the console.

I can't even get an installation going :(

---

### Post by TheFu on 2020-12-30
[https://wiki.polaire.nl/doku.php?id=apu_ubuntu](https://wiki.polaire.nl/doku.php?id=apu_ubuntu)  is for an apu2.  Seems other APU models ave different needs.

> Install Ubuntu 18.04

    dd Ubuntu server netinstall (mini.iso) to USB drive [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads), be sure to select the amd64 arch.
    Connect the USB drive to the APU2 board and boot from USB, press F10 at boot.
    Select Install, then TAB.
    Change kernel options to linux initrd=initrd.gz console=ttyS0,115200
    When asked to unmount mounted partitions choose Yes.
    Install options as you like.
    Reboot after install.

Post installation steps
GRUB

    At the grub menu, press 'e'.
    Scroll to the line starting with linux and add:

    console=ttyS0,115200n8

    Then press 'ctrl-x' to boot.
    You can now log in with your user account.
    Modify grub:

    sudo vi /etc/default/grub
    GRUB_CMDLINE_LINUX="console=ttyS0,115200n8"

    sudo update-grub

    Reboot to test the update grub configuration.

Networking

    Edit /etc/netplan/01-netcfg.yaml

    # This file describes the network interfaces available on your system
    # For more information, see netplan(5).
    network:
      version: 2
      renderer: networkd
      ethernets:
        enp1s0:
          addresses:
            - 10.10.10.2/24
          gateway4: 10.10.10.1
          nameservers:
              search: [mydomain, otherdomain]
              addresses: [10.10.10.1, 1.1.1.1]

    Apply config:

    netplan apply

---

### Post by etrask on 2020-12-30
Ah, the netinstall ISO. As you suggested :P

Let me give that a shot and I will report back w/ findings.

Thank you for your patience and help!

---

### Post by TheFu on 2020-12-30
APU or APU2 or some other model?  They have a bunch these days.

---

### Post by etrask on 2020-12-30
APU2 I think. 3 NICs, 4gb RAM, 4-core AMD something-or-other CPU. Sorry, not sure the exact model name, but it's the "current" model, I believe.

As for netboot: no go. Turns out they don't even roll an alternate/netinst ISO anymore, which is truly baffling. Guess it's back to Debian for me.

---

### Post by QIII on 2020-12-30
> **etrask said:**
> Sorry, not sure the exact model name, but it's the "current" model, I believe.

Unfortunately, there is not a single "current" model, but dozens.  It might be helpful if you were able to provide a less nebulous description.

---

### Post by TheFu on 2020-12-31
APU2 is **not** the current model.  With all these things, correct details matter.

Last time I looked, PCEngines had an entire "how-to" for using TinyCore to bootstrap other OS installers.

Debian is the easy answer. I wouldn't waste an APUx on LXD myself.  These things are pretty good at doing network routing. If you don't have a good, supported, router today, that is where I'd put my effort.  Especially if using some consumer router that will become unsupported next year, like almost all of them are.  I have a number of problems with most consumer routers and poor security. 

They loose support much to quickly. Whereas my APU2 with OPNSense will likely be supported for 10 yrs. Plus, I prefer having all wifi outside my secured LANs. I don't trust any RF networking to be secure, especially from wifi-routers that aren't patched at least monthly.

---

### Post by etrask on 2020-12-31
[This]("https://pcengines.ch/apu2e4.htm") is the guy I'm using. I consider it modern enough -- the only difference I can discern between this and the APU3 models is the slightly different NIC configuration.

I agree with you re: routers. I have a number of these boxes: one acting as my router, one acting as the router at my father's house, both running pfSense and connected via VPN.
The one I'm playing with, running Debian.

And another doing nothing at all right now.

Anyway, last night I was able to get LXC working on Debian 10.

Thank you for your patience and assistance here.

---

### Post by shokinn on 2021-01-14
Hi @etrask,
I managed to install 20.04 to my APU2.

Here is a short HowTo:
1. Create a Bootable USB stick with TinyCore Linux: [https://pcengines.ch/howto.htm#TinyCoreLinux](https://pcengines.ch/howto.htm#TinyCoreLinux)
2. Create a directory "ubuntu20_04" on that newly created Stick
3. Download the netboot.tar.gz for 20.04: [https://wiki.ubuntuusers.de/Downloads/Netzwerkinstallation/](https://wiki.ubuntuusers.de/Downloads/Netzwerkinstallation/)
4. Extract the "initrd.gz" and "linux" files from the archive on the newly created USB-Stick to the directory ubuntu20_04
5. Edit the "syslinux.cfg" (it's on the main directory of the stick); add the following lines below of the tinyCore configuration block.
```

LABEL Ubuntu_20_04_netboot
    MENU LABEL ^Ubuntu 20.04 LTS (Netboot)
    KERNEL /ubuntu20_04/linux
    INITRD /ubuntu20_04/initrd.gz
    append priority=low root=/dev/ram0 ramdisk_size=1500000 ethdevice-timeout=30 ip=dhcp url=http://cdimage.ubuntu.com/ubuntu-server/focal/daily-live/current/focal-live-server-amd64.iso vga=off console=ttyS0,115200n8

```
6. Save it; Eject the usb stick
7. Be sure you have working internet/network/dhcp 
8. Boot the Stick on your APU choose the Ubuntu 20.04 entry.


Post setup:
Since I'm lazy and I already wrote documentation for myself in Markdown, here is it:
```

### Grub tweaking

Edit `/etc/default/grub`:  
```
[...]
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200,n8"
[...]
GRUB_GFXPAYLOAD_LINUX="keep"
[...]
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1"
[...]
```

Update grub with:  
`sudo update-grub2`

```

Hope this will help
ShokiNN

---

### Post by silexh on 2021-03-08
I found this thread looking for instructions on how to install 20.04 on an APU because I encountered the same issue as OP. However, it looks like the 'old' instructions (as described [here]("https://blog.dbrgn.ch/2019/10/5/booting-installing-debian-on-apu2/") and [here]("https://xinau.ch/notes/ubuntu-installation-on-apu-board/")) still work if you find the mini.iso:

[LIST=1]
[*] Download the mini.iso from any [Ubuntu mirror]("https://launchpad.net/ubuntu/+mirror/ftp.snt.utwente.nl-archive"). It can be found under [dists/focal/main/installer-amd64/current/legacy-images/netboot]("https://ftp.snt.utwente.nl/pub/linux/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/").
[*] Select *Install*, press *Tab* and update the command line with `vga=off` and  `console=ttyS0,115200u8`, eg:
     ```
linux vga=off initrd=initrd.gz --- quiet console=ttyS0,115200u8
```
[*] Press *Enter* and follow the installation instructions.
[/LIST]

---

### Post by technophiliac on 2021-12-16
I've just figured out and successfully installed ubuntu server 20.04.3 on a PC Engines apu3b4 board with m-SSD.
1) I installed a standard server 64 bit image (ubuntu-20.04.3-live-server-amd64.iso) onto a USB drive using RUFUS on Windows 10.
2) using programmers notepad comment out last line in E:\isolinux\isolinux.cfg to:
#ui gfxboot bootlogo
(and save...)
3) Revise beginning lines of E:\isolinux\txt.cfg to:
default live
label live
  menu label ^Install Ubuntu Server
  kernel /casper/vmlinuz
  append   initrd=/casper/initrd quiet vga=off console=ttyS0,115200n8 ---
etc....
4) Plug in USB drive to board with DHCP LAN connected, and power up, and install (initially using serial null modem cable / putty) and of course install openssh when offered.
5) Much easier than figuring this all out! No need to worry about time outs, pressing TAB to input the serial specs, its all done and the install will run by default. SOme waiting is required when it might tease you its doing nothing. Be Patient and you will be pleased with yourself!
It now can be run from the serial terminal via the cable or SSH. Nice.
Hope it helps someone else(s)
I do note I get this:
Message from syslogd@[NAME] at Dec 16 09:20:07 ...
 kernel:[ 2185.196053] [Hardware Error]: Corrected error, no action required.

Message from syslogd@[NAME] at Dec 16 09:20:07 ...
 kernel:[ 2185.202339] [Hardware Error]: CPU:2 (16:30:1) MC1_STATUS[-|CE|-|AddrV|-|-|-]: 0x9400000000000012

Message from syslogd@[NAME] at Dec 16 09:20:07 ...
 kernel:[ 2185.211228] [Hardware Error]: Error Addr: 0x00007f769ff621d0

Message from syslogd@[NAME] at Dec 16 09:20:07 ...
 kernel:[ 2185.216938] [Hardware Error]: MC1 Error: L2 TLB parity error.

Message from syslogd@[NAME] at Dec 16 09:20:07 ...
 kernel:[ 2185.222787] [Hardware Error]: cache level: L2, tx: INSN
Not sure what that's about? Anyone?

---

