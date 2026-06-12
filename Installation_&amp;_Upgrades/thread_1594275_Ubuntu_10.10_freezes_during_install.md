---
title: "Ubuntu 10.10 freezes during install"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Valis667 on 2010-10-12
I am trying to do a fresh install of 10.10 to run alongside Windows Vista. I have Vista installed on one HDD and told 10.10 to install on a 2nd HDD. So far so good. I get to the screen that asks "Who are you". I fill in the required information. The progress bar at the bottom moves along and says "copying files". Eventually all activity stops and it says"Ready when you are". Then it just sits there. The "forward" button stays grayed out. I've attached a screenshot of where it hangs. Also, it runs fine when I use LiveCD.  Can anybody help please?

[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by DJ_TYR on 2010-10-12
Remove the Capital V in the user name field, it should be all lower case & that should do it.

---

### Post by Valis667 on 2010-10-12
Woot!  Thank you thank you thank you! It works :D

I thought it would be something simple :p

---

### Post by DJ_TYR on 2010-10-12
No problem, I made the same mistake. :p

---

### Post by nssriharsha on 2010-11-04
Hi 

I'm too facing the same issue(getting struct @ "who are you") even after using small case characters.  I'm clicking on Login automatically.
Any help would be appreciated.

Regards,
Harsha

---

### Post by Quackers on 2010-11-04
You can't leave the password blank (if you have). A password MUST be entered and confirmed.

---

### Post by stargazergal62 on 2011-01-03
I am also having the same problem - install freezes during "Who are you."  And, yes, I have been doing the same thing with the upper case letter.  Here's my question:  What is the best way to install Ubuntu since it was interrupted in the middle of the install?  I am installing it alongside of Windows 7.  When I get to allocating disk space, it appears that Ubuntu is already installed, but I know that it did not finish installing.  Any ideas?  Thanks so much for any help you can give me.

---

### Post by marupingwl on 2011-01-11
This is the best and easy answer I have come across in google...this is the real works!!! Well Done

---

### Post by Tankerdog2002 on 2011-01-26
I can't get it to finish the install. My problem is not like those previously mentioned. 

Ubuntu 10.10 freezes halfway to three quarters of the way through the loading process. 

I've tried it on two different machines. I can't get it to install on either a laptop or a desktop. (Both are only a couple of years old) 

I've tried to let it take over the whole disc. I've tried specifying the partition. I've burned the disc from different sources, verified the Check sums, and tried every trick I could think of and it just locks up. I even tried loading the nVidia driver first.

I'm on my third day of working on this. 

I can load Jaunty, Karmic, or Lynx with no problems. Maverick Meerkat just doesn't work. Sometimes the bar only gets a quarter of the way through the process and then BANG it locks up like a clam out of water.

I see tons of postings on the web for help on this same issue but have yet to see a solution.

---

### Post by Tankerdog2002 on 2011-01-26
OK I solved this dilemma. 
I loaded Jaunty again so I could access my MBR that was hosed from the previous 10.10 freeze mess. Then I went into Win-XP disc manager, formatted the free space, and rebooted.

I downloaded the alternate CD.iso, burned it,  and used it to install Ubuntu 10.10 this time. I chose 'guided in lieu of 'manual. The alternate CD worked so much smoother. No glitches or hangups.

Seems to be working fine now. In fact, its lightening fast. 
 :popcorn:

---

### Post by Tankerdog2002 on 2011-01-26
Regarding the previous posts.

I just now discovered that my mouse causes freezing and hanging.

I kid you not. I was using a Verbatim-USB-96898 when synaptic suddenly froze up. The search screen cursor was still blinking when the event happened. I unplugged the mouse, went to touch-pad and no problems.

I remember reading somewhere in an Aussie forum about the RAT7 causing the same problem.

Just an FYI.

---

### Post by Tankerdog2002 on 2011-01-27
Well its day four and after the update everything went to hell in a handbag. Ubuntu 10.10 is locking up when the wind blows. All I can do is power off. This junk locks up just sitting there. Not to mention that the screen is flickering like a like a loose head-lamp. Lots of other weird stuff is happening also, too much for me to print here. I'm done with it. It's crap.:mad:

---

### Post by Minnie000 on 2011-02-05
I had the same issue with the capital in the username.  Thank goodness for this thread!  Problem solved!
Now if only somebody would type in brackets on that screen (no capitals), what a difference that would make!!
Thanks again guys!

---

