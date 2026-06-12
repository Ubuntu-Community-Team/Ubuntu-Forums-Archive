---
title: "Could someone tell me how to install Karmic Koala Pre-Alpha?"
date: 2009-05-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by charleskw on 2009-05-05
I would like to do this without manually changing all of the sources in the sourcelist to karmic.

---

### Post by super.rad on 2009-05-05
as far as i know, thats the only way until alpha 1 is released

---

### Post by Keithhed on 2009-05-05
I don't mean to sound harsh, but if you have to ask then you should wait until the Alpha.  :)

---

### Post by miwaypet on 2009-05-05
Changing the source list is easy. CTRL+F , then type jaunty in the search box. Replace jaunty with karmic. You do not have to change the cd names, it is commented out.

If you are new to all this, be careful.

---

### Post by gjoellee on 2009-05-06
> **miwaypet said:**
> Changing the source list is easy. CTRL+F , then type jaunty in the search box. Replace jaunty with karmic. You do not have to change the cd names, it is commented out.

If you are new to all this, be careful.

Just if you don't know where the sources.list, this is the path: /etc/apt/sources.list

---

### Post by Ani on 2009-05-06
> **Keithhed said:**
> I don't mean to sound harsh, but if you have to ask then you should wait until the Alpha.  :)

Keithhed, do you know the answer to charleskw's question?

---

### Post by Starks on 2009-05-06
Ani, charleskw is asking for the impossible right now.

---

### Post by calc on 2009-05-06
> **charleskw said:**
> I would like to do this without manually changing all of the sources in the sourcelist to karmic.

As I understand it the daily-live ISOs being generated now are actually karmic although the scripts haven't been updated to say karmic yet.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Though there are still bugs in the livefs generation so you should probably hold off until the announcement of alpha 1 like the others have said.

---

### Post by Ani on 2009-05-06
> **Starks said:**
> Ani, charleskw is asking for the impossible right now.

Starks, I know that it is impossible. But instead of explaining to charleskw that it is impossible, Keithhed, implied that it is possible but 'if you have to ask then you should wait until the Alpha.'

Wouldn't it be easier to just say that right now changing the source files is the only way?

What's up with "I don't mean to sound harsh"?

---

### Post by Ani on 2009-05-06
> **calc said:**
> As I understand it the daily-live ISOs being generated now are actually karmic although the scripts haven't been updated to say karmic yet.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Though there are still bugs in the livefs generation so you should probably hold off until the announcement of alpha 1 like the others have said.

I booted into May 6th ISO, and it was plain jaunty, not karmic at all.

---

### Post by calc on 2009-05-06
> **Ani said:**
> I booted into May 6th ISO, and it was plain jaunty, not karmic at all.

That is due to the livefs generation failure, once that is fixed it will be karmic images... though that might not happen until closer to the alpha 1 release as I already noted in my previous post.

---

### Post by gnomeuser on 2009-05-06
> **Starks said:**
> Ani, charleskw is asking for the impossible right now.

Agreed, if he is unwilling (or unable) to do the change manually - the chance of getting himself into trouble at the current stage of koala is quite high and then it is perfectly legitimate to say no to helping. The first alpha release is not that far away and then there will be a LiveCD for him to try out hopefully and if he so feels upgrade his system from.

It is like going to an amusement park and being told "you must be at least this tall to get on this ride", well when it comes to development software, especially when extended to your whole OS, you have to be willing to learn certain things and take certain risks. If you are not, chances are you will end up ruining your setup or taking up important time to have simple problems explained which could be used tracking down more serious issues.

It is not that testing isn't welcome, in fact it is very welcome but it needs to be understood that it comes at a risk and a certain level of commitment to working on issues.

---

### Post by ronacc on 2009-05-07
I agree completely , all who wish to test are welcome but if they lack even the skill or motivation to use S&R in gedit they shouldn't be running dev software .

---

### Post by autocrosser on 2009-05-07
AGREED!!!  I've been doing this for 4 years now & the early learning curve was "rather" steep---and I had been doing testing work for well on 10+ years before that.........

---

### Post by autocrosser on 2009-05-07
> **calc said:**
> That is due to the livefs generation failure, once that is fixed it will be karmic images... though that might not happen until closer to the alpha 1 release as I already noted in my previous post.


Good to see you here Calc!!!!!  How goes the OOo stuff?

---

### Post by Ani on 2009-05-07
> **ronacc said:**
> I agree completely , all who wish to test are welcome but if they lack even the skill or motivation to use S&R in gedit they shouldn't be running dev software .
So how much skill does one need to replace the word "jaunty" with "karmic"?

Why are you assuming that it is necessarily a lack of skill?

It could be that he simply does not want to waste so much of his time on installing jaunty and then dist-upgrading it to karmic, if he can just boot into Karmic liveCD in a matter of seconds and just do the testing that way.

---

### Post by ronacc on 2009-05-07
> **Ani said:**
> So how much skill does one need to replace the word "jaunty" with "karmic"?

Why are you assuming that it is necessarily a lack of skill?

It could be that he simply does not want to waste so much of his time on installing jaunty and then dist-upgrading it to karmic, if he can just boot into Karmic liveCD in a matter of seconds and just do the testing that way.

It doesn't require much skill at all , hence someone lacking even that level of skill should not be running a dev version where problems are routine and expected .  and If the reason is that " he does not want to waste his time " he lacks the motivation .

---

### Post by Gina on 2009-05-08
I quite agree.  That says it all.

---

### Post by taavikko on 2009-05-08
> **ronacc said:**
> It doesn't require much skill at all , hence someone lacking even that level of skill should not be running a dev version where problems are routine and expected .  and If the reason is that " he does not want to waste his time " he lacks the motivation .

Well put, just want to chime in and say that dev-versions shouldn't be used only to have the newest and shiniest software available.

Reasoning behind this is that during this 6 month cycle, testers help out to find out the bugs, and inform and/or try to solve the issue, so finally during official release, the end-user, (the ones who lack the basic-skills and motivation) would have the finest release possible, do you agree...

If you don't have the time or lack the interest to comply to the above, please don't bother to use dev-versions. Is roughly the same than riding a taxi, but you don't have the money to pay the fair.

Information of upgrade procedures are documented in ubuntu's wiki pages, and in forums numerous times, Some form of self-learning is a must.

Before this thread goes to downward spiral, it should be closed, and just serve it's purpose as a reminder that community (hardcore testers) looks down on lazy people ;)

---

### Post by freeman2000 on 2009-05-10
I'm a real noob here, and I'm not going to attack or defend anyone. I can state though that there is definitely an easier way to get Karmic than what was stated here, but from the tome of the messages here I won't print it.   

I've been running Linux & Ubuntu for less than a month. On my first Linux day I loaded Intrepid from a Live CD. Everything worked! Dang, where's the challenge? So on day 2, I downloaded & installed Jaunty Beta. By golly, other than a proprietary driver for my graphics card, everything worked flawlessly. Therefore, I am once again seeking a mental challenge. So with less than 1 month Linux/Ubuntu experience, I took the plunge 2 days ago and downloaded/installed Karmic (Pre) Alpha, all 595 packages and 420mb of it.  Even though I've only run it 2 days, there's still no challenge - it too just runs flawlessly! It still looks like Jaunty though.  

I understand fully that there are risks involved with software like this, but that's part of the challenge.  It also can give the developers a new set of eyes to have a non-computer-geek newbie involved.  Maybe I'll just go back to Windows for a challenge as MS always breaks. Good luck.

---

### Post by davideotape on 2009-05-10
> I understand fully that there are risks involved with software like this, but that's part of the challenge.

I totally agree with that. I was in exactly the same situation as you about five months ago, and decided to take the plunge and upgrade to jaunty alpha 2. Because I keep regular backups in at least 3 separate places, and have a backup computer it wouldn't really have mattered if the alpha broke my computer, so I thought "Why not?" Now, five months on, I would never have the knowledge or experience I have if I hadn't tried out the development release. I honestly think it is one of the best ways for new linux users to become acquainted with the new OS. It was also great to see the progressions and changes being made to Jaunty every day.

> It also can give the developers a new set of eyes to have a non-computer-geek newbie involved

That's a very good point. Different viewpoints are needed to make sure that the software is doing what it's meant to be doing.

> Even though I've only run it 2 days, there's still no challenge - it too just runs flawlessly! It still looks like Jaunty though.

I think that's because software developers haven't got round to uploading they're newest packages yet. Also remember that UDS is coming up, where some big decisions will be made on the direction that karmic will be taking.

---

### Post by ronacc on 2009-05-10
@ freeman2000  welcome aboard , We do not look down at noobs here , as far as the challange goes , wait , the ball hasn't started rolling good yet, things will break .

---

### Post by davideotape on 2009-05-10
> **ronacc said:**
>  the ball hasn't started rolling good yet, things will break .

They most certainly will :guitar:

---

### Post by freeman2000 on 2009-05-10
Sounds like I'll learn quite a bit then.  I'm looking forward to the challenge!  Whatever I can do to help.

---

### Post by nanog on 2009-05-10
if you want a **REAL** challenge just remove all ubuntu repos, add this:

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) experimental main contrib non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) experimental main

and run

sudo apt-get dist-upgrade

---

### Post by novafluxx on 2009-05-11
> **taavikko said:**
> 
*SNIP*
If you don't have the time or lack the interest to comply to the above, please don't bother to use dev-versions. Is roughly the same than riding a taxi, but you don't have the money to pay the fair.
*SNIP*

Whats this "freedom" I hear about in this community, oh and the wonderful community support? Seems to be lacking slightly hmmm :(

If we want to use the dev versions, we will. Thanks.

What does a Taxi cab have to do with anything?

---

### Post by 23meg on 2009-05-11
> **Ani]Why are you assuming that it is necessarily a lack of skill?

It could be that he simply does not want to waste so much of his time on installing jaunty and then dist-upgrading it to karmic, if he can just boot into Karmic liveCD in a matter of seconds and just do the testing that way.[/QUOTE]

Good point, but the original post would have been more clear and easier to help if the poster simply said so. 

[QUOTE=nanog said:**
> if you want a **REAL** challenge just remove all ubuntu repos, add this:

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) experimental main contrib non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) experimental main

and run

sudo apt-get dist-upgrade

And render your system useless for contributing to Ubuntu through testing. 

If you do this, or similar uncontrolled "for the sake of it" experiments outside the Ubuntu repositories with your installation of Karmic, please refrain from reporting bugs in the Ubuntu bug tracker.

[QUOTE=novafluxx]Whats this "freedom" I hear about in this community, oh and the wonderful community support? Seems to be lacking slightly hmmm :(
[/QUOTE]

This:

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

Nobody is violating another's above freedoms here (they're merely recommending against certain practices in good spirit), and the support the original poster wanted has been provided. 

[QUOTE=novafluxx]If we want to use the dev versions, we will. Thanks.[/QUOTE]

Surely, and if people want to recommend against the use of said versions in certain cases and in certain ways, they will. There's place for both acts to coexist peacefully in conflict.

---

### Post by netwarriorwy on 2009-05-12
I Everyone!

I'm pretty much new in this Ubuntu world. 8 months using it (since Hardy Heron) and 5 months since leaving Windoze and using it in a VirtualBox XD ... but i want to help testing Karmic.

Do I need to make a partition to install Jaunty and change the sources to Karmic or I can do it using VirtualBox. Because I have both my desktop and laptop with Jaunty right now. I'm pretty much like freeman2000 just with a little bit of experience in this world and willing to help as much as I can. 

I hope you can help me on this

---

### Post by davideotape on 2009-05-12
> **netwarriorwy said:**
> I Everyone!

I'm pretty much new in this Ubuntu world. 8months using it and 5 months since leaving Windoze and using it in a VirtualBox XD ... but i want to help test Karmic.

Do I need to make a partition to install Jaunty and change the sources to Karmic or I can do it using VirtualBox. Because I have both my desktop and laptop with Jaunty right now. 

I hope you can help me on this



You need to start off with a jaunty installation either way. It doesn't matter whether on a virtual system or normal install, but I'd reccomend virtual install just incase anything big breaks (as hal did yesterday) Then, just change all of your jaunty 's to karmic 's in /etc/apt/sources.list Be warned that 9.10 will be very unstable until it reaches it's final release, it's not advised to use it pre-release. It's your own choice though :D

Happy testing :D

---

### Post by netwarriorwy on 2009-05-12
What would be the worst thing that can happen to my host Jaunty running a Karmic guest??? 

If I'm not gonna loose my files and configurations I'd be ok with me XD.

I wanna be part of this journey too.:guitar:

---

### Post by Starks on 2009-05-12
> **nanog said:**
> if you want a **REAL** challenge just remove all ubuntu repos, add this:

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) experimental main contrib non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) experimental main

and run

sudo apt-get dist-upgrade
Using the Sid and Experimental repos may be more cutting edge than Karmic, but it does break a lot of things, namely grub.

---

### Post by davideotape on 2009-05-12
> **netwarriorwy said:**
> What would be the worst thing that can happen to my host Jaunty running a Karmic guest??? 

If I'm not gonna loose my files and configurations I'd be ok with me XD.

I wanna be part of this journey too.:guitar:

I should think it's highly unlikely that your host system will be affected at all, but I don't know a great deal about virtualisation so I'm not 100% sure. Then again, since it's a development release, anything could happen theoretically. You have been warned...

---

### Post by cecilpierce on 2009-05-13
pre-alpha
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
alpha 1 maybe may 14 !

---

### Post by jerrylamos on 2009-05-13
Karmic daily build is there, May 13, however I think the iso incomplete.  It booted to "initramfs" then stopped.  It's only 664.3 mb; I expected oversize at first....more (bugs) to come....

Jerry

---

### Post by cecilpierce on 2009-05-13
jerrylamos, glad you posted that, i was just thinking about d/l it. i'm runing low on cd's !
thanks

---

### Post by zika on 2009-05-13
> **jerrylamos said:**
> Karmic daily build is there, May 13, however I think the iso incomplete.  It booted to "initramfs" then stopped.  It's only 664.3 mb; I expected oversize at first....more (bugs) to come....

Jerry
same here. I did not know what to do on initramfs prompt ... :) any hints ... ?

---

