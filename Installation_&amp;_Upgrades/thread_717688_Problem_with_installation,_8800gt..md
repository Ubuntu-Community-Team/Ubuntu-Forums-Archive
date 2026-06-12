---
title: "Problem with installation, 8800gt."
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Suilenroc on 2008-03-07
Hey there all. This is my first post here, and my first time trying to install (or even thinking about) Linux. I've heard some great things about it, so I'm gonna give it a shot. 

So, I downloaded the ISO, made sure the checksums matched, placed it on the CD, and booted into the CD. However, that's as far as I get, as, whenever I select anything, and the linux kernel loads, my display stops responding. I've heard that Ubuntu has some hardware malfunctions, is my 8800gt to blame? 

Thanks very much! 

-Suilenroc

---

### Post by uberlube on 2008-03-07
Nope your Nvidia is not to blame and it is a good thing you have it as compared to ATI. During boot you need to specify to the process what your vga is. Edit the boot line from the live CD by pressing F6 and delete 'quiet splash' and add 'vga=791' and try that. Then once you have Ubuntu installed use "ENVY' to install the nvidia drivers and then your boot will automatically detect your graphics card.

---

### Post by timewave on 2008-03-07
> **uberlube said:**
> Nope your Nvidia is not to blame and it is a good thing you have it as compared to ATI. During boot you need to specify to the process what your vga is. Edit the boot line from the live CD by pressing F6 and delete 'quiet splash' and add 'vga=791' and try that. Then once you have Ubuntu installed use "ENVY' to install the nvidia drivers and then your boot will automatically detect your graphics card.

thanks, this allowed me to boot the live cd on my machine when nothing else that i tried would.

(for reference, i'm running a gigabyte ga-p35-ds3l and nvidia 9600gt)

---

### Post by Suilenroc on 2008-03-07
Allrighty, so, I just got home from school. Quick update:

I did that vga=791, and that allowed it to boot into a prompt discussing "Safe Graphics Mode." It told me to select my GPU and Monitor type. As my monitor wasn't on the list, I selected the normal generic kind, and set it at the resolution (1680x1050). I then selected the GPU from the list, the Nvidia 8 series entry. I then let it go, and...

blank screen. I thought that maybe, just maybe, it was booting. So I left it on all day when I left for school. Get home, and nada. 

So, suggestions? Thanks!

---

### Post by Suilenroc on 2008-03-07
Is bumping allowed here? This isn't a veiled bump (ok, it is), but it's also a sincere question. :guitar:

---

### Post by uberlube on 2008-03-07
Is (1680x1050) your monitors native resolution?

---

### Post by Suilenroc on 2008-03-07
Yes, yes it is. It's a 20 inch.

---

### Post by uberlube on 2008-03-07
Did you also delete quiet splash? And try to set it to a small res size. like 1024 x 786 and see what happens.

---

### Post by Suilenroc on 2008-03-07
I'll go ahead and try that. And yes, quiet splash was deleted. 

Will report back soon.

---

### Post by Suilenroc on 2008-03-07
Oh boy, managed to screw up my windows partition. 

Meh, I've needed to reinstall anyways. Posting this on my ipod, btw.

---

### Post by uberlube on 2008-03-07
:lolflag: So what are you going to do now? Did you manage to boot up the live cd finally?

---

### Post by Pumalite on 2008-03-07
For the Live CD: I at least got the boot menu screen. From there you can press F6 or so (can't remember exactly) and change kernel boot options. Change "splash" to "nosplash".

Now it should come up and you can install your system. Now, BEFORE you reboot after installation, edit the file "/boot/grub/menu.lst" in the newly installed system. Probably you first have to mount the device where you installed the system to, then don't forget that the upper path is given relatively to the mount used for that device, Then, simply change every occurance of "splash" to "nosplash" again.

Now you should be able to use your system. And now you can go on and install the nvidia drivers.

__________________

---

### Post by Suilenroc on 2008-03-07
so, I now at least have Linux installed. However, I can't connect to the Internet at all. I have a linksys witless n reciever. Strange thing, though. Some of the menus and commands that it is telling me to do arent there or available.

---

### Post by Suilenroc on 2008-03-07
hey guess what now. I just set the desktop resoluton to 1680 by 1050 and now its all screwed up. I can't see ****. So I'm just reinstalling ububtu. I mean I like a problem. But this is ridiculous. I NEED Internet.

---

### Post by adelgado on 2008-03-14
I have a suggestion for you:

If you have access to another computer and know how to use IRC, get some help at #ubuntu at irc.freenode.org .

The reason I say this is that Internet configuring is something that if you can't do it by yourself and it doesn't configures itself, it's really a trial and error process until you find out what's the problem.

As there are MANY types of hardware, connections, cables etc. it is necessary to exhaust all possibilities and configurations, and while through IRC you can receive an instruction on one computer and execute it on the other, through a Forum it is a really slower process.


Anyway, you can always do both. To help, you could specify all your hardware and router and how you connect yourself to the internet.

Also, you way want to start a new thread. Should you do so, you could post the URL here so that people who were reading you can follow up and help you, and people who weren't can see a new thread with a specific problem (i.e. people who come here for the first time still come thinking you have a problem with your 8800GT).


Hope I can help.

Great Video Card, by the way


Salute!

---

