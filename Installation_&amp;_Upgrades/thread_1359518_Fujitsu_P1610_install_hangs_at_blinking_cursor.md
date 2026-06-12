---
title: "Fujitsu P1610 install hangs at blinking cursor"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by nsfx on 2009-12-19
My bootable Karmic Koala USB key hangs at a blinking cursor. The LED on the key is blinking rapidly as it does when it's being read from, but I let the thing run over night (12+ hours) and the activity LED is still blinking and I'm still at a black screen with a blinking cursor. I tried the second USB port on the netbook with the same results. Upgrading the BIOS also didn't help. I don't have another key presently to test, but that is my next step. In the mean time, any suggestions from the community? Thanks.

---

### Post by nsfx on 2009-12-20
For anyone interested, I side-stepped the problem by doing a PXE install.

---

### Post by jondoe on 2009-12-24
I guss it has to be the usb, I installed karmic recently with out any problem

Did you find a way to get the touch-screen rotaion working
I got it working partially, but not 180 degree rotation

---

### Post by KsLIVER on 2010-09-12
Old post i know...
 
But in your question about the rotation, I found this article in my travels while I was trying to get my touchscreen to work.  I got the button to work and rotate properly, but I'm still trying to get the touch part to work... :).
 
[http://liliputer.blogspot.com/2010/08/p1510d-ubuntu-1004-better-ipad.html](http://liliputer.blogspot.com/2010/08/p1510d-ubuntu-1004-better-ipad.html)
 
Hope that helps (or anyone else that has come accross here).

---

### Post by taylorjonl on 2011-03-18
I was having the same issues with getting my USB key to boot, it would just hang at a blinking cursor.  I used the Universal USB Installer from the Ubuntu site on my Windows 7 box.  To fix my issue I opened a command prompt as admin then:

diskpart
list disk
select disk <disk#>
list partition
select partition <partition#>
active
exit

After this my Dell Mini 11 booted fine and I am installing as I write this.

---

### Post by taylorjonl on 2011-03-19
Just an update, if you are using the instructions from the Ubuntu download page that call for using the universal installer, make sure you choose the netbook labeled ISO, I chose the plain 10.10 label and it wouldn't install correctly, finally was going to go to 10.04 and try it out when I noticed the netbook label.  So I retried the 10.10 after rebuilding with that option and it worked without a hitch.

---

### Post by treblemaker48 on 2011-03-19
this sound similar to the problem I am having. I installed Mavericks to an old HP laptop from a disc I burned. My screen is not black though. I can move the cursor around but there is nothing to click on. The keyboard has no effect either. If I restart by forcing a shut down... hold off key, I get the same thing. I am ignorant about what to do next. Any help please.

---

