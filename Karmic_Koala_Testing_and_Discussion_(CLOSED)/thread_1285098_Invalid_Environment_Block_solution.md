---
title: "Invalid Environment Block solution"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Madhatter14641 on 2009-10-07
A while back my grub install started throwing up an invalid environment block error. It took me a while to find the fix, so I figured that someone else might want it.

To boot into linux in the first place, push e in the grub menu, delete the save_env recordfail line, and press ctrl+x to boot.

Next, run these commands:

cd /boot/grub
rm grubenv
grub-editenv grubenv create
grub-editenv grubenv set default=0
grub-editenv grubenv list
default=0

This should give you a bootable system. Found the solution here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784"). Hope this helps someone!

---

### Post by jongkind on 2009-10-08
Thanks, you saved my day.

---

### Post by emarkay on 2009-10-08
This is also found here:

[http://ubuntuforums.org/showthread.php?t=1279720&highlight=environment+block](http://ubuntuforums.org/showthread.php?t=1279720&highlight=environment+block)

OP, mark thread as "Solved" and post additional info there.

Thanks!

---

### Post by rocksas on 2009-10-09
> **Madhatter14641 said:**
> A while back my grub install started throwing up an invalid environment block error. It took me a while to find the fix, so I figured that someone else might want it.

To boot into linux in the first place, **push e **in the grub menu, delete the save_env recordfail line, and press ctrl+x to boot....

Hello, I press "e" to turn on the PC, **but nothing happens**? immediately after it shows me the message:  

error invalid environment block 
   Failed to boot default entries.
Press any key to continue...

 any recommendation, I am doing wrong? 
 
 thanks

---

### Post by sub.mesa on 2009-10-09
Thanks, this solved my issue. Had this issue with the karmic server daily build, hope its fixed before release since boot problems aren't that sexy. :)

For those not able to reach the grub menu: i tried pressing and holding shift, which seemed to work cause i got the GRUB menu which i didn't got before. Then its possible to press "e" and follow the instrucitons above.

---

### Post by keithpeter on 2009-10-11
This worked, thanks.

Anyone any ideas on why this cropped up? It happened just after an update last weekend (today is the first opportunity I've had to work with the alpha box)

---

### Post by Peter09 on 2009-10-11
Rocksas - you need to get to the Grub menu first before push e.

To get to the Grub menu hit escape as soon as the Grub prompt appears.

---

### Post by Leu8 on 2009-10-11
> **rocksas said:**
> ...**but nothing happens**?
Hi rocksas,
use the live-cd of your karmic-installation and boot from it. Mount your harddrive, type in the terminal "sudo su" and follow the commands the first poster gave us.

---

### Post by VMC on 2009-10-11
> **Peter09 said:**
> Rocksas - you need to get to the Grub menu first before push e.

To get to the Grub menu hit escape as soon as the Grub prompt appears.

If its grub2 we're talking about, I think now its the shift key.

---

### Post by norbs on 2009-10-13
> **keithpeter said:**
> 
Anyone any ideas on why this cropped up? 

Hi, it just happened to me today.

At one time as my system was starting up, the screen went black and than back. A window appeared but it was frozen, not showing any text or buttons, just a blank sheet. I think it wanted to be an error reporting window, but than my whole system gut stuck. As I forced restart pushing the restart button this error came up. 

For me it`s not associated with any updates, I think.

---

### Post by ranch hand on 2009-10-13
> **Madhatter14641 said:**
> A while back my grub install started throwing up an invalid environment block error. It took me a while to find the fix, so I figured that someone else might want it.

To boot into linux in the first place, push e in the grub menu, delete the save_env recordfail line, and press ctrl+x to boot.

Next, run these commands:

cd /boot/grub
rm grubenv
grub-editenv grubenv create
grub-editenv grubenv set default=0
grub-editenv grubenv list
default=0

This should give you a bootable system. Found the solution here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784). Hope this helps someone!
I linked to this post on the Grub2 Introduction.

I had this problem a while back and my fix was not anywhere near as elegant as this.  Good job and thanks.

---

### Post by Islington on 2009-10-20
Thanks for posting this. I had to forcefully shutdown the laptop today (power button), and this popped up. 

Could you or someone else explain how this fix works?

---

