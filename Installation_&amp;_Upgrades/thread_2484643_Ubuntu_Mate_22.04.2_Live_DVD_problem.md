---
title: "Ubuntu Mate 22.04.2 Live DVD problem?"
date: 2023-03-05
forum: Installation &amp; Upgrades
---

### Post by ken0069 on 2023-03-05
I downloaded Ubuntu Mate 22.04.2 and burned it to a DVD so I could run it live to see what it looks like, BUT, I get the following error on 3 different computers and from 2 different DVDs??

             

              
              Panel encountered a problem while loading &#8220;BriskmenuFactory::BriskMenu&#8221;  ??             

              
              Can someone tell me what this means?

             

              
              And FYI, I&#8217;ve got Linux Mint Mate 21.1 installed on the same hardware I tried to run Ubuntu Mate live on.             
              
              Thanks

---

### Post by #&amp;thj^% on 2023-03-05
> **ken0069 said:**
> Panel encountered a problem while loading “BriskmenuFactory::BriskMenu”  ??


 Can someone tell me what this means?

It means the menu got tripped up along the way.
try this next time:
```
killall mate-panel
```

---

### Post by ken0069 on 2023-03-05
Can't run any terminal commands cuz got no terminal icon to open it with?  That and there's NOTHING else to do much of anything with except shut down.  

I took a picture of the monitor screen but I can't upload it here?????

Thanks but I guess I'm just going to wait and see if anyone else has an idea what's going on with it.

---

### Post by #&amp;thj^% on 2023-03-05
My goodness can't you use a key combo of <Ctrl+ Alt+ t>
But your more than welcome to wait for someone else...good luck

---

### Post by MAFoElffen on 2023-03-05
Or press the keys (simultaneously): <Cntrl><Alt><F4> ...which will toggle the session to VTTY4 so you can log in with your username and password... Then type in the previous tcommand give by fallen1... To reset your menu...

---

### Post by guiverc on 2023-03-05
You used DVD?

DVD media is not expected to be used on releases past Ubuntu 20.04 LTS; for a number of reasons, one of which is the media scan that now occurs in the background.  As the media scan checks the whole drive, it takes time, which on *optical* media with very slow seeks *timeout *errors can occur which are interpreted not as issues with the DVD itself, but as errors but however the code was written (ie. Briskmenu won't know about DVD timeouts, so the error can will be interpreted as its code expects not being coded for slow media).

Best results are letting the media check complete before you start using it (*and this can take up to 60 minutes post boot depending on your CPU, speed of DVD etc*). You can scan system logs to see when media check has completed, but lack of *optical drive activity* can be a clue.

Look at system logs for your actual errors, ie. if a *timeout *occurs there you can assume any GUI message that occurred just after that can be misleading and a consequence of timeout issues.

Easy fix is to use FLASH MEDIA as is expected for releases beyond Ubuntu 20.04 LTS.

This may or not be your issue, but I'd suggest reading system logs carefully esp. looking for *timeout* issues relating to your usage of *optical* media...  Did the media verification complete before you started using it? as you'll get far less issues after that completed (*the media check will fight to read different parts of the media compared to what you want to use creating far more timeout errors*).

---

