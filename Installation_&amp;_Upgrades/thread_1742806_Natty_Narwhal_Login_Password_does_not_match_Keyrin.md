---
title: "Natty Narwhal Login Password does not match Keyring"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by BorisPlankton on 2011-04-29
Hello just upgraded to NN and when I try to log on to Ubuntu One I am told Login Password does not match Keyring password. Cannot remember my Keyring password so cannot get past this.
If I go to Passwords and Encryption keys [I] only have my login password listed?

---

### Post by fcastillo on 2011-05-05
I have the same problem, the only way to get pass it is to put the same as your login password (your system -sudo- password) then just put garbages, and then the login password and it usually works.
If it doesn't just try again the same way, usually by the first try it works, but it can take up to 3 or 4 tries before you it can accept the password

---

### Post by ZootHornRollo on 2011-05-05
i have a similar issue.

once i have logged on, if for any reason i need to enter my 'default' keyring password it does not match the password i entered - the same as my login.

i have tried deleting the 'default' keyring entry in passwords and encryptions then setting up wireless etc again but once i re-start and am required to enter the password again, it is no longer recognised. 

any ideas?

---

### Post by wilee-nilee on 2011-05-05
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Isn't linux cool.;)

---

### Post by BorisPlankton on 2011-05-06
Ok tried fcastillo approach no joy although might be misinterpreting the instructions. Next up is the wilee-nilee approach.

---

### Post by BorisPlankton on 2011-05-08
Right having looked at wilee-nilee this helps me to rest my login password but the problem is that my Keyring password does not match my login p/word and I do not know what my keyring password is? Before I installed Natty I could use Ubuntu One.The message displayed when I enter my Ubuntu One password is 'Password used to log in to the computer no longer matches that of your local keyring'

I have now revisited Password & Enryption keys and deleted the one passowrd key that appeared. I had thought this was the login password but now think this must have been the key ring password. After deleting I was able to get onto Ubuntu One and now under the password tab I have one password: login key and it is for Ubuntu One.
I am not sure this is going to help ZootHornRollo unfortunately.

So I think I am ok now. Thanks to all.

---

### Post by cespinal on 2011-05-12
> **wilee-nilee said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Isn't linux cool.;)

no it is not in this case... I should not go through all that to solve this problem. 

So far, the keyring asks me for passwords 4 TIMES every time I log in.. .

freaking annoying...

---

### Post by oldpath on 2011-06-26
I have a similar problem.  Lost the original password.  Via PsychoCats instructions I set up a new login via recovery mode.  Now No Keyring match.  Since original password is lost I can not reset keyring login for new Password via instructions that call for resetting keyring password with old password.  Where do I go now?  I fear this may get dicey.  I am not very good at command line work.

This is on 10.10 Meerkat

---

### Post by oldpath on 2011-06-27
Please close this entry.  I think I have found the answer.

I was told by someone at System76 that I should delete the keyring password and reboot.  On reboot the keyring would ask for a new password.  The keyring did not ask for a password and the computer works just fine...so far.  The question in my mind is this. Does the keyring have any password right now?  So, I do not know that this problem is completely solved.  But the computer works as advertised. 

Oldpath

---

