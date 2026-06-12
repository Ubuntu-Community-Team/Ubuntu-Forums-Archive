---
title: "Why does firefox take so long to load up. Like about 9 seconds"
date: 2009-05-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-05-02
Nothing else running first app to start and it takes an age.

Same with Jaunty and Intrepid.

---

### Post by Kevbert on 2009-05-02
Closer to five seconds for me. You could try launching firefox via terminal and see if there are any errors.

---

### Post by mabovo on 2009-05-02
Have You tried to disable IPV6 ?

---

### Post by Ericyzfr1 on 2009-05-02
Mine is under 5 seconds, I left the home page from the install.

---

### Post by gnomeuser on 2009-05-02
All of Koala is extremely slow for me currently. I am thinking it is the effect of a bad update somewhere. The churn is very high so I would wait a week or so and see if the problem doesn't go away on it's own once things cool down a tad.

If not then we can start triaging this bad boy.

---

### Post by philinux on 2009-05-02
> **mabovo said:**
> Have You tried to disable IPV6 ?

Makes no diff.

---

### Post by rajeev1204 on 2009-05-02
10 seconds for me too cold start , both intrepid and jaunty.

---

### Post by olskar on 2009-05-02
~9 seconds for me too. Imagine firefox opening instantly :lolflag:

---

### Post by ktp on 2009-05-02
Ya I have seen this also. Have you tried new profile?  

I have also see high CPU usage with plug-ins, mostly flash and java, since 3.0.9.

---

### Post by philinux on 2009-05-02
This is a completely clean install of jaunty upgraded to karmic. So new profile and no addons except the default ones. Not even flash.

---

### Post by Slug71 on 2009-05-02
I think its this FF-3.0.10. For some reason it doesnt feel very stable for me either. I get lots of lock-ups and the screen turns gray. I think it has something to do with Flash too though. 
Hopefully the next Flash will be much better and that we'll have a native 64bit Flash.

---

### Post by rajeev1204 on 2009-05-02
We have a native 64 bit flash , but its still in aplha i believe.

But i have to say, even the repo version is equally as bad for me.

Iam sticking with 64 bit flash for now.

Ya , newer firefox did crash on me a couple of times too with flash.

---

### Post by plun on 2009-05-02
Maybe in the "upper division"  :) but these articles explains a lot and also  the challenge with **SQLlite**

[http://forums.gentoo.org/viewtopic-t-717117.html](http://forums.gentoo.org/viewtopic-t-717117.html)

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm) 

Using RAM is extremely faster.....maybe something to look at ???

---

### Post by davideotape on 2009-05-02
Hmm, I don't seem to have any of the problems described in this post. If anything, my Firefox has got faster.

I hope you guys get your problems solved though. Firefox isn't exactly the fastest browser....

---

### Post by ktp on 2009-05-02
> **Slug71 said:**
> I think its this FF-3.0.10. For some reason it doesnt feel very stable for me either. I get lots of lock-ups and the screen turns gray. I think it has something to do with Flash too though. 
Hopefully the next Flash will be much better and that we'll have a native 64bit Flash.

I agree something changed in 3.0.9 or 3.0.10 which is making flash use high cpu.  I am even seeing this in Windows.

---

### Post by Gina on 2009-05-02
I've been having a couple of problems with Firefox - it's disappeared (shut itself down) once or twice when I've been typing a post and the copy and paste doesn't work.  The text highlights OK then before I can use Copy (either mouse or kb) the highlight turns grey and it won't copy.  I've had to revert to Jaunty for posting :(

Can't say I've noticed much difference in the speed.

---

### Post by Slug71 on 2009-05-02
I really hope FF-3.5 is going to be a lot better than this 3.x.x crap. 
If its not then i really think Ubuntu needs to look at adopting a different Browser as its default.

---

### Post by philinux on 2009-05-02
> **Gina said:**
> I've been having a couple of problems with Firefox - it's disappeared (shut itself down) once or twice when I've been typing a post and the copy and paste doesn't work.  The text highlights OK then before I can use Copy (either mouse or kb) the highlight turns grey and it won't copy.  I've had to revert to Jaunty for posting :(

Can't say I've noticed much difference in the speed.

Apart from the thread title here's some more.

Awesome bar and copy and paste stop working randomly. Have to close FF and restart to get copy/paste going. Awesome bar by going to a couple of websites via bookmarks then it suddenly works again.

---

### Post by Naddiseo on 2009-05-02
> **philinux said:**
> Apart from the thread title here's some more.

Awesome bar and copy and paste stop working randomly. Have to close FF and restart to get copy/paste going. Awesome bar by going to a couple of websites via bookmarks then it suddenly works again.

I find that happens when I'm using compiz, still not sure of the exact trigger.

---

### Post by Gina on 2009-05-02
One other thing while we're talking about Firefox... I still get the odd black rectangle at times as reported with Jaunty.

---

### Post by jfernyhough on 2009-05-02
Running FF3.6a1pre, loads of addons and Weave.

Anyhow, just for lulz I recently tried running my Acer with elevator=noop (seeing as my hdd has NCQ I wanted to see if it would be better or worse). Apart from most things running a bit slower Firefox loaded in a flash - under a second. deadline or cfq and it's back to 9-ish seconds.

---

### Post by gnomeuser on 2009-05-02
This really strikes me as one of those sitauation where having some tracing functionality and some predefined scripts would shed some light on the problem. 

We know it's consistently slow for a number of people, it would though be nice to know where things are going astray.

---

### Post by olskar on 2009-05-02
> **gnomeuser said:**
> This really strikes me as one of those sitauation where having some tracing functionality and some predefined scripts would shed some light on the problem. 

We know it's consistently slow for a number of people, it would though be nice to know where things are going astray.

Would strace firefox work?

---

### Post by miwaypet on 2009-05-02
In jaunty I had to update the kernel and drivers for my Intel graphics to watch full screen video. No biggie, everything was good, better even. When new FF update came things acted really bizarre. Bookmarks opened and closed slowly, and the whole bookmarks sidebar acted slow and strange like. FF was noticeably slower. Downloading from internet slowed. Changing from one web site to another was slow. I thought I was using Windows with some high powered A/V slowing things down. You know what I mean. That hesitation while the A/V scans the incoming data. 

Thinking it was the upgrade I did for the graphics, I did a complete reinstall, and things are better. Have not upgraded the driver and kernal. The upgrade must have caused some instability with the graphics and the FF update picked up on it and exaggerated the thing. My best guess for my situation so far.

In Karmic. No problems. Just a minimal FF to browse and do stuff to check for bugs and such. Smooth so far.

Michael

---

### Post by gnomeuser on 2009-05-02
> **olskar said:**
> Would strace firefox work?

It is my understanding that strace give us information on when the application does system calls. Reading Fredricos guides to performance profiling your application calls for using strace along with some custom code.

The approach basically involves inserting a bit of code that calls a cheap syscall at all the interesting spots in your code. This means modifying the firefox code and doing a custom compile. 

On the whole that does not seem like something I would be apt to deploy to users - unless of course one was to create a ppa for firefox with this code inserted, and still the solution seems oddly misfitting.

---

### Post by ktp on 2009-05-03
> **philinux said:**
> Apart from the thread title here's some more.

Awesome bar and copy and paste stop working randomly. Have to close FF and restart to get copy/paste going. Awesome bar by going to a couple of websites via bookmarks then it suddenly works again.

I have seen issues with compiz and focus issues...specially logging back from locked screen.  Something other then active window gets focus.  I have to switch to the app to get focus back.

When I first ran into this, I would not see filtered results when typing in the address bar. I thought firefox was not working so I was restarting it.  But then noticed the same focus issue with other application active after logging back from logged screen.  Switching application seemed to fix it but really annoying.

---

### Post by freeman2000 on 2009-05-10
FF has worked well for me, taking 2-3 seconds max to load from a cold start.  There are many things beside just the browser that come into play for web speed.  

How fast is your internet connection? 28k dialup or 6mps cable?
How fast is your processor & how much ram do u have?  a slug is a slug. 
What web page are you trying to load? no 2 pages are equal.
How many add-ons do you have FF loaded down with?  These take time. 

These are just some of the variables.  There are many more.  No two computers are alike.

---

### Post by olskar on 2009-05-10
> **freeman2000 said:**
> FF has worked well for me, taking 2-3 seconds max to load from a cold start.  There are many things beside just the browser that come into play for web speed.  

These are just some of the variables.  There are many more.  No two computers are alike.

How fast is your internet connection? 8mps cable
How fast is your processor & how much ram do u have?  2,4 ghz and 3gb ram
What web page are you trying to load? [www.google.com](www.google.com)
How many add-ons do you have FF loaded down with?  One 

Opens in ~ 9 seconds cold (but in ~2 seconds when already opened once)

---

### Post by vishalrao on 2009-05-10
What if you disable "automatically check for updates" option in FF does that speed it up any?

---

### Post by psyke83 on 2009-05-10
> **freeman2000 said:**
> FF has worked well for me, taking 2-3 seconds max to load from a cold start.  There are many things beside just the browser that come into play for web speed.  

How fast is your internet connection? 28k dialup or 6mps cable?
How fast is your processor & how much ram do u have?  a slug is a slug. 
What web page are you trying to load? no 2 pages are equal.
How many add-ons do you have FF loaded down with?  These take time. 

These are just some of the variables.  There are many more.  No two computers are alike.

My understanding is that this thread is not concerned with the speed of a network connection, only the time it takes for Firefox to launch. The only variables that should matter are related to memory, kernel and disk performance.

---

### Post by Reiger on 2009-05-10
Except that Firefox by default tries to open some webpage. Which does require the Internet connection so it's back into the equation from there on. My explanation would be that Firefox simply is that slow/fast.

---

### Post by psyke83 on 2009-05-10
> **Reiger said:**
> Except that Firefox by default tries to open some webpage. Which does require the Internet connection so it's back into the equation from there on. My explanation would be that Firefox simply is that slow/fast.

It's very unlikely that loading the initial homepage significantly affects startup performance. To remove this variable, I suggest we set the default homepage to "about:blank" while testing.

---

### Post by vishalrao on 2009-05-10
yes, which is why i thought about the "check for automatic updates" which happens before FF window appears i believe and can attempt to connect to the internet which might take very long...

---

