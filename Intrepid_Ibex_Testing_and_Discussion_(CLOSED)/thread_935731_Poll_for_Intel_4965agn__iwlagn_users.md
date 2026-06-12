---
title: "Poll for Intel 4965agn / iwlagn users"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syko21 on 2008-10-02
I have an intel 4965 card and have been experiencing random kernel panics (system freezes) while using the ubuntu packaged iwlagn wifi module. Self compiling the Oct-1-2008 compat-wireless source solved this issue for me. I am now wondering if this was just a singular event on my part or if there are more iwlagn users experiencing maching instability. Please vote here.


EDIT: Forgot to include that this only happened to me on 802.11n wifi. not 802.11b/g

EDIT 2: A bug report has been filed, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

---

### Post by smartboyathome on 2008-10-02
I do have freezes and have a 4965 (see thread [here]("http://ubuntuforums.org/showthread.php?t=935446")). I thought it was due to my computer going idle, but it ould be because of the wireless driver.

---

### Post by syko21 on 2008-10-02
When my machine kernel panics my caps lock key light blinks and I have 0 keyboard/mouse control. Are these the kinds of symptoms you are experiencing?

---

### Post by smartboyathome on 2008-10-02
> **syko21 said:**
> When my machine kernel panics my caps lock key light blinks and I have 0 keyboard/mouse control. Are these the kinds of symptoms you are experiencing?

My capslock key doesn't blink (that I remember, don't remember looking and the capslock light isn't very noticable), but I DID have 0 keyboard control. Not even the magic SysRQ keys worked.

---

### Post by jmmL on 2008-10-02
I'll echo that - I haven't experienced any issues so far, after about 5 hours use. However, establishing a connection seems harder in intrepid than in did in hardy. But that might just be because a lot of the wireless signals near me are very weak.

---

### Post by syko21 on 2008-10-02
Just want to make sure this is clear. It only happens on an 802.11N network.

---

### Post by smartboyathome on 2008-10-02
> **syko21 said:**
> Just want to make sure this is clear. It only happens on an 802.11N network.

Thats not my network then. Might be a different driver or something that we have in common. Can you list your hardware or supply your computer model so that we can see? I know I also get a kernel panic when coming out of suspend or hibernate.

---

