---
title: "hp printer"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by haoleboy on 2010-08-02
I am attempting to install the HP psc 2410xi, using Ubuntu 10.4. I have installed the drivers, but I need to install the HPLIP stuff.  I have the understanding I must use the command line to install. I used the example from the HP website, but it looks like I am missing something. What commands do I use? 
Thanks for your help.

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> I am attempting to install the HP psc 2410xi, using Ubuntu 10.4. I have installed the drivers, but I need to install the HPLIP stuff.  I have the understanding I must use the command line to install. I used the example from the HP website, but it looks like I am missing something. What commands do I use? 
Thanks for your help.

Hi,

HPLIP is, by default, included with Ubuntu.

But you can check it something weird happened by reinstalling it through System > Administration > Synaptic Package Manager and search for hplip, if 'Installed version' isn't blank then HPLIP is already installed.

---

### Post by haoleboy on 2010-08-02
Thank you Justin, the program is installed. When i want to use the scanner, it tells me that no scanning software has been installed. Could you please show me how to do this little task? Or is it a big one?
Thank you for your time!:p

Mahalo!!

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> Thank you Justin, the program is installed. When i want to use the scanner, it tells me that no scanning software has been installed. Could you please show me how to do this little task? Or is it a big one?
Thank you for your time!:p

Mahalo!!

Hi! Try going to Applications > Graphics > Simple Scan

---

### Post by haoleboy on 2010-08-02
It shows unable to connect ....change scanner or cancel.And no other scanner is attached.....

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> It shows unable to connect ....change scanner or cancel.And no other scanner is attached.....

Okay, can you post a screenshot of the HPlib error?

---

### Post by haoleboy on 2010-08-02
I'll give it a try....

---

### Post by haoleboy on 2010-08-02
file:///home/dave/Desktop/Screenshot-hplip-3.10.6.run%20(~-Downloads)%20-%20gedit.png

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> file:///home/dave/Desktop/Screenshot-hplip-3.10.6.run%20(~-Downloads)%20-%20gedit.png

Can you attach that image as a attachment? The link you posted to me would only work on your computer, (/home/dave is not on my computer :p)

---

### Post by haoleboy on 2010-08-02
I think I did this right.....

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> I think I did this right.....

According to your previous posts, HPLIP is already installed? If so, there is no reason to install HPLIB again - you can delete that .run file.

If you want to open HPLIP install the package 'hplip-gui' from Synaptic Package Manager. Then go to **System > Preferences > HPLIP Toolbox**

---

### Post by haoleboy on 2010-08-02
Sorry for the delay... I did not find any listing under <system...<preferences.... but I did find the toolbox listed in the System Package Manager... I hesitated to check or uncheck to uninstall the program....

---

### Post by JustinR on 2010-08-02
> **haoleboy said:**
> Sorry for the delay... I did not find any listing under <system...<preferences.... but I did find the toolbox listed in the System Package Manager... I hesitated to check or uncheck to uninstall the program....

Did you install 'hplip-gui'?

---

### Post by haoleboy on 2010-08-02
I am installing it at this moment.....Thank you

---

### Post by haoleboy on 2010-08-02
Mahalo Justin;
The GUI is installed, I can clean the heads, all the good stuff is listed.  But it does not recognize the scanner... I should be able to figure this one out.....
Thank you so very much for your steering me in the right direction!

Mahalo!!

---

