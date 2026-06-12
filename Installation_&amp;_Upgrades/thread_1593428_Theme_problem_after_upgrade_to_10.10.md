---
title: "Theme problem after upgrade to 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by gap on 2010-10-11
Upgraded from 10.04 to 10.10 using standard Update Manager procedure. Now themes don&#8217;t work. When I change the theme, the window decorations change accordingly, but the contents of the windows (controls, panels) are in the raw X look (I don&#8217;t know how else to put it) and do not change regardless of theme selection. I&#8217;ve tried customizing the theme and selecting something different on the "Controls" tab, but it doesn&#8217;t work.

X is working properly with Nvidia driver, Compiz is working properly as well. Killing Compiz didn&#8217;t help with the theme problem.

I used 64-bit Lucid, so I guess it upgraded to 64-bit Maverick.

I would appreciate any help.

---

### Post by zang3tsu on 2010-10-11
I also have the same problem ([https://bugs.launchpad.net/ubuntu/+source/ubuntu-artwork/+bug/649809]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-artwork/+bug/649809")).

For now, the only solution I can think of is to use nouveau. :(

---

### Post by gap on 2010-10-11
That sucks. Thanks for the reply and the workaround.

---

### Post by dino99 on 2010-10-11
look at errors logged , that might help

---

### Post by gap on 2010-10-11
Where, dino?

---

### Post by zang3tsu on 2010-10-11
I checked the logs (dmesg, syslog, messages) but I can't seem to find anything that is related to the theme. From what it looks, the proprietary nvidia driver does load properly, but the theme just doesn't apply correctly.

---

### Post by zang3tsu on 2010-10-11
Another double post.

---

### Post by zang3tsu on 2010-10-11
And another double post. :(

---

### Post by zang3tsu on 2010-10-11
Sorry, double post.

---

### Post by zang3tsu on 2010-10-11
I found a temporary fix: [http://ubuntuforums.org/showpost.php?p=9932580&postcount=20]("http://ubuntuforums.org/showpost.php?p=9932580&postcount=20")

---

### Post by gap on 2010-10-11
Nice find, but it&#8217;s a weak consolation for me. I can&#8217;t get my theme right with this fix either.

Did you upgrade to 10.10 or was it a clean install? This is so bad that I consider reinstalling from scratch. But it&#8217;s not easy and I have no assurance that it would solve the problem.

---

### Post by zang3tsu on 2010-10-12
I did an upgrade. It really isn't an overall fix. And I don't like to do a clean install. I guess I just have to wait for a proper fix to come.

---

### Post by kd8cgo on 2010-10-14
I just did a clean install of 10.10 amd64 desktop on an Asus G73JW laptop computer - same theme problem here - window decorations are working but the panels and in-window controls all remain at gnome default looks.  This behavior started at the very first boot, after installing the nVidia driver the behavior remained unchanged.

---

### Post by gap on 2010-10-14
If you have a Launchpad account, please go to the ticket for this bug and click on the "Does this bug affect you?" link. With a larger number of affected users, it's more likely that we will get help. Here's the ticket page:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-artwork/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/ubuntu-artwork/+bug/649809)

On that page, you can also find workarounds from other users and keep up with the progress, if there will be any.

---

### Post by mercury80 on 2011-01-15
> **zang3tsu said:**
> For now, the only solution I can think of is to use nouveau. :(

Find that hard to believe since i have the same problem on a computer without nVidia, [ASUS U31F]("http://www.asus.com/product.aspx?P_ID=OV45sT3DY56akobY").

---

### Post by mercury80 on 2011-01-15
> **zang3tsu said:**
> For now, the only solution I can think of is to use nouveau. :(

Find that hard to believe since i have the same problem on a computer without nVidia, [ASUS U31F]("http://www.asus.com/product.aspx?P_ID=OV45sT3DY56akobY").

---

### Post by sjw1010 on 2011-01-20
I also have this problem.

#70 in the bug report fixed link fixed it for me

until reboot

#68 fixed it 

must be something with the SSD

---

### Post by rowzy1984 on 2011-12-12
Hi everyone,

I wrote a little script to open gnome-appearance-properties, which changes the theme to your preferred one, then kill nautilus, and finally if errors didn't kill gnome-appearance-properties, the final step will. 

I have an i7 with and SSD so, adjust the sleep times to suit your comp. This problem plagued me after installing the nvidia driver shortly after a clean install. 

I named the file /home/themesfix.sh and opened system >> preferences >> startup applications and added the command /home/themesfix.sh to that list.

[HTML]
#!/bin/sh

# Scripting to delay on start and then run
sleep 2
gnome-appearance-properties --g-fatal-warnings
sleep 2
killall nautilus
#sleep 2
#killall -w gnome-appearance-properties

# done
[/HTML]

On my setup, the gnome-appearance-properties opens with 3 errors, so the --g-fatal-warnings cause it to close, but it still does its thing.

Anyways, I hope this helps someone out there with this frustrating problem.

---

