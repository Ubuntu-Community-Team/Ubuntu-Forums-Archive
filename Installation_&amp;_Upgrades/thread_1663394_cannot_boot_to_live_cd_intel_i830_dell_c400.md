---
title: "cannot boot to live cd intel i830 dell c400"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by pickgrand on 2011-01-09
I have 5 dell Latitude C400's that I have been trying to install ubuntu 10.10 or Linux mint 10. I cannot seem to get anywhere.
Linux mint 10 and ubuntu 10.10 live cd boots a black screen and locks up.

nomodeset and i915.modeset=0 take me to a $ prompt.
I have also tried xforcevesa to no avil.

when I try startx from $ prompt i get 
(EE) VESA (0): no valid modes
(EE) Screen(s) found, bout none have a usable configuration
Fatal server error:
no screens found

I have seen forums that state editing xorg.conf. But I cannot boot to the os to get it installed so I can edit the file.

If anyone can please help or do I just need to stick with version 8.
Thanks in advance

---

### Post by davidmohammed on 2011-01-09
Suggest stick with lucid and install the fix described [here]("http://ubuntuforums.org/showpost.php?p=10329016&postcount=56").

Then perform an upgrade to maverick.

---

### Post by spcwingo on 2011-01-09
Have you tried:

```
i915.modeset=1
```

I had a couple of Dell laptops that refused to display anything on-screen without it.

---

### Post by wojox on 2011-01-09
When you get to the purple screen press enter, select language and at the options screen press F6 scroll to "nomodeset" press Esc and try without installing.

---

### Post by Catharsis on 2011-01-10
This is all with Maverick? That's very interesting. The i8xx problems were fixed for that release.

Maverick should have switched to using the fbdev driver instead of the intel driver, so you should make sure it's loading and whether or not it's erroring. Just boot without "quiet splash" in the kernel command line and watch for errors.

If you can, switch to a tty with Ctrl+Alt+F2 and check Xorg.0.log ("cat /var/log/Xorg.0.log") and dmesg ("dmesg"). Xorg.0.log should have lines beginning with "(0)FBDEV:" or something like that if the fbdev driver loaded correctly; also watch for any errors. There might also be a kernel bug or panic, so watch dmesg for one of those.

You can also try replacing "quiet splash" with "noacpi" and "gfxpayload=text".

P.S. you can edit your xorg.conf by using Nano, i.e. "sudo nano /etc/X11/xorg.conf".

---

### Post by pickgrand on 2011-01-16
Ok so I cannot access ctrl-alt-f2. Screen is totally black. 
no response the only thing I can do it power off.
i915.modeset=1 also gives a black screen. 

noacpi only will give me a $ prompt.

---

### Post by spcwingo on 2011-01-16
After booting to a prompt could you please run:

```
lspci | grep VGA
```

and post the output in your next post.

---

### Post by pickgrand on 2011-01-16
Ok so I booted to a prompt with removing quiet and splash and added i915.modeset=0 right before the prompt the screen blinked a couple times:

Here is the output of the lspci | grep VGA

00:02.0 [COLOR="Red"]VGA[/COLOR] compatible controller: Intel 82830 CGC [Chipset Graphics Controller] (rev 04)

Thanks for all the help

---

### Post by Catharsis on 2011-01-16
> **pickgrand said:**
> Ok so I cannot access ctrl-alt-f2. Screen is totally black. 
no response the only thing I can do it power off.
i915.modeset=1 also gives a black screen. 

noacpi only will give me a $ prompt.

...So, did you try the other stuff I suggested? Like booting without "quiet splash" and adding "gfxpayload=text"?

You can also check the logs from your previous boot using kern.log and Xorg.0.log.old. Boot the broken default configuration and then boot to a command prompt (just replacing "quiet splash" with "text" is enough to do this) and check those log files (you'll have to find the second to last boot in kern.log; Xorg.0.log.old will be only the previous boot.)

---

### Post by pickgrand on 2011-01-17
Catharsis,
I must be doing something wrong. 
cat: /var/log/Xorg.0.log: No such file or directory

also gfxpayload=text locks ups. just text takes me to $ prompt.

---

### Post by Catharsis on 2011-01-17
> **pickgrand said:**
> Catharsis,
I must be doing something wrong. 
cat: /var/log/Xorg.0.log: No such file or directory

There's no colon; it's just "cat /var/log/Xorg.0.log.old".

---

### Post by pickgrand on 2011-01-17
Catharsis, yes I know sorry should have mentioned that was the error that came back after i typed it correct. I check and tried a couple times

---

### Post by Catharsis on 2011-01-17
That's very strange. Maybe X just never loads and that's why it black-screens and doesn't produce an Xorg log. You should check kern.log; my guess is there's an Oops in there somewhere if you check the part of the log that corresponds with the broken boots.

---

### Post by pickgrand on 2011-01-17
Ok so I can get to that file there a lots of paged the scroll through. I don't see anything at the end that raises any flags. 
Is there anything that I need to search for in the file and how to do I search the file.
Thanks,
Matt

---

### Post by Catharsis on 2011-01-17
Sorry, I forgot that all this is on a LiveCD and not an installation. Your only hope of seeing the logs is to remove "quiet splash" and try to spot something strange as dmesg prints to the screen during boot, or to SSH into the machine from a second one once it freezes.

---

### Post by pickgrand on 2011-01-21
Thanks everyone for Trying I will just stay with 9 and maybe the next it will be fixed. I have already put way more time than I had hoped. It's very disappointing that an this OS cannot get a simple video card to work.

---

