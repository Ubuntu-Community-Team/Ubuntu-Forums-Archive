---
title: "Live usb ubuntu - panic"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by m1ody on 2013-08-23
Hi, 
I just made an live usb (ubuntu 12.04 32bit)
with LiLi and get kernel panic. 

[IMG]http://imageshack.us/a/img24/1996/m038.jpg[/IMG]


thx for help

---

### Post by sudodus on 2013-08-23
Welcome to the Ubuntu Forums :-)

You will get much better help, if you tell us more: Please specify the computer, brand name, model, cpu, ram (size), graphics chip/card, wifi chip/card is any).

Did you check with md5sum, that the downloaded iso file is correct?

Did you try to boot another computer with that same USB drive?

I have not used LiLi. It might be good, but you can also try other tools to make the USB boot drive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by m1ody on 2013-08-23
I've tried at 3 pc's and all results are the same -  kernel panic.
Imho there is no problem with a pc but with the live usb. 
Check sum is correct - md5sum : 90a4c7bd3901cd980cd4b48198e84eb1. 
Now i will try use other tools to make the live USB. 
Seems to me that LiLi and this version ubuntu didn't work well or i done something wrong during instalaction  ... but where and what ? 
Thanks Sudodus for help.

---

### Post by sudodus on 2013-08-23
Good luck with some other tool :-)

If you don't need persistence and it is OK for you to use commands in a terminal window, cloning with ***dd*** has a high success ratio. See this link

 [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

