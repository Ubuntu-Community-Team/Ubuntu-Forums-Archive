---
title: "using the server without gui"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Lakeside5 on 2010-08-20
Ok, here goes. I just installed (installed? can only seem to access it from the flash drive, but that's another issue lol) 10.04 and am at the command line after typing in username/password.  Now what? I am going to make a good attempt at using my server without the gui, so of course I haven't got a clue what to do next. I would like to have the gui but I've read a lot about security risks and I actually WAS hacked before with the last version- 9, which destroyed my server and why I started all over with 10.04 so... please point me to all the helpful threads/tutorials of what to do next. I just want to be able to start/stop the server, and install a joomla website into it/develop it. I've done it before with a gui, now I'll try without one  Thanks.

---

### Post by earthpigg on 2010-08-20
hi,

[webmin]("http://www.webmin.com/") is very popular, but i've never used it.

[ssh and sshfs]("http://wiki.archlinux.org/index.php/SSH") alone have been enough to fulfill my needs. if you have any problems transliterating the directions for arch into ubuntu-ese, please post back.

---

### Post by Lakeside5 on 2010-08-21
Thanks very much earthpigg, I will try it.
*edit  So I've been trying, and was following the advice to install webmin, and ran into trouble on the part to 'wget' the package,  I trying  'wget [http://garr.dl.sourceforge.net/sourceforge/webadmin_141_all.deb](http://garr.dl.sourceforge.net/sourceforge/webadmin_141_all.deb) and it said 'failure in name resolution, unable to resolve host address 'garr.dl.sourceforge.net', it did the same when I tried ......prdownloads.sourceforge.net  What am I doing wrong NOW? lol thanks.

---

### Post by earthpigg on 2010-08-21
sounds like a typo following wget.

---

### Post by decent2110 on 2010-08-21
i have been tried this but cant working !!!!
 
 
can u tell me is there any 2nd choice??
 
plz help
 
 
 
[FONT=Arial][SIZE=2]**[]("http://www.relaxhouse.com.au")**[/SIZE][/FONT][B][FONT=Arial][SIZE=2][URL="http://www.relaxhouse.com.au"]
[/URL][/SIZE][/FONT][/B]

---

### Post by Lakeside5 on 2010-08-21
I've tried this a few times, checking and rechecking the address, tried more than one address for the download, and keep getting the same error message 'temporary failure in name resolution'. I have no idea what that means.  All I can think is that the computer isn't connecting to the internet? I am posting in this forum with my laptop, and the install is on another computer. I have a router which this laptop connects to wirelessly, and the computer is connected to the router with a cable to avoid any 'wireless issues' for the install.  Also, it seems any address I try gives me that error, for instance  wget [https://help.ubuntu.com](https://help.ubuntu.com)

---

### Post by wojox on 2010-08-21
Did you try

```
webmin_1.510-2_all.deb
```

---

### Post by Lakeside5 on 2010-08-21
One of the ones I tried, thanks :) My problem seems to be that I can't access websites even with 'wget'. So maybe it is a connectivity problem? Even though this laptop is going through the same router.

---

### Post by wojox on 2010-08-21
Try [this link]("http://sourceforge.net/projects/webadmin/files/webmin/1.510/webmin_1.510-2_all.deb/download")

---

### Post by Lakeside5 on 2010-08-21
I've gone to that link before, but on my laptop. Not sure how to use it on the computer (which just shows me the command line...). I go to the link and it asks me to save the file, then I don't know how to take this file from the lpatop, and install it somehow into the ubuntu on the computer.

---

### Post by Lakeside5 on 2010-08-21
I've gone to that link before, but on my laptop. Not sure how to use it on the computer (which just shows me the command line...). I go to the link and it asks me to save the file, then I don't know how to take this file from the laptop, and install it somehow into the ubuntu on the computer. I also typed the address for that link at the command line, but got the error message.

---

### Post by Lakeside5 on 2010-08-21
So, is there a solution to this, or do I have to break down and take it to the shop (they can't see me for two weeks and they charge toooo  much to install ubuntu, I think lol) I may, when I was installing the ubuntu from the flash drive, entered some wrong info like the ip address of my router for instance, but now I'm wondering how to start over, how to reinstall it. Any ideas?

---

### Post by earthpigg on 2010-08-21
> **Lakeside5 said:**
> I've gone to that link before, but on my laptop. Not sure how to use it on the computer (which just shows me the command line...). I go to the link and it asks me to save the file, then I don't know how to take this file from the lpatop, and install it somehow into the ubuntu on the computer.

dpkg -i would be the command to use. you can move it over to the server via a thumb drive, or email it yourself, etc.

> do I have to break down and take it to the shop 

i vote no. i vote for install plain-jane graphical ubuntu yourself, and use it as a server. it will curb the learning curve, and still work just as well as a server.

servers dont have GUIs by ***tradition***, not for any good reason that still applies in 2010. screw tradition, do what works for you. if you aren't sure how to transfer a file from a thumb drive to the computer at the command line, i think you would be better off with a graphical interface.

---

### Post by Lakeside5 on 2010-08-21
Probably lol To be honest I'm no techie and i'd be just as happy with the plane jane installation and a gui if it isn't too insecure- the last installation with a gui got hacked. But then mayve that had more to do with the vulnerabilities in Joomla (my website)than my server, I'm not sure. Here's my immediate problem though, I don't know how to wipe my hard drive clean and start over. Also a weird thing: I was sure I installed it into the hard drive using my flash stick, but if I try to boot without the flash stick in, all I get is a black screen and a little bliniking dot top left corner. If I put the flash back in, it goes to teh ligin prompt.

---

### Post by wojox on 2010-08-23
> **Lakeside5 said:**
> Probably lol To be honest I'm no techie and i'd be just as happy with the plane jane installation and a gui if it isn't too insecure- the last installation with a gui got hacked. But then mayve that had more to do with the vulnerabilities in Joomla (my website)than my server, I'm not sure. Here's my immediate problem though, I don't know how to wipe my hard drive clean and start over. Also a weird thing: I was sure I installed it into the hard drive using my flash stick, but if I try to boot without the flash stick in, all I get is a black screen and a little bliniking dot top left corner. If I put the flash back in, it goes to teh ligin prompt.


Sounds like it's still on your Flash Stick.

---

