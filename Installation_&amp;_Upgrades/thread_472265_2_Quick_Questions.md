---
title: "2 Quick Questions"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by lemonwonder on 2007-06-12
Hey There!

I got dual-boot win98 and ubuntu, easy but I was scared!

I have 2 questions: 

1. If I go to disk, I can see my win98 docs, but cant make a shortcut to em from desktop... i want quick acess, how do i do it? (Like, make a launcher with a command to open a folder maybe?)


2. How can I make WINDOWS 98 the default OS, so when it boots up grub or whatever it is, Ubuntu is under the other os part instead of windows. (So, if you turned on computer, you could walk away, it says its thing "In 2 seconds WINDOWS will load automatically" so my sister doesnt freak out.


THANKS!!

---

### Post by WNDS1701 on 2007-06-12
> **lemonwonder said:**
> Hey There!

I got dual-boot win98 and ubuntu, easy but I was scared!

I have 2 questions: 

1. If I go to disk, I can see my win98 docs, but cant make a shortcut to em from desktop... i want quick acess, how do i do it? (Like, make a launcher with a command to open a folder maybe?)


2. How can I make WINDOWS 98 the default OS, so when it boots up grub or whatever it is, Ubuntu is under the other os part instead of windows. (So, if you turned on computer, you could walk away, it says its thing "In 2 seconds WINDOWS will load automatically" so my sister doesnt freak out.


THANKS!!

Hello lemonwonder!

Why have you been scared? Ubuntu is meant to be easy and friendly to use. :-)

To your questions:

1.
[LIST]
[*]Take Nautilus (the file manager) and go to the folder above the file or folder you want to link to.
[*]Open in another Nautilus window the folder where you want to have the link placed in.
[*]press and hold the control and shift button and drag the icon of the file or folder into the other window.
[*]Go and get a coffee!
[/LIST]

2.
Take a look at this link. You will find a little script or program that you might feel useful.
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

You can edit the grub file manually if you wish by
[LIST]
[*]starting the terminal (Applications > Accessories > Terminal), 
[*]typing in ```
 sudo gedit 
```,
[*]opening the grub configuration file at ```
/boot/grub/menu.lst
```,
[*]moving the text about WIN98 (at the very end) in front of the ubuntu stuff (take care: it should be the complete lines starting with title until chainloader +1),
[*]saving the file.
[*]now you even deserve some chocolate :)
[/LIST]

I hope that this was useful to you! Let us know!

Cheers! ;)

---

### Post by wh0rd on 2007-06-12
1.** Right Click on Desktop** > **Create Launcher... **
    -Fill in the Info:
[INDENT]a. **Name:** The name of your folder
b. **command:** > nautilus [COLOR="Red"]**/path/to/your/folder**[/COLOR]
c. Click on the "**No Icon**" button to select an icon for your shortcut (launcher).
d. Click** OK**.[/INDENT]

Now you should have a new icon that going to the folder you specified in the command section.







2. You need to edit your Grub's menu.lst file. This is where the configuration of the boot up menu screen happens.
[INDENT]
a. Backup the menu.lst so you can restore it easily incase you do something wrong in editing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

b. Editing the menu.lst located in /boot/grub/ directory:
```
gksu gedit /boot/grub/menu.lst
```
-Enter your password when prompted. Then scroll down and cut (to paste) the section where it lists your Windows operating system, for example look at the red section:
> # This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/COLOR]

-Paste it above the line where it mentions your Ubuntu kernel option, for example:
> [COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

[/COLOR]**title           Ubuntu 7.04 (Feisty Fawn), kernel 2.6.20-16-generic**
root            (hd0,5)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=d0c2af16-87d3-4191-918a-179e644d0b99 ro quiet splash vga=791
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

-Save, close gedit, and then reboot to see the changes.[/INDENT]

---

