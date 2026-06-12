---
title: "Unable to boot :("
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by forpulse on 2011-05-06
So i installed ubuntu 11.04 using wubi from window 7. and I have dual boot now. Installation went fine. but after installation completed and it restarted, I get errors. It never boots up. After selecting ubuntu from windows boot menu and selecting ubuntu from the ubuntu boot menu (pinkish menu) I get errors. here is the snap shot of it. [http://flic.kr/p/9Fe2BG](http://flic.kr/p/9Fe2BG)

please someone help me out.

My laptop specs are.

lenovo y560
i5-450M, 4gb ram, ATI Mobility Radeon HD 5730 1gb. 

Thanks a bunch :)
[IMG]http://flic.kr/p/9Fe2BG[/IMG]_[IMG]http://www.flickr.com/photos/62582862@N04/5694739378/[/IMG]_

---

### Post by ryannathans on 2011-05-06
> **forpulse said:**
> So i installed ubuntu 11.04 using wubi from window 7. and I have dual boot now. Installation went fine. but after installation completed and it restarted, I get errors. It never boots up. After selecting ubuntu from windows boot menu and selecting ubuntu from the ubuntu boot menu (pinkish menu) I get errors. here is the snap shot of it. [http://flic.kr/p/9Fe2BG](http://flic.kr/p/9Fe2BG)

please someone help me out.

My laptop specs are.

lenovo y560
i5-450M, 4gb ram, ATI Mobility Radeon HD 5730 1gb. 

Thanks a bunch :)
[IMG]http://flic.kr/p/9Fe2BG[/IMG]_[IMG]http://www.flickr.com/photos/62582862@N04/5694739378/[/IMG]_


HOW ON EARTH DID YOU GET THIS FAR?!

With WUBI when I choose ubuntu to boot it is looking for some MBR file but can't find it.

/ubuntu/winboot/???.MBR  I think...

Still looking for a fix. xD

WUBI is fail and always has been for me.

---

### Post by wilee-nilee on 2011-05-06
> **forpulse said:**
> So i installed ubuntu 11.04 using wubi from window 7. and I have dual boot now. Installation went fine. but after installation completed and it restarted, I get errors. It never boots up. After selecting ubuntu from windows boot menu and selecting ubuntu from the ubuntu boot menu (pinkish menu) I get errors. here is the snap shot of it. [http://flic.kr/p/9Fe2BG](http://flic.kr/p/9Fe2BG)

please someone help me out.

My laptop specs are.

lenovo y560
i5-450M, 4gb ram, ATI Mobility Radeon HD 5730 1gb. 

Thanks a bunch :)
[IMG]http://flic.kr/p/9Fe2BG[/IMG]_[IMG]http://www.flickr.com/photos/62582862@N04/5694739378/[/IMG]_

At that pinkish menu choose the recovery kernel second one then safe boot, should be low graphics mode. If you get a cli after the safeboot choice login and run startx.

For the radeon card you probably need a driver look in menu-system-admin-additional drivers for anything needing installed.

Remember no grub updates in wubi they will overwrite the mbr, of the HD.

---

### Post by forpulse on 2011-05-07
so like u suggested, i tried safe booting several times. here is the video 

[http://youtu.be/TpqtKCo4Xbg](http://youtu.be/TpqtKCo4Xbg)

first time, it got stuck on the part where it said switching...

second time i got to the menu but before i press enter to select, something happened on its own and screen became pitch black nothing happening

3rd time it also got stuck on a different error.. nothing was happening so i had to do a manual shut down again. and now i just gave up. 

so lost.

---

### Post by wilee-nilee on 2011-05-07
> **forpulse said:**
> so like u suggested, i tried safe booting several times. here is the video 

[http://youtu.be/TpqtKCo4Xbg](http://youtu.be/TpqtKCo4Xbg)

first time, it got stuck on the part where it said switching...

second time i got to the menu but before i press enter to select, something happened on its own and screen became pitch black nothing happening

3rd time it also got stuck on a different error.. nothing was happening so i had to do a manual shut down again. and now i just gave up. 

so lost.

You chose continue regular boot not fail safe. At least from what I saw. To long of a video to watch the whole thing , I'm working for free here, lol.:)

The recovery kernel gets you to that menu the top line does nothing but continue a regular boot.

Okay watched the whole thing try another safe boot with the e=edit out quiet splash and replace with nomodeset in the first kernel and crtl-x to boot to cli login then starx.

If I am not explaining this well enough let me know, the only answer I can work on is a low graphics boot. I'm not sure this is the problem completely though.

Okay  hope you get this working but you have two threads on the same problem, not a good protocol.
[http://ubuntuforums.org/showthread.php?t=1743989](http://ubuntuforums.org/showthread.php?t=1743989)

---

### Post by forpulse on 2011-05-08
sorry about the new thread... i only made a new one cause no one was replying to me anymore :$ ... i tried to do what you suggested. But not working at all. still getting this error ( [http://flic.kr/p/9Fvb2j]("http://flic.kr/p/9Fvb2j")). I use to have 10.04 which worked flawless...

---

