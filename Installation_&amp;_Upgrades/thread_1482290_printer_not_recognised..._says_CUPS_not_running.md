---
title: "printer not recognised... says CUPS not running"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Ceejay34 on 2010-05-13
Since i upgraded to 10.4 my printer doesnt work. My Canon IP 4200 printer is attached via USB. If i turn it on nothing happens.
I look in the online help it says CUPS isnt running. How do i turn this on? I cant find it.

Help is greatly appreciated.

---

### Post by ratcheer on 2010-05-13
Run "sudo service cups start" and it should work. If it does not continue to start across system restarts, install package bum, run it as sudo, and check  cups so it will always start.

I can't guarantee it will work for you, but it worked for me.

Tim

---

### Post by Ceejay34 on 2010-05-13
Thanks! That did the trick. I will now reboot and hope it sticks. thanks again

---

### Post by ratcheer on 2010-05-13
You are welcome.

Tim

---

