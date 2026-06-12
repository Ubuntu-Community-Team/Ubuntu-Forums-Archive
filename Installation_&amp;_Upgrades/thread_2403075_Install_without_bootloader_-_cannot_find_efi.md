---
title: "Install without bootloader - cannot find efi"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by kaprikawn on 2018-10-07
I've installed Ubuntu by going into a LiveCD, opening a terminal and running
```
ubiquity -b
```
and then running the install process from there.  The reason is I already have an Arch install on my machine and I want to manage boots using systemd-boot from my Arch install as it's my primary distro (and I vehemently dislike Grub and don't want it on my system).  The -b parameter is for not installing a bootloader which is what I want.

I used the 'Something else' option for where to install to and selected a partition that I had already created for the Ubuntu install for the root directory.  I made no other mount options.

The Ubuntu install recognized that I had a EFI partition and has placed some directories and files in there during the install process, I have

```

/boot/EFI/BOOT/BOOTX64.EFI
/boot/EFI/ubuntu/fwupx64.efi

```

These are on my EFI partition which is on a separate disk to my Ubuntu install.  However, when I point systemd-boot to use either of these, it doesn't boot into Ubuntu, I think this is correct because I don't think either of these point to my Ubuntu install.  From what I remember from previous Ubuntu installs and by my research today, I'd expect to have a file

```

/boot/EFI/ubuntu/grubx64.efi

```

and this is what I would have to point systemd-boot to in order to boot Ubuntu.  But because I chose the no bootloader option, Ubiquity doesn't seem to have created it.

I'd appreciate it if someone could advise me how I can get Ubuntu booted without having to install a bootloader in a way that allows me to boot from systemd-boot.

---

### Post by oldfred on 2018-10-07
You would have to install grub to have the grub & shim .efi boot files in ESP.

But the reason for -b option is that you will manually add or os-prober will find kernel and add direct boot of Ubuntu from your other system.

I think the user that posted this, uses Arch to boot and adds entries to boot Ubuntu.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen) 

I have used device settings until recently to boot my other test installs of Ubuntu from working install. But often now have flash drive plugged in and my device order changes on reboot.
So I am in process of  converting to labels.

      
 [https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/3](https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/3)
search --no-floppy --fs-uuid --set=root <uuid>
search --fs-uuid --no-floppy --set=root FD76-E33D
search --no-floppy --label --set=root <label>
search --no-floppy --file --set=root <file> 
  
  The syntax can be -u, -l and -f
and search.fs_uuid search.fs_label search.file are aliases for the commands.
and &#8216;set&#8217; if unspecified is for setting as root 
   So this line is similar to our familiar first line above.
search.fs_uuid xxxxxxxxxxxxxxxxxxxxxxxx root
[https://www.gnu.org/software/grub/manual/grub/html_node/search.html](https://www.gnu.org/software/grub/manual/grub/html_node/search.html)
Command: search [--file|--label|--fs-uuid] [--set [var]] [--no-floppy] name
 The default variable is &#8216;root&#8217;.  
    
This thread by cavsfan has lots of examples.
In that thread, I posted some configfile & label examples.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

