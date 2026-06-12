---
title: "Can't install or Upgrade to 6.10"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Dagonus on 2007-02-04
I have a Compaq Tablet TC1000 that I'm trying to get 6.10 on. 

When the system fails, it usually freezes entirely. Can't get to a console to see what its doing and the CD stops spinning and it just sits. Sometimes, it keeps spinning the CD and the whole install just sits someplace and nothing gets done. Upgrades result in a system with a broken/incomplete XServer.

First I tried a dirty upgrade from 6.06. That failed and took the X-Server out with it.

Then I tried a clean install from the desktop CD using a Eide to USB external kit and an internal CD Drive mounted on that. (theoretically it's sized for HDDs but CDs work just as well). That failed at 90% complete.

Then I tried the Alternate CD. That failed.

Then I tired Xubuntu, figuring "good enough." That failed.

The I tried installing 6.06. That worked. So the CD conversion to USB is good.

Then I tried going the dpkg upgrade to 6.10. That failed and gave me an error message and suggested I try the Apt-get method. 

I tried the Apt-Get Method. The system restarted alright, but it was still 6.06. Lovely.

Then I tried using the 6.10 Alternate CD as a repository for the upgrade. That failed and took the X-Server out with it again. Then I tried the method I used to fix the Xserver when it died in the first place: [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177) 
That didn't work. It didn't ever get anywhere. 

Then I attempted to install XUbuntu Desktop CD in safe graphics mode. That failed.

Then I attempted to install it from the Ubuntu Alternate again as an OEM (Figured can't hurt to try.) That told me that there was a problem with IRQ 9 and to try IRQpoll. I know what IRQs are, but what specifically IRQPoll is supposed to do or how specifically to implement it, I don't know. 

So I tried it from the Alternate CD using F6 for more options and sticking IRQPoll at the end. That probably wasn't right, but my Linux mastery isn't that high. I can fiddle and replace things with backups that I've kept, and follow instructions for term commands and even understand what a good number of them are doing, but I havne't a grasp on internal workings enough to troubleshoot this solo any further. This got to just past where it asks for Screen resolutions in "select and install software." I saw a few X-Server things pop up and then it got stuck at 6% with the CD spinning.  Now, in this case it hasn't locked the whole system. I'm getting Buffer I/O Errors on device sr0 on TTY4. It then comesup and says that there was an error and that part of the installation failed. If I tell it to go again, it gets as far as "yelp zenity zip" and then dies again at 6%

Is it just physically impossible for me to run 6.10? I'll accept a Xubuntu install if that's what I can get or an Ubuntu, I'm not too picky, but I really wanted to move on up to 6.10. Does 6.10 just not like EIDE CD Drives? Should I attempt to do the whole thing off a Flash drive? If so... I need to know how to set the Flash Drive up so it will work.

---

### Post by Dagonus on 2007-02-04
Ok, I told it to try again and it managed to finsih the install, but not before the console threw out a mess of errors that flew by so fast that I couldn't read them. 

Now I can't get it to acknowledge my wifi  card in the slot. It picked 'em up in 6.06 so I'm disinclined to believe that they just not supported. I think maybe something's bogus in the networking part of the install now. Anyone know how to check properly?

Thanks

---

