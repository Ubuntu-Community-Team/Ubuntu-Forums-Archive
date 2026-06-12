---
title: "The internet not working on Ubuntu 17.04 live usb!"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by ahmadwinchester on 2017-04-13
I'm trying to install ubuntu 17.04, but the internet is not working at all on the live usb. I even tried ubuntu gnome, still the same issue. It's connected, but it's not working, the cable, and the wifi. Not sure what's the problem.

---

### Post by ajgreeny on 2017-04-13
Please do not use such huge brightly coloured font when posting.
Doing so does not increase your chance of getting an answer.
Use larger or coloured fonts simply to add emphasis to particular points, not a complete post.

---

### Post by Frogs Hair on 2017-04-13
What operating system/s are on the computer. I asked because I had a similar problem on my dual boot , The cable was connected but the browser didn't work.

---

### Post by ahmadwinchester on 2017-04-13
> **Frogs Hair said:**
> What operating system/s are on the computer. I asked because I had a similar problem on my dual boot , The cable was connected but the browser didn't work.

I have windows 10 installed on my system, but I never had this problem before really with dual boot or even just trying ubuntu before installing it, after I googled for a while, I found out that a lot of people are having the same issue.

---

### Post by Frogs Hair on 2017-04-13
> **ahmadwinchester said:**
> I have windows 10 installed on my system, but I never had this problem before really with dual boot or even just trying ubuntu before installing it, after I googled for a while, I found out that a lot of people are having the same issue.


I backed my files to a removable device the deleted the previous Ubuntu partitions and when I tested 17.04 everything worked fine. This a problem because you can't  preform a proper test. When I tried to test Budgie , Chromium identified the problem as a DNS configuration problem.

---

### Post by wildmanne39 on 2017-04-13
If it is the DNS issue that has effected some users of 17.04 you can go into network manager and change the DNS server to googles DNS servers to work around the issue and their servers are faster too.

I am posting a screenshot of how to change the server in network manager.

After you enter the sever information click save and close then restart network manager by doing:
```
sudo systemctl restart NetworkManager.service
```

---

### Post by yordanov on 2017-04-16
> **wildmanne39 said:**
> If it is the DNS issue that has effected some users of 17.04 you can go into network manager and change the DNS server to googles DNS servers to work around the issue and their servers are faster too.


This is not a solution. It is just a workaround.

---

### Post by wildmanne39 on 2017-04-16
> **yordanov said:**
> This is not a solution. It is just a workaround.
Really? of course it is, that is what we do most of the time dealing with networking and wireless issues.

I have been doing this for 6 years and there are still some bugs that have not been fixed so if it were not for work-arounds people would not have internet connections all these years.

You are welcome not to use a work-around if they offend you, and we all would be pleased if you fixed the issue yourself and posted the solution so everyone will have the solution instead of a work-around.

To be honest I do not see what the big deal is as long as your internet works and works good.

Your welcome!:)

---

### Post by DuckHook on 2017-04-16
> **yordanov said:**
> This is not a solution. It is just a workaround.:confused:

A most provocative statement. What would a "solution" look like to you?

---

### Post by gychang2 on 2017-05-22
> **wildmanne39 said:**
> If it is the DNS issue that has effected some users of 17.04 you can go into network manager and change the DNS server to googles DNS servers to work around the issue and their servers are faster too.

I am posting a screenshot of how to change the server in network manager.

After you enter the sever information click save and close then restart network manager by doing:
```
sudo systemctl restart NetworkManager.service
```

does not seem to work on my new budgie 17.04, is "N" and "M" capitalized?, is ".service" needed?

appreciate help.

---

### Post by wildmanne39 on 2017-05-22
When running commands it is best to copy and paste for accuracy, and yes it has to be exactly as you see it, did you do what is in the screenshots first?

---

### Post by gychang2 on 2017-07-09
> **ahmadwinchester said:**
> I'm trying to install ubuntu 17.04, but the internet is not working at all on the live usb. I even tried ubuntu gnome, still the same issue. It's connected, but it's not working, the cable, and the wifi. Not sure what's the problem.

for me, this was the solution.  [https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019#905019](https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing/905019#905019)

---

