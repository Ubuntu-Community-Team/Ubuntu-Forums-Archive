---
title: "OMG Please someone help me !!!! Ubuntu 7.04"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by ileo on 2007-06-24
When I install Ubuntu version 6 it doesn't crash but I wanted to upgrade to version 7.04 and I did.

Okay well now I completely crash at startup, on oppenoffice applications, on any application .

Could it be that I don't have my Nvidia Driver installed ?

Here are my specs

(2) 1000MHZ Pentium 3 Processors
(2)  36GB SCSI Drives @ 10K RPM
Serverworks Motherboard (really old not sure what version)
FX5200 AGP 
2GB of Ram
.

Any help would be great .


One more thing : If I try to check the crash report it crashes so I already tried to reinstall it a couple of times and I get the same results and I get the same results with the live cd too but I don't get the same results with version 6 of ubuntu . Thank you for your help

---

### Post by ileo on 2007-06-24
update I tried booting in "graphics safe mode" and all the applications worked and I didn't crash one time. I'm guessing its my Nvida Driver for all I've tried I can't get the Nvidia driver to work "the one on nvidia's website" can someone give me some detailed instructions and a good driver to work on nvidia . I know my equipment is old but I would love to give ubuntu a shot and so far it looks very promising.

---

### Post by avik on 2007-06-24
Try installing the nvidia-glx driver:

```
sudo apt-get install nvidia-glx
```

Or consider [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by ileo on 2007-06-24
where am I supposed to enter that command ? in the terminal ?

---

### Post by s_h_a_d_o_w_s on 2007-06-24
Yes :D

---

### Post by ileo on 2007-06-24
Do I have to be connected to the internet for this ?

Please excuse my moronic questions . Thank you

---

### Post by avik on 2007-06-24
Yes you do, as apt-get will download the driver from the online repos.  And it's not a moronic question at all.  It's just that Ubuntu is different from Windows, and it takes some time for any of us to get used to the change.  :)

---

### Post by ileo on 2007-06-25
well since I am not connected to the internet this is what I did.

I went to Nvidia's site and downloaded the x86 Linux Driver burned it on a disk (from my windows maching) and loaded the disk in my linux machine. I tried copying it from the cd to the desktop and when I run it , it says "need to be ran as root" or something like that. Then I tried running from the cd and it says the same thing. Whats the deal . Does it have to be the original file. FYI: I love troubleshooting this is really fun.

---

### Post by ileo on 2007-06-25
well since I am not connected to the internet this is what I did.

I went to Nvidia's site and downloaded the x86 Linux Driver burned it on a disk (from my windows maching) and loaded the disk in my linux machine. I tried copying it from the cd to the desktop and when I run it , it says "need to be ran as root" or something like that. Then I tried running from the cd and it says the same thing. Whats the deal . Does it have to be the original file. FYI: I love troubleshooting this is really fun.

---

### Post by ileo on 2007-06-26
okay I think I figured something out after typing in every command I could think of I went with 

sudo + the nvidia file

not 

sh sudo + the nvidia file

the sudo one goes in but it tells me that I have a X server running and I need to disable it .

CTRL+ALT+F2 + Gnome will get me into Ubuntu with the Xserver right ?

---

### Post by ileo on 2007-06-26
bumpers

---

### Post by ileo on 2007-06-26
no help ?

---

### Post by davmaz on 2007-06-27
I feel your NVIDIA pain. You need to start Linux without going into an X session, which is the default for Ubuntu. If you don't know how to, let me know. Once you do, type "sudo su" and your password to become superuser. Then go to the directory with the NVIDIA file in it and type ./NVIdia_bla_bla.sh
That will run their script and install the drivers. If you're connected to the net, it will try to find an appropriate kernel. If it doesn't, or if you're not connected, then you need to install the kernel so it can build one for you with their drivers in it.

Hope this helps...

---

### Post by merlinus on 2007-06-27
Or you can try ENVY....

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

-merlin

---

### Post by ileo on 2007-06-29
> **davmaz said:**
> I feel your NVIDIA pain. You need to start Linux without going into an X session, which is the default for Ubuntu. If you don't know how to, let me know. Once you do, type "sudo su" and your password to become superuser. Then go to the directory with the NVIDIA file in it and type ./NVIdia_bla_bla.sh
That will run their script and install the drivers. If you're connected to the net, it will try to find an appropriate kernel. If it doesn't, or if you're not connected, then you need to install the kernel so it can build one for you with their drivers in it.

Hope this helps...

where could I download the appropriate Kernel to download, fyi I installed Envy and its crashing after making many many changes to the xorg file and it won't work well.

---

### Post by PoltoX on 2007-06-29
The most easy way to install the nvidia driver for me is to first download it an dplace it some where on the harddrive. Then enter ```
sudo /etc/init.d/gdm stop
```
this takes you out of X and this is where th fun starts ;)

Then go into the directory where your nvidia file is and type ```
sudo sh nvidia-package-name.run
```
Then it will ask you if you want to find a nvidia-kernel on the internet. Awnser no to that question, because we are going to compile our own kernel. 

when the kernel is compiled you have to edit your xorg.conf file. Edit the "driver" from "nv" or "vesa" or what it says to "nvidia". Save the file and then enter ```
sudo /etc/init.d/gdm start
``` to start X again.

note that you need to have the x-server-dev package installed to compile the nvidia kernel.

//Simon

---

