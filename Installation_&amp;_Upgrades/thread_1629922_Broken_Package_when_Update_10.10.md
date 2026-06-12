---
title: "Broken Package when Update 10.10"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by partyk1d24 on 2010-11-24
When I run sudp apt-get -u upgrade (or use upgrade manager). I get the following error...

The package libhttpcore-java:i386 is not ok and I don't know how to fix it!

Any ideas? On another note I am running x64 so the i386 is throwing me off.

---

### Post by sikander3786 on 2010-11-24
Please post the output of

```
sudo apt-get install -f
```

and

```
sudo dpkg --configure -a
```

Remeber, we need the complete outputs and you can wrap them using code tags # from post menu to make them easier to read.

Thanks.

---

### Post by partyk1d24 on 2010-11-24
```
jackie@jgleason-workhorse:~$ sudo apt-get install -f
[sudo] password for jackie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libhttpcore-java:i386 is not ok and I don't know how to fix it!

```

```
jackie@jgleason-workhorse:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic
 linux-generic
```


So does this mean I just need to install linux-image-2.6.35-23-generic? Any clue how my machine would have gotten to this state?

---

### Post by partyk1d24 on 2010-11-24
When I try to install that package I get...

```
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jackie@jgleason-workhorse:~$ 

```

---

### Post by sikander3786 on 2010-11-24
Try

```
sudo apt-get clean
```

And try re-installation again.

---

### Post by partyk1d24 on 2010-11-24
After reading the errors I tried the following 


[LIST=1]
[*]sudo rm -rf /var/cache/apt/archives/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb
[*]sudo apt-get install linux-image-2.6.35-23-generic
[/LIST]
Now the update manager appears to have worked so my best guess is that there was a problem DLing the file leading to it getting corrupted. It amazes me that apt couldn't handle this but I suppose that isn't your problem :-). 

Hopefully this solves everything thanks for your help!

---

### Post by partyk1d24 on 2010-11-24
DOPE! apt-get clean I guess there is the functionality :-)

---

### Post by sikander3786 on 2010-11-24
> **partyk1d24 said:**
> DOPE! apt-get clean I guess there is the functionality :-)
Yes, I feel some packages under apt/archives were corrupted and apt-get clean is used to clear those ;-)

Glad you figured it out yourself :-)

You can now mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

