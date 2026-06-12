---
title: "mouse jumps to upper left top corner every 10 seconds"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eightdollarbeer on 2009-12-18
ive been having a problem the mouse cursor jumps up to the left top corner every xx seconds. this happens despite the mouse being plugged in. i also have synaptic touch.

when i initially did the upgrade all was fine so i decided to use the cd and fresh install test and there the mouse problem was .
this problem happens when compiz is off and on.

 so i reinstalled karmic and did the upgrade again all seemed fine for a few days but now the problem has reappeared.
its got to be the most annoying problem ive ever had with ubuntu.
if anyone has any ideas on this much thanks.

---

### Post by LKjell on 2009-12-18
When my laptop behave like that I try to clean it and **dry** it. If it does not work a few bashing and smashing on the pad.

---

### Post by eightdollarbeer on 2009-12-18
> **LKjell said:**
> When my laptop behave like that I try to clean it and **dry** it. If it does not work a few bashing and smashing on the pad.

yea i wish it was hardware. laptop is clean . ill give it a few days and switch back to karmic if its not resolved.

---

### Post by phillw on 2009-12-18
Hi,

have u had a look over here --> [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Has various options you can 'play' with. At the least you should be disable to the touch-pad and use your mouse.

Phill.

---

### Post by ranch hand on 2009-12-18
An update probably put cheese up in that corner.  Feed your mouse.

---

### Post by eightdollarbeer on 2009-12-18
ok i seemed to have fixed it , i realize now both installs cd and update had this problem and both problems happened after a failed resume from lid. 
the fix that worked for me was fn+f7 this disables the synaptics on the hardware level , then i hit it again to re-enable the hardware and problem has stopped "for now". good enuff for me 
if anyone wants to confirm this and do a botched suspend and watch their mouse hide in the corner do-fix etc etc 
i dont know if i should mark solved

thanks for the help

---

### Post by ranch hand on 2009-12-18
You should probably recreate the problem and then, while it is in that condition, use "ubuntu-bug" to report the bug.  That will send the right logs to Luanchpad.

Good work by the way.

---

### Post by eightdollarbeer on 2009-12-19
well i was wrong problem is back on new kernel today . ill try the bug thin after reboot

---

### Post by Hiram on 2009-12-19
> **eightdollarbeer said:**
> well i was wrong problem is back on new kernel today . ill try the bug thin after reboot

are you by any change on a macbook or an other laptop with acceleration sensors? Since jumping to a specific points sound like a joystick plugged in and accelsensors for macbooks are detected as joysticks since a couple of weeks

---

### Post by Amaranth on 2009-12-20
Oh yeah, I had a lot of fun with that one. Picked up my laptop and moved it around to move the cursor so I could open a terminal and turn that dang thing off. :)

---

### Post by phillw on 2009-12-20
> **Amaranth said:**
> Oh yeah, I had a lot of fun with that one. Picked up my laptop and moved it around to move the cursor so I could open a terminal and turn that dang thing off. :)

That's made my day -- I'm still chuckling away at it :lolflag:

Phill.

---

### Post by caryb on 2009-12-20
Lets do the time warp again, It's just a jump to the left..............



Cary :guitar:

---

### Post by eightdollarbeer on 2009-12-20
> **Hiram said:**
> are you by any change on a macbook or an other laptop with acceleration sensors? Since jumping to a specific points sound like a joystick plugged in and accelsensors for macbooks are detected as joysticks since a couple of weeks

im on an acer 5335 , i can only guess its either todo with resuming a bad suspend or a built in unclutter function they are implementing.
the problem comes an goes with updates it seems

---

### Post by phillw on 2009-12-20
> **eightdollarbeer said:**
> im on an acer 5335 , i can only guess its either todo with resuming a bad suspend or a built in unclutter function they are implementing.
the problem comes an goes with updates it seems

This is why we need more victims (oops, volunteers) to test the development OS's on - I don't know of any acers kicking around, twiddling their thumbs doing very little ....... well.... except for a backup laptop at my Dad's works ... Hmmm, I'm sure it is due a checkup to see everything is working on it ....


:lolflag:

Phill.

---

### Post by phenest on 2009-12-21
I had this problem with a bluetooth mouse during Jaunty development. I think the problem was a driver issue connected to the xserver-xorg-input-synaptics package. I thought I reported this as a bug on LP, but I can't find it.

---

