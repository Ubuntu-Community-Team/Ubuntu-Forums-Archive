---
title: "Install Ubuntu Via Removable Storage"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Dr Zolygon on 2007-10-26
Hi,

I am wanting to know if it is possible to install Ubuntu 7.10 off of a removable harddrive.

I've looked around the net and just about everything I find on the subject is about installing ubuntu on the removable disk, rather then simply installing Ubuntu on an internal harddrive via removable storage. Basically I want it to be the same as popping in a live cd, clicking the install icon, and installing Ubuntu on my internal harddrive with the use of my removable hdd. 

If anyone has any idea how to this, it would be greatly appreciated if you helped.
Thank you.

---

### Post by Dr Zolygon on 2007-10-26
Bump.

---

### Post by It_Was_Luck on 2007-10-26
Okay well its possible but understand this:

When you install Ubuntu from the installer its also installing Grub to that removable storage, and its also going to your computers MBR (master boot reconrd) and telling it to (on start-up) look for grub in that removable storage. Now if its not connected you computer will come up with Grub Error 21 (I believe it is) This is because your computers MBR is looking for grub in a place that "doesn't exist" or in this case, not connected.

The way to solve this is to burn yourself a grub disc and from the disc install grub to your computer and uninstall it from your removable storage. Then when your computer boots us it will ask you to boot to windows or ubuntu, now if your removable storage is NOT connected if you press Ubuntu it will come up with an error code, this is because it can't find it (because its not connected, duh)

But if you click Windows XP it will go to that partition and boot it. Then if you plug in your portable removable storage drive then restart and select ubuntu, Grub will find ubuntu on your portable HD and boot-up.

hth

---

### Post by Dr Zolygon on 2007-10-26
Thanks for the response.

I'm thinking im just going to try burning the iso onto a disc. However, I've alread waster 2 discs in the process. The first time I tried burning the CD Iso of Ubuntu 7.10 onto a dvd with Infra Recorder and something weird happened where it said it finished far before it actually did. The second time I tried a blank CD and I set the write speed to 2x. However, when it was burning it kept speeding up till it was writing at 48x. That disc was corrupt when I tried booting from it.

I only have DVDs left so I want to know if I am able to use DVDs for the cd version of Ubuntu 7.10.

Thanks

---

### Post by It_Was_Luck on 2007-10-26
I believe so...

I have Ubuntu 7.04 burned to a DVD and it appears to have worked I don't see why it would be any different for 7.10

---

### Post by Dr Zolygon on 2007-10-26
Ya it works. I just burned 7.10 to a dvd and it is installing right now. Everything seems alright so far.

I used ImgBurn instead of Infra Record because for some reason I could not get Infra Recorder to stay at 2x write speed. But ImgBurn stayed at a consistant 1.9x so everything is good.

---

