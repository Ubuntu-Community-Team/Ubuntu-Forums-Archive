---
title: "ubuntu 6.06 dvd (OEM Installed) cant login"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by kC_ on 2006-06-18
hi, ive just installed ubuntu 6.06 dvd on my laptop (dual booting with XP pro)

grub comes up fine, i can boot into either OS...

BUT when ubuntu starts up, it asks me for a user/pass

when it was installing i dont recollect it asking for a username, it did ask for a password.

ive tried root as username, but it doesnt login..

and as a secondary question, how do i make XP my default OS in the grub bootmanager?

as when grub starts, it auto boots into ubuntu after 5-10 seconds, as the pc is shared, id rather it go straight to xp pro (for my girlfriend)


thanks

p.s 
<<< total linux noob, no idea about commands etc.

---

### Post by RoNoVe on 2006-06-18
I can't give an answer on your first question, however I do know how to solve the second one.
You should change the "default = " option in /boot/grub/menu.lst but since you can't logon onto your system this is going to be a bit more difficult.

I suggest to use a live-cd, mount the ubuntu partition somewhere, and edit (as root) the menu.lst file.

Get root:
su -
(enter password)

Mounting a filesystem is quite easy.
If you have an IDE hd, an ubuntu is on the 1st partition, execute
mount /dev/hda1 /mnt

In case it's a sata disk:
mount /dev/sda1 /mnt

if you'd mount your ubuntu partition to /mnt, you should
nano -w /mnt/boot/grub/menu.lst
And search for a line like
default = 0
and change de 0 into the right value.
look out: counting starts at 0; not at 1.

Hope this helps
have fun

--
Ilias

---

### Post by kC_ on 2006-06-18
ah found out that the default username is OEM, so im now logged in and making my first post on ubuntu via wireless connection..

gonna try your suggestion about grub now.. thanks

---

### Post by kC_ on 2006-06-18
yep worked fine, had to log in as root to edit it, and all good;]

cheers again


been struggling for past hour with realplayer & w32codecs](*,)  
i can now see why windows will NEVER ever be threatened by linux.

---

