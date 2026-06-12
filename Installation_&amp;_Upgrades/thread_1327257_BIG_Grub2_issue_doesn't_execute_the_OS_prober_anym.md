---
title: "BIG Grub2 issue: doesn't execute the OS prober anymore..."
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-11-15
Woa... quite weird.
Basically I can't chmod -x the OS prober, and right now it's not executable. When GRUB runs, I only get the Karmic option. No more Vista.

Not sure what's up... sudo update-grub again only gives me the Karmic distro + recovery mode, and the listing function also skips the Windows OS (while when I tried it 3 minutes ago, they still appeared there :s )

No clue what's up... no chmod command worked except -r, so now it can't even be executable...


Argh :(

---

### Post by darkod on 2009-11-15
I believe -x is to disable it, and you use +x to enable it again. So it would be something like:
sudo chmod +x /etc/grub.d/30_os-prober

That should enable it. After that
sudo update-grub

To update the grub.cfg

---

### Post by Pott on 2009-11-15
Thanks... terminal seems to have recognized the command but the file hasn't changed and update-grub still doesn't get my windows :(

Ah wait... I did some research on chmod and came up with sudo chmod rwx.

It gave me my permissions back.

HOWEVER

There are still no Windows partitions... I get this error message:

pierre@pierre-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
/etc/grub.d/30_os-prober: 214: Original: not found

pierre@pierre-laptop:~$ sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
karmic 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)

So the file permission is restored but I still have no Windows...

---

### Post by darkod on 2009-11-15
I don't understand, which file should change? With the new grub2 any change is not easy to see even if it happened. :)
When you do the update-grub do you see os prober execute? It would show few lines in the terminal.

---

### Post by darkod on 2009-11-15
Is 30_os-prober in the /etc/grub.d folder at all?

Not too familiar with ubuntu messager yet but when is says Not Found does that mean the actual os prober file?

Is there a chance you deleted it and just disabled it earlier?

---

### Post by Pott on 2009-11-15
Nope the file is there and present, in the right folder... it never moved.

---

### Post by darkod on 2009-11-15
Sorry, no idea. In case you want to consider reinstalling grub2 look at post #1 item number 12. The instruction are short and precise.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Pott on 2009-11-15
I'm doing a clean install. I've not had that much tweaks on it and now I'll know what NOT to touch...

Grub legacy was so much easier it seems...

---

