---
title: "Unable to change settings! pls hlp!"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by caffemusse on 2005-07-02
Maybe posted earlier on in the wrong place....

Having just installed kubunto, and set up my lan as standard internet conection, I'd like to configure my wlan too. (ipw2200)

But when entering the settings and choosing administrator mode button, it does not open the functions after giving it the correct password. In terminal I can su myself and it accepts the password .

I need to get into the network settings in order to activate my wlan card. Any suggestions? 
If you suggest commands from a terminal window, please be detailed, since I am a Newbie to linux.

Thx :^o

---

### Post by Juergen on 2005-07-02
> In terminal I can su myself and it accepts the password.
su or sudo? Maybe your just using the wrong password:

In a standard (K)Ubuntu install all admin-stuff is made via sudo or gksudo/kdesudo-menus.
And sudo in all variants wants **your** pasword, not that of root like su does.

---

### Post by caffemusse on 2005-07-02
Yes I am using my password (only one user on the pc) the only password that has been configured.

When trying to enter admin mode in the control panels, it just doen't happen. But it does not tell me either that the password is wrong.

---

### Post by Juergen on 2005-07-05
Try to start those apps in a xterm. 
That way you should see the error messages.

So, open a xterm and try
```
gksudo synaptic
```and look at the ouput.

---

