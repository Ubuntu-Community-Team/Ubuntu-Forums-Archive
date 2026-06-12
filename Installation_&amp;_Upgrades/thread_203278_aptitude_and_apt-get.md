---
title: "aptitude and apt-get"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by presentt on 2006-06-25
Hello,

I was wondering about the relationship between aptitude and apt-get.  I've used apt-get for some time (ever since I realized I could use it instead of Synaptic Package Manager), and recently heard about aptitude.  I ran aptitude from a terminal, but didn't quite take the time to figure it out.

I read the man pages for both, and gathered that apt-get it a back-end for aptitude.

Does aptitude provide additional features for package management than apt-get, or does it just try to improve the interface?  If I'm already comfortable with apt-get, do you think it's worth "switching" from using apt-get to aptitude?  What would the benefits be, and what would I lose?  Is it the type of thing I might use alongside apt-get, or would it be better to choose between the two?

I'm just trying to get a sense for both programs before I take the time to "learn" aptitude to the extent I "know" apt-get--to me, apt-get is simple and straightforward, and gets the job done.  Thanks.

---

### Post by Sye d'Burns on 2006-06-25
You can use aptitude the same way you use apt-get (ie sudo aptitude install) 

The main thing that aptitude brings to the table is it uninstalls unused dependencies when you uninstall a program that you've installed with aptitude. Very handy indeed.

---

### Post by aysiu on 2006-06-25
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by presentt on 2006-07-03
Great, thanks everybody.

---

### Post by BrianK on 2006-07-03
There's a weird issue that pops up with aptitude every so often when you select a packege to install.  It gives you a prompt that says, "Enter new package tree limit" with no hint of what the answer should be.

Once that happens, I've never been able to get aptitude to work again.

If anyone has a solution to that problem, feel free to post it.

---

### Post by aysiu on 2006-07-03
I've never heard of this. Next time it happens, can you post the full output that comes along with it?

---

### Post by BrianK on 2006-07-05
[QUOTE=aysiu]I've never heard of this. Next time it happens, can you post the full output that comes along with it?[/QUOTE]
That is the full message.  A box pops up that looks just like the search box with a line to input text.  It simply says, "Enter a new package tree limit" and wants you to type something in.  In my attempts to find what the heck it's asking for, I found a back & forth about it on a Debian developers mailing list... one person said, "This message seems a bit cryptic & not helpful"  The reply was, "It should be in the help in the next release" ... and that was it.

Very frustrating.  I've asked about it before on this and other forums... never got a response.

---

