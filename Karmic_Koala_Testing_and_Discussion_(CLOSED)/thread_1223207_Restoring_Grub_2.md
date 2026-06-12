---
title: "Restoring Grub 2"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2009-07-25
I know how to restore grub 1 after loading windows but I need to restore grub 2.  I am locked out of Karmic until I get grub 2 fixed.

---

### Post by Michaelg14 on 2009-07-25
I know how to restore grub 1 after installing windows but how do I get grub 2 back again.  I am locked out of 9.10 until I get grub 2 sorted out.

---

### Post by kemsiro on 2009-07-25
i found this
```
http://unpluggable.com/?p=294
```

but in here
```
http://www.supergrubdisk.org/wiki/Howto_Fix_Grub
```
they said
>   GRUB2 solution (on its own)

As long as I know GRUB2 cannot recover itself on its own. 

check it mate.

---

### Post by Michaelg14 on 2009-07-25
Thanks, that looks kind of convoluted and may not work for grub 2.  I do have grub 1 working for 9.04 but it doesn't find 9.10 on a ext4 partition.  Is there any way to fix that?

---

### Post by psyke83 on 2009-07-25
> **Michaelg14 said:**
> Thanks, that looks kind of convoluted and may not work for grub 2.  I do have grub 1 working for 9.04 but it doesn't find 9.10 on a ext4 partition.  Is there any way to fix that?

Follow the "If you messed up" section of the [Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") page. I can confirm that this restored GRUB2 after an install of Windows 7.

I didn't find any other guide that successfully restored GRUB2 except this one, as the others neglected to mention that you need to bind the /dev devices.

---

### Post by Michaelg14 on 2009-07-26
> Follow the "If you messed up" section of the Grub2Testing page. I can confirm that this restored GRUB2 after an install of Windows 7.


That worked, thank you I am back in 9.10

---

### Post by Luca_turicci on 2009-08-14
Hi there, i'm installing Win7 right now on my Hp Mini 110, i have Karmic Alpha 3 installed and updated to Alpha 4. I'm sure that i'll have some problems with groove after that, anyway, i'm planning on do a fresh install of Alpha 4 after this, if I do install Karmic after Win7 will Grub2 work fine and detect both OSs??

---

### Post by psyke83 on 2009-08-14
> **Luca_turicci said:**
> Hi there, i'm installing Win7 right now on my Hp Mini 110, i have Karmic Alpha 3 installed and updated to Alpha 4. I'm sure that i'll have some problems with groove after that, anyway, i'm planning on do a fresh install of Alpha 4 after this, if I do install Karmic after Win7 will Grub2 work fine and detect both OSs??

Yes, it should work fine (although GRUB2 labels 7 as Vista, it boots perfectly).

If the Windows entry isn't automatically added after installation, do the following:

```
$ sudo apt-get install os-prober
$ sudo update-grub2
```

That was necessary after installing Alpha 3, but it may not be necessary for Alpha 4 and later.

---

### Post by VMC on 2009-08-14
> **psyke83 said:**
> 
If the Windows entry isn't automatically added after installation, do the following:

```
$ sudo apt-get install os-prober
$ sudo update-grub2
```

That was necessary after installing Alpha 3, but it may not be necessary for Alpha 4 and later.

Thanks, this just what I was looking for. I knew it was probe something or other. I have Alpha 3 with all the updates, and yes os-prober was already install. One of the updates. I moved and deleted several of my os's and got koala grub2 working , but the other OS's didn't get installed. After os-prober, they all are found. Thanks!

---

### Post by Luca_turicci on 2009-08-15
Hey, didn't need to do anything, just installed Alpha 4 after win7 and it all works perfectly, although for some the bcm43 driver wasn't there by default, anyway, only installed it from synaptyc and it's perfect again. Thanks!

---

