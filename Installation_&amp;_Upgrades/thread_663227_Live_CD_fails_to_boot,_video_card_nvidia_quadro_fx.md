---
title: "Live CD fails to boot, video card: nvidia quadro fx, apci"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by anonymousnobody on 2008-01-09
I am trying to install Ubuntu 7.10 onto a IBM server (Xeon processor). However, the live cd won't boot. I am sure the cd is not corrupted because I have used to to install on other machines.

I think the problem is on the video card. At first, the cd would boot go as far as the splash screen. Then it would crash and default back to the ash shell.

Sample Output:
    BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)

    /bin/sh: can't access tty; job control turned off
    (initramfs)

Reading this post: [http://ubuntuforums.org/archive/index.php/t-568449.html](http://ubuntuforums.org/archive/index.php/t-568449.html)
I tried adding "noacpi" and "acpi=off" to the boot options. That got me past the crashing and defaulting back to the ash shell. However, I can't get to the gnome desktop. I know ubuntu loaded because I can hear the ubuntu music that it plays when it logs in. I just can't see anything on the screen. When I open a virtual console (tty1) it has a bunch of white lines.

PARTIAL SOLUTION (IT ONLY WORKED ONCE): I found the solution to my problem. I am leaving this post up here in case other people have similar problems so they can refer to this post. It is a combination of the apci problem and video card problem. I tried the "noacpi" and "acpi=off" with the "safe graphics" (casper-vesa) and it works. It loads to the gnome desktop and I can install.

I seem to be dyslexic. It's a**cp**i NOT a**pc**i.

Update (1/14/08): other options to use if "noacpi" and "acpi=off" don't work is "no-hlt"

also worth trying is "break=top" which will bring you to the ash shell. from there type "modprobe piix" then exit.

it works sometimes and does others even with the added options. just keep rebooting a few times. sometimes i vary the boot choices.

---

### Post by anonymousnobody on 2008-01-09
Solved: refer to above post.

I spoke too soon!

When I rebooted after the installation. I couldn't find the ubuntu boot option in grub so I tried to reinstall. However, I encountered the same problem as before! The live cd crashes and defaults to the ash shell. Even though I added the boot options! It worked the first time, why wouldn't it work this time!

The ubuntu was installed on a physically separate hard drive. Is there a way to find it or boot it through grub? Why didn't my previous solution work this time?

---

