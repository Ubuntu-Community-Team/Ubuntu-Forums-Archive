---
title: "Getting rid of a newer 9.04 partition"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by aqk on 2009-11-16
Hi -
 I have a laptop with Win-Vista and TWO Ubuntu 9.04 partitions on it- sda6 and sda8. The 2nd 9.04 partition was installed just to fix some brief issue with a Grub error 22, and has no updates on it.
So the grub now points to its menu.lst 

 Now- How can I get rid of this 2nd Ubuntu 9.04 "sda8" partition? 
Obviously if I just reformat its space  (and its Swap) I will lose the menu.lst that grub currently points to.

 How do I get grub to use the menu.lst on my original sda6 Ubuntu partition? 
I'd like to do it before I reformat the sda8 partition with GPARTED, so I know I won't get this %$#* Grub error 22 anymore.
 
At the moment the Win partition is the one that is active. Where the grub is, I have no idea! 
     ...Thanx

---

### Post by sisco311 on 2009-11-16
simply run:
```
sudo grub
```
then type:
```
root (hd0,5)
setup (hd0)
quit
```

done

---

### Post by aqk on 2009-11-16
Thanx, sisco311 !
It worked like a charm!  

Now all I must do is learn some of this Grub language!
And re-format that partition I no longer use.

---

