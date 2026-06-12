---
title: "Ubuntu is running in low graphics mode"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by sudeepbaby on 2011-05-20
Ubuntu is running in low graphics mode.Your screen, graphics card And input device settings could not be detected correctly. You will need to configure these yourself. ( If we press OK ) ( A dialogue box appears.) 
What would you like to do
*Run ubuntu in low graphics mode for just one session
* Reconfigure graphics.
*Troubleshoot the error.
*Exit to console login.
*Restart X
cancel/ok
(If we cancel Commands appear like this:)
 
Ubuntu 10.04.2 LTS johnson-desktop tty2
johnson-desktop login:-
 
(If we press OK another dialogue box appears.)plz help me for solving this problem

---

### Post by corrytonapple on 2011-05-20
What happens if you press "Troubleshoot the error"?  What kind of graphics card do you have?

---

### Post by Rubi1200 on 2011-05-20
Hi and welcome to the forums sudeepbaby :)

As corrytonapple asked, we need to know what graphics card is installed.

Also, did this happen on a fresh install, after an update, or any other situation?

The more information you provide, the better we can help you.

Thanks.

---

### Post by sudeepbaby on 2011-05-28
> **corrytonapple said:**
> What happens if you press "Troubleshoot the error"?  What kind of graphics card do you have?

Intel DG31pr mb used

---

### Post by kansasnoob on 2011-05-28
Please post the output of this command:

```
lspci | grep VGA
```

---

