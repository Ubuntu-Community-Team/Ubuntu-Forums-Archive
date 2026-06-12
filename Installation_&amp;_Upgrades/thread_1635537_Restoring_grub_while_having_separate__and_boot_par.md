---
title: "Restoring grub while having separate / and /boot partitions!?"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by TheChaos0 on 2010-12-01
Ok, so I was in need to install XP on top of my Seven and Ubuntu installs, afterwards as expected I lost grub.

Now I tried to get it back using the obvious method of using live cd and grub-install --root-directory=/mnt /dev/sda

The only problem is / and /boot are actually 2 separate partitions. Here are my partitions, where sda5 is /boot and sda6 is /. I don't actually know what to do now :lolflag: Help. :)

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2613    20988891    7  HPFS/NTFS
/dev/sda2            2614        3952    10755517+   7  HPFS/NTFS
/dev/sda3            3953        8796    38909430    5  Extended
/dev/sda4            5292        8796    28153881   83  Linux
/dev/sda5            3953        3965      104359+  83  Linux
/dev/sda6            3966        5291    10651063+  83  Linux

```

---

### Post by oldfred on 2010-12-02
You also have to mount the /boot partition as part of the grub reinstall. Many posts do not include that as having a separate /boot for standard desktops is not required nor preferred. Some just have it as a foot note like this one:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If separate /boot
 sudo mount /dev/sda6 /mnt
 sudo mount /dev/sda5 /mnt/boot
  sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by TheChaos0 on 2010-12-02
That makes total sense. I actually needed to mount /home too. But now that I done it, all I get is a black screen with a flickering _ ,instead of a grub menu.

Any ideas?

---

### Post by oldfred on 2010-12-02
Sometimes the simple reinstall does not work but the full chroot does. 

Lets see what is where to see if something is missing:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by TheChaos0 on 2010-12-11
Well, I figured out what the problem was. It seems that XP when installing decided to delete one of the partitions, I guess it all messed everything else.

I simply recovered the partition and then reinstalled Linux completely, seemed like the best and fastest solution at the time.

Once again thanks for the help.

---

