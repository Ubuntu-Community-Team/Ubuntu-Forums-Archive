---
title: "Ubuntu 7.10 VERY slow"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by coll_1 on 2007-10-24
Hi everyone,

I have a Toshiba a100-042 dual processor 2 GB ram and video card Intel 945gm

Before now i have had ubuntu 7.04 with beryl and theme OSX and it was working VERY GOOD!! Cube effects and every-things else....

Yesterday I upgraded to7.10 and I found the PC that is slow to work just installed (without compiz installed) using mozzilla me takes the screen shake when the web page ...

I tried to install compiz and is a disaster!

The cube works quite well but when I move windows it's sucks it's like an old 486! ! ! !

Can somebody help me? ?:(

---

### Post by stueyboy on 2007-10-24
I have suffered the same kind of thing with studio 7.10. Rather than try to pin down what the issue was, I have just re-installed 7.04 and I will wait a while until some general fixes come around.

---

### Post by thered on 2007-10-24
I was going to start a new topic so might be a little off-topic.

I installed ubuntu a few days ago.  First time Ubuntu user, but have used a few versions of linux. 

I'm finding browsing very slow.  I dual boot with Vista (spit) and the difference in using firefox in M$oft and firefox in Ubuntu on the same machine is very noticeable.

Machine is Dell Inspiron -256 graphics 2gig ram duocore.

For an example if I load a page of google images - the thumbnails take a while to load.

It's bordering on the unacceptable at times.:(

Overall - I'm happy with version 7.10, I need to be, it is the first distro that would install on my machine so don't have the option of 'going back'.

---

### Post by jkeyes0 on 2007-10-24
> **thered said:**
> I was going to start a new topic so might be a little off-topic.

I installed ubuntu a few days ago.  First time Ubuntu user, but have used a few versions of linux. 

I'm finding browsing very slow.  I dual boot with Vista (spit) and the difference in using firefox in M$oft and firefox in Ubuntu on the same machine is very noticeable.

Machine is Dell Inspiron -256 graphics 2gig ram duocore.

For an example if I load a page of google images - the thumbnails take a while to load.

It's bordering on the unacceptable at times.:(

Overall - I'm happy with version 7.10, I need to be, it is the first distro that would install on my machine so don't have the option of 'going back'.

As far as your problem, thered, you may need to go into firefox and disable IPv6. To do this, open the browser, and in the address bar, type in "about:config" and hit enter. In the main window, search for IPv6, and change the "disable IPv6" from false to true. Restart firefox and see if that makes a difference.

coll_1: have you tried opening system monitor while the system is running slowly, or running top in a terminal to see what's actually clogging things up? Right after I upgraded, I noticed mplayer was running 2 instances for some reason, and eating up the CPU. I killed it, and everything started moving smoothly. Not saying that's what's happening to you, but it could be trackerd or something.

---

### Post by jenhsun on 2007-10-24
I think you can disable the tracker, beagle search in your system/preference/sessions
If you don't need desktop visual effect, change system/preference/appearance/Visual Effect  to none.

Anyway, if I get more performance improvement tweak, I will post again.

---

### Post by thered on 2007-10-24
jkeye0: That does seem to have improved matters.  Will monitor over next few days - thanks for prompt reply.

R.

---

### Post by jenhsun on 2007-10-24
> **jkeyes0 said:**
> As far as your problem, thered, you may need to go into firefox and disable IPv6. To do this, open the browser, and in the address bar, type in "about:config" and hit enter. In the main window, search for IPv6, and change the "disable IPv6" from false to true. Restart firefox and see if that makes a difference.

coll_1: have you tried opening system monitor while the system is running slowly, or running top in a terminal to see what's actually clogging things up? Right after I upgraded, I noticed mplayer was running 2 instances for some reason, and eating up the CPU. I killed it, and everything started moving smoothly. Not saying that's what's happening to you, but it could be trackerd or something.

About the firefox tweak, you can about:config to search network.http.pipeling.maxrequests
change to 10. You might feel a little improve.

---

### Post by thered on 2007-10-24
Thanks for those too, jenhsun

---

### Post by Ced22 on 2007-10-24
I have a similar experience. The upgrade went very well, everything was working, then i wanted to try out the Desktop effects. So I installed the xserver-xgl package, rebooted and I had cool effects. But slowly I noticed the system getting slower and slower over some days. So in the end it was so slow I removed xserver-xgl again and used the normal one. But it did not get better!

I have a ATI Radeon 9600 and upgraded from 7.04 to 7.10, i'm using the restricted drivers.

The symptoms are: Awful lag in the gnome desktop (all programs, including firefox). Sometimes when I switch between apps (ALT-TAB), it takes 5 seconds. When I enter text in a text field such as in this forum, letters take 2 seconds to appear.. Minimizing, maximizing, etc.. It's hell on earth. Before the upgrade I had a very responsive system.
There is no program clogging my RAM. 

I have no idea what happened or if it is related to my desktop effects adventure? Propably not. But what else? Thanks for any hints!

---

### Post by jenhsun on 2007-10-24
> **Ced22 said:**
> I have a similar experience. The upgrade went very well, everything was working, then i wanted to try out the Desktop effects. So I installed the xserver-xgl package, rebooted and I had cool effects. But slowly I noticed the system getting slower and slower over some days. So in the end it was so slow I removed xserver-xgl again and used the normal one. But it did not get better!

I have a ATI Radeon 9600 and upgraded from 7.04 to 7.10, i'm using the restricted drivers.

The symptoms are: Awful lag in the gnome desktop (all programs, including firefox). Sometimes when I switch between apps (ALT-TAB), it takes 5 seconds. When I enter text in a text field such as in this forum, letters take 2 seconds to appear.. Minimizing, maximizing, etc.. It's hell on earth. Before the upgrade I had a very responsive system.
There is no program clogging my RAM. 

I have no idea what happened or if it is related to my desktop effects adventure? Propably not. But what else? Thanks for any hints!

Check this guy's blog
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Ced22 on 2007-10-24
> **jenhsun said:**
> Check this guy's blog
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Thanks for the link, but actually I think the problem lies somewhere else: I just noticed I have a very high load on the CPU, almost constant 100%.
I have the following applications running: Pidgin, Rhythmbox, Google Mail notifier, X-Chat, Firefox, KTorrent. So I first shut down trackerd, then KTorrent and Firefox. The CPU usage dropped down 10-20%. I opened some applications again, it was at 100% again. (I did not reopen firefox).

So apparently my system has suddenly a lot less power than before the update.. I don't understand at all.

---

### Post by jenhsun on 2007-10-24
> **Ced22 said:**
> Thanks for the link, but actually I think the problem lies somewhere else: I just noticed I have a very high load on the CPU, almost constant 100%.
I have the following applications running: Pidgin, Rhythmbox, Google Mail notifier, X-Chat, Firefox, KTorrent. So I first shut down trackerd, then KTorrent and Firefox. The CPU usage dropped down 10-20%. I opened some applications again, it was at 100% again. (I did not reopen firefox).

So apparently my system has suddenly a lot less power than before the update.. I don't understand at all.

You use Gnome, right?
You can try Deluge Bittorrent to replace KTorrent for performance and the native look in Gnome.
No matter what, If I were you, I will backup my data and do a clean installation. I hate upgrading because I can't figure out which version problem between. By the way, I am OK to do the harddisc format, Data organize and backup per 6 months.

By the way, check out this thread
[http://ubuntuforums.org/showthread.php?t=586072](http://ubuntuforums.org/showthread.php?t=586072)
It could speed up the booting. I confirm about that.

---

### Post by Gouz on 2007-10-24
Hey everyone I think 7.10 

but I have a problem with Firefox as I can see others have some as well..
Well I check the post and I didn't found anything like what I am experiencing.
for me FF is very slow on loading pages and also it hungs/crashes all the time
and when I minimize and then I maximize the window I can still see my wallpaper.. well it is cute on but I don't to see it from FF :(

and when the ff is running if I open something else I and then I close it I can still see it in the window for firefox, and also if I open more that one browser window then I have to force quit them both same goes for more that 5 tabs in the same browser.
and it is not RAM or CPU cause I am using something like 2% from my CPU and 40% of the RAM

any ideas....?
thanks

Ps I have uploaded a prtSc so you can get a better idea

---

### Post by Ced22 on 2007-10-25
Ah, jenhsun, you may be right about re-installing fresh. God damnit, I think every single upgrade with Ubuntu I had to reinstall because some stuff was not working, and I don't hack around, I just install software with Synaptic!! I thought the update from 7.04 to 7.10 would finally work, because everything seemed to be allright! But apparently it's just not possible to upgrade smoothly. Arrrrrgh. So I'm gonna reinstall. Or at least try with a new user for a second, maybe that helps...

Btw, Gouz, I experience very similar things...

---

### Post by jsonder on 2007-10-25
One option is to download Mint 3.1 (based upon Feisty).  

I've pretty much done that to deal with the slowdown.  

It also seems like dns info is really slow under 7.10.

---

### Post by Gouz on 2007-10-25
Ok.. i have tried to change DNS and it help a bit I changed IPv6 from False to True and it also helped.. but it is not fix.. I would say far from fix.
And I have the same problem with an other browser I can't recall the name right now and I removed it cause I got pissed heh

I want to know if the problem will be fixed if I reinstall the 7.10 from the Live disk or not. cause I dont want to do yet an other format.. ;)
 or at least if someone has the way to work around it pls tell me :P
I will try few things that I found on the net and I will keep you updated.

---

### Post by Ced22 on 2007-10-26
I just reinstalled and everything works fine now, I believe.
To me, a reinstall is a quick thing: I have a separate /home and data-partition, so it takes me around 1h to do the whole thing basically. Can live with that, but it's still very annoying..

---

### Post by marinos on 2007-11-11
Ced22, is your situation still OK after the fresh 7.10 install?  My experience
with 7.10 almost parallels yours, but I have no time to tweak everything
after a fresh install.  So, I simply gave up and replaced 7.10 with an image
of my perfectly working 7.04 (image taken/restord using the excellent o.s.
"partimage" utility after booting with a RescueCD.)  One would be tempted 
to believe that a fresh installation of 7.10 will alleviate all these problems, 
but as I've read in another thread regarding the dreaded Firefox high-CPU 
problem, there's no guarantee.  So please tell us if your fresh 7.10 installation 
is still working fine now, two weeks after your last post in this thread.

---

### Post by ricoo25 on 2007-12-06
> **coll_1 said:**
> Hi everyone,

I have a Toshiba a100-042 dual processor 2 GB ram and video card Intel 945gm

Before now i have had ubuntu 7.04 with beryl and theme OSX and it was working VERY GOOD!! Cube effects and every-things else....

Yesterday I upgraded to7.10 and I found the PC that is slow to work just installed (without compiz installed) using mozzilla me takes the screen shake when the web page ...

I tried to install compiz and is a disaster!

The cube works quite well but when I move windows it's sucks it's like an old 486! ! ! !

Can somebody help me? ?:(

I have the same problem here. It happened immediately after I installed compiz. When I move windows around...very slow! Anyway, I found that when I enable "water" (shift + F9), the windows move normally again. As soon as I disable "water", The problem comes back after about 30 seconds. 
Has anyone come across this problem and found a fix?
I have the same video card as him. I don't think that it's the card though...
Any help would be greatly appreciated

---

