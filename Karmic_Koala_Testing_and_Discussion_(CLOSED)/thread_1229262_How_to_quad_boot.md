---
title: "How to quad boot?"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2009-08-01
I'd like to avoid constantly reinstalling OSes which is the current situation I've cornered myself. :D

I've got Win7 installed and I have space to install 3 other instances of Linux.

I'd installed Karmic with its GRUB2 on MBR then I installed Arch Linux with GRUB1 overwriting the MBR.

Now I would like to reinstall Karmic when Alpha 4 comes out as well as Fedora 12 alpha when its out.

Any suggestions on how to be able to boot all 4 of them? Should I always have the last OS overwrite MBR with GRUB2? If so, then how can I configure GRUB2 of the last installation to recognise and boot all 4 OSes? Got links?

(yes i will search online also, but was hoping for some tips here)

---

### Post by kingborel on 2009-08-01
Each time you reinstall an OS, just update GRUB2 and it should pick up all the installed systems. Follow the instructions at [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) (under the IF YOU MESSED UP heading) to chroot into the main karmic install and update grub2

---

### Post by ranch hand on 2009-08-01
You can boot from any Linx OS that you have installed.

First, I am assuming that you have romatted your HDD so that you have a large extended partition that you can put logical partitions inside of.  Hopefully swap is in that extended partition.

If the OS that you want to use as boot/root is using grub-legacy you need to boot to a live CD or an OS running grub-legacy and;
```

sudo grub
(this will give you)
grub>
(these are the commands to use at that promt)
grub> find /boot/grub/stage1
grub> root (hd?,x)
(where ? is your drive [one drive ?=0] and x is the partition [they start with 0 also if gparted says 6 then x=5] this should be listed correctly in the results of the "find" command)
grub> setup (hd?)
(?=value used in "root" command [sets grub from "root" to MBR])
grub> quit
(you are done - reboot to check)

```

If you want to do the same thing with an OS using grub2 you do not need a LiveCD you need to boot into that OS and run;
```

sudo update-grub
(this will pickup all OS' on that OS' menu)
sudo grub-install /dev/hd?
(?=samevalue as in grub-legacy)

```

You should be done, reboot and check.

Links for grub2
[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

[http://ubuntuforums.org/showthread.php?t=1229262](http://ubuntuforums.org/showthread.php?t=1229262)

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

I have 4 OS' on my main drive, 7 on a second internal and (so far) 8 on a dual drive external enclosure.

HAVE FUN

---

### Post by vishalrao on 2009-08-01
thanks! i think i *will* have fun :D

so lets say i install karmic which has grub2 but then later i install jaunty which only has grub1 (grub-legacy) then can i "restore" grub2 (by booting karmic live) in such a way that it will boot (chainload is it called?) older jaunty with its older menu.lst ? according to the grub2testing link posted above, if i just run grub-install from a chroot will it recognise old grub1 based OS or do i need to do something extra to chainload into jaunty?

(thanks for the links, the second out of three in the above post is actually pointing to this same thread heh)

---

### Post by ranch hand on 2009-08-02
> **vishalrao said:**
> thanks! i think i *will* have fun :D

so lets say i install karmic which has grub2 but then later i install jaunty which only has grub1 (grub-legacy) then can i "restore" grub2 (by booting karmic live) in such a way that it will boot (chainload is it called?) older jaunty with its older menu.lst ? according to the grub2testing link posted above, if i just run grub-install from a chroot will it recognise old grub1 based OS or do i need to do something extra to chainload into jaunty?

(thanks for the links, the second out of three in the above post is actually pointing to this same thread heh)
Not really.  That should not be needed at all.

If you install Jaunty after Karmic, the grub-legacy from Jaunty should let you boot to Karmic.

In Karmic run the update-grub and grub-install commands.  This should put all, including Jaunty, OS' on your Karmic menu (update-grub) and make Karmic the boot/root for your MBR.  No live disk required.

Do not chainload.  That was something that they were trying to get folks to do to test grub2 without removing grub-legacy.  It did not work well for a lot of people.

As stated in most posts about grub2, the documentation is behind practice and developement.  Except in minor details and occasional teething problems, grub2 is ready to role on its own.  I use it on 2 of 3 drives and it works great.

I did have a problem on one drive where I have 4 variations of 9.10.  One is an upgrade of 9.04 where I left the Jaunty repos and just added the Karmic repos (I do not no if there is something confusing about thisto grub2 or if it has nothing to do with the problem).  I was booting from another 9.10 partition.  Update-grub found the OS but it never got entered in the menu.  I switched (with LiveCD) to grub-legacy with a 9.04 partition as boot/root, booted to the partition that brub2 was missing and switched to that partition as boot/root.  Did not need to boot to Live CD because I was on an OS with grub2.  Just update-grub and then grub-install and I was booting (and am booting) that drive from grub2.  All OS' including itself are picked up by that OS that the other Karmic would not deal with right.

It really is fun.  I love grub-legacy for its flexibility and power.  I think grub2 is going to be better and it really is not quite done yet.  It will be very hard for some of us to get used to it as it is very different from the old grub.  New users will hate the old grub if they have to use it because of the need to us the live CD and manually edit files at times.  Grub 2 does most editing itself with update-grub.

IT'S NEAT

---

### Post by vishalrao on 2009-08-02
alright! thanks a lot... i have win7 and arch linux installed at the moment on my tablet PC. will install karmic today to make it triple boot. then i'll wait for fedora 12 alpha (end august i think) to install and make it quad boot :D

---

### Post by vishalrao on 2009-08-02
yesssss! i have quad boot (and am unscathed) mwaahhahahaha!

install order: win7rc, arch, karmic, fedora11.

wasn't easy for me. required futzing around with karmic's grub2 and fedora11's legacy grub which demands an ext3 boot partition.

going to update fedora 11 to 12 (rawhide) next.

this is on my tablet pc, not yet man enough to try it on my main home desktop, maybe in a few days/weeks.

i have to figure out grub2 customisation because at the moment its not clear to me how to rearrange my preferred OSes to boot and rename the entries since update-grub calls grub-mkconfig which looks at /etc/grub.d to autogenerate entries. and /boot/grub/grub.cfg can be edited but its marked read-only as a hint not to edit i guess.

---

