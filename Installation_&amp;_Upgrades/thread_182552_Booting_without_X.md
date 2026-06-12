---
title: "Booting without X"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2006-05-26
Folks,

I want to install NVidia's video display drivers. It involves running a setup program in a non-GUI terminal. Try as I might, I couldn't find what runlevel to set so that it doesn't go into Gnome and presents me with a login prompt. I tried setting the runlevel 2 in /etc/inittab and also on the Grub menu but it still always brings up the Gnome login. 

How do I accomplish this ?

Thanks in advance.

---

### Post by bruce89 on 2006-05-26
There is no need to login to a terminal.  Do this in the terminal (Applications>System tools>Terminal) to install the drivers -
```
sudo apt-get install nvidia-glx
```
then
```
sudo nvidia-glx-config enable
```

---

### Post by mailforbiz on 2006-05-26
I was referring to the proprietory driver which I downloaded from the NVidia site. 

[http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html")

The install script for the driver complains that I have X server up when I try to run it. It says stop X and to run the script from a non-GUI terminal.

I am not sure what the difference is between this driver and the nvidia-glx  one. I'm just going here with the belief that usually the manufacturer is bound to have a more advanced driver. Is that a valid assumption or should I stick to the nvidia-glx drivers? One observation is that Nvidia doesn't seem to have a different driver for each flavor of Linux.

Thanks.

---

### Post by bluenova on 2006-05-26
sudo /etc/init.d/gdm stop

Will stop gnome

I would suggest hit CRTL + ALT + F1

Then run:

sudo /etc/init.d/gdm stop

It should be happy then.

---

### Post by bluenova on 2006-05-26
Double post, please delete.

---

### Post by christhemonkey on 2006-05-26
Unless you are using a custom compiled kernel, 
The nvidia-glx package is what you want to use.

To my understanding, the nvidia-glx package is the same as the drivers from nvidias website.

But the nvidia-kernel-common package needs to be recompiled for each kernel, so they have in the repositories one for each of ubuntus kernels.

To stop the Xserver, you should use the command
```
sudo /etc/init.d/gdm stop
```

So to summarise, if you are usin a kernel from the repositories, use the nvidia-glx package.

---

### Post by mailforbiz on 2006-05-26
Thanks. 

I am using a repository kernel. I was able to setup the nvidia-glx package. Upon your advice, I've not tried drivers from the Nvidia site.

But still, the text is blurry and I'm having a headache even at 85hz mode. I'm concluding the video card that I recently put in the system is a piece of cr*p (it came very cheap, oh well). Any suggestions for a relatively cheap but good card for an AMD system (Asus7V) ?

Thanks.

---

### Post by christhemonkey on 2006-05-26
I have a nice Nvidia FX5500, cost me about 60 quid a year or so ago.
It does the job quite nicely.

Just have a google an see what looks nice.

---

### Post by Lord Illidan on 2006-05-26
What IS your Nvidia-card?

---

