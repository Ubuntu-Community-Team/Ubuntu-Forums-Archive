---
title: "All user passwords failed to work."
date: 2019-03-23
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-03-23
I encountered a very strange situation. After rebooting Ubuntu 16.04 system, all users password failed to work, i.e. I am not able to login at the login screen after a reboot. I am really perturbed. :confused: How can I fix this situation?

---

### Post by #&amp;thj^% on 2019-03-23
Hello sunbear-c22, i can't imagine what could of happened on your end but see if this helps:  [https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/)

---

### Post by sunbear-c22 on 2019-03-23
> **1fallen said:**
> Hello sunbear-c22, i can't imagine what could of happened on your end but see if this helps:  [https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/)

Thanks. I tried it but still can't login. I noticed the error msg during login has been **"Fail to Start Session"**. My apologies for not stating this earlier. 

Side note: prior to reboot, I did sudo apt remove usbmuxd4  and sudo checkinstall usbmuxd.

---

### Post by sunbear-c22 on 2019-03-23
@1fallen I found the fix. [https://itsfoss.com/failed-to-start-session-ubuntu-14-04/](https://itsfoss.com/failed-to-start-session-ubuntu-14-04/)  Apparently, during my previous installation work, I had accidently affected `ubuntu-desktop`. Thanks.

---

