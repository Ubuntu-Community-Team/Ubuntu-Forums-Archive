---
title: "how to install 8.04?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by dirk_s on 2008-04-27
Hi all.

I know this sounds like a stupid question. My problem is, the installer takes too much out of my hands and then trips over its (mis)assumptions:

[COLOR="Blue"]Language: english, 
 Time zone: Berlin,
 keybord: german dead acute+grav[/COLOR] (or so)
Fine so far.
[COLOR="Blue"]Partitioning: Manual[/COLOR]
because there are other systems on that HD and Xubuntu must be installed on /dev/XdY9. All I can see /dev/sda, cfdisk shows expected stuff, thus /dev/sda9. Still fine.
 [COLOR="Blue"]Use as: ext3 
 Mount point: /
 do not format[/COLOR] (because it already did it half an hour ago.)
[COLOR="Blue"]Warns me about no swap.[/COLOR] with 4 GB RAM I don't expect to need swap any time soon.
[COLOR="Blue"]Warns me about not formatting.[/COLOR] It's ok, I know what I'm doing.
[COLOR="Blue"]User: (I skip the details)[/COLOR] still fine.
Then it says:
 [COLOR="Blue"]**Ready to install**
 Your new operating system will now be installed with the following settings:[/COLOR]
```
 Language: English
 Keyboard layout: Germany - Dead grave acute
 Name: Xavier Ulysses Buntu
 Login name: xavier
 Location: Europe/Berlin
 Migration Assistant:
 Gentoo Base System release 1.12.10 (/dev/sda10):
 p2p:
 ftp:
 mythtv:
 sabayonuser: Mozilla Firefox
Mandriva Linux 2008.1 (2008.1) (/dev/sda11):
 mandriva: Mozilla Firefox
Debian GNU/Linux (lenny/sid) (/dev/sda2):
 grml1: Mozilla Firefox
 scanlogd:
 ftp:
Debian GNU/Linux (testing/unstable) (/dev/sda3):
 10 migration-assistant/sda3/users doesn't exist: 10 migration-
assistant/sda3/10+migration-assistant/sda3/users+doesn't+exist/items doesn't
exist
openSUSE 10.3 (X86-64) (/dev/sda6):
 10 migration-assistant/sda6/users doesn't exist: 10 migration-
assistant/sda6/10+migration-assistant/sda6/users+doesn't+exist/items doesn't
exist
openSUSE 11.0 (X86-64) Beta1 (/dev/sda7):
 10 migration-assistant/sda7/users doesn't exist: 10 migration-
assistant/sda7/10+migration-assistant/sda7/users+doesn't+exist/items doesn't
exist
Ubuntu 8.04 (8.04) (/dev/sda9):
 10 migration-assistant/sda9/users doesn't exist: 10 migration-
assistant/sda9/10+migration-assistant/sda9/users+doesn't+exist/items doesn't
exist


No partition table changes and no creation of file systems have been
planned.

If you plan on using already created file systems, be aware that existing
files may prevent the successful installation of the base system.
```
"migration assistent doesn't exist"?? A good part of the stuff inside the box is obviously nonsense and/or doesn't belong there. (In fact there is no need to take care of any other OS than itself, my master-grub will do that.) But I see no way to remove any foreign stuff. "Advanced" just offers me to change the location of the boot loader - which I did: To /dev/sda9. It must not destroy my main boot loader (grub, in /dev/sda1, boots from the MBR of that disk). 

Now what?

If just let it run, it installs some software to /dev/sda9 (mounted as /target) but /target/boot contains nothing but this afterwards:
```
root@ubuntu:/mnt/1# ll /target/boot
total 10996
-rw-r--r-- 1 root root  420164 2008-04-10 15:12 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   74079 2008-04-10 15:12 config-2.6.24-16-generic
-rw-r--r-- 1 root root 7583122 2008-04-22 19:39 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r-- 1 root root 1145670 2008-04-10 15:12 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1887736 2008-04-10 15:12 vmlinuz-2.6.24-16-generic

```
No hints of a boot loader. If I knew the boot parameters, I could copy all *2.6.24-16* onto /dev/sda1 and make an entry in the menu.list there. But on one hand I don't know them and on the other hand I suspect that the installation is incomplete in other ways.

Is there any way to install Xubuntu anyway, preferably without this "install" program?

TIA
Dirk[COLOR="Blue"][/COLOR]

---

