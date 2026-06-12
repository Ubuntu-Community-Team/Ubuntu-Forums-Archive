---
title: "Windows &amp; Ubuntu, dual boot / default time limit?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by cjacek on 2011-03-23
I was struggling how to phrase the question (in the subject) so let me clarify... I wish to install Windows 2000 and then do Ubuntu, on the same PC. I never had a dual boot before but I understand that it goes automatically (after a short time) to default Windows if Ubuntu is not chosen (on the boot up screen), correct? If so, if there's a "countdown" of sorts, is there a way to _disable_ it? I wish to have control over that aspect, have unlimited time during that boot "choose one" screen. Thanks!:)

---

### Post by tommcd on 2011-03-23
> **cjacek said:**
> 
I understand that it goes automatically (after a short time) to default Windows if Ubuntu is not chosen (on the boot up screen), correct?
When the grub2 menu comes up, if no action is taken, then Ubuntu will boot by default because it is first in the list.
> **cjacek said:**
> 
if there's a "countdown" of sorts, is there a way to disable it? I wish to have control over that aspect, have unlimited time during that boot "choose one" screen. 
You can do this. You will need to edit the */etc/default/grub* file. Scroll down to the *GRUB_TIMEOUT=10* line. Change the **10** to **-1**. This will cause the menu to be displayed until you make a selection.
(The default GRUB_TIMEOUT=10 means that the menu will be displayed for 10 seconds, which is plenty of time to make a selection. You can set it to -1 if you want the menu to be displayed indefinitely until you make a selection though).
After editing the /etc/default/grub file, be sure to run: ```
sudo update-grub
``` from the terminal so the changes take effect.
See this for reference: [https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

---

### Post by cjacek on 2011-03-24
Wow, this is the type of answer I was hoping for! Thank you very, very much!! I will try what you suggest. All the best. :)

---

### Post by Dutch70 on 2011-03-24
I just want to add that if it is set to 10 sec or any other time limit and you hit the down arrow key to choose one. It will stay until you hit "enter" to actually make the selection.

---

### Post by cjacek on 2011-03-24
> **tommcd said:**
> When the grub2 menu comes up, if no action is taken, then Ubuntu will boot by default because it is first in the list.



Sorry, just to clarify that Ubuntu will still be the default and first on the list even if I install Windows 2000 (first) and then Ubuntu (second, after Windows)? Is this correct? Thanks again. :)

---

### Post by cjacek on 2011-03-24
> **Dutch70 said:**
> I just want to add that if it is set to 10 sec or any other time limit and you hit the down arrow key to choose one. It will stay until you hit "enter" to actually make the selection.

Got it, thanks! :)

---

### Post by tommcd on 2011-03-24
> **cjacek said:**
> Sorry, just to clarify that Ubuntu will still be the default and first on the list even if I install Windows 2000 (first) and then Ubuntu (second, after Windows)? Is this correct? Thanks again. :)
Yes, because the grub2 boot loader sets it up that way. When you boot the computer you will see Ubuntu listed first in the menu. Windows will be at the bottom of the menu.

---

### Post by cjacek on 2011-03-24
> **tommcd said:**
> Yes, because the grub2 boot loader sets it up that way. When you boot the computer you will see Ubuntu listed first in the menu. Windows will be at the bottom of the menu.

Great, thanks again! :)

---

