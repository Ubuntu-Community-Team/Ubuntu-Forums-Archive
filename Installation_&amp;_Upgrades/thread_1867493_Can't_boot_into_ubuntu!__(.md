---
title: "Can't boot into ubuntu!  :("
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by link15 on 2011-10-23
I used grub customizer to change my grub boot menu but I unticked the "new entries" for linux and now I'm posting this from a livecd (WAY faster then my windows insall) any suggestions on what to do?

---

### Post by subhadip_sky on 2011-10-23
Why don't you use a live CD and reinstall the GRUB?

---

### Post by mörgæs on 2011-10-23
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by raja.genupula on 2011-10-23
> **mörgæs said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

+1 
one more thing , i think this also going to work for you.

do this 

 ```
sudo dpkg-reconfigure grub-pc
```
install grub to your hard disk.

All the Best.:D

---

### Post by link15 on 2011-10-23
thanks I'll try those and tell you if it works :D

---

### Post by link15 on 2011-10-24
ok I tryed the boot repair but all it did was remove grub :( any other suggestions?

---

### Post by raja.genupula on 2011-10-24
> **link15 said:**
> ok I tryed the boot repair but all it did was remove grub :( any other suggestions?
have you tried #4?

---

### Post by link15 on 2011-10-24
> **raja.genupula said:**
> have you tried #4?
whats #4?

---

### Post by link15 on 2011-10-24
> **raja.genupula said:**
> +1 
one more thing , i think this also going to work for you.

do this 

 ```
sudo dpkg-reconfigure grub-pc
```install grub to your hard disk.

All the Best.:D
I also tried that command but it said grub was not installed

---

### Post by link15 on 2011-10-24
I tried this but it didn't do anything
```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

---

### Post by raja.genupula on 2011-10-25
> **link15 said:**
> I tried this but it didn't do anything
```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```


HI man , this is everything . just look here 
 [U][http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

_all the best._
[/U]

---

### Post by link15 on 2011-10-27
I just gave up and backed up my files and re-installed. Thank you everyone for your help (this forum is awesome :D)

---

