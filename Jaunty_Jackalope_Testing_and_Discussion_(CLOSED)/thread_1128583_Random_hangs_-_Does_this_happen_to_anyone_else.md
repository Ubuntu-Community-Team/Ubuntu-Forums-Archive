---
title: "Random hangs - Does this happen to anyone else?"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tcoffeep on 2009-04-17
I'm not sure if I'd be able to find a log for errors, as I wouldn't know where to look. I'm just getting used to the idea of logs. I'm just wondering if anyone else is getting random system hangs every 30-40 minutes? It usually only lasts for a few seconds, and a minute at most, but it gets annoying.

It started when I began using Dosbox ( but it's not because of DOSbox, I know that ). Maybe it has something to do with the :

INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)

I've been getting with every update?

---

### Post by tcoffeep on 2009-04-18
Noone? :(

---

### Post by gnomeuser on 2009-04-18
Are you using the nvidia driver? If so can you reproduce it without it loaded, it is known to abuse the stack and cause unpredictable latency which might be what you are experiencing.

Additionally is the problem linked to disk access, there are some known latency problems in the block layer and in ext3 which are being dealt with by the kernel developers. I don't know when fixes are hitting Ubuntu but I suspect that depend on issuing an SRU request with backported fixes. As a gapstop there are some ways to ease the pain a bit.

Things that might help:
Using the as io elevator
ionice the kjournal processes into the realtime class
switching ext3 to using data=writeback

---

### Post by jfernyhough on 2009-04-18
I've been hanging around here for a while, and yet those three suggestions are nicely cryptic. ;)

1) Add elevator=as (or elevator=deadline?) to the end of your GRUB kernel option (when booting press Esc, and E to edit the GRUB option).

2) Initially I'm thinking "?". Quick search yields $ sudo ionice -c3 -p{pid} for idle, not sure -c? for realtime, but apparently this only works on CFQ so it shouldn't be combined with 1).

3) I understand it, but can't remember how to do it. :)

(Plus btw, "stopgap")

---

### Post by gnomeuser on 2009-04-19
> **jfernyhough said:**
> I've been hanging around here for a while, and yet those three suggestions are nicely cryptic. ;)

1) Add elevator=as (or elevator=deadline?) to the end of your GRUB kernel option (when booting press Esc, and E to edit the GRUB option).

2) Initially I'm thinking "?". Quick search yields $ sudo ionice -c3 -p{pid} for idle, not sure -c? for realtime, but apparently this only works on CFQ so it shouldn't be combined with 1).

3) I understand it, but can't remember how to do it. :)

(Plus btw, "stopgap")

I am not here for hands holding, research is allowed as is asking questions politely. One reason to do this is to force people to learn about what the changes do, which is important as some of them may lead to very undesirable outcomes. Messing with the defaults for how your system does IO should not be taken lightly. This is also why he should start by eliminating known problematic modules such as the proprietary nvidia driver. The will cause problems and we cannot fix them. Only if the problem presists without that in use should he proceed to doing any of this.

1) the most simple way would be adding it to grub yes, there is also the option to do it in runtime by doing:

sudo -s
echo anticipatory > sys/block/sda/queue/scheduler
echo 64 > /sys/block/sda/queue/max_sectors_kb

That last one is another tweak not related to scheduling as such but it might have an impact on how long a stall we can see for an fsync. Remember to apply to all devices in use not just sda if you have more harddrives.

To have it applied at boot:

sudo vi /boot/grub/menu.lst and add elevator=as to the end of the line that goes something like:

kernel          /vmlinuz-2.6.28-11-generic root=/dev/mapper/dawkins-root ro quiet splash 

or when grub comes up press esc to get to the menu, then e over the item that indicates the kernel you want to boot. go to the line mentioned above and press e. Then add elevator=as to the end, press enter and then b to boot.

2) easiest way is to do:

sudo -s
for i in `pidof kjournald` ; do ionice -c1 -p $i ; done

In some cases this may make stalling worse, it is a little like fishing with dynamite, quick and dirty.

3)

sudo vi /etc/fstab and change, for ext3 partitions only (do it for anything else and it is your fault when bad stuff(tm) happens).

relatime to data=writeback,relatime

save and reboot.

There is a security risk involving multiuser setups doing this in case of crashes. 

You should not apply any of these changes unless you can afford the risk of data loss. It is intended only to narrow down the list of suspects. It is also not certain that they will help, nobody should apply these hoping for a smoother desktop experience. Stick with the defaults unless you have an io related problem and do not do anything you do not understand - research first, this is important and only apply when you feel you have an understanding of what a tweak does. This is for your safety and to help with any bug reporting at a later stage to know exactly what made a difference. 

Now do you understand why I do not give simple cut and paste commands?

---

### Post by jfernyhough on 2009-04-19
Yes, agreed. I probably should have added that the second two options were something I hadn't heard of and as such that post was my research for my future reference. :)

---

### Post by olskar on 2009-04-19
You are not alone, two threads about this already :(


[http://ubuntuforums.org/showthread.php?t=1127591](http://ubuntuforums.org/showthread.php?t=1127591) 
[http://ubuntuforums.org/showthread.php?t=1129414](http://ubuntuforums.org/showthread.php?t=1129414)

---

### Post by tcoffeep on 2009-04-19
> **gnomeuser said:**
> Are you using the nvidia driver? **If so can you reproduce it without it loaded, it is known to abuse the stack and cause unpredictable latency** which might be what you are experiencing.

I am using the nvidia driver. But I am unable to understand what you mean with the bolded. I'm still trying to get an understanding of linux, so, please forgive my confusion. Are you saying that a smart way to try and fix this would be to delete the nvidia proprietary driver? Maybe the x.org nv driver would suffice?

---

### Post by crjackson on 2009-04-19
> **tcoffeep said:**
> I am using the nvidia driver. But I am unable to understand what you mean with the bolded. I'm still trying to get an understanding of linux, so, please forgive my confusion. Are you saying that a smart way to try and fix this would be to delete the nvidia proprietary driver? Maybe the x.org nv driver would suffice?

I'm pretty sure the message is to remove or disable the nvidia proprietary drivers. You can do this by going to system>administration>hardware drivers. From there it will allow you to disable the proprietary driver.

Next reboot. Then test to see if the problem when away. Report back here with your results.

---

### Post by tcoffeep on 2009-04-20
> **crjackson said:**
> I'm pretty sure the message is to remove or disable the nvidia proprietary drivers. You can do this by going to system>administration>hardware drivers. From there it will allow you to disable the proprietary driver.

Next reboot. Then test to see if the problem when away. Report back here with your results.

Alright, though as I've stated, it's intermittent so it might take a few hours to get a real answer.

---

### Post by gotgenes on 2009-04-22
See [Bug #332549]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/332549/").

---

### Post by gnomeuser on 2009-04-22
> **tcoffeep said:**
> I am using the nvidia driver. But I am unable to understand what you mean with the bolded. I'm still trying to get an understanding of linux, so, please forgive my confusion. Are you saying that a smart way to try and fix this would be to delete the nvidia proprietary driver? Maybe the x.org nv driver would suffice?

Yes, the first step in debugging any problem is to get the system in an untainted state. This will allow any problem you have to be completely tracable. The nvidia driver is not always to blame but it abuses the stack quite a bit in odd ways and this can cause crashes in other programs unexpectedly which you would not directly blame on it but rather the program as a user.

Now in terms of this problem, the nvidia driver may be a contributor to making the problem as visible as it is (of course it also excludes a number of features like compiz which may also be related). Even if it isn't the cause, the problem is likely residing in the kernel (assuming it's IO related, it is hard to tell from your description) and with a huge, known problematic, piece of code running in there we can't debug (no source) it is safest to try to reproduce without it.

I would not recommend anyone using the nvidia driver, just for pure stability reasons. I have done QA work in Linux for many years and I have lost track of the number of bugs it has caused over the years. 

It does suck that there aren't any alternatives right now that provide 3D acceleration but nouveau is storming ahead and will fill that gap shortly. Till then you can use the nvidia driver but be adequately prepared to experience and deal with crashing and thus the risk of dataloss, or live with 2D only on the nv driver. Even on Windows the nvidia driver is reported to be [the cause](http://www.downloadsquad.com/2008/03/28/29-of-windows-vista-crashes-caused-by-nvidia-drivers/) of a majority of problems reported to the microsoft crash service.

There is good reason to be worried about that driver, not just for the crashing but you are running a very large amount of code as root directly in your kernel. It has already had one security problem but even in the highest quality code we are talking one bug per thousand lines of code. I don't feel very safe with that in there when I know we have no way to fix it or to inspect it for security holes. 

This isn't meant to be an nvidia driver bashing session though, it was meant to illustrate a bit of why it is important to have an untainted system when facing problems. You start by eliminating factors one by one and work your way towards the problem.

It does seem in this case looking at the bug report that was linked earlier that the crash is related to the nvidia driver and the compiz stack. Removing the driver should give us a definitive answeer. If disabling it and thus also compiz make it unreproducable we know the area to look in. If it does not the fun begins and we get to track down a really exciting bug (yes.. my bran is addled from years of bughunting, I should wear an Elmer Fudd hat)

---

