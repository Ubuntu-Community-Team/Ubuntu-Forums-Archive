---
title: "video problem; upgrading from onboard to PCIe video card.."
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by WareWolf801 on 2010-06-19
Running Ubuntu 10.4 .. It was working fine with the onboard video, but it wasn't able to play the HD video files, so I upgraded to a PCIe nvidia card. Now when it boots up it tells me "no such device: bb15505a-d716-42ef-bd57-c7ed7d7c4dff' which I presume is the intel-based video it had onboard. I'm left with a prompt saying "grub rescue>".

How to get this working? I don't want to have to reinstall the whole OS, but will if I must..

Please let me know any info that might help. I searched around but only found a bunch of junk about people having issues with nvidia cards, and their drivers.

Thanks for your time.

WareWolf801

---

### Post by presence1960 on 2010-06-19
That string of characters refers to the UUID of a partition. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

