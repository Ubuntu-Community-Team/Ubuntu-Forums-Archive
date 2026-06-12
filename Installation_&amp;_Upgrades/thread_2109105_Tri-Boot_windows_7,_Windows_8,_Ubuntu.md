---
title: "Tri-Boot: windows 7, Windows 8, Ubuntu"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by TannerSummers on 2013-01-26
So I just installed Ubuntu 12.10 last night. Right away grub gives me the option of Ubuntu and windows 8, when I click on Windows 8, it takes me to the Windows MBR and shows an option for Windows 7 & 8. So  pretty much I have to go through to boot menus and I wish to make it so grub handles all three of them. I am new to Ubuntu so sorry ahead of time but how can i fix this?

---

### Post by darkod on 2013-01-26
This has nothing to do with grub. When you install more than one copy of windows, it combines the boot files together. So, grub can only load the combined boot files which then give you the option to choose the windows version you want to boot.

Before installing the second version of windows you should have moved the boot flag to that partition because windows puts the boot files where the boot flag is. That way they would have been separated, and grub would show separate entries for win7 and win8.

You can try adding the boot files, which should work, something like bootrec /fixboot. You have instructions how to get to a repair command prompt here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Note that if you do the /fixmbr that will overwrite grub2 on the MBR which you don't want. The /fixboot should be enough, but with windows you never know. It doesn't always works like it's supposed to. :)

Before doing that, move the boot flag on the partition where the second windows version is, and use the dvd for that version to load the rescue command prompt.

Even after you finish that, the boot files on the first windows partition will probably still be combined, so you would have to use some BCD editing to delete the second entry, so that it doesn't show you a second menu. But that is windows and I don't know the exact details, you can find more info on their forums and google tutorials.

Basically all this operation is windows related, it has nothing to do with ubuntu, so you're like in the wrong place. :) Once you have separate boot files, grub2 will show them. Before that, it can't do anything about it.

---

### Post by TannerSummers on 2013-01-27
> **darkod said:**
> This has nothing to do with grub. When you install more than one copy of windows, it combines the boot files together. So, grub can only load the combined boot files which then give you the option to choose the windows version you want to boot.

Before installing the second version of windows you should have moved the boot flag to that partition because windows puts the boot files where the boot flag is. That way they would have been separated, and grub would show separate entries for win7 and win8.

You can try adding the boot files, which should work, something like bootrec /fixboot. You have instructions how to get to a repair command prompt here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Note that if you do the /fixmbr that will overwrite grub2 on the MBR which you don't want. The /fixboot should be enough, but with windows you never know. It doesn't always works like it's supposed to. :)

Before doing that, move the boot flag on the partition where the second windows version is, and use the dvd for that version to load the rescue command prompt.

Even after you finish that, the boot files on the first windows partition will probably still be combined, so you would have to use some BCD editing to delete the second entry, so that it doesn't show you a second menu. But that is windows and I don't know the exact details, you can find more info on their forums and google tutorials.

Basically all this operation is windows related, it has nothing to do with ubuntu, so you're like in the wrong place. :) Once you have separate boot files, grub2 will show them. Before that, it can't do anything about it.

dang that sucks, but makes sense. thanks man I will see what I can do

---

