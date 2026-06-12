---
title: "Help installing Symantec AV"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by Jasmitchera on 2011-09-07
Hi.. I Am Triyng To Install Symantec AV On One Of My Machine(ubuntu 11)..
But I Am Getting Dis Error..
 
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [custom] Error 2

How Can I Fix This Error.. i am new to linux..

---

### Post by coffeecat on 2011-09-07
Let's start here:

> **Jasmitchera said:**
> I Am Triyng To Install Symantec AV On One Of My Machine(ubuntu 11)..

<snip>

i am new to linux..

Since you are new to Linux you may not be aware that you probably don't need AV software. If you are running a mail server you should use AV software so as not to be forwarding Windows viruses, but an ordinary desktop user doesn't need AV software. There are no Linux viruses known to be in the wild at present.

Have a look at this link. In particular scroll down to the section headed, "The Windows Mindset... Viruses..."

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Jasmitchera on 2011-09-07
Hi.. I Am Triyng To Install Symantec AV On One Of My Machine(ubuntu 11)..
But I Am Getting Dis Error..
 
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [custom] Error 2

How Can I Fix This Error.. i am new to linux..

---

### Post by Jasmitchera on 2011-09-07
Hi,
 
ys i know about that, but acoording to our company policy every machine should have AV installed on it. so that is why i am doing installation of AV on it..
 
So help me in solving this issue.

---

### Post by coffeecat on 2011-09-07
Well, if this is to conform to company policy rather than to fulfill any rational purpose, does your company specify which AV you should use? If not, install clamav from the repository. If you install clamtk, you get a GUI frontend.

> **Jasmitchera said:**
> So help me in solving this issue.

I was always taught to say 'please'. :wink:

---

### Post by Jasmitchera on 2011-09-07
Hi,
 
Thnaks for your suggetion, ys they told me to install symantec AV on our machines so can install only symantec. can u please help me in this issue.if your have any solution on this error please tell me.. :)

---

### Post by mörgæs on 2011-09-07
Please don't double-post.

---

### Post by coffeecat on 2011-09-07
I've never tried to install Symantec, so I can't help you with specifics. Nevertheless, that looks like a compile error. Make sure you have the linux-headers package installed for your kernel (it looks as though you have anyway) and make sure you have the package "build-essential" installed.

Other than that I can't help. You need someone who has installed Symantec but your thread title is not descriptive and won't attract the notice of someone who can help. The thread title needs changing, except that only a staff member can do that. You can request a moderator to change the thread title by clicking on the report button in the left pane of your post - [img]http://ubuntuforums.org/images/buttons/report.gif[/img] - and specifying what you want. I would suggest "Help with installing Symantec AV". Don't worry that the button says "Report Abuse" - that's only one of its functions.

---

### Post by Jasmitchera on 2011-09-07
Thanks For Your Reply, And I Checked Both The Packages They Are Installed On Machine..I Installed Symantec AV On 10.04 And It Got Successfully Installed.

---

### Post by cariboo on 2011-09-07
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by haqking on 2011-09-07
What version so AV are you trying to install and where did you get it ?

If it is for corporate they should supply and maintain it, they cant force you to make changes to your own machine, if it is owned by them then they need to sort it.

you can get the *nix endpoint software here [http://www.symantec.com/business/security_response/definitions/download/detail.jsp?gid=savce](http://www.symantec.com/business/security_response/definitions/download/detail.jsp?gid=savce)

If it is one of the Norton (symantec) desktop clients i dont think they do one for Linux, though there is a mac versions

---

### Post by Jasmitchera on 2011-09-07
Hi,
I Got Installable Package From Symantec, Actually Symantec Release AV For Different Linux Versions. Can U Please Tell Me If Their Is Any Solution To Solve This Error .

---

### Post by ottosykora on 2011-09-08
not an expert on building executables , but it seems that symantec did something what is compatible with one kernel only.

Try to complain to them, they should definitely be able to help.

I am not sure if it is possible to install older kernel, the same as in the ubuntu 10 and then make the build when this is loaded.

---

### Post by haqking on 2011-09-08
> **Jasmitchera said:**
> Hi,
I Got Installable Package From Symantec, Actually Symantec Release AV For Different Linux Versions. Can U Please Tell Me If Their Is Any Solution To Solve This Error .


Well it is for work and they are the ones requiring your have Symantec so there problem really ;-)

I dont see why you have to troubleshoot your own machine due to there requirement when you could easily install another solution without the hassle ?

---

