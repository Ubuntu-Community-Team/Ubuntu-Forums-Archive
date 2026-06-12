---
title: "Boot live cd on dell optiplex gx110"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by syst3m on 2007-08-14
i got an old dell optiplex gx110 and i want to install ubuntu 7.04 on it, but im running in to problems every time i boot the live cd. sometimes i get "bin/sh: can't access tty; job control turned off" and sometimes the screen just goes black and stays that way.

when i get the "bin/sh: can't access tty; job control turned off" error, i tried some of the solutions on this forum, but none of them work, they make the screen go black.

plz help me.

---

### Post by Pumalite on 2007-08-14
I'm not familiar with your specs, but I suspect you have low memory; in that case you might be better off with Xubuntu Alternate CD. You might have graphics or hardware problems. You can try to boot your live CD making a swap partition ahead of time in you hard drive .

[http://ubuntuforums.org/showthread.php?t=273018&highlight=dell+optiplex+gx110](http://ubuntuforums.org/showthread.php?t=273018&highlight=dell+optiplex+gx110)

---

### Post by syst3m on 2007-08-14
> **Pumalite said:**
> I'm not familiar with your specs, but I suspect you have low memory; in that case you might be better off with Xubuntu Alternate CD. You might have graphics or hardware problems. You can try to boot your live CD making a swap partition ahead of time in you hard drive .

where can i download the Xubuntu Alternate CD? and wat did u mean about making swap partition ahead of time in my hard drive? sorry im  new to ubuntu.

---

### Post by Pumalite on 2007-08-14
Here is the link: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Do read the  link to the thread I provided. To make the swap partition you can use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php). It would be better if you detailed what you are trying to do. In the thread you will also find other hints as to what you could do.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by syst3m on 2007-08-14
ok wat im trying to do is install ubuntu, but i cant since my live cd isnt booting up properly. i get the ubuntu boot menu, when i press enter it starts to look, but then i either get "bin/sh: can't access tty; job control turned off" error or the screen just goes black.

hope this clears it up.

---

### Post by Pumalite on 2007-08-14
You could try this before trying other things:

 Re: Installing Ubuntu in Dell Optiplex GX110
Another one.... These machines are giving the installer fits. What is happening (or NOT happening) is that it fails to mount the CD. If anyone can come up with a sure fire way around this, I'd love to know.
+-+-+-+Edit+-+-+-+
Used:
Code:

boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false

Worked on all 6 of these donated GX110's.

---

### Post by syst3m on 2007-08-14
> **Pumalite said:**
> You could try this before trying other things:

 Re: Installing Ubuntu in Dell Optiplex GX110
Another one.... These machines are giving the installer fits. What is happening (or NOT happening) is that it fails to mount the CD. If anyone can come up with a sure fire way around this, I'd love to know.
+-+-+-+Edit+-+-+-+
Used:
Code:

boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false

Worked on all 6 of these donated GX110's.

trying but still wont load, black screen with text, more keeps on coming, and it hasnt stopped in like 20mins.

[[IMG]http://img181.imageshack.us/img181/1276/1000367ov4.th.jpg[/IMG]](http://img181.imageshack.us/my.php?image=1000367ov4.jpg)

---

### Post by Pumalite on 2007-08-14
Ubuntu does not like your hardware. Unfortunately, someone that knows more about these laptops will have to chime in.

---

### Post by syst3m on 2007-08-14
> **Pumalite said:**
> Ubuntu does not like your hardware. Unfortunately, someone that knows more about these laptops will have to chime in.

its not a laptop. o.O its a desktop.

and i still need help!

---

### Post by syst3m on 2007-08-16
can any1 help me? i still cant install ubuntu!

---

### Post by ZenoGia on 2007-08-21
well I just picked up 5 Dell OptiPlex GX110 from a company that was giving them away and I successfully installed ubuntu 7.04!  it runs perfect!!!!  I think your problem is that your when you burned your image to disk it didn't burn correctly and you have to try it again.

---

### Post by graphiteman on 2007-08-24
I'm running into the same problem Syst3m is running into.  What I am not clear on is how to use the boot options that Pumalite posted:

------
boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false
------

Do I need to delete the existing boot options after hitting F6, or add this onto the end?  Here is what is already there:

------
file=cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
------

Thanks in advance.

---

### Post by Pumalite on 2007-08-24
Add to the end.

---

### Post by graphiteman on 2007-08-24
So far, no luck.  Here's the string I tried (exactly):

```

file=cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false

```

I also tried it without "boot:", to no avail.  Am I missing something dumb here, or is it just not working the way you expected it to?  Is it possible there's a typo in there?

Thanks for your help.

---

### Post by Pumalite on 2007-08-24
Now try replacing the options from the beginning.

---

### Post by the_colonel on 2007-10-10
> **syst3m said:**
> can any1 help me? i still cant install ubuntu!


I found the solution for me after a bit of trolling the net. I was getting the same "can't access tty:job control turned off" message using 7.04 desktop on my Optiplex GX110. I tried Xubuntu 7.04 as well and had the same result. The answer - after the initial Ubuntu boot up screen , pop a formatted floppy (doesnt need to be bootable) into the a: drive and then press return to boot the CD. It accesses the floppy multiple times and then boots from the CD.
I had noticed before that my floppy drive sounded like it was being accessed multiple times before the error message appeared.
Hope this help.

---

### Post by wakeboarder on 2007-10-28
Although I love ubuntu for old boxes like these ones I would recommend Puppy Linux.
The performance you'll get will be like night and day compared to ubuntu!

:guitar:

---

