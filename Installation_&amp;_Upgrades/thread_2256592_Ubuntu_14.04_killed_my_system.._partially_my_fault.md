---
title: "Ubuntu 14.04 killed my system.. partially my fault."
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by campcreekdude on 2014-12-13
I upgraded to Ubuntu 14.04 and it warned me that my Graphics Card was not compatible.
I did not take this warning seriously because I thought well it does not need to be compatible I can just run a default driver and not have all my features.
I only use it for VLC... and surfing, and i had everything working the way i wanted it with Windows 7 in a virtual box. I had my computer just fine.
Not even sure why I upgraded to 14.04... well it must have been the annoying hey do you want to update warnings that Ubuntu gives.
Then I thought Might as well.... even though I did not need it.

However, I tried fixing and going to an older version in Recovery Console.

All i get is a black screen and a little white mouse at load up of Ubuntu and it will sit like that for hours.
I hope Ubuntu Is not forcing people to upgrade video cards for the next OS's. 
Thats sad. I know 14.02 had issues with really old video cards. BUT the 7970 is not that old...

Should have not updated. If anyone knows how to fix I would enjoy help.

---

### Post by ibjsb4 on 2014-12-13
You cannot downgrade, you can only reinstall.

An option ..
You could try to add a different desktop that does not depend on Unity.
At the login screen, boot to tty (Ctrl + Alt + F2) and login.  Then ..
```
sudo apt-get install gnome-panel
```
Reboot and at the login screen, click on the icon and choose "Flashback (metacity)'.

Can't tell you much about getting Unity running, I do not use it.  But I think that graphic cards may need to be edited to include 3D effects and there may be 3D settings in bios.

And next time you get those annoying version upgrade messages, just disable them :)
[ATTACH=CONFIG]258561[/ATTACH]

---

### Post by campcreekdude on 2014-12-13
I did as you said and now i can use the recovery advanced options to get into ubuntu.
It works normally after i load a previous version in advanced options of boot up manager.

Now the problem is still with the normal boot. I can't get into it at all even after the items i told you to do.
Its just a bunch of corruption on screen with normal boot.

I can figit around and get the password to work but still enter the OS and its full of corruption cant accomplish anything.
Don't know how to fix it. I cant see any icon to go back to flashback metacity.

---

### Post by ibjsb4 on 2014-12-14
> I cant see any icon to go back to flashback metacity.
The only way is at the login screen[ATTACH=CONFIG]258575[/ATTACH]

And click on the icon
[ATTACH=CONFIG]258574[/ATTACH]

---

### Post by campcreekdude on 2014-12-14
Okay... will it be permanent. because login screen is black. I have to do this blind. If i installed it properly on top of that but I typed in what you said therefore it should be good.
Will play with it in a little while.... thanks.

---

### Post by campcreekdude on 2014-12-17
It is possible to log into UBUNTU 14.04..... BUT there is so much screen corruption. I tried to switch to Metro-desktop or whatever... but I an unable to do so. 
I need information on Recovery Mode. Are Changes done in Recovery Mode then resume boot permanent.
Lets pretend I find a graphic Driver for the 7970 that is supposed to work in 14.04. Will I be able to boot in normal 14.04 if I install it in 14.0.35 or whatever verion i am recovery booting into?

---

### Post by campcreekdude on 2014-12-17
_**Linux Distribution Specific**_

[LIST]
[*]Red Hat Enterprise Linux Suite 7.0 , 6.5
[*]Ubuntu 12.04.4 LTS, 14.04 LTS
[/LIST]
Apparently the DRIVER from AMD supports 14.04 and 7970....

---

### Post by campcreekdude on 2014-12-17
So I installed the latest driver using Trusty Method.... and now Ubuntu Loads with no special junk.\
So If I do upgrade in the future I will have to double check if drivers come out for the latest Ubuntu with my Radeon 7970.
To bad they did not have a driver that all video cards worked with like generic Standard VGA like Windows.... 
But going to a recovery mode and installing the new Catalyst... enabled me to launch  into 14.04 no problem now.

---

### Post by ibjsb4 on 2014-12-17
Nice fix :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by campcreekdude on 2014-12-18
Ya... workspace switcher is working properly with the 'real catalyst driver'... I assume people always update to the latest graphic driver except me for Ubuntu and they would not run into this problem. 
Ubuntu works for me now... and I should just leave it alone. I don't notice any huge features going from 12.04 to 14.04. I remember SSD was supported eventually during that time period. I remember reading about that.
I think my bandwidth use went overboard this month because of this update... hahah
I opened up my browser and the company redirected my browswer to a page saying I used more than 120% of my maximum and they are throttling me. So run with images disabled i guess just for another 15 days i guess. lol
Oh i am blabbing now.

---

