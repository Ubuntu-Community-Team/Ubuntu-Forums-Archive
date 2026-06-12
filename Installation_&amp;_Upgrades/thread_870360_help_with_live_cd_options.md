---
title: "help with live cd options"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by hockeyhead019 on 2008-07-25
ok guys so i got my cd the other day and went to run it and the options came up fine and i checked my memory and it passed all the test and had no errors. so i tried the run ubuntu without installing just running from the cd... so the loading bar bounces back and forth a couple times (i think it's about 5 times but i'm not sure) then it stops the screen goes black and then the busy box v1.1.3 (or whatever version it is) comes up with the promp so i let it sit without touching it and then it comes up with an error that says ata1.00 revalidation failed and then a loop comes up giving all these errors about an exception Emask and it says status DRDY.... so then i tried to see if my cd was messed up and went to the check cd for errors (or the name of that option which i believe is something to that affect) and it gives me the same thing...

any help would be appreciated 
thanks in advance

p.s. if you need to know anything about my computer ask and i'll try and answer the best i can :)

---

### Post by Pumalite on 2008-07-25
Post your specs

---

### Post by hockeyhead019 on 2008-07-25
ummm what specs you want?

---

### Post by Pumalite on 2008-07-25
Memory and graphics.

---

### Post by hockeyhead019 on 2008-07-25
ok you're gonna have to cut me some slack with me on this haha because i'm kind of new to this lol... but ok here goes
for mem i have a 250 gig HD which is a Hitachi HDT and then i think the graphics is an intel g33/g31 express chipset family... umm but i'm not sure about the graphics card... so i'm on windows xp so would you mind telling me where to find it?

---

### Post by Pumalite on 2008-07-25
I'm sure there is a place in Windows where you can find this information. Maybe 'Computer'

---

### Post by hockeyhead019 on 2008-07-25
ok i'm sure it's there... i'll dig around and be back quick cuz i have to eat... please don't leave lol... i'm a little desperate for help at this point lol and thanks in advance

---

### Post by hockeyhead019 on 2008-07-25
ok so that is my graphics card the i mentioned above and then my ram is 1 gb... anything else?

---

### Post by hockeyhead019 on 2008-07-26
***bump***

---

### Post by oldos2er on 2008-07-26
Don't worry, the forums are open 24/7.

 Have you tried running safe graphics mode?

---

### Post by hockeyhead019 on 2008-07-26
ya and it did the same thing... bounced back and forth a couple times and then went into the busybox... and at this point i've tried both versions of the desktop... the x86 and the x64 just to see if it would make any difference but there was no difference and both did the same thing and brought me to the busy box. i know that both disks are fine as i checked them on a buddy's computer... so i'm assuming that the problem is somewhere in my hardware maybe??

---

### Post by Pumalite on 2008-07-26
Did you install these CD's?

---

### Post by hockeyhead019 on 2008-07-26
no i didn't... but do you think that it would matter?

---

### Post by Pumalite on 2008-07-26
Up to now you have proved they can boot, but we don't know if they can install.

---

### Post by hockeyhead019 on 2008-07-26
ok well then i'll try the x86 one because i have another computer here that i can try it on and then i'll post after that... once again thanks for your help pumalite... even if we don't solve the problem i appreciate you taking the time to help :)

---

### Post by Pumalite on 2008-07-26
Good luck! Let us know.

---

### Post by hockeyhead019 on 2008-07-26
ok tried the x86 version and it worked like a charm... so i don't think that it's the cd which is messed up but instead i'm assuming that it's something in my computer which is acting up funny... o and i've come to the conclusion that i'm an idiot for getting the x64 version... because that's not for my computer haha... i'm on a intel pentium dual core (if that's any help)

---

### Post by Pumalite on 2008-07-26
Try the 32 bit in your Dual Core.

---

### Post by hockeyhead019 on 2008-07-26
ok you lost me haha... you want me to change my core to 32bit? can you try and explain a little more indepth haha... yes i am a noob with this stuff :D

---

### Post by Pumalite on 2008-07-26
Ubuntu has a 32 bit version and a 64 bit version. I'm saying use the Ubuntu 32 bit in your Dual Core computer

---

### Post by hockeyhead019 on 2008-07-26
so you're saying i have to completely re-dowload the iso image then?.... wait ok i think i have that version.. because when you go to download in the ubuntu website it gives you the option of the 64bit or the standard computer right? so i already downloaded the standard computer and that's what i've been calling the x86 version lol... i don't know i might be wrong but that's what i've been trying (and i tried the other version as well still nothing)

---

### Post by Pumalite on 2008-07-26
Dowload from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Choose 'Standard personal computer'
Follow this guide to burn:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less, do not use CD-RW, check CD integrity before install.

---

### Post by hockeyhead019 on 2008-07-26
once again you da man... thanks for your help i'll try this and let you know how it goes... and thanks again for your time it truely is nice to have somebody care and give good advice :)

---

### Post by hockeyhead019 on 2008-07-26
ok md5sum... fine.... burning to a cd-r (700mb compact disc recordable)....

---

### Post by hockeyhead019 on 2008-07-26
ugh ok now i'm really getting frustrated... ok so i remade the cd and it comes on fine but then jumps to the same error... it gives me the busy box v1.1.3 and all that junk again... but now half way through the continuous errors it says that sychronizing SCSI failed without progress... any ideas before i throw my computer through the wall? haha

---

### Post by Pumalite on 2008-07-26
Is your hard drive formatted? Is it recognized and well configured in BIOS?
If above OK; you might try editing your boot line and adding all_generic_ide at the end.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by hockeyhead019 on 2008-07-26
haha WOOOOOOO HOOOOOOOOO when i added the all_generic_ide at the end of the boot line it did it :D you really have no idea how happy i am now... so now my question is how do i have it install and not run into this problem? or should i be set now that it loaded?? and another question... i have the 250 gig hard drive so how much room should i allot for ubuntu?? while going through the install process i get to step 4 about the partitioning and it says that it wants to resize the windows portion to 74.3 gigs and wants to give ubuntu the rest of it? any advice?

---

