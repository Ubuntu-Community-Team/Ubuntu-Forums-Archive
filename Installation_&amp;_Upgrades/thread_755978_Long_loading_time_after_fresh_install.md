---
title: "Long loading time after fresh install"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by christophdanger on 2008-04-15
I searched some similar topics but no such luck./

I just installed 7.1 on my 131L Dell Latitude notebook.  I've had 7.04 on my laptop before and didn't have to many problems that I couldn't hack through in a couple of minutes or hours.

Anyways GRUB comes up for a second then Ubuntu loads (I'm no longer dual booting) the screen goes black and literaly sits there for about 3 minutes.  Finally the Gnome login comes up and everything is fine (except for the damn WIFI drivers I have to install, that's a different topic though)

Anyone have an idea on how to fix this?

Thanks in advance

---

### Post by PmDematagoda on 2008-04-15
When you see the message telling you to press Esc to bring up GRUB, do that, then at the entry for Ubuntu press F6, once that is done, edit the like so that "splash" becomes "nosplash" and then press "B" once that is done, see if that permits Ubuntu to boot faster.

---

### Post by christophdanger on 2008-04-15
Hey thanks for the reply!

I tried what you told me to do to no avail.  I've been snooping around the forums and I tried pressing "ctrl + alt + 1" and that took the boot up out of, what seems to be "verbose" mode and let me see what was opening and different programs passing and such.  I did notice that it was hanging on something like, Bios Bug #81.  Not sure if that has anything to do with it, but I did notice that there were multiple errors on startup.

After the ctrl + alt +1 thing, the boot up took the normal amount of time.

Don't know if this helps either, but I've never had a splash screen so I don't think I need to disable it.

Thanks

---

### Post by martrn on 2008-04-15
At a terminal type:
```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```

and after it is installed type:
```
sudo sysv-rc-conf
```

An you will be able to see the system processes that start at boot-up time.  You can remove some of these to speed up the boot process.  Some of these system processes are not needed by every ubuntu user but what you need and do not need will vary from system to system.

What to edit and what not to edit is more of a personal choice, faster boot times can mean applications load slower, your applications fail to start or at worst you system will refuse to boot and can render your system unusable.  Its a person choice but the web or internet is full of these kinds of tips and personal preferances is much debatable.  No-one will give you the perfect settings and it would be best to google sysv-rc-conf ubuntu faster boot times for a whole range of diffrent answers......

ttp://[www.extremetech.com/article2/0,1697,2114124,00.asp]("http://www.extremetech.com/article2/0,1697,2114124,00.asp")
[http://blog.kutakutik.or.id/linux/tune-the-speed-and-performance-of-kubuntuubuntu/]("http://blog.kutakutik.or.id/linux/tune-the-speed-and-performance-of-kubuntuubuntu/")

are just two sites of hundreds of what services to load at boot-time or not to load at boot time.

---

### Post by christophdanger on 2008-04-15
This is interesting but I don't think that it entirely relates to my problem.  Once the packages start opening it only takes a couple seconds to get to the login screen.  It's when the boot passes GRUB and then starts to boot Ubuntu, right there it hangs for about 3 min.  If I hit ctrl + alt +1 the booting "starts" up again and moves fine, if I don't press anything it hangs forever then finally goes to Ubuntu login.

---

### Post by martrn on 2008-04-15
Check your fstab file to make sure it is correctly set, and is valid for your ubuntu system.  You can check your fstab file by typing the following at a terminal.

```
sudo kate /etc/fstab
 - [or] -
sudo nano /etc/fstab
```

It should contain an entry like this :--

# /dev/hda1
UUID=789b7571-78d4-4133-7854-61fgfesffiu9       /ext3  notail      0     0

Just check it to make sure it is ok and has the 0 0 or 0 1 otherwise it might force a disk check on every single boot up .  Check the UUID is as it is supposed to be otherwise it might force a disk chek on every single boot up, check that it is set to the correct file system otherwise it might force a disk check on every single boot up.

I am guessing each time your system is going for a reboot is forceing a full disk check, a full disk check happens on my ubuntu system once every 30 days or every 30 reboots, [causing the prevebial 3 minute delay].   I don't know why your ubuntu system would be doing that but check your fstab setting is correct and valid.  Other than that I don't know, only been using ubuntu serveral months myself I have mandrivia perviously, but just think the debian apt system is brillient for installing packages and dependinces.  

[TO ADD}
Your UUID 's should reflect those found from the :-
```
blkid
```
command.

---

