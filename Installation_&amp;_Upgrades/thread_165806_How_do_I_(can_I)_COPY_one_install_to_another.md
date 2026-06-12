---
title: "How do I (can I) COPY one install to another?"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by kwickone on 2006-04-25
Hey all,

Maybe I should know this already, but I have never done this so I figured why not ask the right people.

I have been playing with Ubuntu (Breezy) for about 2 months now, on a USB HD install.  That way I could still boot into XP for work, and any other reason that needed XP only.  I have grown to admire and like Ubuntu quite a bit.

I am close to commiting to a (non-USB HD) standard install on my laptop.  (NOTE:  I will still keep dual boot just in case :mrgreen: )

How can I copy all my USB HD Ubuntu settings (from / filesystem) to my internal HD (to a new / filesystem)?  Basically I want to keep everything that I have done.  Is it as simple as this?:

1.  Perform a new install on the internal HD
2.  Attached the USB drive, which should be auto mounted.
3.  copy * (recursively) from the USB / to the internal /

Any other ideas?

Thanks much.

---

### Post by jazzmuzik on 2006-04-25
1. Perform a new install on the internal HD
2. Attach the USB drive, which should be auto mounted.
3. recursively copy the old /home directories to the new /home directories
4. copy any additional files like databases, etc. that may be scattered about the system as needed.

Don't recursively copy the old root directory to the new root directory. That would be pointless after a new install.

One caveat: I've found I need to delete the /home/user/.gnome* files and directories on the new drive, otherwise my toolbar is screwy for some reason. Gnome will recreate these files on login. Then I just re-add my toolbar icons which takes a few minutes.

---

### Post by kwickone on 2006-04-25
Thanks for the reply jazzmuzik.  That makes sense about the /etc/fstab file.  I guess I was hoping to not have to re-create the wheel and re-install everything.  E.g., I have installed and configured Cisco VPN client, Madwifi, wpa_supplicant, VMWare Server, etc.  Each of which took a bit of tweaking....you know.  I figured since the HW (laptop) is the same (with the exeption of the hd0,0 which was USB), I would keep a lot of the settings.

Anyone else have thoughts?
Thanks.

---

### Post by lha on 2006-04-25
[QUOTE=kwickone]Thanks for the reply jazzmuzik.  That makes sense about the /etc/fstab file.  I guess I was hoping to not have to re-create the wheel and re-install everything.  E.g., I have installed and configured Cisco VPN client, Madwifi, wpa_supplicant, VMWare Server, etc.  Each of which took a bit of tweaking....you know.  I figured since the HW (laptop) is the same (with the exeption of the hd0,0 which was USB), I would keep a lot of the settings.

Anyone else have thoughts?
Thanks.[/QUOTE]
There's no reason to make a new install. Look at [http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/index.html]("http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/index.html") for instructions. They are a bit old and assume you use lilo but otherwise they're good. (You are using grub instead of lilo.) In short, you need to repartition your internal drive and copy the existing installation there. Then edit /etc/fstab (on internal hd) to mount correct partition(s) when booting from internal hd and add a line to external hd's /boot/grub/menu.lst that allows you to test if Ubuntu works when booted off the internal drive. Finally, install grub on the internal drive.

---

