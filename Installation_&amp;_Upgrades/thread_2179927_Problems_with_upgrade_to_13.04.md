---
title: "Problems with upgrade to 13.04"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by dmtparker on 2013-10-10
I originally posted this to Ubuntu Studio forum, but realized that it might be more appropriate here. Sorry for the double post.
I have been using Ubuntu Studio for a year or so (12.04). For reasons  I'm still questioning, I decided to upgrade to 13.04 (which, of course,  required first upgrading to 12.10). All seemed to go well until I  rebooted into 13.04. 

[LIST=1]
[*]The first thing that happened is that I  have a cute notice on the bottom R of screen that says "AMD Unsupported  hardware". Clicking on it does nothing and I cannot find our what  hardware is unsupported. (My laptop is a Dell Inspiron with AMD quad  core cpu and Radeon graphics (the Catalyst Control center still works so  that is not it). When I try the "Additional drivers" app, I get "Failed  to execute child process "/usr/bin/jockey-gtk" (No such file or  directory)".
[*]Also BIGGER PROBLEM: when I boot into the  low latency kernal I have NO WiFi! I tried using the generic kernal and,  thankfully, my WiFi is back, but I still have the "Unsupported  hardware" issue. I also would like to know how to get my WiFi back in  the low latency kernal so I can use that.
[*]I have no sound in Totem. I DO have sound in Pythos so I'm not sure what the issue is.
[/LIST]

I would have thought that all the bugs of 13.04 would have been worked  out by now, but I guess not. Hope someome can help me with all this.
Thanks
Well, here is a bit of new info. If I use kernal 3.8.0-31 (the default) -  low latency, I have the problems above, but if I use 3.8.0-31 generic  WiFi is OK. Also if I use 5.0-41 - low latency (the next choice in grub)  WiFi works but I still don't have sound in Totem, GNOME Mplayer, but I  do have sound in VLC and xine. Does that help?

---

### Post by heir4c on 2013-10-10
"AMD unsupported hardware" concerns your graphic card. Something with the driver. Look for "Software & Updates" (if there is in UbuntuStudio, I never installed) and than on the last Tab you find the open-source and non-free drivers.

But why you want to upgrade to 13.04. The releases between the LTS versions are not long supported. 12.04 is good for 5 years and if you want you can upgrade next year to 14.04 LTS. Certainly when you use UbuntuStudio and want a stable system.

---

### Post by dmtparker on 2013-10-10
OK, that solved the "Unsupported hardware"issue (turns out there is now a open source driver for my video card).
Next the WiFi: It says "using proprietary Broadcom driver from bcmwl-kenral-sources," but gives no alternative. To re-iterate, the WiFi is working in kernal 3.8.0-31 generic and 3.5.0-41 low latency, but NOT in 3.8.0-31 low latency (which is default). 
Any ideas?

---

### Post by mörgæs on 2013-10-10
> **dmtparker said:**
> I originally posted this to Ubuntu Studio forum, but realized that it might be more appropriate here. Sorry for the double post.


Next time please report the post so it can be moved in stead of posting a new one. 
I have removed the other.

---

