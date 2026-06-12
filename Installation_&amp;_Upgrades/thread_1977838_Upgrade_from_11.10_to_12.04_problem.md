---
title: "Upgrade from 11.10 to 12.04 problem"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by hyperhopper on 2012-05-10
Somehow my mother decided she should try to update her computer. No idea what she did wrong, but she called me to look at it and I see this

[http://i.imgur.com/DGv1B.jpg](http://i.imgur.com/DGv1B.jpg)


Is there any way I can fix the system while not deleting any files?


The top option results in the text going away but the purpleish screen staying on the screen forever without change untill the power button is pressed.

---

### Post by jadtech on 2012-05-10
this is all well and good your in recovery  and all , how ever with out a clue how you got there  or what the problems were  or anything else about the  computer its self how is it anyone can know  where to go  from here :) 

upgrades that go wrong are  never good news how ever I will bet unless your willing to just give up everything and go get a ISO  for a fresh install with any where from a day or 5  there is a way to get this going or at least salvage  any pictures and  personal files  there were before that  at least so don't give up on  it unless your just ina big hurry to get a working  computer back ..

how ever I am not sure what to direct you to do in recovery  at this post I just know in most situations clicking the  option for the last version can be an invitation to bigger problems depending various set up it could have been running ..

if you  don't know exactly  how  the update end up in recovery  and your feeling adventurous  maybe try rebooting  and see if you can read copy any of the errors messages and post them here for others to see  there are a lot of people here very good at knowing  what to do seeing a kew key bits of logs .. 

maybe also try to find out did the install go good if any strange messages  or such were seen, did the computer lose power or internet  during the down load or install  any facts  you can dig up would help ...

---

### Post by Bucky Ball on 2012-05-10
What is wrong with it? That is the grub menu. What happens when you hit return on the first entry???

(Looks like she upgraded, not updated. It would now be 12.04 LTS with that kernel I suspect.)

@jadtech: What error messages? The pic looks normal, just missing the last kernel which shouldn't prevent it from booting.

---

### Post by hyperhopper on 2012-05-10
> **Bucky Ball said:**
> What is wrong with it? That is the grub menu. What happens when you hit return on the first entry???

(Looks like she upgraded, not updated. It would now be 12.04 LTS with that kernel I suspect.)

@jadtech: What error messages? The pic looks normal, just missing the last kernel which shouldn't prevent it from booting.

I completely forgot, top message results in the text going away and the screen staying that color infinitely, with no change.

---

### Post by jadtech on 2012-05-10
> **Bucky Ball said:**
> What is wrong with it? That is the grub menu. What happens when you hit return on the first entry???

(Looks like she upgraded, not updated. It would now be 12.04 LTS with that kernel I suspect.)

@jadtech: What error messages? The pic looks normal, just missing the last kernel which shouldn't prevent it from booting.

my question  was how did  it get there a good upgrade will look for your password and boot up to the desk top  not  end up at the grub menu I have upgraded from 11.10 3 times and  have done  2 full installs ..

---

### Post by Bucky Ball on 2012-05-10
K. Reboot and when you get to that screen, hit 'e' to edit, find the line that ends in:

```
quiet splash
```... and add this to the end of that line (a space after splash):

```
nomodset
```Instructions to save and reboot are at the bottom of that edit screen ('x' and 'b' from memory but check). What happens?

---

### Post by kansasnoob on 2012-05-11
> **Bucky Ball said:**
> K. Reboot and when you get to that screen, hit 'e' to edit, find the line that ends in:

```
quiet splash
```... and add this to the end of that line (a space after splash):

```
nomodset
```Instructions to save and reboot are at the bottom of that edit screen ('x' and 'b' from memory but check). What happens?

Shouldn't that second command be:

```
nomodeset
```

---

### Post by hyperhopper on 2012-05-11
The line ends in

```
quiet splash vt.handoff = 7
```

And putting the nomodset or nomodeset between splash and vt.handoff=7 does nothing, same result

---

