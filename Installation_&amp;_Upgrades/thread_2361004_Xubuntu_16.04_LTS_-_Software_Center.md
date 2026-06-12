---
title: "Xubuntu 16.04 LTS - Software Center"
date: 2017-05-10
forum: Installation &amp; Upgrades
---

### Post by ubu112 on 2017-05-10
Please,I'm new with Xubuntu and I used Ubuntu before.

I'd like to know if,in Xubuntu, there is a Software Center,to find something new with descriptions.

Thank you

---

### Post by Autodave on 2017-05-10
Yes there is. Click on the mouse icon on top left of screen: it will be there in the menu that first appears. It is just named "Software".

---

### Post by Bucky Ball on 2017-05-10
You can also use Synaptic Package Manager. Not sure if that also still comes default with Xubuntu. If not, easy to install with Software or in terminal.

```
sudo apt install synaptic
```

Many prefer it.

---

### Post by ubu112 on 2017-05-11
Thank you,for your answers.

For now I'm just tring Xubuntu from a live USB and "software" doesn't work,why?

I checked how much memory my system use

> xubuntu@xubuntu:~$ free -lm
              total        used        free      shared  buff/cache   available
Mem:            986         275         230          56         479         615
Low:            865         635         230
High:           120         120           0
Swap:          1010         251         759
xubuntu@xubuntu:~$ 



Can someone,please, explain to me which is the meaning of  row "Mem","Low" and "High"

Thank you

---

### Post by RobGoss on 2017-05-11
>  For now I'm just tring Xubuntu from a live USB and "software" doesn't work,why?

Please keep in mind running the live installer is just for demo purposes, it allows you to test the OS to see how it performs, you can't install software

---

### Post by Dennis N on 2017-05-11
"Software" takes (by my rough estimate) 30 seconds before it is ready to go - at least on the first launch. Needs to access its data, I think. 

As for free command, best to use **free -h** for understandability:

```
dmn@Sydney:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           3.7G        752M        2.0G         83M        1.0G        2.7G
Swap:          7.8G          0B        7.8G

```

Don't know about the low/high mem option and what it signifies.

---

### Post by ubu112 on 2017-05-11
I just want to take a look at "software".

I tried it more than ones,for minutes,but nothing happend,I mean it doesn't open.

About memory,from your example,first row "mem"it says Total 3,7 Gb but used+free make 2,75 Gb,and the remaining 1 Gb where is?

At the end "available" 2,7 Gb,what does it mean?and which are differences between free and available?

Thank you

---

### Post by vasa1 on 2017-05-11
> **ubu112 said:**
> I just want to take a look at "software".

I tried it more than ones,for minutes,but nothing happend,I mean it doesn't open.

About memory,from your example,first row "mem"it says Total 3,7 Gb but used+free make 2,75 Gb,and the remaining 1 Gb where is?

At the end "available" 2,7 Gb,what does it mean?and which are differences between free and available?

Thank youPlease use a new thread for each new question not really related to the original issue. And when you do so, an appropriate thread title will help attract people knowledgeable on the subject.

---

### Post by Dennis N on 2017-05-12
> About memory,from your example,first row "mem"it says Total 3,7 Gb but used+free make 2,75 Gb,and the remaining 1 Gb where is?

used + free = total - buffers - cache.

so the other 1 gB is buffers + cache.

Don't know what the story is with "Software". My Xubuntu 16.04 live media has been erased for another install, so I don't have that to test. I can confirm it does work in the installed Xubuntu 16.04.

Update: Tested with Xubuntu 17.04 live media, and "Software" application worked fine, once it loaded it's data, which took over a minute.

---

### Post by Bucky Ball on 2017-05-12
> **ubu112 said:**
> For now I'm just tring Xubuntu from a live USB and "software" doesn't work ...

You are using the computer to post here while in a live session? The machine in question is online? Sorry if it's a silly question. ;)

---

### Post by Autodave on 2017-05-12
The software center is not going to work on a live USB session. First off, the live session has no updates installed. So even if the center opens, you will not get anything because of the software nor being updated in the live session.

---

### Post by ubu112 on 2017-05-12
I'd like to say thank you,for your kindness

---

### Post by RobGoss on 2017-05-12
+1 Autodave

---

### Post by RobGoss on 2017-05-12
If you want to use the software center you will have to do a complete installation of Xubuntu

---

### Post by Dennis N on 2017-05-12
> **RobGoss said:**
> If you want to use the software center you will have to do a complete installation of Xubuntu

Software Center ("Software") does work in the live media at least in 17.04. I took the attached screenshot from Xubuntu 17.04 live media. I installed the Clocks application with it as well, so it is functional.

---

### Post by ubu112 on 2017-05-13
Thank you "Dennis N",now I know its look

---

### Post by ricardisimo on 2017-05-14
"Software" is difficult to find, and is only categorized under "All", rather than under "System" or "Settings", as the other related programs are. I'm pretty sure this wasn't the case in either 16.04 or before.

Also, it takes an exceptionally long time to load. Had to close it and reload a few times.

Finally, search function is only on the main page, rather than throughout subsections, etc.

In other words, there are better package handlers.

---

