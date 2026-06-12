---
title: "High CPU usage"
date: 2008-11-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-11-22
(My Jaunty testing machine)Is any one else seeing the CPU running at or near 100% ?
This has been causing me problems over the past week and it's been causing me to experience the 'pretty blue screen pattern' and then the error comes up about graphics and running 'low graphics mode'. I have to reboot and all is good for awhile until I start to put a little light  work on machine and a repeat happens. I did read in one of the logs that 'CPU usage overload'
Any thoughts on this? Other than that, I have been running Jaunty with out to much drama (had the sound issue, but solved)

---

### Post by ronacc on 2008-11-22
I'm not seeing that here on 64bit jaunty (amd64x2 cpu) , what does top say is using the cpu most ?

---

### Post by DougieFresh4U on 2008-11-22
> **ronacc said:**
> I'm not seeing that here on 64bit jaunty (amd64x2 cpu) , what does top say is using the cpu most ?
Thanks for reply
Please forgive my ignorance, (I have just come home from having back surgery this past week and I amm out of it) but could you provide the code for me to obtain that info?

---

### Post by ronacc on 2008-11-22
in a terminal window type 
```
top
```
and hit return . top ( Table Of Processes) is the terminal equivalent of system monitor , but better , it uses less resources and gives more info .

---

### Post by DougieFresh4U on 2008-11-22
Well that was simple. must be really out, any ways here it is

---

### Post by ronacc on 2008-11-22
do that when the cpu usage is high and it will show you what is using most , I see you use Opera , its my browser also and sometimes operapliginwrapper goes berzerk and eats cpu , see if that may be whats happening , I am going to be away for a couple of hours so my next answer may take awhile .

---

### Post by autocrosser on 2008-11-22
I can second that one--Opera will sometimes go crazy & envelop one of my 4 cpus--

The other place to look is in System>Administration>System Monitor & open the <Processes> tab. You can right-click on a process & <kill> it from there or highlight it & <End Process> with the button at the bottom--See if that helps------

Very handy to stop runaways......

If you are using top you can just open another term & do---  killall opera  <return>

---

### Post by ronacc on 2008-11-22
I have found that when opera starts eating cpu it is (almost) always operapluginwraper and you can kill that without killing opera , and it seeems to have gotten alot better with 64bit flash , I know 2 specific sites that I use that caused it and it was a flash ad on both of them .

---

### Post by autocrosser on 2008-11-22
Good point--I forgot about that--I just generally look for the 100% process & kill it......

---

### Post by DougieFresh4U on 2008-11-22
> **autocrosser said:**
> I can second that one--Opera will sometimes go crazy & envelop one of my 4 cpus

It's worse with Swiftfox & Firefox. They open and the fisrt time i srtike keyboard, it goes 'bonkers' and the 'pretty blue pattern' of death appears

---

### Post by autocrosser on 2008-11-22
You might give Seamonkey a try--I find that it will use the same plugins that Firefox uses, but it "seems" to be a bit more stable...I use Seamonkey 2 testing & it still is a smoother experience......

---

### Post by ronacc on 2008-11-22
I just installed the ppa version of ff3.1 , I don't know about stability yet but it sure seems fast .
@DougieFresh4U what is top telling you is hogging the cpu ?

---

### Post by autocrosser on 2008-11-22
I've been using the testing versions from mozilla.org--they "seem" to work slightly better than the ones we are getting---I took your suggestion & upgraded to testing 3.1b1---You are right!!! It's much faster!!

We'll see how stable it is.......

---

### Post by DougieFresh4U on 2008-11-23
> **ronacc said:**
> I just installed the ppa version of ff3.1 , I don't know about stability yet but it sure seems fast .
@DougieFresh4U what is top telling you is hogging the cpu ?

I thank you for your concern. 
I haven't quite figured it out yet. I am giving a screenshot here showing CPU being 'jumpy' and only 'Opera' is running with the forum page up. The 'Proccess' shows all sleeping. As expected, when I went to 'Manage Attachments' and the little window popped up, I clicked 'browse' and my 'pretty blue pattern n' appeared and I had to reboot. If you have any 'codes' or suggestions I might try, I'd appreciate.
Thanks

---

### Post by ronacc on 2008-11-23
you need to look at your processes to see which is spiking the cpu , I had opera choke on manage attachments a few weeks back but it cleared itself after an update and it didn't take down my system . try disabling plugins in opera and see what happens .

---

### Post by DougieFresh4U on 2008-11-25
I forgot that I had Fluxbox installed so I gave it a shot and using Opera and my 'blue pattern/crashes' have become less frequent. I am hoping that when the .8 kernel is all available ( I only see parts of it in Synaptic) that the problem will resolve itself.
Firefox caused CPU usage to go overboard, but using Fluxbox I was able to use it and have two tabs running, but I'm not gonna tease my machine, and I shall stick with Opera until...

---

### Post by ronacc on 2008-11-25
I do notice that most of the problems I have with Operapluginwraper are caused by certain websites that have embeded flash adds .

---

