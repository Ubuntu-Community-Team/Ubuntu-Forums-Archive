---
title: "[SOLVED] Unfinished Upgrade"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by DivineJustice on 2008-05-18
I was updating to version 8.04 and went to sleep, my cousin was still downstairs, and turned off the computer while 20 minutes were still left during the installation process.  Now when I turn on the computer, it does not start up and all that is there is a black screen.

I am not very Ubuntu savvy, so can anyone offer any help?

If I do have to reinstall it, please tell me how (as I said I am not very Ubuntu savvy)

Solution
> **overdrank said:**
> Hi and you can try and use the recovery mode which is the second choice from the grub usually. Login and then try and update
```
sudo apt-get update && sudo apt-get upgrade
```

If you get this error
E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem

Try this
> **overdrank said:**
> Ok then the upgrade was not complete and has issues with the two graphics
then use the command ```
sudo dpkg -- configure -a
``` then the update commands earlier.

---

### Post by overdrank on 2008-05-18
> **DivineJustice said:**
> I was updating to version 8.04 and went to sleep, my cousin was still downstairs, and turned off the computer while 20 minutes were still left during the installation process.  Now when I turn on the computer, it does not start up and all that is there is a black screen.

I am not very Ubuntu savvy, so can anyone offer any help?

If I do have to reinstall it, please tell me how (as I said I am not very Ubuntu savvy)

Hi and you can try and use the recovery mode which is the second choice from the grub usually. Login and then try and update
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by DivineJustice on 2008-05-18
> **overdrank said:**
> Hi and you can try and use the recovery mode which is the second choice from the grub usually. Login and then try and update
```
sudo apt-get update && sudo apt-get upgrade
```

Can't login.  I started the computer 1/2 an hour ago and it still hasn't come to the login screen.
Also, when I tried to use the 'sudo apt-get clean' before the update it required me to enter in my sudo password, but the keyboard wouldn't let me enter anything afterwards, so using sudo is probably out of the question

---

### Post by overdrank on 2008-05-18
> **DivineJustice said:**
> Can't login.  I started the computer 1/2 an hour ago and it still hasn't come to the login screen.
Also, when I tried to use the 'sudo apt-get clean' before the update it required me to enter in my sudo password, but the keyboard wouldn't let me enter anything afterwards, so using sudo is probably out of the question

Hi and the password will not show for security. You are typing it is no showing. That is why I suggested recovery mode from the grub.

---

### Post by DivineJustice on 2008-05-18
> **overdrank said:**
> Hi and the password will not show for security. You are typing it is no showing. That is why I suggested recovery mode from the grub.

That was before the update and the interruption, but it makes sense.  Thing is, the computer won't start period, so should I wipe the hard drive and reinstall? And if so how would I wipe the HD.

edit-
thanks for your quick responses overdrank

---

### Post by PmDematagoda on 2008-05-18
Could you please specify what you mean by "the computer won't start".

---

### Post by Mhurst1 on 2008-05-18
Why would you turn off your computer in the middle of an upgrade?

---

### Post by overdrank on 2008-05-18
Hi and Mhurst1 the op stated in the first post. As to PmDematagoda asked do you see the grub when you boot the system? If ubuntu is the only OS on the system then you should see the grub loading then press esc key to view the grub and enter recovery mode.
Edit as to installing again, you should try and repair as it is a learning process IMO. If you have no data that you are needing then that is always a option.

---

### Post by DivineJustice on 2008-05-18
> **PmDematagoda said:**
> Could you please specify what you mean by "the computer won't start".
I push the on button, wait 1/2 an hour and the monitor does not turn on.


> **Mhurst1 said:**
> Why would you turn off your computer in the middle of an upgrade?
My cousin turned off after I went to sleep.


> **overdrank said:**
> Hi and Mhurst1 the op stated in the first post. As to PmDematagoda asked do you see the grub when you boot the system? If ubuntu is the only OS on the system then you should see the grub loading then press esc key to view the grub and enter recovery mode.
Edit as to installing again, you should try and repair as it is a learning process IMO. If you have no data that you are needing then that is always a option.
I probably should have said this earlier but here goes...
The computer either used to or still has Windows XP installed on it.  The graphics card went on the fritz, and my dad decided to install Ubuntu on it instead of fix it.  Even though Ubuntu worked well graphics wise, when I booted the computer, nothing was visible until the login screen (black screen).  It usually took about 3 minutes for it to reach the login screen and then everything worked well.  Now its not even reaching the login screen and I cannot see anything before then, so I'm pretty screwed. (Never seen this grub thing before)

---

### Post by PmDematagoda on 2008-05-18
Do you see the POST messages/splash screen when starting up the PC? In my case I see an Intel splash screen when the PC is turned on.

---

### Post by DivineJustice on 2008-05-18
Ok so there are two graphics cards on the computer, the good one and the bad one

I plugged the monitor into the other one, and now I can see things.  I did the recovery mode
Ubuntu 7.10, kernel 2,6,22 14-generic (recovery mode)

when I try the sudo apt-get commands it gives me errors such as
E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem

---

### Post by overdrank on 2008-05-18
> **DivineJustice said:**
> Ok so there are two graphics cards on the computer, the good one and the bad one

I plugged the monitor into the other one, and now I can see things.  I did the recovery mode
Ubuntu 7.10, kernel 2,6,22 14-generic (recovery mode)

when I try the sudo apt-get commands it gives me errors such as
E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem

Ok then the upgrade was not complete and has issues with the two graphics
then use the command ```
sudo dpkg -- configure -a
``` then the update commands earlier.

---

### Post by DivineJustice on 2008-05-18
> **overdrank said:**
> Ok then the upgrade was not complete and has issues with the two graphics
then use the command ```
sudo dpkg -- configure -a
``` then the update commands earlier.

ok I ran sudo dpkg --configure -a
and it Aborted from too many errors

---

### Post by overdrank on 2008-05-18
> **DivineJustice said:**
> ok I ran sudo dpkg --configure -a
and it Aborted from too many errors

Ok you can try ```
sudo apt-get install -f
``` and if it fails with errors also you maybe left with the only option of reinstalling. You can do this easily with the live cd and install on top of the existing partition. Or as you quoted earlier 
```
and my dad decided to install Ubuntu on 
``` maybe let him take the issue.

---

### Post by DivineJustice on 2008-05-18
Well the sudo apt-get install -f command had the same error as the other sudo apt-get commands...

So I guess this means I have to reinstall


but the whole idea was not to let my dad know, otherwise he'd probably get pissed

---

### Post by overdrank on 2008-05-18
> **DivineJustice said:**
> Well the sudo apt-get install -f command had the same error as the other sudo apt-get commands...

So I guess this means I have to reinstall


but the whole idea was not to let my dad know, otherwise he'd probably get pissed

I do understand ( being a father ) but honesty will get you far. :)

---

### Post by DivineJustice on 2008-05-18
ok thank you

Ill mark this as solved and put the advice you gave in the original post.

---

