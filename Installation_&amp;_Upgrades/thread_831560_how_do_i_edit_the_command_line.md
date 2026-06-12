---
title: "how do i edit the command line?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Montalo on 2008-06-16
first off, i think i made this in the incorrect forum to begin with, and its diffrent now


I am following this to instal on a VPC, [http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx](http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx) ',

it says i hit f4, im good


it then says  Select F6 and add “noreplace-paravirt” to the end of the command line and press Enter.


my question

how do i add "noreplace-paravurt"to the command line and where is the command line?


thanks

---

### Post by Partyboi2 on 2008-06-17
When you have booted the cd and are at the menu screen press F6 and then at the end of the line add 
```
noreplace-paravirt
``` then press enter
After you have installed ubuntu and have rebooted you will need to add it again to boot into your new install when you see somthing like "grub loading..." press "Esc" to get to grub menu. then highlight the kernel you are going to be booting into (normally the first one on the list) then press "e" to edit then highlight the line starting with "Kernel" and press "e" to edit then at the end of the line add ```
noreplace-paravirt
```then press "enter" then "b" to boot. Once you are at the desktop you will need to add "noreplace-paravirt" to your grub menu.lst so that everytime you boot that boot option will be used. To do this Open a terminal (Applications>Accessories>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
``` (small L) Once it has opened the file look for a section that looks something  like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro splash [/COLOR][COLOR=Blue]noreplace-paravirt[/COLOR]
At the end of the line I have highlighted add
```
[COLOR=Blue]noreplace-paravirt[/COLOR]
``` then save the file.
Then back in the terminal update grub
```
sudo update-grub
```

---

