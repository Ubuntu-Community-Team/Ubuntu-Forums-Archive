---
title: "problem running LiveCD :("
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by djtreo on 2008-01-07
hi guys! I just got my CD (7.10) from cannonical after months of waiting (i got broadband issues)

restarted windows and tried running the LiveCD. but the problem is, the installer got stuck in the powernowd module. i restarted it thrice and got the same problem.

i'm using a dv6000 hp laptop. any clue?

---

### Post by Kingsley on 2008-01-07
I've never had such an issue with my dv6000. Though there's a large chance our laptops are very different because of year and/or components. What processor does your dv6000 have?

---

### Post by djtreo on 2008-01-07
oh hi there!

my dv6000 is an AMD Turion 64 x2...

are there any issues on hp laptops and such?

---

### Post by Kingsley on 2008-01-07
I've seen many complaints about booting up the LiveCD on dv6000s that have the AMD processor. I've never had the issue because mine has an Intel processor. Try the suggestion in this post.

[http://ubuntuforums.org/showpost.php?p=3997130&postcount=256](http://ubuntuforums.org/showpost.php?p=3997130&postcount=256)

---

### Post by Partyboi2 on 2008-01-07
If adding noapic nolapic to boot options does not work, you could try stoping powernowd while installing then removing it.
This is related to core 2 Duo
> During install, or useage, of Edgy 32 / Edgy 64 / Feisty 32 / Feisty 64 would have random complete freeze up. It wasn't resolved until a post gave the solution, located here: [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://ubuntuforums.org/showthread.php?t=285683&page=8]("http://ubuntuforums.org/showthread.php?t=285683&page=8") 
 I stopped powernowd after startup for install: "sudo /etc/init.d/powernowd stop". After install, I removed powernowd: "sudo apt-get remove powernowd".


To add options to boot
When you get to the menu screen press F6 at the end of the line add the boot options
eg noapic then  press enter

---

### Post by djtreo on 2008-01-07
thanks guys. the noapic boot parameter works on LiveCD

a question: if i'm gonna install this thing, do i need to include the noapic parameter? i'm asking for help before i do the installation.

thanks again.

---

### Post by Partyboi2 on 2008-01-07
You will  need to add it to your grub menu.lst
to do that in a terminal (Applications>Accessories>Terminal)
```
 gksudo gedit /boot/grub/menu.lst
```look for something like this
>  ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# [COLOR=Red]kopt=root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro[/COLOR] then add noapic at the end after ro
```
# kopt=root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro noapic
```Then save.
then
```
sudo update grub
```

---

### Post by djtreo on 2008-01-07
oh :confused:

how can i get into that grub menu? sorry i'm just starting to use linux...

---

### Post by Kingsley on 2008-01-07
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Partyboi2 on 2008-01-07
Click on install. Once the system has been installed reboot 
when you see "Grub loading" on the screen. press "Esc" to enter to grub menu. (This happens not long after your pc starts to reboot)
Then press "e" to edit then highlight the line that starts with kernel and press "e" again and then at the end of that line add 
```
noapic
```then press enter, then "b" to boot
then when the system has loaded and you are at the desktop follow what I have posted in my last post. If you get stuck anywhere post back the problem.

---

### Post by djtreo on 2008-01-07
> **Kingsley said:**
> ```
sudo gedit /boot/grub/menu.lst
```

huh? :confused:

---

