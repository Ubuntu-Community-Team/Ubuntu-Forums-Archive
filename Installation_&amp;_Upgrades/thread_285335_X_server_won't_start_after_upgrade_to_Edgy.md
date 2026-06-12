---
title: "X server won't start after upgrade to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2006-10-26
My upgrade seems to have failed, X server won't start and when I view the error log, I see a string of several garabge characters follows by "UTF-8".

---

### Post by ner0tic on 2006-10-26
I ran into this problem and found it to be in relation to my video card being part of the radeon family (it was failing when it couldn't find the ati driver)

all i did was

```
sudo aptitude install xserver-xorg-driver-radeon
```

then i just restarted gdm and i was all set.

I don't know if this helped you at all, but it was my solution to the problem

---

### Post by rrwo on 2006-10-26
In my case it was installing the i810 driver, but that seems to have worked, thanks!

---

### Post by ilushkin on 2006-10-27
didnt help me and mobility radeon 1300 :(

---

### Post by buddachile on 2006-10-27
*sudo aptitude install xserver-xorg-driver-radeon*

i did this but found that i already had the latest version installed.

perhaps i need to change xorg.conf. unfortunately i don't have my old xorg.conf backed up.

how do i change xorg.conf to fix this problem?

also, where is the log where the X server errors are written?

---

### Post by drobvice on 2006-10-27
> **buddachile said:**
> *sudo aptitude install xserver-xorg-driver-radeon*

i did this but found that i already had the latest version installed.

perhaps i need to change xorg.conf. unfortunately i don't have my old xorg.conf backed up.

how do i change xorg.conf to fix this problem?

also, where is the log where the X server errors are written?

/var/log/Xorg.0.log (that's Xorg.zero.log not the letter O)

I tried to install xserver~ as well but already had it.  I also tried changing to "radeon" from "ati" in the /etc/X11/xorg.conf...no dice.  I can't boot!  Ack!  I have a radeon 9800 pro.

**edit** I changed my driver to "vesa" and was able to boot.  I installed fglrx and changed to that and all is well. :)

---

### Post by Beaucephus on 2006-10-27
Since Edgy uses a different kernel you may have to reinstall the driver.

---

### Post by uranus65 on 2006-10-27
Try using:

sudo apt-get install -reinstall xserver-xorg-driver-radeon

sudo shutdown -r now 

the computer will reboot

go to failsafe terminal and do:

sudo dpkg-reconfigure xserver-xorg

---

### Post by rich257 on 2006-10-27
After I upgraded X failed to start using the nvidia driver.  If I try to switch to either of vesa or nv drivers, using dkpg-reconfigure xserver-xorg then it still fails to load.  The X server is reporting that it's version is 7.1.0 (I think) while the nv module is for 7.0.0 and vesa is for 6.9.9, so it's refusing to load those modules.

If I do
```
sudo apt-get install xserver-xorg-driver-nv
```
then it says that (and vesa) are up to date.

So I'm stumped --- I appear to have old version of the vesa and nv drivers and yet they are up to date???

---

### Post by Beaucephus on 2006-10-28
Kernel upgrades (at least in the case of nvidia drivers) requires installation of the restricted kernel modules and RE-installation of the driver.  This is what is getting most people in trouble.  If you expect this its no problem.  Be careful when selecting new kernels in auto-updates.

---

### Post by cls1chuck on 2006-10-31
I am having the same problem w/the nvidia video drivers - so how does one resolve this?  Is there a wiki or other link for 'installing the restricted modules' an 'reinstallation of the driver'?  I have an AMD processor w/ a GEForce4 MX440 video card.

---

### Post by rich257 on 2006-11-02
There were a number of causes of my problem.  For a start I was using the K7 kernel, which no longer exists, so my computer was booting the 386 kernel for which I did not have the restricted modules (since I didn´t boot it).  I could not use the vesa or nv drivers because the xserver-xorg driver names had changed from xserver-xorg-driver-nv to xserver-xorg-video-nv, so they were not upgraded in the distribution update.

So I solved it by installing the restricted modules for the 386 kernel and then I could run X uses my previous xorg.conf file (unchanged from Dapper).

I have also removed the xserver-xorg-driver modules and put in the -video ones instead.

So basically the renaming of modules (K7 kernel becoming generic, and xserver-xorg drivers) meant that the distribution upgrade didn´t go well, which is a bit of a shame.

---

