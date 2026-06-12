---
title: "Ubuntu 11.10 Password Change Error"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by Jessface on 2011-11-08
Hi guys, I'm Jess.  I'm new to these forums, and VERY new to Linux & Ubuntu.  You can literally say that I know nothing about it.

After my mother installed the new OS, Ubuntu 11.10, I wanted to try using the Software Center to get some video editing software.  It prompts me for an administrator password, but the one my mom has is not working.  Also, it use to be required to log into the computer, and now there is no password set.

After researching, I found that I was suppose to go into the command prompt to change it, but when I try to, I get this:

"passwd: Authentication token manipulation error&#8221;: passwd: password unchanged".

So while browsing the Internet, I came across some other Ubuntu-related forums that seem to have solved this issue, but I don't quite understand what to do.

I read the solutions from [here]("http://www.linuxquestions.org/questions/linux-newbie-8/passwd-authentication-token-manipulation-error-236955/") and [here]("http://www.linuxquestions.org/questions/linux-security-4/authentication-token-manipulation-error-2813/"), but I don't understand the step-by-step process.

When I reboot my computer, as it is loading up, I hold the shift key, and select the latest Ubuntu OS in recover mode.  Once there, I select root to get to the command.  After I type in my old password to get access to make any changes, even when I try to change the password, I still get that error message.  Can anyone explain a step-by-step on how to fix this issue and allow me to get change the password so I can finally start using new software?
> _ <

Thank you,
Jess

---

### Post by Jessface on 2011-11-09
This hasn't been resolved.  Am I in the wrong forum for this?

---

### Post by BillyBoa on 2011-11-11
As I understand you lost your password.

If you type ```
sudo passwd -put here the logon name-
``` in the terminal you could change it but I'm afraid that you need the old one to do it.

Look here 

[http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/](http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/) 

and here
 
[http://www.thegeekstuff.com/2009/12/how-to-change-password-on-ubuntu/](http://www.thegeekstuff.com/2009/12/how-to-change-password-on-ubuntu/)

---

### Post by Mel Shepherd on 2011-11-16
I read that Ubuntu Studio 11.10 shouldn't have been put out and I'm beginning to understand why.  Problem: When I ungraded from Ubuntu 11.04, to Ubuntu 11.10 - my password is no longer accepted for some reason. I have the choices in bootup in grub of Gnome Classic, Gnome Classic with no effects, Recovery Console, Ubuntu, User Defined Session, and Xfce Session. I'm to stay with Ubuntu right? What do I have to do to get my password to work? 

I'm able to open Xfce Session with my password, but was Gnome changed to Xfce interface? What should I do? It says also the Host SMBus Controller is not enabled.  I don't know why, so can you help?

---

### Post by Cyclane on 2011-11-16
You should be able to change your password in the recovery console.

When booting choose for recovery
After this has loaded choose for something like 'root terminal'
after this type in 'passwd USERNAME'
This will prompt you for a new password and after you're done you can reboot by typing in reboot and hitting enter. After this boot like you normally do and this time log in with your new password.

---

### Post by pixelnate on 2012-01-26
I hate to bring up a dead thread, but the solution presented here just doesn't work. I realize that $ passwd username should work, but it simply doesn't. I am getting the Authentication token blah, blah error, too. I understand that it SHOULD work even though it doesn't.

Has anybody ever solved this a different way?

---

### Post by psteven80 on 2012-01-27
I'm having a similar problem. There appears to be a solution in the Forums at [http://ubuntuforums.org/showthread.php?t=1863430](http://ubuntuforums.org/showthread.php?t=1863430). I haven't tried it yet however.

---

