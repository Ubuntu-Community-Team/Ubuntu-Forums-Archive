---
title: "Aborted Lucid Upgrade"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by whackedspinach on 2010-04-18
I attempted to upgrade my Karmic installation to Lucid today.  It seemed to work fine until I had about 5 minutes remaining.  Then it reported some error about xorg-server-core I believe.  I attempted to reboot but I just get a blinking cursor.  Now I'm on a Live Xubuntu disc.  Does anyone know if this would be possible to troubleshoot and fix?  Or should I just attempt to download a Lucid image and install a clean copy?

---

### Post by quixote on 2010-04-19
Does the machine boot at all or not?  I.e. when is the blinking cursor, pre-grub or after the grub menu?

If after, there might be some things worth trying.  If before, then maybe not.

Describe exactly what happens and any error messages, or if they go by too fast to see.

---

### Post by grege on 2010-04-19
if you can get to the system cursor

type

sudo apt-get dist-upgrade

if that does not work then try

sudo apt-get install -f

and see what happens

---

### Post by Neds Moar Salt on 2010-04-19
> **whackedspinach said:**
> I attempted to upgrade my Karmic installation to Lucid today.  It seemed to work fine until I had about 5 minutes remaining.  Then it reported some error about xorg-server-core I believe.  I attempted to reboot but I just get a blinking cursor.  Now I'm on a Live Xubuntu disc.  Does anyone know if this would be possible to troubleshoot and fix?  Or should I just attempt to download a Lucid image and install a clean copy?

Boot into your live cd, do a chroot like you were restoring grub (Ubuntu has a nice tut on this) and run `dpkg --configure -a` to fix your broken packages and then use `apt-get dist-upgrade` to hopefully upgrade the rest of your packages, and if it fails, then `dpkg --configure -a` again and do the apt-get again.

---

### Post by garvinrick4 on 2010-04-19
Get a live CD and boot it up. I am using lucid as a label and sda5 as partition #. Use your own. Here is code to get label and partition #. If no label make one in gparted.
right click on partition choose label, type in hit OK then apply with green check mark.
Code:
sudo blkid    (second letter is small L)


sudo mkdir /media/lucid

sudo mount /dev/sda5 /media/lucid

sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf

sudo chroot /media/lucid

apt-get update

apt-get dist-upgrade

apt-get -f install

umount /media/lucid

---

### Post by whackedspinach on 2010-04-22
I'm sorry I didn't update this.  The next day I rebooted it and it booted up fine into lucid.  Dunno what happened.

---

### Post by quixote on 2010-04-23
All's well that ends well.  :D  And should it happen again, you'll know there's a fix.

---

