---
title: "gutsy takes a long time on boot: trying to resume from something that doesen't exist"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by guano on 2007-10-12
Hi, I'm trying the Gutsy beta for about a week now. It works _almost_ perfectly. There are two issues (Compiz should work but don't and boot time), but I will adress only one here, the boot time.

Every time I turn my machine on (Samsung R20 laptop), it takes a long time to actually start doing the bott. If I go to Alt+F1, I can see it is trying to "resume boot" from some file or boot image, or whatever, but there is no file or whatever, so after I hit Crtl+C, it stopos looking for this resume image and proceeds to normal boot.

It's not related to network.

I never played much with GRUB configs, can I set it so it won't try to "resume" anymore? Or any other real fix, as I see this as a workaround?

thanks

sorry, for not posting complete system messages..

---

### Post by franestepona on 2007-10-15
Same problem here, quite annoying. In addition to that, I cant see the ubuntu logo when starting up, just a black screen, and my frequency scaling doesnt work either...

Someone got a hint on what to do??

---

### Post by oneedge on 2007-10-17
Same issue.  Long boot time, no image.  Installed from CD (release candidate) with everything updated on a Dell Inspiron 6000 laptop.

---

### Post by b4silence on 2007-10-19
Hi!!

I've installed the 7.10 official release and I noticed the same problem.

If you check the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/710") (last note), you can see tha the boot splash is a known problem.

The Ubuntu developers are working on it...

I'm still trying to find an answer for the boot time though.. I have exactly the same problems as you guys...

Running ubuntu on an acer 5051 amd turion 64 2000+ 1.5Gb RAM and ATI X1000...


Bye

---

### Post by Julius on 2007-10-20
Exact same problem here.

---

### Post by mr_fong on 2007-10-20
Same here, and my system hangs after a couple of hours too. First install messed up the console fonts (way to big), second install went fine. Went back to Feisty because of the hanging system. Have a Toshiba A40 --Hans

---

### Post by Nikos.Alexandris on 2007-10-20
Hi! Did you guys owning a Samsung R20 upgraded or performed a fresh install of gutsy? Didn't have any issues with the ATI 1250 graphic card?

---

### Post by franestepona on 2007-10-20
> **Nikos.Alexandris said:**
> Hi! Did you guys owning a Samsung R20 upgraded or performed a fresh install of gutsy? Didn't have any issues with the ATI 1250 graphic card?

I solved frequency scaling problem, it was some kernel bug, I downgraded to 15.20 kernel and now it's fine. About the ati card, I own a ATI mobility radeon 9600 and it's working good, i just had to recompile fglrx from source and worked out of the box. For me the upgrade worked fine, just make sure u have a good backup before trying to upgrade.

---

### Post by sirwitti on 2007-10-20
hi together!
i had the same problem on my Acer Travelmate 4001:
no bootsplash at startup (but it worked at shutdown) and boot time was more than it should.
as is seems, the resolution for the bootsplash is detected uncorrectly, which causes both problems.

the solution that worked for me:
1) change resolution in /etc/usplash.conf to the correct one for my/your screen:
```
     xres=1024
     yres=786
```

2) execute the following:
```
     sudo update-initramfs -u -k `uname -r`
```

if found it at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930")
hope, that helps you too.
have fun, witti

---

### Post by bipco on 2007-10-20
Same here on ThinkPad T-40 with ATI Radeon - thanks for the Alt-F1 tip, when I did that I could see it was doing the resume thing, but then it carried on with a normal boot straight off (but still no splash screen). Without that it was taking about three or four minutes to get from GRUB options screen to login (versus about 45 seconds for Feisty).

I've got Feisty and Gutsy side-by-side, so I think I'll stick with Feisty for work until this gets really fixed or we have a workable hack.

Warren

---

### Post by floke on 2007-10-20
** Never mind - the fix above works better! **

---

### Post by djwheels on 2007-10-20
I can confirm that sirwitti's solution for changing the usplash resolution fixed the problem on my Thinkpad X31.

Thanks

---

### Post by franestepona on 2007-10-21
sirwitti's solutionn worked for me too, thanks man!!

---

### Post by frithiof on 2007-10-23
sirwitti did the job here on my ASUS W3000N as well.
Thanks a bunch!

---

### Post by kOna on 2007-10-23
Will give this a try tonight when I get home, thanks for the fix :)

---

### Post by MeKKeR666 on 2007-10-24
Dell Inspiron 5100
P4 2,4 Ghz
512MB ram
ATI Mobility Radeon 7500 same problems.

Fixed with :

- editting the usplash.conf to 1024x768
- sudo update-initramfs -u -k `uname -r`

Startup time decreased to 30 secs instead of 2+ mins, bootsplash working perfectly now.

Also needed to install the xserver-xorg-video-ati and added Option "LVDSBiosNativeMode" "False" under "Device" to get rid off the standard VESA driver.

---

### Post by tashmooclam on 2007-10-30
I have the same problem, only on this laptop with the lower res. My 15" screen laptop doesn't experience this odd problem.
I tried Sirwitti's fix, but I had a problem changing the usplash config.
I used the replace button and changed the res to my laptop. 
But, I could not save the file, or close and save the changes. I got a message that I didn't have permission to make any changes. 
How do I make changes to the "usplash.config" file? Please advise me.
Thanks

---

### Post by hoges on 2007-10-30
You need to run it with admin privileges ie:
sudo gedit /etc/usplash.conf

It will then ask you for your login password.

Cheers
Hoges

---

