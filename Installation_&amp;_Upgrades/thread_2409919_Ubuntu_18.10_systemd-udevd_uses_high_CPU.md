---
title: "Ubuntu 18.10 systemd-udevd uses high CPU"
date: 2019-01-08
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2019-01-08
I AM POSTING THIS SO OTHERS HAVING THIS HIGH CPU PROBLEM CAN SAVE SOME TIME! 

When I  boot up every day without exception, my machine starts up with one of  the CPU cores running at 100%. I see lots of posts going back over a  year or more blaming touchpads or nvidia or WiFi. Some even say they  can't use their thumb drive if it isn't plugged in when they boot. The problem also mimics a defective thumb drive where you plug it in and Ubuntu doesn't see it. Losing one cores makes my machine slower but not too noticeably so. I do see much longer boot times and sometimes my system will "appear to hang" entirely during boot (it will power down normally by briefly touching the power off button when it "looks like" it is stuck). I assume a single core or dual core machine will be drastically slowed down or even unusable. When I search, I find other non-ubuntu OS's complaining about similar problems. 

I have 18.10 running on my Dell studio XPS with an AMD® Phenom(tm) ii  x4 945 processor × 4 and AMD® Juniper graphics. It's a quad-core 64 bit  machine. I have wireless mouse and keyboard for Logitech. I  have a pretty vanilla set-up. I DO NOT have a touchpad or nvidia or  WiFi! 

The problem can be managed by stopping and starting  systemd-udevd. I used the following commands in sequence in the terminal  which corrects the problem until I boot again.  

sudo systemctl stop systemd-udevd systemd-udevd-kernel.socket systemd-udevd-control.socket

sudo systemctl start systemd-udevd systemd-udevd-kernel.socket systemd-udevd-control.socket

Also the problem will "sometimes" re-appear by plugging in a thumb drive! Then I have to use the stop and start commands again. This IMHO is a serious kernel problem which has been around for over a year and is described in [https://bugzilla.kernel.org/show_bug.cgi?id=199035](https://bugzilla.kernel.org/show_bug.cgi?id=199035). 

This problem can manifest its presence in a number of ways depending on your hardware configuration. Hopefully this very annoying problem will get fixed very soon! 

I AM NOT SURE WHERE THIS SHOULD BE POSTED. PLEASE FEEL FREE TO MOVE TO AN APPROPRIATE PLACE!

---

