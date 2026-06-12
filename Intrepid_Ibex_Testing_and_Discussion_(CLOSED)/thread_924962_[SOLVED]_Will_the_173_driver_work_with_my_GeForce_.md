---
title: "[SOLVED] Will the 173 driver work with my GeForce FX5200"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-09-20
I am wondering if the Nvidia 173 driver will work with my GeForce FX5200 graphic card?  Will I be able to use the nvidia driver in xorg.conf, so that I can run compiz? Thanks for your help in advance.

Donnie

---

### Post by doorknob60 on 2008-09-20
I'm 95% sure I used the 173 driver just fine with my old 5200 (compiz and everything). I don't think the 177 driver works with it though.

---

### Post by ronacc on 2008-09-20
both the 173 and 177 drivers work with the fx5200 and should show up in system>administration>hardware drivers

---

### Post by alienexplorers on 2008-09-20
Do you have to edit the xorg.conf file to get it to work.  I loaded the 173 driver and my computer keeps loading in low graphics mode.  Could you list your xorg.conf file so I can see how yours is setup.

---

### Post by psyke83 on 2008-09-20
Hi,

I recently upgraded my FX 5200 to a GeForce 6200, but I seem to recall that the 177 driver didn't work correctly. Yes, the 173 driver will work correctly.

P.S. I noticed that you have some trouble remembering threads on this forum; I have an idea that may make things a little easier:

Right click on this link and choose "Bookmark this link": [http://ubuntuforums.org/search.php?do=finduser&u=75896](http://ubuntuforums.org/search.php?do=finduser&u=75896)

When the "Edit this bookmark" dialog box pops up, type something in the "Name" part, e.g. "My Ubuntu Forums threads", click the dropdown menu to the right of "Folder", and select "Bookmarks Toolbar", then click "Done". That will put the link on Firefox's bookmarks toolbar in plain sight, so you can keep track of all your posts. I find it pretty handy!

---

### Post by gjoellee on 2008-09-20
I am using the same driver and same card right now :)

If you are unlucky and come into low-graphics mode take a look here: [http://www.kshoster.net/?c=tipsandtricks&h=xfix](http://www.kshoster.net/?c=tipsandtricks&h=xfix)

---

### Post by alienexplorers on 2008-09-20
Tried using xfix in recovery mode and I am still in low graphic mode.  Also if I bring up nvidia-settings it tells me I am not using the nvidia 173 driver or any nvidia driver.

---

### Post by Steveway on 2008-09-20
> **ronacc said:**
> both the 173 and 177 drivers work with the fx5200 and should show up in system>administration>hardware drivers

That is not true.
Nvidia has dropped support for the 5*** series.
Anything newer than the 173-versions of their drivers won't work.
Thanks Nvidia, for dumping this perfectly working card, I would buy a new one, but this is a Laptop.
Luckily nouveau is coming along nicely.

---

### Post by alienexplorers on 2008-09-20
What do I need to do to get my card and the nvidia drivers to recognize the"nvidia" drivers and not load up in low grapics mode.

---

### Post by ronacc on 2008-09-20
did you enable the driver in system>administration>hardware drivers .how did you install it ? with intrepid it is best to let jockey do it for you through system>administration>hardware drivers if you are using the driver straight from nvidia it may need some editing to the installer script , that is already done with the ones from the repos .

@ Steveway  they did not drop support for the FX5200 you need to look in the beta drivers to find it , see attached screenshot from nvidia .

---

### Post by ronacc on 2008-09-20
oops forgot the screenshot
@ alienexplorers attach a copy of your /etc/X11/xorg.conf

---

### Post by Steveway on 2008-09-20
> **ronacc said:**
> did you enable the driver in system>administration>hardware drivers .how did you install it ? with intrepid it is best to let jockey do it for you through system>administration>hardware drivers if you are using the driver straight from nvidia it may need some editing to the installer script , that is already done with the ones from the repos .

@ Steveway  they did not drop support for the FX5200 you need to look in the beta drivers to find it , see attached screenshot from nvidia .

From: [http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682)
> Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. **GeForceFX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.**

---

### Post by ronacc on 2008-09-20
I stand corrected , the latest driver 177.76 hadn't shown up on the download page when I took the SS this AM .

---

### Post by rondackcpu on 2008-09-20
This is a very interesting post.  My Dell 5160 laptop has the Nvidia GeForce FX5200 card in it.  While I was running 8.04.1, Ubuntu suggested a better driver for the card -- the "nvidia-glx-new" driver, which is labeled 169.12 in Synaptic.  That driver works just fine in 8.04.1.

When I install 8.10, Ubuntu makes a suggestion for a driver which puts me in "resolution hell"  -- limits the choices to 640x480 and 800x600.

Reading the notes in Synaptic, I find the "nvidia-glx-96" driver is recommended for the 5200 card.  Installing it instead of Ubuntu's suggested, works just fine -- resolution is set at 1400x1050 (or maybe 1440x1000, can't ever remember).  But the Update-Manager has a bunch of updates ready for the system.

Something in the updates hoses the computer.  Immediately from boot-up, the CPU is running flat out.  I try to get a terminal to try "top" to see what is running, but I can't even get the terminal.  Afraid that the CPU will kill itself, I try rebooting several times, but always flat out.

Back to 8.04.1 and "nvidia-glx-new".  I really regret I can't run 8.10 on that machine.

Any ideas?

CRS

---

### Post by alienexplorers on 2008-09-20
I found out I can not run the nvidia-173 driver with my FX5200 card.  The 173 driver requires your processor to support the SSE instruction set.  My old AMD K6-III only supports MMX and 3DNOW so the 173 driver is out for me.  Guess I will have to wait for the new 96.43.07 driver to see if I can get it running.

---

### Post by ronacc on 2008-09-20
ok so it isn't the driver itself but the combination of driver and cpu , if the 173 driver is what is shown in system>administration>hardware drivers  file a bug on it , saying that the 173 driver dosent work with your cpu , and as far as I know the 96 driver dosen't yet work with the new xorg so you may be stuck for awhile .

---

### Post by doorknob60 on 2008-09-20
Simple solution, install the 169 driver that's always been working: [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by psyke83 on 2008-09-20
> **doorknob60 said:**
> Simple solution, install the 169 driver that's always been working: [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

That's not proper advice at all. Manually installing the nvidia driver will break upon new kernel releases. Users should *always* keep to the official packages.

I had an FX 5200 and the 173 drivers worked fine.

alienexplorer, we need some information to help you properly, for example: post your /var/log/Xorg.0.log, /etc/X11/xorg.conf and any useful dmesg output:
```
$ dmesg | grep -i nvidia
```

---

### Post by ronacc on 2008-09-20
@psyke83 from his post above it apears that the problem is with his CPU not his GPU , he is using an amd K6 , which is not supported by the 173 driver series  ,  I am using the 173 driver with an fx5200 right now but with an AMD64x2 the K6 is an old obsolete processor pre athalon .

---

