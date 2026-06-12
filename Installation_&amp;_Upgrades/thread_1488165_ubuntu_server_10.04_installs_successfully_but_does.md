---
title: "ubuntu server 10.04 installs successfully but does not boot upon reboot..."
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by db654 on 2010-05-19
Hey ladies & gents,

Recently I have built an old pc using bits and bobs that have been collecting in the garage for years and decided to try and turn it into a file server, and to get some experience in networking etc. Now I had a choice of 2 motherboards for the system:
1.)gigabyte ga-8siml
2.)elitegroup l7s7a2
I first built the pc using the gigabyte board,install was successful and ubuntu server booted on restart. The only problem was,there is no onboard lan on the board and the only spare wireless pci card I found was completely frazzled. Rather than buying a new wifi card to get the system running, I thought I would try the other motherboard since this had onboard lan.  The elitegroup motherboard however does not have onboard vga, so I dug out an old agp ati radeon 9200se 128m ddr tvo graphics card and plugged her in. The install went fine,but after a restart, I'm left with a blinking cursor at the top left of the screen. If I hold down 'shift' for long enough I can bring up the grub menu,but if I select anything I get no signal on the monitor. After a while on the blinking cursor screen the monitor will time out to no signal on its own. I have tried the installation using different combinations of the options given by F6 of the first installation screen but to no avail. I have also tried installing the generic kernel as opposed to the generic-pae.

Looking around on the net tonight it looks as though its a problem with the graphics card. Has anyone got any suggestions on things I can try to get ubuntu server to boot?

Appologies if this thread is in the wrong place and also if it doesn't read well; I'm typing this from my phone :)

Thanks in advance

---

### Post by darkod on 2010-05-19
I don't have experience with the server version, but the blinking cursor on the desktop also means grub can't continue, it's not looking at the right place for the config files.

One possibility: The initial install worked fine. The second install reformatted everything but grub on the MBR is sometimes not overwritten and the old one is looking for the previous config files.

A quick test would be to plug the hdd into a PC, use Gparted to delete all partition, AND ALSO run some command to destroy grub on the mbr.

For example, if the hdd is added as /dev/sdb on another PC, you can overwrite grub with:

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

You could also reinstall grub, if you can get to a recovery mode. I have no experience with server, but on the desktop you need to start hitting Shift on boot to get the grub menu, and select the recovery mode. Provided it gets that far.

If you can get that far, reinstall grub to your disk which is probably /dev/sda.

On another note, I wonder if using the desktop liveCD would work just to add grub??? Boot into live mode, mount the root partition (depending which partition it is, and reinstall grub2). Something like:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by db654 on 2010-05-20
Thanks for the suggestions, I will give them a go tonight after work and let you know how I get on.

If I select recovery mode from the grub menu the monitor basically goes to no signal, but using the install cd I am able to access a recovery mode and mount the root partition

---

### Post by db654 on 2010-05-20
I have just reinstalled grub, but I'm still stuck at the blinking cursor when I try and boot up. 

Is this issue potentially due to a graphics driver?

---

### Post by unipsycho on 2010-12-27
I have a nearly identical problem with my old desktop.

Install works. Reboot fails. Left with a blinking cursor prior to grub.

Just wondered if you have found an answer.

---

