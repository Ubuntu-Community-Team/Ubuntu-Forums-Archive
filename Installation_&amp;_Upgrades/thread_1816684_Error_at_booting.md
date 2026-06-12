---
title: "Error at booting"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by lodhaakshay on 2011-08-02
Hi, i install ubuntu 10.04 but d problem is dat sometime when i m booting in ubuntu i get an error at console which is as follow: "[13.246710] [drm:rs400_gart_adjust_size] *error*Forcing to 32M GART size(Because of ASIC bug?) ". Can anybody please tell b d solution for this....

---

### Post by dino99 on 2011-08-02
are you using an AGP graphic card ?

As actual kernel directly deals with X, xorg.conf is not needed, so better to remove it:

sudo rm /etc/X11/xorg.conf

---

### Post by lodhaakshay on 2011-08-03
[SIZE=4]No i m nt using AGP graphics card and so this cmd is nt working.
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
                         So sir if you have any solution please let me know.
                          Thany you
[/SIZE]

---

### Post by lodhaakshay on 2011-08-04
No i m nt using AGP graphics card and so this cmd is nt working.
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
So sir if you have any solution please let me know.
Thany you

---

### Post by Blasphemist on 2011-08-04
I googled this and there is a bug shown in launchpad. New kernels seem to have fixed this but there is also a solution that seems to have worked for many. Do you have an ATI Radeon video card? If so, try this.
> in /etc/default/grub

add radeon.modeset=0 to GRUB_CMDLINE_LINUX_DEFAULT

then sudo update-grub2

If you don't have grub2 the method is different a bit so let us know if you have grub legacy in use.

---

### Post by lodhaakshay on 2011-08-04
i have ATI Radeon video card and so try the way shown by you but it didnt work..it gives the error message "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."
 As me new to linux can you plz tell me the way i can do it..
                        Thank you..

---

### Post by smurphy_it on 2011-08-04
```
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."
```

Means you opened the file as a regular user, and thus you don't have the permissions to save the file.  Edit the file again, but this time use sudo.

example:

```
gksudo gedit /etc/default/grub
```

Make the required change, save and close gedit and then type 
```
sudo update-grub2
```

---

### Post by lodhaakshay on 2011-08-05
Thank you for the solution.The problem has been solved successfully..

---

