---
title: "Xorg.conf, nVidia drivers and Asus W7S laptop..."
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by SandersOnSite on 2008-02-11
I have an Asus W7S laptop.
I am having alot of trouble getting all the hardware working at once....

I installed Gusty, the resolution looked fine, however the Open GL drivers would not work.

I managed to install the latest nVidia drivers, and everything was working until I rebooted. The graphics drivers worked, and it added a new entry into my grub menu - however when I select the new entry the sound and wireless dont work.

So I go back to the original grub entry - wireless and sound work again - but no graphics.

I try and enable the proprietry driver, and it "says" its enabled and installed, however if I do a nvidia-settings --config enable
The nVidia Settings gui pops up and tells me I  "Do not appear to be using the nVidia X driver"

So I did..

sudo dpkg-reconfigure -phigh xserver-xorg

which ran me through a little setup routine, answered the questions as best I could....

But still no joy.

when I boot into the grub entry that has will let me have the nVidia drivers, I get no sound and no wireless.

When I boot into the other - it wont let me use the nVidia driver.

I went to check out my xorg.conf....there are 8 different ones in there with the format xorg.conf.1 etc etc through to 8....+ a bunch that say

xorg.conf.20080211143123 

Some insight into this would be great. I "think" that when the nVidia driver compiled some kernel modules for the system and created a new config file for booting - it left out the sound and wireless bits.....

But (as is probably quite obvious by my wonderful description) I am fairly new to Linux so I am not sure how it all hangs together. 

In my defense I am a computer (windows + mac) tech so I have "some" idea of what is happening - I just seem to be missing some crucial bit of information.

Any suggestions or help would be appreciated.

---

### Post by Partyboi2 on 2008-02-11
> I went to check out my xorg.conf....there are 8 different ones in there with the format xorg.conf.1 etc etc through to 8....+ a bunch that say

xorg.conf.20080211143123 When you reconfigure the xserver it backs up your current xorg.conf and displays it with all those numbers which  are the date and time. eg 20080211143123 means 2008 02 11 14:31.23

Check your log file /var/log/Xorg.0.log for any errors the line would have a (EE) at the start indicating there is a error.
```
gksudo gedit  /var/log/Xorg.0.log
```

---

### Post by SandersOnSite on 2008-02-11
Sorry for the totally nube question here but just to make sure I am getting this...

It makes a backup, alters the original? (so the one its actually using is still called xorg.conf with no number or anything)?

I think I have found where I went wrong, and have formatted my disc and reinstalled so I wont be haunted by these mistakes later - but since I installed this to increase my linux knowledge in the first place......knowing how it works is kinda more important to me than it actually working.

=)

Thx in advance.
J

---

### Post by Partyboi2 on 2008-02-11
>  It makes a backup, alters the original? (so the one its actually using is still called xorg.conf with no number or anything)?
correct

---

### Post by SandersOnSite on 2008-02-11
again - thanks heaps.

---

