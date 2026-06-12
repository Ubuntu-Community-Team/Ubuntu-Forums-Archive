---
title: "HELP PLS! X-Server Problems"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by stankyfranky on 2006-10-18
I installed Ubuntu and I got to the final step before log in...at least I think this is the final check before log in o.O I got an error message stating this
"Failed to start the X server(Graphical Interface). It is likely that it is not set up correctly....the x server is now disabled. Restart GDM"

I came from running windows XP and I have never had problems running my GPU Radeon x1600

p.s. dbl post o.O no one replyd

---

### Post by Iarwain ben-adar on 2006-10-18
Hi stankyfranky,

please try this from the console```
sudo dpkg-reconfigure xserver-xorg
```

This will reconfigure your X server,
and with a tad of luck, you can login in graphical mode..

If not,
try to post the exact output of the X server error.


Iarwain


Btw: welcome ;)

---

### Post by remle on 2006-10-18
I have also encountered that particular problem, which is caused by a misconfigured graphics driver. I can't remember the exact steps that i did to solve that though. 
You should start without the GUI(XServer), then edit the XServer configuration, and then reset the graphics driver section, so the Xserver will use standard graphics driver during boot up. Restart your Xserver, after you successfully boot with GUI, download and install the Ubuntu driver for your X1600.

Hope this helps. :)

---

### Post by stankyfranky on 2006-10-18
Hey I am really newb...how do I access the console >< only chance i see to access it is when if first trys to boot. 
The direct text that it pops up is as follows.
"Failed to start the x server(your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

the x server output is 
"x window system version 6.8.2
(ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
X Protocal version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux Ubuntu 2.6.12-9-386
#1 Mon Oct 10 13:14:36 BST 2005 i686
Moduel loader present 
OS Kernal:Linux 
Version 2.6.12-9-386 (build@rothera) (gcc version 3.4.5 20050809 (pre release) (ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
Marekers: (--) Probed. (**) From Config File, (==) default setting

---

### Post by stankyfranky on 2006-10-18
> **remle said:**
> 
You should **start without the GUI(XServer)**, then edit the XServer configuration, and then reset the graphics driver section, so the Xserver will use standard graphics driver during boot up. Restart your Xserver, after you successfully boot with GUI, download and install the Ubuntu driver for your X1600.

Hope this helps. :)



How do I do this?

---

### Post by confused57 on 2006-10-18
Here's a link that may help:

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by stankyfranky on 2006-10-18
> **Iarwain ben-adar said:**
> Hi stankyfranky,

please try this from the console```
sudo dpkg-reconfigure xserver-xorg
```

This will reconfigure your X server,
and with a tad of luck, you can login in graphical mode..

If not,
try to post the exact output of the X server error.


Iarwain


Btw: welcome ;)

I did all this and I followed the seps given at this site [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html). Now I get a error message that says this 

"(EE) No devices detected.
Fatal server error:
no screens found"

...any help would be greatly appreciated.

---

### Post by Iarwain ben-adar on 2006-10-19
Hi
try this url,
maybe it's of some help to you :D

[http://wiki.x.org/wiki/FAQErrorMessages#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed](http://wiki.x.org/wiki/FAQErrorMessages#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed)


Iarwain

---

