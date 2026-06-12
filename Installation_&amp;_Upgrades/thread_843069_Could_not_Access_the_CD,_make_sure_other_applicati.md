---
title: "Could not Access the CD, make sure other applications are not using it"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by nickgt08 on 2008-06-27
When I attempt to install Ubuntu-8.04 using a CD I burned(using Nero) on Windows Vista Ultimate, I receive the following message at the end of the "creating image" portion of the install: "Could not access the CD, please make sure other applications are not using it and try again." I tried putting the CD in my other drive and it did not help. It gives me an option to "Retry," but that does not help. 

I am using the Install Inside Windows option.

---

### Post by VMC on 2008-06-27
> **nickgt08 said:**
> When I attempt to install Ubuntu-8.04 using a CD I burned(using Nero) on Windows Vista Ultimate, I receive the following message at the end of the "creating image" portion of the install: "Could not access the CD, please make sure other applications are not using it and try again." I tried putting the CD in my other drive and it did not help. It gives me an option to "Retry," but that does not help. 

I am using the Install Inside Windows option.

Did you preform the media check on the cd disk? Also, what speed did you burn the cd on? It's best to burn at slowest speed. Finally, Nero has a verify option. Make sure you use that.

---

### Post by nickgt08 on 2008-06-27
VMC: thanks for the advice, but I tried re-burning the CD at the slowest possible speed(8x) and using the verification option. I still receive the same error at 99% through the "generating image".

---

### Post by Partyboi2 on 2008-06-28
This is taken from the wubi guide> **Error "Could not access the CD"**

  This sometimes happens when a DVD media/drive is used and/or if the CD is corrupted and/or if the support is of poor quality and/or the CD/DVD is not finalized. Sometimes burning again on different CD media or using a different CD device solves the issue. A quick workaround is to use Wubi directly with the ISO. Just place the final desktop ISO and wubi.exe in the same folder and run Wubi. Do not leave the CD in the tray. 


Do you have success if you try the workaround mentioned?

---

### Post by jtjordan on 2008-07-10
> **Partyboi2 said:**
> 

Do you have success if you try the workaround mentioned?
I just explored the iso on the disk, copied all the folders to a new folder on my desktop. doubleclicked wubi.exe and it worked flawlessly. 
Thanks for helping him help me.

---

