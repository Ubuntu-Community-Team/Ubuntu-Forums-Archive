---
title: "Now to remove nouveau and install Nvidia."
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-02-24
Hi,

I need to use 3D for special effects and since their is no near plan to introduce 3D in nouveau. Can you please help me removing nouveau and install Nvidia.

Thanks.

---

### Post by dino99 on 2010-02-24
ok, let me draw actual and future situation:
- nv is the past and is no more developped, so "nouveau" replace nv and it's far better.
- both kernel and plymouth work with nouveau and it's built-in, so removing it is not the solution.
- you don't want to be forced to use nouveau, ok i understand, but you was not be forced too using nv right.
- you still have extern solutions like before if you want propriatary drivers

So, add to sources.list: ppa:albertomilone/proprietary-video-improvements,
update and install these 195.36 packages you got, (except *.dev) and nvidia-common, nvidia-current, xserver-xorg-video-nouveau.

   After these packages installed, you need to check and activate the driver you want and need, so go to : system --> admin --> hardware driver and you should have your desired driver  :P

---

### Post by donniezazen on 2010-02-24
> **dino99 said:**
> ok, let me draw actual and future situation:
- nv is the past and is no more developped, so "nouveau" replace nv and it's far better.
- both kernel and plymouth work with nouveau and it's built-in, so removing it is not the solution.
- you don't want to be forced to use nouveau, ok i understand, but you was not be forced too using nv right.
- you still have extern solutions like before if you want propriatary drivers

So, add to sources.list: ppa:albertomilone/proprietary-video-improvements,
update and install these 195.36 packages you got, (except *.dev) and nvidia-common, nvidia-current, xserver-xorg-video-nouveau.

   After these packages installed, you need to check and activate the driver you want and need, so go to : system --> admin --> hardware driver and you should have your desired driver  :P

Thanks.

---

### Post by mc4man on 2010-02-24
> So, add to sources.list: ppa:albertomilone/proprietary-video-improvements,
update and install these 195.36 packages you got

While obviously it would work out there is no reason to add that (or any) ppa anymore.

Just open system - admin - hardware drivers and choose  the "version current" one, ect.

Though can also be done the slightly older way by 
```
sudo apt-get install nvidia-current
```
```
sudo nvidia-xconfig 
```
and rebooting

---

### Post by donniezazen on 2010-02-24
> **mc4man said:**
> While obviously it would work out there is no reason to add that (or any) ppa anymore.

Just open system - admin - hardware drivers and choose  the "version current" one, ect.

Though can also be done the slightly older way by 
```
sudo apt-get install nvidia-current
```
```
sudo nvidia-xconfig 
```
and rebooting

Thanks, i guess the 195.36 is not available in official Ubuntu repo.

---

### Post by tseliot on 2010-02-24
> **soham_1207 said:**
> Thanks, i guess the 195.36 is not available in official Ubuntu repo.

Yes, it is.

---

### Post by donniezazen on 2010-02-24
> **tseliot said:**
> Yes, it is.

Thats good then we don't need the ppa.

---

### Post by gnuckx on 2010-03-08
Do not install 195.36.08,  195.36.03,  or 196.75 NVIDIA drivers. NVIDIA has announced a bug that might burn you card. Meanwhile Canonical advises to use Nouveau drivers for Lucid and 190.53 for previous distros.

[http://www.nvnews.net/vbulletin/announcement.php?a=39](http://www.nvnews.net/vbulletin/announcement.php?a=39)

---

### Post by sdowney717 on 2010-03-08
I am running 195.30 beta in karmic right now. 
I got this right off the nvidia site and it installs very simply compared to what I recall having to go thru in the past.
It works well, but when the kernel changes, I have to reinstall it every time.

---

