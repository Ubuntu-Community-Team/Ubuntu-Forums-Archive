---
title: "update manager error message"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by nicola oxo on 2010-01-31
can anyone please help me, every time i try to update manager this error message keeps showing, i have lots of updates available. i don,t know what to do.    E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline   :confused:

---

### Post by amac777 on 2010-01-31
I did a google search for you and found this solution:

```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0
```

listed here: 
[https://bugs.launchpad.net/ubuntu/+source/x11proto-core/+bug/425599](https://bugs.launchpad.net/ubuntu/+source/x11proto-core/+bug/425599)

hope it works for you

---

### Post by nicola oxo on 2010-01-31
many thanks for your reply, how do i put this code into laptop, i new at all this! :D
 
 
 
 
 
> **amac777 said:**
> I did a google search for you and found this solution:
 
```
cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0
```
 
listed here: 
[https://bugs.launchpad.net/ubuntu/+source/x11proto-core/+bug/425599](https://bugs.launchpad.net/ubuntu/+source/x11proto-core/+bug/425599)
 
hope it works for you

---

### Post by amac777 on 2010-01-31
Those are three commands you need to enter into the terminal. To open the terminal, go to Applications->Accessories->Terminal. When you enter the second command, you will need to enter your password.

After you've entered all three, you can type "exit" to close the terminal and then open update manager to see if the problem is fixed.

---

### Post by nicola oxo on 2010-01-31
Ok thanks, i'll give it go
 
 
> **amac777 said:**
> Those are three commands you need to enter into the terminal. To open the terminal, go to Applications->Accessories->Terminal. When you enter the second command, you will need to enter your password.
 
After you've entered all three, you can type "exit" to close the terminal and then open update manager to see if the problem is fixed.

---

### Post by nicola oxo on 2010-02-01
i,ve tried to enter in the terminal, not too sure what the password required is? where will i find it.
thanks
nicola:)

---

### Post by amac777 on 2010-02-01
That's your password. The same one you use to login to the system.

---

### Post by nicola oxo on 2010-02-01
think my issue is when my daughter got laptop for xmas we couldn;t get on the internet in my house. she got on at her friends house no bother but the address in the terminal box is showing friends internet connections, is it possbile that the password needed is for that. i.ve tried using my daughters password here.  help!!!!

---

### Post by amac777 on 2010-02-01
Well, what you are trying to do is run a command as an administrator by using "sudo". Sudo requires that your user be an administrator on the system, and also requires you to enter your user's password to confirm it really is you. This should be the same password you use to login to Ubuntu as that user after you turn on the computer. (Assuming you don't have automatic login turned on.)

To check and make sure your user is an administrator, you can run these two commands in the terminal:

```
whoami
groups
```

The first command will tell you your user name. The second will tell you which groups you belong to. If you see "admin" as one of the groups, then you know you are an administrator. In that case, the password to use sudo is the same one you would use to log in as that user (shown in response to whoami). 

If you don't see "admin" as one of your groups, then your user doesn't have administrative permission on the computer so you can't use sudo. In this case, maybe your daughter has another user on the machine that is an administrator and you can use that one to make your user an administrator too.

---

### Post by nicola oxo on 2010-02-01
i really apperiate your help, i have checked the termianl and it says the correct whoami is my daughter. She has no other users on the laptop,as soon as i try to enter the password it says incorrect. she is the administrator but i don't think she puts password in when she puts on the laptop. I can't believe i am having so much trouble, the laptop is brand new and i am having all this bother with updating. Not sure where to go now, but thanks anyway. any other suggestions welcome.
nicola

---

### Post by amac777 on 2010-02-01
Hmmm.... I don't quite understand what you meant when you said:

> but i don't think she puts password in when she puts on the laptop

Do you mean the computer automatically boots up to the Ubuntu desktop when you turn it on? Or do you mean, she has to login but doesn't have any password so just presses enter at the password prompt?

If the second, try just pressing enter at the password prompt for sudo too. (no password)

If the first, I suspect you might not know her password. Maybe a typo? And remember the password is case-senstive. Even if you solved the errors for update manager, you will still need to enter this password when you try to update. So you must figure out the password before you will be able to update. 

If all else fails, you could login to ubuntu in recovery mode and reset her password.

---

### Post by nicola oxo on 2010-02-01
i give up. there was no password, so i did the command you said, pressed enter when asked for password, got to the end and pressed exit, but still no joy when trying to update manager, following message still showing

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

any advice on what to do now, who should i contact, is it ubuntu or dell where i bought it from??

:p thanks for taking time to reply and help

---

### Post by amac777 on 2010-02-01
That's too bad it still isn't working. I think you should contact Dell since this problem appears to be a Dell issue. Here's another posting with a different solution about it:

[https://answers.launchpad.net/ubuntu/+question/78863](https://answers.launchpad.net/ubuntu/+question/78863)

Good luck.

---

