---
title: "Weird screen after boot and other strange issues."
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by Illumettius on 2012-01-23
Hello all  

This is my first time on this forum. I have absolutly no experience with Ubuntu.
I would like to give Ubuntu a try. 

One of my friends told me I should try Wubi so I don't have to delete my windows7. 
But I have had some problems installing Wubi though. 

First off, I got a Permission Denied error ( IOError: [Errno 13] Permission Denied: 'G:\\wubidlr') at the end of the install.
After some googling I managed to overcome that error by putting wubi.exe and the Ubuntu 11.10 ISO into the same folder. After that, I rebooted, and I got the option to chose either Windows 7 or Ubuntu. I selected Ubuntu, but after that I got a black screen with the following message: 

"Completing the Ubuntu installation. 
For more installation boot options, press 'ESC' now... 
(timer: 3-2-1-0)" 

Once the timer reached 0, I couldn't do anything else, I waited about 2 hrs but still nothing happened. So I had to do a hard reset. I know it's bad, but I had to, because nothing else responded. 

Then I tried booting Ubuntu again, this time I got in (yay!) but then the screen went very weird. I think it has something to do with my Graphics Card (nVidia Geforce 9600 GT). I'll put a picture of my screen as attachment (I couldn't use printscreen button so I took a picture with my camera, sorry for the bad quality)

Any advice on this issue will be very much appreciated. I don't know that much about Ubuntu though. Also, sorry for my bad English, I'm not a native speaker but I tried my best to explain my issue. I hope you can understand it.
(Also sorry if this is not the right section on the forums, I was hesitating to put it on the newcomers forum, but eventually put it here because of the installation)

I'm very interested in Ubuntu, so it would be nice if I get it installed properly and ready to go.

Additional information:
-Ubuntu 11.10 (that's the one I tried installing)
-GPU: nVidia Geforce 9600 GT
-I'm using Windows 7 atm
If you need more information, feel free to ask.

Thanks in advance

Kind regards


Illumettius

---

### Post by Rubi1200 on 2012-01-23
Hi and welcome to the forums :-)

You are right that this is most likely a graphics issue.

Posts 1 and 8 here describe the options available (use nomodeset:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You can ignore the non-Wubi comments in the first post since the process is essentially the same on first boot with/without Wubi.

---

### Post by Illumettius on 2012-01-23
Thank you :-) I'll take a look at it.

---

