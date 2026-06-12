---
title: "A bit of hand holding please."
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Adriaan Nikken on 2008-02-06
Hi, I can't seem to get a strait answer form anyone about this issue, so here goes...
My working computer is a hp pavilion zv5000 running ubuntu7.4?
I was given a compaq armada e500. the compaq hard drive is not being read by the compaq. Someone said I could use a network cable to connect the two and wipe the compaq drive, and install ubuntu from my hp. 
I don't know where to look in my hp (applications, places system). I am not a linux jedi. 
I am thinking the bios on the compaq could be quirky, F 12? had worked once to open the bios, but not since the current drive was installed. I had to give the previous one back due to data security issues. The current hard drive is 5 times smaller (6 gigs) but is supposedly form the same period of time if that matters. I did install the hard drive myself, is it possible that I need to connect two of the pins on the male end of the hard drive (master/slave/etc)
So my question in a nutshell...
How do I dump whatever data is on the current compaq drive from my hp using this patchcord, Where do i look? Are there any things I should be careful of? 
If I have not provided enough info it is because I don't know what I need to say, so pleas just ask.
Thank you in advance.
~

---

### Post by osos on 2008-02-06
Have you considered using live-cd?
If there is something to be salvaged you can use the live-cd to mount the harddrive and to set up connection so you can move the files over ethernet or what ever.

---

### Post by WenSes on 2008-02-06
To be honest, I don't know how to use networking cables in Ubuntu, however in the folder system the personal config it's one folder... If you copy that sucessfully you can move all the prsonal info and configs from one pc with ubuntu to another... that folder it's your personal folder.. it's all that I know...

About the cable maybe you should search about how to estabilish a network....

It's all I know...
Good luck

---

### Post by Adriaan Nikken on 2008-02-06
I can't open the bios so a cd is not going to do any good from what I can tell. All I have on the screen is a cursor. the f12? or was it f8 to open the bios does not change anything.
I do see the red compaq logo when it starts up, so I know the bios is in there... I just don't know how to access it. A friend found that on my hp the time to hit the esc to get into the bios is different than any computer he had ever seen. He said it was supposed to be at a very specific point in the boot up. Also how do i track this thread? there is no indication on the forum home page...
Everyone said "get an IBM" did I listen? NNNOOO! 
Was that foolish? YYYYEEEESSSS!

---

### Post by confused57 on 2008-02-06
> **Adriaan Nikken said:**
> I can't open the bios so a cd is not going to do any good from what I can tell. All I have on the screen is a cursor. the f12? or was it f8 to open the bios does not change anything.
I do see the red compaq logo when it starts up, so I know the bios is in there... I just don't know how to access it. A friend found that on my hp the time to hit the esc to get into the bios is different than any computer he had ever seen. He said it was supposed to be at a very specific point in the boot up. Also how do i track this thread? there is no indication on the forum home page...
Everyone said "get an IBM" did I listen? NNNOOO! 
Was that foolish? YYYYEEEESSSS!

Maybe this will work:
[http://hardware.mcse.ms/archive17-2005-1-141272.html](http://hardware.mcse.ms/archive17-2005-1-141272.html)

---

### Post by az on 2008-02-06
> **Adriaan Nikken said:**
> Hi, I can't seem to get a strait answer form anyone about this issue, so here goes...
My working computer is a hp pavilion zv5000 running ubuntu7.4?
I was given a compaq armada e500. the compaq hard drive is not being read by the compaq. Someone said I could use a network cable to connect the two and wipe the compaq drive, and install ubuntu from my hp. 

Straight answer:  No.  The laptop would have to be able to use the drive in order to do anything with it. 

> **Adriaan Nikken said:**
> 
I don't know where to look in my hp (applications, places system). I am not a linux jedi. 
I am thinking the bios on the compaq could be quirky, F 12? had worked once to open the bios, but not since the current drive was installed. I had to give the previous one back due to data security issues. 

It sounds like the drive is causing problems with the BIOS.

> **Adriaan Nikken said:**
> 

The current hard drive is 5 times smaller (6 gigs) but is supposedly form the same period of time if that matters. I did install the hard drive myself, is it possible that I need to connect two of the pins on the male end of the hard drive (master/slave/etc)
~

Look in the laptop's manual.  Usually, a laptop requires that a drive is set to Single (no jumpers) but that may be different.  Also, are you sure the new (smaller) hard disk is working?

---

### Post by Adriaan Nikken on 2008-02-07
Well, still no dice on the bios. I am going to hook up with a linux jedi tomorrow or Friday. This guy may just wipe out Lord Gates. I need to get into the bios to use a live disk because I need to change the boot order to be able to use that live disk. 
I will post here what is done to resolve the issue.
~

---

### Post by Partyboi2 on 2008-02-07
try F10 to get into the compaq bios

---

