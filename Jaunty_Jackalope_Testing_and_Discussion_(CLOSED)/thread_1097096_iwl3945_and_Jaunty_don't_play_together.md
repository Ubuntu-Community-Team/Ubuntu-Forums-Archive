---
title: "iwl3945 and Jaunty don't play together"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Doronkatz on 2009-03-15
Hi guys
Not sure if I should post this under this thread or new one. Basically I am new to ubuntu I have a thinkpad x60 with jaunty installed. I have been using interprid before and my wifi worked fine. Ad soon as I upgraded to jaunty I can't get my wifi to work. I have iwl3945 intel card. 

Now under normal boot I can't see wifi existing under network icon. When I boot under different module I get wifi signal and it lists all the hotspots but when I select one, whether an open access or wpa it tries to connect but nothig happens after a few seconds. Help guys I have been googling all over. Thx

---

### Post by excogitation on 2009-03-15
> **klange said:**
> 
The Intel wireless drivers (for the 3945, and others) are extremely buggy and are prone to firmware crashes (microcode errors) when they are not constantly being used. I'm surprised that this is cropping up again. In Intrepid, it seemed a slight workaround was in place that automatically reconnected the network after a crash, but from my experience a week ago it appears to have been removed.

you know about the search function?
[IMG]http://lh6.ggpht.com/__VPr48VILJI/Sb1vf3NxEWI/AAAAAAAAAGw/m91gDVvJCOA/s288/Screenshot-2.jpg[/IMG]

---

### Post by Doronkatz on 2009-03-15
yes I understand and read that post. My problem is i cant get it to recognise there is a wireless network, and b, going backwards in modules, it connects and disconnects. I never actually get a connection. I get some people do get a connection even though its buggy and kicks off.

Secondly, any ides on when this would be rectified?

---

### Post by Zorael on 2009-03-15
When I got microcode errors I went to [http://linuxwireless.org](http://linuxwireless.org) and compiled new drivers. Some builds took care of it, some didn't, so after some trial and error I found one that worked. This was for Gutsy or Hardy though, since then I haven't had any issues. Again, this is for microcode spam.

Out of the box, mine can't find any networks *at all*. But if I pass an option to the iwl3945 module - *disable_hw_scan* - it works great.

```
$ echo iwl3945 disable_hw_scan=1 | sudo tee /etc/modprobe.d/options
$ sudo rmmod iwl3945
$ sudo modprobe iwl3945
```

---

### Post by Doronkatz on 2009-03-16
Thanks  mate but on the last line I got an error:

$... sudo modprobe iwl3945
WARNING: /etc/modprobe.d/options line 1: ignoring bad line starting with 'iwl3945'

And still dont have any wireless visible.

Thanks

---

### Post by shoofy on 2009-03-16
I'm having the same problem. Just upgraded to Jaunty and Network Manager applet says "wireless is disabed," but the checkbox to enable wireless is disabled.

Edit: Never mind. I pressed the keyboard wireless on/off button and it came back. I'm not sure whether it was my fault or if Jaunty turned it off itself, but anyway it's working now.

---

### Post by Doronkatz on 2009-03-18
> **Zorael said:**
> When I got microcode errors I went to [http://linuxwireless.org](http://linuxwireless.org) and compiled new drivers. Some builds took care of it, some didn't, so after some trial and error I found one that worked. This was for Gutsy or Hardy though, since then I haven't had any issues. Again, this is for microcode spam.

Out of the box, mine can't find any networks *at all*. But if I pass an option to the iwl3945 module - *disable_hw_scan* - it works great.

```
$ echo iwl3945 disable_hw_scan=1 | sudo tee /etc/modprobe.d/options
$ sudo rmmod iwl3945
$ sudo modprobe iwl3945
```



This does work, ive tested it out. Essentially my modprobe.d file was stuffed up, so this fixed it, and rmmod and modprobe restart my wireless. 

Now the only problem left is the fact that like what others have reported, i only get a little bit of connection before it disconnects/drops out. 

grr

---

### Post by DanaG on 2009-03-18
I see three problems here: 
One, you're trampling on (not appending to) the default 'options' file.
Two, it should be "options iwl3945 disable_hw_scan=1"
Three, all files in modprobe.d are changing to have to have names ending in .conf .

---

