---
title: "I tried to install Rosegarden but..."
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by statekilla1 on 2008-01-14
I am obviously new around here, peace to you all.  I have two problems that arise when I launched Rosegarden on my computer. One about the kernal timer resolution being set to low, and the other 'failed to connect to JACK audio server.  Any ideas on how to install start the JACK server?  It also seems like my social life will be ruined as I need to try to install 'flac' on my own.  The local linux dude is extremely reluctant to help a brother out on this cause but is willing to charge $300 dollars. I know that I will have to set aside a day and focus on this. PLZ hear my cry.:)

---

### Post by Samhain13 on 2008-01-14
Sorry I can't help you with Jack but regarding the "resolution too low", I think the easiest (if not the only) solution is to install the real-time kernel.

I use Rosegarden myself but I just can't remember how I got the Jack issue resolved. Anyway, from what I remember, I just followed this guide on installing TiMiDiTy++: [http://www.cs.cornell.edu/w8/~djm/ubuntu/feisty/#timidity](http://www.cs.cornell.edu/w8/~djm/ubuntu/feisty/#timidity)

It was after those steps that I installed Rosegarden and the Real-Time Kernel. Restarted and everything seemed alright.

---

### Post by programmer8922 on 2008-01-19
I had a similar jack error when using QSynths, but I installed qjackctl(you do have to run it as well) and it fixed my problem.

---

### Post by luctor on 2008-01-20
install ubuntustudio-desktop, i think that takes care off a lot of the audio/timer/resolution things.
it's also a good idea to install linux-rt (realtime kernel)

you need jack (via qjacktctl) for low-latency / realtime audio. getting it to work ok (ie without x-runs) takes some effort. 

rosegarden 1.5.1 should run without jack just fine but only for midi (not audio)

Rob

---

### Post by statekilla1 on 2008-02-11
THanks for the command.  Something weird is going on inside my terminal. I enter the command and of course it asks me for my password.  But it seems that my keyboard all of a sudden goes dead and I can't type a darn thing!  Has this ever happened to anyone else?

---

### Post by oskar2000 on 2008-02-11
Just to clear up things:

You need the realtime kernel for realtime performence, it is not all that necessary to run rosegarden, but it is recommended.

Jack is the soundserver that rosegarden relies on. Jack doesn't do jack about realtime processing, it's a soundserver. You can do adjustments though.
 I don't think you can run rosegarden without starting jackd.
Qjackctl is a graphical tool to configure and start/stop jack without using the command line.

---

### Post by oskar2000 on 2008-02-11
> **statekilla1 said:**
> THanks for the command.  Something weird is going on inside my terminal. I enter the command and of course it asks me for my password.  But it seems that my keyboard all of a sudden goes dead and I can't type a darn thing!  Has this ever happened to anyone else?
There is no output when you type a password. That's normal.

---

