---
title: "RAID1 recovery"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by matt_b on 2007-09-20
Hi all,

I've got a whitebox server here that has got three hard drives - one 40GB (for OS etc.) and two 500GB drives paired in a RAID1 array (using mdadm) for /home.

I would like to know how I would rebuild this server if the first (OS) hard disk failed. Obviously my first step would be to buy another HDD to use for OS, but what would the install process be? How would I recover the (undamaged) RAID1 array?

Thanks for any pointers
Matt

---

### Post by kidders on 2007-09-21
Hi there,

If I were you, I would totally ignore (and possibly even unplug) the RAID array until your new OS is up and running. Once you have a working OS, you could...[LIST=1]
[*]Run fsck on the RAID array, and maybe temporarily mount it somewhere, just to check that it's still in one piece.
[*]Once you're happy, unmount it & alter your /etc/fstab to have it mounted in /home, where it belongs.
[*]Log everybody out of your box, open a text only console & make sure /home is *completely* empty.
[*]Do a **mount -a** to avoid having to reboot.[/LIST]In theory, you should have no problem configuring your RAID array to mount in /home right from square one, but to be perfectly honest, I wouldn't trust any Linux installer as far as I could throw it. For the sake of saving myself the trouble of a command or two, I wouldn't risk making a mess of my /home ... but the choice is yours.

Once your new /home is in place, you will need to double-check that all the UIDs stored on it tally with the user account configuration on your new system. You may find yourself typing what look like statements of the blatantly obvious, eg ...
```
sudo chown -R matt_b: /home/matt_b [COLOR=Gray][ie matt_b owns matt_b's home][/COLOR]
sudo chown -R kidders: /home/kidders [COLOR=Gray][ie kidders owns kidders's home][/COLOR]
...
```This sort of thing will correct problems like...[LIST]
[*]Your sister owns your home directory.
[*]A number (eg 1004 or something) owns your sister's home directory.[/LIST]It's very important to check who owns what before you do anything, or odd things will happen when someone tries to log in.

---

