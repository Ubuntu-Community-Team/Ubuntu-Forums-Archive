---
title: "can't even get live cd to run"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by snitramc on 2007-02-23
Hello all,

I downloaded 6.10. I ran the hash check using MD5sum, and all was well. I burned a cd using Nero. When I try to run ubuntu from live CD, the CD just gets byapssed after checking it, and my laptops (I have tried it on three different laptops) all boot to windows. I am trying to use it right now on a Dell Inspiron 1405 w/2G RAM, dual core procs, and an 80G HDD. I went into the BIOS and set it to boot from the CD and it still just looks at the CD and goes to XP. If I insert the CD after the laptop is running, it runs the Ubuntu browser and asks me if I want to install all the included apps, and also tells me it is a CD that can boot my laptop. But it never boots from the CD. I tried this from two older Dell laptops (an Inspiron and a Latitude) with similar results. Think I should try burning another CD? I just can't see that as the problem.

---

### Post by taurus on 2007-02-23
Are you sure the have set your BIOS to boot from the CD first instead of the harddrive?  IF the same CD boots with one computer but not the other, then there is something wrong with the BIOS of the second command that can't boot it.

---

### Post by snitramc on 2007-02-23
I am POSITIVE that the laptops are set to boot off the CD first. I went in twice and double checked. On my Dells, there are two ways to select boot drives - F2 for a one time boot order, or F12 to set it in BIOS. I tried it in two laptops, using both F12 and F2, and every time, it just spun the CD around for about 15-30 seconds, and then booted to Windows on the HDD. I think I'll download an older verison of Ubuntu and see if I see anything different. BTW - I have installed Solaris and Redhat on systems, so I do know what an X systems install is supposed to do. Of course, that doesn't mean I am not doing something stupid.

---

### Post by snitramc on 2007-02-26
It turns out there was something wrong with Nero. I burned the ISO on another computer and it worked perfectly. So I uninstalled and re-installed on the original offender, and I got a good image. Sorry for the panic. Who'da thunk it?

---

### Post by .alpeffers. on 2007-02-26
try 6.06, i have the Canadian version of the 1405(640m) and I've found the 6.10 live disc won't load... no matter what i try... its something with the laptop it doesn't like(kubuntu 6.10 live disc works, after some finessing)... that or Dell has purposely made their laptop resist linux :p

but yeah, go 6.06 and use safe graphics... making sure to boot from CD too ;)

i'm starting to get the impression that you'll hafta use 6.06 and then not upgrade to edgy or you might be in my boat(no wireless, or something else breaks :mad: )

---

