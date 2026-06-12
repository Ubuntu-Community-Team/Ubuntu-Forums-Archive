---
title: "Installed Grub to external HDD? Error 22"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by cyclonedr on 2008-05-30
Hi all, 
  I installed ubuntu 7.10 onto my external HDD.  While in the installation options, on the last page there is an advanced button.  I pressed this button and set the install location for the boot loader to be /dev/sdb.  Then I clicked install. Everything went fine, until I restarted my computer. Now lets back up a little... What I want to be able to do is have the computer boot directly into XP on startup, but then I want to boot into Ubuntu when I press F12 to get the boot options. Back to restarting, I pressed F12 to get the options to boot into the USB device and pressed enter, get the GRUB boot menu press enter, and then it says Grub loading, then Grub error 22. What's this about.  Did I use the wrong options to install GRUB? Since I hopefully installed GRUB in the right place does it think it's on drive 0 and I have to edit something? I believe it's pointing to (1,4)  How would I edit this? Thanks for any suggestions

---

### Post by meierfra. on 2008-05-31
That's  one of the things Ubuntu gets wrong fairly often. You didn't do anything wrong and it can be fixed as follows

At the grub menu at boot-up select the ubuntu item, but do not press "enter", press "e" instead. At the new screen which appears, press "e" again to edit the first line. 

Change "root (hd1,4)" to "root (hd0,4)"  (So change the first number to zero, but do not change the second number.)

Press "enter" and then "b"" to boot into ubuntu.

If this worked you have to make the changes permanent by editing the file
"menu.lst". Open a terminal and type

```
 gksudo gedit /boot/grub/menu.lst
```

change the line

"#groot (hd1,4)" to  "#groot (hd0,4)"

Save the file.

In the terminal type


```
sudo update-grub
```

If you  want  to be able to boot to Windows from the Grub menu, you also need to change the Windows item in menu.lst

Change

title Windows XP (or something like that)
root (hd0,?)
....

to

title Windows XP (or something like that)
root (hd1,?)
map (hd0) (hd1)
map (hd1) (hd0)
....

---

