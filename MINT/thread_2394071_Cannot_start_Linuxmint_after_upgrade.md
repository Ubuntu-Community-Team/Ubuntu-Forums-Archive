---
title: "Cannot start Linuxmint after upgrade?"
date: 2018-06-12
forum: MINT
---

### Post by KayeNg on 2018-06-12
Hi guys.  

I was going to install vivaldi browser and I followed the instructions here:

[https://www.addictivetips.com/ubuntu-li ... -on-linux/]("https://www.addictivetips.com/ubuntu-linux-tips/install-vivaldi-web-browser-on-linux/")

As the tutorial suggests, I did the following first:

sudo apt update
sudo apt upgrade -y

...then I was able to successfully install vivaldi browser.  (previous  vivaldi installation attempts, without executing the above two commads  first, were failures)

However, when I tried to log in Linuxmint the next day, I could not get past the log in screen, and it had a window that says,

Your session only lasted less than 10 seconds.  If you have not logged  out yourself, this could mean that there is some installation problem or  that you may be out of diskspace.  Try logging in with one of the  failsafe sessions to see if you can fix this problem.
View details (~/.xsession-errors file)
initctl:  Unable to connect to Upstart:  Failed to connect to ....(sorry the rest of the text was out of screen)

If it matters, this laptop is triple boot:  Windows 7, Linuxmint, and  Lubuntu.  I can boot and start Windows 7 and Lubuntu with no problems,  only Linuxmint.

Also, I believe that during the process "sudo apt upgrade -y" , I chose not to update the grub (?).

Also, I don't know what a failsafe session is and how to log into it, but if  it's the same as Recovery Mode, it doesn't work.  I get the GUI desktop  (somewhat distorted appearance, like wrong resolution), but the same  error message appears.

Help please.
Thank you!

---

### Post by jeremy31 on 2018-06-12
Boot into Linux Mint, when you get to the error press CTRL + ALT + F1, enter your login info and enter ```
sudo apt remove virtualbox-guest*
```
then ```
shutdown -r now
```
See if that fixes Mint

---

### Post by KayeNg on 2018-06-25
jeremy31 you are a genius.  Thank you and God bless you.

---

