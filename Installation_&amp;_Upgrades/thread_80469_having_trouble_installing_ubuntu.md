---
title: "having trouble installing ubuntu"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by armino41 on 2005-10-22
hey everybody this is my first post.
i am having trouble installing ubuntu . during the base system installation i get an error saying:"the deboot strap program exited with an error(return value1) check /ver/log/messages or see virtual console 3 for details"
it happens when the bar reaches 20% 
i am no pro in computers but i want linux installed.
i tried the live cd but i am having problems with that too. when it completes its loading my moniter will turn to off and i cant do anything about it exept restart the computer so any help will be appriciated.
greetz

---

### Post by armino41 on 2005-10-22
an advice on partioning will be good too

---

### Post by Iandefor on 2005-10-22
Let's see... well, try to do the install again, and see what it says below the progress bar right before debootstrap crashes. I've had similar trouble installing.
Did you check /var/log/messages or virtual console 3? 
 Saying "it completes its loading" is kind of vague. When? Like, right after you turn on and it spits out all the POST (Power-On Self-Test) stuff? Or after it's asked you about your locale and that stuff?
 How did you obtain your install/live CDs? Did you download and burn the ISO's or did you use ShipIt?
 If all else fails, you can burn the CD's again (try burning them at a slower rate to decrease the chances of screwing up the disc) or try a net install if you have a broadband connection- check the user documentation for details. 

Advice on partitioning? If you have less than 256 megabytes of RAM, it might be a good idea to make a swapdisk of at least twice the size of your current amount of RAM. Beyond that, there isn't that much to be done. Some people like to make a separate partition for their /home directory, which can mean that if your Ubuntu install ever gets hosed for software reasons, you still have your data.
Does this help?

---

### Post by armino41 on 2005-10-22
thanks for replying
i understood about the partioning but i didnt uderstand what u meant by "/var/log/messages or virtual console 3" how do i check it?
"When? Like, right after you turn on and it spits out all the POST (Power-On Self-Test) stuff? Or after it's asked you about your locale and that stuff?"
okay i will try to explain better when i putt the live cd it copletes its loading and when i should have seen a linux desktop my monitor turns off (like on sleep)
and i got the cds from shipment

---

### Post by Iandefor on 2005-10-25
On the LiveCD thing, what kind of hardware are you attempting to boot from? Like, how much ram, processor speed, video card, that style of thing.

---

### Post by munkymonkjr on 2005-10-25
the livecd is generally forgiving, but it does have issues on some hardware.

---

