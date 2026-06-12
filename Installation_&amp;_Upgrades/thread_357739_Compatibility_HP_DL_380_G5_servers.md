---
title: "Compatibility HP DL 380 G5 servers?"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by mimizone on 2007-02-10
Did anybody install Ubuntu Dapper on HP DL380 G5 (generation 5)?

I have 3 machines coming soon and I usually use Ubuntu 6.06 LTS on my servers.
Couldn't find anything on the web about that new series and its compatibility with Ubuntu.
Just read something about NIC cards and temperature sensors not being recognized.

The HP site mentions that the machines are compatible with Debian 3.1 Sarge.
[http://h71028.www7.hp.com/enterprise/cache/433096-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/433096-0-0-0-121.html)


Any hope seeing it working directly with my Dapper server install without hacking too much around?

---

### Post by mimizone on 2007-02-23
I got my HP DL380 G5. (Quad Core Xeon, with a Raid 5 of SAS disks).

Tried Ubuntu 6.06 Server install, it stops after I select the language and the keyboard type.
It hangs on a great blue screen with a white line at the bottom
I can press enter and it scrolls the all thing up but I can't see a prompt or anything.
The other shells (F2, F3 etc...) work.

Anybody successfully installed Ubuntu 6.06 (or other) on those new HP DL380 G5?

---

### Post by mimizone on 2007-02-23
I had a quick look at the shell on F4 during the install, which is basically some logs apparently.

It loops on some problems with some USB , starting it, killing it on on address, doing it again for another address etc... and it never stops. I guess that's what hangs the install.

I put the exact log messages after the week end.

If it rings anything for anybody, like I should disable something in the BIOS or the kernel, let me know!

Thanks.

---

### Post by fortysixandtwo on 2007-02-25
> **mimizone said:**
> Did anybody install Ubuntu Dapper on HP DL380 G5 (generation 5)?

I have 3 machines coming soon and I usually use Ubuntu 6.06 LTS on my servers.
Couldn't find anything on the web about that new series and its compatibility with Ubuntu.
Just read something about NIC cards and temperature sensors not being recognized.

The HP site mentions that the machines are compatible with Debian 3.1 Sarge.
[http://h71028.www7.hp.com/enterprise/cache/433096-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/433096-0-0-0-121.html)


Any hope seeing it working directly with my Dapper server install without hacking too much around?

Hi,

I have a DL380 G5 with edgy, 64-bit.

When installing it fails to recognize the ethernet interfaces which is poor..
but after having rebooted after the install is complete I found that all NIC are working as expected. Except for one major thingie.. the localhost interface _does not_ work. After rebooting the server you need to manually set the localhost host interface to 'up'.
(And after any sequential reboot..).

Another drawback, Ubuntu seems not to be able to use the onboard RAID memory cache.
My server is a heavily hit web server and I suffer massive IO-wait, but when analysing the problem (iostat) the disks are rarely used at all so the data is cleraly stuck in the cache. I 'll disable it and report back. I guess HP uses proprietary s**t .. sad.

Ubuntu needs to focus on the 64-bit release, pretty soon 4GB is the bare minimum..


Rgds

/PL

---

### Post by mimizone on 2007-02-26
> I had a quick look at the shell on F4 during the install, which is basically some logs apparently.

It loops on some problems with some USB , starting it, killing it on on address, doing it again for another address etc... and it never stops. I guess that's what hangs the install.

I put the exact log messages after the week end.

If it rings anything for anybody, like I should disable something in the BIOS or the kernel, let me know!

Thanks.

here's part of the  logs I get with Dapper (6.06 LTS) during the installation.

[INDENT]kernel - input - HP virtual keyboard as /class/input/input443
kernel - usb - new full speed USB device using uhci_hcd and address 65
kernel - hub 5-2 : USB hub found
kernel - hub : 7 ports detected
kernel usb 5-1 : USB disconnect address 64
kernel - input - HP virtual keyboard as /class/input/input
kernel - usb - new full speed USB device using uhci_hcd and address 66
....[/INDENT]

Does it make sense to anybody?

I disable USB in the BIOS but still getting those messages.

---

### Post by mimizone on 2007-03-03
moving forward in the install of 6.06 by ignoring the USB problem (press ESC when selecting language/keyboard), the install couldn't find the NIC cards. I decided to not continue the install of Dapper at this point.

I learnt that the USB problem is resolved in recent kernels (2.6.17 or so). RedHat has backported the patch for instance, so I successfully installed a Centos 4.4.

But I decided to switch to Debian Etch 4.0 RC1 for now, being used to Ubuntu lately.
It seems to work fine. Still have to install the sensors drivers for temperature but it seems HP has the drivers for version 3.1r4.
I haven't checked if the RAID controller driver is fine. Apparently some people observed that the RAID cache is not used.

A bit sorry of having moved from ubuntu to debian :neutral: .

---

### Post by cbkm on 2007-03-12
Just wanted to add a note here to say that using the Esc method to skip over the keyboard selection when it appears will allow you to install the system.

Once the system reboots it DOES find the NIC however the syslog does scroll with the aforementioned log messages.

We're trying a dist-upgrade as I type, if that doesn't work we'll probably build another kernel for the box. but fingers crossed on the newest version of linux-image-server!

I'll keep the thread updated with how we get on.

(NB I'm not sure if we have a DL 380 or not, but it exhibits the same problem and is definitely a G5)

EDIT: The kernel version 2.6.15-28-server works fine in Ubuntu Dapper.

EDIT2: Then to clean-up the install I just needed to do the following:-

```

To fix the keyboard layout (if applicable):
$ sudo dpkg-reconfigure -plow console-data

To fix the locale warnings/errors I was getting:
$ sudo apt-get install language-pack-en-base
$ cat <<EOF | sudo tee /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"
EOF

```

Ofcourse you'll want to change the locale settings to match your needs. Then I just logged out and back in again and presto, no more locale errors. So it seems like it's possible to get Dapper LTS onto the HP G5 servers. :-)

---

### Post by mimizone on 2007-03-13
nice job.
I might give it a shot on the other boxes.
Have you look at the support of the temperature sensors of the board and hd (lm-sensors)?

Thanks for you time and for sharing all this!

---

### Post by psynode on 2007-03-15
Hey All, 

Just to give some pointers with ubuntu 6.06-1 and proliant dl 360's, 380's and installing


If you get the blank blue screen early in the installation.
Do: ctrl+f2
hit enter to get a prompt
ps aux | grep chooser
#find the 3 pids and kill them in reverse order (ie highest to lowest)
kill -9  $pid  # needs the 9 otherwise they dont die
# switch back to the first terminal ctrl+f1
# it should then have a failed screen, hit ok and go down to the next step after choosing keyboard

done

---

### Post by riptide2k on 2007-12-12
I found another solution to solve that prob here:

[https://bugs.launchpad.net/ubuntu/+source/kbd-chooser](https://bugs.launchpad.net/ubuntu/+source/kbd-chooser)

> This bug is caused by a known problem in USB port caused by iLO (a HP technology) and is solved in last dapper kernel. Installation has an old kernel but the problem can be solved removing the usb module: uhci_hcd

$ modprobe -r uhci_hcd

Then you can update to last kernel.

What i did:

- Starting Installation as usual
- When the installation hangs on the blue screen, change to the console with ALT-F2
- Execute the command above (modprobe -r uhci_hcd)
- Go back to the installer with ALT-F1
- The installer should be back again and you can finish the installation as usual

Thanks to Josué Alcalde González, who wrote about the uhci_hcd, it saved my butt.. :)

One more thing, in my case the installer has a problem with the Broadcom network card.

What i did to bring up the networking after the installer has finished his work:

- Edit the /etc/network/intefaces manually to

```
auto eth0
iface eth0 inet static
address 192.168.0.100
gateway 192.168.0.1
netmask 255.255.255.0 
```

- Restart networking with /etc/init.d/networking restart
- Done

---

