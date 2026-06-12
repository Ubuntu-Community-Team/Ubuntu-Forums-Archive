---
title: "Blank screen after upgrade to 10.04"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by ThomWilhelm on 2010-04-23
I have big problems after upgrading to 10.04 from 9.10

When my laptop starts I just get a blank screen with a blinking cursor for a scond, then the screen flashes to blank for a second then comes back with the blinking cursor. I can type but its not at the stage I can enter commands (its like its not even loading from the HD).

I have a live cd I can try to use to debug this, are there any commands I can run to try and solve this? As otherwise my computer is totally bricked.

I think this could be something GRUB related? Any ideas?

Thanks!

---

### Post by romeroc24 on 2010-04-23
I think its grub, check the /boot/grb/menu.lst file, but if you are not in your HD maybe you need to mount your disk, you have a new grub file 10.04 and it's not configured:
```

$ sudo vim /boot/grub/menu.lst

```
Find or add something like this.
```

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            7b0dd060-80bc-4d0f-ac7a-bc88b5ed65ba
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=7b0dd060-80bc-4d0f-ac7a-bc88b5ed65ba ro quiet splash
initrd          /boot/initrd.img-2.6.28-13-generic
quiet

```:guitar:

---

### Post by ThomWilhelm on 2010-04-23
Hi, thanks for the quick response!

I have managed to get GRUB back now, I had to reinstall GRUB2 and and run a few commands to get it to read from /dev/sda1.

So now I get the screen

Grub loading.
[Linux-bzImage, setup=0x3400, size=0x3d4760]
[Init-rd, addr=0x3787c000, size=0x773d50]

With a blinking cursor below this, so it looks like it is now at least trying to load linux, but its not getting past this and just hanging.

Any ideas anyone?

Cheers,
Thom.

---

### Post by quaeritate on 2010-04-23
I too am getting the blinking cursor on the blank screen after upgrading from karmic to lucid (in this case the RC). I have tried reinstalling grub2 but have not had any improvement. What did you try to get to this point.

I am getting to stage where I am going to have to reinstall.

---

### Post by quaeritate on 2010-04-23
Turns out grub was fine all along.

Pressing and holding shift brings up the grub2 menu and from there I could pick the option to boot with logging. Then I could see it hanging when it was mounting my drives. Turns out the VirtualBox option I had added to my fstab file to allow USB access to my guest machines was the problem. I commented it out and now I can boot all they way into the desktop.

---

### Post by ThomWilhelm on 2010-04-24
You are THE MAN! You have saved me a whole reinstall today or many further hours of googling :)

I booted using a live CD this morning, commented out the virtual box line at the bottom of my /etc/fstab and now I can login just fine and most things are working as before! Thankyou so much for the suggestion.

Just for anyone interested, I unlike the other user DID mess up grub first so please follow this tutorial about getting it back if you are not getting to the "GRUB is loading..." stage.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Now I just need to try and solve and the minor issues, but for now who cares!

Thom :KS

---

### Post by quaeritate on 2010-04-24
Cheers Thom :)

You can mark your thread as solved if you like.

[Here]("https://bugs.launchpad.net/ubuntu/+bug/507881") is the relevant bug report for anyone that is interested.

---

### Post by ThomWilhelm on 2010-04-25
Have you managed to get the USB support for VirtualBox working? Its only a minor issue but its useful for being able to connect to mass storage devices.

Thom.

---

### Post by quaeritate on 2010-04-26
It should just work. I have not tried it though.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

