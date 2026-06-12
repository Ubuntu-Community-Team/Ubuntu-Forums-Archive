---
title: "How to install Avira...anyone?"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Iokua86 on 2010-02-17
I just downloaded the avira package for ubuntu 9.10 but, I haven't the slightest clue of how to install the program. What do I need to type in the terminal to install avira? Do I need anything else? What's this dazuko things I keep coming across?

---

### Post by wilee-nilee on 2010-02-17
What type of download is it a deb or tar. Also Klamav is a good scanner that can also scan MS partitions. Actually you don't need either really, in that they are looking for MS stuff which shouldn't affect a Linux setup theoretically.

---

### Post by Iokua86 on 2010-02-17
Well i'm new to linux and although it's been spectacular so far, I don't want to take my chances. ecspecially since i plan on using Transmission. I don't know which type of file it is. I suppose i'll look for the one that's easiest to install (Spoken like a windows use, I know).

---

### Post by Iokua86 on 2010-02-17
oh, just kidding. It's a tar.

---

### Post by wilee-nilee on 2010-02-17
Some Tar's can be double clicked then extracted and a installer is in the folder, I am not sure of this in Avira though.

---

### Post by Iokua86 on 2010-02-17
Yes, there is an install document. However, it's pretty long, don't know how to read it. and the README file isn't much help either.

---

### Post by pirateghost on 2010-02-17
i have to ask, why do you think you need an antivirus?

---

### Post by Iokua86 on 2010-02-17
just for added protection. I want to use Transmission

---

### Post by pirateghost on 2010-02-17
> **Iokua86 said:**
> just for added protection. I want to use Transmission
and what does transmission have to do with it?

do you plan on sharing with windows computers?

what exactly do you think you are protecting a linux computer from?

---

### Post by 2hot6ft2 on 2010-02-17
Are you aware that ubuntu already has an antivirus installed by default?

Check
Applications > System Tools > Virus Scanner
If it's not there it may be in one of the other menus like Accessories
That's just for the gui for it if you can't find the gui in the menus you can install it by going to
Applications > Accessories > Terminal
and putting in
```
sudo apt-get install clamtk
```
when you type in your password it wont be displayed just type it in and hit enter.
Then it will be there

---

### Post by Iokua86 on 2010-02-17
nope, not planning on sharing, just looking for protection.

I didn't know there was a virus scanner on this thing. I had avira when i was using windows and it worked pretty well. I guess that solves this problem.

---

### Post by 2hot6ft2 on 2010-02-17
> **Iokua86 said:**
> I just downloaded the avira package for ubuntu 9.10 but, I haven't the slightest clue of how to install the program. What do I need to type in the terminal to install avira? Do I need anything else? What's this dazuko things I keep coming across?

[Dazuko-based Applications]("http://dazuko.dnsalias.org/wiki/index.php/Dazuko-based_Applications")
It's used by several linux antivirus applications like clamav

---

### Post by Iokua86 on 2010-02-17
gotcha. I appreciate it

---

### Post by chuckh1958 on 2010-05-28
> **pirateghost said:**
> i have to ask, why do you think you need an antivirus?

Why do you think you DONT need an antivirus program? It's a common misconception that linux is not susceptible to viruses and malware and thats simply not true. A google search of "linux malware" will turn up thousands of hits.

---

