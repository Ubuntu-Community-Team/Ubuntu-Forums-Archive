---
title: "A New, Easy To Use Disk Formatter For GNOME! Finally!"
date: 2009-01-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-01-08
Great news!

It will not be in Gnome 2.26, is there any chance seeing it in 9.04 despite that?

Full story:
[http://www.phoronix.com/scan.php?page=article&item=gnome_format&num=1](http://www.phoronix.com/scan.php?page=article&item=gnome_format&num=1)

---

### Post by Gourgi on 2009-01-08
found it earlier in brainstorm :D
[[IMG]http://brainstorm.ubuntu.com/idea/17131/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/17131/)

---

### Post by ronacc on 2009-01-08
I'm trying to get this to build , sofar I've got it to configure ok but the build fails from what looks more like a policy problem than a build error. 
```
gnome-format-dialog.vala:51.25-51.67: error: class creation methods only allow property assignment statements
gnome-format-hal-storage-provider.vala:33.25-33.66: error: class creation methods only allow property assignment statements
Build failed
 -> task failed (err #1): 
	{task: valac_task gnome-format-dialog.vala,gnome-format-hal-storage-provider.vala,gnome-format-main.vala,gnome-format-storage-provider.vala,gnome-format-storage.vala -> gnome-format-dialog.c,gnome-format-dialog.h,gnome-format-hal-storage-provider.c,gnome-format-hal-storage-provider.h,gnome-format-main.c,gnome-format-main.h,gnome-format-storage-provider.c,gnome-format-storage-provider.h,gnome-format-storage.c,gnome-format-storage.h}

```

---

### Post by ronacc on 2009-01-09
several more try's with different versions of vala each fails with a different vala error . by googleing around I found a fedora 10 rpm (64bit) and extracted that and hand copied the files to the correct dirs , it runs from term and if run with sudo will format an usb stick ( without sudo it gives a permision error ) , should be nice when finished .

---

### Post by MacUntu on 2009-01-10
Never thought that ppl could find gparted too complicated.

---

### Post by ronacc on 2009-01-10
I think newbes might find gparted a bit complicated , particularly since it dosen't always report drive names/numbers the same as Ubuntu , it also presents a lot of options that arent aplicable to the simple formating of a usbstick/mediacard/floppy which is the focus of gnome-format.Gnome-format also dosen't even show your internal drives thus minimising the chances of a mistake wiping out something you would rather not lose.

---

### Post by gnomeuser on 2009-01-10
no no no.. this is all wrong. Having a separate application for formatting is just as insane as having one for burning (oh wait.. Brasero.. but I ranted on that [before](http://davidnielsen.wordpress.com/2008/11/03/im-anti-brasero/)).

This is functionality which should be integrated in places like nautilus, your media player and where else it's relevant. When DeviceKit-disks also provides libraries and widgets which application developers can use to do this kind of integration. By doing it this way we allow greater room for innovation in development, this approach has always shown to bring about far more compelling experiences and quality.

---

### Post by plun on 2009-01-10
Yup... 100 % correct

It has been a standard function as long as I can remember within another famous OS...

[[img]http://www.ubuntu-pics.de/thumb/8167/capture_4NI82S.png[/img]](http://www.ubuntu-pics.de/bild/8167/capture_4NI82S.png)

---

### Post by ronacc on 2009-01-10
I whole heartedly agree that this functionality "should " be integrated into nautilus . However this is in the pipeline now . Lets use it until such time as the functionality becomes available via nautilus . In my book "I can use this today even though it is not the most elegant solution " beats "this will be so wonderful if it ever apears at some unspecified future date".

---

### Post by Gina on 2009-01-10
Yes, I agree too.  One example of where another OS has the right approach and we haven't IMV.  I think using GParted to format removable devices is ridiculous - too complicated for the job in hand and far too dangerous for the ordinary user - no problem for we who use it all the time, of course.  "Sledgehammer to crack a nut"!

---

### Post by MacUntu on 2009-01-10
> **Gina said:**
> "Sledgehammer to crack a nut"!

But then I only format a partition when repartitioning the device. If I just want the data be gone I delete it in Nautilus - is that wrong?

---

### Post by ronacc on 2009-01-10
what works for you IS right for you .

---

### Post by olskar on 2009-01-10
I also agree with having this integrated in Nautilus instead, I think I actually heard that work was being done to make it so

---

### Post by bash on 2009-01-10
As Gnomeuser has said, it will come as part of DeviceKit once that is stable and useable.

---

### Post by gnomeuser on 2009-01-10
> **bash said:**
> As Gnomeuser has said, it will come as part of DeviceKit once that is stable and useable.

Actually it's already here, for the most part, DeviceKit-disks is running here on my Fedora 10 desktop with the reference implementation gnome-disk-utility. Not perfect yet but the code is all there. 

DeviceKit is parallel installable with HAL, there are already uses for DeviceKit-power in GNOME 2.25.x with gnome-power-manager supporting it. 

I would rather see the focus being on doing things right, it is not as far off as people think it is in this case. That aside, if we first replace the current way of performing formatting with another one we admit is going to be replaced "very soon"(tm) we are hurting our usability long term and digging into our limited ressource pool for support needlessly. Remember these are things that need to be tested, documented and supported though their lifetime.

---

### Post by ronacc on 2009-01-10
please note I was not advocating replacing our current way of formating . I was noting that gnome-format might be a nice additional, easy way of handling removeable devices only ,when it becomes a little more mature .

---

### Post by olskar on 2009-02-26
This has been implemented according to this:
[http://brainstorm.ubuntu.com/idea/17131/](http://brainstorm.ubuntu.com/idea/17131/)

I wouldn't call it implemented but it is in the repos :) Give it a try!

---

