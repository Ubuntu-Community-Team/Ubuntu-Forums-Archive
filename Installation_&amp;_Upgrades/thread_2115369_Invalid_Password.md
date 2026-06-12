---
title: "Invalid Password"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by AlanSablo on 2013-02-12
Hello,

Im installing Ubuntu 12.10 from a pen drive using the 'help me boot from CD' option as Its the only way I can get the laptop to boot from USB.

The computer boots -  shows the UBUNTU loading screen then reaches a login screen and asks me for a password which I havn't set/don't remember during 3 or 4 previous install attempts. 

Ive tried going to command prompt using ctrl+alt+f1 and altering the password using a sudo passwrd user command but when I type commands into command prmt the dont seem to register.

Does anyone have any help please

---

### Post by slickymaster on 2013-02-12
Take a look at [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword") and follow it's instructions and you'll have your password problem solved in a few minutes.

---

### Post by bantuvez on 2013-02-12
When you switch to virtual console (ctrl+alt+f1) you still have to login with a password. (Or how do you login to your virtual console??? ) That's the same password what you should use at the graphical login screen.

---

### Post by AlanSablo on 2013-02-12
slickymaster - I'm having some trouble getting into grub I have tried pressings Esc and Shift (Not at the same time) 

bantuvez - cheers man, I did not realize that

---

### Post by bantuvez on 2013-02-12
Yo have to restart, and hold down the SHIFT  button until GRUB comes up. You did this?

---

### Post by slickymaster on 2013-02-12
bantuvez is right. Power up your computer pressing and holding Shift during loading Grub until it comes up.

---

### Post by AlanSablo on 2013-02-12
Yes I did this and was given the following options

 - Normal mode
 - Safe graphic mode
 - ACPI workarounds
 - Verbose mode
 - Demo mode ( Which takes me the same login screen )

---

### Post by deadflowr on 2013-02-12
No version of Ubuntu let's you install it without entering a password and re-entering the same exact password.

---

### Post by bantuvez on 2013-02-12
Have you installed Ubuntu with Wubi? (You installed Ubuntu from a running Windows? )

---

### Post by AlanSablo on 2013-02-12
Well thanks to the fantastic preloaded BIOS rubbish on Sony Viao plus the marvellous windows 8 installing Linux on this computer has been a battle going on a couple of weeks so I must have set a password but im normally quiet good at remembering passwords as I only use 6 and I have tried all of the above.

---

### Post by AlanSablo on 2013-02-12
I used wubi  and the 'help me boot from CD' which doesnt ask for a username or password I tried using the basic install but my computer seemed to ignore it once restarted.

---

### Post by slickymaster on 2013-02-12
> **AlanSablo said:**
> Well thanks to the fantastic preloaded BIOS rubbish on Sony Viao plus the marvellous windows 8 installing Linux on this computer has been a battle going on a couple of weeks so I must have set a password but im normally quiet good at remembering passwords as I only use 6 and I have tried all of the above.

So, can we assume you've installed ubuntu along side with windows 8, with a USB stick or CD or have you use Wubi to install it?

---

### Post by AlanSablo on 2013-02-12
I originally installed Linux along side Windows 8 the idea being that I then delete Windows 8 but that did'nt work and Windows 8 seemed to dominate it. So I formatted the C:\ and tried to boot from USB but that did'nt work.

I then installed a friends copy of Windows 7 (Which Sony aren't providing drivers for for for this specific laptop inc network card and graphics.... Nice one Sony)

Once Windows 7 was on I was able to boot Linux from USB but only using the 'help me boot cd function'

---

### Post by slickymaster on 2013-02-12
I'm getting confused, now. You say you formatted your hard drive, so if you have done that, there's no ubuntu letf instaled in your drive. So now I'm guessing you are just using the **Try Ubuntu** option, and that doesn't have a password request.

Or am I completely misreading your posts?

---

### Post by AlanSablo on 2013-02-12
Yes sorry -  I did format the hard drive on and put Windows 7 on the machine then after a couple of attempts got Ubuntu to take but I have un-installed it since then so where are these passwords being saved ARG

---

### Post by AlanSablo on 2013-02-12
And yes try Ubuntu

---

### Post by slickymaster on 2013-02-12
As far as I'm managing to understand, you are using the Try Ubuntu option, from a LiveCD in a USB stick.
Sometimes a LiveCD might ask you for a user-name or password. Just leave these blank and press enter (or allow it to time-out).

But you must know that using this feature does't means that you have Ubuntu installed on your computer. You even can install programs to a LiveCD session in the normal way, although these will be forgotten as soon as you switch the machine off.

But in order to have your user/password account you'll have to install it. Either dual-booting with your existing Windows 7 instalation, or installing it inside Windows, using Wubi for that.

By the way, passwords can be found (in hashed form) in ```
/etc/shadow
``` and the users in ```
/etc/passwd
```

---

### Post by AlanSablo on 2013-02-12
Cheers for the help. 

I might just give this one away and buy and abacus *sigh* ha

Well on the back of that I am formatting the system and putting the smallest install of windows on and then I'll run a duel boot. Why can't you just buy computers with Linux on .. I'd pay extra to not have to delete Windows(+ other assorted rubbish).

---

