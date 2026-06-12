---
title: "&quot;out of frequency&quot;"
date: 2012-03-30
forum: Installation &amp; Upgrades
---

### Post by harpreet928 on 2012-03-30
Hi,

I just signed up the forums to seek answer from the experts in here , as I am not able to Install Ubuntu on my system
When i boot from "Ubuntu Bootable" CD, it does starts the process of Installtion but after running the screen like this [IMG]<a href="http://imgur.com/b1Bjl"><img src="http://i.imgur.com/b1Bjl.jpg" alt="" title="Hosted by imgur.com" /></a>[/IMG]



IT GIVES ME ERROR OF "OUT OF FREQUENCY" 
I know this is related to my monitor.

and the "OUT OF FREQUENCY" Error looks like this 
[IMG]<a href="http://imgur.com/pEYMs"><img src="http://i.imgur.com/pEYMs.jpg" alt="" title="Hosted by imgur.com" /></a>[/IMG]


Now i have done googled for this error and so many people are talking about to EDIT FILE /etc/X11/Xorg.conf
But i really don't know how to edit it , or how to open it because i am a WINDOW USER and I want to leaves Windows forever and start using Kubuntu or Ubuntu or Linux, and I am not familiar with Linux based OS !!


I have tried to Install Kubuntu and Linux MINT and even Xubuntu also, The problem is same with all Operating system Installation.

Now, somehow, I know to have to change my "HORIZONTAL FREQUENCY" of monitor as its operating frequency is 
HF - 30 - 61
VF - 50 - 120

While , if you can see in the picture my HF turns out to be 68.6, which is out of operating frequencies.
but the VF is within the operating range of frequencies.

SO, please tell me how can i get rid of this problem and get either Kubuntu or Ubuntu Installed on my pc

My monitor specifications:
CRT Monitor
LG Studioworks 563N

My system Configuration:
Intel Celeron 2 GHZ
1 GB ram
Gigabyte Motherboard.


Kindly help me out guys !!

Thanks !!

---

### Post by darkod on 2012-03-30
Try running the cd in live mode first, Try Ubuntu. Don't start the installation right away.

Can it run live mode correctly?

If not, try this:
During boot with the cd hit Esc immediately when you see the first purple screen (before the menu). That should load the older text menu.

Hit F6 for advanced options, then select 'nomodeset'. Then select Try Ubuntu and see if it loads fine.

If it does, don't try to install yet, you need more instructions. Just let us know.

---

### Post by oldos2er on 2012-03-30
What video card do you have?

---

