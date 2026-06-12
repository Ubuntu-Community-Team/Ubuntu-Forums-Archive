---
title: "Jaunty boot problem on MacMini with PC keyboard"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JohnFante on 2009-03-26
Let me start by saying that I have very little Mac esperience. So excuse me in advance if the answer to my qustions are obvious.

I have just bought a MacMini PPC G4. I am running it with a Logitech Media Keyboard Elite Keyboard and a Logitech Revolution mouse and it runs fine with OS 10.4.11.

My problem is that I can't get the machine to boot from the Jaunty CD i have burned from the daily build reposatory (24.3.09 build).

I have tried to hold down the C button on boot with no succes (the CD is in the drive). I have tried to hold down Windows, Alt, O and F (as far as I know the right combination on PC keyboard) and I have also tried to hold down the Alt key alone. But all with no succes. The macine rebootes, plays the chime and then boots Max OS X. No openfirmware prompt or boot menu.

I have also tried to go into system preferencen and set it to boot from the CD next time. The problem is here that I can't see the Januty CD in the different boot alternatives. The OSX install disc comes up fine when i put that in the machine but not the Januty disc.

The last problem is proberbly caused by a bad burn (if jaunty is supposed to come up as a boot alternative) but should't I be able to get in to openfirmware with my keyboard?

When I installed OSX the machine said that it could'nt recognize my keyboard and told me to press the key besides shift. When I did that everything worked fine. Afterwars 

I have googled my problem and found out that Macs are know to have problem with cheap PC keyboards. How can test my keyboard to see if that is the case for me? I have installed Logitech Control Center but only my mouse comes up in the preference menu so maby here is the probelm!?!? 

Fineally if I would like to run 8.10 is it the alternate build I have to burn? There is no live (desktop) version in the reposatory - as far as I can see.

Thank you very much in advance.

---

### Post by Ekos on 2009-03-26
I don't mean any disrespect, but did you download the right version?
[ubuntu for PPC thread]("http://ubuntuforums.org/showthread.php?t=427714")
Other than that I think you might have tried (Bypass startup drive and boot from external CD.... CMD-OPT-SHIFT-DELETE) already, I am not sure of your key layout.

---

### Post by JohnFante on 2009-03-26
No problem :-)

I found a solution to my problem. It is my PC keyboard that dosn't work well with Mac. I borrowed a Mac keyboard and now it boots fine from CD.

The only problem is that Jaunty suddenly turns off the video signal just before it has booted to desktop. I have tried the most of the other kernals but so far with no succes.

I have checked the CD and it is ok.

Any suggestions to what boot options works on a mac mini?

---

### Post by avtolle on 2009-03-26
I'm not testing 9.04, but at the second boot prompt, have you tried "Live video=ofonly" (w/out the quotation marks, of course)?

---

### Post by JohnFante on 2009-03-27
Yes I have. Same problem.

It turns of the video signal and continues booting, playing the boot sound and everything. Strange probably some sort of bug.

If I want to go back to 8.10 is the alternate build the right one to get?

There is no desktop iso here: [http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

---

