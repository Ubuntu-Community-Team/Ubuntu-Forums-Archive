---
title: "ubuntu hangs at installation"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by martinlillo on 2011-03-30
Hi! I'm new in this forum! First of all, I beg your pardon for my english (I'm from Argentina).

I have a little problem with an Ubuntu installation. Actually, with 3 Ubuntu installations! I'm sure the real problem is the pc I want to install in. Tried with Ubuntu 10.04, 9.10 and 8.04, and in the three cases the problem was the same.
The cd installation progress until the main menu (try ubuntu without install, Install Ubuntu, and so on...).
I choose either the first or the second option, and the screen turns black showing only the cursor blinking. Nothing else happens!

The pc is a Pentium 4, with 512 MB RAM. What is strange, is that I have installed Ubuntu in that pc the past year!

Any ideas??

Thanks in advance!!

---

### Post by ChipOManiac on 2011-03-30
How are you installing? by CD or USB?

---

### Post by martinlillo on 2011-03-30
LiveCD.

Thanks!

---

### Post by ChipOManiac on 2011-03-30
I had this problem a few months ago... how much speed is your CD Drive capable of? This was the problem with mine... Check the Live CD's speed... if'it's too much for the CD Drive, what you are saying is happening happens (at least in my case).

---

### Post by mörgæs on 2011-03-30
Sorry, but there is no such thing as 'the Live CD's speed'. 

While burning the CD it pays to use the slowest speed possible, but while reading the drive takes care of all speed negotiation.


Which release of Ubuntu did you manage to install last year?

---

### Post by martinlillo on 2011-03-30
I installed the 10.04 version. Actually, it was the same cd I'm using now!

Thanks!

---

### Post by ChipOManiac on 2011-03-30
> **mörgæs said:**
> Sorry, but there is no such thing as **'the Live CD's speed'.** 

While burning the CD it pays to use the **slowest speed** possible, but while reading the drive takes care of all speed negotiation.


Burn Speed was what I was trying to say ;)... You misunderstood me... :)

---

### Post by mörgæs on 2011-03-30
**Chiopmaniac**, if I misunderstood you there is a fair risk that other readers also did. Please take care that you are writing an exact and complete answer every time. 


**Martinlillo**, there are several things that could explain this.

It is not likely that the CD's themselves are the problem, since you see the same for all three of them. 

The CD drive could have gone bad. If the computer supports booting from USB (which I doubt), you could create an Ubuntu USB stick with Unetbootin and install this way.

If the CD drive has some functionality left, you could install a minimal Ubuntu from this ISO: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After that you install rest of the system with ```
sudo apt-get install ubuntu-desktop
``` This way you only have to read 10-15 MB from the drive and not 700. Always keep a wired internet connection while installing.

Memory could also be the problem. If you manage to get to the screen with the keyboard-man symbol at the bottom, you could press any key here and choose a complete memory test. It might take several hours.

---

### Post by ChipOManiac on 2011-03-30
> **mörgæs said:**
> **Chiopmaniac**, if I misunderstood you there is a fair risk that other readers also did. Please take care that you are writing an exact and complete answer every time. 


Piont Acepted Humbly :D ... Yessirie... Sorry :(

---

