---
title: "Booting with ISO file without CD"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by pushkarajthorat on 2010-02-16
Greetings,

I am absolutely not sure if this is correct channel to discuss ideas, please bear with me. 

Problem: As a linux fan, I tend to tryout all linux Distro and its Releases, so, I burn a CD/DVD for each (Release) X (Distro) and install it, for next Release or another Distro, I burn another CD/DVD, so till now, I have nearly 100(s) of disks lying in my CD bank. 

Constraints: Internet connection at my place is very slow, so cannot use network booting, I don't have a networked environment, so cannot setup the local network booting environment too.. (I download the ISOs from netcafe and get it to my home in pendrive)

Like me there could be *many* users who are unnecessarly consuming plastic disks for single installation, and hampering mother nature!!

Solution: One will download an boot-able ISO and place it on his machine, then, he will boot machine with *generic* booting CD which create a *virtual* CD ROM and mounts the specified ISO and start booting process once more,  installation follows...

I am absolutely not sure about feasibility, I need your views.

Regards, 
Pushkaraj

---

### Post by kellemes on 2010-02-16
I fixed it with [VirtualBox]("https://help.ubuntu.com/community/VirtualBox").
You can also use a **re**writable disk.

---

### Post by Bill D on 2010-02-16
Once you have the ISO on your home machine, you could choose to use unetbootin from ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to turn your pen drive into a live disk, and install it that way. That's how I did my full install, and it's working great so far. The main reason I don't use a CD is because my drive doesn't work at all (in windows or Ubuntu).

---

### Post by pushkarajthorat on 2010-02-17
> **kellemes said:**
> I fixed it with [VirtualBox]("https://help.ubuntu.com/community/VirtualBox").


I didn't get the problem you are pointing here.. could you please elaborate?

---

### Post by pushkarajthorat on 2010-02-17
Hi Bill, 
Thanks for pointing to UNetBootin, I'll try out this, I am feeling that this will solve my problem.

---

### Post by Dayofswords on 2010-02-17
> **pushkarajthorat said:**
> I didn't get the problem you are pointing here.. could you please elaborate?Virtualbox is a program that allows you to run a vitual computer within a running a computer, it can boot the iso and you can run it inside that

though this does not actually allow you to boot the physical computer from an iso

also, i'd recommend you download ubuntu isos from the offical server or one of its many offical mirrors

download link - [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
vitual box site - [http://www.virtualbox.org/](http://www.virtualbox.org/)

vitual box is installable from the *software center* if you are running 9.10, or from *add/remove programs* in 9.04

there is also a windows version on the vitualbox site

---

### Post by ironclaw on 2010-02-17
GRUB 2 now has support for booting from ISO files on the hard drive. The live OS has to support this feature though - most recent distributions, including Ubuntu 9.10, supports this feature.

Something like this in /etc/grub.d/40_custom will work:
```
menuentry "Ubuntu 9.10 32-bit" {
    loopback loop /boot/livecds/ubuntu-9.10-desktop-i386.iso
    set root=(loop)
    linux /casper/vmlinuz iso-scan/filename=/boot/livecds/ubuntu-9.10-desktop-i386.iso file=/cdrom/preseed/ubuntu.seed boot=casper
    initrd /casper/initrd.lz quiet splash --
}
```
The ISO file 'ubuntu-9.10-desktop-i386.iso' is put in '/boot/livecds/'.

---

### Post by pushkarajthorat on 2010-02-17
IronClaw, 
Thanks for your reply, this is interesting; I will try out this today evening, I already have GRUB 2 on my machine. Just matter of executing this. 

For curiosity, is booting from an ISO using GRUB will be capable of installing OS(ubuntu in particular)? 

Regards, Pushkaraj

---

### Post by ironclaw on 2010-02-17
> **pushkarajthorat said:**
> IronClaw, 
Thanks for your reply, this is interesting; I will try out this today evening, I already have GRUB 2 on my machine. Just matter of executing this. 

For curiosity, is booting from an ISO using GRUB will be capable of installing OS(ubuntu in particular)? 

Regards, Pushkaraj
Yes, the functionality of an OS booting from an ISO should be the same as that booting from a CD. So you should be able to install if you boot from the ISO.

The only potential problem I can think of is that you won't be able to resize the partition where the ISO is.

Remember to run "sudo update-grub" after appending the menuentry to '/etc/grub.d/40_custom' so that '/boot/grub/grub.cfg' is updated to include the new menuentry.

---

### Post by pushkarajthorat on 2010-02-19
Bill D,
I tried unetbootin, and it worked great. 


All,
I've not be tried the GRUB 2 thing, but if anyone has, or will in future, please update this thread.

Thanks for everyone for the response.

Regards,
Pushkaraj

---

### Post by Bill D on 2010-02-23
Glad I could be of assistance. :)

---

