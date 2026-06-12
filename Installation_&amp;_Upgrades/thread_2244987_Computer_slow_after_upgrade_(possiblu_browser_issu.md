---
title: "Computer slow after upgrade (possiblu browser issue)"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by kkaniff on 2014-09-20
Hi,

I'm runnning Xubuntu and have just upgraded to 14.04. Right after reboot my computer started acting up and I can't pinpoint what causes it to work so slowly. I suspect it may be the browser, as I keep getting the error below.

```
A script on this page may be busy, or it may have stopped responding. You can stop the script now, open the script in the debugger, or let the script continue.

Script: https://mail.google.com/_/scs/mail-static/_/js/k=gmail.main.en.28jSui15ha8.O/m=m_i,t,it/am=nBHDJRn7g8gZ7tIn1P6977NPit3_J_ITJgBC2AuA_5v9P8DWA_ug7lA/rt=h/d=1/t=zcms/rs=AItRSTNkT8SHuAVsdPjAEIcaQtyn1AONkQ:67
```

What's weird, is that the unresponsive script seems to be appearing whenever I'm on Gmail.

Can anyone suggest a test I can run to diagnose the porobem?

Thanks
KK

---

### Post by JKyleOKC on 2014-09-20
That error message appears to indicate an attempt to connect to port 67 at mail.google.com, which would most probably be a request for a new IP address. Since the URL is so long and complicated, I'd be extremely suspicious of it -- could be some sort of mis-written malware attempting to connect to a botnet's command server.

Have you noticed any other anamolies when working with gmail?

EDIT: Were it happening to me, I would immediately install wireshark and start inspecting all packets to try to see what might be going on behind the scenes...

---

