---
title: "should i install ubuntu using wubi or not?"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by cshekhar on 2011-10-30
[CENTER]Laptop->lenovo Y560
dual boot using grub2[ubuntu , windows7]
[LEFT]i accidently deleted ubuntu partiton in my laptop. Now i get a error each time i boot->"error no such partition.grub rescue>". ithink it is due to grub being deleted. After some research,i used super grub disk & using it i was able to boot using it. so i thougth of an idea,to reinstall ubuntu ,to get back booting menu so that i can boot to windows without using super grub disk . Question should i install ubuntu using wubi or live cd way?? if you have any other way i can boot to windows please suggest?? 
**Note i am not having windows 7 cd ** 
[/LEFT]

[/CENTER]

---

### Post by MG&amp;TL on 2011-10-30
Wubi will not restore the bootloader's configuration. You need the live cd. However, be careful where you put ubuntu when you partition!

---

### Post by cshekhar on 2011-10-30
if using super grub disk i boot to windows.. then put the the live cd in & then using wubi install ubuntu. .so if do these things then will i get menu to choose windows,ubuntu  or not

---

### Post by MG&amp;TL on 2011-10-30
NO, you will still need to boot the Super grub disk if you do that.

To modify the bootloader so that it is grub (properly configured) you will need to install from the live cd, the way you did when you had grub working.

So boot the ubuntu cd, then install ubuntu.

---

### Post by vasa1 on 2011-10-30
This could get "interesting" quite quickly. Have you backed up your data?

I think you could use the LiveCD to save your data from the Windows partition(s) to a pendrive or whatever.

---

### Post by cshekhar on 2011-10-30
sorry to bug you again
i will put the super grub disk then boot to windows then remove the super grub disk . then put ubuntu live cd & then using wubi install ubuntu..now is it correct??

i am not confident in using live cd diectly. thats why i keep going on wubi. because data that is in windows is quite important to me.i know that will not mess it up..
thanks for giving your time

---

### Post by MG&amp;TL on 2011-10-30
> **vasa1 said:**
> This could get "interesting" quite quickly. Have you backed up your data?

I think you could use the LiveCD to save your data from the Windows partition(s) to a pendrive or whatever.

probably easier for them to boot windows, then copy from there? But good idea, backup first.

---

### Post by MG&amp;TL on 2011-10-30
> **cshekhar said:**
> sorry to bug you again
i will put the super grub disk then boot to windows then remove the super grub disk . then put ubuntu live cd & then using wubi install ubuntu..now is it correct??

i am not confident in using live cd diectly. thats why i keep going on wubi. because data that is in windows is quite important to me.i know that will not mess it up..
thanks for giving your time

Ahhhh...my apologies, how did you install ubuntu last time? (when it broke) Currently, does it go to a black "windows or ubuntu" screen first, then a purple one?

---

### Post by cshekhar on 2011-10-30
the whole dual boot thing was there when i got the laptop
i get a black screen with a error message>"error no such partition.grub rescue>".thats all .. nothing more.. though i have successfully booted to windows using super grub disk.Now should i go with the wubi step..

---

### Post by MG&amp;TL on 2011-10-30
Oh. OK, *did* (past tense) the first screen look like this:

[http://www.google.co.uk/imgres?q=wubi+dual+screen&um=1&hl=en&client=opera&sa=N&rls=en-GB&channel=suggest&tbm=isch&tbnid=NrPPNjeuwIUPrM:&imgrefurl=http://computergadgetandtricks.blogspot.com/2011/07/how-to-set-up-dual-boot-windows-linux.html&docid=UCnKkvCvizDgJM&imgurl=http://4.bp.blogspot.com/-C0jBxIZ93xc/ThLpD6cclCI/AAAAAAAAADM/qU9IWV9zWqs/s1600/wubiBootManager.png&w=520&h=125&ei=SYitTsaPK4LL8QOCtPS9Cw&zoom=1&iact=rc&dur=533&sig=113880833687312894665&page=1&tbnh=37&tbnw=152&start=0&ndsp=21&ved=1t:429,r:3,s:0&tx=95&ty=35&biw=1366&bih=587]("http://www.google.co.uk/imgres?q=wubi+dual+screen&um=1&hl=en&client=opera&sa=N&rls=en-GB&channel=suggest&tbm=isch&tbnid=NrPPNjeuwIUPrM:&imgrefurl=http://computergadgetandtricks.blogspot.com/2011/07/how-to-set-up-dual-boot-windows-linux.html&docid=UCnKkvCvizDgJM&imgurl=http://4.bp.blogspot.com/-C0jBxIZ93xc/ThLpD6cclCI/AAAAAAAAADM/qU9IWV9zWqs/s1600/wubiBootManager.png&w=520&h=125&ei=SYitTsaPK4LL8QOCtPS9Cw&zoom=1&iact=rc&dur=533&sig=113880833687312894665&page=1&tbnh=37&tbnw=152&start=0&ndsp=21&ved=1t:429,r:3,s:0&tx=95&ty=35&biw=1366&bih=587"), or like this:

[http://www.google.co.uk/imgres?q=grub+bootloader&um=1&hl=en&client=opera&rls=en-GB&channel=suggest&tbm=isch&tbnid=AL5EgGds6CfKdM:&imgrefurl=http://buzzcodington.wordpress.com/2011/04/26/restoring-ubuntus-grub-loader-after-installing-windows/&docid=j95eOT40cPWeJM&imgurl=http://buzzcodington.files.wordpress.com/2011/04/grub.jpg&w=720&h=400&ei=LZCtTvO-F9PJ8gPVuKmuCw&zoom=1&iact=hc&vpx=141&vpy=149&dur=517&hovh=167&hovw=301&tx=185&ty=86&sig=113880833687312894665&page=1&tbnh=82&tbnw=147&start=0&ndsp=21&ved=1t:429,r:0,s:0&biw=1366&bih=562]("http://www.google.co.uk/imgres?q=grub+bootloader&um=1&hl=en&client=opera&rls=en-GB&channel=suggest&tbm=isch&tbnid=AL5EgGds6CfKdM:&imgrefurl=http://buzzcodington.wordpress.com/2011/04/26/restoring-ubuntus-grub-loader-after-installing-windows/&docid=j95eOT40cPWeJM&imgurl=http://buzzcodington.files.wordpress.com/2011/04/grub.jpg&w=720&h=400&ei=LZCtTvO-F9PJ8gPVuKmuCw&zoom=1&iact=hc&vpx=141&vpy=149&dur=517&hovh=167&hovw=301&tx=185&ty=86&sig=113880833687312894665&page=1&tbnh=82&tbnw=147&start=0&ndsp=21&ved=1t:429,r:0,s:0&biw=1366&bih=562")

If the former, you have not partitioned, instead you have used wubi. :)

If the latter, you have paritioned. Wubi WILL NOT HELP in this case, you need to reinstall ubuntu.

And how did you delete your partition? (if indeed, it was a partition).

---

