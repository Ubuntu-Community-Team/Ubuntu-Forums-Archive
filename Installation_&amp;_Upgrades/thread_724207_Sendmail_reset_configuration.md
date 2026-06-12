---
title: "Sendmail reset configuration"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by jorgepedret on 2008-03-14
Hi buddies,

I installed sendmail for use it with php mail() function. The fresh install worked fine, it took like 1 minute or 2 to send the email, but at least I was getting it in my inbox without any addition configuration. (I just did sudo apt-get install sendmail).

Trying to solve the problem that it was taking too long to send the email, I changed or added lines to the sendmail.cf or sendmail.mc (don't remember), and restarted sendmail and now is not working... :(

I found some better solutions for solving the delay, but I want to make the changes with a fresh sendmail installation. I tried apt-get remove sendmaill; apt-get install sendmail, but it keeps the same configuration. And I don't want to risk to erase the config file manually (should I?).

If you need more information or if you have a possible solution let me know please.

Note: I don't remember the lines that I changed, I believe it was 'define something', it was for defining an smtp server.

Thanks in advance

---

