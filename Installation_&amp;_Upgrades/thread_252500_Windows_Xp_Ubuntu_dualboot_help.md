---
title: "Windows Xp Ubuntu dualboot help"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by mahmudhasankajal on 2006-09-06
Hi

I am new to Ubuntu. I used Fedora 5 along with Windows XP on my machine. Then I wanted to have Ubuntu instead of Fedora and that started the problem. I have 2 HD and FC5 was on first one and winXP on the second. Grub was probably on a small partition on the second HD. Now when I installed Ubuntu, I let it erase everything on the first HD and now it won't show WinXP in the menu. Could anyone help me regarding this? Thanks a lot in advance.

Mahmud

---

### Post by lha on 2006-09-07
> **mahmudhasankajal said:**
> Hi

I am new to Ubuntu. I used Fedora 5 along with Windows XP on my machine. Then I wanted to have Ubuntu instead of Fedora and that started the problem. I have 2 HD and FC5 was on first one and winXP on the second. Grub was probably on a small partition on the second HD. Now when I installed Ubuntu, I let it erase everything on the first HD and now it won't show WinXP in the menu. Could anyone help me regarding this? Thanks a lot in advance.

Mahmud


If you have only two ide hard drives, the following should do the trick:

Open terminal (Applications->Accessories->Terminal) and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

and paste the following lines in the very end of that file.
```
title Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

---

### Post by mahmudhasankajal on 2006-09-07
Thanks for your reply.

Well I did try that but it shows an error that "NTLDR is missing". I tried to fix it with WinXP CD (fixing mbr) but seeing the warning, I didn't proceed.

Mahmud

---

### Post by lha on 2006-09-07
> **mahmudhasankajal said:**
> Thanks for your reply.

Well I did try that but it shows an error that "NTLDR is missing". I tried to fix it with WinXP CD (fixing mbr) but seeing the warning, I didn't proceed.

Mahmud

You seem to have an unusual installation. :) Please, tell us how you installed Fedora, Windows and Ubuntu. (In what order did you proceed, partitions you used...) Also, check bios settings to find the boot order.

---

### Post by mahmudhasankajal on 2006-09-07
Now I have to say I don't remember exactly. But I think I had another small partition in second HD which I had GRUB when I installed Fedora. here is the partion info which exists now-

/dev/hda1   ext3    /
/dev/hda5   swap     

/dev/hdb1   NTFS   (no access path)
/dev/hdb5   NTFS   (no access path)
/dev/hdb6   Unformatted  (no access path)

---

### Post by lha on 2006-09-10
> **mahmudhasankajal said:**
> Now I have to say I don't remember exactly. 

It seems we have way too many unknown factors here. All I can do is guess, and solving this thing by trial and error takes too much time. :( If you only remembered how you installed Windows and Fedora...

---

