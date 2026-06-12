---
title: "GRUB 2 update Error"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by Marcus N on 2010-10-03
When I boot my Labtop i get this error when GRUB II starts

Warning: invalid foreground colour...
press a key to continue...

the only file that I have edited is /etc/grub.d/05_debian_theme

I saved the file and run update-grub2 to update the files

root@Marcus-Labtop:~# update-grub2
Generating grub.cfg ...
Found background image: wallpaper.tga
Found background image: Lake_mapourika_NZ.tga
Found background image: wallpaper.tga
Found background image: wallpaper.tga
/etc/grub.d/05_debian_theme.save.3: 4: /bin: Permission denied

Any help ????????

---

### Post by presence1960 on 2010-10-03
The command should be ```
sudo update-grub
```

---

### Post by drs305 on 2010-10-03
Your /etc/grub.d/05_debian_theme file has errors in it. Either you have a wildcard in the WALLPAPER line (I don't even know if wildcards can be used), you have multiple repetitious lines or you have multiple executable backups in the folder. At a minimum, remove the executable bit from your *.save file.

You can see from the terminal output that update-grub is finding multiple images when it runs. When an image is properly addressed, only one image will be reported in the terminal, such as this:
> 
drs305@homebuilt:~$ sudo update-grub
Generating grub.cfg ...
Found background image: earth.png
Found linux image: /boot/vmlinuz-2.6.32-25-generic


---

