---
title: "HELP! ubuntu 9.04 accident"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by su-37 on 2009-04-09
I decided to try the beta of ubuntu 9.04 so i followed what they said on the website ie alt f2 and so on, however just after it had finished getting the packages the power to my batteryless laptop went out. Now it will try to boot and it gets to the stage just before the loading bar where the "somethings going on wheels" appears and it stays there.I have tried the two recovery options that it has and one will get past the loading bar but will still get stuck on the wheel.

Much aprreciated if anyone could help.

---

### Post by Pasdar on 2009-04-10
> **su-37 said:**
> I decided to try the beta of ubuntu 9.04 so i followed what they said on the website ie alt f2 and so on, however just after it had finished getting the packages the power to my batteryless laptop went out. Now it will try to boot and it gets to the stage just before the loading bar where the "somethings going on wheels" appears and it stays there.I have tried the two recovery options that it has and one will get past the loading bar but will still get stuck on the wheel.

Much aprreciated if anyone could help.

Just some advice for the future. If your Laptop is ever in the process of updating or installing, always connect it to the adapter. If your laptop ever shuts off while you're updating, you have most likely corrupted your whole operating system.

The same thing almost happened to me yesterday when I was installing vista on my laptop (I didn't know my wife had disconnected my laptop from the adapter). Thank God it had already finished, I saw the power at 10% and immediately connected it to the adapter.

As far as your problem goes. You can most likely still go into command line and fix it. However, personally I would just do a fresh install and not go through the trouble fixing it.

---

### Post by su-37 on 2009-04-11
Hey thanks for the advice i wont make the same mistake again. I tried putting a cd into the laptop and turning it back on but it doesnt want to boot from it. I go into the aetting at start up and select the cd but it still boots normally.

I have tried hitting esc when the grub shows and i have tried all of the ubuhtus there as well as their recovery modes. Still the wheel of death comes

---

### Post by su-37 on 2009-04-11
ps if you or anyone know what i need to do to do it by command line i would be grateful.

---

### Post by cariboo on 2009-04-11
Have you tried starting in recovery mode? At the menu select root prompt with networking, then at the prompt type:

```
apt-get -f install
```

then 

```
apt-get update && apt-get full-upgrade
```

You won't see any "Spinning wheels"

Jim

---

### Post by r0b` on 2009-04-11
I agree, do a fresh install, and if there is anything that you want to backup, try backing up to an extra hard drive, or a flash memory drive via Live CD, to access your HDD, before you do the fresh install.
I couldnt really tell you how to fix it other than that, because you have more then likely yes, ****** up your whole OS.

---

### Post by nanog on 2009-04-11
i have not done a fresh install for years.

the recovery boot option mentioned above is your best bet but if that does not work you can almost always fix an ubuntu install problem by doing this:

[http://ubuntuforums.org/showpost.php?p=6629812&postcount=12](http://ubuntuforums.org/showpost.php?p=6629812&postcount=12)

---

### Post by novafluxx on 2009-04-11
Unless you NEED to be running your laptop on battery power, then don't.

---

### Post by su-37 on 2009-04-12
> **cariboo907 said:**
> Have you tried starting in recovery mode? At the menu select root prompt with networking, then at the prompt type:

```
apt-get -f install
```

then 

```
apt-get update && apt-get full-upgrade
```

You won't see any "Spinning wheels"

Jim
i booted up. Hit esc when i saw the grub and then went down and selected: "ubuntu jaunty (development branch) kernel 2.6 27-11-generic (recover" it then booted to the menu. I scrolled down  to: : ```
 netroot Drop to root shell prompt with networking 
``` That is the right one isnt it?

I do what you say and then it comes up with (after downloading and so on) ```
 E: invalid operation full-upgrade 
``` It looked like it was working till it got to there.

---

### Post by tom66 on 2009-04-12
The OP said batteryless laptop -- I think this means that power went out and he had it on AC adapter. Correct me if I'm wrong though...

---

### Post by n3had on 2009-04-12
> **su-37 said:**
> i booted up. Hit esc when i saw the grub and then went down and selected: "ubuntu jaunty (development branch) kernel 2.6 27-11-generic (recover" it then booted to the menu. I scrolled down  to: : ```
 netroot Drop to root shell prompt with networking 
``` That is the right one isnt it?

I do what you say and then it comes up with (after downloading and so on) ```
 E: invalid operation full-upgrade 
``` It looked like it was working till it got to there.

what about this ```
apt-get dist-upgrade
```

---

### Post by kansasnoob on 2009-04-12
Try:

```
sudo dpkg-reconfigure -phigh -a
```

I've had it take as long as 90 minutes to run, but if all the packages are available that might get you working again.

---

### Post by caryb on 2009-04-12
If you are having problems getting to a terminal try hitting escape on boot up & select recovery mode when the menu comes up select repair broken packages, I would have the ubuntu cd in the after bootup as it will try to pull files from the cd.


Cary

---

### Post by su-37 on 2009-04-13
> **nanog said:**
> i have not done a fresh install for years.

the recovery boot option mentioned above is your best bet but if that does not work you can almost always fix an ubuntu install problem by doing this:

[http://ubuntuforums.org/showpost.php?p=6629812&postcount=12](http://ubuntuforums.org/showpost.php?p=6629812&postcount=12)

I did this and it fixed it, i think. Heck even my wireless is now running. Thanks a lot guys, youve all made it easier. Burn vista burn.

---

