---
title: "Unable to update ubuntu 12.10 get dependency error on vaio laptop"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by dojha on 2013-04-29
unable to update ubuntu on my sony vaio. Last thing installed was amd drivers for 7650 gpu  the error i am getting is : The following packages have unmet dependencies:  fglrx: Depends: libqtcore4 (>= 4:4.5.3) but 4:4.8.3+dfsg-0ubuntu3.1 is installed        Depends: lib32gcc1 but it is not installed        Depends: libc6-i386 but it is not installed        Depends: linux-headers but it is a virtual package  and it says try to run :  Furthermore run the following command in a Terminal: apt-get install -f  Kindly tell me What i should do

---

### Post by Frogs Hair on 2013-04-29
Run the command in the terminal as suggested to start with. If there are any more errors copy and paste them in code tags using the # symbol on the reply box tool bar. ```
sudo [COLOR=#000000]apt-get install -f[/COLOR]
```

---

### Post by dojha on 2013-04-30
> **Frogs Hair said:**
> Run the command in the terminal as suggested to start with. If there are any more errors copy and paste them in code tags using the # symbol on the reply box tool bar. ```
sudo [COLOR=#000000]apt-get install -f[/COLOR]
```

I did this command and then ran sudo apt-get update, it updated my ubuntu, but now after i restarted my launchpad and tasbar are not showing up, so i am unable to to use it.
My terminal also runs only once i.e. when i press ctrl+alt+T it works, when i close it once it too dont start up.
I can only see wallpaper in the whole screen nothing else.
I tried pressing windows key to get back launchpad but was of no use.
( Now i am again using windows 7 to reply to this thread, please help me asap to get rid of windows 7 )

---

### Post by dojha on 2013-04-30
i reinstalled using the live disc, all software packages i installed last day spending 8 hours were gone, brightness control and other things still dont work. I think i am done with ubuntu, do you think 13.04 would be any different.
I think i will wait till ubuntu release something more stable and better. ubuntu 10.1 was the last best thing i used

---

### Post by Frogs Hair on 2013-04-30
You may want to post regarding your driver . I am not an ATI user and don't what driver would best suit your card. Consider Xubuntu because it is less demanding or install the gnome fallback session.
 
```
sudo apt-get-install gnome-session-fallback
```    
Select during login

---

### Post by dojha on 2013-05-01
My ATI graphic card is 7650HD Radeon series - 2GB, i5 with 4 gb ram, 500 gb hdd
This is exactly my laptop :
[http://www.sony.co.in/product/sve15116en/specs](http://www.sony.co.in/product/sve15116en/specs)

---

