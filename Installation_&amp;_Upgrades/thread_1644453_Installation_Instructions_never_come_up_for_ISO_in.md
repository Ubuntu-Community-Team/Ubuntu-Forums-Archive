---
title: "Installation Instructions never come up for ISO install"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2010-12-13
I downloaded Ubuntu 10.04LTS ISO and burned it to a CD as an ISO image. I boot the computer and the computer seems to boot from the Cd (although I never changed the boot startup). The monitor shows purple screen with Ubuntu displayed and 5 dots cycling in color. This goes on and on for 20 minutes or more and nothing different ever happens.  I thought instructions/choices were supposed to come up when booting from CD? Is this working correctly? How do I get this CD to install Ubuntu?

---

### Post by Quackers on 2010-12-13
What graphics card are you running?
If it's an nvidia one press any key at the purple screen and then press F6 at the next screen. This will give you some boot options. Nomodeset seems to work well for nvidia cards, i915 options for Intel integrate graphics. You may need to try them all.

---

### Post by nrundy on 2010-12-13
Thanks, I'll try it now. I'm using nvidia card.

---

### Post by nrundy on 2010-12-13
Nothing happens when I press &quot;any key.&quot; If I press ESC or an F key then image changes to a whole page DOS screen with lines of writing displayed.  Could the ISO burn have gone wrong?  I don't know what "nomodoset" is.

---

### Post by Quackers on 2010-12-13
Possibly. Try booting from the disc again and this time tap the F6 key until a screen comes up giving you some options. One of them will be to check the cd for errors. Try that.

---

### Post by nrundy on 2010-12-13
this worked to bring up a menu. I selected English and then selected &quot;Install Ubuntu.&quot; But then the purple screen with the scrolling dots appeared again. I waited several minutes but nothing changed. Aren't I supposed to get more menu screen for repartitioning etc? Is the purple screen normal, do I just need to wait a long time?

---

### Post by Quackers on 2010-12-13
The purple screen is normal, but pressing F6 should have given you a screen where you could select to check the cd for errors.
I suggest you find the downloaded .iso file and check the md5sum

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by nrundy on 2010-12-13
I found the md5sum. I'll have to study that page. It's not clearly apparent to me what to do after browsing it. There's a lot of methods and I don't understand most of them plus which applies to me - Windows xp with iso of ubuntu.  Thanks for all your help though. I really appreciate it!

---

### Post by Quackers on 2010-12-13
Near the bottom of that link I posted is a link to this page

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by nrundy on 2010-12-13
I think it was a bad ISO burn. I redownloaded Ubuntu, checked the MD5; it matched. Burned new CD and I'm posting this in the TRY mode of Ubuntu.

Thanks Quackers. You were a big help.

---

### Post by Quackers on 2010-12-13
Aha! Good news :-) I hope you enjoy yourself!

---

