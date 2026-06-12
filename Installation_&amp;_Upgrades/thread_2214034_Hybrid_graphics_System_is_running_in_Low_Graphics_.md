---
title: "Hybrid graphics: System is running in Low Graphics Mode error"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by Vincent_Siu on 2014-03-30
Hey guys! New to linux, and I decided to install ubuntu 12.04 LTS a few days ago. 

Using this model of labtop
[https://www.asus.com/Notebooks_Ultrabooks/N550JV/#specifications](https://www.asus.com/Notebooks_Ultrabooks/N550JV/#specifications)

So, I'm dual booting Windows 8 and ubuntu. Whenever I try to use ubuntu though, I get the message in the title. I've already upgraded my nvidia drivers as directed in [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error), but the message still appears. After updating the nvidia drivers, I did start getting this screen to appear before the "system is running in low graphics mode error" [http://3.bp.blogspot.com/-Uzk18fmHKG0/TaJYMzOhmFI/AAAAAAAAAv0/bHL6bY0mW7w/s400/ubuntu+loading.jpg](http://3.bp.blogspot.com/-Uzk18fmHKG0/TaJYMzOhmFI/AAAAAAAAAv0/bHL6bY0mW7w/s400/ubuntu+loading.jpg) 
what should I do now? Is this a problem with the hybrid intel-nvidia graphics card?

---

### Post by gordintoronto on 2014-03-30
Yes, it's a problem with the hybrid graphics. If you run the command: inxi -G
it should tell you which video is actually being used. (I'm sorry, I'm not sure if inxi is part of Ubuntu 12.04 by default, you might need to install it.)

I generally suggest using an OS version which is newer than the hardware design. You could get a pre-release version of Ubuntu 14.04 and see how that goes. The scheduled release is less than three weeks away.

By the way, your Asus link requires editing to actually reach the page.

---

### Post by grahammechanical on 2014-03-30
If you have Nvidia Optimus technology then this will be of interest to you

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

I do not have Optimus so I cannot comment on that but I have been running trusty tahr for months and months. I am running it now. It is stable. I even enabled the Proposed repository the other week and I have not suffered any ill effects. If we enable the Proposed repository to get a particular upgraded package then we can disable it once that package has come through.

Regards

---

