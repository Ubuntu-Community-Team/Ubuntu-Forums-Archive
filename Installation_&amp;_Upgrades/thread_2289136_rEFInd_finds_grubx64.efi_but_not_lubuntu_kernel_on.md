---
title: "rEFInd finds grubx64.efi but not lubuntu kernel on partition"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by Marnick_LEau on 2015-08-01
Hi

I'm trying to get refind to boot the lubuntu kernel directly  instead of maintaining the manual config and using grub in between. For  some reason though, refind only finds the grubx64.efi file (on the ESP),  but never the kernel files (on lubuntu's own partition). I have a  virtualbox set up with refind and arch installed, where refind does find  the arch kernel direcly. Its configuration is the same so I don't know  why detecting the kernel doesn't work on the real machine.

Uefi, gpt disks, secure boot off. File permissions are the same, drivers for the filesystems are installed (btrfs).

[B]File details

Arch virtualbox

[/B]/boot: [http://i.imgur.com/8VEfANv.png](http://i.imgur.com/8VEfANv.png)

refind_linux.conf:
"Boot with standard options"        "rw root=UUID=ab4286d4-fe06-453a-8bdf-0b52f53639ee   "
"Boot to single-user mode"          "rw root=UUID=ab4286d4-fe06-453a-8bdf-0b52f53639ee   single"
"Boot with minimal options"         "rw root=UUID=ab4286d4-fe06-453a-8bdf-0b52f53639ee"

refind.conf:
scanfor internal
also_scan_dirs boot

[B]Win8/Lubuntu dualboot real machine
[/B]/boot: [http://i.imgur.com/uUKu7DH.png](http://i.imgur.com/uUKu7DH.png)

refind_linux.conf:
"default"    "rw root=UUID=d1570108-1546-4109-ba6c-5bb35b71c20b" #uuid from gparted for /

refind.conf:
#graphics omitted

use_graphics_for linux, windows, osx, grub
scanfor internal
also_scan_dirs boot
scan_all_linux_kernels 1

#backup
menuentry Windows {
    loader /EFI/Microsoft/Boot/bootmgfw.efi
    icon /EFI/refind/icons2/os_win8.png
}

menuentry Lubuntu {
    loader /EFI/ubuntu/grubx64.efi
    icon /EFI/refind/icons2/os_lubuntu.png
}

Any help in finding out why lubuntu kernels don't show up directly under refind would be much appreciated :)

---

### Post by oldfred on 2015-08-01
Are you sure Arch does not have copies of the kernels in the ESP?

[http://www.rodsbooks.com/efi-bootloaders/refind.html](http://www.rodsbooks.com/efi-bootloaders/refind.html)
Your kernels must reside in the root directory, in a subdirectory of     the EFI directory, or in the boot directory of any     partition that rEFInd can read&#8212;the ESP and **perhaps** other     partitions.
Perhaps default search in rEFInd is different between Arch & Ubuntu?

Thread asking about gummiboot which was another alternative.
[http://ubuntuforums.org/showthread.php?t=2288885](http://ubuntuforums.org/showthread.php?t=2288885)

---

### Post by Marnick_LEau on 2015-08-01
> **oldfred said:**
> Are you sure Arch does not have copies of the kernels in the ESP?

[http://www.rodsbooks.com/efi-bootloaders/refind.html](http://www.rodsbooks.com/efi-bootloaders/refind.html)
Your kernels must reside in the root directory, in a subdirectory of     the EFI directory, or in the boot directory of any     partition that rEFInd can read—the ESP and **perhaps** other     partitions.
Perhaps default search in rEFInd is different between Arch & Ubuntu?

Thread asking about gummiboot which was another alternative.
[http://ubuntuforums.org/showthread.php?t=2288885](http://ubuntuforums.org/showthread.php?t=2288885)

Fairly sure there are no copies in the ESP. There's literally nothing in there besides refind itself.

In virtualbox and on the real machine the discs are both GPT, have the same filesystem under /, same file structure (kernel in /boot). According to what I can read in that chapter, all of it adds up. I tried using the also_scan_dirs volume:/boot (with volume=the label of lubuntu's partition) syntax too but it did nothing.

That thread doesn't reveal much new...

---

### Post by oldfred on 2015-08-01
I prefer our forum, but the author of rEFInd - Rod Smith does post in askUbuntu. If  you make title something related to rEFInd, he probably will post.

---

### Post by Marnick_LEau on 2015-08-01
> **oldfred said:**
> I prefer our forum, but the author of rEFInd - Rod Smith does post in askUbuntu. If  you make title something related to rEFInd, he probably will post.

The first word is literally refind?

---

### Post by oldfred on 2015-08-01
So use same title in AskUbuntu.
Just wanted to make sure you did not change it to something without rEFInd.

---

### Post by Marnick_LEau on 2015-08-01
> **oldfred said:**
> So use same title in AskUbuntu.
Just wanted to make sure you did not change it to something without rEFInd.

Oooh right this isn't askubuntu...

I'm not into the linux ecosystem much at all, sorry

---

### Post by oldfred on 2015-08-01
Major issue was btrfs and several settings in rEFInd.

Solution here:
 [http://askubuntu.com/questions/655440/refind-cant-find-lubuntu-kernel-on-lubuntu-partition](http://askubuntu.com/questions/655440/refind-cant-find-lubuntu-kernel-on-lubuntu-partition)

---

