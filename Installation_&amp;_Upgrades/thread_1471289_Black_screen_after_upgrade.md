---
title: "Black screen after upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by voodoo_doctor on 2010-05-03
I have problems with booting to Ubuntu after upgradte to 10.04. All I get is a black screen and nothing happens. However, my Ubuntu boots perfectly if I select "recovery mode" in the grub boot list and select "failsafeX". Any ideas how to fix this?

I tried to do what is suggested in several threads (quoted under), but this did not help. This just made ubuntu logo stay longer on screen, but it still results in black screen.

Graphics card: Intel Extreme Graphics II

> 
One fix for this is to create this file.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```


Source: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by sfbate on 2010-05-03
I get the same behavior on my Gateway M405.  The fix you found displays the loader for a bit longer, but the end result is the same: black screen.

---

### Post by voodoo_doctor on 2010-05-04
> **sfbate said:**
> I get the same behavior on my Gateway M405.  The fix you found displays the loader for a bit longer, but the end result is the same: black screen.

Yes, exactly. Anyone that managed to solve this problem?

---

### Post by voodoo_doctor on 2010-05-04
sfbate: Try booting to failsafe mode, and installing nVidia drivers. I guess your case is a bit different after all.

---

### Post by Scari on 2010-05-04
Anyone else thinking not much testing happened in the beta process? I think testers were just using it to be using it not giving much constructive feedback.....so far from personal experience of having to revert everything back to 9.10 and from what I've read since release this upgrade gets a grade of D- at best so far....

---

### Post by voodoo_doctor on 2010-05-04
Nah, it is not that bad really, imho. Yes, it has some bugs, but I have experienced the same with every release. I also installed 10.04 on another PC and it worked like a charm. Almost. But close enough to something I can live with. 

However, as far as I can see, it also seems like the video was pretty faulty for nVidia, ATI & Intel cards... I mean, if would have been only one of them... But all tree?! Anyways, that's getting off-topic here.

Back to the problem: I might have found a solution, but I would like to test it before I post it here. It seems like there are several problems that lead to black screen. But let me test it. Stay tuned for updates. :)

---

### Post by coln_panic on 2010-05-05
> **sfbate said:**
> I get the same behavior on my Gateway M405.  The fix you found displays the loader for a bit longer, but the end result is the same: black screen.

i also have a gateway m405, this is what i did to get it working... although i don't consider this a final fix, just to get it going so i can work on it better:

the problem appears to be xorg.conf is missing, no clue how this happened.  i've had more issues installing this release than any previous ubuntu, but whatever, seems to run well once installed...

grab a previous release boot disk and boot to the desktop.  if you don't have one available, boot to the 10.04 livecd, select language, press f6 to get options and add " xforcevesa" to the end of the line.  press enter to boot, and hopefully it will boot you to a desktop.

next you need an xorg.conf on your local drive, so we'll mount the local drive (mine is /dev/sda1) and copy xorg.conf from the livecd filesystem:
```
sudo mkdir /disk
sudo mount /dev/sda1 /disk
sudo cp /etc/X11/xorg.conf /disk/etc/X11/xorg.conf 
```

reboot and you're golden (once again, hopefully...)

---

### Post by voodoo_doctor on 2010-05-05
This might help too: [http://ubuntuforums.org/showthread.php?t=1472054](http://ubuntuforums.org/showthread.php?t=1472054).

---

### Post by voodoo_doctor on 2010-05-12
[COLOR="Navy"][Workaround A]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")[/COLOR] helped me.

---

### Post by voodoo_doctor on 2010-05-12
Hope the rest of you solved your problems as well! :)

---

### Post by sfbate on 2010-05-12
Yay! Workaround A worked for me too.

Thanks for the pointer, voodoo_doctor.  I owe you one.

---

