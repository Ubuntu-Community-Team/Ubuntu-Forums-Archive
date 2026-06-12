---
title: "Update to kernel 2.6.24-17-386 messed up wireless"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by sco01 on 2008-05-27
Hello,

Installed the update to kernel 2.6.24-17 kernel last night. This morning I decided to reboot to complete the update installation. I thought it might be a good idea to do a profile to maybe enhance the boot performance at the same time. The machine (Thinkpad T42) booted nicely but the wireless didn't work. It turned out that the wireless radio was never turned on on boot and lshw listed the device as unclaimed. 

Booting the machine with 2.6.24-16-generic works fine, so i thought about writing a bug report on launchpad. The problem is that i can't figure out if the re-profiling might have messed up the configuration for this kernel option in Grub or if it is an actual kernel bug.

In order to sort this out, I would like to know the following:

Is there a way to undo the profiling so I can test if it actually is a kernel bug?
if not: Is there a way to undo the kernel update? 
If not: Is there a way to set 2.6.24-16-generic as default kernel in grub?

I noticed that linux-restricted-modules-2.6.24-17-generic wasn't installed. Manually installing it solved the problem. I also found Bug #235296 on launchpad that seems to cover my problem.

---

### Post by zythum on 2008-05-31
In my case (Toshiba A210-FS3), with realtek wireless network, I fix it with kernel 2.6.24-16, but now, if I boot with 2.6.24-17, it's not working.

---

### Post by euchrid on 2008-06-05
> **sco01 said:**
> Hello,

In order to sort this out, I would like to know the following:

Is there a way to undo the profiling so I can test if it actually is a kernel bug?
if not: Is there a way to undo the kernel update? 
If not: Is there a way to set 2.6.24-16-generic as default kernel in grub?


I've had similar problems with my wireless with all the 2.6.24 series.

Can't answer the first question, but in an answer to questions #2 and #3:
edit /boot/grub/menu.lst (by typing sudo gedit /boot/grub/menu.lst into a terminal). (You can swap gedit for your preferred text editor).

Scroll down to where it says
```
## ## End Default Options ##
```
and find the kernel you want to use. Make sure you highlight all of the blocks relating to the kernel, e.g.:

```

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e61ff7b5-df4b-46c5-b95f-39de2857387a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e61ff7b5-df4b-46c5-b95f-39de2857387a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

```

Cut them out and paste them at the top of the list, right under
```
## ## End Default Options ##
```

The kernels in this list (and the order they appear in) get changed every time you update the kernel through update manager or whatever, so it can get a bit irritating changing them when a whole kernel series causes problems - but it's easier than uninstalling and re-installing and compiling kernels and turning off update manager and so on...

If doing the above doesn't work, then you might have your boot set-up differently to what I believe is the default. In which case, you'll know better how to sort that out than I will.

At the top of my menu.lst, I have:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

This ensures the grub menu shows up when I boot the computer (hiddenmenu is commented out), and I have ten seconds to choose one of the other kernels. This can really help out when I've forgotten to manually edit the menu.lst (or didn't know I needed to).

By the way, it looks like this is all because of a change in wireless drivers: [http://kernelnewbies.org/Linux_2_6_24#head-62e9ebf067c978bbf70898986c0aa3904d1a3543](http://kernelnewbies.org/Linux_2_6_24#head-62e9ebf067c978bbf70898986c0aa3904d1a3543)

I can't be bothered to go through a load of manual configuration that might  get overwritten in the next kernel update, so I'm sticking to an old kernel until a new one actually works. I do wish that the Linux community in general could find a way to stop the internet from disappearing in these annoying ways. Still, when oil runs out and all the power disappears, we probably won't have an internet anyway.

Hope this all helps!

---

