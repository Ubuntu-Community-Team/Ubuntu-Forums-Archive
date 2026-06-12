---
title: "Ubuntu Boot Repair Doesn't Appear Event After Boot Repair"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by urocks on 2013-02-22
Hi,

I had Windows 7 already installed. I then installed Ubuntu 12.10 64 bit version. However Ubuntu boot menu didn't appear and I then used Boot Repair (via Ubuntu Secure Remix: [http://sourceforge.net/p/ubuntu-secured/home/Home/](http://sourceforge.net/p/ubuntu-secured/home/Home/)).

Following was the repair note for the first time.
[http://paste.ubuntu.com/1703213/](http://paste.ubuntu.com/1703213/)

Though the Repair software said it was successful, no menu appeared and Windows loaded directly at reboot.

I then tried the Repair for the second time. Following was the note.
[http://paste.ubuntu.com/1703379/](http://paste.ubuntu.com/1703379/)

Still no luck.

In both cases, I tried Recommended repair. Should I try advance options? If so what to try (Restore MBR?)?

I couldn't find a detailed guide. Following was the best I could find and it had only screen shots of advance options.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

FYI: Both Ubuntu installation and Repair were carried out with a USB stick.

Any help is much appreciated.

Thanks in advance...

---

### Post by dino99 on 2013-02-22
is the ubuntu partition  set with the "boot" flag ?
is grub installed on /dev/sda ?

boot on a livecd to start gparted, and set the boot flag

then:
sudo grub-install /dev/sda
sudo update-grub

---

### Post by oldfred on 2013-02-22
Actually boot flag should only be on Windows boot partition usually sda1. Otherwise Windows will not boot with Windows boot loader.

And grub does not use boot flag, but a few BIOS need to see a boot flag on a primary partition (assumes Windows?).

Try dino99's suggestion on reinstalling grub to MBR of sda.

Links to pastebin are not working. But I tried one I had and it is not working either, so it looks like pastebin error.

---

### Post by urocks on 2013-02-24
Hi dino99 and oldfred,

Thanks for the info and sorry about the delayed reply.

@dino99

I think the grub is installed in /dev/sda since it's the default option mentioned in Ubuntu installer (I didn't change it). I am not sure about the boot flag. I will check that and let you know.

@oldfred

Following is how partitions were.

```

/dev/sda1   ntfs            104MB
/dev/sda2   ntfs            328512MB
/dev/sda3   ntfs            483183MB
/dev/sda5   ext4    /       40959MB
/dev/sda6   ext4    /var    30719MB
/dev/sda7   ext4    /home   89999MB
/dev/sda8   swap            6318MB

```

I guess /dev/sda1 is the MBR. I will try dino99's instructions. If it didn't work, I will try to re-install Ubuntu. 

When re installing, shall I choose /dev/sda1 one for installing the Grub? Will that erase Windows boot loader? 

There is an option called "Restore MBR" in Boot Repair. If I try that, will it erase Windows boot loader? 

My problem is, if Windows boot loader is erased, there won't be an option to access Windows.

Thank you

---

### Post by oldfred on 2013-02-24
NEVER install grub to a NTFS partition like sda1. Windows has vital boot info in the PBR partition boot sector which is just the first sector of a partition and used only for windows boot code in NTFS.

The MBR is just the first sector of the hard drive and is not part of any partition. So you install grub to sda or the MBR of the drive.

If you want a gui to fix things, you can download this into your liveCD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by urocks on 2013-02-24
Hi oldfred,

I followed the instructions. Following is the boot info output. I have also attached a doc file.

[http://paste.ubuntu.com/5563616/](http://paste.ubuntu.com/5563616/)

---

### Post by presence1960 on 2013-02-24
GRUB is not installed in the MBR of sda, Windows is. Boot the Ubuntu Live CD/USB, try ubuntu without installing. When desktop loads open terminal and run ```
sudo mount /dev/sda5 /mnt
```

next run this in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and you should be good to go.

---

### Post by urocks on 2013-02-24
Hi presence1960,

Thanks a lot for the help!

I tried your instructions and now the dual booting works.

I got following output (error) when I run "sudo grub-install --root-directory=/mnt/ /dev/sda"

```

/usr/sbin/grub-bios-setup: warning: this LDM has no Embedding Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

```

Despite the error it worked. I had a Windows boot menu created with EasyBCD. So that menu loads first and there I have to choose Ubuntu. I have no problem with that :-). I actually set Ubuntu as the first choice so it automatically loads.

Thanks all for spending the time on the issue. I had wasted lot of time on dual booting and didn't want to give up. ):P

---

### Post by presence1960 on 2013-02-24
Glad it worked! Enjoy. Was not aware you used Easy BCD. I don't think you mentioned that.

---

### Post by urocks on 2013-02-24
Sorry I couldn't mention about EasyBCD. Since I was having issues with the Ubuntu boot loader, I also tried Windows way.

---

### Post by oldfred on 2013-02-25
The LDM error is a bug with the new grub2 2.00. It now seems to recognize dynamic Windows partitions, but Linux still does not work with them. 

So if you have or had dynamic partitions meta data is left on the hard drive and grub sees that.

       ldm bug grub2 2.00
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

