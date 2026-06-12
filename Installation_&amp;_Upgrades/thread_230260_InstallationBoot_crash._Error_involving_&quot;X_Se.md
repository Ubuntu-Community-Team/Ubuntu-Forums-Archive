---
title: "Installation/Boot crash. Error involving &quot;X Server&quot;"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by Overbite6014 on 2006-08-05
As most of you can probably discern from the title, I'm new to the linux scene. I'm actually posting using a windows installation that already exists on the computer in question. I've downloaded the newest(6.06?) iso of Ubuntu Desktop, which advertised a Live CD version and an installer. 

I successfully burned the image, booted the CD and began the installation (by selecting the "Run or Install Ubuntu" option) all seemed to be going well until the Ubuntu logo and all of the text around it disappeared. I was brought to a blinking cursor that, after a few moments, disappeared. I was redirected to a blue screen with a grey error box in the center. The error read something like:

**"Failed to start the X Server. It is not set up correctly." **

After a few prompts with information that I knew nothing about, the message told me "X Server Disabled."

I've sifted through the "Problems with X Server" thread, but I can't seem to find anything that relates to my problem. A search on Google hinted that my graphics card may be to blame. I will include my machine details with this post. If any more information is required, I will do all that I can to procure it. 

Thank you all for the support.

AMD Athlon 64 X2 Dual Core 3800+
1gb RAM
Radeon X800 GTO Graphics Card

---

### Post by Herman on 2006-08-05
Hello, Overbite6014, I see that you have some nice hardware threre,  AMD Athlon 64 X2 Dual Core 3800+, 1gb RAM,  Radeon X800 GTO Graphics Card. I also have an ATI card, but mine's a Radeon 9200 SE.

Mine is set up OK in the current Dapper installers, but I used to have to run  sudo dpkg-reconfigure xserver.org for it when I was installing the pre-release versions of Dapper Drake.

I am just an ordinary user learning things here too, but I also make web pages to try to help others with things I have learned a little about already.
I could not hope to add anything that hasn't been covered already in the well known and excellent thread you mentioned, [Dealing with problems with the Xserver]("http://www.ubuntuforums.org/showthread.php?t=187177")
However, I have taken the time to illustrate the process you can expect when you enter 'sudo dpkg-reconfigure xserver.org' and  go through each step as it happens to me. I added  some commentary as well. It  might be helpful to you.  I think  I would try that  first and see if that works or not.  If it doesn't fix it you can always do it over again after downloading a specail driver if necessary, or try choosing the vesa  driver. I believe most LiveCDs work with a vesa driver, so that should at least get ytou going  to begin with, if a Live CD will work in your computer. The exact right specailised driver would normally give optimum performance though, of course.

Anyhow, here is the link, I hope that will explain the process and what it's all about for you, [sudo dpkg-reconfigure xserver.org  Page]("http://users.bigpond.net.au/hermanzone/p7.html")

Good Luck with it, any more questions, please ask, Regards, Herman. :D

---

### Post by taurus on 2006-08-05
You should use the alternate CD to install Dapper on your machine then.  It uses text base and if you still have problems with X after the installing, then you can configure it 

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Overbite6014 on 2006-08-05
Where can I find the Alternate Installation CD?

---

### Post by taurus on 2006-08-05
Same place that you downloaded your desktop version!!!

[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/)

---

### Post by Overbite6014 on 2006-08-05
Ah, got it. Thanks. I'll give it a try.

---

### Post by Herman on 2006-08-05
I found a link to some information on Radeon cards too. It has a well written spiel in the introduction about why not all cards can be supported 'out of the box' in Ubuntu.   [RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver?highlight=%28CategoryDocumentation%29")   
I did not see your  Radeon X800 GTO Graphics Card listed under 'will it work with your card?'  though, Overbite6014, so I'm not sure how relevant that info is to your particular situation. It's probably worth a try later on, first just get it working, then later try getting it working at optimimum performance. Just be sure you make a back up of your /etc/X11/xorg.conf file before trying new drivers and settings so you can always restore the old file to roll back to the old settings again if you need to.
Regards, Herman :D

---

### Post by Twinsen on 2006-08-07
I think some of the GTO cards have R480 cores and some R430.
Could be that its getting confused?
Mine shows in atitool as R430 with 16 pipelines 
but I cant get the GUI to work even when i reconfigure the xserver to use vesa drivers.
After i restart the x server it just says no input siginal on my screen.

---

