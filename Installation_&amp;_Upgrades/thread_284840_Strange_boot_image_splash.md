---
title: "Strange boot image splash"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Sargonmetal on 2006-10-26
Hi,

I've just upgraded to edgy and when rebooted I really got scared when watching a strange boot screen, placed in the up right corner of the screen and about 400x600.
It is like some graphs (like a square and a circle I think), sorrounded by colours like when watching the very beginning of an old VHS tape.
Tehre's also a progress bar in the middle of this, and when it is done, i get to the system totally fine.
Does anybody know what is going on? 
Oh, and when I shutdown the computer, I can see a great Ubuntu splash and a progress bar placed in the correct place.

Thanks!!

[**EDIT**]: It was a problem of my linux kernel. **Installing the linux-generic package** from synaptic solved the problem for me.

---

### Post by magicfab on 2006-10-27
That is weird. During development some drwaft . placeholder artwork looked like what you mention. Perhaps look for any packages containing "usplash" and reinstall them via synaptic.

---

### Post by Sargonmetal on 2006-10-27
I've reinstalled my usplash packages (usplash and usplash-theme-ubuntu) and still doesn't work.

Man, this is weird indeed...

Any other ideas or suggestions?

Thanks!

---

### Post by magicfab on 2006-10-27
Did you remove them completely first (from synaptic, remove completely)...?
Watch for dependencies in case remove them removes other important packages, though.

---

### Post by Sargonmetal on 2006-10-28
Yes, I have removed them completely before.

I even have rebooted the system once I removed them completely and the same image appeared in the booting process.

When I reinstalled them (with their dependences), everything kept going the same wrong way :(

Any other ideas?? It really annoys me...

Thanks!

---

### Post by almalaci on 2006-10-28
I have the same problem but unlike you I haven't tried to do anything about it.No ideas other than we could probably join all the threads about this and similar boot splash issues into one if the problems are the same.

---

### Post by Sargonmetal on 2006-10-28
I feel "better" now that I know I'm not the only one :rolleyes: 
Do you know of a better thread to write about this strange "bug"?

---

### Post by tszanon on 2006-10-28
Here's the weird image.
I upgraded to Edgy just changing the sources.list (from dapper to edgy)...I just read that I should not have done this. :( 

What should we do, reinstall from scratch?

---

### Post by Sargonmetal on 2006-10-28
I just did it the way I saw in some ubuntu page. Opening the update manager with some parameters.
And indeed, that's the same screen that I see, but I can't see the processes :(

---

### Post by tszanon on 2006-10-28
In order to see the processes being loaded, I read in some other thread that you have to remove the "quiet" from kernel parameter list in /boot/grub/menu.lst.

Example:
Change
```
title		Ubuntu, kernel 2.6.17-10-generic Default
root		(hd0,0)
kernel		/vmlinuz root=/dev/md0 ro quiet splash
initrd		/initrd.img
savedefault
boot
```

to

```
title		Ubuntu, kernel 2.6.17-10-generic Default
root		(hd0,0)
kernel		/vmlinuz root=/dev/md0 ro splash
initrd		/initrd.img
savedefault
boot
```

Don't be scared when you see some code scrolling before the splash screen appears :)

Back on topic: I haven't tried anything to solve the problem. Right now, I'm downloading the Alternate CD. Probably I'll reinstall the whole system.

---

### Post by tszanon on 2006-10-28
I took a look in Synaptic and found out that the package usplash-theme-ubuntu wasn't installed.

I installed it and now the splash screen is gray-scaled, like the attached picture. Wasn't it supposed to be in color? Or is this gray-scaled image the right one?

And, as you can see, the progress bar is divided in some parts. Before installing the usplash-theme-ubuntu package, it wasn't divided.

I'll check Synaptic for some other packages that apparently should be installed.

---

### Post by John.Michael.Kane on 2006-10-28
> **tszanon said:**
> I took a look in Synaptic and found out that the package usplash-theme-ubuntu wasn't installed.

I installed it and now the splash screen is gray-scaled, like the attached picture. Wasn't it supposed to be in color? Or is this gray-scaled image the right one?

And, as you can see, the progress bar is divided in some parts. Before installing the usplash-theme-ubuntu package, it wasn't divided.

I'll check Synaptic for some other packages that apparently should be installed.

The gray splash I believe affects 64bit users.

---

### Post by tszanon on 2006-10-28
You probably are right, as I'm a 64-bit user.

Anyway, I'm getting prepared to do a complete reinstall. I want to resize my RAID-0 partitions and, as far as I know, I can't do it without reinstalling the hole system.

---

### Post by featherking on 2006-10-28
I too am getting this screen, but mine doesnt quite fill the whole screen, it just appears in the upper right corner when i boot and shutdown. I have tried reinstalling the usplash* packages to no avail. Even running
```

sudo update-alternatives --config usplash-artwork.so
```

seems to have no effect. I see two options when i run that command, minimalistic and ubuntu-theme-splash. Changing between them doesnt seem to do anything

---

### Post by IbeeX on 2006-10-28
amd64 user and same thing here,

I rely think that developers should buy few 64 bit machines. :)

---

### Post by featherking on 2006-10-28
Actually my machine is 32-bit so perhaps its not limited to just 64-bit after all

---

### Post by MmmSkyscraper on 2006-10-28
I also get the monochrome splash with 64-bit.

---

### Post by Sargonmetal on 2006-10-29
I finally solved the problem.
I don't know why, but it was the kernel image I had (linux386 2.16.17-10). I installed the generic one (linux-generic package) and everything went fine. Great splash image btw! :)

I have the usplash and the usplash-theme-ubuntu packages. I hope you find this useful!

And many thanks for the replies :)

---

### Post by tszanon on 2006-10-29
I reformatted and reinstalled from the alternate cd.
Everything seems to be fine now (as before), but the login screen is still gray-scaled (as before).

The generic kernel was installed by default, and when I tried to install the specific one (amd64-k8 ), I found out that it is obsolete, and that the generic is the right one.

So, reinstalling from scratch is not the solution to this problem. At least, not for me.

---

### Post by OceanSoul on 2006-10-29
I have the same error. 64 bits architecture.
The problem is with the kernel, as all of you seem to know. I have reinstalled Dapper Drake and I'm reupgrading to Edgy Eft.
I had this problem once, when I installed Dapper Drake and made the upgrade, with linux-generic and linux-restricted-modules and linux-image, and that sort of stuff.
I don't know what I will do when the upgrade is complete, because I know that if I restart the system that error will appear. Because of this I will not be able to restart, and I will have to solve the problem before restarting.

What should I do?  "sudo apt-get -f install" so I can see if there's anything wrong? How can I see if I will have that problem without being stuck? :\

Thanks in advance.

---

