---
title: "How do I uninstall if I don't have a copy of Windows 7?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by suclid on 2010-02-08
I'm afraid that if I delete the partition Ubuntu is on it'll mess up GRUB and I won't be able to boot into Windows.

here's the link to what my partitions currently look like: [http://s690.photobucket.com/albums/vv263/simulache/?action=view&current=partitioneditor.png](http://s690.photobucket.com/albums/vv263/simulache/?action=view&current=partitioneditor.png)

---

### Post by suclid on 2010-02-08
OR does anyone know of a 32-bit distro or version of Ubuntu that works with my Toshiba L505D? I should've researched whether Ubuntu was supported for my new laptop. I had 8.10 working great on my previous Dell.

---

### Post by darkod on 2010-02-08
You're right, if you delete the ubuntu partition that will delete the grub config files and it won't work even for windows.

The easiest way to install generic windows bootloader to the mbr is from ubuntu or from the live desktop do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. You should boot straight into win7 after that. You can delete the ubuntu partitions from windows.

Alternatively, you have win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

That can be used only to repair the boot process, not for a full reinstall. Instructions for repairing windows bootloader with commands here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by colinwhipple on 2010-02-08
> **suclid said:**
> OR does anyone know of a 32-bit distro or version of Ubuntu that works with my Toshiba L505D? I should've researched whether Ubuntu was supported for my new laptop. I had 8.10 working great on my previous Dell.

Do a top-level search on L505D in these forums.  There are a couple of solutions.

Colin

---

### Post by suclid on 2010-02-08
> Alternatively, you have win7 repair cd image here:
[http://neosmart.net/blog/2009/window...-repair-discs/](http://neosmart.net/blog/2009/window...-repair-discs/)
se I can't even boot into my 

I can't boot into Ubuntu. So I just delete the ubuntu partitions, then boot a CD burned with this ISO?

---

### Post by darkod on 2010-02-08
> **suclid said:**
> I can't boot into Ubuntu. So I just delete the ubuntu partitions, then boot a CD burned with this ISO?

Yes. Another alternative is to boot the ubuntu cd with Try Ubuntu option, the live desktop. The commands I quoted can be used from the live desktop too.

---

