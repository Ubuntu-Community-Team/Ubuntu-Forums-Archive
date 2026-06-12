---
title: "How can I restore or reinstall destop from console"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-11-18
I think that I get dark screen because of my destop need to be reinstalled.
I can login to ubuntu desktop 9.10, when I use revocery mode.
but when I just launch it I get only dark screen.
iy was working perfectly yesterday.
So I have navigate to my desktop using console, and there was no item there, I know I had many items on it.

---

### Post by dstew on 2009-11-18
> So I have navigate to my desktop using console, and there was no item there, I know I had many items on it.When you use recovery mode, you are the user **root** I believe. The shell prompt will usually have your currently logged in user name. In recovery mode, it will probably say **root**@*<your_machine_name>*. Or, you can check your currently logged-in user name with the **whoami** command.  To navigate to your regular user Desktop folder, you can navigate to /home/*<your_regular_user_name>*/Desktop as root, or change your login to your usual user name. Use the **login** command. Then ~/Desktop will be your usual user name Desktop folder.

You probably have altered some setting in your GUI program that has resulted in the loss of your desktop. You can try the **xfix** command in recovery mode to try to get it back.

---

### Post by doas777 on 2009-11-18
from recovery mode, run 
```
startx
```
and post the error messages if any come up/

---

