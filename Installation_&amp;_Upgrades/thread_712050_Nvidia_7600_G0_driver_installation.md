---
title: "Nvidia 7600 G0 driver installation"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by cozmika on 2008-03-01
I downloaded the driver form Nvidia page but when I type "sh name_of_driver.run" it says that I have to close X-server. I don't know how to do that, and I have the other problem. Wireless card isn't working... But Ubuntu knows what card it is, and it says it is in use.

I think nobody could help me, but this is my only hope

---

### Post by Pumalite on 2008-03-01
sudo /etc/init.d/gdm stop

---

### Post by cozmika on 2008-03-01
> **Pumalite said:**
> sudo /etc/init.d/gdm stop

I get black screen with few sentences and it is doing nothing....

---

### Post by Pumalite on 2008-03-01
Ctrl+Alt+F1 to get command line
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/Driver.run
Then startx
Make sure you have build-essential installed:
sudo aptitude install build-essential
(before you try the driver)

---

### Post by cozmika on 2008-03-01
> **Pumalite said:**
> Ctrl+Alt+F1 to get command line
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/Driver.run
Then startx
Make sure you have build-essential installed:
sudo [COLOR="Red"]aptitude[/COLOR] install build-essential
(before you try the driver)

I cant connect to the net... wireless isn't working

---

### Post by Pumalite on 2008-03-01
Get wired to the Internet, preferably through a router that provides you with DHCP

---

### Post by cozmika on 2008-03-01
Well, I give up... I lost interest for Linux... It does more trouble than happiness... Thanks anyway

---

### Post by Pumalite on 2008-03-01
Too bad. One shouldn't give up so easily. Besides, we were all willing to help you. Nothing is easy in life.

---

### Post by cozmika on 2008-03-01
Well... I have Toshiba A100-599 and if you 100% sure how I can run Ubuntu with all drivers I will gladly try to use Linux :)

---

### Post by Pumalite on 2008-03-01
What are the specs of this laptop?(I assume it's a laptop)

---

### Post by cozmika on 2008-03-01
NVIDIA GeForce Go 7600 (256 MB)
Realtek ALC862 @ Intel 82801GBM ICH7-M - High Definition Audio Controller [B-0]
Intel(R) PRO/Wireless 3945ABG Network Connection

---

### Post by Pumalite on 2008-03-01
Are you wired to the Internet?

---

### Post by cozmika on 2008-03-02
No, I connect thorugh wireless ( Intel(R) PRO/Wireless 3945ABG )

---

### Post by spacesamurai on 2008-03-02
For your network problem, have you installed the wireless driver yet? If you haven't, you will not be able to use your card. 

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Finally, I have to agree with Pumalite. I have been working with Linux for about a year and a half now, and it takes time (or maybe I am a slow learner). But learning and pulling out your hair is one of the things that makes it great, along with the many people that are willing to help. Good luck :-)

---

### Post by cozmika on 2008-03-02
I downloaded it! But how to install :confused:... It seems hard... Can somebody write down  the easyest way?  :confused:

---

