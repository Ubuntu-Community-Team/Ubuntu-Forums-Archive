---
title: "Firefox upgrade request from Paypal"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by rossignol on 2018-06-08
Received an email from Paypal this morning stating that I needed to upgrade my browser because of non-compliance with their security requirements (TLS 1.2) before June 30. There is also a statement to the same effect on the paypal site ( [https://www.paypal.com/us/smarthelp/home](https://www.paypal.com/us/smarthelp/home) ), so I know that it is not a spoof email.

However, in going to the Firefox update web site, it states that updates, if Firefox was installed as part of a Linux package, have to be installed as updates to the package.

How soon does Ubuntu plan on providing this update?

---

### Post by coffeecat on 2018-06-08
Ubuntu usually releases the latest Firefox as part of routine updates very soon after it is released by Mozilla, so long as you are running a currently supported release of Ubuntu.

Have you updated recently? What release version of Ubuntu are you running?

---

### Post by rossignol on 2018-06-08
Upgraded to 18.04 a few months ago. Updates are automatic - i have received a few over that timeframe.

 Firefox version 60.0.1 64 bit. On the Firefox site, i see that there is a version 60.0.2 available.

---

### Post by Dennis N on 2018-06-08
That's just an announcement. Doesn't mean you are not compliant. Firefox 60.0.1 passes loading the test page link on their "How do I check and update my browser" page, so don't worry about it.

---

### Post by ubfan1 on 2018-06-08
Firefox 60 defaults to TLS1.2, and has for a long time.  See [https://support.mozilla.org/en-US/questions/1198543](https://support.mozilla.org/en-US/questions/1198543)  and [https://support.mozilla.org/en-US/questions/1138889](https://support.mozilla.org/en-US/questions/1138889)  There might be some other problem causing a fallback to a lower TLS.    From the first link:
There are TLS settings prefs on the **about:config** page that specify the minimum and maximum TLS version.  
 
[LIST]
[*]security.tls.version.min = 1
[*]security.tls.version.**max** = 3
[/LIST]
 1 means TLS 1.0  2 means TLS 1.1  3 means TLS 1.2 (default)  4 means TLS 1.3;

---

### Post by rossignol on 2018-06-08
Finally found the test page link, and it loaded correctly. Problem solved.

Thanks.

---

