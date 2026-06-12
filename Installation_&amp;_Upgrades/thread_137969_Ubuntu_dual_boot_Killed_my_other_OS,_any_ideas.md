---
title: "Ubuntu dual boot Killed my other OS, any ideas???"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by ecujak on 2006-03-01
I have dual booted windows with FC1-4, Mandrake 7-10, a few Suse and Solaris10.

Only now when trying ubuntu do I loose my WinXp boot.

Although I really like Ubuntu, I really need both systems to reside on the same machine. I hope Breezy didn't badger my WinXp to death.

this is what my grub bootloader has for my winXp boot. Is this my problem or does this part look ok.
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1


I don't have any problem with ubuntu, just can't access all my old files now.........can anyone help me get my crappy windows to boot?

---

### Post by ecujak on 2006-03-01
My Windows Partion is actually on hda5.

---

### Post by schmappel on 2006-03-01
I think it is pointing to the wrong partition. If i'm not mistaken the first number points to the harddrive and the second number points to the partition. Try changing

```
root (hd0,0)
```

to

```
root (hd0,5)
```

If it doesn't work, please post the contents of both /boot/grub/menu.lst and /boot/grub/device.map so i can try and help you.
If you want more info on GRUB, this is a good [resource]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by Luke771 on 2006-03-01
Well if hd0,0 = hda1
then hda5 = hd0,4

So you should actually change```
root (hd0,0)
```to```
root (hd0,4)
```
Anyway, if hd0,5 dont work, then hd0,4 will.
and if hd0,4 wont work then hd0,5 should.
and if neither one works...
what the he££: scrap windows!

---

### Post by schmappel on 2006-03-01
Whoops, you're right Luke! (Check out my new sig...)

---

### Post by Luke771 on 2006-03-01
WAIT! WAIT! I GOT IT! I GOT IT!

I was wrong too!

Hda5 is the "first logical partition" no matter how many primary partitions you have (max 3),
*But* the boot loader will only count the partition starting from zero,  and *not* look at their names; so hda5 could be the third, the fourth or the fifth partition (and the extended partition containing it would be respectively the 2nd, 3rd or 4th). 

So the correct solution is: count the number of primary partitions starting @ zero, add 1 for the ext partition, and use the result to point the boot loader;
so, if there is only one primary partition, the line would be:```
root (hdo,3)
```changing to ```
root (hd0,4)
``` if the primary partitions are two, and so on.

BTW I could still be wrong, and maybe you dont have to count the extended partition after all, in which case you dont need to add 1 to the partition count, and the line would be:```
root (hd0,1)
``` if you have one primary partition;```
root (hd0,2)
``` for two primary partitions etc.

And if you keep trying with all the possible lines, you will get it right sooner or later anyway :-)

---

### Post by jibril on 2006-03-01
I have the same problem except that in the file, there is no option for windows even though i have windows installed.

and when i tried to write to it, it refuses saying i dont have enough previleges.

HELP

jibril

---

### Post by schmappel on 2006-03-01
You can edit the file using root privileges by opening through console, but first make a backup:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Enter your password when asked.

Then open the file for editing with sudo:
```
sudo gedit /boot/grub/menu.lst
```

Again, enter your password when asked.

Didn't Ubuntu 'see' your Windows OS during install? If it's not already there you need to add a section like the following:

```
title Microsoft Windows
root [COLOR="YellowGreen"](hd0,0)[/COLOR]
savedefault
makeactive
chainloader +1
```

Change the [COLOR="YellowGreen"](hd0,0)[/COLOR] part to match the location of your Windows partition (see Luke's post for details).

---

### Post by jibril on 2006-03-01
I type "su" at the prompt and it tells me that password incorrect, not sufficient previliges :(

I only set one password , how come i dont have previliges ?

Jibril

---

### Post by PhilOSparta on 2006-03-01
If you came from another distro you are used to using [COLOR="Red"]su[/COLOR] to gain root access.
Ubuntu doesn't allow you to use su.  Instead, use [COLOR="Red"]sudo[/COLOR] and the command of the action that you want. Example:  sudo gedit /boot/grub/menu.list

That will allow you root privledges to edit the root owned file.

---

