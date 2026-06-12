---
title: "I have met a problem when update ubuntu 7.04 to 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by linyongting on 2007-10-22
Yesterday, I used the following command to update ubuntu 7.04 to ubuntu 7.10

At firstly, edit the sourcec.list.
run sudo apt-get update
run sodup apt-get dist-upgrade

these two command take me 2 hours to finish installation.

reboot my PC, and select the latest version(7.10) to run automatically.

But I can't log on with my username and password. ylin is my username.
It said that the directory /home/ylin is not existed,and other prmt.

So I log in with older version successfully, and some software have been upgrade to 7.10.

Who can tell me the reason, my upgradetion fialed, why can't i log in the new version.

Why?why?
help me!

my email is:
[email]lyt2008bj@163.com[/email]

a china guy. thank you  all!

---

### Post by Pumalite on 2007-10-22
Boot to recovery mode

You will be loged in as root

Enter
Code:

passwd <user>

where <user> = the user you want to set a passowrd

Then enter :

Code:

telinit 2

---

### Post by linyongting on 2007-10-22
Thank you for your suggestion.

I log in with safe model, but the shell print some many error so that I can't type any command to recovery it. When I type a character, the printed information have made it disappeared.  

I think there must be some error in dist-upgrade, but what is the root reason for that, I don't know it, who can help me?


thank ALL,
A Chinese friend, welcome!

---

### Post by Pumalite on 2007-10-22
You'd be better off with a clean install.

---

### Post by linyongting on 2007-10-23
yeah!
I am working now, that not allowed me to execute a clean installation.

I am using the previous version(7.04).

I will uninstall 7.04 and make my pc turn back to 7.04 .


Thank you,guy!

---

