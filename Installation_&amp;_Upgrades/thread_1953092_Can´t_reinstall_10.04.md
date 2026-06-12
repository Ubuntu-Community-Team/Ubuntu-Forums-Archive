---
title: "Can´t reinstall 10.04"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by Lemuriano on 2012-04-05
After using 10.04 for a couple of years my hdd die and then install a new one but for some reason the system do not allow me to install 10.04 in the new hdd. But I was able to install 11.10. Any one had this situation.

---

### Post by Paddy Landau on 2012-04-06
Please remember that we cannot see your computer. You need to be specific. What exactly was the error?

---

### Post by Lemuriano on 2012-04-06
Thank you for your replay and sorry about the lack of details. 

When I boot from my usb with 10.04 64 bit this is the screen that appears. I download twice 10.04 just to make sure. This is a sytem76 pan7 that came with 9.10 and subsequently was upgrade to 10.04 until now. 

On the other hand, their is no obstacle when attempting to install 11.10 but I would like to be able to stay with 10.04 at least one more year. 

Right now Xubuntu 11.10 is install and working fine with the exception that I hear from time to time a small sound that appear to come from the hard drive. (It sound like a metal part is touching something and it last less than a second and **apparently **does not affect the performance of the laptop.)

Last night I check the disk for errors with disk utility but it was healthy.

Any advice would be greatly appreciated

---

### Post by Paddy Landau on 2012-04-07
Hmm, it is curious that you can boot 11.10 but not 10.04.

You would like to remain with 10.04 LTS for another year (when its support term expires). What will you do then... go to 12.04 LTS?

To check that your downloaded ISO is correct, it is not necessary to download again. I have had an instance where the source from which I was downloading (an official source) was corrupt. The way to find out is to [check its MD5sum]("https://help.ubuntu.com/community/UbuntuHashes"). Do this now to ensure that your download is valid.

If it is valid, the next question is how you wrote the ISO to your USB. The "approved" method is to use Startup Disk Creator. If this is not how you created your USB, install [FONT=Lucida Console]usb-creator-gtk[/FONT] from Ubuntu Software Centre, Synaptic Package Manager or the terminal and reinstall to your USB.

If it still fails, you may have to burn the ISO to a CD and install from there.

If none of the above works, then I confess that I am stumped -- sorry. You may have to bite the bullet and install 12.04 LTS when it comes out at the end of this month.

---

### Post by Lemuriano on 2012-04-07
I follow yours recommendations and happy to say that it was possible to successfully burn and boot from a cd with 10.04. 
    [LEFT]
[/LEFT]
    [LEFT]Since it´s MD5sum was correct and for the Ubuntu family I always use usb-creator, the only equation left for me was that the usb drive is defective, so another usb drive was put to the task with the same puzzle outcome. 
[/LEFT]
    [LEFT]
[/LEFT]
    [LEFT]Both are defective? Possible, but not probable.  
[/LEFT]
    [LEFT]
[/LEFT]
    [LEFT]I suspect that if one´s wants to learn about something, what matters is not necessarily answering a question but rather finding and answer which you help me achieve.[/LEFT]
    [LEFT]
[/LEFT]
    [LEFT]Regarding 12.04, I install Xubuntu and Ubunt/Unity on my HTPC so I defenetly will make the jump to the customizable Xubuntu.[/LEFT]

---

