---
title: "&quot;grub problem&quot; with going back to XP"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by stampit on 2006-09-02
i had such a hard time using ubuntu that i had to go back to windows.

i formatted whatever with windows cd (acer manufacturer recoverty cd), and finished installing windows.

when i finally booted, i get an error message like this one.

GRUB loading stage 1.5. 
GRUB loading, 
please wait... 
Error 17

something like that

i looked around many posts on the forum, but i could not understand any.

can anyone give me a simplest solution to this problem?

i am going to university on monday, and i need this fixed badly.

---

### Post by NetworkGuy on 2006-09-02
I'm not sure your recovery CD allows you to do this but:

Boot your XP CD and take an "R" to enter the recovery console.

You will be asked to choose install to repair enter number and you will get prompted for admin password followed by C:WINDOWS>
at this point type FIXMBR or HELP will give you list of options.

---

### Post by stampit on 2006-09-02
no,, that didn't work..

---

### Post by Crooksey on 2006-09-02
get to the recocery console, then type.

```

fdisk /mbr
```

Then reboot!

---

### Post by stampit on 2006-09-02
> **Crooksey said:**
> get to the recocery console, then type.

```

fdisk /mbr
```

Then reboot!

"unable to open /mbr"
i get this

---

### Post by Crooksey on 2006-09-02
are you sure you are at the recovery console?

---

### Post by stampit on 2006-09-02
i am not exactly sure waht recover console is.

terminal?

i tried ctrl alt f1 as well

still unable to open /mbr

---

### Post by Crooksey on 2006-09-02
If you can get to a windows machine, download [http://1gighost.net/dalehollow/boot98se.exe](http://1gighost.net/dalehollow/boot98se.exe) install it onto a floppy, then you reboot with the floppy and, and will be greeted with a command prompt.

fdisk /mbr

---

### Post by stampit on 2006-09-02
if i don't have a floppy drive, would it be okay to do it with cd instead?

---

### Post by jISh on 2006-09-02
That is an odd problem, your Windows install doesn't install a boot loader. Possibly something to do with it being a recovery CD, those CDs I don't like.

What's happened is your stage 2 boot loader is gone, but your stage 1 (which is installed in your hard drive still) is still looking for it. Normally Windows installs it's own stage 1 MBR which would have overwritten this.

The above solution should work, as you are trying to install the Windows MBR.

---

### Post by Crooksey on 2006-09-02
> **stampit said:**
> if i don't have a floppy drive, would it be okay to do it with cd instead?

Think so.

---

### Post by stampit on 2006-09-02
> **jISh said:**
> That is an odd problem, your Windows install doesn't install a boot loader. Possibly something to do with it being a recovery CD, those CDs I don't like.

What's happened is your stage 2 boot loader is gone, but your stage 1 (which is installed in your hard drive still) is still looking for it. Normally Windows installs it's own stage 1 MBR which would have overwritten this.

The above solution should work, as you are trying to install the Windows MBR.

i searched my problem on google and in thie forum.
i realized that there are many other people who have the same problem as i do.
it seems to happen when one formats the harddrive using the windowns cd and the install windows.

---

### Post by confused57 on 2006-09-02
You may just want to reinstall Ubuntu on a small partition(approx 5 Gb) & grub should be reinstalled on the Windows mbr, so you'll at least be able to boot into Windows and have a backup OS(Ubuntu) in case you have problems with Windows.

That way, you'll have use of Windows until you can find a method to restore the Windows mbr...

---

