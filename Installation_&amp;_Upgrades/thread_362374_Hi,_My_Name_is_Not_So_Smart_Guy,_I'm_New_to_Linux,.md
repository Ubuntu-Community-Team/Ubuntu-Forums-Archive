---
title: "Hi, My Name is Not So Smart Guy, I'm New to Linux, and I Think I Just F'ed Up"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Not So Smart Guy on 2007-02-15
Excuse me, I'm not an idiot, I'm just in need of assistance. 

If you don't want to read my lovely rant below (read it if you want additional details and to laugh at my incompetence), then I should tell you my problem out right, I suppose. I just installed Ubuntu 5.10 and apparently my X Server isn't configured correctly. I can't even log in. I see a lovely Ubuntu logo, some stuff is loading up, then it tells me X Server has failed to start and that it likely isn't set up correctly. Humbug. 

For the sake of full disclosure, I am a life long Windows user and my experience with any form of Linux started a couple days ago, and as evidenced by my being here, it didn't go so hot. 

For the sake of background info, I'll tell you how I got here. As most disasters go, mine started off simple enough, I was going to upgrade one of my (slightly) older machines from Windows ME (yes, people still use it), to Windows XP - nothing exciting here, just routine stuff. But after hearing good things about Linux, Ubuntu especially, I decided I would try and dual boot Windows XP Professional and Ubuntu 5.10. Now I've never done anything like that before, but hell, I'm not a an idiot, right? Yeah, well...

Everything seemed to be going fine (except for the irritating baby-sitter-esque install of Ubuntu) until during the install I'm at the all two mind numbingly boring step of entering your name, user name, password, and confirming the password. Well I got real familar with those steps because I forced to repeat them a near infinite amount of times because for whatever reason I *could not* get past those four steps; no matter what I did, immediately after confirming my password I would simply get returned to the screen for entering my name, over, and over, and over until I was on the verge of impaling myself with a pencil and strangling myself with my mouse cord. I managed to bypass the step by using the main install menu (not sure if that's exactly what it's called; where you can view and jump between steps of the install) only to be infuriated by it twice more, again bypassing it. 

I finally get through the install only to find Ubuntu isn't going to load up properly, oh f*cking no, it's going to tell me the X Server isn't set up properly. It gives me some nonsensical read out and tells me to go screw myself (okay, not so much on that last one). To be precise I think the first thing to go wrong is... "Synchroninzing clock to ntp.ubuntulinux.org" that says "FAILED" that happens while the modules are loading then I get the "failed to start X Server" message. 

One other thing to note, during that "baby-sitter-esque" install I was generally absent minded and blowing past options and questions I now realize should have paid more attention to what I was doing. That's why I decided to put this thread in the installation section, because I'm all but certain that's where I must have screwed something up... then again I'm not that smart, so I could be wrong about that. 

Obviously, I'm frustrated, and while I absolutely deplore asking for help (ever), I've heard these here forums are renowned for offering useful assistance and advice for not so smart folks like myself. If there's anything you think I can do to fix this, please let me know, I would very much appreciate it. Or, if you think I'm eternally screwed and have to try and reinstall, let me know also.  

Thank you for your time I'm going to go watch paint dry...

---

### Post by KatieCook on 2007-02-15
First, I am so sorry that you are having this problem, and I feel for you because on my almost shiney computer I have been tearing myself up inside about doing a dual boot but am sooooo freaked out something like this would happen to me.. But that being said.....I feel for you.

Second, I am still very very new to Linux and to ubuntu, but I can say that my older machine also had ME and I had no desire to keep anything and just deleted the whole drive and installed 6.06.  I tried to use 5.10 but could not get a desktop to load. Nothing I did seemed to work, so I changed to 6.06 (not 6.10 only because I wanted the stability of the older one while I was getting my feet wet)  It works great.

 I do not know how the partitions work and where to go from here, but these people here are soo great and will help you out with it.. I would suggest that you try 6.06 as it works great for me, and my machine came from ME also.

---

### Post by lamalex on 2007-02-15
If you're dual booting, install Windows XP first. Once XP is installed, install Dapper (6.06) or Edgy (6.10). Is there any reason you're using the older version? I've had good luck with edgy (6.10). Download one of them and give it another try. The version you're using is outdated. If you need anymore help post or pm me, I'm happy to help :)

---

### Post by meng on 2007-02-15
Well, firstly, it isn't necessarily that you did anything wrong, it might just be that your hardware isn't immediately recognized/configured by Ubuntu. It may be easy to fix. I would start by installing a more recent version of Ubuntu rather than 5.10.

---

### Post by ezphilosophy on 2007-02-15
Plenty of people here to help.  But first, you'll need to give some more information.

You said that you didn't pay much attention to the install and had problems with the user name and password.  You eventually completed it (I don't see that you had a choice)
I assume that after it tells you that the X server can't boot, it kicks you back to the command prompt to login?
What kind of computer are you using?  Do you know what graphics card you are using?
How are you connected to the internet?  DSL?  Do you have a router?  Do you need a password to get online?
Some people might question why you decided to use 5.10 as there is the LTS version 6.04 now and many people are using 6.10.  Both of these have a graphical install via live disc.

EDIT:  haha, sure enough, 3 people responded in the time it took me to write this and said the same thing.  :-)

---

### Post by Not So Smart Guy on 2007-02-15
Hello everyone, and thanks for the replies. 

I'll answer what seems to be the most pressing question first: why am I using 5.10 instead of Dapper? Simply, Dapper (to my knowledge) requires 256 MB of RAM, while I currently only have 128 MB, so that's the reason why I opted for an older version. I find it interesting, however, that someone else(KatieCook) also had an ME machine that had problems with 5.10 I no longer use ME of course, but it jumped out at me nonetheless. 

**ezphilosophy**, Yes, after the X Server message I am indeed taken to the command prompt. As for my computer, it's a Dell Dimension 8100, with an NVIDIA GeForce2 MX/400 graphics card. I have a wireless card on the machine in question, which corresponds to a Linksys router on another machine in my living room, which has a direct DSL connection. And no, no password, open access, our neighbors could use the connection if they felt like it. I'm not entirely sure how any of that is immediately relevant, but I sure hope it is. I remember during the install being prompted to provide the location for my graphics card, and hell if I remember what I put, though I'm sure not knowing screwed me. 

Back to why I'm using the version I am, or more accurately, to what version I should use... would Drapper run smoothly (or at all) on a computer with just 128 MB RAM? Should I try it? 

Again, thanks for your responses. I hope the additional information I gave can help you help me.

---

### Post by meng on 2007-02-15
You'll struggle to run even Breezy with 128 MB RAM unless you choose to use Xfce rather than GNOME. I suggest you install Xubuntu DAPPER, from the Alternate CD (not the Live one).

---

### Post by Not So Smart Guy on 2007-02-15
> **meng said:**
> You'll struggle to run even Breezy with 128 MB RAM unless you choose to use Xfce rather than GNOME. I suggest you install Xubuntu DAPPER, from the Alternate CD (not the Live one).

Hey, that actually sounds like a good suggestion. From the Xubuntu website, > If you wish, you can install any KDE or GNOME application on your Xubuntu desktop system, as it shares the Ubuntu main and universe package selection. If that's so, then I may very well take your suggestion if I can't get Breezy sorted out. 

However, that leads me to another question, if I were to install Xubuntu, or another version of Ubuntu, or even another distro all together (some people have suggested Mepis to me), what potential problems could arise from that? Namely my ability to boot Windows. I did choose to install the GRUB on the MBR during installation, and I've heard removing Ubuntu could prevent me from booting Windows. 

So, unless anyone can point towards a solution on how to sort out my X Server/Breezy problem, I'm now also taking suggestions on alternate versions and/or distros.

---

### Post by meng on 2007-02-15
It shouldn't be a problem. Usually the dual-boot will be available automatically.

---

