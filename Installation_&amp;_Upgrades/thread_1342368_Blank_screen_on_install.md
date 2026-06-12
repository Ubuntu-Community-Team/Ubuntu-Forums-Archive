---
title: "Blank screen on install"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by tohecz on 2009-11-30
Hi,

After I insert the install CD and select any choice on its welcome screen (Install Ubuntu, Try Ubuntu...), I get only black screen. In like 1/10 cases I go thru further.

After one "happy" start I succeded to install the system, but it behaves exactly the same way: in like 9/10 cases I get blank screen after the "GRUB loading..." message. In 1/10 I get to load Ubuntu and it works just fine.

I tried with Ubuntu 9.10 and Kubuntu 9.10, both the same behaviour.

It's a new notebook, HP Compaq 615, Turion X2, ATI Radeon 3200.

Successful help thanked very much.

---

### Post by utnubuuser on 2009-12-01
Most likely a driver issue, if you search around, there's a lot of info on ATI driver configuration. - There's even a ATI-ubuntu wiki.

---

### Post by tohecz on 2009-12-01
> **utnubuuser said:**
> Most likely a driver issue, if you search around, there's a lot of info on ATI driver configuration. - There's even a ATI-ubuntu wiki.
I know, I have read some and didn't get any advice that would solve my problem. Nobody speaks about getting a blank screen on the install CD :neutral: I have to hurry as I can return the PC only this week ... Anyways thanks for caring and advice :)

---

### Post by u.b.u.n.t.u on 2009-12-01
tohecz do you get a blank screen with the live CD?

---

### Post by tohecz on 2009-12-01
> **u.b.u.n.t.u said:**
> tohecz do you get a blank screen with the live CD?
I get the blank screen whatever I try on the menu. I have the same issue with Fedora now too... I'm starting giving up.... :(

---

### Post by u.b.u.n.t.u on 2009-12-01
What operating system is currently on your computer?

Have any CDs worked, such as installing a game from CD?

---

### Post by tohecz on 2009-12-01
> **u.b.u.n.t.u said:**
> What operating system is currently on your computer?

Have any CDs worked, such as installing a game from CD?

Just now, I'm successfully installing Win7 there from a borrowed CD. Maybe I need to install the linux in console mode, and install the correct drivers that are on the web. But how do I force the CD to run the installation in console mode? And is it even possible?

Thankies a lot friends!

---

### Post by u.b.u.n.t.u on 2009-12-01
I am running Windows 7 from a HDD to which I have installed Ubuntu 9.10 via wubi.exe.

Installing Ubuntu 9.10 from Windows via wubi.exe is an ideal way to test Ubuntu 9.10. Second only to a live CD.

A wubi.exe initiated install has the benefit that such can easily be removed via the windows regular software uninstall procedure.

Once you have Windows 7 installed it would be good to know what your hardware specifications are in relation to:

1. GPU = ATI 3200 (the 512MB?)
2. CPU
3. RAM
4. HDD

---

### Post by jaylsi on 2009-12-01
If 9.10 live CD does not work, it is not a good idea to do the install, unless you like challenges. If you really want to use Ubuntu on this computer, try early versions of live CD, like 9.04, 8.10, 8.04.

---

### Post by tohecz on 2009-12-01
Thanks for all your replies. But I tried something totally different that solved the problem: I disabled the unnecessary devices: camera, card reader, express card slot, modem, bluetooth. And it works now ;)

---

### Post by u.b.u.n.t.u on 2009-12-01
Well done!

---

### Post by tohecz on 2009-12-01
DAMN!!! I found that the problem is caused by WiFi -- until it was installed, all had been fine. I installed b43 and it stopped working ... I'll search around for a solution ...

---

### Post by u.b.u.n.t.u on 2009-12-01
Maybe a conflict with the WiFi driver?

---

### Post by tohecz on 2009-12-01
But what should I do? I removed all the b43 drivers, I booted once with the card on, but with no WiFi connection, and after reboot, freezed again.

---

### Post by u.b.u.n.t.u on 2009-12-01
> **tohecz said:**
> But what should I do? I removed all the b43 drivers, I booted once with the card on, but with no WiFi connection, and after reboot, freezed again.

Are you referring to Ubuntu 9.10?

Perhaps consider troubleshooting the drivers for your WiFi. If you have determined that the b43 drivers do create a problem, then are there other drivers that you can test and use?

Alternatively, is there some setting related to your WiFi that is the cause?

---

### Post by jaylsi on 2009-12-01
Could it be the conflict between your wireless device and graphic device because they share a same interrupt channel? Just a wild guess. Don't know what I am talking about. :)

---

### Post by u.b.u.n.t.u on 2009-12-02
> **jaylsi said:**
> Could it be the conflict between your wireless device and graphic device because they share a same interrupt channel? Just a wild guess. Don't know what I am talking about. :)

It might be, but I would think the more usual suspect of drivers being the culprit.

The real question is, what is the current state of driver options for your WiFi.

---

### Post by tohecz on 2009-12-02
> **u.b.u.n.t.u said:**
> It might be, but I would think the more usual suspect of drivers being the culprit.

The real question is, what is the current state of driver options for your WiFi.
It is really tough to boot in linux with the WLAN device enabled. Without it, I can't check the drivers status, can I? And how do I do this when the device is enabled?

And how do I check the interruptions for conflicts?

---

### Post by u.b.u.n.t.u on 2009-12-02
> **tohecz said:**
> It is really tough to boot in linux with the WLAN device enabled. Without it, I can't check the drivers status, can I? And how do I do this when the device is enabled?

And how do I check the interruptions for conflicts?

I was thinking along the lines of conducting an online research into your WiFi hardware to discover that status of linux drivers.

I am unsure how to check for interruption conflicts. I would think that an operating system would assign hardware devices without too much worry about conflicts. Still, that is something that an online search may shed some light on also.

---

### Post by tohecz on 2009-12-02
I'm a noob you know, where do I find the bootlog of unsuccessful boot? Maybe I can get some information there...

---

### Post by force317 on 2009-12-02
Just discovered this discussion about the Compaq 615.

I have posted my own thread about the Compaq 615 and its problems myself a few weeks ago.

I am running Linux Mint 7 (based on Ubuntu 9.04) on this laptop since a week and everything works fine, the wireless included ! The only thing I had to do was install a recent alsa sound driver, everithing else worked !

I discovered what the problem is : it's the kernel version ! Every Linux distro running this recent kernel version 3X will get you a blank screen when installing. I got through the installation once with Linux Mint 8 (based on Ubuntu 9.10) last sunday, but once installed and rebooted things went all wrong again. I decided it wasn't worth the trouble.Since then I remain with Linux Mint 7 for the coming weeks/months.

I intend to wait until there is a better recent kernel version before installing a recent Linux distro like Ubuntu or Linux Mint.

I tried the simplyMEPIS 8.5 alpha distro today - no installation, just running as a Live CD - and to my surprise is started up perfectly! This alpha distro is running kernelversion 32 , so possibly the problem is already being taken care of. Of course an alpha release is not stable enough to run permanently on a laptop for daily use, but it seems there is hope for a perfectly running recent Linux distro for the Compaq 615.

Again, I advice you to read my thread. I hope it will give you some usefull information. I also posted another thread about the sound problem, for which there is a perfectly working solution for Ubuntu 9.04 / Linux Mint 7.

As you probably know you can find a good survey of many Linux distros on [www.distrowatch.com](www.distrowatch.com)

---

### Post by u.b.u.n.t.u on 2009-12-02
force317, excellent post.

What is the url to your discussion of this topic?

---

### Post by tohecz on 2009-12-03
I solved it by updating the graphic card driver ;) 

Thanks for your care :)

---

### Post by force317 on 2009-12-04
This is the link to my thread :

[http://ubuntuforums.org/showthread.php?t=1327853&highlight=compaq+615]("http://ubuntuforums.org/showthread.php?t=1327853&highlight=compaq+615")

---

### Post by force317 on 2009-12-04
Updating the graphics card driver : how do you do that on a linux os ?

Isn't that a bit risky for your laptop ? Could mess up your graphics card ?

---

