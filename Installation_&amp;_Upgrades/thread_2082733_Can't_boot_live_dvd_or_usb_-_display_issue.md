---
title: "Can't boot live dvd or usb - display issue"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by knichel on 2012-11-10
I downloaded the 12.10 kubuntu iso and burned to a DVD, but when I boot from the dvd,  I get really bad display.
[IMG]http://i49.tinypic.com/977byc.jpg[/IMG] 
&
[IMG]http://i49.tinypic.com/6sumtu.jpg[/IMG]
both are flickering and moving . I re-downloaded the iso and tried using a Flash Drive to install but get same problem. The MD5 matches.

Any thoughts?

---

### Post by 2F4U on 2012-11-10
Would you give us some information about your hardware?

---

### Post by knichel on 2012-11-10
I am using an ASUS Laptop G71G with 
Video: GeForce 9800M GT / 512MB.  
HD: 2 HDD - 320G and 750G
RAM: 6GB

I am currently using Kubuntu 11.10.

Thanks for offering to help.

--
Mike

---

### Post by efflandt on 2012-11-10
Not sure about 12.10, which I have not tried yet do to people having driver video issues.  But I do know that with nvidia graphics I had to use **nomodeset** kernel boot parameter for 12.04 live/install iso on USB.  And, although, each Ubuntu version can be a little different about whether that is required or not, it does not hurt to try **nomodeset** first if having video issues.

Press any key when you first see symbols at the bottom, select your language, then F6 allows you to select common boot parameter options (spacebar to X).

---

### Post by knichel on 2012-11-10
Thanks, I will give that a try.

---

### Post by knichel on 2012-11-11
That did the trick.  Thanks.

---

