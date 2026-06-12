---
title: "Cannot open PHPmyadmin"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by tejas87 on 2012-08-03
Hello,

Now that i have installed xampp. I tried opening localhost on web browser and the xampp page opens but when i open localhost/phpmyadmin i get a error:

New XAMPP security concept:

Access to the requested directory is only available from the local network.

This setting can be configured in the file "httpd-xampp.conf".

Please can you let me know what is the main problem. Where do i find httpd-xampp.conf and what changes needs to be done.

---

### Post by TheFu on 2012-08-03
> **tejas87 said:**
> Now that i have installed xampp. I tried opening localhost on web browser and the xampp page opens but when i open localhost/phpmyadmin i get a error:


xampp is a complete installation of a complex software stack. I suspect most people here haven't used it. I haven't.  Adding "xampp" to your subject might get more views.

I can only guess about the phpmyadmin issue, but basically, if your client PC isn't on the same subnet as the server, then it will reject your attempted connection.  **It is about time.**  Remote connections through webguis has been a backdoor for far too long.  How to changes those settings will be in the PHPmyadmin setup and configuration instructions. [http://www.phpmyadmin.net/documentation/](http://www.phpmyadmin.net/documentation/) section 4.6 explains it.

Allowing access to phpmyadmin from the internet is a huge, huge, big, huge security risk. Ask if you'd like to know more or ways to lock it down to specific IP only.

---

### Post by tejas87 on 2012-08-03
Can you tell me how to lock it down to specific ip

---

### Post by TheFu on 2012-08-08
> **tejas87 said:**
> Can you tell me how to lock it down to specific ip
 How to changes those settings will be in the PHPmyadmin setup and configuration instructions. [http://www.phpmyadmin.net/documentation/](http://www.phpmyadmin.net/documentation/) section 4.6 explains it.

---

### Post by dakshbhatt21 on 2012-09-01
hey buddy go through this link and if not solve then tell me . . .

[http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html)

---

