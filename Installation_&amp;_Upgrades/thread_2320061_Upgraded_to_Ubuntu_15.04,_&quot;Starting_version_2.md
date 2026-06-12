---
title: "Upgraded to Ubuntu 15.04, &quot;Starting version 219&quot; problem with NO tty1-tty6 access."
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by murmures.kgs on 2016-04-10
Hello all,


I first installed Ubuntu 14.04 on an external hard drive.
Everything went fine and I could boot, but there was no way I could connect my computer to the internet (eth0 and wlan0 not recognized and no success in finding appropriate drivers).

I read a newer version of Ubuntu could solve that problem, so I installed Ubuntu 15.04 on my external hard drive.
Now, no successful boot anymore, I get the famous black screen with the "starting version 219" message.

I tried to switch to a console to see what's going on (as it is done everywhere in the Internet).
The shift works, I can enter my login and password to tty, they are accepted and about 5 lines are written to the screen before everything disappears and I'm back at tty asking me for login and password again and again.
The lines disappear so fast I cannot read them.
I tried wrong logins and passwords to verify that what I entered was correct (indeed, otherwise tty tells me immediately login or password is wrong).
I tried all of tty1-tty6, the same things happen.
I went to the boot options to boot with upstart, it ends with a kernel panic telling that it tried to kill init.
I tried to boot in safe mode, I reach tty asking me for login and password (during boot messages before, I saw a lot of 'FAILED' among the 'OK' initializations), but the same things happen again: login and password are accepted, then everything disappears and I'm back to tty asking me for login and password again and again.

What could go wrong?
What can I try?
Is there another version of Ubuntu that might help me to solve this problem?
All I need is a working Linux (version doesn't matter, although I only worked with Ubuntu) with a terminal and Internet access.
Please note that I am really not an Linux expert. :)

Thanks a lot in advance

---

### Post by grahammechanical on 2016-04-10
Ubuntu 15.04 reached end of life 4th February 2016. So, there is no point trying to progress further with 15.04 because it will not get any security updates.

You say that the install of 14.04 worked but did not have drivers for ethernet & WiFi. It sometimes happens that we need to install drivers for WiFi but ethernet is standard technology. It is usual that ethernet is not working.

Your options are (a) try again with 14:04. (b) try with Ubuntu 15.10. It is supported up to the end of July 2016. (3) wait a couple of weeks and try with Ubuntu 16.04 when it is released 21st April 2016.

If you get an ethernet connection to the router with either 14.04 or 15.10 you can do an online upgrade to 16.04 when it is released.

Regards

---

