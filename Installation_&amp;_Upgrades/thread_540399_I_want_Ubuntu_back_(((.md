---
title: "I want Ubuntu back :((("
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by d4x2hhhy on 2007-09-01
All was fine, I originally installed drake on a win XP machine and they dual booted no worries.  Then upgraded to feisty and all was really good :)))

But then.. I wanted to run a windows game and so went back to XP but it was so full of viruses that I re-installed XP.  I then lost Ubuntu :(

I tried the stuff about grub and the hdd (0,1) etc and then neither worked!!!

My windows partition has a boot flag.

I just want them both to work or Ubuntu!  but my CDR seems to have packed up and my keyboard is wirelss (MS require you to push F8, w***ers!  cant be done on their own wireless keyboard!!!!)

So I need to be careful
My Feisty is still there Im sure and it was all setup so dont want to lose it.

Please help.....

I have the gparted cd

Dave

---

### Post by merlinus on 2007-09-01
You can use any live cd to get to a CLI (or terminal).

Then try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

For you, it may be root (hd0,1) and setup (hd0).

-merlin

---

### Post by d4x2hhhy on 2007-09-01
Ok thanks, if im not back in 5 mins....

---

### Post by d4x2hhhy on 2007-09-01
Ok some progress and it seems windows still works.
I get a boot menu (GRUB?) now

it lists some Ubuntu then windows then some more ununtu (old version)

but when i tru ubuntu:

error 17 cannot mount selected partition

Still fighting:)

---

### Post by merlinus on 2007-09-01
What did you wind up entering for root and setup that got the grub menu back?

Also, whilst booted from the live cd, post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by d4x2hhhy on 2007-09-01
hd0,2

i have wirless so cant use my internet with the live cd (beyond my wit at least)

basically fdisk -l returns:

drive details

device boot 1-5

start and end cylinders seq with 4 and 5 the same (9690 -9964)

id 7 7 83 5 82

then hpfs/ntfs
        hpfs/ntfs
       linux
       extended
       linux swap

thanks for the help, sorry for piss poor reply

---

### Post by merlinus on 2007-09-01
No need for Internet to do this.

So boot normally, press e at grub menu and change it to (hd0,2), then press b to boot and see what happens.

If that does not work, post complete output of sudo fdisk -l.

-merlin

---

### Post by d4x2hhhy on 2007-09-01
I speak to you from the hallowed land of Ubuntu!

thanks very much, its so good to be back.

Will the editing of grub be permanent?

david

---

### Post by merlinus on 2007-09-01
Excellent news!

To make the change permanent, you will need to edit /boot/grub/menu.lst to make sure all of the ubuntu kernel root entries point to (hd0,2).

Also change this line to:

# groot=(hd0,2)

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
gksudo gedit /boot/grub/menu.lst

```The first command makes a backup of the file, just in case, and the second allows you to edit and save it.

Then the change will be permanent.

-merlin

---

### Post by d4x2hhhy on 2007-09-01
ive changed all the references to 0,2 but dont see what you mean by change this line to #groot = (hd0,2)

---

### Post by merlinus on 2007-09-01
The line is after:

## DO NOT UNCOMMENT THEM, Just edit them to your needs, before all of the kernel stanzas.

Make sure it says:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

It will keep things from changing next time there is a kernel update.

-merlin

---

### Post by d4x2hhhy on 2007-09-01
Ok got it.

Thanks very much.  Think ill stay on the light side from now on.

---

### Post by merlinus on 2007-09-01
You are most welcome.  Glad to help.

Keep that light side shining!

-merlin

---

