---
title: "Where is grub menu.lst??"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-07-31
Hi

I just installed alpha 3 and i dont see any menu.lst in /boot/grub.

Grub 2 didnt detect my windows OS,so i need to add this manually.





rajeev

---

### Post by doas777 on 2009-07-31
nothing to see here

---

### Post by phenest on 2009-07-31
Look at the link for Grub2 in my signature.

---

### Post by psyke83 on 2009-07-31
See: [http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)

Don't edit any configuration files - simply run "sudo update-grub".

---

### Post by rajeev1204 on 2009-07-31
> **psyke83 said:**
> See: [http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)

Don't edit any configuration files - simply run "sudo update-grub".


Ugh that didnt work for me even though i see a windows xp entry in grub.cfg.

Looks very complex now, there goes whatever i had learned about repairing grub :)

---

### Post by Slug71 on 2009-07-31
Try running

```
sudo os-prober

sudo update-grub
```

---

### Post by rajeev1204 on 2009-07-31
> **Slug71 said:**
> Try running

```
sudo os-prober


```

command not found.

---

### Post by wayne_cat on 2009-07-31
os-prober is in the package "os-prober"

[http://packages.ubuntu.com/de/karmic/i386/os-prober/filelist](http://packages.ubuntu.com/de/karmic/i386/os-prober/filelist)

```
sudo apt-get install os-prober
```

---

### Post by rajeev1204 on 2009-07-31
> **Slug71 said:**
> Try running

```
sudo os-prober

sudo update-grub
```

> **wayne_cat said:**
> os-prober is in the package "os-prober"

[http://packages.ubuntu.com/de/karmic/i386/os-prober/filelist](http://packages.ubuntu.com/de/karmic/i386/os-prober/filelist)

```
sudo apt-get install os-prober
```


Thanks a lot guys,it says at the end , windows xp too :)



rajeev

---

