---
title: "Disable ipv6 in Ubuntu 9.04 beta"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eriksi on 2009-04-02
Hi everyone I have banged my head for a fiew days now how to disable the blody ipv6 in Ubuntu 9.04, I tried the /etc/modprobe.d/aliases but the file isnt there .. I cant find anything to help me out. So if anyone know the problem and the solutions I would be very greatefull to hear it :D

Thanks a lot!

---

### Post by Sef on 2009-04-02
moved to jaunty.

---

### Post by ronacc on 2009-04-02
you can disable IPV6 in firefox but can nolonger globaly disable it . as of alpha4 it is built into the kernel rather than being loaded as an independent module .. in other words those of us who need it disabled globaly are screwed .see my bug 313218  , but it looks like we aren't going to get much help .

---

### Post by JotaCapa on 2009-04-04
I used an old process that I found somewhere:

sudo gedit /etc/modprobe.d/aliases


and write

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6


works fine with my router.

---

### Post by binbash on 2009-04-04
> **JotaCapa said:**
> I used an old process that I found somewhere:

sudo gedit /etc/modprobe.d/aliases


and write

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6


works fine with my router.

I will try this

---

### Post by bigo72 on 2009-04-05
Nothing, this "old" trick not works for me: after reboot "ip a | grep inet6" has output! :-(

---

### Post by binbash on 2009-04-05
it didn't work for me

---

### Post by pressureman on 2009-04-05
Try adding "disable_ipv6=1" to your kernel command-line.

You can selectively re-enable it on certain interfaces by setting sysctl options. Check out the net.ipv6.conf.* options.

---

### Post by MidasTouchBR on 2009-04-08
Ok, guys, maybe my solution is not the best, nor the easiest, but it works. I've got the kernel source with Ubuntu patches, provided in the repos, and recompiled it with IPv6 support as modules (just in case someday it become useful) and after that I blacklisted the ipv6 modules in order not to load them. So far, I've got everything working here and no more IPv6 issues as slow connection speed. Bla, bla, bla... well, these were the commands:

Step 1 - Get the packages needed
```
$ sudo apt-get install kernel-package libncurses5-dev fakeroot bzip2 linux-source

```

Step 2 - Unpack the kernel image
```
$ cd /usr/src
$ tar jxvf linux-source-*.tar.bz2
$ ln -sf /usr/src/linux-source-[version of the source you've got] /usr/src/linux

```
NOTE: You will get the source of the latest kernel version available in the Ubuntu repositories. By the time I wrote this, 2.6.28 was the latest one. 

Step 3 - Save your kernel configuration to avoid messing things that you don't need to
```
$ cd linux
$ sudo cp /boot/config-$(uname -r) .
$ sudo mv config-$(uname -r) .config

```

Step 4 - Building IPv6 as a module
```
$ sudo make menuconfig

```
It will open the kernel configuration menu. First, select "Networking support", then "Networking options". Inside the "Networking options" look for the "IPv6 Protocol" line and with it highlighted press "M" or press the space bar until the letter "M" appears between the major and minor signs, like this "<M>". Save your new configuration and exit.

Step 5 - Recompiling the new kernel
```
$ sudo make-kpkg clean
$ sudo fakeroot make-kpkg --initrd --append-to-version=-noipv6 kernel_image kernel_headers

```
It took a couple of hours for me the recompiling process, so, go get a coffe or something and wait...

Step 6 - Installing the new kernel
```
 $ cd /usr/src
$ sudo dpkg -i linux-headers-*.deb
$ sudo dpkg -i linux-image-*.deb

```

Step 7 - Blacklist the IPv6 module

```

$ sudo nano /etc/modprobe.d/blacklist

```

In the end fo the file, add the following line:

```

blacklist ipv6

```

Save it and exit.

Step 8 - Check if everything is right

Well, reboot your machine, connect in the internet in the way you always do and in the terminal use the following command:
```

$ ip a | grep inet*

```

If the output did not show anything like "inet6", congrats. You're now using IPv4.

NOTE 1: in step "4", instead of building IPv6 as a module someone could simply get rid of it by pressing space bar until leave IPv6 unmarked. If you do that, you could skip Step 7 because blacklisting would not be necessary (since you've chosen not to build the IPv6 at all).
NOTE 2: Sorry for my poor english. I'm brazilian and this is not definitely my mother tongue :-P

---

### Post by bigo72 on 2009-04-08
OK, people...I love this man! :D It looks easy, but have to be done everytime a new kernel comes in jaunty (every "two days").
Anyway a very good tutorial, thank you veryVery much! I'm doing everything you described (crossing fingers...is better with kernel "things") :-)

---

### Post by rockin_goliath on 2009-04-08
Why does one *need*IPv6 disabled? Hardware limitations?

---

### Post by ronacc on 2009-04-08
in some cases yes  and in some cases its your ISP .

---

