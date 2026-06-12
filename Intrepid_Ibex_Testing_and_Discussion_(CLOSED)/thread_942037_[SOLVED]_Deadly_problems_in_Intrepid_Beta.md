---
title: "[SOLVED] Deadly problems in Intrepid Beta"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by inxygnuu on 2008-10-08
Hello, I am using the new Intrepid beta, and I am experiencing some huge problems!:(First, whenever i boot, instead of using the loading bar, it tells me what it is doing and I have to press enter multiple times to get the list going and I have to hold control to keep it going. Second, The network connectivity is terribly unstable:(:(. I have to use a different browser and a different connection program to connect to internet. I am even scared to do anything:(:( so please help me if you will:(:(:(!

---

### Post by knix on 2008-10-08
Say again?
Not trying to be rude, but I don't quite get what your problem is.

---

### Post by bodhi.zazen on 2008-10-08
Why do you think they call it beta ?

---

### Post by inxygnuu on 2008-10-08
It is okay, i did not explain myself that well anyway...
 My problem is that when Ubuntu is starting up, what it does is it will tell me what it is gathering, and I have to hold the control button while it is loading to keep it loading, or it will stop. another loading problem is that I have to press the enter button multiple times to get it started.

My second problem is that m internet connection is wildly unstable. I am connected right now, but the network Icon says I am not, and somehow, after i installed madwifi, it disabled wireless, so i have to use a wired connection...

---

### Post by inxygnuu on 2008-10-08
@bodhi.zazen:

I understand it is a beta, but I am stating my problems to see if I can get any help.:)

---

### Post by inxygnuu on 2008-10-08
anyone???

---

### Post by chrisod on 2008-10-08
Err, by definition an "absolute beginner" should not be mucking around with beta operating systems :) I recommend trying the current stable release of Ubuntu.

---

### Post by kforum on 2008-10-08
so, what happens if you dont press anything, or simply press ctrl once, then stop pressing?

this is a funny bug btw :)

see if in the kernel line you have 'quiet' and 'splash', removing them might help, who knows.(as in, when your choosing the system to boot, press 'e', then press 'e' again in the kernel line, go till the end, then check what i said ;) )
i've never seen anything like you described... why ctrl? why enter?
or is it any input/key?

weird indeed.


cheers

---

### Post by inxygnuu on 2008-10-08
> **chrisod said:**
> Err, by definition an "absolute beginner" should not be mucking around with beta operating systems :) I recommend trying the current stable release of Ubuntu.

I would not call myself an "_absolute_beginner" but the description said that it came with better hardware support, and I need to gain more knowledge if I want to be able to work in the computer industry.:)

---

### Post by inxygnuu on 2008-10-08
for the list to keep going, eneter will pause it, and I dont know why:lolflag:

---

### Post by caryb on 2008-10-08
You don't think the term Deadly might be a tad melodramatic? I opened this post thinking we had another Intel hardware type scenario again.


Cary

---

### Post by kforum on 2008-10-08
> **inxygnuu said:**
> I would not call myself an "_absolute_beginner" but the description said that it came with better hardware support, and I need to gain more knowledge if I want to be able to work in the computer industry.:)

so um... did my suggestion help you any bit?

and also, if you really wanna learn about linux/your pc then i'd suggest trying out gentoo, it will take a while for you to be able to use it, but the path to functionality will teach you a great many things. ^^


cheers.

---

### Post by inxygnuu on 2008-10-08
How compatible is it? I need something that will get me wirelessly online:)
Please also understand that I am very young, so I can't do very much...:(

---

### Post by inxygnuu on 2008-10-08
Just checked it out! thanks!:):popcorn:! Can you give me a little information about it now?

---

### Post by Nullack on 2008-10-08
> **caryb said:**
> You don't think the term Deadly might be a tad melodramatic? 

Yeah.

Its disappointing to see new people coming here since the beta was released with posts about how Ubuntu Intrepid Beta killed their pet and destroyed the world.

What clearly is lacking is any form of *basic* debugging by most of these people. It doesnt take much to have a look at the wiki sections on debugging and the many topics for how to effectively contribute to Ubuntu.

The most effective way to make a difference in FOSS projects is to do some work yourself - you dont need to be a developer at all. That gets results.

---

### Post by inxygnuu on 2008-10-09
why is everyone yelling at me? I thought Ubuntu was about "humanity towards others" not "yelling at otthers when they need your help" that is why I posted my problems here.

---

### Post by philinux on 2008-10-09
Ok boot up and make sure you do all the updates.

sudo apt-get update && sudo apt-get upgrade

Then reboot.

---

### Post by Ub1476 on 2008-10-09
Do you have an atheros wireless card? You can check by typing "lspci" into the terminal. 

If so, they are currently unstable, and some don't work at all (like mine). It will be fixed for the final release though, so don't worry. I suggest you search launchpad.net for your problem percisting at boot, and fill a bug if there's not one there already.

---

### Post by bash on 2008-10-09
You know a bit more information about your problem would be nice. Just coz we are here doesn't mean Mark has come by and touched all our foreheads and now we have super-fancy-power(tm) and can just magically guess what your problem is from you saying you have to hold down your CTRL key. That said quite a few posts in here do not fall in the particularly helpful category.

So for the first problem: What error do you receive when it does not continue to boot? That would help quite a bit. 

For the networking problem. You mention both wireless and wired? What do use when normally? With what connection does the problem occur? Wired? Wireless? If wireless what card do you have? What exactly happens? You say madwifi? Why do you install extra software? Normally networkmanager should handle all network connections, so why did you install extra software? Did networkmanager not work. And so on?

And even if you answer all those question, there is a chance we will not be able to solve your problem. That is the risk of TESTING BETA software.

---

### Post by inxygnuu on 2008-10-09
Yes i have an atheros, and I installed extra softwre because it would not configure. I wnt to use wireless, i normally used a wired connection, and now it is not even saying I have a connection. There is no error when I stop holding control, it just stops.

---

### Post by inxygnuu on 2008-10-09
You guys can stop bickering at me now:) I have dual boot
1. Ubuntu
2. Ubuntu
:lolflag:

(the first one is intrepid and the second is Hardy)

---

### Post by caryb on 2008-10-09
Sorry If you thought I was yelling at you, Congrats on having the dual boot, It is the best way to go! You have 2 options when Intrepid is released 1) Use the intrepid partition as your primary & start attacking the Hardy or vice versa.


My little rant was more at the choice of topic name, it really doesn't reflect the issue.


Sorry Cary

---

### Post by cariboo on 2008-10-09
We can help you, but you have to give us a lot more information. THe first thing you should learn if you want to be part of the computer industry, is to give us enough information to allow us to help you solve the problem. 

1. The first thing is where does the bootup stop when you just let it run

2. Next is how long do you wait before hitting any keys. 

3. Next is to list your hardware using either:

```
lspci
```

or

```
sudo lshw
```

Both of the above commands have to be run in a Applications-->Accessories-->Terminal. Paste the output of either command in your next post.

And next time use a better title, like caryb, I though it was something like the e1000e bug and there was more hardware that being rendered unusable.

Jim

---

### Post by happyhamster on 2008-10-10
The bootup problems could be related to:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271099)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254668](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254668)

No solution yet, but at least you're not alone...

---

### Post by inxygnuu on 2008-10-10
Now I have Dual Vista and Ubuntu Intrepid (don't know what happened to Hardy) and everything is smooth:guitar:8-)8-)! Although I can say, Windows XP (or as i call it, windows X-treme Problem:lolflag:) because it is horrible when connecting to a network!:mad: It is even worse than Ubuntu's (not to offend Ubuntu)

---

### Post by inxygnuu on 2008-10-11
Oh and also, compared to Vista, XP Sucks!! (no offense to XP users)

---

### Post by inxygnuu on 2008-10-11
Does anyone know how to completely re-install Intrepid? mine is corrupted so bad that I just want to reinstall it to the same partition after it comes out.:)

---

