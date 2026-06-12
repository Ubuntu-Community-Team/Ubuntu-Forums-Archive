---
title: "Can't able to install jUART plugin in my system?"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by yuvang on 2013-03-07
Hi to all,
 
       I have to install jUART plugin in firefox. I have a npjUART.so file. File is in there _**[https://github.com/billhsu/jUART](https://github.com/billhsu/jUART)**_. I had tried in some ways.

**Way1:**     **[COLOR=#000000][FONT=Ubuntu Mono]sudo ln -s [/FONT][/COLOR]npjUART[COLOR=#000000][FONT=Ubuntu Mono].so /etc/firefox/[/FONT][/COLOR]npjUART**[COLOR=#000000][FONT=Ubuntu Mono]**.so  **

**Way2:   **paste that file in  **usr/lib/mozilla/plugins/** location.

**Way3:**   Simply  paste the file in [/FONT][/COLOR]**usr/lib/mozilla/ **location.
[COLOR=#000000][FONT=Ubuntu Mono]   
      Each time checked the firefox with restart. How can i activate that plugin? Please give me a solution...

Thamks & Regards,
 
  *** Yuvang ***
[/FONT][/COLOR]

---

### Post by oldos2er on 2013-03-07
Did you try copying it to ~/.mozilla/plugins/ ?

The "~" is shorthand for your user's home folder.*

---

### Post by yuvang on 2013-03-09
Hi, 
 I tried that way and ways are in  [http://kb.mozillazine.org/Determining_p%20...%20y_on_Linux](http://kb.mozillazine.org/Determining_p%20...%20y_on_Linux)  too. But still  I didn't get plugin active.
Any other ways are there..?

Thanks & Regards 
 
Yuvang...

---

### Post by yuvang on 2013-03-15
Hi to all,

 I got successfully added that plugin, Mistake was in version, It has worked nice in 12.0.4 Ubuntu 64 bit machine.

Thanks all who has helped me...


Thanks & Regards,

Yuvang...

---

