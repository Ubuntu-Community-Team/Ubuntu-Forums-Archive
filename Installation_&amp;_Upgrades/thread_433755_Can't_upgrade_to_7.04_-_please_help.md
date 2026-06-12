---
title: "Can't upgrade to 7.04 - please help"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by douglerner on 2007-05-05
I am using the upgrade tool in Ubuntu. All the packages download (like 143 packages). But when installation starts on any of the packages there are always errors, segmentation faults, blah, blah, blah...

Any suggestions on how to proceed?

Thanks,

doug

---

### Post by Big Ed on 2007-05-06
From a console, try 'sudo apt-get dist-upgrade'.  You may have to do it more that once.

HTH,
Ed

---

### Post by douglerner on 2007-05-06
Thank you very much, Ed. That seemed to work!

After restart, I couldn't login though because I kept getting a "Couldn't load theme Human" error about a missing .png file.

But just "trying everything" I switched my "session" to "Gnome" and was able to login. 

I *think* everything is ok.

Now if I can just figure out how to get full 1680 x 1050 resolution... :)

doug

---

### Post by Big Ed on 2007-05-06
If you have an Nvidia card and you have already enabled the Nvidia restricted drivers, then you should be able to run "sudo nvidia-settings" to get a nice gui tool.

If you have an ATI card, try "udo aticonfig --initial".

Otherwise try "sudo dpkg-reconfigure -phigh xserver-xorg", use the space bar to select which resolutions to be available, restart X.

Outside of that, I don't know.  Haven't had enough problems with screen resolution to know much about fixing it.

HTH,
Ed

---

### Post by douglerner on 2007-05-06
This is a MacBook Pro and it says it is using an ATI RadeonX1600. I'll try that and see what happens. Thanks.

doug

---

### Post by douglerner on 2007-05-06
Well... things are not looking good. aticonfig didn't exist, so I tried the 3rd suggestion dpkg-reconfigure. There I chose ATI and the 1680x1050 resolution. Then I restarted and am getting the  X11 errors shown in the screenshot and can't even login anymore.

[IMG]http://lerner.net/doug/Ubuntu/Ubuntu1.jpg[/IMG]


[IMG]http://lerner.net/doug/Ubuntu/Ubuntu2.jpg[/IMG]

doug

---

### Post by Big Ed on 2007-05-06
> **douglerner said:**
> This is a MacBook Pro and it says it is using an ATI RadeonX1600. I'll try that and see what happens. Thanks.

doug

Ahh, I was assuming a PC of some kind.  I don't know how those commands will work on a MacBook.  You might try posting your question in one of the Apple forums here, if you don't have any luck or if no one else responds.

Ed

---

