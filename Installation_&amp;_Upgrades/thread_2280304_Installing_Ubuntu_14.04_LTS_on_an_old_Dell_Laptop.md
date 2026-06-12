---
title: "Installing Ubuntu 14.04 LTS on an old Dell Laptop"
date: 2015-05-29
forum: Installation &amp; Upgrades
---

### Post by rbmoler on 2015-05-29
I'm in the process of trying to load 14.04 LTS (32bit) onto an old Dell **Latitude **D610 laptop.  It has a 40 GB HD.  The installation seemed to be going fine until close to the end, but stalled with the following:

*configuring bcmwl-kernel-source-(i386*).

That probably means something significant, but I'm not knowledgeable enough to know what.

---

### Post by kerry_s on 2015-05-29
that's the firmware drivers for your wireless. you are connected to the internet while installing right ?

---

### Post by RobGoss on 2015-05-29
Hello and welcome,

What are the specs for your machine this will anyone that's trying to help you get better results.

How are you installing your Ubuntu distribution, DVD or USB and how did you create it?

One of the biggest things I see with people trying to install Ubuntu 14.04 LTS is not having enough ram or a older graphic card.

If you would have said you have a newer machine I would have advised that maybe your installation device might not be created correctly.

As **Kerry_s**, mentioned you should always be connected to the internet when Installing a fresh installation of Ubuntu or other Linux distributions because this will allow you to download all the latest updates and packages.

---

### Post by rbmoler on 2015-05-29
The machine is not mine, but one a friend bought at a yard sale while vacationing in Florida.  I had downloaded the 32 bit version 14.04 a from the Ubuntu site and put it on a DVD a year ago.  I did the same for the 64 bit AMD version which I installed on two different machines in my house.  

I could not find the way to have the machine tell me how much RAM it has.  That could certainly be a problem.

The graphic card seems to be OK.  He ran Ubuntu in test mode from the DVD.

My friend misunderstood the warning that his machine was "now disconnected from the internet."  I remedied that by connecting him to my home system via cable.  So the installation should be up to date.  At least Ubuntu acknowledged that there was a connection and the updates button was activated.

Unfortunately there is no manual with this old Dell,  I can probably find out some information about it.

I'm no expert, so it's OK to tell me what I should be doing and why.  I try to follow along.

---

### Post by chris389 on 2015-05-29
I am trying to install LXLE over Ubuntu 8.4 on the same machine. The old Dell D610. I did upgrade my RAM so took a look at the old RAM I pulled out of the machine and it is 512 if that is any help. It only had the one stick. It was working when pulled. Some one gifted me two sticks of I think 1024? If you want the one stick I would be happy to pass it on to you to up your RAM. One stick is easy to replace and the second one is under the keyboard. I managed the replacement and I am a total non geek.

Chris

---

### Post by RobGoss on 2015-05-29
> **rbmoler said:**
> The machine is not mine, but one a friend bought at a yard sale while vacationing in Florida.  I had downloaded the 32 bit version 14.04 a from the Ubuntu site and put it on a DVD a year ago.  I did the same for the 64 bit AMD version which I installed on two different machines in my house.  

I could not find the way to have the machine tell me how much RAM it has.  That could certainly be a problem.

The graphic card seems to be OK.  He ran Ubuntu in test mode from the DVD.

My friend misunderstood the warning that his machine was "now disconnected from the internet."  I remedied that by connecting him to my home system via cable.  So the installation should be up to date.  At least Ubuntu acknowledged that there was a connection and the updates button was activated.

Unfortunately there is no manual with this old Dell,  I can probably find out some information about it.

I'm no expert, so it's OK to tell me what I should be doing and why.  I try to follow along.


Open system info:

[COLOR=#333333][FONT=Ubuntu]This can be done either in the dash, or by going to the gear icon (top right), opening [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]System Settings[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu], and opening [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]System Info[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

---

