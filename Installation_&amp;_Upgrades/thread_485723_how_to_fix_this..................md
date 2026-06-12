---
title: "how to fix this.................?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by saurabh kakkar on 2007-06-27
[SIZE="4"]hi
    i recently installed ubuntu 7.04 from alternate CD .i am having 98 on my c : and   
xp on d drive so i created 5 gb partion and installed ubuntu on it also installed grub on my sys now my 98 is working fine but xp is not   loading giving this  error 
<windows root>\system32\hal.dll>
what should i do so that my 98 , xp  and ubuntu run plz provide the steps[/SIZE]

---

### Post by Jellyffs on 2007-06-27
Hi,

You lost windows boot loader. Have a google for "hal.dll"

---

### Post by Herman on 2007-06-27
Hello saurabh kakkar,
It could be that you just need to edit your boot.ini file with the correct partition number.
Take a look in this link and see if it helps you, [                                        hal.dll is missing or corrupt]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt").

---

### Post by saurabh kakkar on 2007-06-27
> **Herman said:**
> Hello saurabh kakkar,
It could be that you just need to edit your boot.ini file with the correct partition number.
Take a look in this link and see if it helps you, [                                        hal.dll is missing or corrupt]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt").

thanks a lot for the link its really usefull but i have rectifird problem by using windows cd repair feature i used
two commands :
bootcfg/rebuild
fixboot

---

### Post by Herman on 2007-06-27
:D Thank you for your feedback and sharing how you fixed it, I added that info to the link, I hope you don't mind. It might help someone else with the same problem.
Thanks again,
Regards, Herman :D

---

### Post by saurabh kakkar on 2007-06-28
> **Herman said:**
> :D Thank you for your feedback and sharing how you fixed it, I added that info to the link, I hope you don't mind. It might help someone else with the same problem.
Thanks again,
Regards, Herman :D

no need for thanks buddy i think its my duty u r doing a good job for noobs like us 

just wana know its ur bolg  ?

---

### Post by Herman on 2007-06-28
Thanks saurabh kakkar, :D
>  just wana know its ur bolg  ?
You want to know if that's my blog? Yes, it is, I take care of it for a hobby. I try to help people who have booting problems and collect information on boot loaders and how to fix them. I am mainly learning about the GRUB boot loader  but I also like to learn about other boot loaders and all kinds of other things that affect booting up as well. 
It is my pleasure if I can help people. And thanks again for your help too.
Regards, Herman :D

---

