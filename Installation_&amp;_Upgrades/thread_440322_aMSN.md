---
title: "aMSN"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by epq on 2007-05-11
Hey..
Firstly Im no linux expert.
I wanted to use msn so I installed aMSN from apt-get, however it wouldnt log in and just crashed.. eventually a bug report window appeared but that also crashed.
I then installed the newer version SVN Snapshot, but that also has the same problem.
My access to the internet is through a proxy so maybe that is affecting it.
I would be very grateful for any suggestions.

---

### Post by sdowney717 on 2007-05-12
Can you start it from terminal, perhaps you will see an error message
Does it not start, how far do you get when running it?

I am using feisty. It works well, so If you can get it going it is just like windows version.

I am not using a proxy, would it really crash if you were?
I would expect it to just be unnable to login. 
I installed it thru synaptic.

An MSN messenger written in tcl
A very nice MSN compatible messenger application. Works pretty much like its
Windows based counterpart. Perfect for keeping in touch with those friends
who have not yet seen the light.

This package supersedes ccmsn, which is no longer maintained upstream.

---

### Post by epq on 2007-05-13
I tried starting it from a terminal and it helped somewhat... the programme does crash as soon as it does otherwise.
However, it is still the case that when the 'Log In' button is pressed the programme stalls.
If it is left long enough a 'report a bug' window appears, but that also crashes.

---

### Post by jfinkels on 2007-05-13
> **epq said:**
> I tried starting it from a terminal and it helped somewhat... the programme does crash as soon as it does otherwise.
However, it is still the case that when the 'Log In' button is pressed the programme stalls.
If it is left long enough a 'report a bug' window appears, but that also crashes.

What is the error output in the terminal when it crashes?

---

### Post by epq on 2007-05-14
It doesnt say anything on the terminal... even when the error report window comes up. The programme just seems to stop working... if I cover its window with another one for a while it is left blank. 

The problem seems to be related to the proxy. When start the programme after turning the computer on the proxy settings are at the default and if I click 'log in' it shows that there is an error connecting.. I can even cancel that and get back to the login screen again. When I enter my proxy settings though, the programme stalls on clicking 'log in'. If I kill it and start it up again the proxy settings are retained.. and the programme still stalls.

I would be very grateful for any help or suggestions that can be given.

---

### Post by jfinkels on 2007-05-14
> **epq said:**
> It doesnt say anything on the terminal... even when the error report window comes up. The programme just seems to stop working... if I cover its window with another one for a while it is left blank. 

The problem seems to be related to the proxy. When start the programme after turning the computer on the proxy settings are at the default and if I click 'log in' it shows that there is an error connecting.. I can even cancel that and get back to the login screen again. When I enter my proxy settings though, the programme stalls on clicking 'log in'. If I kill it and start it up again the proxy settings are retained.. and the programme still stalls.

I would be very grateful for any help or suggestions that can be given.

Sorry, I can't help you any further. I hope someone else comes along who has experienced a similar problem or knows something about proxy problems.

---

### Post by epq on 2007-05-15
Thanks for thinking about it...
Has anyone else a suggestion or an experience of a similar problem??

---

### Post by ghostboy on 2007-05-15
It sounds to me that once you hit that Log In button, your signal hits something, hangs, and stops responding. Try disabling/removing your proxy settings and try it again.

---

