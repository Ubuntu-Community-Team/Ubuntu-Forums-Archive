---
title: "Couple of questions on Ubuntu"
date: 2004-11-26
forum: Installation &amp; Upgrades
---

### Post by Sniffer on 2004-11-26
Ok, i have gather a couple of questions to see if you can help me out :D 

1 - I have an laptop without a floppy device, i have installed the greatest ubuntu on it and in the installation i have always uncheck the floppy module, tough now when booting the ubuntu system always appear:

modprobe: FATAL error inserting device.....no such device (ok, i know that, but how can i take this off, disable this module on booting...i lost precious seconds waiting for this to be gone)

2 - I don't like graphical login (or init 5) i prefer the good all days of terminal (init 3), to do it, it's like Fedora?, editing /etc/inittab for init 3?? and the login, i have to make startx or startgnome (better to ask now the when in terminal mode :)??

3 - In gxmame (i have solved the problem i had with the executable already) i need to put the bios (mame bios, i have the all pack, neo geo/cps 2 and so on) where?? i have put some roms on the rom directory...but when scanning don't appears anything!!!!!!!!

4 - This is important, how can i enter gnome with root, IT'S very ANNOYING have to copy /cut/ delete stuff by the terminal or at least how can i open root folders with the normal user..so i can drag and drop and not see READ ONLY??

Thks a bunch
Sniff.

---

### Post by Alessio on 2005-03-04
[QUOTE=Sniffer]Ok, i have gather a couple of questions to see if you can help me out :D 

3 - In gxmame (i have solved the problem i had with the executable already) i need to put the bios (mame bios, i have the all pack, neo geo/cps 2 and so on) where?? i have put some roms on the rom directory...but when scanning don't appears anything!!!!!!!!
.[/QUOTE]

I have the same problem, do you have solve? How?

---

### Post by duff on 2005-03-04
[QUOTE=Sniffer]
4 - This is important, how can i enter gnome with root, IT'S very ANNOYING have to copy /cut/ delete stuff by the terminal or at least how can i open root folders with the normal user..so i can drag and drop and not see READ ONLY??
[/QUOTE]```
# sudo nautilus 
```

---

### Post by dewey on 2005-03-04
You can activate the root by doing
```
$sudo su -
#passwd

```

Then you'll be able to login with root, since it would have a password, though I highly discourage this.

---

### Post by Sniffer on 2005-03-29
Thanks for your reply's...just come back to use Hoary again :)

Regarding GXmame see this:

[http://www.ubuntuforums.org/showthread.php?p=109048#post109048](http://www.ubuntuforums.org/showthread.php?p=109048#post109048)


Hope it helps tough i didn't have tried to compile gxmame 0.35 beta myself.

---

### Post by GentleHatemonger on 2005-03-29
[QUOTE=Sniffer]1 - I have an laptop without a floppy device, i have installed the greatest ubuntu on it and in the installation i have always uncheck the floppy module, tough now when booting the ubuntu system always appear:

modprobe: FATAL error inserting device.....no such device (ok, i know that, but how can i take this off, disable this module on booting...i lost precious seconds waiting for this to be gone)[/QUOTE]

```
echo "floppy" | sudo tee -a /etc/hotplug/blacklist
```

as far as I know, that should work, but I'm not 100% sure

---

