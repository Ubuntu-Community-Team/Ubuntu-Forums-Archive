---
title: "Maverick-Proposed 2.6.38-10: Yeah, it ain't bootin'"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2011-06-06
I guess this is what happens when you use Proposed updates.
So several minutes ago I got a Maverick-Proposed kernel update, which is 2.6.38-10. I'm kinda guessing that Natty is running on this one.
Anyway. Had it installed, reboot, then it won't boot. More precisely, I can get past Plymouth but nothing else. The purple screen would disappear and it will be a simple black screen there. No output, no CLI, nothing. Ctrl + Alt + Fx does not respond. There is no disk activity according to the Disk Busy light.
Well I got Grub and I'm booting 2.6.35-29 mighty fine, so... What's up?

Thank you very much!

---

### Post by 3602 on 2011-06-06
Error messages. Here we go.
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.35-29-generic
Found initrd image: /boot/initrd.img-2.6.35-29-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```
Nothing there, actually. Then:
```
sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169

```
I have installed linux-firmware-nonfree. It does not solve this problem.

---

### Post by 3602 on 2011-06-06
What I did to make that error go away:
```
wget https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.49_all.deb
sudo dpkg -i linux-firmware_1.49_all.deb
sudo update-initramfs -u
```
Hooray, now I've got bits of Natty in my Maverick! Will now reboot.

---

### Post by 3602 on 2011-06-06
OK it's still not booting. Same symptoms.

In GRUB, I have removed, from the boot-line:
```
quiet splash nomodeset
```
And added:
```
nosplash --verbose text
```
And **it is booting CLI**. Picture attached with output.
I wrote *startx* and it would give me "Checking battery state... [OK]" then that's it. I cannot go back to the CLI by Crtl + Alt + Fx.

---

### Post by TBABill on 2011-06-06
How did you install the kernel? You can ```
apt-cache search linux-image

``` to find what kernel images are available and then ```
apt-get install linux-image-2.6.38-10
``` if it shows up in your search.

---

### Post by 3602 on 2011-06-06
> **TBABill said:**
> How did you install the kernel? You can ```
apt-cache search linux-image

``` to find what kernel images are available and then ```
apt-get install linux-image-2.6.38-10
``` if it shows up in your search.
 
I installed the kernel through Update Manager.

---

### Post by TBABill on 2011-06-06
Perhaps boot into the old kernel, remove the one you got via update, then follow what I posted above? Worth a shot and you can just remove it if it's not successful either. Sometimes you can get a new kernel that installs fine but just does not work with your hardware, but too soon to know for sure on your situation.

---

### Post by 3602 on 2011-06-06
I am currently in 2.6.35-29, which boots fine. The just-installed 2.6.38-10 does not boot.
I will now proceed into *sudo synaptic* and purge all files marked 2.6.38-10.

EDIT: No-can-do. Removing 2.6.38-10 packages will bring along the corresponding metapackages with them (linux-headers-generic and such).

---

### Post by emarkay on 2011-06-06
I think this is it:

"Hello Ubuntu developers,

Today we released another round of Linux kernel updates to
lucid/maverick/natty-proposed. However, the proposed natty update
(2.6.38 based kernel) was accidentally copied to lucid-proposed and
maverick-proposed, and thus had been on the master archive.ubuntu.com
between 09:00 and 14:00 UTC.

That means, if you have proposed updates enabled on your 10.04 LTS
(lucid) or 10.10 (maverick) Ubuntu installation, and did a system
upgrade during that time, it might have pulled in the 2.6.38 kernel.

To check this, please run

  dpkg -l linux* | grep '^ii.*2.6.38'

If you have any results, please first run another system upgrade,
which will again pull in the 2.6.32 (lucid) or 2.6.35 (maverick)
kernels, and then remove the wrong kernel packages with

  sudo apt-get purge `dpkg -l linux* | grep '^ii.*2.6.38' | awk '{print $2}'`

I fixed the script that handles the proposed kernel packages now, so
this won't happen again.

I sincerely apologize for any inconvenience that this caused!

Martin Pitt"

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-June/000854.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-June/000854.html)

---

### Post by 3602 on 2011-06-06
Nice! Actually the two lines of script did not work, so I went around Synaptic and did it myself. And I'm running on 2.6.35-30 now! Thanks!

---

### Post by nutznboltz on 2011-06-07
Heh, don't mess around with kernels unless you know what you are doing.

As for me:

$ lsb_release -sd
Ubuntu 10.04.2 LTS

$ uname -rv
2.6.38-10-server #44~lucid1-Ubuntu SMP Mon Jun 6 21:59:33 UTC 2011

$ uptime
 15:47:11 up 40 min,  3 users,  load average: 9.33, 11.66, 11.03

$ sudo virsh list | grep -c running
3

---

### Post by 3602 on 2011-06-07
> **nutznboltz said:**
> Heh, don't mess around with kernels unless you know what you are doing.

As for me:

$ lsb_release -sd
Ubuntu 10.04.2 LTS

$ uname -rv
2.6.38-10-server #44~lucid1-Ubuntu SMP Mon Jun 6 21:59:33 UTC 2011

$ uptime
 15:47:11 up 40 min,  3 users,  load average: 9.33, 11.66, 11.03

$ sudo virsh list | grep -c running
3
Wait, what?

---

### Post by jcolyn on 2011-06-07
I am currently running Linux Mint 10 on the 2.6.39.1 oneiric kernel which is a stable kernel and should work with your system.

If you would like to upgrade go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and scroll down to the listed kernel. I would suggest however that you stay clear of the rc kernels.

Click the folder to open it. You will see several files but you will only need to download 3 of them.

If you are using a 32 bit system download the Linux-headers 2.6.39.1 that ends in all.deb. Next the Linux-headers 2.6.39.1 ending in i386.deb then the Linux-image 2.6.39.1 ending in i386.deb.

If you are using a 64 bit system download the Linux-headers 2.6.39.1  that ends in all.deb. Next the Linux-headers 2.6.39.1 ending in amd64.deb  then the Linux-image 2.6.39.1 ending in amd64.deb.

Now go to the folder where you downloaded the files to and double-click the Linux-headers all.deb after it installs double-click the Linux-headers i386.deb (or  amd64.deb) after it installs double-click the Linux-image i386.deb (or amd64.deb)

DO NOT mix the i386 and amd64. Remember the 32 bit OS uses i386 and the 64 bit OS uses amd64 both use the Linux-headers all.deb

Once done reboot..

I've used this method a number of times without a single glitch but be sure to install in the above listed order..

---

### Post by 3602 on 2011-06-08
Nope. It would seem like the DKMS modules for *fglrx* aren't installed along with, so Xserver won't start (I boot into CLI with *startx *failing).
Oh well. Kernel grafting.

---

### Post by foresthill on 2011-06-08
> **jcolyn said:**
> I am currently running Linux Mint 10 on the 2.6.39.1 oneiric kernel which is a stable kernel and should work with your system.

If you would like to upgrade go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and scroll down to the listed kernel. I would suggest however that you stay clear of the rc kernels.

Click the folder to open it. You will see several files but you will only need to download 3 of them.

If you are using a 32 bit system download the Linux-headers 2.6.39.1 that ends in all.deb. Next the Linux-headers 2.6.39.1 ending in i386.deb then the Linux-image 2.6.39.1 ending in i386.deb.

If you are using a 64 bit system download the Linux-headers 2.6.39.1  that ends in all.deb. Next the Linux-headers 2.6.39.1 ending in amd64.deb  then the Linux-image 2.6.39.1 ending in amd64.deb.

Now go to the folder where you downloaded the files to and double-click the Linux-headers all.deb after it installs double-click the Linux-headers i386.deb (or  amd64.deb) after it installs double-click the Linux-image i386.deb (or amd64.deb)

DO NOT mix the i386 and amd64. Remember the 32 bit OS uses i386 and the 64 bit OS uses amd64 both use the Linux-headers all.deb

Once done reboot..

I've used this method a number of times without a single glitch but be sure to install in the above listed order..

I did this and can confirm that it works (at least on my system). I'm now running kernel 2.6.39.1 on 11.04. It did not fix the backlight problems on my laptop. And now I'm probably hosed as far as future updates is concerned.

So I'm not really sure if I could recommend this route to others, but I did it. Took about 20 minutes to install everything, for some reason. And I can't boot back into my old kernel. 

For some reason. in 11.04, when you do a kernel update, your old kernel is not listed in grub like it used to be.

So I would say, proceed with caution.

---

### Post by bsh on 2011-06-10
i was wondering about this when i saw it on the updates list, i tought it could be some fault, but then i installed it :)
and it works perfectly. it's a 10.04.2 desktop install, acting as a file server. i have no problems.

---

