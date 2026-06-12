---
title: "Dual boot Windows 10 + Ubuntu Gnome 15.10, no Windows grub option."
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by Cody_Balos on 2016-01-28
I know there has been quite a few posts on this, but I am running into the issue of the Windows boot entry in grub not existing.
[I]Hardware
[/I]Skylake build with [Asus H170 Pro Gaming mobo]("https://www.asus.com/us/Motherboards/H170-PRO-GAMING/"). 
[I]
Steps I Performed When Setting up Dual Boot and then Troubleshooting:[/I]
Had a Windows 10 install already up and running. So I proceeded like so:

1) Disabled Fastboot/Hibernation in Windows.
2) Disabled Fastboot in BIOS
3) Changed BIOS Secure boot option from "Windows UEFI" to "Other OS"
4) Booted to Ubuntu Gnome 15.10 Live USB
5) Began installation process
6) Windows was not detected, so I went with the option to manually setup the partitions
7) Created a swap partition, root ext4 partition, and ESP partition (596MB)
8) Installed
9) Restarted, grub didn't come up and the system went straight into Ubuntu, 
10) Ran "sudo update-grub"
11) Restarted again, still no grub, installed boot-repair, and ran it with recommended settings

At this point grub started loading now, but there is no windows option. So I continued:

12) Tried the suggestions from [this askubuntu post]("http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot"), which were to create the entry in grub
13) Restarted, tried my new entry, grub says it can't find the .efi file specified
14) Tried a few other possible entry settings I stumbled across but cannot remember exactly.
15) Ran boot-repair again, and got [this paste]("http://paste.ubuntu.com/14686712/")


*Other Information*
When I drop into the grub shell with the "c" command, and run the command "exit" the system boots into Windows instead of Ubuntu.

Any help is much appreciated.

---

### Post by Cody_Balos on 2016-01-28
Found a fix. Found a very useful askubuntu post right after I posted this ( I literally have been searching and hadn't found this for several hours, and somehow didn't find it until after this post).

If you drop in the grub shell and "ls" you will get a list of your disks, and then you can methodically "ls (hd0,gpt1)" "ls (hd0,gpt2)", etc. until you find the partition that has your windows bootloader on it. Then you can add a menu entry in grub (file to edit is /etc/grub.d/40_custom) like so:

menuentry "Windows 10" {
    set root='(hd0,gpt1)'
    chainloader [COLOR=#000000]/EFI/Microsoft/Boot/bootmgfw.efi[/COLOR]
}

---

