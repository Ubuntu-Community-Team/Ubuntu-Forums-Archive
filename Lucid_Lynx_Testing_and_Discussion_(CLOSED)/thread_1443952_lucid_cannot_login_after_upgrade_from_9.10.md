---
title: "lucid cannot login after upgrade from 9.10"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by azurehi on 2010-03-31
After upgrading from 9.10 and reaching the linux 2.6.32-18 kernel, I can no longer reach the desktop. The login screen appears with my username and mouse cursor can be moved. Upon hitting Enter, the screen for password appears but mouse cursor is frozen and nothing can be typed in to password box. Within a few seconds there is reboot, with the same process repeated. There is no way to get to the desktop. This is true for each of the previous kernels.

Using recovery mode root shell, allows entry of username and password but at (username)@(username):~$  I do not know what to enter.

Update:  I again upgraded from 9.10, this time without making any changes (hardware driver not enabled), reached desktop but mouse pointer was a square sometimes, hardly visible other times.  Upon reboot I reached the login screen:  mouse pointer was visible and could be moved; I selected username and the same problem was present - pointer frozen and I could not type in my password; after several seconds, the computer rebooted and returned to same login screen problem.

I dual boot with 9.10 and have no problem.

---

### Post by garvinrick4 on 2010-03-31
startx  and enter then password? (If you can)

Code: aptitude show gdm

Is gdm installed?


Code: aptitude show plymouth

I cannot boot with plymouth installed as of yet.
New mountall do out shortly.

Will have to use Live cd to remove plymouth.

Do you have another install of Ubuntu or did you upgrade to beta on your only one?

---

### Post by azurehi on 2010-03-31
> **garvinrick4 said:**
> startx  and enter then password? (If you can)

Code: aptitude show gdm

Is gdm installed?


Code: aptitude show plymouth

I cannot boot with plymouth installed as of yet.
New mountall do out shortly.

Will have to use Live cd to remove plymouth.

Do you have another install of Ubuntu or did you upgrade to beta on your only one?
aptitude show gdm:  I cannot tell if gdm is installed...screen passes by too quickly

aptitude show plymouth:  plymouth is installed

I Do have karmic 9.10 installed, also

---

### Post by garvinrick4 on 2010-03-31
Try to remove plymouth to see if it boots then.

my install will not boot right now with plymouth and
a lot of other peoples.

It is in the process of a fix as we speak.

---

### Post by azurehi on 2010-03-31
how do I remove plymouth?  you mention live cd - do you mean that I should reinstall?  any specific help would be appreciated.  thanks

---

### Post by azurehi on 2010-03-31
I was able to get to the desktop by following the suggestion posted in Bug report:
[https://bugs.launchpad.net/ubuntu/lucid/+source/gdm/+bug/516520]("https://bugs.launchpad.net/ubuntu/lucid/+source/gdm/+bug/516520")

Tom Louwrier wrote on 2010-03-25:	 #15
OK, tried the following:
- boot into rescue mode
- choose 'resume normal boot'
- this gives me a pure text mode login, no virtual tty
- login with user/passw as normal
- change my password with 'passwd' (success)
- reboot with sudo reboot
- booted the normal way
- got exactly the same situation as earlier this morning: login window resets within a second and I don't get to fill in my password

So I rebooted again and used my workaround (rescue mode, resume normal boot, login in text mode) to get in.
After that I reset my password to what it was and started X (startx).
After that I got into my normal desktop and everything works OK.

Note: switching to a tty session will *not* work, since KMS ant ATI do not play together very well (bug 509273).

cheers
Tom

---

### Post by azurehi on 2010-03-31
after updating, once again the login screen continues to loop after selecting username (only one on system) either by Enter or mouse.

I am going to wait for Beta 2 and not waste anymore time.

---

