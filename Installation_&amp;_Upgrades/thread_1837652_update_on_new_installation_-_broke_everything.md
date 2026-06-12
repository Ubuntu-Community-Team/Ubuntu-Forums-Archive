---
title: "update on new installation - broke everything???"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by adza on 2011-09-02
Hi there, 

this one is weird, it seems like i may have a conflict in some H/w somewhere (maybe), but every live cd works without an issue.. I have three specific questions that can help me on my journey on this issue.. 

1) how can i boot into the CLI only from Grub? thinking of doing this to re-run the restricted drivers on my video card installation, maybe the problem?? 
2) can anyone pass on some of their experience with newer hardware conflicts between 10.10 and 11.04 .. an explanation of my situation below.. 
3) can i restore a system to a previous state? ie, remove my system updates just performed? 

I have just upgraded (hooray!) to completely new PC - old one was 6 years old and while still running well (ubuntu rocks!), it was time for some new hardware.. system as follows..

AMD Phenom II Six Core processor
Asus M5A97 motherboard
Radeon HD6540 graphics
8GB Ram
Patriot 60GB SSD boot drive
WD Caviar Green 2TB Storage drive

so, both 10.10 and 11.04 run perfectly fine in live CD mode... when i install 11.04 however, system hangs after grub selection. 10.10 however, boots perfectly once installed... 

the problem just experienced (and why i'm posting from within live cd session) is due to the software updates (380MB) that are proposed when 10.10 is installed. updates run and then, same state as the 11.04 install, system hangs after grub... 

i'm stumped here, not sure why this would happen as this is the first time something like this has ever happened to me with ubuntu (user since dapper drake)... i've rebuilt this system once already into 10.10 after experiencing this, then this time (assuming it was the kernel update) didn't do any of the kernel updates etc.. still the same response... 

any suggestions on how to recover my system?

---

### Post by Hakunka-Matata on 2011-09-02
Hi, Welcome to the forums.

> **adza said:**
> Hi there, 

this one is weird, it seems like i may have a conflict in some H/w somewhere (maybe), but every live cd works without an issue.. I have three specific questions that can help me on my journey on this issue.. 

1) how can i boot into the CLI only from Grub? thinking of doing this to re-run the restricted drivers on my video card installation, maybe the problem?? 
2) can anyone pass on some of their experience with newer hardware conflicts between 10.10 and 11.04 .. an explanation of my situation below.. 
3) can i restore a system to a previous state? ie, remove my system updates just performed? 

I have just upgraded (hooray!) to completely new PC - old one was 6 years old and while still running well (ubuntu rocks!), it was time for some new hardware.. system as follows..

AMD Phenom II Six Core processor
Asus M5A97 motherboard
Radeon HD6540 graphics
8GB Ram
Patriot 60GB SSD boot drive
WD Caviar Green 2TB Storage drive

so, both 10.10 and 11.04 run perfectly fine in live CD mode... when i install 11.04 however, system hangs after [COLOR=Red]grub selection.[/COLOR] 10.10 however, boots perfectly once installed... 

the problem just experienced (and why i'm posting from within live cd session) is due to the software updates (380MB) that are proposed when 10.10 is installed. updates run and then, same state as the 11.04 install, system hangs after grub... 

i'm stumped here, not sure why this would happen as this is the first time something like this has ever happened to me with ubuntu (user since dapper drake)... i've rebuilt this system once already into 10.10 after experiencing this, then this time (assuming it was the kernel update) didn't do any of the kernel updates etc.. still the same response... 

any suggestions on how to recover my system?

Re: [COLOR=Red]grub selection[/COLOR]
[LIST]
[*]You get your grub menu?
[*]then choose what?,
[*]and it hangs?  yes?
[*]black screen? blinking cursor?
[/LIST]

---

### Post by adza on 2011-09-02
hey there, thanks for the response.. 

in answer, yep i get grub... i choose the first kernel option and then it hangs.. it hangs with a black screen and nothing happens.. .

from some reading, i believe this is due to the radeon graphics card... but i haven't been able to find an option that will make it work... :S

---

### Post by Hakunka-Matata on 2011-09-02
Once you break through, and can get to **System>Administration>Additional Drivers, **hopefully you'll get the correct driver downloaded automatically and it'll be fixed, till the next time.....................................
while it's hung, try F6 key.
bang on Shift Key from end of BIOS cycle till you get loaded, it might bring up the Grub boot menu options
also try holding down the Shift Key all the time for end of BIOS cycle till ????????????
here's a thread (a sticky big one) on the graphics hangup [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by adza on 2011-09-02
thanks for the help, i got it fixed by running the recovery mode from the grub menu and installing all the updates in there.. i think that the xserver-ati fix might have done the trick.. this seems to have resolved this issue...

---

### Post by Hakunka-Matata on 2011-09-02
Good, glad you are back in business

---

