---
title: "Unable to install lubuntu 12.10"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by americast on 2012-11-02
I was installing lubuntu 12.10. The installation window appeared but after I proceeded and was at the last step, lubuntu would not install. The progress bar did not move at all. I clicked on the arrow and it tells me 'Failed to allocate memory'. How do I make my lubuntu get installed.

Existing OS: MS Windows XP
RAM: 256 MB
Processor: 1.6 GHz

Thanx...

---

### Post by ajgreeny on 2012-11-02
With only 256 MB ram I think you need the [Alternate install CD]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") not the live CD version.

Try that to see if it will install OK that way; it uses a text installer, not a live desktop but it is still very easy to use.

---

### Post by snowpine on 2012-11-02
I recommend upgrading your RAM (if your hardware has this capability). Even if you manage to get Lubuntu installed, 256mb is not very much for web surfing, documents, and so forth without going into "swap" which will make your computer very sluggish. If you can get up to 1gb (or even just 512mb) you will have a much more pleasant Lubuntu experence. :)

---

### Post by Rex Bouwense on 2012-11-02
+1.  I added a 256 MB chip to an old Dell Inspiron 1000 and it runs Lubuntu 12.04 quite well.

---

### Post by americast on 2012-11-03
I thank all of you for your quick and helpful response.
 
I shall try out Lubuntu alternate but tell me- should I give Puppy Linux a try?
 
Lucid Puppy supports the installtion of .deb files, right? And I can also install it using a Windows installer: [http://puppylinux.org/main/Download%20Latest%20Release.htm#winEXE]("http://puppylinux.org/main/Download%20Latest%20Release.htm#winEXE")
 
So, should I go ahead?
 
Thanx again...

---

### Post by Rex Bouwense on 2012-11-03
There are somewhere in the neighborhood of 350 different Linux operating systems.  Try all you like until you find one that suits you.

---

### Post by snowpine on 2012-11-03
Not a fan of Puppy, personally, but give it a try!

My personal picks for older hardware: Debian (LXDE or Xfce desktop), CrunchBang, AntiX, SliTaz.

---

### Post by americast on 2012-11-04
All 350????? Are you crazy?!!!

Anyway, Puppy is good but I have not being able to make wireless work..

Thanx to all.

---

### Post by tokyobadger on 2012-11-04
> **americast said:**
> I was installing lubuntu 12.10. The installation window appeared but after I proceeded and was at the last step, lubuntu would not install. The progress bar did not move at all. I clicked on the arrow and it tells me 'Failed to allocate memory'. How do I make my lubuntu get installed.

Existing OS: MS Windows XP
RAM: 256 MB
Processor: 1.6 GHz

Thanx...

[Quoting from the Lubuntu documentation "The lowest specification that we have seen working is a Pentium 2, with 64MB of RAM using lubuntu core."](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
Some questions:
1) How long did you let the installer run? At the link above they describe waits of up to 90 minutes on older hardware

2) Please give more details about your hardware

3) Have you tried a minimal install of lubuntu?

With the hardware constraints I guess you have I think you'll have to put in a swap of maybe 4G and choose lighter applications e.g. Firefox here is at 728M and Thunderbird at 102M - doesn't matter how lightweight your DE is, heavy apps will most likely render the experience unbearable

Maybe look at a minimal debian + *box (fluxbox/openbox or even lighter) install

---

### Post by americast on 2012-11-07
> **tokyobadger said:**
> [Quoting from the Lubuntu documentation "The lowest specification that we have seen working is a Pentium 2, with 64MB of RAM using lubuntu core."]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")
Some questions:
1) How long did you let the installer run? At the link above they describe waits of up to 90 minutes on older hardware

2) Please give more details about your hardware

3) Have you tried a minimal install of lubuntu?

With the hardware constraints I guess you have I think you'll have to put in a swap of maybe 4G and choose lighter applications e.g. Firefox here is at 728M and Thunderbird at 102M - doesn't matter how lightweight your DE is, heavy apps will most likely render the experience unbearable

Maybe look at a minimal debian + *box (fluxbox/openbox or even lighter) install

I shall try out the minimal installation.

Hardware- It's HP...

I think it will be a waste for me to wait till 90 minutes because the installation doesnt even start after a long time and the hardware light also does not blink at all...!

[RIGHT]Thanx to you all!!!
[/RIGHT]

---

### Post by snowpine on 2012-11-07
Curious why you don't simply upgrade your hardware, you could probably find a better computer second-hand in the "free" section of Craigslist, or brand new for under $500 (and the holidays are right around the corner).

---

### Post by americast on 2012-11-07
It is not my laptop. I have got it from my office...

---

### Post by snowpine on 2012-11-07
If you need Linux for your job, isn't there an IT person at work who can help you install it? It seems weird that they are leaving you hanging with crappy hardware and an a non-functional operating system. How do they expect you to get your work done without the right tools?

---

### Post by americast on 2012-11-07
The company doesn&#8217;t have funds to buy new comps.....

Anyway, lets avoid such discussions..

---

### Post by snowpine on 2012-11-07
Is it OK if I ask which applications you need for your job, and have you verified they are available for Lubuntu, and that they will run with such low hardware specs?

---

### Post by americast on 2012-11-07
Office apps, opera and dropbox...thats all

---

### Post by snowpine on 2012-11-07
Lubuntu includes Abiword and Gnumeric, which are a pretty bare-bones word processor and spreadsheet. LibreOffice is available from the repos, but I think your hardware is borderline to run it. 

Microsoft Office is known to have problems running in Linux, which you can read more at winehq.org

I'm sorry your boss is not supporting you with a functional laptop to do your job, that sounds like a very uncomfortable situation at work. Good luck! :)

---

### Post by americast on 2012-11-07
Right! I am trying to convince him...

---

### Post by snowpine on 2012-11-07
I just had a brainstorm, if all your work is by browser/dropbox, can't you just use your own personal machine? I mean, how would they know you are actually using the work craptop instead of your own nicer computer?

---

### Post by snowpine on 2012-11-07
Also at the risk of stating the obvious, you said in your first post: "Existing OS: MS Windows XP." 

Office apps, Opera, and Dropbox are all available for Windows.

---

### Post by americast on 2012-11-07
Ha ha...

The problem is that the *top has been given to me for office work and there is no comp in the office...so i need to use this one at my office....i dont have any problems at home..

I had MS Win XP already installed but it cannot run office 2007 due to low ram and so i cant open .*x (eg .docx) files. Also, due to virus and anti-virus related issues, it is very slow.

---

### Post by snowpine on 2012-11-07
I would say that you need more RAM, I can't think of any other feasible solution. Good luck! :)

---

### Post by americast on 2012-11-07
Yes... I am gonna try the minimal install very soon...

Thanx to all for your support...

---

### Post by snowpine on 2012-11-07
^-- I meant more RAM for your office tasks, not more RAM to install Lubuntu. If you manage to get Lubuntu installed, you will still have the same problem, that you don't have enough RAM to comfortably run a full office suite compatible with .docx documents.

Unless you think Office 2007 will run faster and use less RAM in Lubuntu than in its native Windows? Have you read the winehq page?

---

### Post by snowpine on 2012-11-07
Also I forgot to mention, LibreOffice and Abiword (the two most popular word processors for Lubuntu) are also available as free downloads for Windows, so you can evaluate these applications for your needs in Windows, *without* switching to Lubuntu.

---

### Post by americast on 2012-11-07
Is it? LibO in Windows also needs 512 MB RAM. But I can give AbiWord a try.

---

### Post by americast on 2012-11-18
Can I install Lubuntu using Wubi?

---

