---
title: "Failed to open \EFI\UBUNTU\grubx64.efi error - but PC eventually boots"
date: 2022-10-08
forum: Installation &amp; Upgrades
---

### Post by chabekah on 2022-10-08
Hi folks,

I have actually had this problem for several years, but am fed up waiting the extra 3-6 seconds on every boot-up for this error to clear so would like to solve it.

This is what I see:

```
failed to open \EFI\UBUNTU\grubx64.efi
failed to load image \EFI\UBUNTU\grubx64.efi
start_image() not found
```


I have read several threads on the forums/stack overflow, tried to copy various grubx64.efi files into locations that I *think* are correct, changed the casing of various efi/EFI/ubuntu/UBUNTU folders, and tried to understand the output of efibootmgr. All to no avail...

Here is pastebin from the last time I ran boot-repair: [https://paste.ubuntu.com/p/zM7tbY8RYj](https://paste.ubuntu.com/p/zM7tbY8RYj)

I have been using this install of ubuntu (after various upgrades, currently on 22.04) for many years, and can only assume something got screwed up in an upgrade somewhere. It's windows dual boot.

I am not a linux noob, but equally I am not a linux geek - so easy on the acronyms please! Many thanks.

---

### Post by oldfred on 2022-10-08
You show two ESP, each with Windows & Ubuntu boot entries.
But you have three  Ubuntu entries & one looks for partUUID that does not exist. And that seems to be set as default boot. New install should have overwritten that entry.

You can see it here, which is in Boot-Repair report.  Compare partUUID in UEFI entry with partUUID of ESPs.
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by chabekah on 2022-10-09
OK, that is helping me to understand the output of efibootmgr.

To make sure I fully understand this before deleting something from the boot system (and potentially causing me more grief) can I just confirm what I think you are saying?

From efibootmgr -v we have this line:

BootOrder: 001D,001C,0000,0017,001E,0012,000B

So, the first item my system is trying 001D - but when you looked at the PartUUIDs of the blocks on my system, you didn't see the PartUUID that 001D refers to. And so if it is looking for grubx64 on a disk that doesn't exist, no surprise that it doesn't find it, and then goes to the next thing on the list 001C - which does exist, and does have the required files on it, and therefore boots succcessfully.

Therefore, you are recommending that I use a command like efibootmgr -b 001D -B to try and delete this bogus boot entry. I guess I could also use the -o (change order command) to try and set 001C to boot first if I was nervous about deleting something. Have I got that more or less right? BTW, is it a problem to have more than one EFI System Partitions? I suspect not, but I just thought I'd ask.

I had read the man pages for efibootmgr before, but because I didn't really understand what I was doing (and crucially hadn't spotted that one of the partitions was missing), I was a little nervous to try something...Thanks so much for your help.

---

### Post by oldfred on 2022-10-10
Yes you can change boot order first. Probably safer, in your case.

You can use efibootmgr to create new UEFI boot entries if you delete wrong one.
Or just use Boot-Repair and the Advanced mode to do a total reinstall of grub which resets UEFI (it uses efibootmgr) and update /EFI/ubuntu entry. With advanced mode you do chose which install, if you have more than one, as then that will be the default.

I have tried adding multiple UEFI entries for my multiple Ubuntu installs, but something in Ubuntu's version of efi boot files is hard coded to /EFI/ubuntu/grub.cfg. So even when I create a new entry called "jammy" it appears as a separate UEFI entry, but still boots default.

---

### Post by chabekah on 2022-10-11
I changed the boot order and it all seems to have booted in the normal way - but without that annoying message at the start. Many thanks for your patience and clear explanation.

---

