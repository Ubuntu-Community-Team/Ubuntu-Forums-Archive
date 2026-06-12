---
title: "[SOLVED] screen not bounded to the edge of monitor (7.10)"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by HUNTtheHIPPO on 2008-04-04
When I upgrade to 7.10 a few days ago, I found that it has a problem displaying to my monitor. My desktop extends past my monitor's edge. The area that is viewable scrolls as I move my mouse. I experience this problem in every resolution I have tried so far, except for 1024x768. I have a Westinghouse 1440x900 monitor with a GeForce 7 gt card. 

I know that resolution problem are common for people using 7.10, but I have seen any posts about screen scrolling.

Thanks.

---

### Post by Rocket2DMn on 2008-04-04
Hey,
Are you using the restricted drivers?  Have you reconfigured X automatically or manually?
Also, your profile says you are using 7.04, have you considered upgrading to Gutsy (though Hardy will be released is 2-3 weeks).

---

### Post by HUNTtheHIPPO on 2008-04-06
I am using the restricted nvidia driver, but I don't think I have updated X (or if I have it was automatic). I am running 7.10, I just have not updated my profile.

---

### Post by Rocket2DMn on 2008-04-06
OK, try reconfiguring X with this guide - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
Select the nv open source driver.  Then once you're in the GUI after the reconfiguration, you can reinstall the restricted nvidia driver.
If you still have problems, let me know your model nvidia card.  We may need to file a bug report.

---

### Post by HUNTtheHIPPO on 2008-04-07
Thanks, the link above worked great. Problem solved.

---

### Post by HUNTtheHIPPO on 2008-04-07
My Horizsync Vertrefresh where out of wack.

---

