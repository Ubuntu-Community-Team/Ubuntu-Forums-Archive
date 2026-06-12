---
title: "cannot dualboot with pc-bsd"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by frankyboynl on 2015-02-03
hello, I am trying to dualboot my laptop with ubuntu,windows and pc-bsd. I adapted the menu-entry as follows:


menuentry "PC-BSD (on /dev/sda4)" {
        insmod ufs
        set root='(hd0,4)'
	search --no-floppy --fs-uuid
        chainloader +1
}

and ran grub-update, but when I select pc-bsd from the boot menu, it says:


file /boot/grub/ufs.mod not found

---

### Post by tokyobadger on 2015-02-03
I think the error is coming because you should have insmod ufs2 (not ufs)

[more info here](http://unix.stackexchange.com/questions/109272/add-freebsd-to-grub2-boot-menu)

---

### Post by frankyboynl on 2015-02-03
I changed it to ufs2, but now I get the error code: error: one argument expected.  When I press enter, it says NO UFS...



grtz, Frank

---

### Post by tokyobadger on 2015-02-03
[three options here]("https://blog.debiania.in.ua/posts/2013-09-30-dualbooting-debian-and-freebsd.html") - when I did this before I called the FreeBSD bootlaoder via the chainloading option which is the most straightforward
/dev/sda4 (hd0,4) looks correct - I suspect it's because you are mixing several approaches (1 & 2 in the above link) to call the PC-BSD bootloader
```
menuentry "PC-BSD (on /dev/sda4)" {
set root='(hd0,4)'
chainloader +1
}
```
in /etc/grub.d/40_custom
```
sudo update-grub
```
[post #24 in this thread also shows all 3 ways]("https://forums.freebsd.org/threads/freebsd-accessed-via-grub2.5918/")

---

### Post by frankyboynl on 2015-02-03
when I tried as stated above, I get the following: not ufs     no /boot/loader


grtz, Frank

---

### Post by tokyobadger on 2015-02-03
can you show output of sudo fdisk -l

---

### Post by tokyobadger on 2015-02-03
ok, plugged in an old hdd from when I was dual-booting ubuntu and FreeBSD and the /etc/grub.d/custom_40 entry looks like this
```
menuentry "FreeBSD"{
    insmod ufs2
    set root=(hd1,1)
    chainloader +1
}


```
And it was working - last modified 13 Oct 2012 - obviously the set root line will need to change for you this was /dev/sdb1

---

### Post by frankyboynl on 2015-02-03
the bsd is located on /dev/sda4, so how wil the grub-file need to look?


grtz, Frank

---

### Post by tokyobadger on 2015-02-03
you have it correct as I understand 
```
set root=(hd0,4)
```
but maybe drop the ' ' - my working entry didn't have those

---

### Post by frankyboynl on 2015-02-03
strange, when I do that it gives again the error code: not ufs...


grtz, Frank

---

### Post by oldfred on 2015-02-03
Remove the search line also. That overrides the set root command as it searches for the correct UUID, if set root command not correct. But you do not even have the UUID in the command, so that is failing.

---

### Post by frankyboynl on 2015-02-03
ok, so I tried to use boot-repair, but that resulted in 2 BSD entries, which both didnt work. Also I do not know exactly what you mean by search line..



grtz, Frank

---

### Post by frankyboynl on 2015-02-03
tried the following:


menuentry 'PC-BSD' {
insmod zfs
search -s -l tank1 --hint hd1,gpt63
kfreebsd /boot@/loader
}


now it says on startup:  file boot not found


grtz, Frank

---

### Post by oldfred on 2015-02-03
In post #1 you have a search line.
Most examples that have worked just had the set root line.

For FreeBSD I have seen this:
 menuentry "FreeBSD" {
    insmod ufs2   
    set root=(hd0,1)
    chainloader +1
    }

But if using zfs you also need the insmod zfs as shown above.

---

### Post by frankyboynl on 2015-02-03
I tried the above, but I keep getting the following:

not ufs
FreeBSD/x86 boot
Default : 0,ad(0.a)/boot/loader
boot: not ufs
No /boot/loader



grtz, Frank

---

### Post by oldfred on 2015-02-03
Then there are more differences with PC-BSD and Free-BSD on how they are configured.
It looks like it must be a MBR primary partition or gpt partitioned and does use grub to boot.

And it looks like it does not use ufs.

menuentry "PC-BSD 9.1" {
    set root='(hd0,2)'
    chainloader +1
    }


[https://pcbsd.org/showthread.php?t=22998](https://pcbsd.org/showthread.php?t=22998)

Post the Summary report from Boot-Repair.

---

### Post by frankyboynl on 2015-02-03
[http://paste.ubuntu.com/10041458/](http://paste.ubuntu.com/10041458/)

---

### Post by oldfred on 2015-02-03
Your Windows is hibernated or needs chkdsk. Best not to hibernate Windows if dual booting. Even if two copies of Windows.

You are using zfs. So you will need the insmod zfs. But not sure how well grub/Linux support zfs. Last I saw was that it was all experimental.

---

### Post by frankyboynl on 2015-02-04
ok, I give up, instead of using freebsd I now used that partition to test opensuse. Thanks a lot anyway..


grtz, Frank

---

