---
title: "Unable to boot thru Linux Version 3.13.0-24 after Upgrade to 14.04 LTS"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by shravan.vaddadi on 2014-04-15
Hi,
Today i have upgraded my PC from Ubuntu 13.10 to Ubuntu 14.04 LTS beta but after the Upgrade i am unable to boot with Linux 3.13.0-24-generic
and i am getting this error "Serious errors were found while checking the disk drive for Press **I** to ignore **S **to skip mount **M** to Manual intervention"
But i am able to Boot with the Old Linux Kernel 3.11.0-20-generic.

I tried to do the following after checking the fourm
fsck /dev/sda1
fsck -Aa
but it returned that file system is clean

---

### Post by alias5 on 2014-04-19
I upgraded from 13.10 to 14.04, too.  I can not boot to kernel 3.13.0-24 either.  I am able to boot to 3.11.0-19, though.  Although, I have not seen the same errors as you.  Mine just hangs with a flashing white cursor on the screen.

---

### Post by shravan.vaddadi on 2014-04-20
Hi if u try giving ESC Key while booting to Kernel 2.13.0-24 you may find what are the errors

---

### Post by alias5 on 2014-04-22
My issue is SOLVED.

I resolved mine by rebooting back into 3.13.  I opened "Software & Updates".  I clicked on the "Additional Drivers" tab.  I chose the 331.38 Nvidia driver and rebooted.  The first time, my Atheros wifi would not work.  I'm not sure if it was after waking from sleep or original boot.  Either way, I've rebooted and it is working correctly now (even after sleep).

Hope this helps.

---

### Post by shravan.vaddadi on 2014-04-23
Hi I am not able to login during start up only with 3.13 version and how can i do Software updates

---

### Post by raja.genupula on 2014-05-02
I have seen your PM , you still with this issue ?

---

### Post by shravan.vaddadi on 2014-05-07
Hi,
Yes I am still facing this Issue.

---

### Post by raja.genupula on 2014-05-07
Put a Live CD or USB , then run live session.
after that open terminal in live session

now type 

> sudo fsck -y /dev/sdaXY

That X,Y are nothing but the partition number where you have installed The Ubuntu.

for example if you have installed Ubuntu in /dev/sda1 then run it as

> sudo fsck -y /dev/sda1

After running that save the log and post here and restart your system and check about the issue status and let me know what happen.

---

### Post by shravan.vaddadi on 2014-05-10
Hi,
Can i Use Ubuntu 12.04 Live CD

---

### Post by raja.genupula on 2014-05-10
yes you can use.

---

### Post by shravan.vaddadi on 2014-05-28
Hi,
Thanks everyone for the messages and the issue was solved today after checking the below Link
[ttp://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-temp-could-not-be-mounted]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-temp-could-not-be-mounted")

---

