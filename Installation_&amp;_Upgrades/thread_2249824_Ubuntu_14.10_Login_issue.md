---
title: "Ubuntu 14.10 Login issue"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by belaa-maca on 2014-10-24
Hello,

Today I update my Ubuntu 14.04 to 14.10. It was standard update release proces and new ubuntu remove some package and instal new one... But when I was restarted my computer everithing is look normal but when I enter my pass and try to login noting happends. Username and pass field just dissaper and screen is showing welcome picture. 
When I try to login using console (Alt+Ctrl+F1) it's say that my pass is wrong. 
When I try old kernel the same thing happends again. I also try to use safe mode but I had no luck.

Can someone give me some instructions what I need to do to solve this issue?

---

### Post by Vladlenin5000 on 2014-10-24
Hi, welcome.

First of all double-check your password. It can actually be wrong and the system is behaving as it should. However, there's also the possibility of you typing it right but because **a)** you have special characters in your password **-and- b)** you have a non-US keyboard layout **-and- c)** somehow during the upgrade it changed back to the default US keyboard layout, it'll result in a wrong password...

---

### Post by belaa-maca on 2014-10-25
Hello,

I already check my keyboard layout and it's set English US keybord. Also my pass is created from letters and number. Any other guess?

---

### Post by belaa-maca on 2014-10-25
Hello,

New update,
I changed my password using root@ login and now when I  type it nothing happens. It just let me to again write it, but when I  put wrong pass there is message that say it was wrong. I can login using  console (ATL + CRTL + F1) pass is working here. But what I need to do  here?
I tried to update and upgrade but still I can't  login

---

### Post by Vladlenin5000 on 2014-10-26
Somehow the graphical UI is refusing to start. You may need to reinstall some proprietary drivers for your graphics card.

---

### Post by Bashing-om on 2014-10-26
belaa-maca; Hello;

As another thought, maybe "you" have lost authorization to access your /home ?

> **belaa-maca said:**
> Hello,

New update,
I changed my password using root@ login and now when I  type it nothing happens. It just let me to again write it, but when I  put wrong pass there is message that say it was wrong. I can login using  console (ATL + CRTL + F1) pass is working here. But what I need to do  here?
I tried to update and upgrade but still I can't  login

What returns: (ctl+alt+F1 at the login screen )
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /
ls -al /home

```

[INDENT][INDENT]a tale is told
[/INDENT][/INDENT]

---

### Post by belaa-maca on 2014-10-27
When I try to execute this
ls -al .Xauthority  - nothing
ls -al .ICEauthority - nothing
ls -al / - folders

---

### Post by Bashing-om on 2014-10-28
belaa-maca; Yuk !

Really odd, and not the expected result.
We have these error conditions:
> 
When I try to login using console (Alt+Ctrl+F1) it's say that my pass is wrong.
ls -al .Xauthority - nothing
ls -al .ICEauthority - nothing

Under these conditions I am not certain how to proceed .
@ Vladlenin5000; what are your thoughts on "changing the password" would that create the required .Xauthority & .ICEauthority files as opposed to 'exporting' XAUTHORITY ?

[INDENT][INDENT]when I do not know
[INDENT][INDENT][INDENT]preparation to learn something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2014-10-28
Sorry, I'm no longer here. My days is this forum are over, just logged on to tell you that.
Good luck.

---

