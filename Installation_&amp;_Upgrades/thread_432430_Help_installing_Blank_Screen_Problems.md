---
title: "Help installing/ Blank Screen Problems"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by thmst30 on 2007-05-04
Every time I try to install Ubuntu, or run the Live CD it won't start up.  I get to the screen with the Ubuntu logo and the orange progress bar.  Once the bar fills all the way up the screen goes blank and stays that way.  It doesn't go anywhere.  Can someone help me out, I looked but couldn't find any information on this.:confused:

---

### Post by t.storbeck on 2007-05-04
[CENTER]I have the same exact problem... someone please help![/CENTER]

---

### Post by finalzero on 2007-05-04
when you boot with the CD, you will see the Grub startup menu, press F6 to edit the menu list, you should now see a black and white screen.

You should already have highlighted the default option which will be the first item in the list. Press **e** to edit the boot parameters.  Delete the following words from the paramenters:

**quiet**
**splash**

Save the changes and then press **b** to boot up with the new parameters, you should now see linux booting without splash screening enabling you to view the boot up messages and any errors.

Fz

---

### Post by auditory on 2007-05-04
i got the same problem,

without quiet option, i got the following message and
booting stops

last three lines:

[48.450663] Total of 2 processors activated (13356.40 BogoMIPS).
[48.450852] ENABLING IO-APIC IRQs
[48.451069] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

Interestingly, i got the same situation and message with FC6.
Edgy also doesn't work.

---

### Post by JBlade on 2007-05-11
I'm also in the same boat as auditory is, where those are my last lines before hanging...has any solution come to this?  I've yet to find one by Search, but that doesn't mean one isn't there. 

Much appreciated :)

---

### Post by dcskater_12 on 2007-05-11
I had this problem but when i plugged in my acer flat screen it worked? i dont know why but i  tihink it could just be a resolution problem or something but if you are using an older monitor that could be your problem

---

