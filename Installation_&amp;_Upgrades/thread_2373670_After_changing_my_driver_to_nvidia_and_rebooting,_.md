---
title: "After changing my driver to nvidia and rebooting, linux doesnt open and shows error m"
date: 2017-10-08
forum: Installation &amp; Upgrades
---

### Post by alex4123 on 2017-10-08
I have a dell inspiron 35558 laptop with NVIDIA geforce 920m graphics card.I recently tried changing the default nouveau graphics driver to nvidia driver (which i urgently need for cuda programming) by typing some commands from the internet and once successfully done, i rebooted the computer. But, now it shows the following the message which i have attached and the booting is not proceeding..how do i open the os again?Plz help!

---

### Post by Bashing-om on 2017-10-08
alex4123; Hello - Welcome to the forum .

Best here if you provide the link to what guide you followed:
> 
 by typing some commands from the internet 

(Ouch !)
Save a lot of hassle to find out what the state of the system is .

If you boot up from a recovery console OR boot with the nomodeset boot parameter - what results ?
[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

We need to know what you did in order to know what to do to Un-do .

Once you are at a terminal we can look at what is installed and what is needed .


keep in mind this is 'buntu
[INDENT][INDENT]with time and effort ( and a liveDVD(USB) )
[INDENT][INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubfan1 on 2017-10-08
You probably don't need bumblebee. Check the UEFI settings for video, you might need to select discrete, vs interated or hybrid.  If you then get to login, but it just loops back to login, but you can login to the guest account, you need to clean up the "hidden" dot files (those whose first character is a period).

---

### Post by alex4123 on 2017-10-08
Thanks for the reply... I changed the quiet splash parameter to nomodest parameter and it worked. But the problem is that at every time i boot i have to change to nomodest parameter, otherwise the result remains the same.

---

### Post by alex4123 on 2017-10-08
Could you please tell the steps to clean up the "hidden" dot files which you stated above?

---

### Post by Bashing-om on 2017-10-08
alex4123; Making progress;

> **alex4123 said:**
> Thanks for the reply... I changed the quiet splash parameter to nomodest parameter and it worked. But the problem is that at every time i boot i have to change to nomodest parameter, otherwise the result remains the same.

Still want to know what you did ..

And now that we have access to a terminal ;
Post back - Between Code Tags. please :
```

lspci -k|grep -iEA5 'vga|3d'

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to see what the hardware is -- and prepare to clean up and match a driver.

[INDENT][INDENT]it's a process[/INDENT][/INDENT]

---

