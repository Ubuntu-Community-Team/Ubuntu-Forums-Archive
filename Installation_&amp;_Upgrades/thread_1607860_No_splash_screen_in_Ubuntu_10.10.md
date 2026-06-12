---
title: "No splash screen in Ubuntu 10.10"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Deepak Jindal on 2010-10-28
Hello gurus, 
i have ubuntu 10.10, its an clean installation, and it was running fine. all things were good except that i didn't liked the splash screen, so i decided to make it better. and i found an script for that, without thinking twice i runit on my system and BAMM!!. default splash screen is gone, now everytime i boot, i see text bootup process(also in ugly low resolution). 

url: [http://d0rkye.zsenialis.com/?p=167](http://d0rkye.zsenialis.com/?p=167)

1. My question is how can i restore the default splash screen in ubuntu 10.10
2. if its not possible to retrieve the splash screen back, how can i increase the resolution of those text login process.. ??

---

### Post by Deepak Jindal on 2010-10-29
No answer yet!!...

---

### Post by tristan on 2010-10-29
The plymouth splash system is pretty annoying and difficult to get working well.

I'd suggest installing and running startupmanager
```
sudo apt-get install startupmanager
```

This will allow you to set the resolution, and whether you can see the splash and any text. Depending on how badly your previous script broke things, you might be able to get something back.

---

### Post by Deepak Jindal on 2010-10-29
> **tristan said:**
> The plymouth splash system is pretty annoying and difficult to get working well.

I'd suggest installing and running startupmanager
```
sudo apt-get install startupmanager
```

This will allow you to set the resolution, and whether you can see the splash and any text. Depending on how badly your previous script broke things, you might be able to get something back.

hi, after installing startup-manager this is what i got...!!

linux@Linux:~$ startupmanager
Found linux image: /boot/vmlinuz-2.6.35-22-generic
ult
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda4
done
Grub2 detected
Usplash not detected
Splashy not detected
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 193, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 202, in setup_widgets
    self.set_shared_grub_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 223, in set_shared_grub_widgets
    self.timeout_spinner.set_value(self.grub.get_timeout())
  File "/usr/lib/pymodules/python2.6/bootconfig/grub.py", line 91, in get_timeout
    timeout = utils.extract_number(line)
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 64, in extract_number
    match = number_filter.search(line)
TypeError: expected string or buffer
linux@Linux:~$

---

### Post by maximus20895 on 2010-10-29
Looks like you have a "free" version of windows there...

---

### Post by Deepak Jindal on 2010-10-31
still not able to find anything on net which can helps me setting a new splash screen, i previously had problem in plymouth, + changing login screen in ubuntu.. looks like ubuntu developers will do anything to make the bootup process faster, even if they had to limit the customization functionality in ubuntu. i personally happy if my ubuntu takes 5 more seconds and give me a good looking bootscreen as i intented..

---

### Post by Jechem on 2010-10-31
try this in terminal:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

sudo update-initramfs -u

read: [http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html](http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html)

---

### Post by Deepak Jindal on 2010-10-31
> **Jechem said:**
> try this in terminal:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

sudo update-initramfs -u

read: [http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html](http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html)

yes, had tried this alredy, and again after you suggested but didnt worked. if you read my output above, it tells no usplash found. and this post if for CHANGING usplash screen.. i guess it was clear it wont work..!!

---

### Post by Jechem on 2010-10-31
10.10 is using plymouth now for its splash screen. try checking at if the file plymouth is present at /lib/plymouth. if not maybe I can send you the files

---

### Post by Jechem on 2010-10-31
I have attached a zip file. unzip and extract the attached file 

type sudo nautilus in terminal then copy and paste plymouth folder into /lib/

type in terminal:

sudo update-alternatives --config default.plymouth

choose ubuntu-logo.plymouth

sudo update-initramfs -u

reboot
you should have a splash screen

---

### Post by Deepak Jindal on 2010-10-31
> **Jechem said:**
> I have attached a zip file. unzip and extract the attached file 

type sudo nautilus in terminal then copy and paste plymouth folder into /lib/

type in terminal:

sudo update-alternatives --config default.plymouth

choose ubuntu-logo.plymouth

sudo update-initramfs -u

reboot
you should have a splash screen


well, i checked the /lib/plymouth/ and its alredy there. still i copied your files there, and run the script, still no gain.. any idea why?? anyways, thanks for your support...

---

### Post by Jechem on 2010-11-01
try this link:
[http://www.n00bsonubuntu.net/content/install-zorin-splash-screen-manager-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/install-zorin-splash-screen-manager-ubuntu-1010-maverick-meerkat)

haven't tried it though but worth a look.

---

### Post by Deepak Jindal on 2010-11-01
> **Jechem said:**
> try this link:
[http://www.n00bsonubuntu.net/content/install-zorin-splash-screen-manager-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/install-zorin-splash-screen-manager-ubuntu-1010-maverick-meerkat)

haven't tried it though but worth a look.


i did installed it, but it alreayd says xubuntu screen installed. after your recommendation, i reinstall normal ubuntu logo and text screen, still no splash screen.. however, at boot screen i read that v86d not found. and i run apt-get install v86d and some text are now in good resolution.. but not from starting.. please suggest something.. i had learned one new thing, never run unknown scripts without reading it..:(

---

### Post by Jechem on 2010-11-01
You could give this a try: 
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml).

10.10 uses the same as 10.04 basically.

If this still won't work I'm out of ideas.:(

---

### Post by lmellor on 2010-11-01
Hi, I've been having real problems with plymouth on my machine which I managed to fix today.

My simple fix was to purge grub in synaptic, remove all config files, etc.  When it's done simply reinstall setting "quiet splash" as the defaults it asks for.

After this I went ahead and installed burg (I really dislike seeing any text as my computer starts or shuts down) which I gave the same commands to.

My plymouth now looks awesome, full screen, full resolution and I have added the ubuntu-sunrise theme to it.

I do hope that this helps, I've been trying for weeks now

---

### Post by Deepak Jindal on 2010-11-02
anyone have anyidea how to get my splash screen back in ubuntu 10.10 ??

---

### Post by Jechem on 2010-11-02
i think you have to reinstall 10.10 to solve it

---

### Post by Deepak Jindal on 2010-11-03
> **Jechem said:**
> i think you have to reinstall 10.10 to solve it

well yeah.. soon gonna buy new hdd, will reinstall new ubuntu there. till then, lets see if anyone can give me a solution for this one.. by the way, i think the problem is related to grub configuration. can you give me any link for reinstalling grub2 in 10.10 ?? i m sure that script had made changed in grub2 file. and by reinstalling grub2 it should resolve the problem, what do you think??

---

### Post by Jechem on 2010-11-03
this is explaining Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
this is a how to remove and reinstall Grub2:  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Deepak Jindal on 2010-11-03
Finally Win!! , it worked.. 

so the problem was in grub configuration. it done something wrong with pymouth.. becuase of that script... 

anyways, purgeing grub2 and reinstalling it worked for me, i finally had got back my old ugly boot screen, will try new plymouth themes now.. 

thx Jecham for your time and help...:KS:KS:KS

---

### Post by Deepak Jindal on 2010-11-03
> **lmellor said:**
> Hi, I've been having real problems with plymouth on my machine which I managed to fix today.

My simple fix was to purge grub in synaptic, remove all config files, etc.  When it's done simply reinstall setting "quiet splash" as the defaults it asks for.

After this I went ahead and installed burg (I really dislike seeing any text as my computer starts or shuts down) which I gave the same commands to.

My plymouth now looks awesome, full screen, full resolution and I have added the ubuntu-sunrise theme to it.

I do hope that this helps, I've been trying for weeks now

Yes bro, you idea did worked.. thanks for your time also.. :)

---

### Post by Jechem on 2010-11-03
glad to be of help

---

### Post by bmcglone on 2010-11-26
I am having the same problem with start up and shut down splash screens.  Tried Start up Manager and purging Grub.  No change.  Any other ideas.

Thanks.

EDIT:  Problem solved.  Purged Grub, then executed code from post #8, then tweaked with start up manager.

---

### Post by HJB on 2010-12-03
This is all to difficult
What I did in Kubuntu 10.10 is

sudo nano /etc/default/grub

then add this one line

GRUB_CMDLINE_LINUX="splash vga=795"

save file and

sudo update-grub2

and reboot!

for more info look here [http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/]("http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/")

Hope this helps.:P

---

### Post by ajay_vishvanathan on 2011-02-04
i have a doubt.. there is an option in startup manager called "timeout in seconds" whats that??

---

