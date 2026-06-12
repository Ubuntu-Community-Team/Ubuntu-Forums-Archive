---
title: "Help with GRUB after Ubuntu Installation"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by tvianna2010 on 2010-11-17
Hey Guys,

I'm fairly new at this stuff, so this may seem simple. I just installed Ubuntu on a partition of my partitioned hard drive (sda2). I have windows 7 installed on this hard drive as well (sda5). When I start up the computer, Grub does not show any option for windows 7. I don't believe os prober is finding it. How can I make Grub boot to Windows 7 as well?

Thanks for the help!!

-Tomas

---

### Post by oldfred on 2010-11-17
Welcome to the forums.

Windows does not work from logical partitions. Did you have another install of windows in a primary partition? Second installs of windows will move boot files to the first install. If the second install is on a primary partition it can be repaired. With win7 it is just about impossible. I have seen some of the users here make it work with XP although windows does not support it.

If you create a primary NTFS partition, you may be able to install windows there and get that to boot your other install. I do not know. How vital is your windows install. You can copy data with Ubuntu from it, if you do not have a good backup. In some cases I have seen partition table directly rewritten to convert a logical partition to a primary but it depends greatly on how your partitons are laid out now.

---

### Post by oldfred on 2010-11-18
What ever your do you need really good backups as any major edits can cause you to totally reinstall. And the easiest way for most users is to just reinstall win7 in a primary partition.

How willing are you to directly edit partition tables? 

Or you may be able to directly copy the partition and run windows repairs to try to may it work.

To even know what may be possible post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

