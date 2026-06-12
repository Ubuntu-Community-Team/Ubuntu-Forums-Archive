---
title: "installed but booting to windows"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by Kenneth David on 2012-11-19
first yes I'm a noob. 
I installed ubuntu it said it was installed and the partition for ubunto shows 6gigs of the 200+ used but it boots into windows and when i try to choose ubunto it isn't an option.
can i get it to boot to ubuntu with out reinstall?
if not do in need to reformat the partition it used for ubuntu and if so what file forma do I use. 
windows seven.
thank you from the noob.

---

### Post by aliddell on 2012-11-19
This is because GRUB was improperly installed or not installed at all to your master boot record (or you installed Windows after you installed Ubuntu and Windows overwrote it).

There's a pretty good tutorial [here]("http://www.av8n.com/computer/htm/grub-reinstall.htm") on how to fix that.

---

### Post by Kenneth David on 2012-11-19
> **aliddell said:**
> This is because GRUB was improperly installed or not installed at all to your master boot record (or you installed Windows after you installed Ubuntu and Windows overwrote it).

There's a pretty good tutorial [here]("http://www.av8n.com/computer/htm/grub-reinstall.htm") on how to fix that.

thank you
WOW not sure i understand most of that. It may be easier to wipe the whole thing and start over. 
it lost me at 2. open a shell window and become root. 

my machine boots fine but it doesn't see ubuntu.

---

### Post by Bucky Ball on 2012-11-19
Welcome to the forums.

Try Boot Repair. Not sure if it's in the repos. Have a look (Synaptic Package Manager or Software Centre). If not, look here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You will find that a lot easier.

---

### Post by Kenneth David on 2012-11-19
> **Bucky Ball said:**
> Welcome to the forums.

Try Boot Repair. Not sure if it's in the repos. Have a look (Synaptic Package Manager or Software Centre). If not, look here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You will find that a lot easier.
Working know. Fingers crossed

---

### Post by Bucky Ball on 2012-11-19
Good luck. The other thing you might try if it's still happening is to start hitting the shift key after the BIOS screen. That should bring up the menu list where you can choose what to boot.

If you are still not getting that list, try Grub Customizer, also very easy, and check that the list is set to appear and stick around for awhile until you make a decision:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by Kenneth David on 2012-11-19
I don't say this every day but I love you man.
Everything is as should be. 

> **Bucky Ball said:**
> Welcome to the forums.

Try Boot Repair. Not sure if it's in the repos. Have a look (Synaptic Package Manager or Software Centre). If not, look here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You will find that a lot easier.

---

### Post by arpanaut on 2012-11-19
With only 6gigs partitioned for Ubuntu, You should be careful how much you install and download; space could get tight in a hurry.

---

### Post by Kenneth David on 2012-11-19
the partition is 250 but i could see the 6 gigs used. that's how i knew it was installed.

> **arpanaut said:**
> With only 6gigs partitioned for Ubuntu, You should be careful how much you install and download; space could get tight in a hurry.

---

### Post by arpanaut on 2012-11-19
> **Kenneth David said:**
> the partition is 250 but i could see the 6 gigs used. that's how i knew it was installed.
I see,
Pardon the interruption... ):P

I must read more carefully in the future!

---

### Post by Bucky Ball on 2012-11-19
> **Kenneth David said:**
> I don't say this every day but I love you man.
Everything is as should be.

Ha. All good, happy to help and glad it's all happening.

Please mark thread as 'Solved' from Thread Tools at top right to help others. ;)

PS: You might still like to try Grub Customizer anyway. It is great for tweaking the menu in many ways and getting rid of unwanted kernels from the list (which will expand after after updating for awhile).

---

### Post by Kenneth David on 2012-11-20
i will gige the grub customizer a shot thank you  
marked solved  

> **Bucky Ball said:**
> Ha. All good, happy to help and glad it's all happening.

Please mark thread as 'Solved' from Thread Tools at top right to help others. ;)

PS: You might still like to try Grub Customizer anyway. It is great for tweaking the menu in many ways and getting rid of unwanted kernels from the list (which will expand after after updating for awhile).

---

### Post by Kenneth David on 2012-11-20
i will give the grub customizer a shot thank you  
marked solved  

> **Bucky Ball said:**
> Ha. All good, happy to help and glad it's all happening.

Please mark thread as 'Solved' from Thread Tools at top right to help others. ;)

PS: You might still like to try Grub Customizer anyway. It is great for tweaking the menu in many ways and getting rid of unwanted kernels from the list (which will expand after after updating for awhile).

---

