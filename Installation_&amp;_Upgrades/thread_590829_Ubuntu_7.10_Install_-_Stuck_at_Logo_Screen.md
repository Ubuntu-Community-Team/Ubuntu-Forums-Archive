---
title: "Ubuntu 7.10 Install - Stuck at Logo Screen"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by war59312 on 2007-10-25
Hi,

Trying to install Ubuntu 7.10 but it fails. It basically just stops at the Ubuntu logo screen with the orange progress bar, bouncing back and forth.

So I enter the cd in my drive and boot of it. I pick to install Ubuntu and then it loads the linux kernel. After this it shows the Ubuntu screen that I just mentioned.

I let it sit there for over half an hour and same thing. Nothing ever happens.

So not a clue to what the problem could be. So where should I begin to find out what is going on?

> Windows XP Pro. SP2
eVGA GeForce 8800 GTS Video Card
AMD Athlon 64 X2 5200+ Windsor 2.6GHz Processor
ASUS M2N-SLI Deluxe MB (Bios: 1203)
CORSAIR CMPSU-620HX 620W Power Supply
Seagate Barracuda 320GB 7200 RPM SATA 3.0Gb/s Hard Drive
Patriot Extreme Performance 2GB (2 x 1GB) DDR2 1200 (PC2 9600) (Model: PDC22G9600ELK) RAM

Thanks,

Will

---

### Post by gtdaqua on 2007-10-25
the ISO image should be burned at low speed (like 24x or less). Not 48x. This happened to me - installation would halt at various stages after restarting it. 

try installing it from another CD - just remember to burn the image at 24x or less.

---

### Post by jenhsun on 2007-10-25
> **war59312 said:**
> Hi,

Trying to install Ubuntu 7.10 but it fails. It basically just stops at the Ubuntu logo screen with the orange progress bar, bouncing back and forth.

So I enter the cd in my drive and boot of it. I pick to install Ubuntu and then it loads the linux kernel. After this it shows the Ubuntu screen that I just mentioned.

I let it sit there for over half an hour and same thing. Nothing ever happens.

So not a clue to what the problem could be. So where should I begin to find out what is going on?



Thanks,

Will

Did you use x386 ISO or X86_64 ISO? 
Try use x86_64 ISO might solve your problem.

---

### Post by fructal_jabolcnik on 2007-10-25
Hello.
I must say that i have the same problem. I also have ASUS M2N32 SLI deluxe(wireless edition) and i have exact same problem with installation. 
First of all: I tried 4 different ubuntu versions. I think it was 6.06 32 bit, 6.06 64 bit(if there was one, becouse i dont remember exactly), 7.04(or one before 7.10) x64 and 32 bit, and finally i tried 7.10 x64. None worked for me. I even tried with kubuntu, but the result was all the same.
second thing: I burned ISOs on CD, DVD and DVD-rw, with different speeds(cd 24x and 16x, DVD 8x and 4x) but "corrupt burn" is not the issue here. I think it has something to do with the MB or something.
thirdly: 32 bit version even showed ubuntu/kubuntu animated loading screen(i think it was a little progress bar beneath the logo), but in x64 versions the screen just went blank and nothing happened afrer that. CTRL,ALT, DEL returned restart. And yeah, the last version caused one of my disks stopped to respond-only afrer power down(if i just restarted it didnt respond-like something was wrong with the sata cable-it took like 10 seconds longer to pass the "detecting ide drives" screen and disk wasn't recongnised) it went back to action, with no problems after that.
SO, does anybody have a solution for my MB? or should I cry and hid onto a tree (look up for some other linux distribution) :(

---

### Post by jenhsun on 2007-10-25
> **fructal_jabolcnik said:**
> Hello.
I must say that i have the same problem. I also have ASUS M2N32 SLI deluxe(wireless edition) and i have exact same problem with installation. 
First of all: I tried 4 different ubuntu versions. I think it was 6.06 32 bit, 6.06 64 bit(if there was one, becouse i dont remember exactly), 7.04(or one before 7.10) x64 and 32 bit, and finally i tried 7.10 x64. None worked for me. I even tried with kubuntu, but the result was all the same.
second thing: I burned ISOs on CD, DVD and DVD-rw, with different speeds(cd 24x and 16x, DVD 8x and 4x) but "corrupt burn" is not the issue here. I think it has something to do with the MB or something.
thirdly: 32 bit version even showed ubuntu/kubuntu animated loading screen(i think it was a little progress bar beneath the logo), but in x64 versions the screen just went blank and nothing happened afrer that. CTRL,ALT, DEL returned restart. And yeah, the last version caused one of my disks stopped to respond-only afrer power down(if i just restarted it didnt respond-like something was wrong with the sata cable-it took like 10 seconds longer to pass the "detecting ide drives" screen and disk wasn't recongnised) it went back to action, with no problems after that.
SO, does anybody have a solution for my MB? or should I cry and hid onto a tree (look up for some other linux distribution) :(

I think it might be your asus motherboard problem. Try to do some research and bios update. Don't overclock it. check connection.
When playing the CD, press ctrl+alt_f1 or f3 to bring up Kernel dialog to see what's wrong inside.

---

### Post by fructal_jabolcnik on 2007-10-25
OK, will do. I found some other topics to the same problem and get a few tips how to solve my problem. If i found the solution, I'll post it here, if i don't I'll just post what the kernel dialog has to say.

Just for the info: I have the latest bios on my MB, connectors are all fine. I'll just downclock it to stock, but I already tried that and it didnt help. Help for the tips
regards

---

### Post by jenhsun on 2007-10-25
> **fructal_jabolcnik said:**
> OK, will do. I found some other topics to the same problem and get a few tips how to solve my problem. If i found the solution, I'll post it here, if i don't I'll just post what the kernel dialog has to say.

Just for the info: I have the latest bios on my MB, connectors are all fine. I'll just downclock it to stock, but I already tried that and it didnt help. Help for the tips
regards

Great. Try to do some search in this forum. Make some posts about your problems and solutions. Help yourself and others. You're in a great Ubuntu community.

Welcome.

---

### Post by war59312 on 2007-10-26
OK indeed it turned out to be a bad mirror, that has since been fixed...

a few files where missing.. Only noticed thanks to jenhsun, had no idea how to bring that window up...

Anyhow, sad to see support for linksys wireless and audigy x-fi cards are not supported out of box.. :( Too bad, so I see why many people still dont use linux... oh well..

Guess I will play around with it in vmware and/or virtual pc instead...

---

### Post by jenhsun on 2007-10-27
> **war59312 said:**
> OK indeed it turned out to be a bad mirror, that has since been fixed...

a few files where missing.. Only noticed thanks to jenhsun, had no idea how to bring that window up...

Anyhow, sad to see support for linksys wireless and audigy x-fi cards are not supported out of box.. :( Too bad, so I see why many people still dont use linux... oh well..

Guess I will play around with it in vmware and/or virtual pc instead...

I think you can wait for this.
[http://kerneltrap.org/mailarchive/linux-kernel/2007/10/24/352404](http://kerneltrap.org/mailarchive/linux-kernel/2007/10/24/352404)

---

### Post by war59312 on 2007-10-28
> In short, we just had an unusually large amount of not just x86 merges, 
but also tons of new drivers (wireless networking stands out, but is by no 
means the only thing - we've got dvb, regular wired network, mmc etc all 
joining in), and a fair amount or architecture stuff, filesystems, 
networking etc too.OK cool, but he does not mention which wireless devices will be supported...

---

### Post by jenhsun on 2007-10-28
> **war59312 said:**
> OK cool, but he does not mention which wireless devices will be supported...

Have you check madwifi.org ?

---

### Post by granz on 2007-10-28
> **jenhsun said:**
> Great. Try to do some search in this forum. Make some posts about your problems and solutions. Help yourself and others. You're in a great Ubuntu community.

Welcome.

I checked the 'unanswered posts' (link at top right of page) and my post is buried at page 385, of unanswered posts starting from 2004.
Not everyone benifits from this 'great Ubuntu community' ..... I wish you all well.
Just don't rely on an answer here.

cheers / Graham

---

### Post by jenhsun on 2007-10-28
> **granz said:**
> I checked the 'unanswered posts' (link at top right of page) and my post is buried at page 385, of unanswered posts starting from 2004.
Not everyone benifits from this 'great Ubuntu community' ..... I wish you all well.
Just don't rely on an answer here.

cheers / Graham

I think this is very wrong, Graham.
When you are in a community (no matter in your real world sociality or internet), you have to try and try again. Post your problems or bump it for getting attention. 
There are several ways to do that....
1. Your interesting title in this thread.
2. You problem's detail. How it arise? Change something wrong?
3. If you get help, then it's time to return to this community.

I bet in the real world you might not have closed friends around you. 
You can forget about the computers, the internet....anything...However, our world is built with human being...the sociality around us. When we got problems, just ask ask and ask in an active, positive way.
You know what, because of this forum, I got a school professor from the other side (NYC) to solve my routers firmware problem. I know his position because of his website and email info. After all, he is a stranger to me. But you never have this kind of impact and grateful to realize and emotional feeling about it.

Anyway, you should open your arms, walk into this community. You won't regret.

---

### Post by granz on 2007-10-28
Over the years I have received many helpful answers from forums,and contributed to help solve any that I felt I could.(time permitting)
BUT ... there are still hundreds of unanswered posts in this forum, and that was my point,and it  is NOT wrong. (go look)
It is being helpful to point this out, as I have seen many examples of frustration ....  yes,do things to improve your chances of a reply. But be aware that all posts are not answered.

---

### Post by jenhsun on 2007-10-28
> **granz said:**
> Over the years I have received many helpful answers from forums,and contributed to help solve any that I felt I could.(time permitting)
BUT ... there are still hundreds of unanswered posts in this forum, and that was my point,and it  is NOT wrong. (go look)
It is being helpful to point this out, as I have seen many examples of frustration ....  yes,do things to improve your chances of a reply. But be aware that all posts are not answered.

We will have unanswered posts of course. This is a community, a free service.
That's why we have launchpad.net.
We don't pay anything for getting help. This is the best part of the linux nature.
By the way, you can get paid service from Canonical. 

Don't rely on others to solve your problem for just some posts from you. You have to do the search in this forum, try to find the similar problem. Look into your application or system documents and help yourself. Then post your result to here and share. This is what this forum all about.

By the way, the world is not perfect because of bad guys/things happened. However, it doesn't mean this world suck.

---

