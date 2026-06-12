---
title: "Grub2 + 32/64 bit problem.."
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by solitaire on 2009-09-16
Ok total Newbie mode here! (brain has shutdown!)

System setup is currently a dual boot with Win7 RC + Ubuntu 9:04 (Both 32Bit editions)

Problem:

 I installed 9:10 Alpha-5 AMD64 version (I know i should have waited for Alpha-6 tomorrow!!) on to a spare partition on my machine. When Alpha-5 installed it installed Grub2 but it did not find win7 or my 9:04 install.

Currently I reverted back to GRUB so that I can boot into my main OS's. I might just wait for Alpha-6 or the first Beta before i try it again! lol  o_0

When i was using GRUB2 I ran grub-mkconfig, It found my Win7 and 9:04 install but did not update the Grub2 boot list. 

  i) How do you get Grub2 to list those OS's?
 ii) Can you manually edit the list (like grub's menu.lst)?
iii) Does 9:10 work with GRUB or does it need GRUB2 to boot?

---

### Post by drs305 on 2009-09-16
One of the Grub updates today dealt with Windows 7 recognition. Although the changelog wasn't specific, this may have addressed your problem. You can view the following links to see what the format for a Windows entry should be, but running "sudo update-grub" should find and put a Windows entry into the menu.

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by sisco311 on 2009-09-16
> **solitaire said:**
> 
When i was using GRUB2 I ran grub-mkconfig, It found my Win7 and 9:04 install but did not update the Grub2 boot list. 



try:
```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg-backup
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by Podex on 2009-09-16
From the man page of update-grub:
> update-grub  is a stub for running grub-mkconfig -o /boot/grub/grub.cfg

So you can use update-grub instead of grub-mkconfig. I think that if you just run grub-mkconfig without any options it wont write it to /boot/grub/grub.cfg

---

### Post by solitaire on 2009-09-16
Many thanks guys!

Will give it a go when Alpha-6 is released :) hopefully it won't be needed! lol ^_~

---

### Post by solitaire on 2009-09-18
Urgh!

Installed A-6 and it's getting to the desktop!

Having issues after the grub2 menu (screen goes blank and crashes / freezes)

Im trying to chroot using the LiveCD  but getting errors!
```
root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
grub-probe: error: cannot find a device for /.

```:(

Was going to try an apt-get update && apt-get install but that's not working either!
I'm on a wireless connection, which does not work, at the moment! need to get a cable >_<

---

### Post by ranch hand on 2009-09-18
Well, I am happy that you can get the LiveCD  to boot.

Welcome to testing an OS with a lot of fairly basic changes.  There is going to be "growing pains".

---

### Post by solitaire on 2009-09-18
lol! ^_^

I'm getting the problems in A-6 that people were getting in A-5

i've reinstalled GRUB so guess i'll wait for Beta. lol

---

### Post by VMC on 2009-09-18
> **solitaire said:**
> Urgh!

Installed A-6 and it's getting to the desktop!

Having issues after the grub2 menu (screen goes blank and crashes / freezes)

Im trying to chroot using the LiveCD  but getting errors!
```
root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
grub-probe: error: cannot find a device for /.

```:(

Was going to try an apt-get update && apt-get install but that's not working either!
I'm on a wireless connection, which does not work, at the moment! need to get a cable >_<
Why not just run update-grub?

---

### Post by solitaire on 2009-09-18
> **VMC said:**
> Why not just run update-grub?
it could not find "update-grub" :(

Also I rebooted with the live CD and had to manually change the /etc/apt/sources.list with the one on the live CD. It was looking for GB. based servers which did not exist. 

Once I did that "apt-get update" ran fine bit still it's not working...

will leave it a few hours for new updates to get into the repos then try it again...

---

### Post by VMC on 2009-09-18
> **solitaire said:**
> it could not find "update-grub" :(

Also I rebooted with the live CD and had to manually change the /etc/apt/sources.list with the one on the live CD. It was looking for GB. based servers which did not exist. 

Once I did that "apt-get update" ran fine bit still it's not working...

will leave it a few hours for new updates to get into the repos then try it again...

OK, I see. You still running grub-legacy. Or from first post it appears you are. It looks like jaunty is the grub holder. If that's true then from jaunty is where you want to edit in karmic.

---

### Post by solitaire on 2009-09-18
I formatted the partition that had A-5 on it and had a clean install of A-6

I reinstalled Grub when I could not get GRUB2 to see my Win7 or Jaunty installs.

Later (probably tomorrow) I'll have to use the LiveCD to remove GRUB and reinstall GRUB2 and try again to get win7 and Jaunty to pop-up in grub2.

*!!Note!!*
Probably it's they way i've installed it!

win7 and jaunty are 32Bit  
alpha-6 is 64Bit (thats probably what's causing most of the problems!) :)

might get 32bit alpha-6 tomorrow and see if that makes a difference... lol!!!

---

### Post by ranch hand on 2009-09-19
You don't need the Live CD to do any of tht with grub2.

Just boot into 9.10.

Install grub2 and grub-pc.  Grub-legacy should be removed in doing that.

Update-grub shuold also run when you do that but I would do it again;
```

sudo update-grub

```
also
```

sudo grub-install

```
That "should" have you seeing all your OS' and booting with grub2 from your 9.10 install.

---

### Post by solitaire on 2009-09-19
I'll give grub2 another go and see If I can get it to see all my OS's

Personally I've never been 100% confident about Grub2 (dunno why, just one of those nagging feelings your get!) 

Well pub is calling. playing about with an OS is best done while slightly inebriated... ^__^ 

more fun and excitement that way.... lol

---

### Post by ranch hand on 2009-09-19
Grub2 is going to be fine, I think.  It is certainly rough right now.

Remember that you can put custom entries in grub.d.

---

### Post by solitaire on 2009-09-19
Urgh!

I installed grub2 and it didn't work!!

All I get is an error with any option I select.....

```
error 11 : unrecognized device string
```

Looks like I'll be installing grub1 again.....

---

### Post by VMC on 2009-09-19
> **solitaire said:**
> Urgh!

I installed grub2 and it didn't work!!

All I get is an error with any option I select.....

```
error 11 : unrecognized device string
```

Looks like I'll be installing grub1 again.....

Output your /boot/grub/grub.cfg file first.

---

### Post by donniezazen on 2009-09-19
> **solitaire said:**
> Ok total Newbie mode here! (brain has shutdown!)

System setup is currently a dual boot with Win7 RC + Ubuntu 9:04 (Both 32Bit editions)

Problem:

 I installed 9:10 Alpha-5 AMD64 version (I know i should have waited for Alpha-6 tomorrow!!) on to a spare partition on my machine. When Alpha-5 installed it installed Grub2 but it did not find win7 or my 9:04 install.

Currently I reverted back to GRUB so that I can boot into my main OS's. I might just wait for Alpha-6 or the first Beta before i try it again! lol  o_0

When i was using GRUB2 I ran grub-mkconfig, It found my Win7 and 9:04 install but did not update the Grub2 boot list. 

  i) How do you get Grub2 to list those OS's?
 ii) Can you manually edit the list (like grub's menu.lst)?
iii) Does 9:10 work with GRUB or does it need GRUB2 to boot?

I too faced same problem but fully updating system and installing maintainer's version of grub menu solved the problem.

---

### Post by solitaire on 2009-09-19
> **VMC said:**
> Output your /boot/grub/grub.cfg file first.

Will Post it once I get back to my laptop...

I'm currently seeking liquid refreshment at the local pub..... ^_~

---

### Post by solitaire on 2009-09-19
> **VMC said:**
> Output your /boot/grub/grub.cfg file first.
  Ahem... Lets try that again... (posted wrong grub.cfg file....)
```

  #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,3)
search --fs-uuid --set 1e2a2a2a-fd27-4126-ade2-47843141890d
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,3)
search --fs-uuid --set 1e2a2a2a-fd27-4126-ade2-47843141890d
menuentry "Ubuntu, linux 2.6.28-15-generic" {
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro single 
    initrd    /boot/initrd.img-2.6.28-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda2)" {
    set root=(hd0,2)
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=55fb3519-0350-40fb-9d1f-e9289dcbd027 ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda2)" {
    set root=(hd0,2)
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=55fb3519-0350-40fb-9d1f-e9289dcbd027 ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

```

---

### Post by solitaire on 2009-09-19
> **ranch hand said:**
> You don't need the Live CD to do any of tht with grub2.

Just boot into 9.10.

Install grub2 and grub-pc.  Grub-legacy should be removed in doing that.

Update-grub shuold also run when you do that but I would do it again;
```

sudo update-grub

```

That throws up the following error 
```
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /.

```
> 
also
```

sudo grub-install

```That "should" have you seeing all your OS' and booting with grub2 from your 9.10 install.

nope... :(

---

### Post by MalphasWats on 2009-09-19
I got the Error 11 thing when I first installed Grub2, took me a while to find the answer.

When grub loads, you have to edit the command line (hit e), then edit the first part (I think it says root and then some junk), change 'root' to 'uuid' and boot, it should work.

Once you're in, you can run the command to complete the grub2 installation (the command is at the top of the grub output) and that will correctly configure grub2.

Hope this helps, sorry it's a little vague, I'm working from memory!

-Malphas

---

### Post by solitaire on 2009-09-19
i fixed the error (I think...) changed the first line from the UUID to  "/dev/sda3" that seemed to boot correctly..
but I then removed grub2 and reinstalled grub

(trying to reinstall grub using the liveCD didn't work what ever i did it still booted using grub2)

chroot into the 9:04 install would not connect to the internet so could not reinstall grub that way!

but i'm back with a working 9:04 so i'll leave A-6 for a few days!

---

### Post by solitaire on 2009-09-20
Woo! At last......

Got A-6 to load up

I did a clean install of A-6
Chroot into it using the LiveCD
Copied the etc/apt/sources.list from the live CD to A-6
Edited the sources.list to add the following lines
```

## Added Intel xorg-edgers fresh X crack unstable graphics
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb http://archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
```Also un-commented all the deb lists in the file
Ran sudo apt-get update && sudo apt-get upgrade
It installed everything except "Pulseaudio" and 4 other items were held back (but I ignored this for now!)
I rebooted the laptop
In the gurb2 menu i changed the line on the "Ubuntu, Linux 2.6.31-10-generic" an added ```
 nomodeset
``` to the end and then hit ctrl+x
After a few secs it dropped to the command line in read only mode and i logged it
Was complaining of date mismatch on /dev/sda2 (A-6 partition)
Ran ```
sudo fsck
```There was a 10 min future time mismatch in the system time and the time of the partition
I then rebooted and selected the repair console.
Got GDM to start (only options was reboot or shutdown) but hit ctrl+alt+f1 to get to the repair console.
Ran fsck again (just to be sure!) all was good!
Then ran the option to fix broken packages (after running around the house to find a network cable!!!)
After running the updates a couple of times till everything, including pulseaudio, was installed correctly i then rebooted for the final time!

success!!

Got the login screen and logged in to A-6

only problem now is I can't get the wireless to work! :(
I hate it when the Broadcom STA wireless drivers work in the liveCD but don't when it's installed :(
```
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```Well at least i can now use A-6 ^__^

---

### Post by darkstaar on 2009-09-20
> **solitaire said:**
> only problem now is I can't get the wireless to work! :(
I hate it when the Broadcom STA wireless drivers work in the liveCD but don't when it's installed :(

Have you tried reinstalling the bcmwl-kernel-source?

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

...and reboot.

Assuming that you can get online with a regular ethernet connection.

---

### Post by solitaire on 2009-09-20
> **darkstaar said:**
> Have you tried reinstalling the bcmwl-kernel-source?

```
sudo apt-get install --reinstall bcmwl-kernel-source
```...and reboot.

Assuming that you can get online with a regular ethernet connection.

I reinstalled it from the .deb on the CD..

Got it working ^__^

---

