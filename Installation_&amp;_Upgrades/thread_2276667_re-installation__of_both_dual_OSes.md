---
title: "re-installation  of both dual OSes"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by ashok_saini on 2015-05-04
helllo ,
i am a newbie to ubuntu 

i bought this [http://www.flipkart.com/lenovo-b40-70-notebook-4th-gen-ci3-4gb-500gb-free-dos-2gb-graph-59-440450/p/itme2c5hngyqvqwm?pid=COME2C5GAPK6YCBZ](http://www.flipkart.com/lenovo-b40-70-notebook-4th-gen-ci3-4gb-500gb-free-dos-2gb-graph-59-440450/p/itme2c5hngyqvqwm?pid=COME2C5GAPK6YCBZ) thi laptop .

it came with freeDOS preloaded then i installed win8.1 pro and then ubuntu 14.04(also upgraded to 15.04)

but now i forgot my  password of the admin account in the ubuntu ,
 
and i also wants to install win7 as my win8.1 is just not working good, 

how should i do preform the re-installation of both OS.

also why my win8.1 is not working good (i scanned with windows defender - no threats )

here is a pic of my current disk patters [IMG]http://i57.tinypic.com/ildt95.jpg[/IMG]

---

### Post by kc1di on 2015-05-04
The best way to do a re-install of your dual boot system is to install windows 7 first , then ubuntu.   Since windows always wants to set it's self up at the control of the boot.  I take it this a a UEFI machine since you had win 8.1 on it , if it is you may want to disable that first also. 
Good Luck :)

---

### Post by grahammechanical on 2015-05-04
Unless we are prepared to upgrade every 7 to 9 months then we should install and stay on a Ubuntu Long Term Support (LTS) version. I would re-install in this order.

1st install Windows 7
2nd install Windows 8
3rd install Ubuntu

I cannot not give advice on installing Windows. Nor can I give advice on why Windows 8 is "not working good." I do not even know what "not working good" means. Anyway, I know nothing of Windows 8.

If the machine has a UEFI boot system, even if Windows 8 did not come pre-installed, I would follow the advice in this wiki page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you wish advice on troubleshooting Windows problems, then I suggest you open a thread in this section of the forum.

[http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)

Regards.

---

### Post by kurt18947 on 2015-05-04
The advice to install Ubuntu after any Windows OSs is good and for the reason kc1di stated - Windows boot loader doesn't play well with others. ( Big surprise there, huh?:rolleyes:). I did need to install Windows 7 to an existing Ubuntu install. As expected, the machine would not boot Ubuntu afterwards. I created a boot-repair DVD, rebooted and let boot-repair work its magic. Both OSs now boot as expected. I know nothing of UEFI or Windows 8 and for now, ignorance is bliss.

---

### Post by Mark Phelps on 2015-05-04
> my win8.1 is just not working good, I know this is not a Windows forum, but vague terms like this only lead to the suspicion that you have an underlying hardware problem -- as a failing drive would cause ANY OS to not "work good".  

Installing a Linux distro is not a cure for a poorly performing Windows OS.  It would be better for you to determine if the underlying Windows problem is hardware before pressing ahead with a Linux distro installation -- as any hardware problem is going to affect the Linux distro, as well.

If I were you, before wiping Win8 and replacing it with Win7, I would post to a Windows 8 forum for help -- suggest [www.eightforums.com](www.eightforums.com).

---

### Post by kc1di on 2015-05-05
Windows 8 in my experience , which is very limited with that OS. is a dog of an OS any way.  My Wife's laptop came with it installed, best thing I ever did was wipe it and install Ubuntu for her.. Now she's happy.  Problem with here machine was that it simply did not have enough cpu and ram to run 8. but it was a budget buy anyway. 

Another alternative for you might be to run windows in virtual box , with Ubuntu as the host, then you will not have to reboot to use windows when you need it.  That's what I did on her machine, and she hasn't used windows in almost a year now. :)
Good Luck whatever to choose to do.

---

