---
title: "Language Selection Screen - Keyboard Freezes"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by 4d4m on 2008-06-17
Greetings,

I'm currently trying to load 8.04 LTS on a Dell Optiplex GX520 and, as always, the first screen I see when booting off the CD is the language selection screen. However, not like always, my keyboard seems to freeze and I am unable to do anything (move / select language or hit a function key). I checked to see if the keyboard is responsive and it doesn't appear to be so (by that I mean I hit num lock over and over and over hoping the num lock light would turn off and on... it didn't). 

Anyway I slapped in my 8.04 desktop disk and the same thing happen. However there was a countdown that happened on that disk that auto selected English for me. After that I was able to use my keyboard and mouse with out incident. 

So I put the Sever disk back in and still no luck. I then proceeded to use a different disk, CD-ROM drive, hard drive, RAM, and keyboard(s). Nothing has seemed to help. I would like to say that I've installed LTS on a couple of other machines using this disk. Even installed it on a GX280 with is very similar. 

With that all said, I'm still a fairly large newb at Linux and I'm not sure where to go from here. Any help would be appreciated. 

Thanks,
Adam

---

### Post by 4d4m on 2008-06-18
Fixed: Apparently you can just hold down the Shift key after the computer POST. Then it will give you the option to skip the graphical interface. Easy enough I guess.

Thanks for all the help......

---

### Post by wpshooter on 2008-06-18
I have never installed the server version before but I really can't imagine why you would have to do that.

Did you check to see if the CD drive firmware was on the latest version on the machine you are having the problems on ?

---

### Post by bchapman on 2009-01-02
I know this is an old thread, but in case anyone is searching and comes across it - there might be multiple reasons for the issue, but in my case it was lack of support for USB keyboard in the BIOS. Double-check your BIOS settings and make sure that you have "enable USB keyboard support" selected. I was using an old PC for a media server project and trying to install 8.10 server. It failed until I turned on USB KB support. BTW, the shift-key workaround didn't work for me without USB KB support.

Thanks! Ben

---

