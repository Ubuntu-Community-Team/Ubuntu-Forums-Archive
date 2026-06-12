---
title: "[SOLVED] how to get pass the bios password."
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by cmay on 2008-11-26
hi.
i have with me an old computer i been asked to install ubuntu in but there is no way of doing anything before i get pass a bios password. which they have forgot. also there is something strange about the keyboard not responding to input at all and it cant just boot from cd. it is correct to assume the only way is to remove the bios and put it back in after a good five minuttes right. i do not want to destroy anything . 
thanks.

---

### Post by taurus on 2008-11-26
If you want to reset the BIOS, remove the battery and leave it out for 5 minutes.  Put it back in and boot your old machine up and see if it's still asking for a password to get into the BIOS.

---

### Post by Kevbert on 2008-11-26
Disconnect the PC from the power and there should be a link to the bios battery (probably a CR2032 button cell) on the motherboard, which you can remove and then reconnect after 5 minutes. Hopefully that should do it.

---

### Post by cmay on 2008-11-26
i can not spoil or destroy anything by doing this can i?. i done it once before on my old computer  and it went well but i also seen my brother having to buy new motherboard from playing too much with bios updates .

---

### Post by icanfly0307 on 2008-11-26
Hey,
         Like everyone said above, remove the BIOS battery and leave it out. However, don't put it back in for ATLEAST 30 MINUTES. I've left it out once for 10 minutes and it didn't work. The info in the BIOS needs to clear and it can take up to 45 minutes. And no, if you take the battery out, it will not ruin your BIOS. Just be sure to mind the + and - when you're putting it back in.

Good Luck!:)

---

### Post by cmay on 2008-11-26
<off topic> i just reached giving hundred thanks </on topic>

thanks for the help everyone. its been almost 2 years since i did this before so i could not remember if it was the right way to do it.

---

### Post by icanfly0307 on 2008-11-26
Did it work? :)

---

### Post by cmay on 2008-11-26
i am about to find out soon. its a computer i have promised to fix that is really vira infected so i hope its not a virus bios also that got it. anyway i will post an update and maybe even a screenie when i fixed it. should be done running ubuntu 8.10 by tonight i hope. 
it has a 2 ghz amd and 512 ram so it will do just fine i think.

---

### Post by icanfly0307 on 2008-11-26
yeah, i'm actually running ubuntu 8.04 on a 1ghz 256mb ram computer and it works like lightening.

---

### Post by Kevbert on 2008-11-26
> **cmay said:**
> i am about to find out soon. its a computer i have promised to fix that is really vira infected so i hope its not a virus bios also that got it. anyway i will post an update and maybe even a screenie when i fixed it. should be done running ubuntu 8.10 by tonight i hope. 
it has a 2 ghz amd and 512 ram so it will do just fine i think.

There may be an option to stop anything writing to the bios or boot sector in the bios settings. Make sure that's turned on.

---

### Post by icanfly0307 on 2008-11-26
@Kevbert: I doubt if he will be able to access the BIOS if he's lost his password. Accessing the BIOS requires a password and he doesn't have it unfortunately. I hope that the battery fix will work.

---

### Post by cmay on 2008-11-26
:) i am typing this from the livecd
thanks everyone.

---

### Post by icanfly0307 on 2008-11-26
Great to know that you got it to work! :-)

---

### Post by cmay on 2008-11-26
thanks. i am actually installing from the livecd right now. its really great to able to do that. in less than five minutes from now i repaired an 2 year old computer that otherwise just would been trashed. i am getting nothing for it but i like to help others and let them learn about linux as well .

 thanks for your time.

---

### Post by icanfly0307 on 2008-11-26
Just so that others can benefit, could you please mark this as solved?

---

### Post by cmay on 2008-11-26
done. 
after fetching the updates its a perfectly good computer that just works. it would have been a real shame to trash it.
thanks everybody.

now i going to call them and let them know they have got a whole new computer :)

---

### Post by ekh on 2008-11-26
Just a warning regarding the IBM Thinkpad series. I lost my bios password, and removed the small internal battery to "reset" the bios.

But instead I got a message that the computer has been tampered and was now locked.

Now my T41 was worthless without the bios password.

But I found help here:

[www.allservice.ro](www.allservice.ro)

I downloaded some programs and built the simple I2C programmer/reader.

I managed to read the contents of the eeprom and decrypt the bios password to get the t41 going again.

Much trouble for a lost bios password, be sure to keep your bios password.

---

