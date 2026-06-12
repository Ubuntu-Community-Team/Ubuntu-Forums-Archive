---
title: "Nvidia problem with generic kernel."
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by Freddy on 2006-11-05
Hi all, I just installed Kubuntu once again after using Ubuntu Breezy for several months. With this new version I have stumbled on some problems with the new generic kernel and installing my gf 6800gt. 

When trying to install nvidia-glx it seems to have the i386 version of the kernel as a dependency. What to do ?   /// Freddan

---

### Post by Freddy on 2006-11-05
I'm confused. I managed to install nvidia-glx without the i386 kernel. I just had to install linux-restricted-modules-generic meta package which include the nvidia kernel to. After that I rebooted and installed nvidia-glx without any fuzz but when trying to "sudo nvidia-glx-config enable" through my console I got.> error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.What to do ???   /// Freddan

---

### Post by Freddy on 2006-11-05
Bump

---

### Post by highneko on 2006-11-06
I'm getting a very similar problem. Windows draw slowly when moved like lag. I did everything you did, and get the same message saying I have no driver installed. I tried a reconfigure but it didn't help and it made my screen resolution worse so I restored the backup xorg.conf. 

I use AMD Athlon 64 X2 Dual-Core with Edgy x86, NVIDIA GeForce 6150 LE. The AMD64 desktop livecd wouldn't work so I used the x86. Any ideas?

---

### Post by Freddy on 2006-11-06
Where have every 1337 linux gurus gone, are they all tired of Ubuntu and switched distro :-).
+ BUMP

---

### Post by Freddy on 2006-11-06
I tried to install the i386 kernel along with the restricted modules for that kernel and I'm getting the same freaking problem when trying to enable nvidia-glx...I'm sad now.   /// Freddan

---

### Post by highneko on 2006-11-07
Shortly after posting my last message in this thread yesterday I got it working. I used this tutorial to get it working, I suggest printing the tutorial if you're gonna try it. Good luck. [http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

---

### Post by hawkeye69 on 2006-11-13
> **Freddy said:**
> I'm confused. I managed to install nvidia-glx without the i386 kernel. I just had to install linux-restricted-modules-generic meta package which include the nvidia kernel to. After that I rebooted and installed nvidia-glx without any fuzz but when trying to "sudo nvidia-glx-config enable" through my console I got.What to do ???   /// Freddan

Same here. Found a solution which worked for me:

Don't type "sudo nvidia-glx-config enable" as shown in the drivers description. Use "sudo nvidia-xconfig"

Dunno when they changed that and why it's not shown in the description.

---

### Post by neighborlee on 2006-11-14
> **hawkeye69 said:**
> Same here. Found a solution which worked for me:

Don't type "sudo nvidia-glx-config enable" as shown in the drivers description. Use "sudo nvidia-xconfig"

Dunno when they changed that and why it's not shown in the description.

how odd...thought id try edgy and came upon this....im beginning to think that these '6 mo  release cycles' are too fast because something like this I believe is due to people being stress on schedules...while I would NEVER stick up windows as being the pride and joy of my OS experiences I have never seen the nvidia driver not install there ever, proving a point here I guess that a 6 mo cycle is risky ? ;). Not everyone is going to think to check the forums as some newbies wont even KNOW what a forum is :-).. )

cheers
neighborlee()

---

### Post by jonesyp on 2006-11-23
That worked for me as well.  Thanks!  I think it is all to do with Legacy drivers. I have a Gforce2 Ti4200.

The only thing is, that I don't get the Nvidia splash page come up.  Is that common?

---

### Post by durward on 2006-12-31
[http://forum.beryl-project.org/topic...nvidia-drivers](http://forum.beryl-project.org/topic...nvidia-drivers) currently is unreachable. Now what? My screen driver is not working properly.

Dur

---

### Post by chriswyatt on 2007-02-22
Hi, newby here.  I'm confused :confused: .

I'm also having trouble using "sudo nvidia-glx-config enable"

When I use "sudo nvidia-xconfig" do I need to have "nvidia-xconfig" installed, when I install this I have to remove "nvidia-glx", does this mean "nvidia-glx" is not needed because Glide functionality is already built in to the NVidia drivers?  Anyway, I did this but performance hasn't increased.

By the way I have an NVIDIA GeForce Go 7200 TurboCache supporting 128MB, my mainboard also has an on-board graphics chipset, though I'm pretty sure Ubuntu is using this as it shows that the NVidia drivers are intalled.

Any help would be greatly appreciated.

---

