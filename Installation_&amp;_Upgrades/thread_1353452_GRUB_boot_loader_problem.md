---
title: "GRUB boot loader problem"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by dulac on 2009-12-12
Hey guys, please redirect if this exists somewhere...

Here is the problem:


I have a tower with 2 SATA hard drives. The first was installed with the tower and had Windows Vista.

The second i purchased and installed with UBUNTU 9.04. It installed it from the Live Disc with the built-in "boot loader" that allows you to choose either Windows or Ubuntu(this is not the bios boot loader)

Everything was fine. Then my Vista crashed. I took this opportunity to install 7.

Now, i have Windows 7 and Ubuntu(seperate hard drives). Now the ubuntu boot loader does not show up. Further, when i go into the bios boot sequence and load the ubuntu HD it loads with a blinking "underscore" and does nothing.

Is there anyway to load ubuntu? Or do i have to do a complete install(if this is the case i need to know how NOT to install the boot loader from ubuntu since i want my hard drives to be disjoint)

Thanks.

---

### Post by raymondh on 2009-12-12
> **dulac said:**
> Hey guys, please redirect if this exists somewhere...

Here is the problem:


I have a tower with 2 SATA hard drives. The first was installed with the tower and had Windows Vista.

The second i purchased and installed with UBUNTU 9.04. It installed it from the Live Disc with the built-in "boot loader" that allows you to choose either Windows or Ubuntu(this is not the bios boot loader)

Everything was fine. Then my Vista crashed. I took this opportunity to install 7.

Now, i have Windows 7 and Ubuntu(seperate hard drives). Now the ubuntu boot loader does not show up. Further, when i go into the bios boot sequence and load the ubuntu HD it loads with a blinking "underscore" and does nothing.

Is there anyway to load ubuntu? Or do i have to do a complete install(if this is the case i need to know how NOT to install the boot loader from ubuntu since i want my hard drives to be disjoint)

Thanks.

Hi,

When it was Vista + Ubuntu, you mentioned that you do not alter bios to access any OS .... am I right?

When you installed win7 (assuming everything was the same in BIOS), win7 overwrote GRUB in the MBR.

Go back to the old, orginal BIOS settings and then re-install GRUB.  Here's a tutorial.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Post back any errors.  We may have to chainload win7 (far chance) but that will be manageable with GRUB installed.

Regards,

---

### Post by dulac on 2009-12-12
well GRUB is back. but it still reads "windows vista" and not 7. this is not too large of a problem since i can go into the boot menu if need be. but is there a way to update the information?

Thanks.

---

### Post by QIII on 2009-12-12
If you are running Jaunty, then you likely still have GRUB and not GRUB2.  This means you can easily update menu.lst (which does not exist any long with GRUB2).

Edit:  Back things up first!

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

Then, you can make your edits.

```
gksudo gedit /boot/grub/menu.lst
```Scroll down until you find something that looks similar to 

```

title Vista
root (hdx,x)
makeactive
chainloader +1

```and simply change the title line to (without quotes) "title Windows 7".

It is always a good idea to wait when someone gives you commands to run in the terminal and see if someone will chime back in and say "Yeah, that's good."

You don't know me from Adam, so I could either be an idiot or malicious.

---

### Post by raymondh on 2009-12-12
> **QIII said:**
> 

Edit:  Back things up first!

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

Then, you can make your edits.

```
gksudo gedit /boot/grub/menu.lst
```Scroll down until you find something that looks similar to 

```

title Vista
root (hdx,x)
makeactive
chainloader +1

```and simply change the title line to (without quotes) "title Windows 7".

It is always a good idea to wait when someone gives you commands to run in the terminal and see if someone will chime back in and say "Yeah, that's good."

You don't know me from Adam, so I could either be an idiot or malicious.

I would do and suggest the same thing .... I don't think that makes us idiots or malicious ;)

Happy ubuntu-ing.

---

