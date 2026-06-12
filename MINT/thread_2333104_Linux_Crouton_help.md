---
title: "Linux Crouton help"
date: 2016-08-07
forum: MINT
---

### Post by irfan61802 on 2016-08-07
Hi,
I have an acer c720 chromebook and i was following instructions to download linux mint/cinnamon here:
[https://tr1t.wordpress.com/2015/04/21/installing-mint-cinnamon-in-crouton/](https://tr1t.wordpress.com/2015/04/21/installing-mint-cinnamon-in-crouton/)

I got up to the part where it says extra necessary programs and tells me to writ this command:
[FONT=Open Sans, Helvetica, Arial, sans-serif][COLOR=#444444]*sudo apt-get install python-software-properties ttf-ubuntu-font-family ubuntu-settings*[/COLOR][/FONT]

[FONT=Open Sans, Helvetica, Arial, sans-serif][COLOR=#444444]******In crosh, i then get this error: [B]
[/B][I]ubuntu-settings is not available, but is referred to by another package. 
This may mean the package is deleted, obsoleted, or only available from another source
Please help, Thank You![/I][/COLOR][/FONT]

---

### Post by Bucky Ball on 2016-08-07
Welcome. ***Ubuntu, Linux and OS Chat*** is not a support area, so

Thread moved to ***MINT***.

---

### Post by ajgreeny on 2016-08-07
Try running ```
sudo apt-get update
``` before you run that **sudo apt-get install** command.

---

### Post by irfan61802 on 2016-08-07
I tried it and it didn't work. Might there be another name for this package? Edit: When i try ubuntu-system-settings(the correct one)instead, it says package not found

---

