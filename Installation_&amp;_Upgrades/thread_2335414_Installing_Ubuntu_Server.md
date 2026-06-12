---
title: "Installing Ubuntu Server"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by LaJuan on 2016-08-28
I have a Dell, 12.5TB (two 250GB HHD and 6 2 TB HHD), Intel i7CPU, 8GB, 2U server. Ubuntu 16.04 Server was installed but, the person who did the install didn't write down the username and PW. So, I figured he just boot to CD and reinstall Server again. Looks like he never finished the first install and is stuck. I have tried to get the unit to boot from the CD but, can't seem to access the bios due to the raid. Looked inside the raid menu and doesn't give any options to boot from CD. Says boot options is set in bios. We are at a complete lost as to what to do next. I've done a lot of desktop installs but, no server installs. Is there a way to get the unit to boot from CD so we can reinstall Server/ Also, do we have to use server or can we install desktop and still have access to all the storage devices?

---

### Post by SeijiSensei on 2016-08-28
Can you boot from a [USB drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")?  You may need to muck around in the BIOS to change the order of boot devices.

---

### Post by 1clue on 2016-08-28
Your bios for the motherboard should allow entry first. You should press F2 when the screen first appears.  Or hit power and hold the F2 key.

---

### Post by LaJuan on 2016-09-04
Thanks guys!!!!!!!!!!!! After speaking to the community, I the options provided in this thread would not work since the BIOS was locked from factory. I had to dump the CMOS an order to enter the BIOS. I'm in the process of helping him setup the system. I haven't done many server installs but, I'm way more knowledgeable of Ubuntu then he is since he has never done any type of install at all....

---

