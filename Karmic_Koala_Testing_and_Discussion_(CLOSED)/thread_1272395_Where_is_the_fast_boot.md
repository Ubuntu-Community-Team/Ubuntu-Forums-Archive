---
title: "Where is the fast boot??"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2009-09-22
Hi,
I was wondering where the fast boot speeds are??
They are not on my machine, and it's taking over 1 minute between grub and the desktop.

??????

thanks

---

### Post by zika on 2009-09-22
> **KrazyPenguin said:**
> Hi,
I was wondering where the fast boot speeds are??
They are not on my machine, and it's taking over 1 minute between grub and the desktop.

??????

thanksOn my machine the boot-time was shortened for more than 10 sec with upgrades this morning and I'm back to above the Jaunty speed. Alpha's 3 and 4 were a bit faster.

---

### Post by 23meg on 2009-09-22
> **KrazyPenguin said:**
> Hi,
I was wondering where the fast boot speeds are??
They are not on my machine, and it's taking over 1 minute between grub and the desktop.

It's impossible to tell without seeing your [bootchart]("https://wiki.ubuntu.com/BootCharting") output.

---

### Post by Nickedynick on 2009-09-22
My boot is still slower, but I'm not sure if that's due to Ubuntu or something I've messed up. My bootcharts for Jaunty and Karmic on the same system are below:

---

### Post by vishalrao on 2009-09-22
Aren't the actual boot speed improvements due to land "by" the Beta milestone?

---

### Post by Nickedynick on 2009-09-22
I had heard that,  not sure how true it is though. Either way I think I'll reserve any complaining until I've installed the beta :)

---

### Post by philinux on 2009-09-22
My bootcharts show 15 and 22 seconds. At the moment it's back to 22 but I think thats cos of the udev bug at startup. Things will improve as the bugs are cleared.

---

### Post by VMC on 2009-09-22
> **philinux said:**
> My bootcharts show 15 and 22 seconds. At the moment it's back to 22 but I think thats cos of the **udev bug at startup**. Things will improve as the bugs are cleared."udev" bug was fixed yesterday updates. If you mean the "symlink" errors.

---

### Post by philinux on 2009-09-22
> **VMC said:**
> "udev" bug was fixed yesterday updates. If you mean the "symlink" errors.

The bootchart I was referring to was yesterdays. Yep fully update now and much less text at startup. :P

---

### Post by Nickedynick on 2009-09-22
Confusingly I now have less messages displayed, but my latest boot time was up to 38 secs :S

---

### Post by hambone79 on 2009-09-22
Just curious (not trying to flame), but why is everybody so concerned with boot times? I rarely reboot my computers (servers are on all the time, laptop/desktop are hibernated) so if it takes 2 minutes to boot versus 10 seconds I really don't care.

Maybe this is strictly an issue with people that dual boot?

---

### Post by Joe_Bishop on 2009-09-22
> **hambone79 said:**
> Maybe this is strictly an issue with people that dual boot?
I think so. It proves only windows users use ubuntu: try it, then tell everything how buggy linux is.

---

### Post by Kazade on 2009-09-22
> **hambone79 said:**
> Just curious (not trying to flame), but why is everybody so concerned with boot times? I rarely reboot my computers (servers are on all the time, laptop/desktop are hibernated) so if it takes 2 minutes to boot versus 10 seconds I really don't care.

Maybe this is strictly an issue with people that dual boot?

Many people don't have the usage habits that you do. I, for example, always switch off my PC when I've finished with it, because I like starting with a fresh desktop with all the updates taken effect and I like saving electricity :) 

I do this at work, on my desktop and on my laptop. Most average users also do the same, I know my Mum wouldn't know what a PC's hibernate function did, she knows that "shut down" turns it off though. Getting the boot down to 10 seconds would be awesome, because there are times I just quickly want to look up something before heading out, or I'm late into work and the quicker I get online the better :)

EDIT: Also, how much better is it to get your Windows/Mac-using friend round to show them the new Ubuntu install, and it start in 10 seconds with a flashy hi-res boot screen. That would piss on their Win 7/Snow Leopard bonfire. :p

---

### Post by VMC on 2009-09-22
I also turn my computer off every time. The only time it stays on for any extended period of time is when I'm downloading.

In fact, the only appliance I continuously leave on is my refrigerator. :)

---

### Post by zika on 2009-09-22
> **VMC said:**
> In fact, the only appliance I continuously leave on is my refrigerator. :)And power amp of course ... Off/On-cycle is a killer for electrical appliances ... If only there was not a thing with mechanical wear I would leave PC on all the times. Wear is worse than killing influence of the Off/On-cycle on electronics of PC ...

---

### Post by Schendje on 2009-09-22
I use my laptop at school a LOT, and it's turned on and off multiple times every day.

A fast boot, for me, is absolutely wonderful.:)

---

### Post by solitaire on 2009-09-22
The boot on my laptop is a bit faster. 29 - 33 seconds in Jaunty.
Down to 23 seconds in today's updated Karmic... ^_^

Resume from "suspend to ram" is about the same between versions (couple of seconds difference)
I think Karmic is a bit quicker to reconnect a wireless connection.

All and all considering it's still  Alpha it quicker (hopefully Beta or release will shave another second or 2 off of boot) ^_^

i only ever shut down the laptop if i'm away for a extended period of time (+4h or more) but I usually just leave it suspended to ram.

---

### Post by KrazyPenguin on 2009-09-22
I was just wondering if the boot was suppose to improve and it looks like the answer is yes, and it appears the super fast boot isn't here yet.

But i don't know what kind of help i am getting when somebody responds that they don't turn their computer off, so it doesn't matter about boot time.

Kind of off topic imho.

thanks

---

### Post by zika on 2009-09-22
> **KrazyPenguin said:**
> Kind of off topic imho.I'm guilty, I was one of the bunch that wrote off topic, I'm sorry. I do stand by my observation that, just today, boot-time decreased significantly ... It's just Alpha, people often say ...
EDIT:Try to use (yes, I know it is not safe and it is a risk) automatic login. It makes boot very fast ...

---

### Post by Compintuit on 2009-09-22
> **zika said:**
> I'm guilty, I was one of the bunch that wrote off topic, I'm sorry. I do stand by my observation that, just today, boot-time decreased significantly ... It's just Alpha, people often say ...
EDIT:Try to use (yes, I know it is not safe and it is a risk) automatic login. It makes boot very fast ...

Login without encryption is useless, afaik. And I don't think ubuntu's encryption is stable enough to trust all my data to. 

Personally, I'll be really, really happy if I can get 20 secs to a desktop, and 25 to a working browser :)

---

### Post by zika on 2009-09-22
> **Compintuit said:**
> Login without encryption is useless, afaik. And I don't think ubuntu's encryption is stable enough to trust all my data to. 

Personally, I'll be really, really happy if I can get 20 secs to a desktop, and 25 to a working browser :)Maybe this is a good time to ask this question, even though it is bluntly off topic: When You say that You would not trust Your data to Ubuntu's login, do You mean that someone with physical access to Your computer could get a hold of Your data or You do not trust it in a way that it is not secure on a network once it is already working ...? I hope I did state my question in a clear enough way ...

---

### Post by Seventh Reign on 2009-09-22
With PC components (namely Fans) being as cheap and easy to replace as they are these days.  2 of my PC's may go 8-10 months without being shut off.  Depending on power outages, and upgrades.

But even I like the thought of Sub 20/15/10 second boot times.

---

### Post by Compintuit on 2009-09-22
> **zika said:**
> Maybe this is a good time to ask this question, even though it is bluntly off topic: When You say that You would not trust Your data to Ubuntu's login, do You mean that someone with physical access to Your computer could get a hold of Your data or You do not trust it in a way that it is not secure on a network once it is already working ...? I hope I did state my question in a clear enough way ...

I have a near 100% faith in ubuntu's network security. Yes, I'm saying that if someone had physical access, the login procedure is useless. If you encrypt with you login, then it is more secure, but as good old xkcd says... [http://xkcd.com/538/]("http://xkcd.com/538/")

And I've added my crappy bootchart as well, for the curious.

---

