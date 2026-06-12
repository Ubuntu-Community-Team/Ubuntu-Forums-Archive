---
title: "Ubuntu 8.10 very slow"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by cleocirjh on 2008-10-30
The boot and de install of ubuntu 8.10 is very slow on my notebook HP 6515b (Turion64). After install the system also very slow. I have test with i386 and amd64 and the same problem.

On previus 8.04 version I no have problems.

????


I detected the problem:
When ACPI enabled on boot options, then very slow boot and instalation.
When ACPI disabled on boot with option "acpi=off" then normal boot speed and instalation.

I wait for this problem fix !

---

### Post by lemming465 on 2008-10-31
Edit /boot/grub/menu.lst after the install and make sure that "acpi=off" is included on the kernel line to make your fix permanent.  A lot of BIOS have very buggy ACPI implementations, which are tested only with Windows XP.

---

### Post by jonofan on 2008-11-01
My laptop (HP Pav dv2000) also boots very slowly since upgrade to 8.10. Tried turning acpi off but still the same, also wouldn't let me use my wireless card. The loading bar hangs just under halfway for about 2 minutes then boots fine. Does anyone have a fix for this?

---

### Post by debugged on 2008-11-02
well i have a hp6515(turion 64)....for me its not even booting properly it crashes like anything and even my touchpad or keyboard are nt detected

---

### Post by simeonbg on 2008-11-02
I have laptop hp compaq 6715s amd turion 64 X 2.
I installed  ubuntu 8.10 from live cd. The Instalation was very slow more than 2-3 hours. Everything after install was very, very slow.
I tried the fix with acpi=off in the end of the kernel line, it worked everything was faster maybe normal. 
But when i start system monitor i realized one of 2 core was missing and no cpu frequency.
Then i ad to the end of my kernel line in menu.lst "noapic" and i delete "acpi=off" from there. After restart everything was normal with normal speed and the 2 cores of the procesors were there.
I hope this is the fix for me. Now my kernel line look like this:

"kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dfa4f40a-d798-44b5-b310-0dfda7cf9f90 ro quiet splash noapic"

---

### Post by walawa on 2008-11-03
I also have this problem. The loading bar stops at a little before halfway on boot and stays very long before continuing. Otherwise, I haven't noticed any performance problems except that login time is pretty long. I tried disabling acpi from the bios, but it didn't make a difference.

Any ideas for a fix?

---

### Post by Mitosk on 2008-11-03
yes same situation on my computer. I'm booting 50 seconds, what is really too much. 

Always in halfway it stops for 5 seconds.

---

### Post by jonofan on 2008-11-08
I tried both noacpi tips but still have same issue. Pressing alt+F1 during the halt seems to show that it is getting stuck on my network interface. My guess is it's trying to get DHCP, but can't as the card is not up yet.

---

### Post by walawa on 2008-11-09
I also tried alt+f1 during boot and noted what came up:

kinit: trying to resume from /dev/disk/by-uuid/<series of numbers and letters>

kinit: no resume image folder, doing normal boot
<This is where nothing happens for a while before the boot actually starts taking place>



Any idea what's wrong and how to fix it?

---

### Post by Charter33 on 2008-11-09
I had exactly this problem when upgrading to 8.10.
 I have a Belkin wireless card (enabled by ndiswrapper) because my built-in Intel wireless does not have the range I need.
 8.10 would not let me run the card, and the start-up stalled for a minute or so.
 I have discovered that the new Network Manager assumed that my hardware wireless switch meant that all wireless was disabled, so I either had both running or neither.  I couldn't find a way to make one work on startup and not the other.

 I have just re-built with a clean 8.10 install.  I immediately un-installed Network Manager, and then configured my card with ndiswrapper and network-admin.

All is now good!

---

### Post by walawa on 2008-11-09
I found a fix for the kinit problem on this thread: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148).

The post that helped me was as follows:
> My fix:
edit /etc/usplash.conf to use my laptop's true resolution. It was detected as 1280x1024, but my laptop's native resolution is 1280x800.
then I ran the following commands
$ sudo swapoff /dev/sda2
to turn off my swap partition
$ sudo mkswap /dev/sda2
to rebuild my swap partition
$ sudo update-initramfs -u
to rebuild my initial boot image to use my new, rebuilt swap partition 

That's fixed but now I have the same problem as jonofan, boot stops at "configuring network interfaces". I can kill the process by doing ctrl+alt+delete while it's loading, but it would be nice not to have to intervene that way everytime. Also, this is less important, but I don't have the ubuntu logo and loading bar anymore. It just shows the console executing the boot commands.

---

### Post by jonofan on 2008-11-09
> **walawa said:**
> I found a fix for the kinit problem on this thread: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148).

The post that helped me was as follows:


That's fixed but now I have the same problem as jonofan, boot stops at "configuring network interfaces". I can kill the process by doing ctrl+alt+delete while it's loading, but it would be nice not to have to intervene that way everytime. Also, this is less important, but I don't have the ubuntu logo and loading bar anymore. It just shows the console executing the boot commands.


I am at the same stage as you. I have fixed the network interfaces problem though and am left with a new problem, hangs now trying to load "nfs kernal" (I might try getting rid of my nfs share when I have more time). Fix for the network interfaces was as follows.

Remove everything form /etc/network/interfaces or just comment out everything.

This did not create a problem for me, possibly because I'm using wicd in place of network manager.

---

### Post by walawa on 2008-11-09
Thanks, that worked perfectly, and I'm still using network manager. Now I just have to figure out how to get graphical loading bar back. But that is just a minor problem.

I really don't know anything about the nfs kernel problem. For now you can always just kill the process during boot with ctrl+alt+delete.

---

### Post by jonofan on 2008-11-09
I've narrowed it down to the line

```
auto eth0
```

in /etc/network/interfaces that was causing the problem. Seems to boot fine now, and nfs-common is started on boot.

My /etc/network/interfaces file looks like so:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
```


No luck with the graphical loading bar as of yet, but its not like theres any major loss there.

I also had a problem when rebooting or shutting down, where the computer just hung. Found a fix at **post #14** here:
[http://ubuntuforums.org/showthread.php?t=966844&page=2](http://ubuntuforums.org/showthread.php?t=966844&page=2)

---

### Post by walawa on 2008-11-10
Since this thread is pretty much solved, I'll move to your new one on the progress bar issue.

---

### Post by xiyang81 on 2008-12-03
> **cleocirjh said:**
> The boot and de install of ubuntu 8.10 is very slow on my notebook HP 6515b (Turion64). After install the system also very slow. I have test with i386 and amd64 and the same problem.

On previus 8.04 version I no have problems.

????


I detected the problem:
When ACPI enabled on boot options, then very slow boot and instalation.
When ACPI disabled on boot with option "acpi=off" then normal boot speed and instalation.

I wait for this problem fix !
I have the same problem. My computer is hp6515b as well. The AMD64 works very well.But the i386 very very slowlly

---

### Post by GhostBunnies on 2009-01-24
So what is the solution for this slowing down problem?

I'm experiencing it right now, on a 6715s AMD Sempron 3800+ w/ ATI X1250 and I don't know what to do.

The boot/grub/menu.lst has already "noacpi noapic nolapic" but it doesn't seem to solve this problem.

I've tried the swap trick, but I had an UUID error, even though this is not the main problem for me neither, since I don't have a kinit error.

How to avoid this slow-down?

My computer boots currently in 5 minutes, and for a 2.2 GHz. CPU & 2 Gb. RAM that is unbearable.

I need some help!

Thanks a lot and have a nice weekend!

---

### Post by jonofan on 2009-01-25
upgrade or fresh install?

---

### Post by barberd on 2009-01-26
Hi there.

I hit this problem of a very slow boot after upgrading from 8.04 to 8.10 on my HP dv6815nr laptop.  The acpi=no in grub's config has worked to get back to a semblance of normal operation, but things like battery level, suspend, and power-off do not work without acpi.

This seems to be the kernel bug I'm getting here: [http://bugzilla.kernel.org/show_bug.cgi?id=12269](http://bugzilla.kernel.org/show_bug.cgi?id=12269)

It looks like 2.6.29rc2 has a lot of acpi fixes.  Hopefully 2.6.29 will take care of this problem.

Thanks,

Don

---

