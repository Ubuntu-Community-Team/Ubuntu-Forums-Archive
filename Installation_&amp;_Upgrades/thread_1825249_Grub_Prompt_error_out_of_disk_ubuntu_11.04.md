---
title: "Grub Prompt error out of disk ubuntu 11.04"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by rchande on 2011-08-15
I am installing ubuntu 11.04 from CD from inside Windows - dual boot.

Have 3 drives C, E and F. C - windows XP sp2 works fine even after ubuntu installation, no problem here.
I have installed Ubuntu in F drive, ubuntu installation went 
fine, but after reboot it halts at the grub prompt.

```

C: (hd0,msdos1)
D: (hd0,msdos5)
F: (hd0,msdos6)
F:/ubuntu/disks/boot/grub --- No files in here, its empty
F:/ubuntu/disks/boot/ --- No files in here, its empty
```

I tried following the steps given at: [https://help.ubuntu.com/community/Grub2#Command]("https://help.ubuntu.com/community/Grub2#Command") 

```
set prefix=(hd0,msdos6)/ubuntu/disks/boot/grub
set root=(loop0)
insmod normal
normal
set
ls (hd0,msdos6)/ubuntu/disks/boot
insmod linux
linux /vmlinuz root=/(hd0,msdos6)/ loop=/ubuntu/disks/root.disk ro  ---- This fails with "error: out of disk". 
initrd /initrd.img
boot
```

I am a newbie and not ubuntu expert, any help please?

Regards,
Raj.

---

### Post by madjr on 2011-08-15
hmm, could you test other drives?
try installing in C and/or D.

also make sure you give any ubuntu install enough space (10+ gb)

uninstall the ubuntu you already have in add/remove software.

if installing from inside windows keeps failing, i would try from a live-cd or live-usb and install from there.

---

### Post by rchande on 2011-08-15
Thanks for a quick response. 

Currently I have given 30GB while installing on F drive. I believe thats more than enough.

I will try on D drive as u said, Should the D drive be fully empty? I have some other data on this D drive with still @25 GB space available. Ubuntu installation can co-exist with some other data on D Drive, no issues with that, right? 

I am planning to allocate 17GB to Ubuntu on D drive, -- I hope that should be sufficient.

---

### Post by madjr on 2011-08-15
> **rchande said:**
> Thanks for a quick response. 

Currently I have given 30GB while installing on F drive. I believe thats more than enough.

I will try on D drive as u said, Should the D drive be fully empty? I have some other data on this D drive with still @25 GB space available. Ubuntu installation can co-exist with some other data on D Drive, no issues with that, right? 

I am planning to allocate 17GB to Ubuntu on D drive, -- I hope that should be sufficient.

if its an install from inside windows than yes, no problem with having files in the same drive.

just remember that a windows install should only be temporary, it is usually slower (windows filesystem fragments too, linux doesnt)and may have issues with some package updates later on.

Also if anything happens to windows you also lose the ubuntu install and your files. So is better and safer to have a separate partition just for ubuntu (you can even recover files from windows), so try to install in its own partition when possible. And not to mention all the malware/spyware/viruses you will avoid.

but if you want to just try it no problems.

---

### Post by rchande on 2011-08-15
yep i am trying it for the first time on my personal laptop. initially tried on separate drive F: for the same reason, but then since thats giving issues I will for trial do it on D: (emptying data from D: would take me lot of time :)) Its a very old laptop with only @ 768MB RAM. ;)

Once I am comfortable a bit with Ubuntu, i would switch it for good.

---

### Post by rchande on 2011-08-15
Wow.. I installed it on E and it went fine without any Grub issue like on F. 

So now whats the conclusion? What is wrong with my F:\ I did even format it yesterday. 

Any suggestions?

Regards,
Raj.

---

### Post by rchande on 2011-08-15
Hello,

I was able to login, work and surf using ubuntu on my E:\.

But now the question is if i just go and replace my windows... like it failed on my F:\ will i face any issues similar when replacing the entire windows?

Any issues on F:\ that i should take care first?

Regards,
Raj.

---

### Post by madjr on 2011-08-15
glad you solved it.

not really sure what went wrong with F. Maybe Wubi (windows program that installs ubuntu), likes main drives better...

anyway, if you go ahead and do a real install of ubuntu in the future , the real installer should have no problems with F, that i think off. So i believe it should go fine on that partition. Just remember that in linux, drives are not called "A,B,C..", but instead they called SD-A, SD-B for hard disks and SD-A1, SD-A2 for the partitions on that one disk.

Is done like that because sometimes people have many different linux installed for many purposes and need better categorization.

see here for some examples and install info:
[http://silverwav.wordpress.com/2011/04/30/ubuntu-natty-narwhal-11-04-stunning-and-beautiful/](http://silverwav.wordpress.com/2011/04/30/ubuntu-natty-narwhal-11-04-stunning-and-beautiful/)

anyway good luck and welcome to ubuntu. :)

some nice sites you may want to check to get you familiar and updated:
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
[http://www.webupd8.org/](http://www.webupd8.org/)

---

