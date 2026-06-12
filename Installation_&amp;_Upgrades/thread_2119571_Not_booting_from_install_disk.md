---
title: "Not booting from install disk"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Nor9864 on 2013-02-24
Well, I made an install disk of Ubuntu 12.10,  following the boot from CD guide ([https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)) did it correctly and stuff, but my PC will not boot from it. I know how to make it boot from it and it works perfectly with my windows 7 install disk. Why isn't it booting and how can I fix it?

---

### Post by jnesset on 2013-02-24
Hi! 

I also had this problem earlier. Have you changed the boot order to boot from CD? Also check if you have "Fast BIOS mode" enabled. If you have so, disable it.

Good luck!:)

---

### Post by Nor9864 on 2013-02-24
Yes I have set the boot order from beforehand. But I am unsure whenever or not the Fast BIOS mode is enabled, beacuse I could not find the option. What is it disguising as?

---

### Post by jnesset on 2013-02-24
> **Nor9864 said:**
> Yes I have set the boot order from beforehand. But I am unsure whenever or not the Fast BIOS mode is enabled, beacuse I could not find the option. What is it disguising as?

On my computer (Samsung NP530U3B) I enter the BIOS by holding down F2 on startup. Fast BIOS Mode for me is found in the Advanced section in BIOS. What computer do you have?

---

### Post by Nor9864 on 2013-02-24
I have a Dell Alienware x51 desktop computer. There's no fast BIOS mode option it seems.

---

### Post by jnesset on 2013-02-24
Allright. I don't know. You might want to take a look at this post: [http://en.community.dell.com/owners-club/alienware/f/3746/p/19455075/20133078.aspx]("http://en.community.dell.com/owners-club/alienware/f/3746/p/19455075/20133078.aspx")

Have you tried booting from USB?

Good luck!

---

### Post by Nor9864 on 2013-02-24
The post says that I should set the boot mode to legacy, instead of UEFI, but the option is greyed out and unavailible?

And yes, I have tried booting from USB with the same result as with the CD.

---

### Post by Nor9864 on 2013-02-24
Also updating BIOS in case it makes any difference.

---

### Post by jnesset on 2013-02-24
Then I don't know, I'm sorry!

---

### Post by jnesset on 2013-02-24
> **Nor9864 said:**
> Also updating BIOS in case it makes any difference.

Yes, maybe. Though I would be careful doing that if you don't know what you're doing/haven't done it before.

---

### Post by Nor9864 on 2013-02-24
Updating the BIOS made all the difference! 
Currently installing Ubuntu!

Thanks for your help mate!

---

### Post by jnesset on 2013-02-24
> **Nor9864 said:**
> Updating the BIOS made all the difference! 
Currently installing Ubuntu!

Thanks for your help mate!

Congrats! No problem, I don't know a lot myself, but glad I could help :)

Let's mark this as solved, huh?

---

### Post by sirriffsalot on 2013-02-24
If anyone has problems like this in the future, a thing that helped me get temporary access to the install so I could sort things out from within the OS itself was to hold down SHIFT after the BIOS-bootup screen with the F12 for boot device and Delete-button for BIOS options and so on. 

It is the default way for grub to load, and with a bit of luck you'll see "Grub loading" and following a prompt to choose between recovery mode and the normal install, and any other things you might have there, windows dual boot etc. Good luck!

---

### Post by jnesset on 2013-02-24
Nor9864, 
mark this as solved by going to Thread Tools and hit Mark as solved.

---

