---
title: "Want to revert back to 14.04 from 16.04.................."
date: 2016-08-15
forum: Installation &amp; Upgrades
---

### Post by wolfie52 on 2016-08-15
After several attempts to install 16.04 from CD and whilst a "version" runs, I have no printer connect, unable to get my files, cannot load Adobe ad infinitum. 

I run a 32 bit Packard Bell
Memory 2 GiB

Either how can I resolve or maybe ideally (?) can I rever t back to the safety of 14.04

Finally, a throw away comment. Is it perhaps time to dump my current machine and upgrade? 


```

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           232.9G            
&#9500;&#9472;sda1 ext4   130.3G            
&#9500;&#9472;sda2            1K            
&#9500;&#9472;sda3 ext4    38.8G            
&#9500;&#9472;sda5 swap     3.8G [SWAP]     
&#9500;&#9472;sda6 ext4    24.6G            
&#9500;&#9472;sda7 ext4    17.6G /          
&#9492;&#9472;sda8 ext4    17.8G            
sr0            1024M

```

```

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  140GB  140GB   primary   ext4            boot
 3      140GB   182GB  41.6GB  primary   ext4
 2      182GB   250GB  68.5GB  extended
 8      182GB   201GB  19.1GB  logical   ext4
 6      201GB   227GB  26.4GB  logical   ext4
 7      227GB   246GB  18.9GB  logical   ext4
 5      246GB   250GB  4096MB  logical   linux-swap(v1)

```

```

Filesystem      Size  Used Avail Use% Mounted on
udev            990M     0  990M   0% /dev
tmpfs           202M  6.5M  195M   4% /run
/dev/sda7        18G  6.8G  9.6G  42% /
tmpfs          1007M  103M  905M  11% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs          1007M     0 1007M   0% /sys/fs/cgroup
tmpfs           202M   60K  202M   1% /run/user/1000

```

---

### Post by Bashing-om on 2016-08-15
wolfie52; Hello;

My thought, as many 32 bit applications have or will loose support in our 64 bit world ; I would give consideration to installing a 64 bit release .
What returns:
```

sudo lshw | grep "description: CPU" -A 12 | grep width

```
It says clearly whether it's 64 or 32 bits (may take a little while to finish).

Additionally:
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware. I have experienced great results with (l)ubuntu on older hardware systems .

As to the time to dump the current machine .. well, that all depends on your use case ! There are several things one can do to an old box to extend it's usefulness .
Easiest and best is to install additional ram .. 2 more Gigs will make a world of difference .
IF the data buss is SATA .. then one could get a huge jump in performance with replacing the old spinning hard drives with SSD(s).

These will be much more cost effective than replacing the machine . -  Though an 8 core AMD or Intell I7 system sure would be Nice !

[INDENT][INDENT]use case
[INDENT][INDENT][INDENT]bottom line
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-08-15
What video adapter? How much video memory? As you have Ubuntu installed run this command:

```
/usr/lib/nux/unity_support_test -p
```

This is what I see
> 
graham@Ub1604:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 11.2.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

If you see anything different then your video adapter cannot run Ubuntu with its 3D Unity user interface.

Regards

---

### Post by wolfie52 on 2016-08-15
Thank you Basing-om

I never ever thought of using a version other than Ubuntu, considered it a compromise, which of course it is, but I am only a light user so perhaps this will suit my current situation. 

I ran the code you suggested and the result was: [B] width: 64 bits

[/B]So, hey, I still have the need to dump or get back to a useable situation with 16.04, but I really appreciate the comments you make.

Again many thanks

---

### Post by wolfie52 on 2016-08-15
grahammechanical


Thank you. Here is the result of your code suggestion.

```

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL version string:  3.0 Mesa 11.2.0


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

```

So I guess all is well from video adaptor

---

