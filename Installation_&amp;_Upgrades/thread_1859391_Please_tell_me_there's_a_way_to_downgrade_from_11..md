---
title: "Please tell me there's a way to downgrade from 11.10 to 11.04"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by modestmachine on 2011-10-13
The FAQ said there's no dumb questions, so I'm banking on that for my second post.

Long story short I am not happy with 11.10, and even though I respect that a day 1 install might not have been a good idea, the power of hindsight doesn't make this sting any less.

Quick reasons for wanting to downgrade/revert :
*all applications run notably slower
*I don't see any actual improvements
*My wifi doesn't work anymore, and the solution I had used for when I installed 11.04 (my first ubuntu install ever) no longer works; I click the connection icon in the top right and it Wireless Networks is greyed out as well as 'device not ready (firmware missing)'

Anyone know of a way to downgrade? Or a fix for the wireless, I'm going to keep looking for that as it might sooth the pain until everything else is fixed.

Thanks

EDIT: Just a note about the Wi-fi, I think I'm missing drivers (during the install it said b43, the broadcom driver or something, could not be installed, I forgot what it was at the time and I didn't really have a choice) and doing sudo lshw tells me 'network - DISABLED'; I recognise this from before when the wireless wouldn't work.

---

### Post by zvacet on 2011-10-13
AFAIK only way to downgrade is to reinstall previous version.

---

### Post by RJARRRPCGP on 2011-10-13
> **modestmachine said:**
> The FAQ said there's no dumb questions, so I'm banking on that for my second post.

Long story short I am not happy with 11.10, and even though I respect that a day 1 install might not have been a good idea, the power of hindsight doesn't make this sting any less.

Quick reasons for wanting to downgrade/revert :
*all applications run notably slower
*I don't see any actual improvements
*My wifi doesn't work anymore, and the solution I had used for when I installed 11.04 (my first ubuntu install ever) no longer works; I click the connection icon in the top right and it Wireless Networks is greyed out as well as 'device not ready (firmware missing)'

Anyone know of a way to downgrade? Or a fix for the wireless, I'm going to keep looking for that as it might sooth the pain until everything else is fixed.

Thanks

EDIT: Just a note about the Wi-fi, I think I'm missing drivers (during the install it said b43, the broadcom driver or something, could not be installed, I forgot what it was at the time and I didn't really have a choice) and doing sudo lshw tells me 'network - DISABLED'; I recognise this from before when the wireless wouldn't work.

Sorry, in your case, you're required to burn the ISO and install from scratch.

Just get the 11.10 ISO and burn it. The easiest way! 

Please wipe the drive and try again. 

(Especially when it acts something like a malware-infested Windows.)

DO NOT do an upgrade-install.

---

### Post by Tweak42 on 2011-10-13
I'm not sure about downgrading but for speed you could try logging in using using the Unity 2D desktop. 

For the wireless try checking the "Additional Drivers" utility for the wifi broadcom drivers.  You will of course require a wired internet connection to get them.

---

### Post by modestmachine on 2011-10-13
Bonus : opening the rubbish bin opens the Movie Player.

Genius.

Looks like I'm going for a fresh install. I've been looking on the forums and the advice NOT to do upgrade install day one isn't as helpful as you might think.

Surely there should be some warning or something; as they say, prevention is better than the cure that tells you to prevent the bad thing from happening after it's happened.

Sorry if I sound rude, I am pretty peeved right now.

Thanks for the tips all round

---

### Post by Ginzell on 2011-10-13
Well, I appreciate this post because I haven't upgraded yet and I am so glad to have run across this before I did.  
Altho, I'm sorry for your troubles.


(I'd be crazy if I had to start over)

---

### Post by e79 on 2011-10-13
> **modestmachine said:**
> Bonus : opening the rubbish bin opens the Movie Player.

***Vade Retro Satana*** !!

---

### Post by antheia on 2011-10-13
I'm also regretting upgrading today. I can't *stand* unity/gnome3. I'm not the most technical person, but this feels like a very dumbed-down interface, and I'm not happy with it at all.

Looks like I'll need to burn the 11.04 cd and start over. And yes, I know it's my own fault for upgrading so quickly. Had I known what I was getting into, I never would have done it.

It would be nice if there was a way to revert back to the old look and feel without going through a complete reinstall. Ah well, nothing to be done for it now. Glad to get this off my chest, at least.

---

### Post by oldfred on 2011-10-13
With large hard drives today it is not difficult to have many installs.

I still consider Maverick 10.10 my working system. But I have Natty & 2 Oneirics, one was just testing & one is a clean install (should not be different at end). I also still have my 9.10 & 10.04 each is in a 20 to 25 GB partition with data in other partitions.

---

### Post by ubudog on 2011-10-13
> **RJARRRPCGP said:**
> Sorry, in your case, you're required to burn the ISO and install from scratch.

Just get the 11.10 ISO and burn it. The easiest way! 

Please wipe the drive and try again. 

(Especially when it acts something like a malware-infested Windows.)

DO NOT do an upgrade-install.

Make sure to back up your stuff first.

---

### Post by erniej on 2011-10-14
Installing 11.10 may have been the biggest mistake in my life, and I've been married twice. First I tried to upgrade, which was an absolute failure. What appeared on the screen after startup was a frozen screen. I couldn't close any open windows, and absolutely nothing worked. Then I went the download-and-burn-to-CD route. 

Now, whenever I try to open 11.10 I'm treated to a purplish screen. Every time. I managed to get this earlier version of 11.10 to open, but it too is a mess. I can't find a previous install of 11.04. I could only get Chrome running surreptitiously, since the Ubuntu software repository denies such an animal exists.

I am miffed, I tell you, MIFFED!

---

### Post by zvacet on 2011-10-14
@ [B][antheia]("http://ubuntuforums.org/member.php?u=603230")

[/B]Going back to Natty will solve your problem witj Unity and Gnome 3 for some time,but you will upgrade some day.If you don´t like Unity and Gnome3 install Xubuntu.Back up your files first,of course.

---

### Post by antheia on 2011-10-14
> **zvacet said:**
> @ [B][antheia]("http://ubuntuforums.org/member.php?u=603230")

[/B]Going back to Natty will solve your problem witj Unity and Gnome 3 for some time,but you will upgrade some day.If you don´t like Unity and Gnome3 install Xubuntu.Back up your files first,of course.

Thanks zvacet! That's an excellent point! I managed to do a bit of tweaking to make it more tolerable (I've got it sort of 'pretending' to look like gnome2), so I'll hold out for a couple of days and then see how I feel. 

Now to decide if I should go with mint, xubuntu, or kubuntu. I think I'm going to play with all three first and then decide. You know, sort of like what I failed to do with this upgrade.

---

