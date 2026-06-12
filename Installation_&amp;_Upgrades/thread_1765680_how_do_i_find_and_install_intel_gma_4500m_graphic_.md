---
title: "how do i find and install intel gma 4500m graphic drivers? 10.10"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Xinu38 on 2011-05-23
having trouble with video and windows/links/applications etc on 10.10, just came from windows 7 with everything fine. had 10.04 on my desktop with nvidia card, was easy to get that driver installed, but intel i cant find the correct information. on a laptop, compaq presario cq56. can anyone help out?

---

### Post by Xinu38 on 2011-05-23
main problems are, missing links, videos have glitches/holes throughout the video, firefox has frozen up using normal tabs, not overdoing anything...so im guessing the system isnt using the intel graphics card but using my ram to handle the business.

---

### Post by Xinu38 on 2011-05-23
example here, when i click applications, it will not show anything until i mouse over the options. i also have a fresh install off 11.04 partitioned to 10 gigs on my hdd and all the same issues are on there as well. i tried returning to default theme to eliminate that. but heres some SS's

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-10.png[/IMG]

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-1-2.png[/IMG]

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/Screenshot-9.png[/IMG]

just missing links, and words. it mostly glitches/flashes on and off when i scroll as well. its there but its just like something is masking over it. its annoying the **** out of me. also when i maximize a video, i have to do it about 5 times to get it to play, otherwise i just get a frozen picture of when i hit maximize.

---

### Post by foresthill on 2011-05-23
Hey, don't feel too sorry for yourself. I have Intel GMA 4500MHD graphics on my laptop and the back light won't even work with the current driver for 11.04. So I'm stuck in 10.10.

From what I understand, the driver in 10.10 is also buggy. For example, when I run Firefox in WINE, many web pages have a black background that makes reading type impossible. 3D acceleration seems pretty poor as well. This is due to the buggy Intel driver, from the research I have done.

All of this leads me to the conclusion that Ubuntu does not work well with Intel graphics. So I don't know what else to tell you but that it could be much worse.

---

### Post by MAFoElffen on 2011-05-23
> **Xinu38 said:**
> having trouble with video and windows/links/applications etc on 10.10, just came from windows 7 with everything fine. had 10.04 on my desktop with nvidia card, was easy to get that driver installed, but intel i cant find the correct information. on a laptop, compaq presario cq56. can anyone help out?
I don't personally know a whole lot about this particular video chipset, but I did look around for you and here's what I found...  

*** Are you using the xserver-xorg-video-intel package with this?  Current versions for Maverick is 2:2.12.0-1ubuntu5.2; Natty is 2.14.0-4ubuntu7.1

Of the two drivers in that package for your video chipset... There is the Vesa and the intel drivers.  You should be using the Intel driver.  The Vesa one will cause some of the problems you seem to be getting.

You could look in sysnaptic to see what xserver package is installed,  Then look in your xorg.conf and it will say which driver it is using.

Note- I did see that here are 132 bugs and 17 open questions on this package up at LP.  

There seemed to be a few older tweaks, fixes and workarounds that already seemed to be incorporated into the newer drivers.  There are versions of this driver in the edgers ppa.

That's the info I've found and thought I'd pass on.  Hope it helps.

---

### Post by Xinu38 on 2011-05-23
thats weird, foresthill, i run 11.04 perfectly other than the few graphic glitches that dont effect performance much unless i open 2 videos or something, the browser will lag hard. guessing the easy non headache fix would be just to get a cheap nvidia card. i saw that thread as well and it just seems such a pain to fix a minor annoyance. plus he had 2 graphic cards in his system.  ill keep waiting for a solution if there is any. not much info on these stupid intel gma's

---

### Post by Xinu38 on 2011-05-24
bump

---

### Post by Xinu38 on 2011-05-25
i did find videos where the card is working perfectly. like here [http://www.youtube.com/watch?v=RFAznCro1xY](http://www.youtube.com/watch?v=RFAznCro1xY)

and here 

[http://www.youtube.com/watch?v=9klAxeQsHlQ](http://www.youtube.com/watch?v=9klAxeQsHlQ)

the second video even has a link for a driver in the description
here
[http://www.mediafire.com/?zw2zqx1hfq6327g](http://www.mediafire.com/?zw2zqx1hfq6327g)

i downloaded it, just dont know how to get it to work, or even if its the right driver...

---

