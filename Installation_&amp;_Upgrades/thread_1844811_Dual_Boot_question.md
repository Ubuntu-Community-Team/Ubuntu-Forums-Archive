---
title: "Dual Boot question"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by ti84plus on 2011-09-15
So I have Ubuntu 10.04 installed and Windows 7 installed on my toshiba laptop. I only gave ubuntu 20 gb of mem because i didnt think i would use at much. Now its full and i want to decrease windows 7 mem and increase ubuntu by a lot. Im also looking to get ubuntu 11.04. Is there an easy process to get both things done simultaneously? I was think if i use a bootable 11.04 disk, then would it prompt me for the ubuntu partition size again? I know about gparted but im not sure how to use.

---

### Post by YesWeCan on 2011-09-16
Hi and welcome. :)
I think this will help you: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Back up vital files before you mess with partitions.

---

### Post by Blasphemist on 2011-09-16
Run GParted in your ubuntu. What you need to do is shrink the size of the windows partition then expand the extended partition to include that new free space. Then you can increase the size of your existing ubuntu partition and create any new ones you want to and have room for. I originally had just the situation you describe. Win 7, added ubuntu, needed more space for linux, did as I describe here. This screen shot is what my drive looks like now in GParted. Think this through in detail till it all makes sense and ask us questions to get there as much as needed. You can run this command to let us see your partitions now, or show us your GParted screen shot.
```
sudo fdisk -lu
```

---

