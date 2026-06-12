---
title: "Dual boot with xp on a different disk"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by xVern on 2005-09-06
okay. i un-plugged all my hard drives, besides the one i wanted ubuntu on.

installed everything fine.

i can boot up into it, when i dont have my xp drive plugged in. haha.

would it just be something i put in the boot.ini?
or something else?


this is my first time playing with linux, so sorry if this is dumb.

thanks!

---

### Post by aveline on 2005-09-06
didn't you have your xp drive plugged in when you installed ubu?

cuz if you did it should detect XP & add it to the GRUB boot menu as a choice.

aveline

---

### Post by xVern on 2005-09-06
[QUOTE=aveline]didn't you have your xp drive plugged in when you installed ubu?

cuz if you did it should detect XP & add it to the GRUB boot menu as a choice.

aveline[/QUOTE]
 i didnt :-/.

reasoning; i have 4 of the same drive. so i couldnt tell the difference between them, so i unplugged the ones i knew i didnt want ubu on.

anything i can do?

---

### Post by born_confused on 2005-09-06
[QUOTE=xVern]i didnt :-/.

reasoning; i have 4 of the same drive. so i couldnt tell the difference between them, so i unplugged the ones i knew i didnt want ubu on.

anything i can do?[/QUOTE]

you can, you are gonna have to look up grub manual.

---

### Post by xVern on 2005-09-06
[QUOTE=born_confused]you can, you are gonna have to look up grub manual.[/QUOTE]
 Is it a bad thing i dont know this "grub" you speak of?

---

### Post by GreyFox503 on 2005-09-06
Because you unplugged all your other drives when you installed Ubuntu, it probably put grub onto the MBR of the drive containing Ubuntu (GRUB is Ubuntu's bootloader).  So even though you have two operating systems, you're not really dual-booting (sort of).

The easy thing to do is to go into your BIOS and change the boot order of the hard drives in your system.  Boot from the windows drive, you'll see windows; boot from the Ubuntu one, you'll see Ubuntu.  Some BIOSes even have a cool feature like a "quick-boot" menu that lets you choose a certain drive to boot from when you press a certain key at boot, without going into the BIOS.

At least with the above method, you don't have to unplug any drives anymore.

If you want to have a real dual-boot system (where you get a menu with OS choices) then that will take a little more work.  You could probably modify GRUB on Ubuntu's drive and add Windows as a choice, though I'm not exactly sure how to do that.

The file that grub uses to display its menu choices is here:

/boot/grub/menu.lst

But please be very careful when editing that file.

---

### Post by xVern on 2005-09-06
[QUOTE=GreyFox503]Because you unplugged all your other drives when you installed Ubuntu, it probably put grub onto the MBR of the drive containing Ubuntu (GRUB is Ubuntu's bootloader).  So even though you have two operating systems, you're not really dual-booting (sort of).

The easy thing to do is to go into your BIOS and change the boot order of the hard drives in your system.  Boot from the windows drive, you'll see windows; boot from the Ubuntu one, you'll see Ubuntu.  Some BIOSes even have a cool feature like a "quick-boot" menu that lets you choose a certain drive to boot from when you press a certain key at boot, without going into the BIOS.

At least with the above method, you don't have to unplug any drives anymore.

If you want to have a real dual-boot system (where you get a menu with OS choices) then that will take a little more work.  You could probably modify GRUB on Ubuntu's drive and add Windows as a choice, though I'm not exactly sure how to do that.

The file that grub uses to display its menu choices is here:

/boot/grub/menu.lst

But please be very careful when editing that file.[/QUOTE]


How would i know what to add?

and the real dual-boot system is what im going for.

---

### Post by GreyFox503 on 2005-09-06
Well, I read through the descriptions of GRUB.  Do this to backup and edit the file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

Then scroll to the bottom, and you should see some entries that look like the current kernel you're using (and it might say memtest86 too).  Try adding these lines under them in a blank spot:



```
title		Windows 95/98/NT/2000/XP
root		**(hd0,0)**
makeactive
chainloader	+1
```

You can change the title to whatever you want.  What you have to do to make it work, though is change the bolded part to point to the windows installation on your computer.  In this example, it is referring to the first partion on the first drive.  Examples:

1st drive, 2nd partition:  (hd0,1)
3rd drive, 1st partition:  (hd2,0)

Grub is a little weird so you need to use its numbering system and not just hda1 like you might be used to.

After you punch that in, save the file and reboot.  Go into the grub menu (you might have to press Esc during boot).  Then you can see your choices and your new windows one should appear.  To test it, just highlight it with the arrow keys and hit enter.  If it works, great!  If not, it will just spit back some error message.  Then you can reboot and choose to go into Ubuntu again and try something else.

---

