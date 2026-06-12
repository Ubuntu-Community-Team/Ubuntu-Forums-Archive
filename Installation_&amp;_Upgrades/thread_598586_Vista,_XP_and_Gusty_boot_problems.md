---
title: "Vista, XP and Gusty boot problems"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Amorphous_Snake on 2007-10-31
A friend insisted that he tries Gusty. He had XP on hd0,0, then he installed Vista previously on hd0,5. When I installed Gusty for him, I did so by wiping out XP and installing Gusty on hd0,0.

Now Ubuntu boots fine, but it didn't detect Windows at all. I tried to add entries into menu.lst but it just didn't work. I get error 13 on Grub.

My friend started to panic. I tried Super Grub Disc, and again it didn't work.

The strange thing is the Vista DVD didn't boot, although it booted on another PC at his home. He is buying another DVD burner tomorrow anyway and I will take my copy of Vista to him in case his copy was scratched.

I need help, I am not at his place right now, but he can follow any instructions or if he can't I will do them for him tomorrow. I really don't want this to end in a Windows reinstall. I think he will never ever use Linux again if this happens!

---

### Post by Fire_Chief on 2007-10-31
You mentioned that he installed Vista on hd0,5...just out of curiosity, what are the other 3 partitions on the system (hd0,1   hd0,2   hd0,3) being used for? It's not often you run across a Windows desktop system with that many partitions on the same drive. If you can post the menu.lst file from the system (boot to live cd, then mount and view /boot partition) it would be very helpful in troubleshooting the problem.

---

### Post by jennymanda on 2007-10-31
Gusty? Freudian slip or?

---

### Post by Amorphous_Snake on 2007-11-01
> **Fire_Chief said:**
> You mentioned that he installed Vista on hd0,5...just out of curiosity, what are the other 3 partitions on the system (hd0,1   hd0,2   hd0,3) being used for? It's not often you run across a Windows desktop system with that many partitions on the same drive. If you can post the menu.lst file from the system (boot to live cd, then mount and view /boot partition) it would be very helpful in troubleshooting the problem.

I don't have access to his PC now, I will post the file when I go to him. In the meantime, I need a brainstorm here so that by the time I go to him, I have a solid solution!

---

### Post by Fire_Chief on 2007-11-01
Ok, no problem...

Assuming that Vista was installed prior to Gutsy (which I believe you said is the case), you can edit the menu.lst file and manually add the entry for booting Vista. It should look something like this
```
title            Vista
rootnoverify     (hd0,1) 
savedefault
makeactive
chainloader      +1
```

I don't have the savedefault line in my menu.lst file and Vista boots without a problem. Of course, you'll need to change the partition it looks at from hd0,1 to hd0,5. You probably want to remove any other boot entries for Vista to prevent any confusion long term.

---

### Post by Amorphous_Snake on 2007-11-02
Thanks everyone. But the porblem was solved.

It seems that what happened had no relation to Ubuntu or Linux in general, just the fact that I deleted the Windows XP partition. Stupid Vista had no bootloader (NTLDR) in its partition and that's why Super Grub Disc couldn't do anything. The partition was simply unbootable. Everything was on the XP partition.

I repaired the system using the Vista DVD on the new DVD drive that my friend bought (it turns that his older one was failing) and everything worked.

Unfortunately, my friend decided to remove Ubuntu. He told me that he knows that it wasn't Ubuntu's fault, but he just doesn't want it anymore. Oh, well... *So it goes.*

---

