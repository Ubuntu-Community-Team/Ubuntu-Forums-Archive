---
title: "Anohter dual boot problem between windows 7 and ubuntu 12.10 in UEFI"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by gerpc on 2013-02-06
Hi,

I've installed a time ago a new machine. First I install windows 7 and the ubuntu 12.10 in EUFI mode. All work fine.

This week, my XFS partition crashed unexpectly. Then, as I haven't important files already, I decided to reinstall my ubuntu. I've done the next steps:

1- Boot with a booteable USB stick
2- Format /dev/sda1 (EFI partition) and /dev/sda2 (root partition).
3- After reinstall and boot, windows dissapeared from my grub menu!

I've tried adding the entry to 40_custom grub configuration file

```

menuentry "Windows (UEFI)" {
 search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
 chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

Now I can see an entry, but, if I select it, nothing happend

I've try using boot-repair, and nothing.

This is my boot-repair report: [http://paste.ubuntu.com/1618129/]("http://paste.ubuntu.com/1618129/")

If someone could help me, I'll be grateful

German.-

---

### Post by oldfred on 2013-02-06
Both Windows & Ubuntu use the same efi partition for boot files. So if you reformated the efi partition you deleted the Windows boot files. But it looks like they are restored?

Windows also has several partitions that it wants and one that it must have that you must have deleted. You need the system reserved with the Microsoft gpt code. And it is not formatted. It must be just before the main install.
I think it is like the area after the MBR where Microsoft and DRM or virus software writes serial numbers or other hidden data.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

