---
title: "nvidia driver select in grub2"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bluesscream on 2009-10-10
Nvidiadriver 173.14... for my geforce 5200fx works in generic kernel but not in -rt. Also there are experiences that proprietary-drivers in realtime kernels impair performance and latencies.
So I asked aunt Google for help and found this: 
[wiki.ubuntuusers.de/Treiber_per_Grub_wählen]("wiki.ubuntuusers.de/Treiber_per_Grub_wählen")
It's written in my native language and for legacy grub, so I had to use my own brain a little.
Here is the switch:
altoptions I had to ignore cause there is no such option in new /etc/default/grub
But elsewhere I followed this wiki - tx to the author:
As root I copied /etc/X11/xorg.conf to /etc/X11/xorg.conf.nv and /etc/X11/xorg.conf.nvidia and edited them for the suitable drivers.

/proc/cmdline is created by grub at boot-time and contents the optional commands to be run at start time.
 
As root I created /etc/init.d/DriverSelect.sh
for the following script:

```
#!/bin/sh
if grep -q nvdriver /proc/cmdline
then
        cp -lf /etc/X11/xorg.conf.nv /etc/X11/xorg.conf
else
        cp -lf /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
fi

```
made it executable
and run

```
sudo update-rc.d DriverSelect.sh defaults 10
```

to make it run at start up

I remembered there was a file in /etc/grub.d named 40_custom:
 
As root I opened /boot/grub/grub.conf and copied menuentry of 2.6.31-6-rt into this 40_custom
and added (nv) to title and nvdriver to boot line, 
so looks my new 40_custom like:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu, Linux 2.6.31-6-rt (nv)" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 0f2825f0-1aee-45ef-a7d6-85d2d8227c3e
	linux	/boot/vmlinuz-2.6.31-6-rt root=UUID=0f2825f0-1aee-45ef-a7d6-85d2d8227c3e ro   nvdriver
	initrd	/boot/initrd.img-2.6.31-6-rt
}

```
Now ```
sudo update-grub
```
reboot and select the  entry with (nv), it's at the end of the list.
If you select an other entry it will start with proprietary nvidia driver (as long as it's properly installed)

---

### Post by hanzomon4 on 2009-10-10
Nice!

---

### Post by trulan on 2009-10-10
Good stuff Blues - thanks for sharing!

---

### Post by trulan on 2009-10-11
I had to google one step in your process to figure it out:
Make DriverSelect.sh executable:
```
sudo chmod +x DriverSelect.sh
```It is working, except:
I seem to need to reboot twice for the changes to take effect.  I guess X is starting before the script is run, so while xorg.conf will be changed during boot-up, X will load with whatever settings were in xorg.conf on the previous boot-up.  It's still a useful trick, but we need to figure out how to run your script before X starts for this to be a complete fix.

---

### Post by bluesscream on 2009-10-11
If you only use this method for automatically selecting the fitting graphicdriver at booting -generic xor -rt kernels, editing /etc/grub.d/40_custom is not needed. 
Let system read out /proc/version instead of /cmdline. Just edit (create if you didn't before)

/etc/init.d/DriverSelect.sh
as follows:

```
#!/bin/sh
if grep -q -e -rt /proc/version
then
        cp -lf /etc/X11/xorg.conf.nv /etc/X11/xorg.conf
else
        cp -lf /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
fi
```

If you not have done this before
make sure it's executable ```
sudo chmod +x DriverSelect.sh
```, and ```
sudo update-rc.d DriverSelect.sh defaults 10
```
You can restore original /etc/grub.d/40_custom, remove it's x-flag ```
sudo chmod -x /etc/grub.d/40_custom
``` and again ```
sudo update-grub
```.
Make sure  Section "Device" in /etc/X11/xorg.conf.nv 
```
Section "Device"
    Identifier     "Device0"
    Driver         "nv" 
    VendorName     "NVIDIA Corporation"
EndSection
```
and in
/etc/X11/xorg.conf.nvidia  
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation"
EndSection
``` 
are edited for the suitable drivers
Now for me on selection of each -rt kernel ubuntu starts with driver "nv" and on a -generic with "nvidia"

---

### Post by trulan on 2009-10-11
> **trulan said:**
> It is working, except:
I seem to need to reboot twice for the changes to take effect.  I guess X is starting before the script is run, so while xorg.conf will be changed during boot-up, X will load with whatever settings were in xorg.conf on the previous boot-up.  It's still a useful trick, but we need to figure out how to run your script before X starts for this to be a complete fix.
I'm not sure what was going on the first few times I rebooted, but it is working properly now.  Driver selection changes on one reboot - no need to reboot twice for it to take effect.  Must have been a fluke or something.  Again, it is working correctly now.

Thanks again!

Edit: It did it again - made me reboot twice to take effect.  Not a big deal, this is still better than nothing, just an FYI.

---

### Post by ranch hand on 2009-10-11
That is really nice.

I added it to the links on;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by motin on 2009-10-19
Thanks, driver select on boot makes this a bit easier... Using a hybrid:

```
#!/bin/sh
if grep -q -e -rt /proc/version
then
	if grep -q propnvidia /proc/cmdline
	then
	        cp -lf /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
	else
	        cp -lf /etc/X11/xorg.conf.nv /etc/X11/xorg.conf
	fi
else
        cp -lf /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
fi

```

So that I can choose to use the nvidia driver as well in rt mode in hope that some day it will work better...

Using the latest rt and 185 nvidia drivers from karmic repos and still no-go with stable graphics... Tracking my progress and have collected some valuable information in [http://ubuntuforums.org/showthread.php?p=8127639](http://ubuntuforums.org/showthread.php?p=8127639) on the subject...

---

### Post by bluesscream on 2009-10-20
fine :) That's a quick and easy way to construct and select other customized boot options too -
select kernel in grubmenu, type e, add customized command to boot line, type ctrl+x....

---

