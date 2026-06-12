---
title: "Howto reboot to latest kernel with kexec"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Xmister on 2008-05-07
If you don't know what is kexec take a look **[here]("https://wiki.ubuntu.com/RapidReboot")**.

For me kexec hasn't worked until 8.04.
The examples that I saw before just boot to the current kernel, but this will boot the newest installed one. 

First you have to install kexec-tools:
```
sudo apt-get install kexec-tools
```

Then we need to edit the reboot script.
First make a backup of it:
```
sudo cp /etc/init.d/reboot /etc/init.d/reboot_normal
```
Then edit:
```
sudo gedit /etc/init.d/reboot
```
Find the do_stop function, it looks like this:
> 
do_stop () {
	# Message should end with a newline since kFreeBSD may
	# print more stuff (see #323749)
	log_action_msg "Will now restart"
        reboot -d -f -i
}

And replace it with this:
```

do_stop () {
	# Message should end with a newline since kFreeBSD may
	# print more stuff (see #323749)
	log_action_msg "Will now restart"
	if [ -x /sbin/kexec ]; then
            kexec -l --append="`cat /proc/cmdline`" --initrd=/boot/initrd.img-`ls /lib/modules | sort -nr | head -n 1` /boot/vmlinuz-`ls /lib/modules | sort -nr | head -n 1`
            sync
            umount -a
            kexec -e
        else
            reboot -d -f -i
        fi
}

```

---

### Post by nusch on 2010-03-01
With Ubuntu 9.10 and Grub2 it hangs at "Will now restart.."
```
echo "`cat /proc/cmdline`" --initrd=/boot/initrd.img-`ls /lib/modules | sort -nr | head -n 1` /boot/vmlinuz-`ls /lib/modules | sort -nr | head -n 1`
```
gives me:
```
BOOT_IMAGE=/vmlinuz-2.6.31-19-server root=UUID=33748a9d-1ee5-4931-9188-9927ffd3922a ro quiet splash --initrd=/boot/initrd.img-2.6.31-19-server /boot/vmlinuz-2.6.31-19-server
```
Is it correct or new grub is messing something?

---

### Post by Skaperen on 2010-03-01
The boot loader does not run when using kexec.  Think of the first running Linux as the boot loader.  It loads the image of the new kernel to run (which might even not be Linux) and runs it in place of itself.  If it never gets there, something is clearly wrong, but it's not GRUB in this case.

---

### Post by fman23 on 2011-08-20
I do realize this thread is old, but one thing could be fixed in the script for people stumbling on this page like I did.

To make the script more accurate in choosing the latest kernel installed, you should use sort -**V**r instead of sort -**n**r.  This sorts the input by version but not necessarily number.  Executing "ls /lib/modules | sort -nr | head -n 1" on my computer returns 2.6.38-8-server which is not the latest installed, but executing "ls /lib/modules | sort -Vr | head -n 1" returns 2.6.38-11-server which is the latest installed.  The corrected do_stop() function should look like this.
```
do_stop () {
	# Message should end with a newline since kFreeBSD may
	# print more stuff (see #323749)
	log_action_msg "Will now restart"
	if [ -x /sbin/kexec ]; then
            kexec -l --append="`cat /proc/cmdline`" --initrd=/boot/initrd.img-`ls /lib/modules | sort -Vr | head -n 1` /boot/vmlinuz-`ls /lib/modules | sort -Vr | head -n 1`
            sync
            umount -a
            kexec -e
        else
            reboot -d -f -i
        fi
}
```

---

### Post by steve11911 on 2011-08-22
I am surprised at the number of views on this topic so I did a quick dig.There is solid evidence that kexec is stable for 2.6.38.The author of the page linked below points a finger at the cause of kexec related issues:

[https://lkml.org/lkml/2011/3/17/235](https://lkml.org/lkml/2011/3/17/235)


youtube gentoo kexec 2.6.38:

[http://www.youtube.com/watch?v=ZGvIQ47uEuQ](http://www.youtube.com/watch?v=ZGvIQ47uEuQ)

---

### Post by dacresni on 2011-12-21
does this package work with crash or lcrash the crashdump programs? are there instructions to make LKCD work with grub2?

---

