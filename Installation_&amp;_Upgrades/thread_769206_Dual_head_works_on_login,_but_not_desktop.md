---
title: "Dual head works on login, but not desktop???"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by RobbanC on 2008-04-26
Hi!

I'm scratching all my hair off.
I have installed Ubuntu Hardy on my desktop computer, that has a ATI X1300 graphics card (I think). I have connected two monitors. In my time with Windoze this has been working good as a huge desktop. 

Since I'm planning to move over to Ubuntu I want this to work as I want, but I'm stuck!

I have searched, looked and tested a number of things, but now I am as close as I can get, but not fully there.

I typed in this:
```

aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right -v

```
and presto! My _login screen_ is now NOT cloned. I have only one mousepointer that I can move between my monitors. Yey!!
BUT: As soon as I log in, my two monitors go back to beeing cloned and I see two mousepointers moving on each screen simultaniously. I have looked at "system->settings->screen resolution" but it seems there is only one screen to change the resolution on. Further, I can not uncheck the "cloned" tickbox.

Since the login screen works, I guess there is some other (personal) desktop setting that I want to remove or reset..... or???

Please help, I feel so close getting this to work! :(

---

### Post by RobbanC on 2008-04-26
Hmm, it seems like I got something to work after all.

Under "Programs" I found "ATI Catalyst Control Center" where both my monitors were detected properly. Here I could setup to use a big desktop. And after pressing OK, I got a big desktop to work on - until the next time I logged in.

I then found out that I had to have Gnome's own "Screen Resolution" open while configuring ATI Catalyst. When I was done in Catalyst I had to press OK also in Screen Resolution. Now it seems to work somewhat as I want it to. :)

---

### Post by JOliver83 on 2008-04-27
I am having the same problem with an ATI X550 but your solution does not seem to work for me. I get dual heads working as a big desktop at login but when I use your method or not, the screens become scrambled. Also I am using the Catalyst Control Center. What does your xorg.conf file look like if you dont mind. 
Thanks.

---

### Post by RobbanC on 2008-04-27
Sorry to hear that it didn't work for you.
Here's what my xorg.conf looks like now. I have not altered anthing manually in it.

I hope it helps or at least give you a clue...

---

