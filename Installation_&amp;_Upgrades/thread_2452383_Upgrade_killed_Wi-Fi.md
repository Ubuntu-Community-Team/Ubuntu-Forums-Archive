---
title: "Upgrade killed Wi-Fi"
date: 2020-10-21
forum: Installation &amp; Upgrades
---

### Post by aughey on 2020-10-21
I saw a message that there was a software upgrade availible. I clicked for it to proceed. When it finished about 20 minutes ago my wi-fi was dead. It was not even showing any availible networks whatsoever. I rebooted the system but it made no difference. As my laptop has windows 10 on the other half of the hard drive I now switched to windows. It was working fine so I tried positng a question on here about this but I forgot the password. I rebooted into ubuntu to find it and lo and behold the wifi was now working fine on ubuntu end as well. What went wrong??

---

### Post by Impavidus on 2020-10-21
Do you know what package was upgraded? Check the logs if you don't remember.

My guess is that some networking service was stopped because of the upgrade, but not properly restarted. When you rebooted, it was restarted and wifi was restored.

---

