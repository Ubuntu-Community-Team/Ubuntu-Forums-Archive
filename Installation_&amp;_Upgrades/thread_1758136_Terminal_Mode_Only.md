---
title: "Terminal Mode Only"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by macmike on 2011-05-14
I have been able to successfully run my Web Server using 10.04 version. I then upgraded to the next version 10.10 (?) ok. Then yesterday I tried to upgrade to the latest version 11.04 I believe it is. Took all night to go through all of it. When it restarted the computer there were problems. I had to have it rebuild the packages. Now it is running in terminal mode only. The website seems to be working ok - [www.mikealrhughes.com](www.mikealrhughes.com). I would like to get the graphic desktop working again. What commands do I need to issue from the command line to get the graphic user interface back? Any help appreciated. You can also write me at my email - mail (at) mikealrhughes (dot) com

macmike

---

### Post by dabl on 2011-05-14
At the command line, log in, then type these commands:

```
sudo service gdm stop
```

```
sudo service gdm start
```


What error message(s) do you see?

---

### Post by MAFoElffen on 2011-05-14
> **dabl said:**
> At the command line, log in, then type these commands:

```
sudo service gdm stop
``````
sudo service gdm start
```What error message(s) do you see?

1.  What version of server are you running 11.04 32bit or 64bit?
2.  What desktop do you have installed?
3. What is you hardware? (PC, CPU, Video card, monitor)
4.  What does is do now / at what point does the graphics session lock?

It may be that there was a problem in the install of the desktop package... But I suspect it was rather a configuration problem with the graphics.  

Please post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor

```Id not installed, please install
```

sudo apt-get install hwinfo

```

---

### Post by macmike on 2011-05-14
> **MAFoElffen said:**
> 1.  What version of server are you running 11.04 32bit or 64bit?
2.  What desktop do you have installed?
3. What is you hardware? (PC, CPU, Video card, monitor)
4.  What does is do now / at what point does the graphics session lock?

It may be that there was a problem in the install of the desktop package... But I suspect it was rather a configuration problem with the graphics.  

Please post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor

```Id not installed, please install
```

sudo apt-get install hwinfo

```

When I try to do an install of hwinfo I get Invalid operation hwinfo
When I try and do a hwinfo --framebuffer I gety sudo: hwinfo: command not found
Graphic doesn't lock up just comes up in Terminal mode.
Video is VIDIA Geforce 2 MX200
2 GB Ram
Running 11.04 Server 32 bit version.

Hardware is PC with Asus Motherboard P4B533

---

### Post by macmike on 2011-05-14
adf

---

