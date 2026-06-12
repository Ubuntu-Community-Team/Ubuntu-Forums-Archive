---
title: "Ubuntu installed but graphics are garbled"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by StepOne on 2012-06-01
[FONT=Times New Roman]Hi,

I am trying to install Ubuntu onto a Dell Precision T7500 (windows 7 Pro 64bit) with a NVidia Quadro NVS-295 graphics card.

I started with the latest Ubuntu Desktop 12.04 LTS. It installed and I rebooted. It gave me the two boot options. If I choose Ubuntu, a few lines of text flashed briefly on the screen, then a blank screen and nothing more.

I then tried Ubuntu 10.04 LTS 32-bit as this version is officially 'Ready' for my T7500. This time when I choose Ubuntu at boot, Ubuntu starts but the screen is totally garbled. I can move the cursor blob and if I press a few keyboard keys I can see that I must be entering text into a login screen, but it's useless.

Can anyone help a total newbie to install Ubuntu?

Many thanks,[/FONT]

---

### Post by 2F4U on 2012-06-01
You should try to boot with the nomodeset grub kernel parameter and see if that resolves the screen problem:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by StepOne on 2012-06-03
Hi,
 
Thanks for your reply.  Yes, from what I read your suggestion seems a good one.  But, how do I get to Grub in order to edit?  I've tried tapping the Shift key when booting Ubuntu, but it made no difference.  After clicking on the Ubuntu option as the PC starts, I don't get any further options.  
 
Also,  should I go back to the latest version of Ubuntu or stck with the older version 10?  As you can tell, I'm new to this type of thing.
 
Many thanks for any help you may be able to provide.

---

### Post by oldfred on 2012-06-03
It is not tap, but hold shift from BIOS screen until grub menu appears.

---

### Post by StepOne on 2012-06-06
Hi and thanks for taking the time to reply.
 
What you suggest worked just fine with my laptop, but this Dell T7500 refuses to play ball.  It's got a Dell SAS Host Bus Adaptor with it's own BIOS.  If I hold down the Shift key after the BIOS screen, the Windows Boot Manager comes up with the two options, Windows 7 and Ubuntu. If I select Ubuntu, I get a quick flash of 3 lines of text, each line starting with the word 'Try' at the top screen.   Then the screen goes blank and I get nothing more.
 
Any ideas?
 
Ubuntu 12.04 LTS 32bit

---

### Post by oldfred on 2012-06-06
Well that is wubi as it boots with Windows and then presents the grub menu (like a normal partition boot).

Do not know if holding shift from entry in Windows works or not.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

