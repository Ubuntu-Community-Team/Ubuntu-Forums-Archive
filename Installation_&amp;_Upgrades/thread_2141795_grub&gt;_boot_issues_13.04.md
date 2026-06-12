---
title: "grub&gt; boot issues 13.04"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by GlennW on 2013-04-29
I'm hoping this is the right thread for this. I am attempting to install ubuntu 13.04 on my desktop system. Here's the skinny on my setup. I was originally running 11.04 on an 80 gb. After constantly running out of space I bought a 1 tb and installed 11.04 on it as well. I then ran off of it since it was considerably faster than the 80 gb hdd. However, at some point, something happened to grub. So, I simply reverted to booting from the 80 gb drive and then mounting the 1 tb whenever I wanted access to my media.

I recently purchased a 2 tb external drive to provide backup. Now I want to relegate the 80 gb hdd to the dustbin. I made a live usb with 13.04 but after trying to repair grub on the 1 tb drive, I can't get anything to boot from the usb. At the bios menu I select the appropriate choices to ensure that the usb is first in the boot order. But, as the system verifies the data pool, it goes to the grub prompt. This is on the 80 gb drive which was running fine. I can't even get past the grub prompt if I remove the live usb. The 1 tb drive goes to the grub rescue prompt.

I am at a complete loss. Yes, I need to repair the PC boot. But, I can't even get to a place where I can do that!

Thanks for your help on this.

---

### Post by GlennW on 2013-05-02
> **oldfred said:**
> @GlennW
Are you getting grub prompt before install or from live system or after install.

If after install did you run Boot-Repair?  If that does not work post link to BootInfo report from Boot-Repair.

When I turn the computer on or issue "reboot" from the grub prompt this is the order:

The light on the live usb flashes indicating that it's being accessed.
The monitor displays the BIOS info.
A bit more light flashing on the usb.
BIOS scrolls up and says that the Data Pool is being verified.
The grub prompt appears: grub>

That's it. I don't get the chance to do anything. I've verified from the mobo maker (Gigabtye) that my BIOS selections are correct to get the usb to boot first.

Thanks...

---

### Post by oldfred on 2013-05-02
If booting flash drive in UEFI mode it uses grub. In BIOS mode it uses syslinux.

So the grub on the flash drive is not correct. Which means either the download was not correct or it was not correctly installed to flash drive. You are using 64 bit version?

I might verify download with md5sum.
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
[/URL]
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by GlennW on 2013-05-03
> **oldfred said:**
> If booting flash drive in UEFI mode it uses grub. In BIOS mode it uses syslinux.

So the grub on the flash drive is not correct. Which means either the download was not correct or it was not correctly installed to flash drive. You are using 64 bit version?

I might verify download with md5sum.
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
[/URL]
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

@oldfred, the live usb in question boots quickly and cleanly in my laptop. I'm at a complete loss here...

Yes, it is 64-bit. Both my computers are 64-bit compatible.

---

### Post by oldfred on 2013-05-03
@GlennW
I missed that you said you have a Gigabyte board. Have you checked to make sure you have the lastest UEFI/BIOS. They recently posted a major update to many newer boards to convert from a minimal UEFI to a full UEFI. I found a page that listed many boards, but mine was too old, but did not save link.

So live installer boots, it is just your install that does not boot.
Then post a link to a new BootInfo report.

---

### Post by GlennW on 2013-05-03
> **oldfred said:**
> @GlennW
I missed that you said you have a Gigabyte board. Have you checked to make sure you have the lastest UEFI/BIOS. They recently posted a major update to many newer boards to convert from a minimal UEFI to a full UEFI. I found a page that listed many boards, but mine was too old, but did not save link.

So live installer boots, it is just your install that does not boot.
Then post a link to a new BootInfo report.

I don't mean to be obtuse, but what is a Bootinfo report and how do I obtain it?

---

### Post by oldfred on 2013-05-03
@GlennW
You are in the Boot-Repair thread so I thought you came here from running Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by GlennW on 2013-05-03
> **oldfred said:**
> @GlennW
You are in the Boot-Repair thread so I thought you came here from running Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

@oldfred. I apologize for being in the wrong thread. I appreciate the time you've put into attempting to help me. The issue is that the live usb is not booted into. It doesn't come up. There is no choice for me to make to be able to choose to run Boot-Repair. 

Here is a pic of the grub prompt that I've mentioned. This is as far as I can get. If there is a better thread for diagnosing this problem please direct me there.

[ATTACH=CONFIG]242140[/ATTACH]

---

### Post by oldfred on 2013-05-03
Moved to your own thread from Boot-Repair mega-thread.

That grub error looks like it is from your hard drive not liveCD.
I need more info to diagnose grub issues, so from liveCD or flash can you not boot? It has to be  first in boot order or use the one time boot key (f12 on my system) to choose live installer and boot it in live mode.

Then either run BootInfo report or Bootinfoscript. You have to download into your live system.

Some BIOS do not boot from large / (root) installs. Did you install with a large root? Is BIOS in LBA or AHCI but not IDE nor RAID?

---

### Post by GlennW on 2013-05-03
> **oldfred said:**
> Moved to your own thread from Boot-Repair mega-thread.

That grub error looks like it is from your hard drive not liveCD.
I need more info to diagnose grub issues, so from liveCD or flash can you not boot? It has to be  first in boot order or use the one time boot key (f12 on my system) to choose live installer and boot it in live mode.

Then either run BootInfo report or Bootinfoscript. You have to download into your live system.

Some BIOS do not boot from large / (root) installs. Did you install with a large root? Is BIOS in LBA or AHCI but not IDE nor RAID?

@oldfred. Being a linux noob and being persistent, I often accomplish stuff without knowing how. Speaking of which, I have managed to get to the boot menu. I don't know what it's called but the purple screen where I can choose which kernel to run or recovery mode, whatever. However, it will not continue to boot to the Ubuntu desktop. I think this is progress. Can something be done if I drop to the root shell with networking?

Need some serious help. All I want to do is to be able to get to the place where I can either reformat the whole drive from the terminal or from the desktop where GParted can be used.

Thanks.

---

### Post by oldfred on 2013-05-03
Does recovery mode work. It should be second entry or in the sub-menu.

Or what video card? Often nomodeset is required. You can press e on grub menu, scroll down to linux line and change splash quiet to nomodeset. Sometime other boot parameters are also required.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

